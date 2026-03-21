================================================================================
FREEZE 6 — R+MUNI BLUEPRINT (KONSOLIDIERT)
Stage 5.7 + Stage 6 — Abschluss / Startpunkt Stage 7
================================================================================
Projekt             : R+MUNI Blueprint
Dokument            : FREEZE-6 (konsolidiert)
Erstellt            : 2026-03-18
Konsolidiert        : 2026-03-21
Stage               : 6 — ABGESCHLOSSEN
Status              : FREEZE BESTÄTIGT — Stage 6 vollständig
Vorgänger           : FREEZE-5.5 (Sprint 5.5 CleaningRun — 2026-03-14)
Nachfolger          : FREEZE-7 (Startpunkt Stage 7 — neues Claude-Projekt)
Erstellt durch      : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
HINWEIS ZUR FREEZE-NUMMERIERUNGS-KONVENTION
================================================================================

Freeze 6 ist der letzte Freeze mit organisch gewachsener Nummerierung.

Historischer Hintergrund:
  Freeze 6 wurde am 2026-03-18 als Startpunkt für Stage 5.7 erstellt.
  Die Nummer "6" spiegelte den internen Zähler wider — nicht die Stage-Nummer.
  Das erzeugte Mehrdeutigkeit: "Freeze 6" ≠ "Stage 6 Abschluss".

Entscheidung (2026-03-21, EUMAXL):
  Ab Freeze 7 gilt verbindlich:
  → Freeze-Nummer = Startpunkt des gleichnamigen Stage
  → FREEZE-7 = autarke Wissensbasis für Stage 7
  → FREEZE-8 = autarke Wissensbasis für Stage 8
  → usw.

  Freeze 6 wird konsolidiert — nicht umbenannt.
  Es bleibt FREEZE-6 und deckt nun vollständig ab:
  Stage 5.7 Baseline (ursprünglicher Inhalt) +
  Stage 6 Abschluss (Konsolidierung) +
  Ausblick Stage 7 (Startpunkt-Vorbereitung)

  Diese Notiz wird nicht in Freeze 7 übernommen.
  Ab Freeze 7 ist die Konvention gültig und selbstverständlich.


================================================================================
ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument ist die vollständige, autarke Wissensbasis für ein neues
Claude-Projekt ab Stage 7. Es enthält alles was Claude benötigt um
inkrementelle Sprints in Stage 7 eigenständig durchzuführen — ohne
Nachladen von Scripts, Dev-Dokumentationen oder Vorgänger-Freeze-Dokumenten.

Dieses Dokument ersetzt für neue Claude-Sessions vollständig:
  - FREEZE-5.5 (Sprint-5.5-FREEZE.md)
  - STAGE5_ZIELE.md
  - STAGE6_ZIELE.md
  - STAGE4_FREEZE.md (als Referenz-Wissen eingearbeitet)
  - Sprint-DEV-Doku-CleaningRun-5-5-Gesamt.md
  - Alle Stage-6-Sprint-Dokumentationen (als Erkenntnisse eingearbeitet)

Ergänzend bereitgestellt im neuen Projekt (nicht in diesem Dokument):
  - Global_GOV_S6.md              (normative Governance — vollständig)
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
Stage 5  FREEZE  — Betriebsphase / Ökosystem-Enablement (abgeschlossen)
Stage 6  FREEZE  — Beta Feedback Integration & Blueprint Maturity (abgeschlossen)
Stage 7  AKTIV   — [Titel wird in Stage-7-Eröffnung definiert]

Rückkopplungsschutz: Stage-3- bis Stage-6-Scripts sind read-only.
Keine Logikänderung ohne explizite GOV-Freigabe.
Erweiterungen in Stage 7 sind immer additiv, nie modifizierend.


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
      99-mappingmodel\            OEF Mapping-Modell (ECM-Reihe) — NEU S6
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

Status: Stage-5-Konventionen vollständig.


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


