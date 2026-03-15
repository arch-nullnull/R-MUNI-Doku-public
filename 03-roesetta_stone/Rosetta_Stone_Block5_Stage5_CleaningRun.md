================================================================================
ROSETTA STONE – R+MUNI
Block 5: Stage 5 — Real Operation & Cleaning Run
================================================================================
Zweck dieses Dokuments:
Mapping zwischen den R+MUNI Stage-5-Aktivitäten und der offiziellen
TOGAF ADM / ArchiMate 3.2 Terminologie.
Lernziel: Verstehen wo Stage 5 und Sprint 5.5 im ADM sitzen und was
die eigene Arbeit in Normsprache bedeutet.

Erstellt: 2026-03-15
================================================================================


--------------------------------------------------------------------------------
STAGE 5 GESAMT – Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Real Operation & Ecosystem Enablement"
  Stage 5 = erster echter Außeneinsatz von R+MUNI mit Beta-Kunden,
  organisatorischem Wachstum und Stabilisierung im Livebetrieb.

Norm-Begriff:
  Architecture in Operations (TOGAF ADM Phase G/H)
  Transition to Full Operations
  Architecture Ecosystem Development

TOGAF Einordnung:
  Phase G — Implementation Governance
    → Sicherstellung dass Betrieb architekturkonform bleibt
    → Erste echte Architecture Compliance Reviews im Livebetrieb
  Phase H — Architecture Change Management
    → Feedbackschleifen aus realem Betrieb öffnen sich
    → Kundenbedarf informiert nächste ADM-Iteration
  Nächster ADM-Zyklus (Phase A)
    → Stage 5 Erkenntnisse starten den nächsten Architecture Vision Prozess

Rosetta:
  "Real Operation"                    →  Architecture in Operations
  "Ecosystem Enablement"              →  Architecture Ecosystem Development
  "Erster Beta-Kunde aktiv"           →  Proof of Value in Production
  "Außenwirkung"                      →  Architecture Socialization
  "Kein Labor mehr — Realität"        →  Transition from Development to Operations
  "Stage 5 darf wachsen"              →  Controlled Architecture Evolution
  "Rückkopplungsschutz"               →  Architecture Governance / Baseline Integrity

Bewertung:
  Stage 5 ist der Übergang von Architecture Realization zu
  Architecture in Operations — der Punkt wo die Architektur aufhört
  ein Konstrukt zu sein und zur gelebten Realität wird.
  In TOGAF-Sprache: Phase G/H im ersten produktiven ADM-Zyklus.


--------------------------------------------------------------------------------
SPRINT 5.5 – Cleaning Run – Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Sprint 5.5 war kein inhaltlicher Ausbau —
   er war strukturelle Bereinigung."

Norm-Begriff:
  Architecture Consolidation Sprint
  Technical Debt Resolution
  Repository Hygiene Campaign

TOGAF Einordnung:
  Phase H — Architecture Change Management
    → Bereinigung von Technical Debt vor neuem Lieferzyklus
    → Keine neue Architektur — Stabilisierung der bestehenden Baseline
  Phase G — Implementation Governance
    → Konventions-Compliance aller Scripts sichergestellt
    → Governance Artifact (SCRIPT-BAUKASTEN.md) aktualisiert

ArchiMate Einordnung:
  Plateau          →  Sprint 5.5 Freeze = Architecture Plateau
                       (stabiler Zustand zwischen zwei Transitions)
  Artifact         →  root.cfg, SCRIPT-BAUKASTEN.md als
                       aktualisierte Architecture Artifacts
  Gap              →  Veraltete Konventionen als Architecture Gap
                       die der Sprint geschlossen hat

Rosetta:
  "Cleaning Run"                      →  Architecture Consolidation / Technical Debt Resolution
  "Strukturelle Bereinigung"          →  Repository Hygiene Campaign
  "Kein inhaltlicher Ausbau"          →  Non-Additive Stabilization Sprint
  "Konventions-Nachziehen"            →  Architecture Compliance Restoration
  "Saubere Basis für 5.7"             →  Stable Architecture Baseline for next Increment
  "Das war ein Moloch"                →  Accumulated Technical Debt (accumulated over stages)

