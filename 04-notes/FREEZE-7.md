================================================================================
FREEZE 7 — R+MUNI BLUEPRINT
Stage 7 – Real Beta & Ecosystem Expansion — Abschluss / Startpunkt Stage 8
================================================================================
Projekt             : R+MUNI Blueprint
Dokument            : FREEZE-7
Erstellt            : 2026-03-26
Stage               : 7 — ABGESCHLOSSEN
Status              : FREEZE BESTÄTIGT — Stage 7 vollständig
Vorgänger           : FREEZE-6_konsolidiert (2026-03-21)
Nachfolger          : FREEZE-8 (Startpunkt Stage 8 — neues Claude-Projekt)
Erstellt durch      : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
FREEZE-NUMMERIERUNGS-KONVENTION
================================================================================

Ab Freeze 7 gilt verbindlich (entschieden 2026-03-21):
  Freeze-Nummer = Startpunkt des gleichnamigen Stage
  FREEZE-7 = autarke Wissensbasis für Stage 7 (abgeschlossen)
  FREEZE-8 = autarke Wissensbasis für Stage 8 (folgt)

Dieses Dokument ist die vollständige, autarke Wissensbasis für ein neues
Claude-Projekt ab Stage 8. Es enthält alles was Claude benötigt um
inkrementelle Sprints in Stage 8 eigenständig durchzuführen — ohne
Nachladen von Scripts, Dev-Dokumentationen oder Vorgänger-Freeze-Dokumenten.

Dieses Dokument ersetzt für neue Claude-Sessions vollständig:
  - FREEZE-6_konsolidiert.md
  - STAGE7_ZIELE.md
  - Alle Stage-7-Sprint-Dokumentationen (als Erkenntnisse eingearbeitet)

Ergänzend bereitgestellt im neuen Projekt (nicht in diesem Dokument):
  - Global_GOV.md                (normative Governance — vollständig)
  - SCRIPT-BAUKASTEN.md          (Script-Konventionen)
  - structure.txt                (aktuelle Ordnerstruktur)
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
Stage 7  FREEZE  — Real Beta & Ecosystem Expansion (abgeschlossen)
Stage 8  AKTIV   — [Titel wird in Stage-8-Eröffnung definiert]

Rückkopplungsschutz: Stage-3- bis Stage-7-Scripts sind read-only.
Keine Logikänderung ohne explizite GOV-Freigabe.
Erweiterungen in Stage 8 sind immer additiv, nie modifizierend.


================================================================================
3. ORDNERSTRUKTUR (STAGE-5-STANDARD — FIXIERT AB FREEZE 5.5)
================================================================================

<rootfolder>\
  root.cfg                        Einzige Konfigurationsquelle
  .gitignore                      .bak, .log, .lck, .obsidian/ ausgeschlossen
  README.md                       Aktualisiert Stage 7 — Kundenstruktur + GitHub-Sync-Modell
  structure.txt                   Aktuelle Ordnerauflistung (generiert)

  00-model\                       Archi-Modell (read-only für Scripts)
    00-archimate\
      00-archimateactive\         Aktives Archi-Modell (MUNI EA.archimate)
      01-archimateactivesub\      Submodelle (MUNI FLOW, MUNI IMPO)
      99-mappingmodel\            OEF Mapping-Modell (ECM-Reihe)
    01-bpmn\
    02-xyvision\

  01-artifacts\                   Alle abgeleiteten Artefakte
    00-xml\                       XML-Verarbeitung
      00-master\                  master.xml
      01-mapping\
      02-sync\
      03-child\
        00-archimatechild\
        01-bpmnchild\
        02-xychild\
      04-import\
      99-exports\
    01-scripts\                   ALLE Python-Scripts
    02-csv\                       CSV-Artefakte
      00-master\                  elements.csv, relations.csv, properties.csv
      01-mapping\
      02-sync\
      03-child\
      04-import\
      99-exports\
    03-XLSX\
    04-flow\                      FLW-Reihe + flowmapping.txt + flowtriggers.txt
    05-reports\                   Archi HTML Reports (HLP09 Server)

  02-stages\
    model-scope.txt
    run-scope.txt
    00-archimatearchive\
    01-bpmnarchive\
    02-xyarchive\
    99-logs\                      ALLE Logs (.log), resolved.txt Dateien

  R+MUNI Doku-public\             Blueprint-Dokumentation (öffentlich)
    00-governance\
    01-principles\
    02-how2\
    03-rosetta_stone\
    04-notes\
    visuals\                      NEU Stage 7 — SVG-Grafiken (Toolbaukasten etc.)

  R+MUNI Doku-internal\           Interne Dokumentation
    backlog\
    infocfg\
    sprints\                      Sprint-DEV-Dokumentationen

  R+MUNI Doku-creative\           Creative Assets (eigenes Repo)


