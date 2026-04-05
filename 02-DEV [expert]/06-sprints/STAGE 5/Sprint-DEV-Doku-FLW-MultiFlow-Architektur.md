================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-FLW-MultiFlow-Architektur
Datum               : 2026-03-16
Stage               : 5 (aktiv)
Status              : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch      : EUMAXL + Claude (Pair-Session)
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Stage-Modell (Ist-Zustand)
-------------------------------
Stage 4  FREEZE
         FLW00/01/02 entstammen Stage 4, wurden im Cleaning Run 5.5
         auf Stage-5-Konventionen gebracht. Kernlogik unverändert.

Stage 5  AKTIV
         BPMN Default Flows schrittweise abbilden ist explizites
         Stage-5-Ziel (STAGE5_ZIELE.md 4.7).
         Dieser Sprint legt die architektonische Basis dafür.

1.2 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Architekturerweiterung Stage 5 (additiv)

Begründung   : Die bestehende FLW-Reihe (FLW00/01/02) kann technisch
               nur einen einzigen, flachen Flow abarbeiten. Die
               flowmapping.txt ist ein gemeinsamer, ungetrennter
               Dispatch-Namespace für alle denkbaren Flows. Ein
               gezieltes Starten eines definierten, benannten Flows
               (z.B. "nur CSV-Flow", "nur XML-Flow") ist nicht möglich.

               Weiters verwendet die bisherige BPMN-Konfiguration
               "serviceTask" als Trigger — semantisch korrekt für
               externe Web-Service-Aufrufe, aber unpassend für die
               direkte Python-Script-Ausführung, die in R+MUNI
               stattfindet. BPMN 2.0 (OMG) definiert "scriptTask"
               explizit für den Fall dass eine Engine ein Script
               direkt ausführt — was exakt dem R+MUNI Modell entspricht.

               Im Gespräch wurde darüber hinaus eine 3-Ebenen-Architektur
               entwickelt die es ermöglicht, Flows als fixierte BPMN-Files
               zu speichern, gezielt zu starten und bei Bedarf über einen
               Meta-Flow zu orchestrieren.

Fachlicher   : Mehrere benannte, isolierte Flows werden möglich.
Mehrwert       Jeder Flow ist ein eigenständiges BPMN-File.
               Ein Meta-Flow kann mehrere Flows orchestrieren.
               scriptTask ist semantisch korrekt und gibt die
               Description wieder für Dokumentation frei.
               Prio/Order bleibt als Steuerungsmechanismus erhalten.

Governance-  : Ausschließlich additive Erweiterung.
Konformität    FLW00-Kernlogik (Scan, Sort, Exec) bleibt unverändert.
               Neue Ordner und neue Scripts ergänzen, ersetzen nichts.
               Stage-3/4-Artefakte werden nicht angefasst.


--------------------------------------------------------------------------------
2. ZIELDEFINITION (gemäß GOV 10.6)
--------------------------------------------------------------------------------

Ziel 1 — scriptTask als Standard-Trigger
  flowtriggers.txt wird auf scriptTask umgestellt.
  serviceTask entfällt als aktiver Trigger.
  Wildcard-Modus: jeder scriptTask wird ausgeführt —
  kein "Trigger:Ja" in der Description nötig.
  Trigger-Condition bleibt auskommentiert als Option erhalten.
  dispatch_key = attr:name → Scriptname kommt direkt aus dem Task-Namen.

Ziel 2 — Neue Flow-Ordnerstruktur
  01-artifacts\04-flow\ erhält zwei neue Unterordner:
    00-archimateFLW\   für ArchiMate-basierte Flows
    01-bpmnFLW\        für BPMN-basierte Flows
  FLW00 scannt künftig diese Ordner statt 00-xml\03-child.
  Dateiname des BPMN/Archimate-Files = Flow-Name (dokumentarisch).