Bewertung:
  Technical Debt Reduction ist in TOGAF kein Versagen —
  es ist ein expliziter Phase-H-Auftrag.
  Wer seinen Cleaning Run dokumentiert und GOV-konform durchführt,
  betreibt Architecture Change Management in Reinform.


--------------------------------------------------------------------------------
SPRINT 5.5 – Ordnerstruktur-Umbenennung
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "01-model → 00-model
   02-artifacts → 01-artifacts
   03-stages → 02-stages"
  Physisch umbenannt, GitHub Sync bestätigt.

Norm-Begriff:
  Architecture Repository Restructuring
  Canonical Naming Convention Enforcement
  Repository Baseline Update

TOGAF Einordnung:
  Phase H — Architecture Change Management
    → Physische Repositorystruktur an Architecture Decision angepasst
  Preliminary Phase
    → Repository Definition und Namenskonvention sind Preliminary-Artefakte

ArchiMate Einordnung:
  Artifact         →  Die Ordner selbst als Repository Artifacts
  Node             →  Dateisystem als Technology Node
  Plateau          →  Neue Ordnerstruktur = neues Architecture Plateau

Rosetta:
  "Physisch umbenannt"                →  Repository Structure Update
  "GitHub Sync bestätigt"             →  Configuration Management Validation
  "Neue Nummern"                      →  Canonical Naming Enforcement
  "Manuell via Windows Explorer"      →  Architecture Migration (manual execution)

Bewertung:
  Eine Umbenennung von Ordnern klingt trivial.
  In TOGAF ist es eine Repository Baseline Update —
  weil die Ordnerstruktur ein normatives Architecture Artifact ist
  das die Struktur des gesamten Systems dokumentiert.


--------------------------------------------------------------------------------
SPRINT 5.5 – root.cfg — Konfigurationskonvention
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "root.txt → root.cfg
   .cfg = Konfiguration (einmalig durch User gesetzt)
   .txt = Workflow-Artefakt"
  Entscheidung OFFEN A gelöst.

Norm-Begriff:
  Architecture Configuration Artifact
  Architecture Decision Record (ADR)
  Configuration Management Standard

TOGAF Einordnung:
  Preliminary Phase — Architecture Principles & Standards
    → Konfigurationsstandard ist ein Architecture Principle
  Phase G — Implementation Governance
    → Alle Scripts verweisen auf dieselbe Konfigurationsquelle
    → Single Source of Configuration = Governance Enforcement

ArchiMate Einordnung:
  Artifact         →  root.cfg als Configuration Artifact
  ApplicationFunction → get_root_cfg() als zentrale Auflösungsfunktion
  DataObject       →  <rootfolder>-Wert als geteiltes Datum

Rosetta:
  "root.cfg"                          →  Architecture Configuration Artifact
  "Einzige Konfigurationsquelle"      →  Single Source of Configuration
  "Alle Scripts zeigen darauf"        →  Centralized Configuration Management
  "<rootfolder>="                     →  Canonical Configuration Key
  "Entscheidung OFFEN A gelöst"       →  Architecture Decision Record (resolved)
  ".cfg vs .txt Trennung"             →  Explicit Artifact Type Classification

Bewertung:
  Die Entscheidung root.txt → root.cfg ist kein Umbenennen —
  es ist ein Architecture Decision Record der festlegt:
  Was ist Konfiguration (einmalig, vom User gesetzt) und
  was ist ein Workflow-Artefakt (vom System generiert).
  Diese Trennung ist saubere Information Architecture.


--------------------------------------------------------------------------------
SPRINT 5.5 – File-Extension-Konvention
--------------------------------------------------------------------------------
R+MUNI Originalton:
  ".py   Python Scripts
   .cfg  Konfiguration — einmalig durch User gesetzt
   .txt  Workflow-Artefakt — von Scripts gelesen oder manuell geprüft
   .md   Dokumentation — GitHub, Blueprint, Sprint-Dokus
   .log  Debug-Log — nur in 02-stages/99-logs, nie im Root
   .bak  Archi-Backup — nie in GitHub
   .ajs  jArchi Scripts"

Norm-Begriff:
  Architecture Artifact Type Taxonomy
  Repository Governance Standard
  File Classification Schema