================================================================================
4. KONFIGURATION — root.cfg
================================================================================

root.cfg ist die einzige Konfigurationsquelle.
Alle Scripts lösen Pfade daraus auf — niemals hardcoded.

Aufbau root.cfg:
  <rootfolder>=C:\...\r-muni        Absoluter Pfad zum Projektordner
  <model>=00-model
  <artifacts>=01-artifacts
  <stages>=02-stages
  <scripts>=01-artifacts\01-scripts

HLP00_resolve_root.py — zentrale Import-Bibliothek:
  from HLP00_resolve_root import get_root_cfg
  cfg = get_root_cfg()
  basepath = cfg["<artifacts>"]

File-Extension-Konvention (verbindlich ab Freeze 5.5):
  .py     Python Scripts
  .cfg    Konfiguration
  .txt    Workflow-Artefakt
  .md     Dokumentation
  .log    Debug-Log (nur in 02-stages\99-logs)
  .bak    Archi-Backup (nie in GitHub)
  .ajs    jArchi Scripts
  .svg    Visuelle Artefakte (NEU Stage 7 — in visuals\)


================================================================================
5. SCRIPT-REIHEN — ÜBERSICHT UND STATUS
================================================================================

5.1 HLP-Reihe (HLP00–HLP10) — Hilfsfunktionen
------------------------------------------------
  HLP00  Zentrale Root-Auflösung (öffentliche Bibliothek)
  HLP01  Kopieren
  HLP02  Verschieben
  HLP03  Generischer Ordner-Clean
  HLP04  Verzeichnis-Log
  HLP05  Kontext-Struktur
  HLP06  Backup erstellen
  HLP07  Restore
  HLP08  Struktur → XML/CSV
  HLP09  Report Server (lokaler HTTP-Server für Archi HTML Reports)
  HLP10  Property Definitions bereinigen

Status: Stage-5-Konventionen vollständig. Alle Tests grün. READ-ONLY.


5.2 CSV-Reihe (CSV00–CSV09, CSV98, CSV99) — Kern-Datenverarbeitung
--------------------------------------------------------------------
  CSV00  Umgebungs-Validierung → CSV00-root.resolved.txt
  CSV01  Modell-Validierung → model-scope.txt
  CSV02  Leer (Platzhalter)
  CSV03  Run-Scope auflösen → run-scope.txt (SOURCE=archi)
  CSV04  Modell-Übersicht → run-scope.txt erweitert + gefiltert
  CSV05  Master-CSVs anlegen
  CSV06  Child → Master append
  CSV07  XLSX → Master CSV
  CSV08  Properties → CSV
  CSV09  master.xml → CSV
  CSV98  Quality Gate (Formula-Prefix FIX, Backtick→Apostroph FIX)
  CSV99  Export Snapshot → 04-import

Referenz-Flow:
  CSV00 → CSV01 → CSV03 → CSV04 → CSV05 → CSV06 →
  CSV07 → CSV08 → CSV98 → CSV99

Status: Stage-5-Konventionen vollständig. Archi Reimport validiert OK. READ-ONLY.


5.3 XML-Reihe (XML00–XML07) — XML-Verarbeitung
------------------------------------------------
  XML00–XML07 vollständig implementiert.
Status: READ-ONLY.


5.4 M2B-Reihe (M2B00–M2B07) — Master to BPMN
-----------------------------------------------
  M2B00–M2B07 vollständig implementiert.
  M2B01-Fix aus Stage 5.0 aktiv.
Status: READ-ONLY.


5.5 ATL-Reihe (ATL00–ATL02) — Atlassian Integration
------------------------------------------------------
  ATL00  Scope-Validierung
  ATL01  master.xml → ATL CSV
  ATL02  ATL CSV → Jira CSV (importfertig)

Jira-Import-Struktur: Komponente = ArchiMate Layer, Stichwort = Typ.
Status: READ-ONLY.


5.6 FLW-Reihe (FLW00–FLW02) — Scriptrunner / Flow-Steuerung
--------------------------------------------------------------
  FLW00  Scriptrunner (trigger- und mappinggesteuert)
  FLW01  Discover
  FLW02  Map Elements

