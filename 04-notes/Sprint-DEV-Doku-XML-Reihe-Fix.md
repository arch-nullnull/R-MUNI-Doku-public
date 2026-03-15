================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-XML-Reihe-Fix
Datum               : 2026-03-13
Stage               : 5 (aktiv)
Status              : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch      : Entwickler + Claude (Pair-Session)
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Stage-Modell (Ist-Zustand)
-------------------------------
Stage 4  FREEZE
Stage 5  AKTIV
         XML-Reihe (XML00–XML07) war nach Cleaning Run 5.5 strukturell
         angepasst worden (Pfade 03-stages → 02-stages, 02-artifacts →
         01-artifacts), jedoch nicht vollständig getestet.
         Beim ersten produktiven Testlauf traten drei voneinander
         unabhängige Fehler auf.

1.2 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Bugfix (produktiver Testlauf XML-Reihe)

Begründung   : Erster vollständiger Testlauf der XML-Reihe nach
               Cleaning Run 5.5 zeigte drei Fehler:

               1) XML05 scheiterte an lxml-Importfehler
               2) CSV09 fand root.cfg nicht (Tippfehler)
               3) CSV09 schrieb falschen Relationship-Type in relations.csv

               Der Archi CSV-Import schlug fehl mit:
               "Type should be of ArchiMate relationship type"

Fachlicher   : Die XML-Reihe ist nach diesem Sprint vollständig
Mehrwert       funktionsfähig. Der Kreislauf OEF → XML → CSV → Archi
               läuft stabil durch.

Governance-  : Ausschließlich Bugfixes. Keine Logikänderung an der
Konformität    Kernarchitektur. XML-Flow-Prinzip unverändert.


--------------------------------------------------------------------------------
2. ZIELDEFINITION (gemäß GOV 10.6)
--------------------------------------------------------------------------------

Ziel         : XML-Reihe (XML00–XML07) + CSV09 vollständig lauffähig.
               Archi CSV-Import nach dem Flow schlägt nicht mehr fehl.

Abgrenzung   : Kein Eingriff in Mapping-Logik, Sync-Regeln oder
               Archi-Modell-Inhalte. Ausschließlich technische Fixes
               in drei Scripts.

Überprüfbar  : Erfolgreich wenn:
               - XML00–XML07 fehlerfrei durchlaufen
               - CSV09 root.cfg findet und CSVs produziert
               - Archi Import der relations.csv ohne Fehlermeldung


--------------------------------------------------------------------------------
3. IST-ZUSTAND — PROBLEMANALYSE
--------------------------------------------------------------------------------

3.1 Fehler 1: XML05 — lxml ImportError
----------------------------------------
Script   : XML05-clear_merge.py
Fehler   : ImportError: cannot import name 'etree' from 'lxml'

Ursache  : XML05 verwendete lxml als XML-Bibliothek. Die lxml-Installation
           unter dem R+MUNI Python-Pfad war beschädigt bzw. inkompatibel.
           Reinstallation hatte in früheren Sessions keinen Erfolg gebracht.

Diagnose : Keine XML-Logs in 02-stages/99-logs vorhanden, weil XML05
           bereits beim Import abstürzte — noch vor jeder Log-Ausgabe.

3.2 Fehler 2: CSV09 — root.cfg nicht gefunden
-----------------------------------------------
Script   : CSV09-masterxml2csv.py
Fehler   : [ERROR] root.cfg not found or BLUEPRINT_ROOT not set.

Ursache  : Tippfehler in der Root-Auflösungslogik (Zeile 93):

             Alt (falsch):   line.startswith("<rootfolde>=")
             Neu (korrekt):  line.startswith("<rootfolder>=")

           Das 'r' am Ende von 'rootfolder' fehlte. Dadurch wurde der
           <rootfolder>-Eintrag in root.cfg nie gefunden.