Ziel 3 — Direkte Script-Auflösung ohne flowmapping.txt
  Bei scriptTask: dispatch_key = attr:name → direkt als Scriptname.
  Kein flowmapping.txt Eintrag nötig für scriptTask-basierte Flows.
  flowmapping.txt bleibt für ArchiMate WorkPackage Flows erhalten.

Ziel 4 — FLW10+ als Flow-Scripts (eine Datei pro Flow)
  Pro Flow wird ein dediziertes Script angelegt:
    FLW10-<FlowName>.py   ruft FLW00 mit dem zugehörigen BPMN-File auf
    FLW11-<FlowName>.py   nächster Flow
    FLW12-<FlowName>.py   usw.
  Namensschema: FLW + fortlaufende Nummer + Bindestrich + Flow-Name

Ziel 5 — FLW-Meta-BPMN (3-Ebenen-Architektur)
  Ein Meta-BPMN in 01-bpmnFLW\ orchestriert die FLW10+ Scripts.
  scriptTasks im Meta-BPMN verweisen auf FLW10.py, FLW11.py etc.
  FLW00 führt den Meta-Flow aus → startet FLW10/11/... → die wiederum
  FLW00 mit ihrem jeweiligen Flow-BPMN aufrufen.
  Order-Werte im Meta-BPMN steuern Reihenfolge und ermöglichen
  bei Problemen gezieltes Eingreifen.

Ziel 6 — FLW02 Sonderregel auf scriptTask erweitern
  FLW02-map_elements.py erkennt scriptTask mit direktem Namen
  analog zur bestehenden serviceTask-Sonderregel.
  Principles und How2 werden entsprechend aktualisiert.

Abgrenzung   : FLW00 Kernlogik (Scan, Sort, Exec) bleibt unverändert.
               Keine Änderung an CSV-, XML-, ATL-, M2B-, HLP-Scripts.
               Stage-3/4-Artefakte unberührt.
               flowmapping.txt bleibt für ArchiMate-Flows erhalten.

Überprüfbar  : Erfolgreich wenn:
               - Ein scriptTask-basiertes BPMN in 01-bpmnFLW\ liegt
               - FLW00 dieses File findet und die Tasks direkt ausführt
               - Ein FLW10-Script den Flow gezielt starten kann
               - Ein Meta-BPMN FLW10 + FLW11 orchestrieren kann


--------------------------------------------------------------------------------
3. IST-ZUSTAND — PROBLEMANALYSE
--------------------------------------------------------------------------------

3.1 Einzelner flacher Flow
---------------------------
FLW00 scannt aktuell 01-artifacts\00-xml\03-child\ und führt ALLE
gefundenen Trigger in ALLEN dort liegenden Dateien aus. Es gibt keine
Möglichkeit zu sagen "führe nur den CSV-Flow aus" — alles oder nichts.

flowmapping.txt ist ein einziger gemeinsamer Namespace. Zwei Flows
die denselben dispatch_key verwenden würden kollidieren.

3.2 serviceTask — semantisch unpassend
----------------------------------------
BPMN 2.0 (OMG Spec) unterscheidet klar:
  serviceTask  → externe Web-Services, automatisierte Applikationen,
                 API-Aufrufe, externe Systeme
  scriptTask   → Engine führt ein Script direkt aus

R+MUNI führt Python-Scripts direkt aus → scriptTask ist korrekt.
Zusätzlicher Effekt: mit serviceTask war die Description durch
"Trigger:Ja" belegt und stand nicht für Doku zur Verfügung.
Mit scriptTask + Wildcard ist die Description wieder frei.

3.3 Keine fixierten, wiederverwendbaren Flow-Definitionen
----------------------------------------------------------
Flows sind aktuell nicht als eigenständige, benennbare Einheiten
gespeichert. Es gibt kein "CSV-Flow.bpmn" das man aufrufen könnte.
Jeder Lauf ist implizit durch den Inhalt von 03-child\ definiert.


--------------------------------------------------------------------------------
4. LÖSUNG — ARCHITEKTUR UND UMSETZUNG
--------------------------------------------------------------------------------

4.1 3-Ebenen-Architektur
--------------------------

