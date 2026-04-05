================================================================================
FREEZE 6 — R+MUNI BLUEPRINT
Stage 5 — Betriebsphase / Sprint 5.7 aktiv
================================================================================
Projekt             : R+MUNI Blueprint
Dokument            : FREEZE-6
Datum               : 2026-03-18
Stage               : 5 (aktiv) — Betriebsphase
Status              : FREEZE BESTÄTIGT
Vorgänger           : FREEZE-5.5 (Sprint 5.5 CleaningRun — 2026-03-14)
Aktiver Sprint      : Stage 5.7 — Betrieb / Beta Endkunde
Erstellt durch      : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument ist die vollständige, autarke Wissensbasis für ein neues
Claude-Projekt ab Freeze 6. Es enthält alles was Claude benötigt um
inkrementelle Sprints in Stage 5.7 eigenständig durchzuführen — ohne
Nachladen von Scripts, Dev-Dokumentationen oder Vorgänger-Freeze-Dokumenten.

Dieses Dokument ersetzt für neue Claude-Sessions vollständig:
  - FREEZE-5.5 (Sprint-5.5-FREEZE.md)
  - STAGE5_ZIELE.md
  - STAGE4_FREEZE.md (als Referenz-Wissen eingearbeitet)
  - Sprint-DEV-Doku-CleaningRun-5-5-Gesamt.md

Ergänzend bereitgestellt im neuen Projekt (nicht in diesem Dokument):
  - Global_GOV_S5.md              (normative Governance — vollständig)
  - SCRIPT-BAUKASTEN.md           (Script-Konventionen)
  - structure.txt                  (aktuelle Ordnerstruktur)
  - Principles und How2 der aktiven Reihen (nach Bedarf)


================================================================================
1. SYSTEMÜBERSICHT — WAS IST R+MUNI
================================================================================

R+MUNI ist ein Blueprint-System für Enterprise Architecture Management.
Es verbindet ArchiMate-Modellierung (Archi 5.8) mit strukturierter
Datenverarbeitung über Python-Scripts und Atlassian als Kundenfrontend.

Kernprinzip: Das Archi-Modell ist die Single Source of Truth.
Alle Artefakte (CSV, XML, XLSX) werden aus dem Modell abgeleitet.
Kein manueller Eingriff in abgeleitete Artefakte — nur im Modell selbst.

R+MUNI ist dauerhaft kostenlos für Endanwender.
Claude ist ein Entwicklungswerkzeug — kein Produktbestandteil.
Archi hat kein Kaufmodell — R+MUNI Kunden erhalten ein Geschenk-Abo
an den Archi-Entwickler als Wertschätzung.


================================================================================
2. STAGE-MODELL — AKTUELLER STAND
================================================================================

Stage 1  FREEZE  — Proof of Concept (historisch)
Stage 2  FREEZE  — Strukturaufbau (historisch)
Stage 3  FREEZE  — Kernlogik (read-only, kein Eingriff)
Stage 4  FREEZE  — Erweiterungslogik (Bugfix nur mit expliziter Freigabe)
Stage 5  AKTIV   — Betriebsphase / Ökosystem-Enablement

Rückkopplungsschutz: Stage-3- und Stage-4-Scripts sind read-only.
Keine Logikänderung ohne explizite GOV-Freigabe.
Erweiterungen in Stage 5 sind immer additiv, nie modifizierend.


================================================================================
3. ORDNERSTRUKTUR (STAGE-5-STANDARD — FIXIERT AB FREEZE 5.5)
================================================================================

