================================================================================
FLOW_SCRIPTRUNNER – PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : FLOW_SCRIPTRUNNER_principles_S105
Tag             : #dev #principles #flowscriptrunner #flw #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-02
Letzte Änderung : 2026-04-14 — S105-Update | scriptTask-Sonderregel ergänzt,
                               Scan-Ordner korrigiert, Order-Baseline aktualisiert,
                               Pfade auf 01-artifacts / 02-stages angepasst
Ablageort       : 01-principles\FLOW_SCRIPTRUNNER_principles_S105.md
================================================================================


1. ZWECK UND DESIGNPHILOSOPHIE
--------------------------------------------------------------------------------
Die FLW-Serie ist der modellgetriebene Orchestrator des Blueprints.
Sie verbindet ArchiMate-Arbeitspakete und BPMN-Tasks mit konkreten
Python-Scripts – ohne Hardcoding, ohne Engine-Semantik.

Kernprinzip: Das Modell entscheidet was läuft. Der Mensch entscheidet wann.
FLW00 fragt nicht – FLW00 führt aus was das Modell sagt, wenn du es startest.

FLW00 ist kein Scheduler, kein Trigger-System, keine Automatisierungslösung.
Es ist die Sichtbarmachung impliziter Abläufe als ausführbare Sequenz.
MUNI ist die Stufe VOR der Automatisierung.


2. FLW-SERIE – ÜBERSICHT UND AUFGABENTRENNUNG
--------------------------------------------------------------------------------
Die FLW-Serie besteht aus drei Scripts und zwei Konfigurationsfiles:

FLW00-scriptrunner.py  (Orchestrator)
  Liest flowtriggers.txt und flowmapping.txt.
  Scannt die Flow-Ordner (BPMN und ArchiMate getrennt), erkennt Trigger,
  führt gemappte Scripts aus.
  Das einzige Script das andere Scripts startet.

FLW01-discover.py  (Typ-Scanner)
  Zeigt welche xsi:type-Werte und BPMN-Tags in den Quelldateien vorhanden sind.
  Zeigt ob diese bereits in flowtriggers.txt konfiguriert sind.
  Verändert nichts. Referenz für: flowtriggers.txt
  HINWEIS: FLW01 scannt 01-artifacts\00-xml\03-child\ — nicht die Flow-Ordner.

FLW02-map_elements.py  (Element-ID-Scanner)
  Zeigt welche konkreten Elemente (ID + Name + Typ) in den Flow-Ordnern sind.
  serviceTask mit Trigger:Ja + Scriptname als Name → fertige Mapping-Zeile.
  scriptTask mit documentation-Inhalt → Scriptname direkt (Wildcard-Modus).
  Verändert nichts. Referenz für: flowmapping.txt

flowtriggers.txt  (Detection-Konfiguration)
  Definiert welche Modellelemente als Trigger erkannt werden.
  Kein Script-Name hier.

flowmapping.txt  (Dispatch-Konfiguration)
  Verbindet dispatch_key mit Script-Name.
  Kein Modell-Kontext hier.
  Nicht relevant für scriptTask — scriptTask nutzt Documentation-Dispatch.


3. DREI-PHASEN-MODELL (FLW00)
--------------------------------------------------------------------------------
Phase 1 – SCAN:
  Alle XML/BPMN/Archimate-Dateien in den Flow-Ordnern werden gescannt:
    01-artifacts\04-flow\00-archimateFLW\  (ArchiMate-Flows)
    01-artifacts\04-flow\01-bpmnFLW\       (BPMN-Flows)
  Für jede Datei werden Trigger gemäß flowtriggers.txt erkannt.
  Ergebnis: Liste aller Trigger mit order-Wert.
  Fehlt ein Ordner → SKIP mit Log, kein Abbruch.

Phase 2 – SORT:
  Alle gesammelten Trigger werden nach dem order-Wert sortiert.
  Die order-Reihenfolge ist die einzige garantierte Ausführungsreihenfolge.
  Dateisystem-Reihenfolge, Modell-Reihenfolge, Fundort – alles irrelevant.

Phase 3 – EXEC:
  Scripts werden in order-Reihenfolge via subprocess ausgeführt.
  CWD ist immer BLUEPRINT_ROOT (aus root.cfg).
  returncode != 0 → ABORT. Kein Script nach einem Fehler.


4. SCAN-ORDNER – TRENNUNG FLW00/FLW02 vs. FLW01
--------------------------------------------------------------------------------
FLW00 und FLW02 scannen ausschließlich die dedizierten Flow-Ordner:

  01-artifacts\04-flow\00-archimateFLW\   ArchiMate-Flow-Dateien
  01-artifacts\04-flow\01-bpmnFLW\        BPMN-Flow-Dateien

