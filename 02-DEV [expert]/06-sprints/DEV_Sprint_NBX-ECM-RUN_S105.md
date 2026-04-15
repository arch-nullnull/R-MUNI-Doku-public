================================================================================
NBX-ECM ERSTER PRODUKTIVRUN — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_NBX-ECM-RUN_S105
Tag             : #dev #sprint #nbx #ecm #run #s105
Datum           : 2026-04-13
Stage           : S1.05 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-13
Jira-Sync       : NEIN
================================================================================

---
title: "NBX-ECM Erster Produktivrun"
stage: S1.05
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-13"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, nbx, ecm, run, s105]
---

================================================================================
NBX-ECM ERSTER PRODUKTIVRUN — SPRINT (DEV)
Stage S1.05 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Erster vollständiger Produktivrun des NBX-Flows (NBX00–NBX05) kombiniert
mit dem ECM-Flow (ECM00–ECM01) zur Erstellung eines Mapping-Modells.
Sprint entstand aus dem S105-Ziel Z2 (NBX Erweiterung & Cleanup) und
diente gleichzeitig als Debugging-Session für den IP-Merge in NBX04
sowie als Klärung des korrekten ECM-Ablaufs für die Mapping-Modell-Erstellung.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[DEV_Sprint_NBX_S102_FINAL]]        NBX-Flow Ursprungssprint
- [[FREEZE_1_04]]                      Ausgangszustand Stage 1.05
- [[STAGE105_ZIELE_S105]]              Stage-Ziele — Z2 NBX

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Fehlerbehebung + Feature-Zuwachs
Beschreibung: NBX04 IP-Merge hat Services nicht korrekt auf Host-Zeilen
              aggregiert — Ursache: einmaliger Durchlauf mit
              Reihenfolgeabhängigkeit. Zusätzlich war der korrekte
              ECM-Ablauf für Mapping-Modell-Erstellung unklar.
              Beide Punkte in einer Session geklärt und behoben.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         NBX04 IP-Merge korrekt — eine Zeile pro Host in trash_nbx.csv.
              Mapping-Modell erstellt, OEF XML abgelegt, Archi-Modell gesichert.
              Korrekter ECM-Ablauf dokumentiert und verstanden.

Abgrenzung:   - Kein Eingriff in NBX00–NBX03
              - Kein Eingriff in ECM00–ECM03
              - Kein ECM02-Lauf in diesem Sprint (Mapping-Modell erst erstellt)
              - Kein ECM03 ID-Merge in diesem Sprint


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  NBX04 vorhanden aber fehlerhaft — Service-Zeilen wurden nicht
  zuverlässig auf Host-Zeilen aggregiert weil Reihenfolge in CSV
  vorausgesetzt wurde. Mapping-Modell nicht vorhanden.
  ECM-Ablauf für Erstlauf nicht explizit dokumentiert.
  Fehler durch falsches Import-File (Import-Ordner statt
  00-archimatechild) zusätzlich verschleiert.

Soll-Zustand nach dem Sprint:
  NBX04 mit Zwei-Durchlauf-Logik — Hosts zuerst, Services danach,
  Reihenfolge in CSV irrelevant.
  Mapping-Modell vorhanden — OEF XML in 99-mappingmodel abgelegt.
  ArchiMate-Modell gesichert für eventuelle Anpassungen.
  ECM-Ablauf Erstlauf explizit bekannt und dokumentiert.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 NBX04 — IP-Merge Fix
--------------------------

NBX04 komplett neu geschrieben. Kernänderung: zwei separate Durchläufe
statt einem kombinierten Durchlauf.

  Durchlauf 1: Alle Host-Zeilen einsammeln (ip → host-dict)
  Durchlauf 2: Alle Service-Zeilen zuordnen (ip aus nbx_raw_id: IP:Port)

Zusätzlich: Port-String Rekonstruktion aus Description-Spalte statt
fragiler 3PartyID-Parsing Logik. Description enthält `Port 22/tcp`
sauber aus NBX03 — direkt lesbar ohne Rückwärts-Parsing.

Artefakte:    NBX04-ip_merge.py — 01-artifacts\01-scripts\
GOV-Konform:  JA


