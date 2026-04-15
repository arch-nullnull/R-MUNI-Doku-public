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
  _S8          Stage 1.00 — erste Beta mit Außenwirkung (out of date)

Hinweis S10nc: GOV und AI Driven Methode wurden in Stage 1.03 auf einen
tool-agnostischen Stand gebracht. Dokumente mit _S10nc sind Übergangs-
artefakte aus dieser Konsolidierung — kein eigener Stage-Stand.

Grundregel: Suffix nie weglassen. Ohne Suffix ist kein Versionskontext erkennbar.


================================================================================
2. ABLAGESTRUKTUR — ÜBERSICHT
================================================================================

── 2.1 ROOT-EBENE ───────────────────────────────────────────────────────────────

Wurzel: C:\Prototyping\

  R+MUNI\              Produktiv-Repo — Modell, Skripte, Artefakte
  R+MUNI Apps\         Eigenständige Applikationen rund um R+MUNI
  R+MUNI Archiv\       Archivierte Stände und ZIP-Snapshots
  R+MUNI Custo\        Kundenprojekte — eigenständig, anonymisiert (GOV 9.5)
  R+MUNI DEV\          DEV-Arbeitsumgebung (nicht publiziert)
  R+MUNI Doku\         Dokumentation
  R+MUNI Installer\    Installationspakete
  R+MUNI Norm\         Normen, Standards, Referenzdokumente
  R+MUNI TEMP\         Temporäre Arbeitsdateien


── 2.2 R+MUNI DOKU ──────────────────────────────────────────────────────────────

Wurzel: C:\Prototyping\R+MUNI Doku\

Enthält alle Dokumentationsbereiche. Aufgeteilt in einen internen
und einen öffentlichen Bereich. Public-Ableitungen gehen direkt
in das Produktiv-Repo unter 99-doku\.

  00-internal\     Ausschließlich EUMAXL — non-public GitHub Repo (GOV 10.2)
                   Vier Unterbereiche nach Variante (siehe 2.3)


── 2.3 00-INTERNAL — VARIANTENBEREICHE ──────────────────────────────────────────

Jede Variante hat einen eigenen Bereich. Die Klammerbezeichnung
zeigt die inhaltliche Funktion des Bereichs.

  00-CARD [fun]\       CARD-Variante — spielerischer Einstieg
                       Ordnerstruktur folgt Kartenspiel-Thema (siehe 2.4)
                       Eigenständig geführt (GOV 10.3)

  01-R+MUNI [normal]\  R+MUNI-Variante — Produktivvariante, KMU-tauglich
                       Standard-Ordnerstruktur (00–07)
                       Eigenständig geführt (GOV 10.3)

  02-DEV [expert]\     DEV-Variante — vollständig, GOV-konform
                       Basis für alle Ableitungen
                       Eigenständig geführt (GOV 10.3)

  99-CFG [info]\       Konfig- und Referenzdateien — Mappings, Normen, Cheatsheets
                       Kein Dokumentationsbereich — reine Arbeitsablage


── 2.4 CARD-ORDNERSTRUKTUR ──────────────────────────────────────────────────────

CARD folgt einem Kartenspiel-Thema statt der Standard-Nummerierung.
Die inhaltliche Entsprechung zur Standardstruktur steht in Klammern.

  00-General\       [gov]
  01-Exile\         [principles]
  02-Stack\         [how2]
  03-Hand\          [rosetta_stone]
  04-Library\       [notes]
  05-Graveyard\     [backlog]
  06-Battlefield\   [sprint]
  07-illustration\  [creative]


── 2.5 STANDARD-ORDNERSTRUKTUR (DEV / R+MUNI) ───────────────────────────────────

DEV und R+MUNI folgen der nummerierten Standardstruktur.

  00-governance\
  01-principles\
  02-how2\
  03-rosetta_stone\
  04-notes\
  05-backlog\
  06-sprints\
  07-creative\


── 2.6 R+MUNI PRODUKTIV-REPO ────────────────────────────────────────────────────

