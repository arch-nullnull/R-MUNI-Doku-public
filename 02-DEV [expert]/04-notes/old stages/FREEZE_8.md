================================================================================
FREEZE 8 — R+MUNI BLUEPRINT
Stage 8 – Beta 1.0 | Außenwirkung & Abschluss — Abschluss / Startpunkt Stage 1
================================================================================
Projekt             : R+MUNI Blueprint
Dokument            : FREEZE-8
Erstellt            : 2026-03-28
Stage               : 8 — ABGESCHLOSSEN
Status              : FREEZE BESTÄTIGT — Stage 8 vollständig
Vorgänger           : FREEZE-7 (2026-03-26)
Nachfolger          : FREEZE-1.x (Startpunkt Stage 1 — neues Claude-Projekt)
Erstellt durch      : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
FREEZE-NUMMERIERUNGS-KONVENTION
================================================================================

Freeze-Nummer = Startpunkt des gleichnamigen Stage (verbindlich ab Freeze 7)
  FREEZE-8   = autarke Wissensbasis für Stage 8 (abgeschlossen)
  FREEZE-1.x = autarke Wissensbasis für Stage 1 (Produktivbetrieb — folgt)

Dieses Dokument ist die vollständige, autarke Wissensbasis für ein neues
Claude-Projekt ab Stage 1. Es enthält alles was Claude benötigt um
inkrementelle Sprints in Stage 1 eigenständig durchzuführen — ohne
Nachladen von Scripts, Dev-Dokumentationen oder Vorgänger-Freeze-Dokumenten.

Dieses Dokument ersetzt für neue Claude-Sessions vollständig:
  - FREEZE-7.md
  - STAGE8_ZIELE_S8.md
  - Alle Stage-8-Sprint-Dokumentationen (als Erkenntnisse eingearbeitet)

Ergänzend bereitgestellt im neuen Projekt (nicht in diesem Dokument):
  - Global_GOV.md                (normative Governance — vollständig)
  - SCRIPT-BAUKASTEN.md          (Script-Konventionen)
  - structure.txt                (aktuelle Ordnerstruktur)
  - README.md                    (Außenperspektive — S8-Stand)
  - Install.txt                  (Stack & Setup — S8-Stand)
  - Sprint-DEV-Doku_Template_S8.md
  - Aktive Reihen-Principles (nach Sprint-Bedarf)


================================================================================
1. SYSTEMÜBERSICHT — WAS IST R+MUNI
================================================================================

R+MUNI ist ein Blueprint-System für Enterprise Architecture Management.
Es verbindet ArchiMate-Modellierung (Archi 5.8) mit strukturierter
Datenverarbeitung über Python-Scripts und Atlassian als optionales
Kundenfrontend.

Kernprinzip: Das Archi-Modell ist die Single Source of Truth.
Alle Artefakte (CSV, XML, XLSX) werden aus dem Modell abgeleitet.
Kein manueller Eingriff in abgeleitete Artefakte — nur im Modell selbst.

R+MUNI ist dauerhaft kostenlos für Endanwender.
Claude ist ein Entwicklungswerkzeug — kein Produktbestandteil.
Archi hat kein Kaufmodell — R+MUNI Kunden erhalten ein Geschenk-Abo
an den Archi-Entwickler als Wertschätzung.

NEU Stage 8:
  Beta 1.0 offiziell released — GitHub Release v1.0-beta (Tag: v1.0-beta).
  Zwei-Repo-Modell vollständig umgesetzt (Public + DEV).
  Associate-Terminologie konsequent eingeführt — USER-Begriff abgelöst.
  Erste Außenwirkung gestartet (LinkedIn silent beta).


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
Stage 8  FREEZE  — Beta 1.0 | Außenwirkung & Abschluss (abgeschlossen)
Stage 1  AKTIV   — Produktivbetrieb (neue Zählung — Titel folgt)

HINWEIS ZUR STAGE-ZÄHLUNG:
  Nach Stage 8 beginnt eine neue Zählung mit Stage 1.
  Stage 1 (neu) = Produktivbetrieb — kein Zusammenhang mit historischem Stage 1.
  Bezeichnung im Freeze-Dokument: Stage 1.x zur Unterscheidung.

Rückkopplungsschutz: Stage-3- bis Stage-8-Scripts sind read-only.
Keine Logikänderung ohne explizite GOV-Freigabe.
Erweiterungen in Stage 1 (neu) sind immer additiv, nie modifizierend.


================================================================================
3. ORDNERSTRUKTUR (STAGE-5-STANDARD — FIXIERT AB FREEZE 5.5)
================================================================================

