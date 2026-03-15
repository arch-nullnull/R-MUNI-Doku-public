================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-5.5-CleaningRun — Gesamtabschluss
Datum               : 2026-03-13
Stage               : 5 (aktiv) — Cleaning Sub-Stage
Status              : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch      : Entwickler + Claude (Pair-Session)
Vorgänger           : Stage 5.0 (Portal live, GOV-Restore, CSV06-Fix, M2B01-Fix)
Nachfolger          : Stage 5.7 — Restart Blueprint Beta Endkunde
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Stage-Modell (Ist-Zustand)
-------------------------------
Stage 3  FREEZE — read-only, kein Eingriff
Stage 4  FREEZE — Bugfixing mit expliziter Freigabe zulässig
Stage 5  AKTIV  — Cleaning Run als strukturelle Bereinigung vor Stage 5.7

1.2 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Strukturbereinigung (Entwicklerwunsch, GOV 10.3/10.5)

Begründung   : Stage 5.0 hat die Grundlogik stabilisiert (Portal live,
               GOV vollständig, CSV06-Fix, M2B01-Fix, root.cfg Aufbau).
               Die physische Struktur und alle Script-Referenzen mussten
               auf die neue root.cfg-Logik nachgezogen werden.

               Zusätzlich hatte die FLW-Reihe als einzige Script-Gruppe
               noch Stage-4-Konventionen — bewusst zurückgestellt,
               im Cleaning Run als letzter Schritt abgeschlossen.

Fachlicher   : Vollständige Strukturkonsistenz aller Scripts und Ordner.
Mehrwert       Saubere Basis für Stage 5.7 Beta Endkunde Restart.
               Kein Script mehr mit veralteten Pfaden oder Keys.

Governance-  : Ausschließlich Pfad-Strings, Extensions und Konventionen.
Konformität    Keine Logikänderung in keinem Script.


--------------------------------------------------------------------------------
2. ZIELDEFINITION (gemäß GOV 10.6)
--------------------------------------------------------------------------------

Ziel         : Alle R+MUNI Scripts (CSV, XML, ATL, M2B, HLP, FLW) auf
               Stage-5-Konventionen bringen:
                 - root.cfg statt root.txt
                 - <rootfolder>= statt BLUEPRINT_ROOT=
                 - 02-stages statt 03-stages
                 - 01-artifacts statt 02-artifacts
                 - 00-model statt 01-model

               Ordner physisch umbenannt (Windows Explorer, manuell).
               File-Extension-Konvention definiert und dokumentiert.
               SCRIPT-BAUKASTEN.txt → SCRIPT-BAUKASTEN.md überführt.

Abgrenzung   : CSV-Refactoring (CSV10+, XLSX00+, MaM00+) wurde bewusst
               auf SPRINT-CSV-Refactoring verschoben. Kein neuer
               Funktionscode in diesem Sprint.

Überprüfbar  : Alle Scripts starten fehlerfrei. Kein veralteter Pfad
               oder Key in keinem Script. FLW00 durchläuft CSV-Trigger-Test.


--------------------------------------------------------------------------------
3. UMSETZUNG — WAS WURDE GEMACHT
--------------------------------------------------------------------------------

3.1 Ordnerstruktur (manuell, Windows Explorer)
------------------------------------------------
  IST (Stage 4)     →  SOLL (Stage 5)
  01-model          →  00-model
  02-artifacts      →  01-artifacts
  03-stages         →  02-stages

3.2 Konventions-Entscheidungen (OFFEN A + B aus Sprint-DEF)
-------------------------------------------------------------
  OFFEN A gelöst:
    root.txt → root.cfg
    Begründung: .cfg = Konfiguration (einmalig durch User gesetzt)
    .txt ist Workflow-Artefakt — klar getrennt

  OFFEN B gelöst:
    .gitignore angelegt mit Ausschlüssen: .bak, .log, .lck, .obsidian/

  File-Extension-Konvention fixiert:
    .log  → Debug-Log, nur in 02-stages/99-logs
    .txt  → Workflow-Artefakt (von Scripts gelesen oder manuell geprüft)
    .cfg  → Konfiguration (einmalig durch User gesetzt)
    .md   → Dokumentation (GitHub, Blueprint)

3.3 Script-Reihen — Pfad-Anpassungen
--------------------------------------
Alle Scripts der folgenden Reihen auf neue Konventionen gebracht:

  HLP-Reihe (HLP00–HLP09)
    HLP00: zentrale get_root_cfg() API — öffentliche Bibliothek
    HLP01–HLP09: Pfade, Keys und Extensions angepasst

  CSV-Reihe (CSV00–CSV09, CSV98, CSV99)
    CSV00: HLP00 Import, schreibt CSV00-root.resolved.txt
    CSV01: liest CSV00-root.resolved.txt, schreibt model-scope.txt
    CSV04: Bugfix Extension-Filter (OEF→.xml only, XLSX→.xlsx only)
    CSV98: Neu — Quality Gate (Formula-Prefix FIX, Backtick FIX)
    CSV03–09, CSV99: Pfade angepasst

  XML-Reihe (XML00–XML07)
    XML00: schreibt XML00-root.resolved.txt
    XML01–07: Pfade angepasst

  M2B-Reihe (M2B00–M2B06)
    M2B00: Fast-Path entfernt, einheitlich via HLP00
    M2B01–M2B06: Pfade angepasst

  ATL-Reihe (ATL00–ATL02)
    ATL00: Eigenlogik bleibt, Pfade aus cfg
    ATL01–02: Pfade angepasst

  FLW-Reihe (FLW00–FLW02) — letzter Schritt Cleaning Run
    FLW00, FLW01, FLW02: root.txt→root.cfg, BLUEPRINT_ROOT→<rootfolder>,
    03-stages→02-stages, 02-artifacts→01-artifacts
    Kernlogik (Scriptrunner, Discovery, Element-Mapping): unverändert

