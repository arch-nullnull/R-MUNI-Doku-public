================================================================================
SPRINT-DEV-DOKU – EasyMapper
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : Sprint-DEV-EasyMapper_S6
Datum               : 2026-03-21
Stage               : S6 – AKTIV
Status              : Abgeschlossen
Erstellt durch      : EUMAXL + Claude (Pair-Session)
Vorgänger           : [[FREEZE-6]]
Nachfolger          : noch offen
================================================================================


================================================================================
1. AUSGANGSLAGE UND KONTEXT
================================================================================

1.1 Ist-Zustand vor diesem Sprint
-----------------------------------
Der Blueprint besitzt in Stage 5 einen stabilen CSV-Import-Flow für
kontrollierte Quellen: Archi-Exporte (SOURCE=archi) und XLSX-Dateien
(SOURCE=XLSX) mit bekannter Spaltenstruktur. Beide Quellen setzen voraus
dass Spaltenköpfe bekannt sind und über csvmapping.txt / propmapping.txt
auf die Master-CSV-Felder gemappt werden.

Für unkontrollierte externe CSV-Quellen (variierende Struktur, unbekannte
Spaltenköpfe, unbekanntes Encoding, unbekannte Trennzeichen) gibt es
keinen definierten Weg in das Modell.

Das 99-mappingmodel-Verzeichnis unter 00-model\00-archimate\99-mappingmodel\
existiert in der Ordnerstruktur aber ist leer — kein normatives
Mapping-Referenzartefakt vorhanden.

Relevante Artefakte vor dem Sprint:
  - 01-artifacts\02-csv\01-mapping\csvmapping.txt   Status: aktiv, XLSX-orientiert
  - 01-artifacts\03-XLSX\01-mapping\propmapping.txt  Status: aktiv, XLSX-orientiert
  - 02-stages\run-scope.txt                          Status: aktiv, GOV-geschützt
  - 00-model\00-archimate\99-mappingmodel\           Status: vorhanden, leer

Bezug: [[FREEZE-6]]


1.2 Konkrete Diskrepanz
------------------------
  IST:  Kein definierter Weg für externe, unkontrollierte CSV-Quellen
        in das ArchiMate-Modell. Encoding, Trennzeichen und Spaltenstruktur
        sind bei externen Quellen nicht garantiert bekannt.

  SOLL: Eigenständige ECM-Reihe (EasyCSVMapper) die externe CSV-Quellen
        erkennt, via ArchiMate OEF Mapping-Modell auf Ziel-Typen mappt
        und sauber als Archi-importfertige CSVs bereitstellt.


1.3 Auslöser
-------------
Auslöser-Typ: Feature-Zuwachs (Entwicklerwunsch, GOV 10.3 / 10.5)

Additiver Sprint — kein Eingriff in bestehende Reihen.


================================================================================
2. ENTSCHEIDUNGEN UND GRUNDSÄTZE DIESES SPRINTS
================================================================================

2.1 Eigene ECM-Reihe — keine Integration in CSV-Reihe
-------------------------------------------------------
Entscheidung:
  EasyMapper wird als vollständig eigenständige Reihe (ECM) gebaut.
  Keine Änderung an CSV-Reihe, XML-Reihe oder anderen bestehenden Reihen.

Begründung:
  Die CSV-Reihe ist Stage-5-frozen. Eine Integration würde Eingriffe
  erfordern die GOV-widrig sind. Die ECM-Reihe liefert am Ende
  Archi-importfertige CSVs — die Übergabe an bestehende Flows
  erfolgt über den manuellen Archi-Import-Kanal.

Auswirkung:
  CSV-Reihe unverändert. ECM ist vollständig autark bis zur CSV-Übergabe.


2.2 OEF XML als Mapping-Modell
--------------------------------
Entscheidung:
  Das Mapping zwischen externer CSV-Struktur und ArchiMate-Ziel-Typen
  wird als ArchiMate OEF XML Modell in 99-mappingmodel\ abgelegt.
  Der Entwickler baut das Mapping visuell in Archi — kein textbasiertes
  Konfig-Format, kein neues proprietäres Schema.

Begründung:
  ArchiMate ist Core-Komponente des Blueprints. Das Mapping-Wissen
  gehört ins Modell — nicht in eine weitere Konfigurationsdatei.
  OEF ist das standardisierte Austauschformat, bereits bekannt und
  von Archi nativ unterstützt.