Ebene 1 — Meta-Orchestrierung
  Meta-Flow.bpmn  (in 01-bpmnFLW\)
    scriptTask: FLW10-CSV-Flow.py
    scriptTask: FLW11-XML-Flow.py
    scriptTask: FLW12-ATL-Flow.py
    ...
  Order-Werte steuern Reihenfolge und ermöglichen Prio-Steuerung.
  FLW00 führt Meta-Flow.bpmn aus → startet FLW10/11/12 in Sequenz.

Ebene 2 — Flow-Scripts (FLW10+)
  FLW10-CSV-Flow.py   → ruft FLW00 mit CSV-Flow.bpmn auf
  FLW11-XML-Flow.py   → ruft FLW00 mit XML-Flow.bpmn auf
  FLW12-ATL-Flow.py   → ruft FLW00 mit ATL-Flow.bpmn auf
  Jedes FLW10+-Script ist eigenständig startbar (direkter Aufruf)
  UND über den Meta-Flow aufrufbar.

Ebene 3 — Flow-BPMNs (die eigentlichen Arbeitsabläufe)
  CSV-Flow.bpmn   → scriptTasks: CSV00, CSV01, CSV03 ... CSV09
  XML-Flow.bpmn   → scriptTasks: XML00, XML01 ... XML07
  ATL-Flow.bpmn   → scriptTasks: ATL00, ATL01, ATL02
  M2B-Flow.bpmn   → scriptTasks: M2B00 ... M2B07
  ...
  Alle in 01-bpmnFLW\ abgelegt.
  scriptTask name = Scriptdateiname (z.B. "CSV01-validate_model.py")
  Description = frei für Doku, Beschreibung, Hinweise

4.2 Neue Ordnerstruktur
------------------------
01-artifacts\04-flow\
    flowtriggers.txt          (bestehend, angepasst)
    flowmapping.txt           (bestehend, für ArchiMate Flows)
    FLW00-scriptrunner.py     (bestehend, Scanpfad angepasst)
    FLW01-discover.py         (bestehend, Scanpfad angepasst)
    FLW02-map_elements.py     (bestehend, scriptTask Regel ergänzt)
    FLW10-CSV-Flow.py         (NEU)
    FLW11-XML-Flow.py         (NEU)
    FLW12-ATL-Flow.py         (NEU)
    FLW13-M2B-Flow.py         (NEU)
    00-archimateFLW\          (NEU — ArchiMate Flow-Dateien)
    01-bpmnFLW\               (NEU — BPMN Flow-Dateien)
        CSV-Flow.bpmn         (NEU — vom EUMAXL in Camunda zu erstellen)
        XML-Flow.bpmn         (NEU)
        ATL-Flow.bpmn         (NEU)
        M2B-Flow.bpmn         (NEU)
        Meta-Flow.bpmn        (NEU — orchestriert FLW10+)

4.3 flowtriggers.txt — Änderung
---------------------------------
Alt:
  [bpmn_servicetask]
  element_tag  = serviceTask
  condition.1  = tag:documentation:Trigger:Ja
  dispatch_key = attr:id

Neu:
  [bpmn_scripttask]
  element_tag  = scriptTask
  # condition.1 = tag:documentation:Trigger:Ja   ← auskommentiert = Wildcard
  dispatch_key = attr:name                        ← Name = Scriptdateiname

Erklärung Wildcard:
  Kein condition.1 aktiv → JEDER scriptTask in der Flow-Datei wird
  ausgeführt. Sobald selektives Triggern gewünscht wird, einfach
  condition.1 einkommentieren und "Trigger:Ja" in die Description
  des gewünschten scriptTask eintragen.

Erklärung dispatch_key = attr:name:
  Der Name-Wert des scriptTask (z.B. "CSV01-validate_model.py") wird
  direkt als Scriptdateiname verwendet. Kein flowmapping.txt Eintrag
  nötig. FLW00 sucht das Script in 01-artifacts\01-scripts\.