FLW01 scannt demgegenüber den XML-Kindordner:
  01-artifacts\00-xml\03-child\

Diese Trennung ist bewusst: FLW01 ist ein Typ-Inventar über die gesamte
Modell-Ausgabe. FLW00 und FLW02 operieren nur auf den expliziten Flow-Dateien.

Konsequenz: Eine Datei muss in den Flow-Ordner abgelegt werden,
damit FLW00 sie erkennt und ausführt. Dateien in 00-xml\03-child\
werden von FLW00 nicht berücksichtigt.


5. KONFIGURATIONSTRENNUNG
--------------------------------------------------------------------------------
Zwei separate Konfigurationsfiles mit klar getrennten Aufgaben:

flowtriggers.txt (Detection):
  Definiert WELCHE Modellelemente als Trigger erkannt werden.
  Format: INI-Sektionen mit order, source, element_tag, element_type,
          conditions, dispatch_key.
  Kein Script-Name hier.

flowmapping.txt (Dispatch):
  Verbindet dispatch_key mit Script-Name.
  Format: <dispatch_key>=<script_dateiname.py>
  Kein Modell-Kontext hier.

Konsequenz: Ein dispatch_key der in flowmapping.txt nicht vorkommt
→ SKIP (mit Log), kein Abbruch.
Ein Script in flowmapping.txt das nicht gefunden wird → ABORT.


6. DETECTION-ENGINE: ARCHI vs. BPMN
--------------------------------------------------------------------------------
Archi-Detection (source=archi):
  Arbeitet mit Property-Indirektion. Archi OEF speichert Property-Namen
  in <propertyDefinition> Elementen und referenziert sie via
  propertyDefinitionRef. FLW00 baut zuerst einen propdefs-Index auf
  (id → name Mapping), dann liest er Properties der Elemente.

  Voraussetzung für Archi-Trigger:
  - element_tag matcht lokalen Tag-Namen des Elements
  - element_type matcht xsi:type Attribut (wenn konfiguriert)
  - ALLE conditions erfüllt (AND-Verknüpfung)
  - dispatch_key liefert nicht-leeren Wert

BPMN-Detection (source=bpmn):
  Liest Kind-Elemente direkt (keine Indirektion).
  condition.tag: prüft ob ein Kind-Element mit gegebenem Tag-Namen
  den gesuchten Text enthält.

  Voraussetzung für BPMN-Trigger:
  - element_tag matcht lokalen Tag-Namen des Tasks
  - ALLE conditions erfüllt (AND-Verknüpfung)
  - dispatch_key via attr: (meist id-Attribut) — außer scriptTask


7. ORDER-PRINZIP
--------------------------------------------------------------------------------
order ist ein Integer in jeder flowtriggers.txt-Sektion. Er bestimmt
ausschließlich die globale Ausführungsreihenfolge aller erkannten Trigger –
über alle Dateien und alle Modelltypen hinweg.

Gleiche order-Werte zwischen Sektionen sind zulässig aber nicht empfohlen
(Reihenfolge bei Gleichstand undefiniert).

Wichtig: order hat NICHTS mit der Position im Modell zu tun. Ein WorkPackage
das im Archi-Diagramm "oben links" steht läuft nicht vor einem das "unten
rechts" steht – es läuft in der Reihenfolge seines order-Werts.

Aktuelle Baseline (S105):
  order=10 → archi_workpackage  (ArchiMate WorkPackage Trigger)
  order=20 → bpmn_scripttask    (BPMN scriptTask Wildcard-Trigger)
  order=30 → bpmn_servicetask   (BPMN serviceTask Trigger:Ja)

  Neue Trigger ab order=40 aufwärts vergeben.


8. CONDITION-AUSWERTUNG
--------------------------------------------------------------------------------
Alle conditions in einer Sektion werden AND-verknüpft ausgewertet.
Ein Element triggert nur wenn ALLE conditions erfüllt sind.

Archi condition-Typen:
  property:<n>=<Wert>
    Prüft ob das Element eine Property mit Name=<n> und Wert=<Wert> hat.

BPMN condition-Typen:
  tag:<TagName>:<Text>
    Prüft ob ein Kind-Element mit lokalem Tag <TagName> den Text <Text> enthält.

Sonderfall scriptTask:
  Keine condition erforderlich — scriptTask läuft im Wildcard-Modus.
  Jeder scriptTask wird als ausführbar behandelt, solange seine
  <documentation> nicht leer ist (leere documentation → SKIP, kein Abbruch).