Verworfene Alternativen:
  csvmapping.txt-Erweiterung: setzt bekannte Struktur voraus,
    funktioniert nicht für unkontrollierte externe Quellen.
  Eigenes Konfig-Format (.cfg): proprietär, nicht modellbasiert,
    kein visueller Überblick möglich.

Auswirkung:
  99-mappingmodel\ erhält erstmals normative Inhalte.
  Mapping ist in Archi navigierbar und visuell prüfbar.


2.3 Mapping-Semantik via ArchiMate Associations
-------------------------------------------------
Entscheidung:
  Die Mapping-Logik wird über ArchiMate Association-Beziehungen ausgedrückt:
    - Element OHNE eingehende Association → eigenständiges Archi-Element
      (Ziel-Typ = xsi:type des Elements im OEF)
    - Element MIT eingehender Association → Property des Ziel-Elements
      (Key = Spaltenname, Value = CSV-Wert)

Begründung:
  Association ist der universell zulässige ArchiMate-Beziehungstyp —
  keine Regel-Verletzung bei beliebigen Elementkombinationen.
  Die Semantik ist einfach, deterministisch und visuell sofort lesbar.

Auswirkung:
  ECM02 und ECM03 können die Mapping-Logik vollständig aus dem OEF
  auslesen ohne zusätzliche Konfiguration.


2.4 MAPPING= Erweiterung in run-scope.txt
-------------------------------------------
Entscheidung:
  run-scope.txt wird um einen neuen KEY MAPPING= erweitert:
    SOURCE=CSV
    MODEL=<dateiname>.csv
    MAPPING=<oef-dateiname>.xml

  MAPPING= referenziert direkt den OEF-Dateinamen (inkl. Extension)
  in 99-mappingmodel\.

Begründung:
  Additiv — bestehende Scripts ignorieren unbekannte Keys.
  Kein Eingriff in CSV03/CSV04 nötig.
  MAPPING= wird manuell nach CSV04-Lauf eingetragen (TD-02 bekannt).

Verworfene Alternativen:
  Separate Lookup-Datei (easycsvmapping.txt): doppelt gemoppelt,
    run-scope.txt enthält die Information bereits implizit.

Auswirkung:
  run-scope.txt Format erweitert, rückwärtskompatibel.
  MAPPING= wird nur von ECM-Scripts ausgewertet.


2.5 trash_*.csv Konvention
----------------------------
Entscheidung:
  Externe CSV-Quellen müssen mit Prefix trash_ benannt sein:
    trash_<name>.csv
  ECM-Scripts filtern explizit nach diesem Prefix — andere CSVs
  im gleichen Ordner werden ignoriert.
  Genau eine trash_*.csv pro Lauf — mehrere → harter Fehler.

Begründung:
  Der 00-archimatechild-Ordner enthält auch Archi-native Child-CSVs.
  Ohne Prefix-Filter würden ECM-Scripts alle CSVs verarbeiten.
  Einheitliche Benennung macht den ECM-Scope sofort erkennbar.

Auswirkung:
  Saubere Trennung zwischen Archi-Child-CSVs und externen Quellen.


2.6 Zweistufiger Import — IDs via Reihenfolge-Join
----------------------------------------------------
Entscheidung:
  Properties können nicht in einem Schritt mit Elementen importiert
  werden — Archi vergibt IDs erst beim Import. Daher zweistufig:

  Stufe 1: ECM02 → elements.csv nach 04-import\
           properties.csv + relations.csv nach 00-archimatearchive\ (geparkt)
           Archi-Import → IDs vergeben
           Archi CSV-Export → 04-import\elements.csv (mit IDs)

  Stufe 2: ECM03 → ID-Merge via Reihenfolge-Join
           Merged IDs aus elements.csv in properties.csv
           Schreibt 04-import\properties.csv + relations.csv
           Archi-Import → Properties korrekt zugewiesen

  Reihenfolge-Join: Property-Zeile N gehört zu Element-Zeile N
  (pro Ziel-Typ-Gruppe, basierend auf OEF-Mapping).

Kritische Regel:
  Element-Namen DÜRFEN zwischen Stufe-1-Import und ECM03-Lauf
  NICHT in Archi verändert werden. Der Reihenfolge-Join setzt
  stabile Exportreihenfolge voraus.