<rootfolder>\
  root.cfg                        Einzige Konfigurationsquelle
  .gitignore                      .bak, .log, .lck, .obsidian/ ausgeschlossen
  README.md
  structure.txt                   Aktuelle Ordnerauflistung (generiert)

  00-model\                       Archi-Modell (read-only für Scripts)
    00-archimate\
      00-archimateactive\         Aktives Archi-Modell (MUNI EA.archimate)
      01-archimateactivesub\      Submodelle (MUNI FLOW, MUNI IMPO)
      99-mappingmodel\
    01-bpmn\
    02-xyvision\

  01-artifacts\                   Alle abgeleiteten Artefakte
    00-xml\                       XML-Verarbeitung
      00-master\                  master.xml (ArchiMate Merge-Ergebnis)
      01-mapping\
      02-sync\
      03-child\
        00-archimatechild\        Exportierte XML-Childs aus Archi
        01-bpmnchild\
        02-xychild\
      04-import\
      99-exports\
    01-scripts\                   ALLE Python-Scripts (eine Ablage)
    02-csv\                       CSV-Artefakte
      00-master\                  elements.csv, relations.csv, properties.csv
      01-mapping\
      02-sync\
      03-child\                   Child-CSVs je Modell-Typ
      04-import\                  Archi-Import-Dateien (CSV99-Output)
      99-exports\
    03-XLSX\                      XLSX-Artefakte (analog CSV)
    04-flow\                      FLW-Reihe + flowmapping.txt + flowtriggers.txt
    05-reports\                   Archi HTML Reports (HLP09 Server)

  02-stages\                      Stages und Logs
    model-scope.txt               Archi-Modell Scope (CSV01-Output)
    run-scope.txt                 Aktiver Verarbeitungs-Scope (CSV03/04-Output)
    00-archimatearchive\
    01-bpmnarchive\
    02-xyarchive\
    99-logs\                      ALLE Logs (.log), resolved.txt Dateien


================================================================================
4. KONFIGURATION — root.cfg
================================================================================

root.cfg ist die einzige Konfigurationsquelle.
Alle Scripts lösen Pfade daraus auf — niemals hardcoded.

Aufbau root.cfg:
  <rootfolder>=C:\...\r-muni        Absoluter Pfad zum Projektordner
  <model>=00-model                  Modell-Ordner (relativ zu rootfolder)
  <artifacts>=01-artifacts          Artefakte-Ordner
  <stages>=02-stages                Stages-Ordner
  <scripts>=01-artifacts\01-scripts Scripts-Ordner

HLP00_resolve_root.py ist die zentrale Import-Bibliothek:
  from HLP00_resolve_root import get_root_cfg
  cfg = get_root_cfg()
  basepath = cfg["<artifacts>"]     # → absoluter Pfad

File-Extension-Konvention (verbindlich ab Freeze 5.5):
  .py     Python Scripts
  .cfg    Konfiguration (einmalig durch User gesetzt)
  .txt    Workflow-Artefakt (von Scripts gelesen oder manuell geprüft)
  .md     Dokumentation (GitHub, Blueprint, Sprint-Dokus)
  .log    Debug-Log (nur in 02-stages\99-logs, nie im Root)
  .bak    Archi-Backup (nie in GitHub)
  .ajs    jArchi Scripts


================================================================================
5. SCRIPT-REIHEN — ÜBERSICHT UND STATUS
================================================================================

5.1 HLP-Reihe (HLP00–HLP10) — Hilfsfunktionen
------------------------------------------------
  HLP00  Zentrale Root-Auflösung (öffentliche Bibliothek, import-fähig)
  HLP01  Kopieren
  HLP02  Verschieben
  HLP03  Generischer Ordner-Clean (ohne Blueprint-Semantik)
  HLP04  Verzeichnis-Log
  HLP05  Kontext-Struktur
  HLP06  Backup erstellen
  HLP07  Restore
  HLP08  Struktur → XML/CSV
  HLP09  Report Server (lokaler HTTP-Server für Archi HTML Reports)
  HLP10  Property Definitions bereinigen

Status: Stage-5-Konventionen vollständig. Alle Tests grün.


5.2 CSV-Reihe (CSV00–CSV09, CSV98, CSV99) — Kern-Datenverarbeitung
--------------------------------------------------------------------
  CSV00  Umgebungs-Validierung → CSV00-root.resolved.txt
  CSV01  Modell-Validierung → model-scope.txt
  CSV02  Leer (Platzhalter)
  CSV03  Run-Scope auflösen → run-scope.txt (SOURCE=archi)
  CSV04  Modell-Übersicht → run-scope.txt erweitert + gefiltert
  CSV05  Master-CSVs anlegen (wenn fehlend)
  CSV06  Child → Master append
  CSV07  XLSX → Master CSV
  CSV08  Properties → CSV
  CSV09  master.xml → CSV
  CSV98  Quality Gate (Formula-Prefix FIX, Backtick→Apostroph FIX)
  CSV99  Export Snapshot → 04-import (Archi-Import-Vorbereitung)

Referenz-Flow (vollständig, Stage 5):
  CSV00 → CSV01 → CSV03 → CSV04 → CSV05 → CSV06 →
  CSV07 → CSV08 → CSV98 → CSV99

CSV98 Report: 02-stages\99-logs\CSV98-clean_master_report.txt
Beobachtung: CSV98 meldet 2 XLSX-Treffer — kein Blocker, beobachten.