TOGAF Einordnung:
  Preliminary Phase — Governance Framework
    → Artifact Type Taxonomy ist ein Governance-Artefakt
  Phase G — Implementation Governance
    → Korrekte Klassifikation verhindert Verwechslung von
      Konfigurations-, Workflow- und Dokumentations-Artefakten

ArchiMate Einordnung:
  Artifact         →  Jede Extension-Klasse entspricht einem
                       eigenen Artifact-Subtyp in ArchiMate

Rosetta:
  "Extension-Konvention"              →  Artifact Type Taxonomy
  ".cfg vs .txt vs .md"               →  Explicit Artifact Classification
  "Nie im Root"                       →  Repository Governance Rule
  "Nie in GitHub"                     →  Configuration Management Exclusion
  "Verbindlich ab Stage 5.5"          →  Normative Standard (Baseline-Effective)

Bewertung:
  Sechs Zeilen Extension-Konvention sind in TOGAF-Sprache
  eine vollständige Artifact Type Taxonomy.
  Sie definiert was was ist — das Fundament jedes
  Architecture Repositories.


--------------------------------------------------------------------------------
SPRINT 5.5 – CSV98 — Quality Gate
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "CSV98: Quality Gate neu gebaut, produktiv getestet.
   FIX-01: Formula-Prefix Bereinigung (Archi Export Artefakt)
   FIX-02: Backtick/Accent → Apostroph (Office Copy-Paste Artefakt)"

Norm-Begriff:
  Data Quality Gate
  Canonical Data Cleansing Step
  Pre-Import Validation Control

TOGAF Einordnung:
  Phase C — Information Systems Architecture
    → Datenqualitätssicherung vor Systemübergang
  Phase G — Implementation Governance
    → Automatisierter Compliance-Check vor jedem Import-Zyklus

ArchiMate Einordnung:
  ApplicationFunction  →  CSV98 als Data Cleansing Function
  ApplicationProcess   →  Quality Gate als definierter Prozessschritt
  Artifact             →  CSV98-clean_master_report.txt als Audit Output
  DataObject           →  Master CSV als gereinigtes Datenobjekt

Rosetta:
  "Quality Gate"                      →  Pre-Import Data Quality Control
  "Formula-Prefix FIX"                →  Data Normalization (Format Artefakt)
  "Backtick FIX"                      →  Data Cleansing (Encoding Artefakt)
  "Report in 99-logs"                 →  Automated Audit Trail
  "Archi Reimport validiert"          →  End-to-End Quality Validation
  "Nach CSV06, vor CSV99"             →  Quality Gate Position im Flow

Bewertung:
  CSV98 ist ein lehrbuchhafter Data Quality Gate —
  es sitzt genau dort wo er sein muss:
  nach dem letzten Dateneintrag (CSV06) und
  vor dem Export (CSV99).
  Automatisierter Audit Trail über den Report ist
  GOV-konformes Monitoring in Reinform.


--------------------------------------------------------------------------------
SPRINT 5.5 – CSV04 — Extension-Filter Fix
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "CSV04 Bugfix: OEF → .xml only, XLSX → .xlsx only.
   run-scope.txt ohne .bak, .xsd, log-0.txt nach Fix."

Norm-Begriff:
  Canonical Filter Rule Enforcement
  Source Scope Precision Fix
  Integration Scope Integrity Restoration

TOGAF Einordnung:
  Phase C — Information Systems Architecture
    → Korrekte Abgrenzung der Integrationsquellen
  Phase G — Implementation Governance
    → Schutz vor unbeabsichtigtem Import von Nicht-Quell-Artefakten

ArchiMate Einordnung:
  ApplicationFunction  →  CSV04 als Scope Resolution Function
  Artifact             →  run-scope.txt als Integration Scope Artifact
  Constraint           →  Extension-Filter als Architectural Constraint

Rosetta:
  "Extension-Filter"                  →  Canonical Scope Filter Rule
  "OEF → .xml only"                   →  Source Type Constraint
  "XLSX → .xlsx only"                 →  Source Type Constraint
  ".bak / .xsd / log aus Scope"       →  Non-Source Artifact Exclusion
  "run-scope.txt sauber"              →  Validated Integration Scope