<rootfolder>\
  root.cfg                        Einzige Konfigurationsquelle
  .gitignore                      Blueprint-spezifisch (S8-Standard, neu gebaut)
  README.md                       S8-Stand — Associate-Terminologie, Außenperspektive
  Install.txt                     S8-Stand — Associate-Terminologie, Stack aktuell
  structure.txt                   Aktuelle Ordnerauflistung (generiert)

  00-model\                       Archi-Modell (read-only für Scripts)
    00-archimate\
      00-archimateactive\         Aktives Archi-Modell (MUNI EA.archimate)
                                  Archi schreibt log-0.txt + log-0.txt.lck
                                  direkt neben das Modell — in .gitignore erfasst
      01-archimateactivesub\      Submodelle (MUNI FLOW, MUNI IMPO)
      99-mappingmodel\            OEF Mapping-Modell (ECM-Reihe)
    01-bpmn\
    02-xyvision\

  01-artifacts\                   Alle abgeleiteten Artefakte
    00-xml\
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
    02-csv\
      00-master\                  elements.csv, relations.csv, properties.csv
      01-mapping\                 csvmapping.txt
      02-sync\
      03-child\
      04-import\
      99-exports\
    03-XLSX\
    04-flow\                      FLW-Reihe + flowmapping.txt + flowtriggers.txt
    05-reports\                   Archi HTML Reports (HLP09 Server)

  02-stages\
    model-scope.txt               Laufzeit — in .gitignore
    run-scope.txt                 Laufzeit — in .gitignore
    00-archimatearchive\
    01-bpmnarchive\
    02-xyarchive\
    99-logs\                      ALLE Logs — in .gitignore

  R+MUNI Doku-public\
    00-governance\
    01-principles\
    02-how2\
    03-rosetta_stone\
    04-notes\
    visuals\

  R+MUNI Doku-internal\
    backlog\
    infocfg\
    sprints\

  R+MUNI Doku-creative\           Creative Assets (eigenes Repo)


================================================================================
4. KONFIGURATION — root.cfg
================================================================================

root.cfg ist die einzige Konfigurationsquelle.
Alle Scripts lösen Pfade daraus auf — niemals hardcoded.

Aufbau root.cfg:
  rootfolder=C:\...\r-muni        Absoluter Pfad zum Projektordner
  model=00-model
  artifacts=01-artifacts
  stages=02-stages
  scripts=01-artifacts\01-scripts

HLP00_resolve_root.py — zentrale Import-Bibliothek:
  from HLP00_resolve_root import get_root_cfg
  cfg = get_root_cfg()
  basepath = cfg["artifacts"]

File-Extension-Konvention (verbindlich ab Freeze 5.5):
  .py     Python Scripts
  .cfg    Konfiguration
  .txt    Workflow-Artefakt
  .md     Dokumentation
  .log    Debug-Log (nur in 02-stages\99-logs)
  .bak    Archi-Backup (nie in GitHub)
  .ajs    jArchi Scripts
  .svg    Visuelle Artefakte (in visuals\)


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

Status: READ-ONLY. Keine Änderungen in Stage 8.


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

Status: READ-ONLY. Keine Änderungen in Stage 8.


5.3 XML-Reihe (XML00–XML07) — XML-Verarbeitung
------------------------------------------------
  XML00–XML07 vollständig implementiert.
Status: READ-ONLY. Keine Änderungen in Stage 8.


5.4 M2B-Reihe (M2B00–M2B07) — Master to BPMN
-----------------------------------------------
  M2B00–M2B07 vollständig implementiert.
  M2B01-Fix aus Stage 5.0 aktiv.
Status: READ-ONLY. Keine Änderungen in Stage 8.


5.5 ATL-Reihe (ATL00–ATL02) — Atlassian Integration
------------------------------------------------------
  ATL00  Scope-Validierung
  ATL01  master.xml → ATL CSV
  ATL02  ATL CSV → Jira CSV (importfertig)

Jira-Import-Struktur: Komponente = ArchiMate Layer, Stichwort = Typ.
Status: READ-ONLY. Keine Änderungen in Stage 8.
Atlassian-Nutzung: nur auf explizite Aufforderung durch EUMAXL.


5.6 FLW-Reihe (FLW00–FLW02) — Scriptrunner / Flow-Steuerung
--------------------------------------------------------------
  FLW00  Scriptrunner (FLW00-scriptrunner.py) — trigger- und mappinggesteuert
  FLW01  Discover
  FLW02  Map Elements

Steuerung: flowmapping.txt + flowtriggers.txt
Python-Version: 3.14.2
Status: READ-ONLY. Keine Änderungen in Stage 8.