Begründung:
  Name ist der einzige stabile Anker vor ID-Vergabe.
  Reihenfolge ist deterministisch solange keine Umbenennung erfolgt.

Auswirkung:
  Vollständiger Import in zwei manuellen Archi-Schritten möglich.
  Properties landen korrekt am richtigen Element.


2.7 Property Definitions — manuell jetzt, jArchi später
---------------------------------------------------------
Entscheidung:
  Property Definitions werden für diesen Sprint manuell in Archi
  angelegt. Eine Automatisierung via jArchi ist als Folge-Sprint
  definiert — Python-Stunts um Archi zur Anlage zu zwingen sind
  tool-abhängig und fragil.

Begründung:
  Archi verhält sich inkonsistent wenn Properties importiert werden
  bevor die Property Definitions im Modell registriert sind.
  jArchi ist der saubere Kanal für Archi-interne Operationen.

Auswirkung:
  Manueller Schritt im Flow dokumentiert. Kein Blocker für den Sprint.


================================================================================
3. SPRINT-ZIELE UND UMSETZUNG
================================================================================

3.1 Ziel 1 — ECM-Reihe aufbauen (ECM00–ECM03)
-----------------------------------------------
Vier Scripts, vollständig implementiert und produktiv getestet.

  ECM00  Umgebungsvalidierung
         Prüft: root.cfg, 99-mappingmodel\, 00-archimatearchive\,
                00-archimatechild\ + trash_*.csv vorhanden
         Output: ECM00-root.resolved.txt in 02-stages\99-logs\
         Status: ✅ produktiv getestet

  ECM01  Müll-CSV → Artifact-CSV
         Erkennt Encoding automatisch (utf-8-sig, utf-8, cp1252, latin-1)
         Erkennt Trennzeichen automatisch (; , \t |)
         Liest alle Spaltenköpfe → je ein Artifact
         Schreibt elements.csv nach 04-import\ (Archi-importfertig)
         Status: ✅ produktiv getestet

  ECM02  Müll-CSV + OEF Mapping → elements/properties/relations
         Liest OEF XML aus 99-mappingmodel\ (via MAPPING= in run-scope.txt)
         Wertet Associations aus → Element vs. Property Unterscheidung
         Schreibt elements.csv → 04-import\
         Schreibt properties.csv + relations.csv → 00-archimatearchive\ (geparkt)
         Status: ✅ produktiv getestet

  ECM03  ID-Merge
         Liest elements.csv (frischer Archi-Export, MIT IDs)
         Liest properties.csv aus 00-archimatearchive\ (ID-los)
         Merged IDs via Reihenfolge-Join pro Ziel-Typ-Gruppe
         Schreibt properties.csv + relations.csv → 04-import\
         Status: ✅ produktiv getestet, Properties korrekt zugewiesen


3.2 Ziel 2 — OEF Mapping-Modell Konvention etablieren
-------------------------------------------------------
  Ablageort : 00-model\00-archimate\99-mappingmodel\
  Dateiname : <name>.xml (frei wählbar, wird in MAPPING= referenziert)
  Format    : ArchiMate 3.1 OEF XML
  Inhalt    : Artifacts (Quell-Felder) + ArchiMate-Typen (Ziele)
              + Associations (Mapping-Semantik)

  Erstmaliger produktiver Einsatz: trash_test.xml
  Mapping: Datum→Property, Fälligkeit→Property (beide zu Artifact/Buchungstext)
           Vorschreibung→Requirement, Zahlung→Goal, Buchungstext→Artifact

  Status: ✅ etabliert, produktiv getestet


3.3 Ziel 3 — Encoding + Trennzeichen Erkennung
------------------------------------------------
  Erkennungsreihenfolge Encoding   : utf-8-sig → utf-8 → cp1252 → latin-1
  Erkennungsreihenfolge Trennzeichen: ; → , → \t → |
  Praxistest: trash_test.csv (cp1252, Semikolon, CRLF, Excel-Export)
  Ergebnis: Korrekt erkannt und verarbeitet ohne manuelle Konfiguration.

  Status: ✅ produktiv getestet


================================================================================
4. ABGRENZUNG — WAS DIESER SPRINT NICHT TUT
================================================================================