Steuerung: flowmapping.txt + flowtriggers.txt
Status: READ-ONLY.


5.7 CLE-Reihe (CLE00–CLE53) — Cleaning Utilities
--------------------------------------------------
Schema: CLE00 Basis | CLE1x XML | CLE2x CSV | CLE3x XLSX | CLE4x Reports | CLE5x Stages
Zwei Modi: Modus A Ordner-Clean | Modus B Datei-Delete (CLE26)
WICHTIG: CLE-Scripts löschen sofort ohne Bestätigung. Kein Undo.
Status: READ-ONLY.


5.8 ECM-Reihe (ECM00–ECM03) — EasyCSVMapper
---------------------------------------------
  ECM00  Umgebungs-Validierung
  ECM01  CSV-Felder → Artefakte
  ECM02  CSV → Mapping → CSV (via OEF Mapping-Modell)
  ECM03  ID-Merge

Mapping-Modell: 99-mappingmodel\ als ArchiMate OEF XML.
Status: READ-ONLY. Produktiv getestet Stage 6.

Offener Folge-Sprint (zurückgestellt auf Stage 8):
  ECM-Script-Erweiterung (CSV10+) — SOURCE=CSV in run-scope.txt aktivieren.


================================================================================
6. ATLASSIAN FRONTEND — KUNDENKONFIGURATION
================================================================================

Atlassian Free Bundle (Confluence + Jira) als Kunden-Interface.
Vollständig auf Free-Tier lauffähig.

Atlassian ist ADDON — nicht Default-Setup.
Entscheid Stage 7: Atlassian wird nicht reflexartig als Standard-Onboarding
eingesetzt. IST-Situation des Kunden bestimmt ob Atlassian gebraucht wird.

Beta-Kunden Status (Stand Stage 7 Abschluss):
  Betakunde_01   Status: OFFBOARDED — bilateral abgestimmt (Nahverhältnis).
                 Atlassian Reset + vereinfachtes Q&A durchgeführt.
                 1 Master + 3 Sub-Cases identifiziert.
                 Führungskräfte informiert, Feedback ausstehend.
                 Operative Deaktivierung läuft — kein Blocker für Freeze.
                 Sprint-DEV-Doku folgt nach operativem Abschluss.

  Betakunde_02   Status: AKTIV — vollständig ongeboardet.
  (ASC)          Surface: eigener Windows-Account (Rollentrennung GOV 13.8).
                 DEFAULT Setup vollständig, GitHub Sync aktiv, CSV00 grün.
                 Feedbackschleifen aktiv (GitHub Issues + Jira Support Portal).
                 EUMAXL = Obmann = DEV in einer Person — Rollentrennung physisch.


================================================================================
7. GITHUB / VERSIONIERUNG
================================================================================

GitHub Sync: aktiv und sauber.
.gitignore: .bak, .log, .lck, .obsidian/ ausgeschlossen.

Zwei-Repo-Prinzip (etabliert Stage 5, erweitert Stage 7):
  DEV Repo (intern):    R+MUNI Entwicklungsumgebung — normativ, GOV-konform
  Download Repo (public): Beta Release Paket — außenwirksam, eigenständig

GitHub Pages: aktiv (R+MUNI Doku-Portal öffentlich).

Kunden-Repo-Modell (NEU Stage 7):
  Kunde erstellt eigenes Repo — gibt DEV Zugriff frei.
  Kein R+MUNI-seitiger Zugang zum Kundensystem erforderlich.
  Erkenntnisse fließen in Onboarding-Dokumentation ein.

Grundsatz: Nur saubere, dokumentierte Zustände werden gepusht.
Keine automatischen Pushes aus Scripts.


================================================================================
8. OBSIDIAN — BLUEPRINT-NAVIGATIONSWERKZEUG
================================================================================

Etabliert Stage 6, erweitert Stage 7.

Obsidian ist das MD-basierte Navigationswerkzeug für den Blueprint.
Kernregeln:
  - Lesewerkzeug und Navigationshilfe — keine neue Logikschicht
  - Kein Eingriff in bestehende Dateistruktur oder Dateinamen
  - Vault liegt im Blueprint — portabel, kein Cloud-Zwang
  - .obsidian/ in .gitignore ausgeschlossen
  - SVG-Einbettung: nur externe Datei via ![[]] — kein Inline-SVG