5.8 ECM-Reihe (ECM00–ECM03) — EasyCSVMapper
---------------------------------------------
NEU in Stage 6 — dedizierte Reihe für externe CSV-Quellen.
Zweck: unkontrollierte externe CSV-Dateien (variables Encoding,
variables Trennzeichen, unbekannte Spaltenstruktur) in das
ArchiMate-Modell importieren.

  ECM00  Umgebungs-Validierung
  ECM01  CSV-Felder → Artefakte (Struktur-Erkennung)
  ECM02  CSV → Mapping → CSV (via OEF Mapping-Modell)
  ECM03  ID-Merge (Archi-IDs zuweisen / aktualisieren)

Mapping-Logik:
  Mapping-Modell als ArchiMate OEF XML in 99-mappingmodel\
  Association-Semantik: ohne eingehende Association = Element,
  mit eingehender Association = Property des Ziel-Elements.
  MAPPING= Key in run-scope.txt referenziert OEF-Dateinamen direkt.

Erster produktiver Test: trash_test.csv (cp1252, Semikolon) erfolgreich.
99-mappingmodel\ erstmals mit normativem Inhalt befüllt.

Status: vollständig implementiert und produktiv getestet (Stage 6).

Offener Folge-Sprint (zurückgestellt auf Stage 7):
  ECM-Script-Erweiterung (CSV10+) — SOURCE=CSV in run-scope.txt aktivieren.


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

Beta-Kunden Status (Stand Stage 6 Abschluss):
  Betakunde_01   Status: PASSIV — kein aktives Feedback seit Onboarding.
                 Kommunikationsweg vollständig durchlaufen:
                 persönliches Gespräch → Onboarding-E-Mail →
                 Reminder mit Wiederholung des initialen Gesprächs.
                 Adoption auf Kundenseite nicht erfolgt.
                 Organisationales Verhalten, kein Blueprint-Defizit.
                 Atlassian-Zugang technisch aktiv.
                 Review: wenn Stage 7 einen Sprint produktiv läuft.

  Betakunde_02   Status: GEPLANT für Stage 7.
  (ASC)          Primärer aktiver Beta-Kontext ab Stage 7.
                 EUMAXL = Obmann = DEV + User in einer Person.
                 Rollentrennung explizit dokumentiert (GOV 13.8).
                 Vollständiges Onboarding erfolgt in Stage 7.

Grundsatz: Das Bundle wird optimal genutzt —
kein ungenutztes Potential, keine unnötige Komplexität.


================================================================================
7. GITHUB / VERSIONIERUNG
================================================================================

GitHub Sync: aktiv und sauber (Freeze 5.5 bestätigt, Stage 6 fortgeführt).
.gitignore schließt aus: .bak, .log, .lck, .obsidian/

GitHub Pages: aktiv (R+MUNI Doku-Portal öffentlich).
Beta-Nutzung dokumentiert in BETA_GitHub_Nutzung_S5.md.

Grundsatz: Nur saubere, dokumentierte Zustände werden gepusht.
Keine automatischen Pushes aus Scripts.


================================================================================
8. OBSIDIAN — BLUEPRINT-NAVIGATIONSWERKZEUG
================================================================================

NEU etabliert in Stage 6 (S6-Z4).

Obsidian ist das MD-basierte Navigationswerkzeug für den Blueprint.
Es macht Abhängigkeiten zwischen Dokumenten sichtbar und navigierbar.

Kernregeln:
  - Obsidian ist Lesewerkzeug und Navigationshilfe — keine neue Logikschicht
  - Kein Eingriff in bestehende Dateistruktur oder Dateinamen
  - Obsidian-Vault liegt im Blueprint — portabel, kein Cloud-Zwang
  - .obsidian/ ist in .gitignore ausgeschlossen

Verlinkungskonvention:
  [[Dokumentname]]         MD-Link zu einem Blueprint-Dokument
  SVG/PNG Einbettung       für Diagramme in Dokumenten definiert

How2-Dokumentation vorhanden:
  OBS_How2_DEV_S6.md      DEV-Perspektive
  OBS_How2_USER_S6.md     USER-Perspektive


================================================================================
9. TOOLBAUKASTEN — TRANSPARENZ UND STRUKTUR
================================================================================

NEU dokumentiert in Stage 6 (S6-Z6).