Dieser Sprint tut explizit nicht:
  - Kein Eingriff in CSV-Reihe, XML-Reihe oder andere bestehende Reihen
  - Keine Automatisierung der manuellen Archi-Import-Schritte (→ jArchi)
  - Keine automatische Property-Definition-Anlage (→ jArchi Folge-Sprint)
  - Keine Verarbeitung mehrerer trash_*.csv pro Lauf
  - Kein Relations-Mapping (relations.csv bleibt leer — Grundlage vorhanden)
  - Keine Änderung an run-scope.txt Erzeugungslogik (CSV03/CSV04)

Bewusst zurückgestellt:
  Property Definitions automatisieren → jArchi, eigener Sprint
  Relations zwischen gemappten Elementen → Erweiterung ECM wenn Bedarf
  Script-Länge optimieren (ECM02/ECM03 ~300 Zeilen) → Cleaning Run,
    gemeinsame Hilfsfunktionen in HLP auslagern


================================================================================
5. BETROFFENE ARTEFAKTE
================================================================================

Neu erstellt:
  ECM00-validate_environment.py      01-artifacts\01-scripts\
  ECM01-csv_fields_to_artifacts.py   01-artifacts\01-scripts\
  ECM02-csv_to_mapping_to_csv.py     01-artifacts\01-scripts\
  ECM03-id_merge.py                  01-artifacts\01-scripts\
  trash_test.xml                     00-model\00-archimate\99-mappingmodel\

Geändert:
  run-scope.txt   Additiv um MAPPING= Tripel erweitert (manuell nach CSV04)

Unverändert:
  Alle Stage-3/4/5-Scripts          read-only — kein Eingriff
  CSV-Reihe                         vollständig unberührt
  csvmapping.txt / propmapping.txt  unberührt
  root.cfg                          kein neuer Eintrag


================================================================================
6. VOLLSTÄNDIGER ECM-FLOW
================================================================================

```
PHASE 1 — Erstmalige Strukturerkennung (einmalig pro neuer CSV-Quelle)
──────────────────────────────────────────────────────────────────────
ECM00   Umgebung validieren
ECM01   trash_*.csv → Spaltenköpfe als Artifacts → elements.csv (04-import)

Manuell: Archi Import elements.csv
         Property Definitions anlegen (manuell oder via HLP10)
         Mapping-Modell in Archi bauen:
           - Artifact-Elemente auf richtige Typen umwandeln
           - Associations für Property-Felder setzen
         OEF Export → 00-model\00-archimate\99-mappingmodel\<name>.xml
         MAPPING=<name>.xml in run-scope.txt eintragen

PHASE 2 — Regulärer Lauf (wiederholbar)
────────────────────────────────────────
CLE20   Master-CSVs leeren (optional, vor sauberem Lauf)

ECM00   Umgebung validieren
ECM02   trash_*.csv + OEF Mapping → elements.csv (04-import)
                                  + properties.csv (00-archimatearchive, geparkt)
                                  + relations.csv  (00-archimatearchive, geparkt)

Manuell: Archi Import → elements.csv → IDs vergeben
         Archi CSV Export → 04-import\elements.csv (mit IDs)

ECM03   ID-Merge → properties.csv + relations.csv (04-import, mit IDs)

Manuell: Archi Import → properties.csv + relations.csv

CLE26   (optional) Zwischenartefakte bereinigen

→ Elemente stabil im Modell, IDs vergeben, Properties korrekt zugewiesen
→ Ab hier XML-Reihe nutzbar wenn OEF-Export gewünscht
```


================================================================================
7. KRITISCHE REGEL — REIHENFOLGE-JOIN
================================================================================

Element-Namen DÜRFEN zwischen ECM02-Import (Stufe 1) und ECM03-Lauf
NICHT in Archi verändert werden.

Begründung: ECM03 matcht Properties via Reihenfolge — Zeile N in
properties.csv gehört zu Zeile N in elements.csv (pro Typ-Gruppe).
Archi exportiert in Importreihenfolge solange keine Umbenennung erfolgt.

Konsequenz bei Verletzung: falsche Properties am falschen Element — kein
Fehler sichtbar, aber falsche Daten im Modell.

Empfehlung: Nach vollständigem ECM03-Lauf und Validierung umbenennen.


================================================================================
8. ERGEBNIS DES SPRINTS
================================================================================

8.1 Erreichter Zustand
-----------------------
Vollständige ECM-Reihe (ECM00–ECM03) implementiert und produktiv getestet.
Erstmaliger erfolgreicher Import einer externen CSV (trash_test.csv,
cp1252-kodiert, Semikolon-getrennt, Excel-Export) in das ArchiMate-Modell
mit korrekter Typ-Zuweisung und Property-Zuordnung.