5.7 CLE-Reihe (CLE00–CLE53) — Cleaning Utilities
--------------------------------------------------
Schema: CLE00 Basis | CLE1x XML | CLE2x CSV | CLE3x XLSX | CLE4x Reports | CLE5x Stages
Zwei Modi: Modus A Ordner-Clean | Modus B Datei-Delete (CLE26)
WICHTIG: CLE-Scripts löschen sofort ohne Bestätigung. Kein Undo.
Status: READ-ONLY. Keine Änderungen in Stage 8.


5.8 ECM-Reihe (ECM00–ECM03) — EasyCSVMapper
---------------------------------------------
  ECM00  Umgebungs-Validierung
  ECM01  CSV-Felder → Artefakte
  ECM02  CSV → Mapping → CSV (via OEF Mapping-Modell)
  ECM03  ID-Merge

Mapping-Modell: 99-mappingmodel\ als ArchiMate OEF XML.
Status: READ-ONLY. Keine Änderungen in Stage 8.

Offener Folge-Sprint (zurückgestellt auf Stage 1):
  ECM-Script-Erweiterung (CSV10+) — SOURCE=CSV in run-scope.txt aktivieren.


================================================================================
6. ATLASSIAN FRONTEND — KUNDENKONFIGURATION
================================================================================

Atlassian Free Bundle (Confluence + Jira) als optionales Kunden-Interface.
Atlassian ist ADDON — nicht Default-Setup.
IST-Situation des Kunden bestimmt ob Atlassian gebraucht wird.

Atlassian MCP in Claude: nur auf explizite Aufforderung durch EUMAXL.
Jira läuft als primäres Tracking-Tool aus — GitHub wird primäre
Kommunikationsschiene in Stage 1.

Beta-Kunden Status (Stand Stage 8 Abschluss):
  Betakunde_01   Status: OFFBOARDED — operativ abgeschlossen.
                 Sprint-DEV-Abschlussdoku: verschoben → Stage 1.01 Beta.
                 Kein Blocker für Freeze-8.

  Betakunde_02   Status: AKTIV — vollständig ongeboardet.
  (ASC)          Surface: eigener Windows-Account (Rollentrennung GOV 13.8).
                 DEFAULT Setup vollständig, GitHub Sync aktiv, CSV00 grün.
                 Feedbackschleifen aktiv.
                 EUMAXL = Obmann = DEV in einer Person — Rollentrennung physisch.


================================================================================
7. GITHUB / VERSIONIERUNG
================================================================================

Zwei-Repo-Modell (vollständig umgesetzt Stage 8):
  Public Repo (Release):  Saubere, freigegebene Stände.
                          GitHub Release v1.0-beta aktiv (Tag: v1.0-beta).
                          URL bleibt stabil — externe Links gültig.
                          .gitignore: Blueprint-spezifisch S8-Standard.
                          DEV-Inhalte: nicht enthalten.

  DEV Repo (privat):      Vollständige History des bisherigen Public Repo.
                          Aktive Entwicklung ab sofort nur hier.
                          .gitignore: Blueprint-spezifisch S8-Standard
                                      (Archi-Modelle erlaubt).

History-Reset Public Repo (zurückgestellt):
  Orphan-Branch-Reset bewusst zurückgestellt bis offizieller Release.
  DEV Repo hat vollständige History als Sicherung.
  Kein Blocker für Stage 1.

.gitignore S8-Standard (neu gebaut, bewusst strukturiert):
  Aufbau: Applikationen → Einzelfiles → Ordner
  Applikationen: Windows/OS, Archi (inkl. log-0.txt), Obsidian, Python
  Einzelfiles:   Laufzeit-Scopes, generische Typen (.tmp, .log, .lck etc.)
  Ordner:        Laufzeit-Archive, Logs, abgeleitete Artefakte
  GitHub Desktop: Ergänzungen landen am Ende — bewusst Platz freigehalten
  Global einsetzbar — ein File für beide Repos
    (DEV: 00-model/ und *.archimate nicht ausgeschlossen)

GitHub Pages: aktiv (R+MUNI Doku-Portal öffentlich).

Kunden-Repo-Modell (etabliert Stage 7):
  Kunde erstellt eigenes Repo — gibt DEV Zugriff frei.
  Kein R+MUNI-seitiger Zugang zum Kundensystem erforderlich.

Grundsatz: Nur saubere, dokumentierte Zustände werden gepusht.
Keine automatischen Pushes aus Scripts.


================================================================================
8. OBSIDIAN — BLUEPRINT-NAVIGATIONSWERKZEUG
================================================================================

Obsidian ist das MD-basierte Navigationswerkzeug für den Blueprint.

