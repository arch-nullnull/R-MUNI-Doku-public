================================================================================
FLOW_SCRIPTRUNNER – HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : FLOW_SCRIPTRUNNER_How2_S105
Tag             : #dev #how2 #flowscriptrunner #flw #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-02
Letzte Änderung : 2026-04-14 — S105-Update | root.txt → root.cfg, Pfade auf
                               01-artifacts / 02-stages, scriptTask ergänzt,
                               Order-Baseline aktualisiert, Flow-Ordner korrigiert
Ablageort       : 02-how2\FLOW_SCRIPTRUNNER_How2_S105.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- Python 3.10+
- root.cfg vorhanden und <rootfolder> korrekt eingetragen
- flowtriggers.txt und flowmapping.txt vorhanden in:
    01-artifacts\04-flow\
- Flow-Dateien abgelegt in:
    01-artifacts\04-flow\00-archimateFLW\   (ArchiMate)
    01-artifacts\04-flow\01-bpmnFLW\        (BPMN)
- Scripts aller Reihen liegen in:
    01-artifacts\01-scripts\


================================================================================
FLW00 – SCRIPTRUNNER STARTEN
================================================================================

  cd 01-artifacts\04-flow\
  python FLW00-scriptrunner.py

  root.cfg wird automatisch zwei Ebenen aufwärts gesucht.
  Log: 02-stages\99-logs\flw00-scriptrunner.log (append)


WAS FLW00 IN DER KONSOLE AUSGIBT
--------------------------------------------------------------------------------
  [FLW00] ... | Blueprint root resolved: <pfad>
  [FLW00] ... | Loaded N mapping entries
  [FLW00] ... | Loaded N trigger rule(s) (order: 10, 20, 30)
  [FLW00] ... | SCAN [bpmn]:  01-artifacts\04-flow\01-bpmnFLW\MeinFlow.bpmn
  [FLW00] ... |   TRIGGER [order=20] [bpmn_scripttask] key=CSV05-create_master_csvs.py info=Master CSVs
  [FLW00] ... |   TRIGGER [order=30] [bpmn_servicetask] key=Activity_0oba9ny info=Validate Env
  [FLW00] ... | SCAN [archi]: 01-artifacts\04-flow\00-archimateFLW\mini.xml
  [FLW00] ... |   TRIGGER [order=10] [archi_workpackage] key=Script info=id-abc
  [FLW00] ... | Detected N trigger(s)
  [FLW00] ... | Execution order: Script(order=10), CSV05-create_master_csvs.py(order=20), ...
  [FLW00] ... | EXEC: ...\01-artifacts\01-scripts\CSV00-validate_environment.py
  [FLW00] ... | FLW00 finished: executed=3, total_triggers=3


WICHTIG – FLOW-ORDNER SIND DIE QUELLE
--------------------------------------------------------------------------------
FLW00 scannt NUR die beiden Flow-Ordner:
  01-artifacts\04-flow\00-archimateFLW\
  01-artifacts\04-flow\01-bpmnFLW\

Dateien in 01-artifacts\00-xml\03-child\ werden von FLW00 nicht ausgeführt.
Für den FLW muss die BPMN- oder ArchiMate-Datei in den richtigen Flow-Ordner.


================================================================================
FLW01 – DISCOVER STARTEN
================================================================================

  python FLW01-discover.py

  Zeigt welche Element-Typen und Tags in 01-artifacts\00-xml\03-child\
  vorhanden sind und ob sie bereits in flowtriggers.txt konfiguriert sind.

  Ausgabe:
    02-stages\99-logs\flw01-discover.log   (detailliert, mit Fundorten)
    02-stages\flw01-discover.txt           (kompakt, Referenz)

  Wann verwenden:
  - Neue XML/BPMN-Dateien wurden in 03-child abgelegt
  - Prüfen ob alle Typen in flowtriggers.txt erfasst sind
  - Vor dem Anlegen neuer Trigger-Regeln

  HINWEIS: FLW01 scannt 01-artifacts\00-xml\03-child\ — nicht die Flow-Ordner.
  Er ist ein Typ-Inventar für die gesamte Modell-Ausgabe, kein FLW00-Vorlauf.


================================================================================
FLW02 – MAP_ELEMENTS STARTEN
================================================================================

  python FLW02-map_elements.py

  Scannt die Flow-Ordner und gibt alle Elemente mit ID + Name + Typ aus
  — als fertige Referenz für flowmapping.txt.

  Ausgabe:
    02-stages\99-logs\flw02-map_elements.log
    02-stages\flw02-map_elements.txt

  Wann verwenden:
  - flowmapping.txt befüllen oder aktualisieren (serviceTask)
  - Nach Änderungen im BPMN-Modell (neue Tasks, geänderte IDs)
  - Prüfen welche serviceTask IDs mit Trigger:Ja vorhanden sind
  - Prüfen welche scriptTask-Elemente vorhanden und ob documentation gefüllt ist