NEU Stage 7 (S7-Z6):
  Obsidian Vault umgebaut, Ordnerstruktur bereinigt, GitHub Sync aktiv.
  SVG-Visualisierungen eingebettet via ![[toolbaukasten_kartendeck_S7_final.svg]]

How2-Dokumentation:
  OBS_How2_DEV_S6.md      DEV-Perspektive
  OBS_How2_USER_S6.md     USER-Perspektive


================================================================================
9. TOOLBAUKASTEN — TRANSPARENZ UND STRUKTUR
================================================================================

Tier-Struktur:
  MINIMAL    Pflichttools — R+MUNI läuft nicht ohne sie
  DEFAULT    Empfohlene Tools — Standard-Setup für alle User
  ADDON      Optionale Erweiterungen — nach Bedarf (Atlassian = ADDON)
  AGNOSTIC   Tool-unabhängige Komponenten

NEU Stage 7 (S7-Z8):
  Toolbaukasten visuell aufbereitet als SVG-Kartendeck.
  Drei Visualisierungs-Ebenen: MINIMAL DECK / CORE / SIDEBOARD.
  Ablage: R+MUNI Doku-public\visuals\toolbaukasten_kartendeck_S7_final.svg
  Einbettung in TOOLBAUKASTEN_Visual_S7.md für Obsidian.

Dokumentation:
  TOOLBAUKASTEN_principles_S6.md     DEV-Referenz
  TOOLBAUKASTEN_How2_DEV_S6.md       Developer-Anleitung
  TOOLBAUKASTEN_How2_USER_S6.md      User-Anleitung
  TOOLBAUKASTEN_Visual_S7.md         NEU — Obsidian-Einbettungsdatei


================================================================================
10. DOKUMENTEN-TEMPLATES — BLUEPRINT STANDARD
================================================================================

Templates definiert Stage 6, erweitert Stage 7.

Bestehende Templates (S6):
  Sprint-DEV-Dokumentation     Sprint-DEV-Doku_Template_S6.md
  Sprint-DEV-Backlog           Sprint-DEV-BACKLOG_Template_S6.md (+ S7 Konvention)
  Stage-Ziele Dokument         Stage_Ziele_Template_S6.md
  GOV-Ergänzung                GOV_Global_Template_S6.md
  How2 USER                    how2_USER_Template_S6.md
  How2 DEV                     how2_DEV_Template_S6.md  (Header-Update Stage 7)
  Freeze-Dokument              dieses Dokument als Referenz

NEU Stage 7 (S7-Z5):
  ASSOCIATE Templates (5 Stück):
    ASSOCIATE_principles_Template_S7.md
    ASSOCIATE_How2_Template_S7.md
    ASSOCIATE_Sprint_Template_S7.md
    ASSOCIATE_Backlog_Template_S7.md
    ASSOCIATE_Notes_Template_S7.md
  Konzeptnotiz-Format (kein GOV-Overhead, für nicht-spruchreife Erkenntnisse)

Stage-Bezeichnungs-Konvention: Alle Dokumente im Beta-Zustand erhalten _S<N>.
Einheitlicher Header-Standard ab Stage 7 für alle neuen Dokumente.
ASSOCIATE als Zielgruppen-Begriff eingeführt und im Blueprint verankert.

Dokumenttypen-Unterscheidung (NEU Stage 7):
  Sprint-DEV-BACKLOG   = geplanter Sprint mit Ziel, Abgrenzung, GOV-Check
  Konzeptnotiz         = destillierte Erkenntnis, noch nicht spruchreif


================================================================================
11. FEEDBACKSCHLEIFEN — KANALMODELL
================================================================================

Etabliert Stage 6, auf S7-Realität nachgezogen (Sprint S7-Z3).

Kernregel: "GitHub ist Quelle der Wahrheit.
            Jeder Kanal hat seine Zielgruppe.
            Jira und Confluence sind Spiegel — kein Sync-Zwang."

Kanal-Struktur nach Zielgruppe:
  Interne DEV-Schleife:        Lokal first → GitHub intern → Jira/Confluence
  Externe Feedback-Schleife:   Portal für Kunden (strukturiert)
                               GitHub Issues für externe DEV und Viewer
                               Beides landet bei GitHub — EUMAXL routet intern
  Persönliches Feedback:       Confluence nur wenn EUMAXL triggert
                               Handlungspunkt: Jira, Doku oder nichts

Solo-DEV-Realität: EUMAXL = einziger DEV = Entscheider aller Kanäle.
Jira/Confluence-Sync: nur bei Freeze oder expliziter Anweisung.