3.3 Fehler 3: CSV09 — falscher Relationship-Type
--------------------------------------------------
Script   : CSV09-masterxml2csv.py
Fehler   : Archi Import: "Type should be of ArchiMate relationship type"
           id-426467a786c54685b8f563ee12655b4e

Ursache  : Archi OEF XML speichert Relationship-Typen ohne Suffix:
             OEF XML:       xsi:type="Composition"
             Archi CSV:     Type="CompositionRelationship"

           CSV09 übernahm den OEF-Wert unverändert. Archi erwartet
           beim CSV-Import den vollen Typ mit "Relationship"-Suffix.

           Diagnosemethode: Direktvergleich
             relations_direkt.csv  (nativer Archi-Export)   → CompositionRelationship
             relations.csv         (nach Flow)               → Composition

           Das OEF XML wurde als Quelle bestätigt:
             testi.xml Zeile 1198: xsi:type="Composition"
           → Der Flow kopiert korrekt. Das Mapping muss in CSV09 erfolgen.


--------------------------------------------------------------------------------
4. LÖSUNG — TECHNISCHE UMSETZUNG
--------------------------------------------------------------------------------

4.1 Fix 1: XML05 — lxml durch Standard-ET ersetzt
---------------------------------------------------
Datei    : XML05-clear_merge.py
Ansatz   : Komplette Neuentwicklung ohne lxml.
           Einzige Bibliothek: xml.etree.ElementTree (Python Standard)

Technische Anpassungen gegenüber lxml-Version:
  - find_parent() neu implementiert (ET hat kein .getparent())
  - ET.indent() für formatierte Ausgabe (ab Python 3.9)
  - tree.write() statt lxml pretty_print=True
  - Alle Namespace-Handling Funktionen (strip_ns, match_selector)
    bleiben funktional identisch

Unverändert:
  - Konsolidierungslogik (merge / keep / ignore)
  - sync.txt Regelwerk und Selector-Syntax
  - Alle Pfade und Log-Ausgaben

4.2 Fix 2: CSV09 — Tippfehler root.cfg Auflösung
--------------------------------------------------
Datei    : CSV09-masterxml2csv.py
Zeile    : 93
Änderung :
  Alt:  line.startswith("<rootfolde>=")
  Neu:  line.startswith("<rootfolder>=")

4.3 Fix 3: CSV09 — Relationship-Type Normalisierung
-----------------------------------------------------
Datei    : CSV09-masterxml2csv.py
Ansatz   : Neue Hilfsfunktion normalize_relationship_type()

Implementierung:
  RELATIONSHIP_TYPES = {
      "Association", "Access", "Influence", "Realization",
      "Serving", "Assignment", "Aggregation", "Composition",
      "Flow", "Triggering", "Specialization",
  }

  def normalize_relationship_type(etype):
      if etype in RELATIONSHIP_TYPES:
          return etype + "Relationship"
      return etype

Anwendung: Im Relationship-Parser (Zeile ~503):
  Alt:  etype = child.get(f"{xsi}type", "")
  Neu:  etype = normalize_relationship_type(child.get(f"{xsi}type", ""))

Abdeckung: Alle 11 ArchiMate 3.2 Relationship-Typen erfasst.
           Element-Typen (BusinessProcess etc.) werden nicht verändert.


--------------------------------------------------------------------------------
5. BETROFFENE DATEIEN
--------------------------------------------------------------------------------

  XML05-clear_merge.py     Neuentwicklung ohne lxml
  CSV09-masterxml2csv.py   Tippfehler-Fix + Normalisierungsfunktion


--------------------------------------------------------------------------------
6. DIAGNOSEVORGEHEN (Lernpfad)
--------------------------------------------------------------------------------

Schritt 1  Keine Logs in 02-stages/99-logs
           → Fehler tritt vor Log-Initialisierung auf
           → Verdacht: Script-Import schlägt fehl

Schritt 2  XML05 direkt ausgeführt
           → ImportError: lxml
           → Ursache klar

Schritt 3  XML05 mit Standard-ET neu entwickelt
           → XML00–XML07 laufen durch