================================================================================
FLOWTRIGGERS.TXT – KONFIGURATION
================================================================================

  Datei: 01-artifacts\04-flow\flowtriggers.txt
  Format: INI (configparser kompatibel)

  Sektion ArchiMate WorkPackage:
    [archi_workpackage]
    order        = 10
    source       = archi
    element_tag  = element
    element_type = WorkPackage
    condition.1  = property:Trigger=Ja
    dispatch_key = property:Type

  Sektion BPMN scriptTask (Wildcard — kein condition, kein dispatch_key):
    [bpmn_scripttask]
    order        = 20
    source       = bpmn
    element_tag  = scriptTask
    # keine condition  → Wildcard: jeder scriptTask wird erkannt
    # kein dispatch_key → <documentation>-Inhalt ist direkt der Scriptname

  Sektion BPMN serviceTask:
    [bpmn_servicetask]
    order        = 30
    source       = bpmn
    element_tag  = serviceTask
    condition.1  = tag:documentation:Trigger:Ja
    dispatch_key = attr:id

  Pflichtfelder    : order, source, element_tag
  Pflicht (außer   : mind. eine condition (nicht bei scriptTask)
  scriptTask)
  Pflicht (außer   : dispatch_key (nicht bei scriptTask)
  scriptTask)
  Optional         : element_type (nur Archi, filtert xsi:type)
  Kommentare       : Zeilen die mit # beginnen werden ignoriert


================================================================================
FLOWMAPPING.TXT – KONFIGURATION
================================================================================

  Datei: 01-artifacts\04-flow\flowmapping.txt
  Format: <dispatch_key>=<script_dateiname.py>

  Beispiele:
    Script=CSV02-leer.py
    Activity_0oba9ny=CSV00-validate_environment.py

  Regeln:
  - Kein doppelter Key erlaubt (ABORT)
  - Script-Name ohne Pfad – FLW00 sucht in 01-artifacts\01-scripts\
  - Script muss vorhanden sein – fehlendes Script → ABORT
  - Unmapped dispatch_key → SKIP (kein Abbruch, wird geloggt)
  - Reihenfolge der Einträge egal – Ausführungsreihenfolge kommt aus order

  HINWEIS: scriptTask-Einträge gehören NICHT in flowmapping.txt.
  FLW00 holt den Scriptnamen direkt aus <documentation> — kein Lookup.

  Empfehlung: flowmapping.txt nicht manuell befüllen.
  Stattdessen FLW02 verwenden → Abschnitt 1 aus flw02-map_elements.txt
  direkt kopieren.


================================================================================
SCRIPTRUNNER MODELL-MODELL-TYPEN – KURZÜBERSICHT
================================================================================

  Element       | Trigger-Bedingung        | Scriptname kommt aus    | flowmapping.txt?
  --------------|--------------------------|-------------------------|------------------
  scriptTask    | immer (Wildcard)         | <documentation>         | NEIN
  serviceTask   | documentation=Trigger:Ja | flowmapping.txt (attr:id)| JA
  WorkPackage   | property:Trigger=Ja      | flowmapping.txt (property:Type) | JA
  andere        | —                        | —                        | —


================================================================================
NEUEN TRIGGER ANLEGEN – SCHRITT FÜR SCHRITT
================================================================================

── VARIANTE A — BPMN scriptTask (Wildcard) ──────────────────────────────────

  Einfachste Variante: kein flowmapping.txt-Eintrag nötig.

  SCHRITT 1 – Camunda Modeler
    scriptTask anlegen oder öffnen
    name           = beliebige lesbare Bezeichnung (z.B. "CSVs erstellen")
    documentation  = CSV05-create_master_csvs.py   ← Scriptname direkt hier

  SCHRITT 2 – BPMN-Datei ablegen
    Datei speichern nach:
    01-artifacts\04-flow\01-bpmnFLW\

  SCHRITT 3 – flowtriggers.txt prüfen
    Sektion [bpmn_scripttask] bereits vorhanden? → fertig, direkt zu Schritt 4.
    Neue Sektion nur anlegen wenn scriptTask noch nicht konfiguriert ist.

  SCHRITT 4 – FLW00 ausführen und prüfen
    python FLW00-scriptrunner.py
    02-stages\99-logs\flw00-scriptrunner.log prüfen


── VARIANTE B — BPMN serviceTask (Trigger:Ja) ───────────────────────────────

  SCHRITT 1 – Camunda Modeler
    serviceTask anlegen oder öffnen
    name           = CSV01-validate_model.py   ← Scriptname als Task-Name
    documentation  = Trigger:Ja

  SCHRITT 2 – BPMN-Datei ablegen
    Datei speichern nach:
    01-artifacts\04-flow\01-bpmnFLW\

  SCHRITT 3 – flowtriggers.txt prüfen
    Sektion [bpmn_servicetask] bereits vorhanden? → weiter mit Schritt 4.
    Neue Sektion anlegen falls neuer Element-Typ:
      FLW01-discover.py ausführen → flw01-discover.txt prüfen
      Neue Sektion in flowtriggers.txt ergänzen.

  SCHRITT 4 – FLW02 ausführen
    python FLW02-map_elements.py
    flw02-map_elements.txt öffnen
    Abschnitt 1 kopieren → in flowmapping.txt einfügen.

  SCHRITT 5 – FLW00 ausführen und prüfen
    python FLW00-scriptrunner.py
    02-stages\99-logs\flw00-scriptrunner.log prüfen