Dokumentation:
  HOW2_Feedbackschleifen_S7.md     NEU — nachgezogen auf S7-Stand
  HOW2_Feedbackschleifen_S6.md     Vorgänger (als Referenz erhalten)


================================================================================
12. ZWEI-WELTEN-ENTSCHEID — INTERN / PUBLIC
================================================================================

NEU Stage 7 (Sprint S7-Z2) — gilt ab sofort normativ.

R+MUNI trennt konsequent zwei Welten:
  INTERN (DEV-Welt):   Blueprint, GOV, Principles, Scripts, Sprint-Dokumentation.
                       Für DEV-Mitglieder und Betreiber.
                       Sprache: technisch, präzise, GOV-konform.

  PUBLIC (MGT Layout): Außenwirkung, Einstieg ohne Rulebook-Wissen.
                       Für Kunden, potenzielle Beta-Kunden, nicht-technische Leser.
                       Sprache: direkt, ergebnisorientiert, ohne Jargon.

MGT-Prinzip (Magic: The Gathering Analogie):
  Einfache erste Karten — sofort spielbar ohne Regelwerk.
  Emergent Complexity — wer tiefer will findet den Weg.
  Kein falsches Spiel — nur ein anderes.

Phasen:
  Phase 1 — Beta 1.0 Paket (Stage 7 Abschluss):
    Installierbar ohne Begleitung. Test: Lädt es jemand runter
    der nur die Sprache spricht — ohne dass EUMAXL nachhelfen muss?
  Phase 2 — MGT Layout bauen (Stage 8 und folgende):
    Außenwelt. Kartensprache. Neue Reihe. Eigene Welt. Nicht mischen.

Strukturelle Umsetzung (GOV, Templates, Dokumentenreihen) zurückgestellt
auf eigenen Sprint nach Stage 7 — MUNIEA-148 in Jira offen.

Grenze: PUBLIC-Welt ersetzt nicht die INTERN-Welt — sie ergänzt sie.
        User-Reihe (How2 USER etc.) bleibt bis Phase 2 erhalten.


================================================================================
13. BETA-ONBOARDING UND OFFBOARDING — STAND STAGE 7
================================================================================

Offboarding (Sprint S7-Z1):
  Principles und How2 DEV vollständig dokumentiert (BETA_OFFBOARDING_*_S7).
  Tier-basierte Offboarding-Logik etabliert.
  Sonderfall Nahverhältnis in Principles Kapitel 7.1 dokumentiert.
  Operative Durchführung Betakunde_01 läuft — Sprint-DEV-Doku folgt.

Onboarding (Sprint S7-Z2):
  Neues Onboarding-Modell: MINIMAL-Tier als Pflicht-Einstieg.
  Erste Runde spielbar in unter 60 Minuten. Sichtbares Ergebnis.
  Atlassian ist ADDON — kein Default-Setup mehr.
  Kunden-Repo-Modell: Kunde erstellt, gibt frei.
  Rollentrennung physisch erzwingbar (eigener Windows-User).
  Lessons Learned BKO1 direkt eingearbeitet:
    LL-01: Adoption-Signal vor Setup validieren
    LL-02: MINIMAL-Tier als harter Scope-Limiter
    LL-03: Session nur mit echter Beteiligung zählen
    LL-04: Checkpoint bei instabilem Kundenkontext

  Drei MGT-Setup-Varianten identifiziert (Konzeptnotiz, noch nicht umgesetzt):
    Setup 1: DEV Hardcore — volle GOV, audit-fest
    Setup 2: Human Biz — seriöser Mittelweg, KMU ohne Compliance-Zwang
    Setup 3: MGT Leicht — Verein, privat, spielerisch


================================================================================
14. README UND ÖFFENTLICHE DOKUMENTATION
================================================================================

NEU Stage 7 (Sprint S7-Z5+Z6 kombiniert).

README_hauptrepo.md:        Aktualisiert — Stage 7, M2B korrigiert
README_Doku-public.md:      NEU — ersetzt index.md + leere README

ASSOCIATE als Zielgruppen-Begriff:
  Externe Mitstreiter die nicht DEV sind und nicht Betakunde sind.
  Viewer, Interessenten, externe Contributor — mit eigenem Onboarding-Pfad.

Einheitlicher Header-Standard: alle neuen Dokumente ab Stage 7.