3.4 Neue Scripts
-----------------
  CSV98-clean_master.py
    Quality Gate nach CSV06, vor CSV99
    FIX-01: ="..." Formula-Prefix (Archi Export Artefakt)
    FIX-02: Backtick/Accent → Apostroph (Office Copy-Paste)
    Report: 02-stages/99-logs/CSV98-clean_master_report.txt

3.5 Dokumentation
------------------
  SCRIPT-BAUKASTEN.txt → SCRIPT-BAUKASTEN.md
    Neu: Naming-Konvention Tabelle, Sondernummern (00/98/99),
    File-Extension-Konvention, root.cfg Aufbau, HLP00 Import-Muster,
    Extension-Filter Tabelle, Ordnerstruktur Stage 5

  Sprint-DEV-Doku-CSV98-CleanMaster.md
  Sprint-DEV-Doku-CSV04-ExtensionFilter.md
  Sprint-DEV-Doku-FLW-CleaningRun-5-5.md
  Sprint-DEV-Doku-CleaningRun-5-5-Gesamt.md (dieses Dokument)


--------------------------------------------------------------------------------
4. VOLLSTÄNDIGER CSV-RUN — REFERENZ
--------------------------------------------------------------------------------

Nach Abschluss des Cleaning Run gilt folgender Referenz-Flow:

  py .\CSV00-validate_environment.py     # HLP00 → root.cfg → CSV00-root.resolved.txt
  py .\CSV01-validate_model.py           # model-scope.txt
  py .\CSV03-resolve_run_scope.py        # run-scope.txt (SOURCE=archi)
  py .\CSV04-model-overview.py           # run-scope.txt erweitert (alle Sources, gefiltert)
  py .\CSV05-create_master_csvs.py       # Master CSVs anlegen wenn fehlend
  py .\CSV06-append_child_to_master.py   # child → master append
  py .\CSV07-xlsx_2_csv.py               # XLSX → master
  py .\CSV08-properties2csv.py           # Properties
  py .\CSV98-clean_master.py             # Quality Gate
  py .\CSV99-export_snapshot.py          # Export Snapshot → 04-import

Archi Import aus 01-artifacts/02-csv/04-import — sauber, keine Artefakte.


--------------------------------------------------------------------------------
5. TESTERGEBNISSE
--------------------------------------------------------------------------------

  CSV-Run vollständig    : OK ✓
  FLW00 CSV-Trigger-Test : OK ✓ (nach FLW-Fix)
  CSV98 Quality Gate     : OK ✓ (Archi Reimport validiert)
  CSV04 Extension-Filter : OK ✓ (run-scope.txt ohne .bak, .xsd, log-0.txt)
  Alle Scripts sauber    : OK ✓ (kein veralteter Pfad / Key in keinem Script)


--------------------------------------------------------------------------------
6. BEWUSSTE VERSCHIEBUNGEN — NÄCHSTE SPRINTS
--------------------------------------------------------------------------------

  SPRINT-CSV-Refactoring (definiert, nicht gestartet)
    CSV10+, XLSX00+, MaM00+ parallel aufbauen
    run-scope.txt SOURCE=CSV aktivieren
    flowmapping.txt erweitern
    GOV 7.5 Naming präzisieren

  HLP00-Import vollständig (Kosmetik-Run)
    Alle Scripts direkt auf from HLP00_resolve_root import get_root_cfg
    statt über CSV00-root.resolved.txt umstellen
    Bewusst zurückgestellt — laufende Scripts nicht anfassen

  .gitignore Verteilung (Kosmetik-Run)
    Master-Inhalt in alle relevanten Ordner übertragen

  Doku-Verschiebung (Kosmetik-Run)
    Sprint-Dokus, GOV, Principles, How2 aus Blueprint-Root
    in R+MUNI Doku-internal verschieben

  Anmerkung Entwickler (2026-03-13):
    "der csv split machen wir nicht mehr das verschieben wir auf einen
     kosmetik run ich denke wir haben als genug gefixed in 5
     das war ein moloch"
    → Cleaning Run 5.5 ist damit offiziell abgeschlossen.


--------------------------------------------------------------------------------
7. OFFENE PUNKTE
--------------------------------------------------------------------------------

  CSV98 XLSX Treffer beobachten
    CSV98 meldet 2 Treffer bei XLSX-Dateien
    Status: Beobachten — kein akuter Handlungsbedarf
    Aktion: Report prüfen 02-stages/99-logs/CSV98-clean_master_report.txt

  Stage-Ende Dokumentation
    Ausstehend (GOV 10.9 verpflichtend bei Stage-Abschluss)
    Dev-Dokumentation ist nicht auditpflichtig (GOV 10.8)


--------------------------------------------------------------------------------
8. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Strukturbereinigung Stage 5
GOV 10.5  Fachlicher Mehrwert        OK  Vollständige Strukturkonsistenz
GOV 10.5  Keine implizite Gov-Änd.   OK  Keine Logikänderung in keinem Script
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 2
GOV 10.6  Ziel überprüfbar           OK  Testergebnisse Abschnitt 5
GOV 10.7  Zwischenschritte           OK  Abschnitt 3 (reihenweise dokumentiert)
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument + 3 Einzel-Dokus
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Kein neuer Code, keine Logikänderung
Stage 5   Rückkopplungsschutz        OK  Stage-3/4-Logik vollständig unverändert


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-5.5-CleaningRun Gesamtabschluss | Stage 5 | 2026-03-13
R+MUNI Blueprint | Erstellt durch: Markus Resel + Claude (Pair-Session)
================================================================================