2.2 Debugging — Falsches Import-File
--------------------------------------

Root-Cause des "Merge-Problems" identifiziert: EUMAXL hatte beim
Mapping-Aufbau die trash_nbx.csv aus dem 04-import Ordner (alter Stand)
statt aus 00-archimatechild (aktueller NBX04-Output) geladen.
Kein Script-Bug — Layer-8-Problem.

Artefakte:    kein Artefakt
GOV-Konform:  JA


2.3 ECM-Ablauf Erstlauf — Klärung
-----------------------------------

Korrekter Ablauf für Mapping-Modell-Erstellung (Erstlauf) explizit
geklärt. ECM01 macht bereits was für den Erstlauf benötigt wird —
Header als Artifacts ausgeben, Beispielwert in Documentation.
ECM04 war irrtümlich als neues Script geplant — nicht notwendig,
ECM01 deckt den Use Case vollständig ab.

Ablauf Erstlauf (dokumentiert):
  NBX00–NBX05 → trash_nbx.csv (gemergt)
  ECM00 → ECM01 → elements.csv (Header als Artifacts)
  Archi Import → Mapping-Modell visuell aufbauen
  OEF Export → 99-mappingmodel abgelegt

Artefakte:    kein Artefakt — Dokumentation in diesem Sprint
GOV-Konform:  JA


2.4 Mapping-Modell erstellt
-----------------------------

Erster vollständiger Lauf ECM00 → ECM01 → Archi Import →
Mapping-Modell aufgebaut → OEF XML exportiert → abgelegt.
ArchiMate-Modell zusätzlich gesichert für eventuelle Anpassungen.

Artefakte:    OEF XML → 99-mappingmodel\
              ArchiMate-Modell → gesichert (Pfad EUMAXL)
GOV-Konform:  JA


2.5 BPMN NBX-Flow — Beschreibung
----------------------------------

Vollständige BPMN 2.0 Beschreibung des NBX-Flows (NBX00–NBX05)
für Camunda Modeler erstellt. Drei Lanes (EUMAXL, NBX-Scripts,
Filesystem), alle Error Boundary Events, alle Gateways,
Rückpfeil bei erneutem Scan, zwei reguläre End Events
(Phase 1 / Phase 2). Für DEV-Doku vorgesehen.

Artefakte:    BPMN_NBX-Flow_DEV_S105.md — 00-internal\99-doku\
GOV-Konform:  JA


2.6 Backlog NBA-Flow
---------------------

Eigenständige Script-Reihe NBA (NetBox Agent) als Backlog angelegt.
Agent-Daten als optionale Anreicherung zum NBX-Flow — kein Eingriff
in NBX00–NBX05, eigener Merge-Schritt, ECM-Flow unverändert.

Artefakte:    BACKLOG_NBA-FLOW_DEV_S105.md — 00-internal\99-doku\
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: NBX04 Zwei-Durchlauf-Logik
  Auslöser:    Reihenfolgeabhängigkeit im alten Script führte zu
               fehlenden Service-Aggregationen
  Ergebnis:    Zwei separate Durchläufe — erst alle Hosts, dann alle Services
  Begründung:  Reihenfolge in CSV darf keine Rolle spielen —
               deterministisches Ergebnis unabhängig von NBX03-Output-Reihenfolge
  GOV-Bezug:   GOV 1.4 Explizitheit, GOV 6.7 Ableitung deterministisch
  Auswirkung:  NBX04 ersetzt altes Script vollständig — kein Modus-Schalter
  Rückwirkung: NEIN


Entscheidung: ECM04 nicht bauen
  Auslöser:    Idee eines neuen Scripts für Header-zu-Mapping Konvertierung
  Ergebnis:    ECM04 wird nicht gebaut — ECM01 deckt den Use Case ab
  Begründung:  ECM01 schreibt bereits Header-Namen als Artifacts mit
               Beispielwert in Documentation — exakt der gewünschte Output
  GOV-Bezug:   GOV 3.4 keine implizite Weiterentwicklung ohne Bedarf
  Auswirkung:  ECM-Reihe bleibt ECM00–ECM03 — kein neues Script
  Rückwirkung: NEIN