GitHub-Repo R-MUNI. Modell, Skripte, Artefakte, Doku-Ableitungen.

  00-model\        ArchiMate-Modelle, BPMN-Modelle, XY-Vision
  01-artifacts\    Scripts, XML, CSV, XLSX, Flow, Reports
  02-stages\       Archiv-Stände, Logs
  99-doku\         Public-Ableitungen aus Doku (CARD, MUNI, DEV)
                   Unterbereich 07-creative\ für visuelle Assets


── 2.7 R+MUNI CUSTO ─────────────────────────────────────────────────────────────

Kundenprojekte. Eigenständig geführt, vollständig anonymisiert (GOV 9.5).
Kein Bestandteil des öffentlichen Repos.
Erkenntnisse nur mit [CUSTO→RMUNI] Tag in DEV übernehmen.


================================================================================
3. VARIANTEN UND TIERING
================================================================================

Vier Varianten gemäß AI Driven Methode Kap. 1. Führung gemäß GOV 10.3.

  DEV      Interne Arbeitsgrundlage — vollständig, GOV-konform.
           Basis für alle Ableitungen. Eigenständig geführt.

  EXPERT   Volle Norm-Konformität.
           On-demand aus DEV — nicht eigenständig geführt (GOV 10.3).

  R+MUNI   Produktivvariante — reduzierte Norm-Sprache, KMU-tauglich.
           Eigenständig geführt.

  CARD     Spielerischer Einstieg — minimal, keine Fachbegriffe.
           Eigenständig geführt mit eigener Ordnerstruktur (siehe 2.4).

Dateinamen-Kürzel:
  _DEV_    Development
  _EXP_    Expert
  _MUNI_   Produktivvariante
  _CARD_   Spielerischer Einstieg

Deprecated — werden über Stage-Überarbeitung entfernt:
  _ASSOCIATE_    alter Name für CARD
  _PUBLIC_       nicht mehr verwendet


================================================================================
4. NAMENSKONVENTION — DATEIEN
================================================================================

── 4.1 GRUNDREGEL ───────────────────────────────────────────────────────────────

Ist ein Template vorhanden → Template-Naming verwenden. Keine Ausnahme.
Templates werden über die Stages bereinigt und sind die verbindliche Basis.


── 4.2 PYTHON SCRIPTS ───────────────────────────────────────────────────────────

Schema:   <Reihe><Nr>-<Beschreibung>.py

Reihe     Großbuchstaben-Kürzel der Script-Reihe (ATL, CLE, CSV, ECM,
          FLW, HLP, M2B, NBX, SVG, XML, ...)
Nr        Zweistellige Nummer (00, 01, 02, ...)
Trennzeichen zwischen Nr und Beschreibung: Bindestrich (-)

Beispiele:
  NBX00-validate_environment.py
  SVG03-embed.py

Hinweis: Historische Scripts mit Unterstrich (z.B. HLP06_backup.py)
werden über die Stages auf das Bindestrich-Schema bereinigt.


── 4.3 ARCHI-INTERN (OBJEKTE UND VIEWS) ─────────────────────────────────────────

Schema:   <Präfix><Nr>-<Beschreibung>

Gilt für die Benennung von Elementen, Properties und Views
innerhalb des ArchiMate-Modells. Wird via jArchi Script geprüft
(liegt in 01-artifacts\01-scripts\jArchi\).

Beispiel:
  PRI04-Offene Normen und Guidelines

Abweichungen werden vom jArchi-Check als Fehler gemeldet.


── 4.4 FALLBACK — KEIN TEMPLATE VORHANDEN ───────────────────────────────────────

Schema:   <Thema>_<Dokumenttyp>_<Tieringstufe>_<Stageinfo>.ext

Thema          Inhaltliches Kürzel des Dokuments (z.B. FREEZE, NOTIZ, STAGE)
Dokumenttyp    Art des Dokuments (z.B. GOV, Sprint, Backlog, Principles, How2)
Tieringstufe   Varianten-Kürzel: DEV · EXP · MUNI · CARD
Stageinfo      Stage-Suffix: S104, S103, ...
Trennzeichen   Unterstrich (_) zwischen allen Segmenten

Beispiel:
  STAGE_ZIELE_DEV_S104.md


── 4.5 NAMENSKONVENTION R-MUNI VS. R+MUNI ───────────────────────────────────────

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