Entstandene Artefakte:
  ECM00-validate_environment.py      01-artifacts\01-scripts\
  ECM01-csv_fields_to_artifacts.py   01-artifacts\01-scripts\
  ECM02-csv_to_mapping_to_csv.py     01-artifacts\01-scripts\
  ECM03-id_merge.py                  01-artifacts\01-scripts\
  trash_test.xml                     00-model\00-archimate\99-mappingmodel\

Geänderter Systemzustand:
  99-mappingmodel\ erstmals mit normativem Inhalt befüllt.
  ECM-Reihe als neuer eigenständiger Flow etabliert.
  run-scope.txt Format additiv um MAPPING= erweitert.


8.2 Abweichungen vom Plan
--------------------------
  Konzept-Phase länger als erwartet → Entscheidungen zu Extension (.txt vs .cfg),
  Ablageort easycsvmapping.txt, und run-scope.txt Format wurden mehrfach
  iteriert. Keine funktionale Abweichung — nur konzeptionelle Iterationen
  vor der Umsetzung.

  easycsvmapping.txt vollständig weggefallen → MAPPING= in run-scope.txt
  referenziert OEF-Dateinamen direkt. Einfacher und konsistenter.


================================================================================
9. TEST UND VALIDIERUNG
================================================================================

| Prüfpunkt                                              | Ergebnis | Anmerkung                    |
|--------------------------------------------------------|----------|------------------------------|
| ECM00 läuft sauber durch                               | OK       | Produktiv getestet           |
| ECM01 erkennt cp1252 + Semikolon korrekt               | OK       | trash_test.csv               |
| ECM01 bricht bei mehreren trash_*.csv ab               | OK       | Fehlermeldung korrekt        |
| ECM01 schreibt elements.csv (Archi-importfertig)       | OK       | Archi-Import erfolgreich     |
| ECM02 liest OEF + wertet Associations korrekt aus      | OK       | trash_test.xml               |
| ECM02 trennt Elemente vs. Properties korrekt           | OK       | Laut OEF-Mapping             |
| ECM02 schreibt elements.csv nach 04-import             | OK       | Archi-Import erfolgreich     |
| ECM02 parkt properties.csv in 00-archimatearchive      | OK       | ID-los, korrekt geparkt      |
| ECM03 merged IDs korrekt via Reihenfolge-Join          | OK       | Properties am richtigen Elem |
| ECM03 schreibt properties.csv nach 04-import           | OK       | Archi-Import erfolgreich     |
| Properties im Modell korrekt zugewiesen                | OK       | Visuell in Archi bestätigt   |
| Alle Stage-3/4/5-Scripts logisch unverändert           | OK       | Kein Eingriff                |
| Kein unbeabsichtigter Seiteneffekt                     | OK       | Additiver Sprint             |

Testmethode: Manueller Durchlauf mit trash_test.csv (Excel-Export, cp1252)
Log-Referenz: 02-stages\99-logs\ECM00–ECM03 Logs


================================================================================
10. OFFENE PUNKTE NACH SPRINT-ABSCHLUSS
================================================================================

| Thema                                    | Status          | Nächste Aktion                      |
|------------------------------------------|-----------------|-------------------------------------|
| Property Definitions automatisieren      | Zurückgestellt  | jArchi Sprint                       |
| Relations-Mapping implementieren         | Zurückgestellt  | ECM-Erweiterung wenn Bedarf         |
| ECM02/03 Hilfsfunktionen in HLP auslagern| Zurückgestellt  | Cleaning Run                        |
| Mehrere trash_*.csv pro Lauf             | Kein Bedarf     | Bewusst 1 Datei pro Lauf            |
| run-scope.txt MAPPING= via CSV04         | Zurückgestellt  | SPRINT-CSV-Refactoring              |


================================================================================
11. GOVERNANCE-KONFORMITÄTSCHECK
================================================================================