Schritt 4  CSV09 scheitert an root.cfg
           → Code-Review: Tippfehler "<rootfolde>=" gefunden
           → Fix: fehlendes 'r' ergänzt

Schritt 5  Archi Import schlägt fehl
           → Direktvergleich: relations_direkt.csv vs. relations.csv
           → Type-Differenz gefunden: CompositionRelationship vs. Composition

Schritt 6  Quelle geprüft: testi.xml
           → OEF XML speichert "Composition" — korrekt laut OEF Standard
           → Fix muss in CSV09 beim Lesen erfolgen

Schritt 7  normalize_relationship_type() implementiert
           → Archi Import läuft durch ✓


--------------------------------------------------------------------------------
7. TESTERGEBNIS
--------------------------------------------------------------------------------

Testlauf 2026-03-13:

  XML00   root.cfg gelesen, XML00-root.resolved.txt geschrieben    OK ✓
  XML01   2 Archi + 1 BPMN Quelldatei erfasst                      OK ✓
  XML02   3 Dateien geparst                                         OK ✓
  XML03   MUNI EA.xml: 686 Einträge, MUNI FLOW.xml: 805 Einträge   OK ✓
          BPU01: 91 Einträge
  XML04   1491 Archi-Einträge in master.generated.xml gemerged      OK ✓
  XML05   10.901 Elemente verarbeitet, master.cleared.xml erstellt  OK ✓
  XML06   Durchgelaufen                                             OK ✓
  XML07   Durchgelaufen                                             OK ✓
  CSV09   CSVs erstellt                                             OK ✓
  Archi   Import ohne Fehlermeldung                                 OK ✓

Gesamtstatus: XML-Reihe + CSV09 stabil ✓

Offen:  bpmn: 0 entries matched in XML04
        → BPMN-Einträge werden noch nicht in master gemerged
        → Separater Sprint erforderlich


--------------------------------------------------------------------------------
8. OFFENE PUNKTE / NEXT STEPS
--------------------------------------------------------------------------------

8.1 BPMN 0 entries matched
----------------------------
Status   : Beobachtet, nicht behoben
Symptom  : XML04 loggt "bpmn: 0 entries matched"
Ursache  : Mapping-Regeln in mapping.txt greifen BPMN-Einträge nicht
Aktion   : Separater Analyse-Sprint — Mapping-Regeln für BPMN prüfen

8.2 XML05 Konsolidierung ohne Treffer
---------------------------------------
Status   : Beobachtet, erwartet
Symptom  : XML05 Log enthält keine MERGE/KEEP/IGNORE Einträge
Ursache  : Hängt mit BPMN 0 entries zusammen — keine BPMN-Elemente
           im master → keine Konsolidierung nötig/möglich
Aktion   : Wird mit 8.1 gemeinsam adressiert

8.3 M2B Erweiterung
---------------------
Status   : In Arbeit (laufender Test)
Aktion   : M2B-Anreicherung des master XML wird getestet ob der
           Gesamtflow stabil bleibt

8.4 DeprecationWarning utcnow()
---------------------------------
Status   : Kosmetisch, kein Fehler
Symptom  : datetime.utcnow() deprecated in XML05, XML06
Aktion   : Bei nächster Überarbeitung auf datetime.now(datetime.UTC)


--------------------------------------------------------------------------------
9. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Bugfix nach produktivem Testlauf
GOV 10.5  Fachlicher Mehrwert        OK  XML-Reihe erstmals vollständig lauffähig
GOV 10.5  Keine implizite Gov-Änd.   OK  Keine Logikänderung
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 2
GOV 10.6  Ziel überprüfbar           OK  Testergebnis Abschnitt 7
GOV 10.7  Zwischenschritte           OK  Normativ zugelassen
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Keine Architekturänderung
Stage 5   Rückkopplungsschutz        OK  Kernlogik XML-Flow unverändert


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-XML-Reihe-Fix | Stage 5 | 2026-03-13
================================================================================