4.4 FLW00 — Scanpfad-Anpassung
---------------------------------
Aktuell scannt FLW00:  01-artifacts\00-xml\03-child\
Neu scannt FLW00:      01-artifacts\04-flow\01-bpmnFLW\  (BPMN)
                        01-artifacts\04-flow\00-archimateFLW\  (ArchiMate)

Kernlogik (Scan → Sort → Exec) bleibt vollständig unverändert.
Nur der Ausgangspfad des os.walk() wird angepasst.

Für scriptTask: dispatch_key = attr:name → FLW00 verwendet den
Namen direkt als Scriptpfad, ohne flowmapping.txt Lookup.
Für ArchiMate WorkPackages: flowmapping.txt Lookup bleibt wie bisher.

4.5 FLW10+ Scripts — Aufbau
------------------------------
Jedes FLW10+-Script:
  - Liest root.cfg (Standard-Konvention)
  - Baut Pfad zu seinem Flow-BPMN auf
    (z.B. 01-artifacts\04-flow\01-bpmnFLW\CSV-Flow.bpmn)
  - Ruft FLW00 via subprocess auf mit dem BPMN-File als Parameter
  - Gibt returncode weiter — Fehler in FLW00 = Fehler in FLW10

Eigenständig startbar:
  python FLW10-CSV-Flow.py    → startet nur den CSV-Flow
  python FLW11-XML-Flow.py    → startet nur den XML-Flow

Über Meta-Flow:
  python FLW00.py             → Meta-Flow.bpmn → FLW10, FLW11, FLW12...

4.6 FLW02 — scriptTask Sonderregel
-------------------------------------
FLW02-map_elements.py wird erweitert:
  Bisherige Sonderregel: serviceTask mit Trigger:Ja → Name als Scriptname
  Neue Sonderregel:      scriptTask (Wildcard) → Name als Scriptname
  Ausgabe in Abschnitt 1 (fertige Mapping-Referenz, da Name = Script)
  serviceTask Regel bleibt für Rückwärtskompatibilität erhalten.

4.7 Prio / Order — Steuerungsmechanismus
------------------------------------------
Order-Werte in flowtriggers.txt und in den BPMN-Files bleiben
vollständig funktionsfähig. Standardmäßig laufen alle scriptTasks
durch (Wildcard + gleicher oder kein gesetzter order-Wert).

Bei Problemen im Livebetrieb:
  - Order-Werte im Meta-Flow.bpmn setzen → Reihenfolge der FLW10+ steuern
  - Einzelne scriptTasks in einem Flow-BPMN mit order priorisieren
  - condition.1 einkommentieren → selektives Triggern aktivieren


--------------------------------------------------------------------------------
5. ARBEITSPAKETE — UMSETZUNGSREIHENFOLGE
--------------------------------------------------------------------------------

AP1  Ordner anlegen
     01-artifacts\04-flow\00-archimateFLW\
     01-artifacts\04-flow\01-bpmnFLW\
     Aktion: EUMAXL legt Ordner manuell an (Konvention: mkdir nicht per Script)

AP2  flowtriggers.txt anpassen
     serviceTask → scriptTask
     condition.1 auskommentieren (Wildcard)
     dispatch_key = attr:name
     Datei: 01-artifacts\04-flow\flowtriggers.txt

AP3  FLW00 Scanpfad anpassen
     os.walk Ausgangspfad auf 04-flow\01-bpmnFLW\ und 04-flow\00-archimateFLW\
     dispatch_key = attr:name → direkte Script-Auflösung ohne Mapping-Lookup
     für scriptTask-Trigger
     Datei: 01-artifacts\04-flow\FLW00-scriptrunner.py

AP4  FLW02 scriptTask Sonderregel ergänzen
     scriptTask erkennen → Name direkt als Scriptname ausgeben
     Datei: 01-artifacts\04-flow\FLW02-map_elements.py