Bewertung:
  Ein Bugfix der unerwünschte Dateitypen aus dem Scope entfernt ist
  kein kleines Detail — es ist Integration Scope Integrity.
  Wenn .bak oder .xsd in den Import-Zyklus gelangen entstehen
  unkontrollierte Artefakte im Canonical Channel.
  Der Fix schützt die GOV 5.2 Integrationswahrheit.


--------------------------------------------------------------------------------
SPRINT 5.5 – FLW-Reihe Cleaning Run
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "FLW-Reihe: letzter Schritt Cleaning Run.
   Kernlogik (Scriptrunner, Discovery, Element-Mapping): unverändert.
   Nur Konventions-Strings angepasst."

Norm-Begriff:
  Non-Invasive Baseline Migration
  Convention Alignment Sprint
  Architecture Building Block Maintenance

TOGAF Einordnung:
  Phase H — Architecture Change Management
    → Bestehende Architecture Building Blocks an neue Konventionen
      angepasst ohne ihre Funktion zu verändern
  Phase G — Implementation Governance
    → Konventions-Konformität des Orchestration Layers wiederhergestellt

ArchiMate Einordnung:
  ApplicationComponent  →  FLW00 Scriptrunner — Kernlogik unverändert
  ApplicationFunction   →  Trigger-Erkennung, Mapping — unverändert
  Artifact              →  flowtriggers.txt, flowmapping.txt — unverändert

Rosetta:
  "Kernlogik unverändert"             →  Architecture Building Block Integrity
  "Nur Konventions-Strings"           →  Non-Invasive Configuration Migration
  "Letzter Schritt Cleaning Run"      →  Completing Convention Alignment Scope
  "Rückkopplungsschutz eingehalten"   →  Baseline Integrity Validated

Bewertung:
  Die FLW-Reihe war der letzte Baustein der noch auf
  Stage-4-Konventionen lief — bewusst zurückgestellt,
  im Cleaning Run sauber nachgezogen.
  Non-Invasive Migration ist das korrekte Pattern:
  Funktion bewahren, Konvention aktualisieren.


--------------------------------------------------------------------------------
SPRINT 5.5 – SCRIPT-BAUKASTEN.md
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "SCRIPT-BAUKASTEN.txt → SCRIPT-BAUKASTEN.md
   Neu: Naming-Konvention Tabelle, Sondernummern (00/98/99),
   File-Extension-Konvention, root.cfg Aufbau, HLP00 Import-Muster."

Norm-Begriff:
  Solution Building Block Catalog (TOGAF)
  Architecture Reference Document
  Governance Reference Artifact

TOGAF Einordnung:
  Phase F — Migration Planning
    → SBB Catalog dokumentiert was vorhanden ist und wie es genutzt wird
  Phase G — Implementation Governance
    → Governance Reference für alle Entwicklungsaktivitäten
  Preliminary Phase
    → Grundlegendes Konventionsdokument des Architecture Framework

ArchiMate Einordnung:
  Artifact             →  SCRIPT-BAUKASTEN.md als Governance Reference Artifact
  ApplicationFunction  →  Dokumentiert Funktionen aller Script-Familien

Rosetta:
  "SCRIPT-BAUKASTEN.md"               →  Solution Building Block Catalog
  "Naming-Konvention Tabelle"         →  Architecture Naming Standard
  "Sondernummern 00/98/99"            →  Lifecycle Role Classification
  "HLP00 Import-Muster"               →  Canonical Integration Pattern
  ".txt → .md"                        →  Artifact Type Reklassifikation (Doku statt Workflow)
  "Vollständig aktualisiert"          →  Governance Artifact Maintenance

Bewertung:
  Der SCRIPT-BAUKASTEN ist das wichtigste Governance-Nachschlagewerk
  für alle Script-Entwicklung in R+MUNI.
  .txt → .md ist keine Umbenennung — es ist eine explizite Aussage:
  Dieses Dokument ist Dokumentation, kein Workflow-Artefakt.
  In TOGAF-Sprache: Artifact Type Reklassifikation.