Offene Punkte (bewusst zurückgestellt):
  - GOV-Header-Review am Stage-Ende noch ausstehend
  - EXPERT Templates noch nicht erstellt
  - MGT Templates — Phase 2

Beta 1.0 Release:
  Ablage: Download-Repo (public) — nicht im DEV-Repo
  Inhalt: Extraktion/Verdichtung der README-Informationen, global formuliert
  Verknüpfungen: README + Toolbaukasten-Principles + Onboarding-Einstieg
  Charakter: Kommunikationsmittel, kein Blueprint-Artefakt, keine GOV-Wirkung


================================================================================
15. AI-DRIVEN DEVELOPMENT METHODIK — STAND STAGE 7
================================================================================

Methodik-Dokument: AI_DRIVEN_DEV_METHODE_S7-final.md
Vorgänger: AI_DRIVEN_DEV_METHODE_S6.md → S7 → S7U1 → S7-final

Neu in Stage 7 (Kapitel 16+17 in S7-final):
  16.1 Chat-Aufteilung nach Funktion (Zielbegleitung / Methodik / Sprint)
  16.2 Chat-Initialisierung mit expliziter Rolle — Investition gegen Drift
  16.3 Verhaltenstransparenz als Methodik-Werkzeug (auf Wunsch aktivierbar)
  16.4 Strukturierungsmuster und wann es bremst — Struktur auf Abruf
  16.5 Erkenntnisse sofort sichern — nicht als losen Chat-Inhalt lassen
  17.x Tool-Rollentrennung: Claude (DEV), Copilot (Exploration/Sales)

Erkenntnisse aus Stage 7 Chats (noch nicht in S7-final eingearbeitet):
  — Überkorrektur-Reflex bei neutralem Feedback vermeiden
  — Exploration ≠ Transfer (explizite Anweisung nötig)
  — Backlog ≠ Konzeptnotiz (GOV-Overhead nur bei spruchreifen Sprints)
  — SVG-Drift durch Neugenerierung → chirurgische Änderung als Standard
  Aufnahme erfolgt in Stage 8 Sprint AI-Driven-Methodik-Update.

Claude-Nutzung in R+MUNI (Rahmenbedingungen unverändert):
  Bereitgestellte Dokumente minimal:
    - FREEZE-7-Dokument (dieses Dokument)
    - Global_GOV.md
    - SCRIPT-BAUKASTEN.md
    - structure.txt
    - Principles + How2 der aktiven Reihe (nach Sprint-Bedarf)

  Nicht initial laden:
    - Einzelne Scripts (.py)
    - Dev-Dokumentationen vergangener Sprints
    - Rosetta Stone Dokumente (nur bei Onboarding neuer Personen)


================================================================================
16. GOVERNANCE-ECKPFEILER FÜR NEUE SPRINTS
================================================================================

Jeder Sprint in Stage 8 folgt diesen GOV-Regeln (Kurzform):

GOV 10.3  Zulässige Auslöser: Bugfix, Erweiterung, Kundenbedarf,
          Strukturbereinigung, Entwicklerwunsch

GOV 10.5  Fachlicher Mehrwert muss explizit benennbar sein.
          Keine implizite GOV-Änderung durch Seiteneffekte.

GOV 10.6  Ziel explizit und überprüfbar definiert bevor Umsetzung startet.

GOV 10.7  Zwischenschritte dokumentieren (reihenweise, nachvollziehbar).

GOV 10.8  Dev-Doku erstellen für jede Entwicklungsaktivität.
          Verpflichtend für Nachvollziehbarkeit — nicht auditpflichtig.

GOV 10.9  Stage-Ende Dokumentation: fällig bei Stage-8-Gesamtabschluss.

GOV 10.10 Keine GOV-Regel darf stillschweigend aufgehoben werden.

Rückkopplungsschutz (absolut):
  - Stage-3/4/5/6/7-Scripts: read-only, kein Eingriff
  - Keine Logikänderung ohne Stage-Entscheid
  - Neue Funktionen: eigene Stages oder Spin-outs
  - Bugfixes: explizite Freigabe + Dokumentation

Rollentrennung (GOV 13):
  - R+MUNI DEV-Rolle strikt getrennt von anderen Rollen
  - ASC-Rolle (Obmann) strikt getrennt von DEV-Rolle
  - Externe Erkenntnisse nur mit [BetaKunde→RMUNI] Tag transferieren
  - Anonymisierungspflicht für alle externen Inhalte

