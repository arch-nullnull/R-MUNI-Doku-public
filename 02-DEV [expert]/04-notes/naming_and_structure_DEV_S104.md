================================================================================
NAMING AND STRUCTURE — R+MUNI BLUEPRINT
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : naming_and_structure_S104
Tag             : #naming #structure #ablage #s104 #global
Datum           : 2026-04-12
Stage           : S1.04 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Ablageort       : C:\Prototyping\R+MUNI Doku\00-internal\02-DEV [expert]\04-notes\naming_and_structure_S104.md
Erstellt durch  : EUMAXL
Letzte Änderung : 2026-04-12 — S104-Update | Basis: naming_and_structure_S102.md
================================================================================


================================================================================
ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument ist die Single Source of Truth für Namenskonventionen
und Ablagestruktur aller R+MUNI Dokumente und Templates.

Es gilt rollenübergreifend für alle Varianten.
Dieses Dokument ersetzt keine operativen Anleitungen (How2) und
keine normativen Regeln (GOV). Es beschreibt die Struktur — nicht den Prozess.


================================================================================
1. SUFFIX-LOGIK UND STAGE-HERKUNFT
================================================================================

Jedes R+MUNI Dokument trägt einen Stage-Suffix. Dieser macht die
Herkunft und den Reifestand eines Dokuments direkt lesbar.

  _S104        Stage 1.04 — aktueller Standard
  _S103        Stage 1.03 — vorheriger Standard
  _S102        Stage 1.02 — vorheriger Standard
  _S101        Stage 1.01 — vorheriger Standard
  _S8          Stage 1.00 — erste Beta mit Außenwirkung (S8 = pre Beta Struktur | out of date)

Hinweis S10nc: GOV und AI Driven Methode wurden in Stage 1.03 auf einen
tool-agnostischen Stand gebracht. Dokumente mit _S10nc sind Übergangsartefakte
aus dieser Konsolidierung — kein eigener Stage-Stand.

Grundregel: Suffix nie weglassen. Ohne Suffix ist kein Versionskontext erkennbar.


================================================================================
2. ABLAGESTRUKTUR — ÜBERSICHT
================================================================================

── 2.1 ROOT-EBENE ───────────────────────────────────────────────────────────────

Wurzel: C:\Prototyping\

  R+MUNI\              Produktiv-Repo — Modell, Skripte, Artefakte
  R+MUNI Apps\         Eigenständige Applikationen rund um R+MUNI
  R+MUNI Archiv\       Archivierte Stände und ZIP-Snapshots
  R+MUNI Custo\        Kundenprojekte — eigenständig geführt, anonymisiert
  R+MUNI DEV\          DEV-Arbeitsumgebung (nicht publiziert)
  R+MUNI Doku\         Dokumentation
  R+MUNI Installer\    Installationspakete
  R+MUNI Norm\         Normen, Standards, Referenzdokumente
  R+MUNI TEMP\         Temporäre Arbeitsdateien


── 2.2 R+MUNI DOKU — INTERNE STRUKTUR ──────────────────────────────────────────

Wurzel: C:\Prototyping\R+MUNI Doku\

  R+MUNI_DOKU-01R+MUNI.txt    Überblick-Datei auf Root-Ebene

  00-internal\                 Ausschließlich EUMAXL — sync mit non-public GitHub Repo (GOV 10.2)
  └─ siehe 2.3

  (kein separates public-Repo auf dieser Ebene — Public-Ableitungen
   gehen direkt ins R+MUNI Produktiv-Repo unter 99-doku\)


── 2.3 R+MUNI DOKU — 00-INTERNAL ───────────────────────────────────────────────

Ausschließlich EUMAXL — sync mit non-public GitHub Repo (GOV 10.2).

  .gitattributes
  .gitignore
  Kostenrechnung.xlsx
  LICENSE
  README.md
  structure_doku_00-internal.txt

  00-CARD [fun]\               CARD-Variante — eigenständig (GOV 10.3), siehe 2.5
  01-R+MUNI [normal]\          R+MUNI-Variante — eigenständig (GOV 10.3)
  02-DEV [expert]\             DEV-Variante — vollständig, GOV-konform
  99-CFG [info]\               Konfig- und Referenzdateien (Mappings, Normen)


── 2.4 02-DEV [expert] — DETAILSTRUKTUR ─────────────────────────────────────────

Interne DEV-Arbeitsgrundlage. Vollständig, GOV-konform. Basis für alle Ableitungen.

  LICENSE
  R+MUNI_DOKU-DEV.txt

  00-governance\
  01-principles\
  02-how2\
  03-rosetta_stone\

  04-notes\
  |   AI_DRIVEN_DEV_METHODE_DEV_S102.md
  |   BACKLOG_Template_DEV_S101.md
  |   DEV_Sprint_Template_S102.md
  |   FREEZE_N_Template.md
  |   how2_DEV_Template_S101.md
  |   naming_and_structure_S104.md           ← dieses Dokument
  |   principles_Template_S101.md
  |   STAGE103_ZIELE_S103.md
  |   svg_inhalte.md
  |   SVG_MASTER_DEV_S102.md
  |   [weitere Templates und Notizen]
  |
  +---AI Driven Methodes\                    Historische Versionen der AI Driven Methode
  +---naming\                                Historische Naming-Dokumente
  \---old stages\                            Archivierte Stage-Dokumente (FREEZE, ZIELE, GOV)

  05-backlog\
  |   BACKLOG_AIOF_DEV_S103.md
  |   FREEZE_1_03.md
  |   STAGE104_ZIELE_S104.md
  |   [weitere Backlogs]

  06-sprints\
  |   DEV_Sprint_AIOF-ROLLENDEF_S104.md
  |   DEV_Sprint_INSTALLTXT_UPDATE_S104.md
  |   DEV_Sprint_README_INSTALL_UMBAU_S104.md
  |   DEV_Sprint_SVGREIHE_S104.md
  |   [weitere Sprint-Dokumente]
  |
  +---STAG 1.0x EXIT CLAUDE\                 Übergangsartefakte S10nc
  +---STAGE 3\  STAGE 4\  STAGE 5\
  +---STAGE 6\  STAGE 7\  STAGE 8\

  07-creative\