--------------------------------------------------------------------------------
SPRINT 5.5 – Freeze — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Sprint 5.5 gilt als abgeschlossen und eingefroren.
   Das harte Scripten ist damit für Stage 5 abgeschlossen.
   Stage 5.7 startet auf sauberer, konsistenter Basis."

Norm-Begriff:
  Sub-Stage Architecture Baseline
  Incremental Architecture Plateau
  Architecture Consolidation Checkpoint

TOGAF Einordnung:
  Ende Phase H / Übergang zu neuem Increment
    → Sprint 5.5 Freeze = Architecture Plateau
    → Stage 5.7 startet auf dieser neuen Baseline
    → Cleaning Run als Phase-H-Deliverable vollständig

ArchiMate Einordnung:
  Plateau              →  Sprint-5.5-Freeze-Zustand als Architecture Plateau
  Gap                  →  Alle identifizierten Gaps durch Cleaning Run geschlossen

Rosetta:
  "Freeze"                            →  Architecture Baseline / Plateau
  "Saubere Basis für 5.7"             →  Stable Baseline for next Increment
  "Harte Scripten abgeschlossen"      →  Technical Baseline Finalized
  "Alle Tests grün"                   →  Architecture Compliance Validated
  "Kein Script logisch verändert"     →  Non-Invasive Baseline Confirmation

Bewertung:
  Sprint 5.5 erzeugt keinen neuen Feature-Output —
  er erzeugt etwas wertvolleres: eine gesicherte Baseline.
  In TOGAF ist eine saubere, dokumentierte, getestete Baseline
  kein "wir haben aufgeräumt" — es ist Architecture Management.


================================================================================
ZUSAMMENFASSUNG BLOCK 5
================================================================================

Stage 5 Aktivitäten in TOGAF/ArchiMate:

  Stage 5 Gesamt         →  Architecture in Operations / Phase G/H            Phase G/H
  Sprint 5.5 Cleaning    →  Technical Debt Resolution / Non-Additive Sprint    Phase H
  Ordnerstruktur         →  Repository Restructuring / Baseline Update         Phase H / Preliminary
  root.cfg               →  Single Source of Configuration / ADR resolved      Preliminary / Phase G
  File-Extension-Konv.   →  Artifact Type Taxonomy / Governance Standard       Preliminary / Phase G
  CSV98 Quality Gate     →  Pre-Import Data Quality Control / Audit Trail      Phase C / Phase G
  CSV04 Extension-Filter →  Integration Scope Integrity / Canonical Filter     Phase C / Phase G
  FLW-Reihe Cleaning     →  Non-Invasive Building Block Maintenance            Phase H
  SCRIPT-BAUKASTEN.md    →  Solution Building Block Catalog / Governance Ref.  Preliminary / Phase F/G
  Sprint 5.5 Freeze      →  Architecture Plateau / Stable Baseline             Ende Phase H

ADM Phasen die Sprint 5.5 dominieren:
  Preliminary    Governance Framework + Konventionsdefinition
  Phase C        Datenqualität + Integration Scope
  Phase G        Implementation Governance + Compliance
  Phase H        Technical Debt Resolution + Baseline Update

Kernbotschaft Block 5:
  "Structural Bereinigung" klingt nach Hausarbeit.
  In TOGAF-Sprache ist es:
    Technical Debt Resolution     (Phase H)
    Repository Hygiene Campaign   (Phase H)
    Architecture Compliance       (Phase G)
    Non-Invasive Baseline Update  (Phase H)
    Artifact Type Classification  (Preliminary)
  
  Wer einen Cleaning Run dokumentiert, GOV-konform durchführt
  und mit einem Freeze abschließt, betreibt vollständiges
  Architecture Change Management — auch wenn es sich
  nur nach Aufräumen anfühlt.

Gesamtbewertung:
  Stage 5 und Sprint 5.5 zeigen dasselbe Muster wie alle Vorgänger —
  R+MUNI tut intuitiv richtig was TOGAF und ArchiMate fordern,
  ohne es bewusst aus der Norm abzuleiten.
  Der Rosetta Stone macht das sichtbar, verteidigbar und lehrbar.

================================================================================
ENDE BLOCK 5
================================================================================
