================================================================================
NAMING AND STRUCTURE — R+MUNI BLUEPRINT
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : naming_and_structure_S10nc
Tag             : #naming #structure #ablage #s10nc #global
Datum           : 2026-04-06
Stage           : S1.02 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Ablageort       : C:\Prototyping\R+MUNI Doku\R+MUNI Doku-internal\04-notes\naming_and_structure_S10nc.md
Erstellt durch  : EUMAXL
Letzte Änderung : 2026-04-06 — S10nc KI-Tool-Neutralisierung | Freigabe: EUMAXL
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

  _S10nc       Stage S10nc — neutralisierter Stand (KI-Tool-agnostisch)
  _S102        Stage 1.02 — vorheriger Standard
  _S101        Stage 1.01 — älterer Standard
  _S8          Stage 1.00 - erste Beta mit Außenwirkung (S8 = pre Beta Struktur | out of date)


Grundregel: Suffix nie weglassen. Ohne Suffix ist kein Versionskontext erkennbar.

================================================================================
2. ABLAGESTRUKTUR — ÜBERSICHT
================================================================================

── 2.1 ROOT-EBENE ───────────────────────────────────────────────────────────────

Wurzel: C:\Prototyping\

  R+MUNI\              Produktiv-Repo — Modell, Skripte, Artefakte
  R+MUNI Apps\         Eigenständige Applikationen rund um R+MUNI
  R+MUNI Archiv\       Archivierte Stände und ZIP-Snapshots
  R+MUNI DEV\          DEV-Arbeitsumgebung (nicht publiziert)
  R+MUNI Doku\         Dokumentation
  R+MUNI Installer\    Installationspakete
  R+MUNI Norm\         Normen, Standards, Referenzdokumente
  R+MUNI TEMP\         Temporäre Arbeitsdateien


── 2.2 R+MUNI DOKU-INTERNAL ─────────────────────────────────────────────────────

Ausschließlich EUMAXL — sync mit non-public GitHub Repo (GOV 10.2).

  LICENSE
  R+MUNI_DOKU-DEV.txt
  README.md

  00-governance\

  01-principles\

  02-how2\

  03-rosetta_stone\

  04-notes\

  05-backlog\

  06-sprints\

  07-creative

── 2.3 R+MUNI DOKU-PUBLIC ───────────────────────────────────────────────────────

Öffentlich zugänglich — reduzierte Ableitungen aus 00-internal.
Übernahme erfordert explizite Betreiber-Freigabe (GOV 10.4).

  00-governance\

  01-principles\

  02-how2\

  03-rosetta_stone\

  04-notes\

  05-backlog\

  06-sprints\

  07-creative\


── 2.4 R+MUNI (PUBLIC REPO) ─────────────────────────────────────────────────────

Produktiv-Repo — GitHub-Repo R-MUNI. Modell, Skripte, Artefakte.

  .gitattributes
  .gitignore
  Install.txt
  LICENSE
  README.md
  root.cfg
  structure.txt

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
      01-scripts\                 Python-Scripts (ATL, CLE, CSV, ECM, HLP, M2B, XML)
                                  jArchi-Scripts
      02-csv\                     Master CSVs, Mapping, Sync, Child, Import, Exports
      03-XLSX\                    Master XLSX, Mapping, Sync, Child, Import, Exports
      04-flow\                    Flow-Scripts, Mappings, Triggers
      05-reports\                 Report-Output (ArchiMate, BPMN, HTML)

  02-stages\
      model-scope.txt
      run-scope.txt
      00-archimatearchive\
      01-bpmnarchive\
      02-xyarchive\
      99-logs\

  99-doku\                 Platz für relevante Doku aus Doku public Bereich (CARD, MUNI, DEV)
      LICENSE
      README.md


── 2.5 CARD (EIGENSTÄNDIGER BEREICH) ────────────────────────────────────────────

Eigenständig geführt (GOV 10.3). Ordnerstruktur folgt einem Kartenspiel-Thema.

  00-General\          [gov]

  01-Exile\            [principles]

  02-Stack\            [how2]

  03-Hand\             [rosetta_stone]

  04-Library\          [notes]

  05-Graveyard\        [backlog]

  06-Battlefield\      [sprint]

  07-illustration\     [creative]


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
           Eigenständig geführt mit eigener Ordnerstruktur (siehe 2.5).

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

[[Global_GOV_DEV_S10nc]]              Normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S10nc]]   Methodik und Rollenkontext


================================================================================
naming_and_structure_S10nc | 2026-04-06 | R+MUNI Blueprint | Stage S10nc
================================================================================