Status: Stage-5-Konventionen vollständig. Archi Reimport validiert OK.


5.3 XML-Reihe (XML00–XML07) — XML-Verarbeitung
------------------------------------------------
  XML00  Root-Auflösung → XML00-root.resolved.txt
  XML01  Quellen einsammeln
  XML02  Child-XML parsen
  XML03  Index aufbauen
  XML04  Master zusammenführen
  XML05  Merge bereinigen
  XML06  Master finalisieren
  XML07  Artefakte bereinigen

Status: Stage-5-Konventionen vollständig. Alle Tests grün.


5.4 M2B-Reihe (M2B00–M2B07) — Master to BPMN
-----------------------------------------------
  M2B00  Root-Auflösung (via HLP00, kein Fast-Path mehr)
  M2B01  Master extrahieren
  M2B02  Modell aktivieren
  M2B03  Clear
  M2B04  Reconcile + Enrich
  M2B05  Writeback Master
  M2B06  Writeback BPMN ID
  M2B07  Scope Snapshot

Status: Stage-5-Konventionen vollständig. M2B01-Fix aus Stage 5.0 aktiv.


5.5 ATL-Reihe (ATL00–ATL02) — Atlassian Integration
------------------------------------------------------
  ATL00  Scope-Validierung gegen run-scope.txt
  ATL01  master.xml → ATL CSV (ArchiMate Layer + Typ)
  ATL02  ATL CSV → Jira CSV (importfertig)

Jira-Import-Struktur: Komponente = ArchiMate Layer, Stichwort = Typ.
Vollständig auf Atlassian Free-Tier lauffähig.
Erster produktiver Jira-Import: 2026-03-08 erfolgreich (EUMAXL).

Status: Stage-5-Konventionen vollständig.


5.6 FLW-Reihe (FLW00–FLW02) — Scriptrunner / Flow-Steuerung
--------------------------------------------------------------
  FLW00  Scriptrunner (trigger- und mappinggesteuert)
  FLW01  Discover (Element-Typ-Erkennung aus XML/BPMN)
  FLW02  Map Elements (vollständige Element-Referenz)

Steuerung über externe Dateien (in 01-artifacts\04-flow\):
  flowmapping.txt    Welche Scripts in welchem Flow laufen
  flowtriggers.txt   Welche Elemente welchen Flow auslösen

FLW00 CSV-Trigger-Test: OK ✓ (nach Cleaning Run 5.5 validiert)
Kernlogik (Scriptrunner, Discovery, Element-Mapping): unverändert.

Status: Stage-5-Konventionen vollständig. Letzter Schritt Cleaning Run 5.5.


5.7 CLE-Reihe (CLE00–CLE53) — Cleaning Utilities
--------------------------------------------------
NEU in Stage 5 — dedizierte Cleaning-Utilities.
Zweck: definierte Artifact- und Stages-Ordner reproduzierbar leeren.

Schema:
  CLE00   Basis / Diagnose
  CLE1x   XML-Gruppe       (01-artifacts\00-xml)
  CLE2x   CSV-Gruppe       (01-artifacts\02-csv)
  CLE3x   XLSX-Gruppe      (01-artifacts\03-XLSX)
  CLE4x   Reports-Gruppe   (01-artifacts\05-reports)
  CLE5x   Stages-Gruppe    (02-stages)

Nummern-Muster (x0=Master/All, x1=AllChilds, x2=ArchiMate, x3=BPMN,
x4=Import, x5=Export). Ausnahme CLE26: Datei-Delete statt Ordner-Clean.

Zwei Modi:
  Modus A: Ordner-Clean (Standard) — Inhalt löschen, Ordner bleibt
  Modus B: Datei-Delete (CLE26) — gezielte Einzeldatei-Löschung

Jedes CLE-Script ist vollständig autark (inline root.cfg-Auflösung).
Logs: 02-stages\99-logs\CLE<Nr>-<n>.log (Append-Modus).

WICHTIG: CLE-Scripts löschen sofort ohne Bestätigung. Kein Undo.
Vor Einsatz: Git aktiv prüfen oder HLP06 Backup erstellen.

Status: vollständig implementiert, in Flows einbindbar.


================================================================================
6. ATLASSIAN FRONTEND — KUNDENKONFIGURATION
================================================================================

Atlassian Free Bundle (Confluence + Jira) als Kunden-Interface.
Vollständig auf Free-Tier lauffähig — keine kostenpflichtigen Features.