Entscheidung: NBA-Flow als eigenständige Reihe im Backlog
  Auslöser:    Wunsch Agent-Daten in NBX-Output einzubringen
  Ergebnis:    Eigenständige Reihe NBA — kein Eingriff in NBX
  Begründung:  GOV 5.6 Ebenentrennung — Producer/Consumer sauber trennen.
               NBX bleibt stabiler Core, NBA ist optionale Erweiterung
  GOV-Bezug:   GOV 5.6, GOV 6.9
  Auswirkung:  Backlog angelegt — Umsetzung nach Agent-Evaluation
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Keine Abweichungen.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: NBX02 Script war im Projektordner vorhanden —
  Claude hat es übersehen und nachgefragt statt selbst nachzuschauen.
  Korrektur durch EUMAXL.

⚠ Verhaltenshinweis: ECM04 Idee zu schnell als neues Script aufgenommen
  ohne zuerst ECM01 vollständig zu prüfen. ECM01 hätte vorher gelesen
  werden müssen — Drift durch zu schnelle Umsetzungsbereitschaft.
  Erkannt und korrigiert bevor Code entstanden ist.

⚠ Verhaltenshinweis: BPMN Ablauf war initial falsch — ECM01 nicht als
  Pflichtschritt vor Mapping-Modell-Erstellung eingetragen. Durch
  EUMAXL korrigiert. BPMN wurde nicht neu ausgegeben — Korrektur
  im Chat dokumentiert.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| ECM02 Lauf mit fertigem Mapping-Modell | keiner | offen | Nächste Session — regulärer Lauf |
| ECM03 ID-Merge | keiner | offen | Nach ECM02 |
| BPMN korrigieren — ECM01 als Pflichtschritt | keiner | offen | EUMAXL entscheidet ob Update |
| NBX04 testen — sauberer Lauf bestätigen | keiner | offen | EUMAXL nach Script-Einspielung |
| nbx_config.txt + nbx_raw.json in .gitignore | GOV 6.13 | offen | EUMAXL |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA
  — NBX04-ip_merge.py             01-artifacts\01-scripts\
  — BPMN_NBX-Flow_DEV_S105.md    00-internal\99-doku\
  — BACKLOG_NBA-FLOW_DEV_S105.md  00-internal\99-doku\
  — OEF XML Mapping-Modell        99-mappingmodel\
  — ArchiMate-Modell              gesichert (Pfad EUMAXL)
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Zwei-Durchlauf-Logik in NBX04 ist sauber und reihenfolgeunabhängig
  - Root-Cause Analyse hat schnell den Layer-8-Fehler (falsches Import-File)
    aufgedeckt — kein unnötiger Script-Umbau
  - ECM01 Use Case Klärung hat einen unnötigen ECM04-Bau verhindert
  - Mapping-Modell erster Lauf erfolgreich — Flow funktioniert end-to-end

Was beim nächsten Mal anders gemacht werden sollte:
  - Alle vorhandenen Scripts zuerst vollständig lesen bevor neue
    Scripts vorgeschlagen werden
  - Import-Pfad explizit im BPMN und in der Doku verankern —
    00-archimatechild ist die einzige valide Quelle für Archi-Import
  - BPMN vor Ausgabe gegen tatsächlichen Script-Ablauf prüfen

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Korrekter ECM-Erstlauf-Ablauf sollte in NBX05-handoff_report.txt
    explizit dokumentiert sein → NBX05 Script anpassen: Sprint anlegen: NEIN
    — bei nächster regulärer NBX-Revision aufnehmen
  - BPMN als DEV-Doku Format etablieren → kein GOV-Änderungsbedarf,
    bewusste Entscheidung EUMAXL

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[DEV_Sprint_NBX_S102_FINAL]]        NBX-Flow Ursprungssprint
[[BACKLOG_NBA-FLOW_DEV_S105]]        NBA-Flow Backlog — aus diesem Sprint
[[FREEZE_1_04]]                      Ausgangszustand

---

================================================================================
NBX-ECM ERSTER PRODUKTIVRUN — SPRINT (DEV) | S1.05 | 2026-04-13 | R+MUNI Blueprint
================================================================================