Kernregeln:
  - Lesewerkzeug und Navigationshilfe — keine neue Logikschicht
  - Kein Eingriff in bestehende Dateistruktur oder Dateinamen
  - Vault liegt im Blueprint — portabel, kein Cloud-Zwang
  - .obsidian/ in .gitignore ausgeschlossen
  - SVG-Einbettung: nur externe Datei via ![[]] — kein Inline-SVG
  - Obsidian-interne Links: [[DocumentName]] Konvention

Keine Änderungen in Stage 8.


================================================================================
9. TOOLBAUKASTEN — TRANSPARENZ UND STRUKTUR
================================================================================

Tier-Struktur:
  MINIMAL    Pflichttools — R+MUNI läuft nicht ohne sie
  DEFAULT    Empfohlene Tools — Standard-Setup für alle Associate
  ADDON      Optionale Erweiterungen — nach Bedarf (Atlassian = ADDON)
  AGNOSTIC   Tool-unabhängige Komponenten

Kern-Stack (0 EUR):
  Archi 5.8 | Camunda Modeler | Python 3.9+ (aktuell 3.14.2)
  jArchi 1.11.0 | OpenJDK 11+
  Notepad++ | Git | GitHub Desktop | Obsidian | PowerShell 7
  Claude Pro | KeePass

Keine Änderungen am Stack in Stage 8.

Visuelle Assets:
  Toolbaukasten SVG-Kartendeck: toolbaukasten_kartendeck_S7_final.svg
  Geplant: Stable Diffusion + LoRA für MUNI-Figuren — Stage 1 oder später.
  Copilot: für visuelle Asset-Erstellung (Logo, Mascot) evaluiert —
           besser geeignet als ChatGPT für diesen Use Case.
           Evaluation-Backlog vorhanden, noch nicht formal ausgegeben.


================================================================================
10. DOKUMENTEN-TEMPLATES — BLUEPRINT STANDARD
================================================================================

Aktive Templates (Stand Stage 8):
  Sprint-DEV-Dokumentation        Sprint-DEV-Doku_Template_S8.md
  Stage-Ziele Dokument            Stage_Ziele_Template_S8.md
  GOV-Ergänzung                   GOV_Global_Template_S8.md
  Freeze-Dokument                 FREEZE_N_Template.md (NEU Stage 8)

  ASSOCIATE Templates (alle S8):
    ASSOCIATE_principles_Template_S8.md
    ASSOCIATE_How2_Template_S8.md
    ASSOCIATE_Sprint_Template_S8.md
    ASSOCIATE_Backlog_Template_S8.md
    ASSOCIATE_Notes_Template_S8.md

NEU Stage 8:
  FREEZE_N_Template.md — erstmals als eigenständige, wiederverwendbare
  Vorlage formalisiert. Abgeleitet aus FREEZE_7 und Stage-8-Praxis.
  Ablage: öffentliche Doku (durch EUMAXL).

Stage-Bezeichnungs-Konvention: Alle Dokumente im Beta-Zustand erhalten _S<N>.
  Ab Stage 1 (Produktivbetrieb): Konvention wird in Stage-1-Eröffnung neu definiert.

Einheitlicher Header-Standard: verbindlich ab Stage 7 für alle Dokumente.
ASSOCIATE als Zielgruppen-Begriff: vollständig im Blueprint verankert.

Dokumenttypen-Unterscheidung:
  Sprint-DEV-BACKLOG   = geplanter Sprint mit Ziel, Abgrenzung, GOV-Check
  Konzeptnotiz         = destillierte Erkenntnis, noch nicht spruchreif —
                         kein GOV-Overhead, kein Sprint erforderlich
  ASSOCIATE-Doku       = zielgruppen-spezifische Dokumentation


================================================================================
11. FEEDBACKSCHLEIFEN — KANALMODELL
================================================================================

Kernregel: "GitHub ist Quelle der Wahrheit.
            Jeder Kanal hat seine Zielgruppe.
            Jira und Confluence sind Spiegel — kein Sync-Zwang."

Kanal-Struktur:
  Interne DEV-Schleife:        Lokal first → GitHub DEV intern → Jira/Confluence
  Externe Feedback-Schleife:   GitHub Issues für externe DEV und Viewer
                               Portal für Kunden (strukturiert)
  Persönliches Feedback:       Confluence nur wenn EUMAXL triggert

Solo-DEV-Realität: EUMAXL = einziger DEV = Entscheider aller Kanäle.

NEU Stage 8:
  Jira läuft aus — GitHub wird primäre Kommunikationsschiene.
  Backlog.md = Jira-Eingabe wenn Jira noch verwendet wird.
  Jira-Sync: nur auf explizite Aufforderung — kein automatischer Reflex.
  GitHub Issues: primärer externer Feedback-Kanal ab Beta 1.0.