================================================================================
HÄUFIGE FEHLER UND LÖSUNGEN
================================================================================

Fehler: "flowtriggers.txt not found"
  Datei in 01-artifacts\04-flow\ anlegen oder root.cfg prüfen.

Fehler: "flowmapping.txt not found"
  Datei in 01-artifacts\04-flow\ anlegen.

Fehler: "mapped script not found"
  Script in flowmapping.txt eingetragen aber Datei fehlt in
  01-artifacts\01-scripts\ → Script-Datei prüfen.

Fehler: "[section] order is required"
  order = <Zahl> in der betroffenen flowtriggers.txt-Sektion ergänzen.

Fehler: "script failed"
  Script direkt ausführen und Fehler analysieren.
  Das Script selbst schreibt Details in sein eigenes Logfile.

FLW00 erkennt keine Trigger (Detected 0 trigger(s))
  1. Flow-Dateien nicht in 01-artifacts\04-flow\00-archimateFLW\ bzw. \01-bpmnFLW\?
     → Dateien in den richtigen Flow-Ordner legen
  2. element_tag stimmt nicht überein?
     → FLW01 ausführen um vorhandene Tags in 03-child zu sehen
  3. condition nicht erfüllt?
     → documentation / Property direkt im Modell prüfen
  4. dispatch_key liefert leeren Wert?
     → id-Attribut / Property im Modell prüfen

FLW02 findet keine BPMN-Dateien
  01-artifacts\04-flow\01-bpmnFLW\ ist leer.
  → BPMN-Flow-Dateien in diesen Ordner kopieren (nicht nach 03-child).

FLW02 Warnung: "Trigger:Ja aber kein Scriptname"
  serviceTask hat Trigger:Ja aber keinen name-Wert.
  → Im Camunda Modeler Scriptnamen als Task-Name eintragen.
  → FLW02 erneut ausführen.

FLW02 Warnung: "scriptTask ohne documentation"
  scriptTask hat keine <documentation> → wird von FLW00 als SKIP behandelt.
  → Im Camunda Modeler documentation mit Scriptnamen befüllen.
  → FLW02 erneut ausführen.

scriptTask wird ausgeführt obwohl ich das nicht will
  Der Wildcard-Modus gilt für ALLE scriptTask-Elemente in den Flow-Ordnern.
  Lösung: documentation leer lassen → SKIP (kein Fehler).
  Oder: Datei aus dem Flow-Ordner entfernen.


================================================================================
ORDER-WERTE – EMPFEHLUNGEN
================================================================================

  Empfohlene Staffelung:
    10, 20, 30 ... → grobe Schritte zwischen Trigger-Gruppen
    11, 12, 13 ... → Feinschritte innerhalb einer Gruppe

  Aktuelle Baseline (S105):
    order=10 → archi_workpackage  (ArchiMate WorkPackage Trigger)
    order=20 → bpmn_scripttask    (BPMN scriptTask Wildcard)
    order=30 → bpmn_servicetask   (BPMN serviceTask Trigger:Ja)

  Neue Trigger ab order=40 aufwärts vergeben.


================================================================================
ABLAGE DER FLW-SERIE
================================================================================

  Scripts (liegen direkt im Flow-Ordner):
    01-artifacts\04-flow\FLW00-scriptrunner.py
    01-artifacts\04-flow\FLW01-discover.py
    01-artifacts\04-flow\FLW02-map_elements.py

  Konfiguration:
    01-artifacts\04-flow\flowtriggers.txt
    01-artifacts\04-flow\flowmapping.txt

  Flow-Dateien (Quellen für FLW00 und FLW02):
    01-artifacts\04-flow\00-archimateFLW\    ArchiMate-Flows
    01-artifacts\04-flow\01-bpmnFLW\         BPMN-Flows

  Ausgaben von FLW01 und FLW02 (generiert, nicht manuell bearbeiten):
    02-stages\flw01-discover.txt
    02-stages\flw02-map_elements.txt

  Logs (generiert, append):
    02-stages\99-logs\flw00-scriptrunner.log
    02-stages\99-logs\flw01-discover.log
    02-stages\99-logs\flw02-map_elements.log


================================================================================
BEZÜGE
================================================================================

[[FLOW_SCRIPTRUNNER_principles_S105]]   Leitprinzipien und Designentscheidungen
[[naming_and_structure_S104]]           Namenskonvention Scripts
[[Global_GOV_DEV_S102]]                Normative Grundlage


================================================================================
FLW-SERIE – HOW2 | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