Tier-Struktur des Toolbaukastens:
  MINIMAL    Pflichttools — R+MUNI läuft nicht ohne sie
  DEFAULT    Empfohlene Tools — Standard-Setup für alle User
  ADDON      Optionale Erweiterungen — nach Bedarf
  AGNOSTIC   Tool-unabhängige Komponenten

Dokumentation:
  TOOLBAUKASTEN_principles_S6.md     DEV-Referenz + Entscheidungslogik
  TOOLBAUKASTEN_How2_DEV_S6.md       Developer-Anleitung
  TOOLBAUKASTEN_How2_USER_S6.md      User-Anleitung (Kosten, Philosophie)

Grundsatz: R+MUNI läuft kostenlos — Tools sind Ergänzung, kein Zwang.
Kostenstruktur und Abhängigkeiten sind vollständig transparent dokumentiert.


================================================================================
10. DOKUMENTEN-TEMPLATES — BLUEPRINT STANDARD
================================================================================

NEU definiert in Stage 6 (S6-Z5).

Templates für alle wiederkehrenden Dokumententypen im Blueprint:
  Sprint-DEV-Dokumentation     Sprint-DEV-Doku_Template_S6.md
  Stage-Ziele Dokument         Stage_Ziele_Template_S6.md
  GOV-Ergänzung                GOV_Global_Template_S6.md
  How2 USER                    how2_USER_Template_S6.md
  How2 DEV                     how2_DEV_Template_S6.md
  Freeze-Dokument              (dieses Dokument als Referenz)
  Sprint-DEV-Backlog           Sprint-DEV-BACKLOG_Template_S6.md
  TMP-Reihe                    Sprint-DEV-Doku_TMP-Reihe_S6.md

Ablageort: 00-concept\ im Blueprint.
Grundsatz: Templates sind Vorlagen — keine normativen Pflichtformate
rückwirkend. Neue Dokumente starten auf validierter Grundstruktur.

Stage-Bezeichnungs-Konvention (S6-Z3):
  Alle Dokumente im Beta-Zustand erhalten Suffix _S<N> im Dateinamen.
  Format ist verbindlich und wird bei Stage-Übergang aktualisiert.
  Ziel: externer Leser erkennt sofort ob ein Dokument Beta-Status hat.


================================================================================
11. OFFENE PUNKTE — BEWUSST ZURÜCKGESTELLT
================================================================================

11.1 Kosmetik-Run (kein Datum, nach Bedarf — kein Blocker)
  - HLP00-Import vollständig direkt in allen Scripts
    (from HLP00_resolve_root import get_root_cfg statt über .txt)
    Scripts laufen stabil — kein Druck
  - .gitignore Inhalt in Unterordner verteilen

11.2 SPRINT-CSV-Refactoring (definiert, nicht gestartet)
  - CSV10+, XLSX00+, MaM00+ parallel aufbauen
  - run-scope.txt SOURCE=CSV aktivieren
  - flowmapping.txt erweitern
  - GOV 7.5 Naming präzisieren
  - Voraussetzung: ECM Folge-Sprint abgeschlossen

11.3 ECM Folge-Sprint (zurückgestellt auf Stage 7)
  - ECM-Script-Erweiterung für SOURCE=CSV Flow
  - Setzt SPRINT-CSV-Refactoring als Kontext voraus

11.4 Beobachtungspunkt
  - CSV98 meldet 2 XLSX-Treffer
  - Report prüfen: 02-stages\99-logs\CSV98-clean_master_report.txt
  - Status: beobachten, kein akuter Handlungsbedarf

11.5 O365-Integration (geplant Stage 7)
  - M365 Dev Account (EUMAXL) als isolierte Test-Umgebung
  - Separates Notebook Windows 11 — vollständig isoliert von Main-System
  - OneDrive, SharePoint, Teams Integration als Backlog-Sprint
  - Status: VORBEREITET, Umsetzung in Stage 7


================================================================================
12. BACKLOG STAGE 7 — GEPLANTE SCHWERPUNKTE
================================================================================

Primärer Beta-Kontext:
  ASC (Betakunde_02) — vollständiges Onboarding in Stage 7
  EUMAXL als Obmann = echter Anwendungskontext
  Changemanagement, Mitgliederverwaltung, 5-Jahres-Entscheidungsgrundlage