── 2.5 R+MUNI (PUBLIC REPO) ─────────────────────────────────────────────────────

Produktiv-Repo — GitHub-Repo R-MUNI. Modell, Skripte, Artefakte.

  .gitattributes
  .gitignore
  Install.txt
  LICENSE
  plugins.dat
  README.md
  root.cfg
  structure.txt
  structure_R+MUNI.txt

  00-model\
      00-archimate\
          00-archimateactive\     MUNI EA.archimate
          01-archimateactivesub\
          99-mappingmodel\
      01-bpmn\
          00-bpmnactive\
          99-bpmnMUNI\
      02-xyvision\

  01-artifacts\
      00-xml\                     Mappings, Sync, Master, Child, Import, Exports
      01-scripts\                 Python-Scripts — Reihen:
                                    ATL, CLE, CSV, ECM, FLW, HLP, M2B, NBX, SVG, XML
                                  jArchi-Scripts
      02-csv\                     Master CSVs, Mapping, Sync, Child, Import, Exports
      03-XLSX\                    Master XLSX, Mapping, Sync, Child, Import, Exports
      04-flow\                    Flow-Scripts, Mappings, Triggers
      05-reports\                 Report-Output (ArchiMate, BPMN, HTML)

  02-stages\
      model-scope.txt
      run-scope.txt
      run-scope_ReadMe.txt
      00-archimatearchive\
      01-bpmnarchive\
      02-xyarchive\
      99-logs\

  99-doku\                        Relevante Doku aus Doku public Bereich (CARD, MUNI, DEV)
      README.md
      structure_99-doku.txt
      svg_config.txt
      07-creative\
          00-flip\
          01-draw\
          01-images\
          02-r+muni\
          03-svg\
          04-logo\
          05-Werkzeugkasten\
          99-svg_TMP\


── 2.6 CARD (EIGENSTÄNDIGER BEREICH) ────────────────────────────────────────────

Eigenständig geführt (GOV 10.3). Ordnerstruktur folgt einem Kartenspiel-Thema.
Ablage innerhalb 00-internal unter 00-CARD [fun]\.

  00-General [gov]\

  01-Exile [principles]\

  02-Stack [how2]\

  03-Hand [rosetta_stone]\

  04-Library [notes]\

  05-Graveyard [backlog]\

  06-Battlefield [sprint]\

  07-illustration [creative]\


── 2.7 R+MUNI CUSTO ────────────────────────────────────────────────────────────

Kundenprojekte — eigenständig geführt, anonymisiert (GOV 9.5).
Kein Bestandteil des öffentlichen Repos. Ablage lokal unter C:\Prototyping\R+MUNI Custo\.

Jedes Kundenprojekt erhält einen eigenen Ordner mit eigener Ablagestruktur.
Übernahme von Erkenntnissen in DEV nur mit [CUSTO→RMUNI] Tag und Anonymisierung.


================================================================================
3. VARIANTEN — GÜLTIG AB STAGE 1.02
================================================================================

Vier Varianten gemäß AI Driven Methode Kap. 1. Führung gemäß GOV 10.3.

  DEV      Interne Arbeitsgrundlage — vollständig, GOV-konform.
           Basis für alle Ableitungen. Eigenständig geführt.

  EXPERT   Volle Norm-Konformität.
           On-demand aus DEV — nicht eigenständig geführt (GOV 10.3).

  R+MUNI   Produktivvariante — reduzierte Norm-Sprache, KMU-tauglich.
           Eigenständig geführt.

  CARD     Spielerischer Einstieg — minimal, keine Fachbegriffe.
           Eigenständig geführt mit eigener Ordnerstruktur (siehe 2.6).

Dateinamen-Kürzel ab S102:
  _DEV_    Development
  _EXP_    Expert
  _MUNI_   Produktivvariante
  _CARD_   Spielerischer Einstieg


================================================================================
4. NAMENSKONVENTION R-MUNI VS. R+MUNI
================================================================================

GitHub unterstützt kein +-Zeichen in Ordnernamen:

  R-MUNI-<Kürzel>    GitHub-Repo-Name (Sync-Umgebung)
  R+MUNI <Kürzel>    lokale Kundeninstallation


================================================================================
BEZÜGE
================================================================================

[[Global_GOV_DEV_S102]]              Normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   Methodik und Rollenkontext
[[STAGE104_ZIELE_S104]]              Stage-Ziele Phase 1.04
[[FREEZE_1_03]]                      Ausgangszustand Stage 104


================================================================================
naming_and_structure_S104 | 2026-04-12 | R+MUNI Blueprint | Stage 1.04
================================================================================