Session-Regel (NEU Stage 7):
  In stabilen Kontexten kann eine Session-Regel eine dokumentierte Regel
  ersetzen wenn Auslöser klar und Kontext stabil ist.
  Kein Backlog-Eintrag nötig — GOV bleibt schlank.


================================================================================
17. OFFENE PUNKTE — BEWUSST IN STAGE 8 VERSCHOBEN
================================================================================

17.1 BKO1-Offboarding Sprint-DEV-Doku (kein Blocker)
  - Operative Durchführung läuft (Feedback ausstehend)
  - Sprint-DEV-Abschlussdoku folgt nach operativem Abschluss
  - Keine Auswirkung auf R+MUNI-Kernlogik

17.2 ECM-Script-Erweiterung (CSV10+)
  - SOURCE=CSV in run-scope.txt aktivieren
  - Setzt SPRINT-CSV-Refactoring als Kontext voraus

17.3 SPRINT-CSV-Refactoring
  - CSV10+, XLSX00+, MaM00+ aufbauen
  - GOV 7.5 Naming präzisieren

17.4 Zwei-Welten-Umsetzung (MUNIEA-148)
  - GOV Global Erweiterung: Zwei-Welten-Regel verankern
  - Template-Kennzeichnung: INTERN / PUBLIC
  - User-Reihe einordnen: "Phase 2 pending — MGT Layout"
  - Komplexitätswarnung: mindestens 2–3 fokussierte Sessions
  - Priorität: Mittel — nicht dringend

17.5 MGT Layout Phase 2
  - Außenwelt, Kartensprache, neue Reihe
  - Erst wenn Phase 1 (Beta 1.0) steht
  - Eigener Stage oder Sprint — nicht in Stage 8 forcieren

17.6 DEV Team fixieren (S7-Z7)
  - Vom Wunschkonzert zur realen Gruppe
  - Kein Chat gefunden — bewusst offen gelassen oder verschoben

17.7 AI-Driven Methodik Update (S7-Z9 Restpunkte)
  - 4 Erkenntnisse aus Stage 7 Chats noch nicht eingearbeitet
  - Aufnahme in eigenem Sprint Stage 8

17.8 BPMN Flows (S7-Z10 — OPTIONAL)
  - Additiv, kein Blocker
  - Nur wenn Kapazität vorhanden

17.9 O365-Integration
  - M365 Dev Account als isolierte Test-Umgebung
  - OneDrive / SharePoint / Teams Anbindung evaluieren
  - Zurückgestellt auf Stage 8 bei Kapazität

17.10 GOV-Header-Review
  - Alle bestehenden Dokumente auf einheitlichen Header prüfen
  - Kein Blocker — am Stage-8-Ende oder bei Kapazität

17.11 EXPERT und MGT Templates
  - EXPERT Templates noch nicht erstellt
  - MGT Templates — Phase 2

17.12 Beobachtungspunkt
  - CSV98 meldet 2 XLSX-Treffer
  - Report: 02-stages\99-logs\CSV98-clean_master_report.txt
  - Status: beobachten, kein akuter Handlungsbedarf


================================================================================
18. STAGE 7 — ABSCHLUSSFESTSTELLUNG
================================================================================

Stage 7 — Real Beta & Ecosystem Expansion