Geplante Sprints (keine festen Termine — Bedarf steuert):

  SPRINT-ASC-Onboarding
    Atlassian-Setup für ASC als Beta-Kunde 2
    Rollentrennung DEV/Obmann explizit dokumentiert
    Feedbackschleife aktivieren

  SPRINT-O365-Integration
    M365 Dev Account als Test-Umgebung
    OneDrive / SharePoint / Teams Anbindung evaluieren
    Voraussetzung: M365 Dev Account reaktiviert

  SPRINT-ECM-Script-Erweiterung
    CSV10+ für SOURCE=CSV Flow
    Setzt SPRINT-CSV-Refactoring voraus

  SPRINT-CSV-Refactoring
    CSV10+, XLSX00+, MaM00+ aufbauen
    SOURCE=CSV in run-scope.txt aktivieren

  SPRINT-BPMN-Flows
    BPMN Default Flows für Script-Reihen als Flows abbilden
    flowmapping.txt schrittweise erweitern

Nicht Teil von Stage 7 (wächst aus Stage 7 heraus):
  - Vollständig automatisiertes Onboarding ohne manuelle Begleitung
  - Fertiges Claude-Produkt mit Preismodell
  - Skalierbare Multi-Tenant-Architektur
  - Vollständige BPMN-Abdeckung aller Script-Reihen


================================================================================
13. GOVERNANCE-ECKPFEILER FÜR NEUE SPRINTS
================================================================================

Jeder Sprint in Stage 7 folgt diesen GOV-Regeln (Kurzform):

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

GOV 10.9  Stage-Ende Dokumentation: fällig bei Stage-7-Gesamtabschluss.

GOV 10.10 Keine GOV-Regel darf stillschweigend aufgehoben werden.

Rückkopplungsschutz (absolut):
  - Stage-3/4/5/6-Scripts: read-only, kein Eingriff
  - Keine Logikänderung ohne Stage-Entscheid
  - Neue Funktionen: eigene Stages oder Spin-outs
  - Bugfixes: explizite Freigabe + Dokumentation

Rollentrennung (GOV 13):
  - R+MUNI Entwickler / DEV-Rolle strikt getrennt von anderen Rollen
  - ASC-Rolle (Obmann) strikt getrennt von DEV-Rolle
  - Externe Erkenntnisse nur mit [BetaKunde→RMUNI] Tag transferieren
  - Anonymisierungspflicht für alle externen Inhalte


================================================================================
14. CLAUDE-NUTZUNG IN R+MUNI — RAHMENBEDINGUNGEN
================================================================================

Claude ist Entwicklungswerkzeug, kein Produktbestandteil.
R+MUNI läuft ohne Claude vollständig und kostenlos.

Für neue Claude-Projekte (ab Stage 7 / Freeze 7) gilt:
  Bereitgestellte Dokumente (minimal):
    - FREEZE-7-Dokument                 (Baseline + Kontext)
    - Global_GOV.md                     (normative Regeln)
    - SCRIPT-BAUKASTEN.md               (Script-Konventionen)
    - structure.txt                      (Ordnerstruktur aktuell)
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
    - Kontext-Optimierung gemäß AI_DRIVEN_DEV_METHODE_S6 Kapitel 15

AI-Driven Development Methodik ist dokumentiert in:
  AI_DRIVEN_DEV_METHODE_S6.md (vollständige Methodenbeschreibung)


================================================================================
15. STAGE 6 — ABSCHLUSSFESTSTELLUNG
================================================================================

Stage 6 — Beta Feedback Integration & Blueprint Maturity