User-Struktur (bis 10 User, Service Collection Bundle):
  Betreiber (EUMAXL)         Volle Rechte, Projektverantwortung
  Service User 1 (Claude)    AI-Unterstützung im Atlassian Umfeld
  Service User 2             Reserve
  Team User (voll)           Konkrete Person, volle Rechte
  Restliche User             Kunden und Team nach Bedarf

Portal-Artikel Reihe (RMNP): Confluence-Struktur für Kundenkommunikation.
Atlassian-Setup ist standardisiert als wiederholbares Onboarding-Artefakt.

Grundsatz: Das Bundle wird optimal genutzt —
kein ungenutztes Potential, keine unnötige Komplexität.


================================================================================
7. GITHUB / VERSIONIERUNG
================================================================================

GitHub Sync: aktiv und sauber (Freeze 5.5 bestätigt).
.gitignore schließt aus: .bak, .log, .lck, .obsidian/

GitHub Pages: aktiv (R+MUNI Doku-Portal öffentlich).
Beta-Nutzung dokumentiert in BETA_GitHub_Nutzung_S5.md.

Grundsatz: Nur saubere, dokumentierte Zustände werden gepusht.
Keine automatischen Pushes aus Scripts.


================================================================================
8. OFFENE PUNKTE — BEWUSST ZURÜCKGESTELLT
================================================================================

8.1 Kosmetik-Run (kein Datum, nach Bedarf — kein Blocker)
  - HLP00-Import vollständig direkt in allen Scripts
    (from HLP00_resolve_root import get_root_cfg statt über .txt)
    Scripts laufen stabil — kein Druck
  - .gitignore Inhalt in Unterordner verteilen

8.2 SPRINT-CSV-Refactoring (definiert, nicht gestartet)
  - CSV10+, XLSX00+, MaM00+ parallel aufbauen
  - run-scope.txt SOURCE=CSV aktivieren
  - flowmapping.txt erweitern
  - GOV 7.5 Naming präzisieren

8.3 Beobachtungspunkt
  - CSV98 meldet 2 XLSX-Treffer
  - Report prüfen: 02-stages\99-logs\CSV98-clean_master_report.txt
  - Status: beobachten, kein akuter Handlungsbedarf


================================================================================
9. BACKLOG STAGE 5.7 — GEPLANTE SPRINTS
================================================================================

Aktiver Sprint: Stage 5.7 — Betrieb / Beta Endkunde
  - Realer Livebetrieb mit ersten Kunden
  - BPMN Default Flows nach Bedarf aufbauen (flowmapping.txt wächst)
  - Bugfixing aus dem Livebetrieb (dokumentiert, GOV-konform)
  - Kundenfeedback strukturiert aufnehmen (GOV Kapitel 11)

Geplante Folge-Sprints (keine festen Termine — Kundenbedarf steuert):
  SPRINT-CSV-Refactoring
    CSV10+, XLSX00+, MaM00+ aufbauen
    SOURCE=CSV in run-scope.txt aktivieren

  SPRINT-BPMN-Flows
    BPMN Default Flows für Script-Reihen als Flows abbilden
    flowmapping.txt schrittweise erweitern

  SPRINT-Kosmetik (nach Bedarf)
    HLP00-Import vollständig direkt
    .gitignore Verteilung

  SPRINT-USER-Dokumentation
    USER-Reihe ausbauen (anwenderorientierte Dokumente)
    Vorarbeit für spätere User-Kommunikation

Nicht Teil von Stage 5 (wächst aus Stage 5 heraus):
  - Vollständig automatisiertes Onboarding ohne manuelle Begleitung
  - Fertiges Claude-Produkt mit Preismodell
  - Vollständige BPMN-Abdeckung aller Script-Reihen
  - Skalierbare Multi-Tenant-Architektur


================================================================================
10. GOVERNANCE-ECKPFEILER FÜR NEUE SPRINTS
================================================================================

Jeder Sprint in Stage 5.7 folgt diesen GOV-Regeln (Kurzform):

GOV 10.3  Zulässige Auslöser: Bugfix, Erweiterung, Kundenbedarf,
          Strukturbereinigung, Entwicklerwunsch

GOV 10.5  Fachlicher Mehrwert muss explizit benennbar sein.
          Keine implizite GOV-Änderung durch Seiteneffekte.

GOV 10.6  Ziel muss explizit und überprüfbar definiert sein
          bevor Umsetzung startet.