AP5  FLW10-13 Scripts erstellen
     FLW10-CSV-Flow.py
     FLW11-XML-Flow.py
     FLW12-ATL-Flow.py
     FLW13-M2B-Flow.py
     Ablage: 01-artifacts\04-flow\

AP6  BPMN Flow-Files erstellen
     CSV-Flow.bpmn, XML-Flow.bpmn, ATL-Flow.bpmn, M2B-Flow.bpmn
     Meta-Flow.bpmn
     Aktion: EUMAXL erstellt in Camunda Modeler
     Ablage: 01-artifacts\04-flow\01-bpmnFLW\
     Konvention: scriptTask name = Scriptdateiname

AP7  Principles + How2 aktualisieren
     FLOW_SCRIPTRUNNER_principles_S4.md → Hinweis Stage 5 Erweiterung
     FLOW_SCRIPTRUNNER_How2_S4.md       → neue Ablaufbeschreibung
     Neue Principles für Stage 5: FLW_principles_S5.md

AP8  structure.txt aktualisieren
     Neue Ordner 00-archimateFLW und 01-bpmnFLW eintragen
     Aktion: EUMAXL pflegt structure.txt manuell


--------------------------------------------------------------------------------
6. TESTERGEBNIS
--------------------------------------------------------------------------------

Status      : Ausstehend — Sprint noch nicht abgeschlossen
Geplanter   : Testlauf mit CSV-Flow.bpmn in 01-bpmnFLW\
Testfall      FLW00 startet, findet CSV-Flow.bpmn, führt
              CSV00 → CSV01 → CSV03 durch ohne Fehler.
              Anschließend Meta-Flow Test mit FLW10 + FLW11.


--------------------------------------------------------------------------------
7. OFFENE PUNKTE / NEXT STEPS
--------------------------------------------------------------------------------

7.1 BPMN Files erstellen (EUMAXL)
-----------------------------------
Status   : Offen
Aktion   : Für jeden Flow ein BPMN in Camunda Modeler erstellen.
           Beginnen mit CSV-Flow.bpmn als erstem Testkandidat.
           scriptTask name = exakter Scriptdateiname (inkl. .py)

7.2 Meta-Flow Tiefe
--------------------
Status   : Konzept definiert, Umsetzung nach erstem Flow-Test
Aktion   : Erst wenn mindestens 2 Flow-BPMNs existieren sinnvoll.
           Meta-Flow.bpmn dann als letzten Schritt bauen.

7.3 ArchiMate Flow-Files
-------------------------
Status   : Struktur vorbereitet (00-archimateFLW\)
Aktion   : Erst wenn Archi-basierte Flows konkret gebraucht werden.
           Kein Aufbau auf Vorrat.

7.4 Principles S5 FLW
----------------------
Status   : Wird im Zuge AP7 erstellt
Aktion   : Neue Datei FLW_principles_S5.md mit der
           3-Ebenen-Architektur als normative Referenz.

7.5 Sprint-DEF-CSV-Refactoring
--------------------------------
Status   : Weiterhin definiert, noch nicht gestartet
Aktion   : Bleibt eigenständiger Sprint. Dieser Sprint ist
           Voraussetzung (Flow-Infrastruktur) für CSV-Refactoring.


--------------------------------------------------------------------------------
8. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Stage-5-Ziel 4.7 explizit
GOV 10.5  Fachlicher Mehrwert        OK  Mehrere benannte Flows möglich
GOV 10.5  Keine implizite Gov-Änd.   OK  Additive Erweiterung, kein Eingriff
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 2, 6 Ziele
GOV 10.6  Ziel überprüfbar           OK  Testfall definiert Abschnitt 6
GOV 10.7  Zwischenschritte           OK  AP1-AP8 sequenziell
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Keine Architekturänderung Kern
Stage 5   Rückkopplungsschutz        OK  Stage-3/4 unberührt
Stage 5   Additiv nicht modifizierend OK  FLW00 Kernlogik unverändert


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-FLW-MultiFlow-Architektur | Stage 5 | 2026-03-16
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
[[SPRINT-5-5-FREEZE]]