================================================================================
12. ZWEI-WELTEN-ENTSCHEID — INTERN / PUBLIC
================================================================================

Normativ gültig ab Stage 7. Strukturelle Umsetzung: Stage 1.

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
  Phase 1 — Beta 1.0 Paket: ABGESCHLOSSEN (Stage 8).
  Phase 2 — MGT Layout bauen: Stage 1 und folgende — eigener Sprint.

Grenze: PUBLIC-Welt ersetzt nicht die INTERN-Welt — sie ergänzt sie.
MUNIEA-148 in Jira: strukturelle GOV-Umsetzung Zwei-Welten — offen für Stage 1.


================================================================================
13. BETA-ONBOARDING UND OFFBOARDING — STAND STAGE 8
================================================================================

Offboarding (Sprint S7-Z1 + S8-Z5):
  Principles und How2 DEV vollständig dokumentiert (BETA_OFFBOARDING_*).
  Tier-basierte Offboarding-Logik etabliert.
  Betakunde_01: operativ abgeschlossen.
  Sprint-DEV-Abschlussdoku: verschoben → Stage 1.01 Beta.

Onboarding:
  MINIMAL-Tier als Pflicht-Einstieg.
  Erste Runde spielbar in unter 60 Minuten. Sichtbares Ergebnis.
  Atlassian ist ADDON — kein Default-Setup.
  Kunden-Repo-Modell: Kunde erstellt, gibt frei.
  Rollentrennung physisch erzwingbar (eigener Windows-User).

  Drei MGT-Setup-Varianten (Konzeptnotiz — noch nicht umgesetzt):
    Setup 1: DEV Hardcore — volle GOV, audit-fest
    Setup 2: Human Biz — seriöser Mittelweg, KMU ohne Compliance-Zwang
    Setup 3: MGT Leicht — Verein, privat, spielerisch

NEU Stage 8:
  README + Install.txt vollständig auf Associate-Terminologie migriert.
  Onboarding ohne EUMAXL-Begleitung als Ziel erreicht (S8-Z3).


================================================================================
14. README UND ÖFFENTLICHE DOKUMENTATION
================================================================================

README.md (S8-Stand):
  - Außenperspektive vollständig — verständlich ohne Begleitung
  - Associate-Terminologie konsequent (USER-Begriff abgelöst)
  - Ehrlichkeit beibehalten: Beta = Beta, Esel steht auf wackeligen Beinen
  - Drei Rollen dokumentiert: Expert / Associate / MGT
  - Toolbaukasten-Übersicht mit Links
  - Script-Reihen-Übersicht
  - Dank & Anerkennung inkl. Nadine Rossa (visuelle Inspiration)
  - Claude als Pair-Partner explizit genannt

Install.txt (S8-Stand):
  - Associate-Terminologie
  - Stack aktuell
  - DEV-spezifische Infos erhalten

Release Notes v1.0-beta:
  - Erstellt Stage 8 — direkt im GitHub Release hinterlegt
  - Charakter: ehrlich, kurz, kein Marketing
  - Inhalt: Was ist drin, was noch nicht, Voraussetzungen, Einstieg

ASSOCIATE als Zielgruppen-Begriff: vollständig im Blueprint verankert.


================================================================================
15. AI-DRIVEN DEVELOPMENT METHODIK — STAND STAGE 8
================================================================================

Methodik-Dokument: AI_DRIVEN_DEV_METHODE_S8.md
Vorgänger: AI_DRIVEN_DEV_METHODE_S7-final.md

Neu in Stage 8 (Kap. 9, 11, 12, 15, 16.3, 17 — S8-Vorbereitung):
  Kap. 9    Grenzen erweitert — chirurgische Eingriffe als Standard
  Kap. 11   Rollen-Parallelbetrieb — Beta-Kanal präzisiert
  Kap. 12   Konzeptnotiz als eigenständiger Typ bestätigt
  Kap. 15   Kontext-Optimierung — Mittelmaß-Prinzip, README+Install als Pflicht
  Kap. 16.3 Verhaltenstransparenz — auf Wunsch aktivierbar
  Kap. 17   Tool-Rollentrennung — Copilot-Rolle präzisiert

Erkenntnisse Stage 8 (in Methodik eingearbeitet oder bewusst nicht):
  ✓ 3 von 4 Stage-7-Restpunkten bereits in S7-final vorhanden
  ✓ Überkorrektur-Reflex: betrifft nicht Claude-Zusammenarbeit — kein Einbau
  ✓ Jira-Sync-Neuausrichtung: implizit durch Workflow gelöst — kein separater Eintrag
  ✓ Backlog.md = Jira-Eingabe wenn Jira verwendet — als Praxis etabliert