9. DISPATCH-KEY PRINZIP
--------------------------------------------------------------------------------
Der dispatch_key ist der Schlüssel den FLW00 nach Erkennung eines Triggers
in flowmapping.txt nachschlägt.

Archi dispatch_key Typen:
  property:<PropertyName>  → Wert der genannten Property des Elements
  attr:<Attributname>      → Wert des genannten XML-Attributs

BPMN dispatch_key Typen (serviceTask):
  attr:<Attributname>      → Wert des genannten XML-Attributs (meist "id")

BPMN scriptTask – KEIN dispatch_key:
  scriptTask hat keinen dispatch_key in flowtriggers.txt.
  FLW00 liest den <documentation>-Inhalt direkt als Scriptnamen.
  Kein flowmapping.txt-Lookup – der documentation-Inhalt ist der Scriptname.

Ist der dispatch_key leer (Property nicht vorhanden, Attribut fehlt) →
Trigger wird ignoriert, kein Abbruch.


10. BPMN ELEMENT-TYPEN UND IHRE TRIGGER-MECHANIK
--------------------------------------------------------------------------------
serviceTask (Sonderregel 1 — seit S4):
  Trigger-Erkennung: <documentation> enthält "Trigger:Ja"
  dispatch_key: attr:id → Wert wird in flowmapping.txt nachgeschlagen
  Scriptname: kommt aus flowmapping.txt (id=Scriptname.py)
  FLW02-Ausgabe: fertige flowmapping.txt-Zeile (id=name-Attribut)
  Voraussetzung im Modell: name=Scriptname, documentation=Trigger:Ja

scriptTask (Sonderregel 2 — Wildcard, seit S5):
  Trigger-Erkennung: jeder scriptTask wird erkannt (kein condition nötig)
  dispatch_key: keiner — documentation-Inhalt wird direkt als Scriptname verwendet
  Scriptname: kommt direkt aus <documentation>
  Leer = SKIP (Warnung in Konsole und Log, kein Abbruch)
  name-Attribut: frei verwendbar für lesbare Bezeichnung im Diagramm
  Kein flowmapping.txt-Eintrag nötig

Alle anderen Element-Typen (userTask, sendTask etc.):
  Erscheinen in FLW02-Ausgabe nur als auskommentierte Referenz.
  Kein automatisches Dispatch.


11. FLW01 UND FLW02 ALS BEGLEITWERKZEUGE
--------------------------------------------------------------------------------
Beide Tools sind eigenständig – sie importieren nichts aus FLW00.
Beide verändern nichts – sie sind reine Lesewerkzeuge.
Beide schreiben nach 02-stages\ – nie in die Quelldateien.

FLW01 → Referenz für flowtriggers.txt
  Frage: Welche Typen/Tags sind vorhanden und konfiguriert?

FLW02 → Referenz für flowmapping.txt
  Frage: Welche IDs/Namen haben die konkreten Elemente?

Empfohlene Reihenfolge beim Aufsetzen neuer Trigger:
  FLW01 ausführen → flowtriggers.txt anpassen
  FLW02 ausführen → flowmapping.txt befüllen (serviceTask)
  FLW00 ausführen → Ergebnis prüfen


12. GRENZEN DER FLW-SERIE
--------------------------------------------------------------------------------
- Keine parallele Ausführung – strikt sequenziell
- Kein Retry bei Fehler – ein fehlgeschlagenes Script stoppt alles
- Kein Rollback – bereits ausgeführte Scripts werden nicht rückgängig gemacht
- Kein Scheduling – FLW00 startet nur wenn manuell aufgerufen
- Kein Monitoring – nur Log-Datei als Rückmeldung
- Versteht keine Modellsemantik – erkennt Tags und Properties, nicht Bedeutung
- Scripts werden als Kindprozesse gestartet – kein gemeinsamer Zustand
- scriptTask Wildcard gilt für ALLE scriptTask-Elemente in den Flow-Ordnern
- serviceTask ohne Trigger:Ja wird nicht ausgeführt, erscheint nur als Referenz
- FLW01 scannt nicht die Flow-Ordner – nur 01-artifacts\00-xml\03-child\


================================================================================
BEZÜGE
================================================================================

[[FLOW_SCRIPTRUNNER_How2_S105]]      Operative Kurzreferenz und Anwendungsfälle
[[naming_and_structure_S104]]        Namenskonvention Scripts
[[Global_GOV_DEV_S102]]              Normative Grundlage


================================================================================
FLW-SERIE – PRINCIPLES | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