Alle 6 Ziele erreicht:

  ✓ S6-Z1  Beta-Kunden-Feedback Einbindung
           Feedbackstruktur vollständig aufgebaut. Kommunikationsweg
           vollständig durchlaufen: persönliches Gespräch (CEO,
           Head-of-Ebene) → Onboarding-E-Mail → Reminder mit
           Wiederholung des initialen Gesprächs zur Vermeidung
           von Missverständnissen beiderseits. Adoption auf
           Kundenseite nicht erfolgt — organisationales Verhalten,
           kein Blueprint-Defizit. Feedbackschleifen funktionieren
           strukturell korrekt.

  ✓ S6-Z2  Feedbackschleifen — How2 für GitHub, Jira, E-Mail
           DEV- und Kundensicht getrennt dokumentiert.
           Beide Kanäle definiert, How2 im Blueprint abgelegt.

  ✓ S6-Z3  Reviewschleifen — Stage-Bezeichnung in Beta-Dokumenten
           _S<N> Suffix als verbindliche Konvention eingeführt.
           Bestehende Dokumente nachgezogen. Sprint-Doku vorhanden.

  ✓ S6-Z4  Obsidian-Nutzung im Blueprint
           Obsidian etabliert als Navigationswerkzeug.
           DEV-How2 + USER-How2 vorhanden. Sprint-Doku abgeschlossen.

  ✓ S6-Z5  Templates für Dokumententypen im Blueprint
           Alle definierten Template-Typen erstellt und abgelegt.
           Neue Dokumente starten auf validierter Grundstruktur.

  ✓ S6-Z6  Toolbaukasten transparent für User
           Tier-Struktur definiert. Drei Doku-Ebenen erstellt.
           Kosten und Philosophie transparent. Sprint-Doku abgeschlossen.

Zusätzliche Erkenntnisse aus Stage 6 (nicht in STAGE6_ZIELE.md):
  ✓ ECM-Reihe (EasyCSVMapper) implementiert und produktiv getestet
  ✓ Freeze-Nummerierungs-Konvention ab Freeze 7 definiert
  ✓ ASC als Betakunde_02 für Stage 7 vorbereitet
  ✓ M365 Dev Account als O365-Testumgebung für Stage 7 identifiziert

Stage-Ende Dokumentation (GOV 10.9): ERFÜLLT durch diesen Freeze.


================================================================================
16. FORMALE ABSCHLUSSFESTSTELLUNG
================================================================================

Freeze 6 (konsolidiert) gilt als vollständige Baseline für Stage 7, da:

  ✓ Alle Sprint-5.5-Ziele erfüllt (14/14 — Freeze 5.5 bestätigt)
  ✓ Alle Stage-6-Ziele erfüllt (6/6 — siehe Kapitel 15)
  ✓ Ordnerstruktur 00/01/02 physisch umgesetzt und verifiziert
  ✓ root.cfg als einzige Konfigurationsquelle etabliert
  ✓ Alle Script-Reihen auf Stage-5/6-Konventionen
  ✓ File-Extension-Konvention definiert und angewendet
  ✓ GitHub Sync sauber
  ✓ CSV98 Quality Gate produktiv getestet (Archi Reimport OK)
  ✓ FLW00 CSV-Trigger-Test grün
  ✓ CLE-Reihe vollständig implementiert
  ✓ ECM-Reihe vollständig implementiert und produktiv getestet
  ✓ Rückkopplungsschutz vollständig eingehalten
  ✓ Dev-Dokumentation GOV-konform vorhanden
  ✓ Atlassian Frontend-Setup dokumentiert
  ✓ GOV Kapitel 13 (User-Feedback-Kanal) vorhanden
  ✓ AI_DRIVEN_DEV_METHODE_S6 erweitert (Kapitel 14-15)
  ✓ Obsidian als Navigationswerkzeug etabliert
  ✓ Templates für alle Blueprint-Dokumenttypen definiert
  ✓ Toolbaukasten transparent dokumentiert (3 Ebenen)
  ✓ Stage-Bezeichnungs-Konvention (_S<N>) eingeführt
  ✓ Freeze-Nummerierungs-Konvention ab Freeze 7 definiert
  ✓ Betakunde_01 Status PASSIV dokumentiert
  ✓ ASC (Betakunde_02) für Stage 7 vorbereitet
  ✓ Stage-Ende Dokumentation (GOV 10.9) erfüllt

Stage 6 ist vollständig abgeschlossen.
Stage 7 startet auf sauberer, konsolidierter, vollständig
dokumentierter Basis — im neuen Claude-Projekt.


================================================================================
FREEZE 6 — KONSOLIDIERT BESTÄTIGT | 2026-03-21
R+MUNI Blueprint | Stage 6 ABGESCHLOSSEN | Stage 7 VORBEREITET
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