Soft-Erkenntnisse Stage 8 (in EUMAXL-Speicher — methodisch zu besprechen):
  - Session-Überlastung bei Header-Updates: absehbar, bei Massenupdates einplanen
  - Session-Abbrüche bei langen Reihen: Richtwert max. 10er Script-Reihen pro Session
  - Ordner außerhalb Root R+MUNI: zu subjektiv für Claude entscheidbar —
    EUMAXL entscheidet, Claude führt aus
  - Projektfolder-Inhalt: README + Install + structure sind Pflicht neben GOV/Freeze

Claude-Nutzung in R+MUNI (Rahmenbedingungen Stand S8):
  Bereitgestellte Dokumente minimal:
    - FREEZE-8-Dokument (dieses Dokument)
    - Global_GOV.md
    - SCRIPT-BAUKASTEN.md
    - structure.txt
    - README.md + Install.txt
    - Aktive Sprint-Dokumente (laufende Arbeit)
    - Principles + How2 der aktiven Reihe (nach Sprint-Bedarf)

  Nicht initial laden:
    - Einzelne Scripts (.py)
    - Dev-Dokumentationen vergangener Sprints
    - Rosetta Stone Dokumente (nur bei Onboarding neuer Personen)
    - Mehrere Sprint-Dokumentationen gleichzeitig

  KI-Tool-Rollentrennung:
    Claude     Vollständiger Blueprint-Kontext, GOV-konform.
               Primär für alle technischen und konzeptionellen Arbeiten.
               Atlassian MCP: nur auf explizite Aufforderung.
    Copilot    Bewusst kontextfrei — keine R+MUNI-Dokumente.
               Visuelle Assets, Exploration, Sales-Dokumentation.
               Erkenntnisse fließen als [BETA→RMUNI] kontrolliert zurück.
               Für Logo/Mascot-Workflow besser geeignet als ChatGPT.


================================================================================
16. GOVERNANCE-ECKPFEILER FÜR NEUE SPRINTS
================================================================================

Jeder Sprint in Stage 1 folgt diesen GOV-Regeln (Kurzform):

GOV 10.3  Zulässige Auslöser: Bugfix, Erweiterung, Kundenbedarf,
          Strukturbereinigung, Entwicklerwunsch

GOV 10.5  Fachlicher Mehrwert muss explizit benennbar sein.
          Keine implizite GOV-Änderung durch Seiteneffekte.

GOV 10.6  Ziel explizit und überprüfbar definiert bevor Umsetzung startet.

GOV 10.7  Zwischenschritte dokumentieren (reihenweise, nachvollziehbar).

GOV 10.8  Dev-Doku erstellen für jede Entwicklungsaktivität.
          Verpflichtend für Nachvollziehbarkeit — nicht auditpflichtig.

GOV 10.9  Stage-Ende Dokumentation: fällig bei Stage-Gesamtabschluss.

GOV 10.10 Keine GOV-Regel darf stillschweigend aufgehoben werden.

Rückkopplungsschutz (absolut):
  - Stage-3- bis Stage-8-Scripts: read-only, kein Eingriff
  - Keine Logikänderung ohne Stage-Entscheid
  - Neue Funktionen: eigene Stages oder Spin-outs
  - Bugfixes: explizite Freigabe + Dokumentation

Rollentrennung (GOV 13):
  - R+MUNI DEV-Rolle strikt getrennt von anderen Rollen
  - ASC-Rolle (Obmann) strikt getrennt von DEV-Rolle
  - Externe Erkenntnisse nur mit [BetaKunde→RMUNI] Tag transferieren
  - Anonymisierungspflicht für alle externen Inhalte

Session-Regel (ab Stage 7):
  In stabilen Kontexten kann eine Session-Regel eine dokumentierte Regel
  ersetzen wenn Auslöser klar und Kontext stabil ist.
  Kein Backlog-Eintrag nötig — GOV bleibt schlank.

NEU Stage 8 — Verhaltensregeln für Claude:
  - Scope-Disziplin: kein strategisches Reinterpretieren, keine adjacenten
    Erweiterungen ohne explizite Freigabe
  - Kurze/neutrale Antworten von EUMAXL = Zustimmung, kein Expansions-Trigger
  - Freies Denken/Exploration von EUMAXL = kein impliziter Arbeitsauftrag
  - Verhaltensänderungen explizit melden — keine stille Adaptation
  - Atlassian MCP: nur auf explizite Aufforderung
  - Jira-Sync: nur auf explizite Aufforderung
  - Bei "Copilot Anfällen" (Kontext-Drift): sauberer Session-Restart mit
    explizitem GOV-Reload ist der etablierte Recovery-Weg