| GOV-Kriterium                              | Status | Anmerkung                             |
|--------------------------------------------|--------|---------------------------------------|
| GOV 10.3  Auslöser zulässig               | OK     | Feature-Zuwachs (Entwicklerwunsch)    |
| GOV 10.5  Fachlicher Mehrwert benennbar   | OK     | Externer CSV-Import in Modell möglich |
| GOV 10.5  Keine implizite GOV-Änderung    | OK     | Additiv — keine GOV-Regeländerung     |
| GOV 10.6  Ziel explizit definiert         | OK     | Kapitel 3                             |
| GOV 10.6  Ziel überprüfbar               | OK     | Kapitel 9                             |
| GOV 10.7  Zwischenschritte dokumentiert   | OK     | Kapitel 6                             |
| GOV 10.8  Dev-Doku vollständig            | OK     | Dieses Dokument                       |
| GOV 10.9  Stage-Ende Doku                 | OFFEN  | Fällig bei Stage-6-Abschluss          |
| GOV 10.10 Keine GOV-Regel aufgehoben      | OK     | Keine GOV-Änderung                    |
| Rückkopplungsschutz eingehalten           | OK     | Stage-3/4/5 unberührt                 |
| run-scope.txt GOV-Schutz eingehalten      | OK     | Nur additiv erweitert                 |


================================================================================
12. LESSONS LEARNED
================================================================================

12.1 Was gut funktioniert hat
------------------------------
  - OEF als Mapping-Modell — visuell in Archi baubar, maschinenlesbar,
    kein proprietäres Format nötig
  - Association-Semantik für Element vs. Property — einfach, deterministisch,
    universell in ArchiMate zulässig
  - Auto-Encoding + Auto-Trennzeichen Erkennung — funktioniert ohne
    manuelle Konfiguration auch für "schmutzige" Excel-Exporte
  - Zweistufiger Import mit Parking-Pattern — sauber, nachvollziehbar,
    ohne Archi-interne Tricks

12.2 Was beim nächsten Mal anders gemacht werden sollte
--------------------------------------------------------
  - Konzept-Entscheidungen (Extension, Ablageort, Lookup-Mechanismus)
    früher finalisieren bevor Code geschrieben wird — die Iterationen
    haben Zeit gekostet
  - Hilfsfunktionen (Encoding, OEF-Parser) von Anfang in HLP planen
    wenn sie in mehreren Scripts benötigt werden

12.3 Erkenntnisse für das System
----------------------------------
  - 99-mappingmodel\ ist jetzt definierter Ablageort für OEF Mapping-Modelle
    → Konsequenz: zukünftige Mapping-Erweiterungen haben einen festen Ort
  - Reihenfolge-Join ist fragil bei Umbenennungen in Archi
    → Konsequenz: GOV-Regel dokumentiert, jArchi-Automatisierung als
      Folge-Sprint definiert
  - Property Definitions müssen vor Properties vorhanden sein
    → Konsequenz: jArchi Sprint für Automatisierung geplant
  - Script-Länge ~300 Zeilen für ECM02/ECM03 ist grenzwertig
    → Konsequenz: Cleaning Run — gemeinsame Funktionen in HLP auslagern


================================================================================
13. BEZÜGE UND VERLINKUNGEN
================================================================================

Ausgangspunkt:
  [[FREEZE-6]]                          Baseline für diesen Sprint

Entstanden:
  Sprint-DEV-EasyMapper_S6.md          Dieses Dokument
  ECM00-validate_environment.py        01-artifacts\01-scripts\
  ECM01-csv_fields_to_artifacts.py     01-artifacts\01-scripts\
  ECM02-csv_to_mapping_to_csv.py       01-artifacts\01-scripts\
  ECM03-id_merge.py                    01-artifacts\01-scripts\
  trash_test.xml                       00-model\00-archimate\99-mappingmodel\

Verwandte Dokumente:
  [[GOV_Global_S5]]                     normative Grundlage
  [[STAGE6_ZIELE]]                      Stage-Rahmen S6-Z5 (Blueprint-Reifung)
  [[CSV_FLOW_principles_S3]]            bestehende CSV-Logik (read-only)
  [[FREEZE-6]]                          Script-Konventionen, Ordnerstruktur

Folge-Sprints (definiert, nicht gestartet):
  jArchi Property Definitions           Automatisierung manueller Archi-Schritte
  ECM Cleaning Run                      HLP-Auslagerung gemeinsamer Funktionen
  ECM Relations                         Relations-Mapping wenn Bedarf entsteht

Creative-Assets:
  Keine Creative-Assets für diesen Sprint.


================================================================================
Sprint-DEV-EasyMapper_S6 | S6 | 2026-03-21 | R+MUNI Blueprint
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