GOV 10.7  Zwischenschritte dokumentieren (reihenweise, nachvollziehbar).

GOV 10.8  Dev-Doku erstellen für jede Entwicklungsaktivität.
          Sprint Dev-Dokumentation ist nicht auditpflichtig —
          aber verpflichtend für Nachvollziehbarkeit.

GOV 10.9  Stage-Ende Dokumentation: ausstehend — fällig erst bei
          Stage-5-Gesamtabschluss (nicht bei Sub-Sprints).

GOV 10.10 Keine GOV-Regel darf stillschweigend aufgehoben werden.

Rückkopplungsschutz (absolut):
  - Stage-3/4-Scripts: read-only, kein Eingriff
  - Keine Logikänderung ohne Stage-Entscheid
  - Neue Funktionen: eigene Stages oder Spin-outs
  - Bugfixes: explizite Freigabe + Dokumentation

Rollentrennung (GOV 13):
  - R+MUNI Entwickler / DEV-Rolle strikt getrennt von anderen Rollen
  - Externe Erkenntnisse nur mit [MLAT→RMUNI] Tag transferieren
  - Anonymisierungspflicht für alle externen Inhalte


================================================================================
11. CLAUDE-NUTZUNG IN R+MUNI — RAHMENBEDINGUNGEN
================================================================================

Claude ist Entwicklungswerkzeug, kein Produktbestandteil.
R+MUNI läuft ohne Claude vollständig und kostenlos.

Für neue Claude-Projekte (ab Freeze 6) gilt:
  Bereitgestellte Dokumente (minimal):
    - Dieses Freeze-6-Dokument            (Baseline + Kontext)
    - Global_GOV_S5.md                    (normative Regeln)
    - SCRIPT-BAUKASTEN.md                 (Script-Konventionen)
    - structure.txt                        (Ordnerstruktur aktuell)
    - Principles + How2 der aktiven Reihe (nach Sprint-Bedarf)

  Nicht initial laden:
    - Einzelne Scripts (.py Dateien)
    - Dev-Dokumentationen vergangener Sprints
    - Rosetta Stone Dokumente (nur bei Onboarding neuer Personen)

  Arbeitsweise:
    - Pair-Session Prinzip: Claude generiert, Entwickler entscheidet
    - Jede Umsetzung benötigt explizite Freigabe durch Betreiber
    - GOV-Hoheit liegt ausschließlich beim Betreiber (EUMAXL)
    - Claude fragt bei Rollenzweifel nach (GOV 13.8)

AI-Driven Development Methodik ist dokumentiert in:
  AI_DRIVEN_DEV_METHODE.md (vollständige Methodenbeschreibung)


================================================================================
12. FORMALE ABSCHLUSSFESTSTELLUNG
================================================================================

Freeze 6 gilt als gültige Baseline für Stage 5.7, da:

  ✓ Alle Sprint-5.5-Ziele erfüllt (14/14 — Freeze 5.5 bestätigt)
  ✓ Ordnerstruktur 00/01/02 physisch umgesetzt und verifiziert
  ✓ root.cfg als einzige Konfigurationsquelle etabliert
  ✓ Alle Script-Reihen auf Stage-5-Konventionen
  ✓ File-Extension-Konvention definiert und angewendet
  ✓ GitHub Sync sauber (.gitignore korrekt)
  ✓ CSV98 Quality Gate produktiv getestet (Archi Reimport OK)
  ✓ FLW00 CSV-Trigger-Test grün
  ✓ CLE-Reihe vollständig implementiert
  ✓ Rückkopplungsschutz vollständig eingehalten
  ✓ Dev-Dokumentation GOV-konform vorhanden
  ✓ Atlassian Frontend-Setup dokumentiert
  ✓ GOV Kapitel 13 (User-Feedback-Kanal) hinzugefügt
  ✓ AI_DRIVEN_DEV_METHODE erweitert (Kapitel 11–13)

  ⚠ Stage-Ende Dokumentation (GOV 10.9): OFFEN
    Fällig bei Stage-5-Gesamtabschluss — kein Blocker für Stage 5.7

Das harte Scripten von Stage 5 ist abgeschlossen.
Stage 5.7 startet auf sauberer, konsistenter, vollständig dokumentierter Basis.
Nächster Schwerpunkt: Realer Betrieb, BPMN Flows nach Bedarf, Bugfixing.


================================================================================
FREEZE 6 — BESTÄTIGT | 2026-03-18
R+MUNI Blueprint | Stage 5.7 aktiv
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