================================================================================
17. OFFENE PUNKTE — BEWUSST IN STAGE 1 VERSCHOBEN
================================================================================

17.1 BKO1-Offboarding Sprint-DEV-Doku
  - Operativer Teil abgeschlossen — Sprint-DEV-Abschlussdoku ausstehend
  - Verschoben → Stage 1.01 Beta (nächste Woche)
  - Kein Blocker für Freeze-8

17.2 Public Repo History-Reset (Orphan Branch)
  - Bewusst zurückgestellt bis offizieller Release
  - Ziel: Notfall-Rückholung noch möglich während silent beta
  - DEV Repo hat vollständige History als Sicherung
  - Kein Blocker für Stage 1

17.3 ECM-Script-Erweiterung (CSV10+)
  - SOURCE=CSV in run-scope.txt aktivieren
  - Setzt SPRINT-CSV-Refactoring als Kontext voraus
  - Priorität: mittel

17.4 SPRINT-CSV-Refactoring
  - CSV10+, XLSX00+, MaM00+ aufbauen
  - GOV 7.5 Naming präzisieren
  - Priorität: mittel

17.5 Zwei-Welten-Umsetzung strukturell (MUNIEA-148)
  - GOV Global Erweiterung: Zwei-Welten-Regel verankern
  - Template-Kennzeichnung: INTERN / PUBLIC
  - Komplexitätswarnung: mindestens 2–3 fokussierte Sessions
  - Priorität: mittel — nicht dringend

17.6 MGT Layout Phase 2
  - Außenwelt, Kartensprache, neue Reihe
  - Erst wenn Phase 1 stabil läuft
  - Eigener Stage oder Sprint — nicht forcieren
  - Priorität: niedrig

17.7 ChatGPT Evaluations-Backlog
  - Auswertung des ChatGPT-Ausflugs (Logo/Mascot-Workflow) formell ausgeben
  - Copilot als bessere Alternative für diesen Use Case dokumentiert
  - Priorität: niedrig — bei Kapazität

17.8 LibreOffice Evaluations-Backlog
  - ASSOCIATE_Backlog_LibreOffice_Evaluierung_S8.md vorhanden
  - Block A: XLSX-Kompatibilität (CSV07, openpyxl)
  - Block B: TXT/CSV Delimiter-Verhalten (Windows regional)
  - O365 ADDON Evaluation: formal noch ausstehend, niedrige Priorität
  - Priorität: niedrig

17.9 BPMN Flows (Optional)
  - Additiv, kein Blocker
  - Nur bei Kapazität und Interesse

17.10 EXPERT und MGT Templates
  - EXPERT Templates noch nicht erstellt
  - MGT Templates — Phase 2

17.11 DEV Team fixieren
  - Vom Wunschkonzert zur realen Gruppe
  - Bewusst offen — kein Zeitdruck

17.12 O365-Integration
  - M365 Dev Account als isolierte Test-Umgebung
  - Zurückgestellt auf Stage 1 bei Kapazität
  - Priorität: niedrig

17.13 Beobachtungspunkt CSV98
  - CSV98 meldet 2 XLSX-Treffer
  - Report: 02-stages\99-logs\CSV98-clean_master_report.txt
  - Status: beobachten, kein akuter Handlungsbedarf

17.14 LinkedIn Kommunikationsstrategie (S8-Z2 — in Beobachtung)
  - Silent Beta aktiv: Logo im LinkedIn-Profil ohne Post
  - Post folgt nach Feedback-Beobachtung (3–14 Tage)
  - Entscheidung über Timing liegt bei EUMAXL
  - Kein Sprint-Zwang — organisch


================================================================================
18. STAGE 8 — ABSCHLUSSFESTSTELLUNG
================================================================================

Stage 8 — Beta 1.0 | Außenwirkung & Abschluss