Zielstatus (10 von 11 Zielen abgeschlossen):

  ✓ S7-Z1  Betakunden Offboarding — Betakunde_01
           Principles + How2 DEV vollständig. Operative Durchführung
           läuft (bilateral, Nahverhältnis). Atlassian reset, vereinfachtes
           Q&A, 1 Master + 3 Sub-Cases. Führungskräfte informiert.
           Sprint-DEV-Doku folgt nach operativem Abschluss.

  ✓ S7-Z2  Betakunden Onboarding — Neue Struktur
           ASC (Betakunde_02) vollständig ongeboardet. DEFAULT Setup,
           CSV00 grün, GitHub Sync aktiv. Zwei-Welten-Entscheid normativ.
           Lessons Learned BKO1 eingearbeitet. Atlassian = ADDON.
           Umsetzung MGT-Layout → Stage 8.

  ✓ S7-Z3  Feedbackschleifen ausbauen
           Kanalmodell auf S7-Realität nachgezogen. GitHub Issues +
           Jira Support Portal im ASC-Betrieb validiert.
           HOW2_Feedbackschleifen_S7 erstellt.

  ✓ S7-Z4  GitHub Paketierung — Beta 1.0 Paket
           Aktueller Sprint/Doku-Stand = Beta 1.0 Basis.
           Download-Repo als separate PUBLIC-Welt definiert.

  ✓ S7-Z5  README & Dokumentationsbereich ausbauen
           README_hauptrepo.md + README_Doku-public.md aktualisiert.
           ASSOCIATE-Begriff eingeführt. 5 ASSOCIATE Templates erstellt.
           Install.txt Stage 7, Kunden-Repo-Modell dokumentiert.

  ✓ S7-Z6  Obsidian Vault öffentlich
           Vault umgebaut, bereinigt, GitHub Sync aktiv.
           SVG-Einbettungsstandard definiert.

  —  S7-Z7  DEV Team fixieren
           Kein Sprint durchgeführt. Bewusst offen — verschoben Stage 8.

  ✓ S7-Z8  Visuelle Aufbereitung Toolbaukasten
           SVG-Kartendeck erstellt (toolbaukasten_kartendeck_S7_final.svg).
           TOOLBAUKASTEN_Visual_S7.md für Obsidian.
           SVG-Drift-Erkenntnis dokumentiert.

  ✓ S7-Z9  AI-Driven Development Methodik Update
           AI_DRIVEN_DEV_METHODE_S7-final.md erstellt.
           Kapitel 16 (Chat-Struktur, Drift-Prävention) + Kapitel 17
           (Tool-Rollentrennung) neu. 4 Restpunkte → Stage 8.

  —  S7-Z10 BPMN Flows (OPTIONAL)
           Nicht umgesetzt — kein Blocker.

  ✓ S7-Z11 Bugfixing & Optimierung R+MUNI Core
           Laufend im ASC-Betrieb. Keine normativen Eingriffe.

Zusätzliche Erkenntnisse aus Stage 7 (nicht in STAGE7_ZIELE.md):
  ✓ Zwei-Welten-Entscheid normativ gültig — strukturelle Umsetzung Stage 8
  ✓ MGT-Prinzip im realen Kundenbetrieb validiert (ASC01 Emoji-Beweis)
  ✓ Kunden-Repo-Modell als Architekturmuster etabliert
  ✓ Session-Regel als GOV-Erweiterung dokumentiert
  ✓ SVG-Chirurgie als Arbeitsmodell für Datei-Eingriffe definiert
  ✓ Konzeptnotiz als eigenständiger Dokumenttyp eingeführt
  ✓ ASSOCIATE als Zielgruppen-Begriff im Blueprint verankert
  ✓ Drei MGT-Setup-Varianten konzeptionell entwickelt

Stage-Ende Dokumentation (GOV 10.9): ERFÜLLT durch diesen Freeze.


================================================================================
19. FORMALE ABSCHLUSSFESTSTELLUNG
================================================================================

FREEZE-7 gilt als vollständige Baseline für Stage 8, da:

  ✓ Stage-7-Ziele dokumentiert und bewertet (10/11 — Z7 bewusst verschoben)
  ✓ Alle abgeschlossenen Sprints in Erkenntnissen eingearbeitet
  ✓ Rückkopplungsschutz vollständig eingehalten
  ✓ Zwei-Welten-Entscheid normativ gültig dokumentiert
  ✓ ASC (Betakunde_02) vollständig ongeboardet und produktiv
  ✓ Kanalmodell Feedbackschleifen auf S7-Realität nachgezogen
  ✓ README + öffentliche Dokumentation Stage 7 aktualisiert
  ✓ Obsidian Vault bereinigt und synchronisiert
  ✓ Toolbaukasten visuell aufbereitet (SVG + Obsidian)
  ✓ AI_DRIVEN_DEV_METHODE_S7-final erstellt
  ✓ ASSOCIATE-Konzept und Templates eingeführt
  ✓ BKO1-Offboarding operativ eingeleitet (Doku folgt)
  ✓ Offene Punkte vollständig in Kapitel 17 dokumentiert
  ✓ GOV-Regeln für Stage 8 in Kapitel 16 festgehalten
  ✓ Freeze-Nummerierungs-Konvention eingehalten

Stage 7 ist vollständig abgeschlossen.
Stage 8 startet auf sauberer, konsolidierter, vollständig
dokumentierter Basis — im neuen Claude-Projekt.


================================================================================
FREEZE 7 — BESTÄTIGT | 2026-03-26
R+MUNI Blueprint | Stage 7 ABGESCHLOSSEN | Stage 8 VORBEREITET
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