Zielstatus (4 von 5 Pflichtzielen abgeschlossen, 1 verschoben):

  ✓ S8-Z1  Beta 1.0 Release
           GitHub Release v1.0-beta erstellt (Tag: v1.0-beta).
           README + Install.txt auf Associate migriert und finalisiert.
           Release Notes verfasst und im GitHub Release hinterlegt.
           Zwei-Repo-Modell vollständig umgesetzt (Public + DEV).
           .gitignore Blueprint-spezifisch neu gebaut (global einsetzbar).
           Block A (Doku-Bereinigung + Associate-Migration): abgeschlossen.
           Block B (README + Install.txt): abgeschlossen.
           Block C (Repo-Aufspaltung): abgeschlossen (History-Reset bewusst zurückgestellt).
           Block D (GitHub Release): abgeschlossen.

  ⏳ S8-Z2  Kommunikation nach außen
           LinkedIn silent beta aktiv — Logo im Profil.
           Post folgt nach Feedback-Beobachtung.
           Status: in Beobachtung — kein Blocker für Freeze.

  ✓ S8-Z3  Onboarding-Basis für externe Betakunden
           README und Install.txt vollständig auf Außenperspektive ausgerichtet.
           Associate-Terminologie konsequent umgesetzt.
           Onboarding ohne EUMAXL-Begleitung als Ziel erreicht.

  ✓ S8-Z4  AI-Driven Methodik Update
           3 von 4 Stage-7-Erkenntnissen waren bereits in S7-final enthalten.
           Überkorrektur-Reflex: betrifft nicht Claude — kein Einbau.
           Jira-Sync-Neuausrichtung: implizit durch Workflow gelöst.
           AI_DRIVEN_DEV_METHODE_S8.md: aktuell und vollständig.
           Keine Dokumentänderung nötig — Methodik spiegelt gelebte Realität.

  ➡️ S8-Z5  BKO1-Offboarding Doku
           Operativer Teil abgeschlossen.
           Sprint-DEV-Abschlussdoku: verschoben → Stage 1.01 Beta.

Optionale Ziele:
  — S8-OPT-1  BPMN Flows: nicht umgesetzt — kein Blocker
  — S8-OPT-2  MGT Prinzip experimentell: nicht umgesetzt — Phase 2
  — S8-OPT-3  Bugfixing reaktiv: keine gemeldeten Fehler
  — S8-OPT-4  GOV-Header-Review: nicht umgesetzt — Stage 1 bei Kapazität

Zusätzliche Erkenntnisse aus Stage 8 (nicht in STAGE8_ZIELE_S8.md):
  ✓ FREEZE_N_Template erstmals als eigenständige Vorlage formalisiert
  ✓ .gitignore Blueprint-spezifisch neu gebaut — bewusst strukturiert
  ✓ Zwei-Repo-Modell vollständig umgesetzt und validiert
  ✓ Copilot für visuelle Asset-Erstellung besser geeignet als ChatGPT (evaluiert)
  ✓ GitHub Desktop als primäres GUI-Tool für Repo-Operationen bestätigt
  ✓ PowerShell 7 bleibt für orphan-branch-Reset reserviert (gezielter Einsatz)
  ✓ Projektfolder-Pflichtinhalt als Standard etabliert

Stage-Ende Dokumentation (GOV 10.9): ERFÜLLT durch diesen Freeze.


================================================================================
19. FORMALE ABSCHLUSSFESTSTELLUNG
================================================================================

FREEZE-8 gilt als vollständige Baseline für Stage 1 (Produktivbetrieb), da:

  ✓ Stage-8-Ziele dokumentiert und bewertet (4/5 — Z5 bewusst verschoben, Z2 in Beobachtung)
  ✓ Alle abgeschlossenen Sprints in Erkenntnissen eingearbeitet
  ✓ Rückkopplungsschutz vollständig eingehalten (Stage-3 bis Stage-8 unberührt)
  ✓ Zwei-Repo-Modell vollständig umgesetzt
  ✓ GitHub Release v1.0-beta aktiv und öffentlich
  ✓ README + Install.txt Associate-konform und außentauglich
  ✓ .gitignore Blueprint-spezifisch neu gebaut
  ✓ FREEZE_N_Template erstmals formalisiert und abgelegt
  ✓ AI_DRIVEN_DEV_METHODE_S8.md aktuell
  ✓ Offene Punkte vollständig in Kapitel 17 dokumentiert
  ✓ GOV-Regeln für Stage 1 in Kapitel 16 festgehalten
  ✓ Freeze-Nummerierungs-Konvention eingehalten
  ✓ BKO1-Offboarding operativ abgeschlossen (Doku folgt Stage 1.01)
  ✓ LinkedIn silent beta aktiv — Außenwirkung gestartet

Stage 8 ist vollständig abgeschlossen.
Stage 1 (Produktivbetrieb) startet auf sauberer, konsolidierter, vollständig
dokumentierter Basis — im neuen Claude-Projekt.

Der Esel steht. 🧱


================================================================================
FREEZE 8 — BESTÄTIGT | 2026-03-28
R+MUNI Blueprint | Stage 8 ABGESCHLOSSEN | Stage 1 (Produktivbetrieb) VORBEREITET
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
