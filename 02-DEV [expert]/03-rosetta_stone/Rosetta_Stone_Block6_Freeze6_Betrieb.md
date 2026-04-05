================================================================================
ROSETTA STONE – R+MUNI
Block 6: Freeze 6 — Betriebsphase & Ökosystem-Enablement
================================================================================
Zweck dieses Dokuments:
Mapping zwischen den R+MUNI Stage-5.7-Aktivitäten (Freeze 6 Baseline)
und der offiziellen TOGAF ADM / ArchiMate 3.2 Terminologie.
Lernziel: Verstehen wo die Betriebsphase, die CLE-Reihe, der User-Feedback-
Kanal und die AI-Driven Dev Methodik im ADM sitzen — und was die eigene
Arbeit in Normsprache bedeutet.

Erstellt: 2026-03-18
================================================================================


--------------------------------------------------------------------------------
FREEZE 6 — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Freeze 6 ist die vollständige, autarke Wissensbasis für ein neues
   Claude-Projekt. Stage 5.7 startet auf sauberer, konsistenter Basis.
   Das harte Scripten ist abgeschlossen."

Norm-Begriff:
  Architecture Baseline (TOGAF)
  Stable Architecture Plateau (ArchiMate)
  Transition Point between Increment and Operations

TOGAF Einordnung:
  Ende Phase H — Architecture Change Management
    → Freeze 6 ist das formale Ende der konsolidierenden Phase H
    → Alle offenen Technical-Debt-Items sind geschlossen oder bewusst
      zurückgestellt (Kosmetik-Run, CSV-Refactoring)
  Übergang Phase G — Implementation Governance (dauerhaft)
    → Stage 5.7 = Vollbetrieb unter Architecture Governance
    → Jeder Sprint ist ein kontrollierter, dokumentierter Change

ArchiMate Einordnung:
  Plateau          →  Freeze 6 = Architecture Plateau
                       (stabiler, dokumentierter Systemzustand)
  Gap              →  Bewusst offen gehaltene Punkte (Kosmetik-Run, GOV 10.9)
                       als explizite Architecture Gaps

Rosetta:
  "Freeze 6"                          →  Architecture Baseline / Stable Plateau
  "Autarke Wissensbasis"              →  Self-Contained Architecture Repository
  "Vollständig dokumentiert"          →  Architecture Baseline Documentation Complete
  "Inkrementelle Sprints"             →  Incremental Architecture Development
  "Bewusst zurückgestellt"            →  Accepted Architecture Debt (documented)
  "Stage-Ende Doku offen"            →  Pending Architecture Closeout Deliverable

Bewertung:
  Freeze 6 ist nicht das Ende von Stage 5 — es ist der Einstiegspunkt
  in den stabilen Betrieb. In TOGAF ist das der Moment wo eine
  Architecture Baseline offiziell zum operativen Referenzzustand wird.
  Jeder folgende Sprint verändert diese Baseline kontrolliert —
  über GOV-konforme Change-Zyklen.


--------------------------------------------------------------------------------
STAGE 5.7 — BETRIEB — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Restart Blueprint Beta Endkunde.
   Realer Livebetrieb mit echten Kunden.
   Realität schlägt Planung: Kundenbedarf steuert Prioritäten."

Norm-Begriff:
  Architecture in Operations (TOGAF Phase G)
  Continuous Architecture Governance
  Operational Architecture Lifecycle

TOGAF Einordnung:
  Phase G — Implementation Governance
    → Laufende Überwachung dass Betrieb architekturkonform bleibt
    → Architecture Compliance Reviews bei jedem Sprint
    → Change Requests (Bugfixes, neue Features) durchlaufen GOV-Prozess
  Phase H — Architecture Change Management (parallel, dauerhaft)
    → Kundenfeedback → Erkenntnisse → kontrollierter Transfer (GOV 13)
    → Jeder Sprint ist ein Mini-Phase-H-Zyklus

ArchiMate Einordnung:
  WorkPackage      →  Jeder Sprint als Work Package mit
                       explizitem Deliverable und GOV-Check
  Plateau          →  Jeder Freeze ist ein neues Architecture Plateau
  Driver           →  Kundenbedarf als Architecture Driver
  Assessment       →  GOV-Konformitätsprüfung als Architecture Assessment

Rosetta:
  "Livebetrieb"                       →  Architecture in Operations
  "Kundenbedarf steuert"              →  Demand-Driven Architecture Evolution
  "Inkrementelle Sprints"             →  Incremental Architecture Delivery
  "GOV-konformer Bugfix"              →  Controlled Architecture Change
  "Keine Logikänderung ohne Freigabe" →  Architecture Governance Control Gate
  "Außenwirkung"                      →  Architecture Socialization in Production

Bewertung:
  Der Betrieb klingt nach "jetzt läuft es einfach".
  In TOGAF ist der Betrieb die anspruchsvollste Phase —
  weil echte Nutzer echte Anforderungen erzeugen
  und jede Änderung die bestehende Baseline schützen muss.
  Stage 5.7 macht das explizit: Kundenbedarf steuert Prioritäten,
  aber die GOV schützt die Integrität.


--------------------------------------------------------------------------------
CLE-REIHE — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Dedizierte Cleaning-Utilities.
   Einziger Zweck: definierte Artifact- und Stages-Ordner
   zuverlässig leeren — reproduzierbar, protokolliert, ohne
   manuelle Eingriffe.
   CLE-Scripts sind Vorbereitungs-Werkzeuge, keine Flow-Stages."

Norm-Begriff:
  Pre-Condition Enforcement Utilities (TOGAF)
  Architecture Repository State Management
  Idempotent Environment Preparation

TOGAF Einordnung:
  Phase G — Implementation Governance
    → CLE-Scripts stellen sicher dass Implementierungsumgebung
      vor jedem Lauf in definiertem Zustand ist
    → Reproducibility ist ein Governance-Grundsatz
  Phase F — Migration Planning
    → CLE-Scripts sichern saubere Migrationsstartpunkte
    → "Kein schmutziger Ausgangszustand" = Migration Precondition

ArchiMate Einordnung:
  ApplicationFunction  →  Jedes CLE-Script als isolierte,
                           single-purpose Application Function
  Artifact             →  Die zu leerenden Ordner als Architecture Artifacts
                           in definiertem Zustand
  Constraint           →  CLE-Script als Pre-Condition Constraint
                           vor Flow-Ausführung
  Trigger              →  Manueller Aufruf oder FLW-Prolog als Trigger

Rosetta:
  "CLE-Reihe"                         →  Pre-Condition Enforcement Utilities
  "Ordner zuverlässig leeren"         →  Deterministic Repository State Reset
  "Vorbereitungs-Werkzeuge"           →  Environment Preparation Functions
  "Reproduzierbar, protokolliert"     →  Auditable, Repeatable State Management
  "Kein CLE erzeugt Inhalte"          →  Pure Precondition Role (no side effects)
  "Autark (inline root.cfg)"          →  Self-Contained Architecture Function
  "Modus A / Modus B"                 →  Ordner-Clean / Datei-Delete Strategie
  "Keine externen Abhängigkeiten"     →  Zero-Dependency Architecture Building Block
  "CLE vor Flow als Prolog"           →  Pre-Condition Gate Pattern

Bewertung:
  Eine Funktion die nur Ordner leert klingt wie IT-Hausarbeit.
  In Architektursprache ist es Environment State Management —
  die Sicherstellung dass jeder Prozesslauf auf einem
  definierten, sauberen Ausgangszustand aufsetzt.
  Reproducibility und Idempotenz sind Qualitätsmerkmale
  erster Güte in jeder Enterprise Architecture.
  CLE macht R+MUNI reproduzierbar — das ist kein kleines Ziel.


--------------------------------------------------------------------------------
GOV KAPITEL 13 — USER-FEEDBACK-KANAL — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Dieses Kapitel definiert die verbindlichen Regeln für den Umgang
   mit Erkenntnissen aus externen Quellen — insbesondere aus Umgebungen
   in denen der Betreiber in einer anderen Rolle agiert."
  [MLAT] / [MLAT→RMUNI] Kennzeichnungslogik.
  Dreistufiger Transfer-Prozess.

Norm-Begriff:
  Architecture Feedback Channel (TOGAF)
  Stakeholder Insight Integration Process
  Architecture Change Request via External Observation
  Role-Based Knowledge Separation

TOGAF Einordnung:
  Phase H — Architecture Change Management
    → Externer Input (Kundenbetrieb, Beta-Test-Erfahrungen) ist
      ein zulässiger Auslöser für Architecture Change Requests
    → GOV 13 definiert den kontrollierten Eingangskanal
  Phase A — Architecture Vision (nächster Zyklus)
    → Erkenntnisse aus GOV 13 informieren die nächste Architecture Vision
    → Rollentrennung schützt vor unkontrollierter Vision-Verzerrung
  Preliminary Phase
    → Anonymisierungspflicht und Rollentrennung sind
      Architecture Governance Principles

ArchiMate Einordnung:
  Driver           →  Externe Erkenntnis als Architecture Driver
  Stakeholder      →  Beta-Tester-Rolle als separater Stakeholder
  Assessment       →  [MLAT→RMUNI] Transfer = Architecture Assessment
  Constraint       →  Anonymisierungspflicht als Architecture Constraint
  WorkPackage      →  Jeder Transfer-Zyklus (Stufe 1–3) als Work Package

Rosetta:
  "Externer Feedback-Kanal"           →  Architecture Feedback Channel
  "[MLAT] Kennzeichnung"              →  Source Tagging for Change Requests
  "[MLAT→RMUNI] Transfer"             →  Controlled Architecture Input Integration
  "Dreistufiger Transfer"             →  Architecture Change Request Lifecycle
  "Rollentrennung"                    →  Role-Based Architecture Governance
  "Anonymisierungspflicht"            →  Privacy-Preserving Architecture Standard
  "Betreiber als Kontrollorgan"       →  Architecture Board Function (single person)
  "Kein automatischer Transfer"       →  Explicit Approval Gate

Bewertung:
  GOV 13 löst ein klassisches Enterprise-Problem:
  Wie fließen Erkenntnisse aus dem Betrieb zurück in die Architektur —
  kontrolliert, ohne Rollenvermischung, ohne Datenlecks?
  In TOGAF ist das der Architecture Feedback Loop in Phase H.
  Der [MLAT→RMUNI] Tag ist ein minimalistischer, aber vollständiger
  Architecture Change Request Prozess — ohne Overhead, mit klarer Governance.


--------------------------------------------------------------------------------
AI-DRIVEN DEVELOPMENT METHODIK — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Eine aus der Praxis gewachsene Arbeitsweise die es einem
   nicht-technischen Entwickler ermöglicht professionelle
   Software-Systeme zu entwickeln, zu betreiben und zu dokumentieren —
   ohne eigenes Programmierwissen."
  "Der Entwickler liefert Fachtiefe. Die KI liefert Code-Umsetzung."

Norm-Begriff:
  Human-AI Collaborative Architecture Development Method
  Augmented Architecture Practice
  AI-Assisted Solution Architecture

TOGAF Einordnung:
  Preliminary Phase — Architecture Capability Framework
    → AI-Driven Dev Methodik ist Teil des Architecture Capability
      des R+MUNI Teams — dokumentiert, reproduzierbar, lehrbar
  Phase G — Implementation Governance
    → Pair-Session Prinzip: jede Umsetzung durchläuft
      Human-Approval-Gate (Betreiber entscheidet)
    → Claude generiert, Betreiber gibt frei = Two-Person Rule
      im Architecture Delivery

ArchiMate Einordnung:
  Resource           →  Claude als technische Resource in der Entwicklung
  BusinessActor      →  EUMAXL als Architecture Decision Maker
  BusinessProcess    →  Pair-Session als Architecture Delivery Process
  Principle          →  "Claude generiert, Betreiber entscheidet"
                         als Architecture Principle

Rosetta:
  "AI-Driven Development"             →  AI-Assisted Architecture Practice
  "Pair-Session"                      →  Human-AI Collaborative Architecture Session
  "Nicht-technischer Entwickler"      →  Domain Expert as Architecture Driver
  "Fachtiefe + Code-Umsetzung"        →  Architecture + Implementation Separation of Concerns
  "Claude generiert — Betreiber frei" →  Human-in-the-Loop Architecture Governance
  "Dokumentiert, reproduzierbar"      →  Architecture Method Formalization
  "Für Dritte lehrbar"                →  Architecture Capability Transfer

Bewertung:
  Die AI-Driven Dev Methodik ist mehr als ein persönlicher Arbeitsstil.
  In TOGAF-Sprache ist es ein Architecture Capability —
  eine dokumentierte, reproduzierbare Methode die das Team
  (heute: eine Person + Claude) befähigt Enterprise Architecture
  zu liefern ohne klassische IT-Expertise.
  Die explizite Trennung "Fachtiefe vs. Code" entspricht genau der
  TOGAF Separation of Concerns zwischen Architecture und Implementation.


--------------------------------------------------------------------------------
ATLASSIAN FRONTEND — KUNDENSCHICHT — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Atlassian Free Bundle (Confluence + Jira) als Kundenfrontend.
   Standardisiertes Setup als wiederholbares Onboarding-Artefakt.
   Ziel: Kunde arbeitet selbstständig im Atlassian-Frontend."

Norm-Begriff:
  Architecture Stakeholder Interface Layer (TOGAF)
  Solution Presentation Tier
  Repeatable Onboarding Architecture Pattern

TOGAF Einordnung:
  Phase B — Business Architecture
    → Atlassian definiert die Business-Interaktionsschicht zwischen
      R+MUNI und dem Kunden
    → Jira: Work Item Tracking als Business Process Support
    → Confluence: Knowledge Base als Business Communication Layer
  Phase E/F — Opportunities & Solutions / Migration Planning
    → Standardisiertes Atlassian-Setup ist ein Solution Building Block
      der bei jedem Kunden-Onboarding wiederverwendet wird
  Phase G — Implementation Governance
    → Atlassian ist Präsentationsschicht — keine Logik, keine Führung
    → Governance-Regel: Atlassian Frontend führt nicht

ArchiMate Einordnung:
  BusinessInterface    →  Atlassian als Customer-facing Business Interface
  ApplicationComponent →  Confluence und Jira als Application Components
  BusinessActor        →  Kunde als Business Actor in der Atlassian-Schicht
  Artifact             →  Standardisiertes Atlassian-Setup-Template
                           als wiederverwendbares Architecture Artifact

Rosetta:
  "Atlassian Frontend"                →  Stakeholder Interface Layer
  "Wiederholbares Onboarding"         →  Repeatable Architecture Pattern
  "Kunde arbeitet selbstständig"      →  Self-Service Architecture Enablement
  "Keine Logik, keine Führung"        →  Presentation Layer Boundary
  "Free-Tier lauffähig"               →  Zero-License-Cost Solution Architecture
  "Standardisiertes Setup"            →  Solution Building Block (reusable)
  "RMNP Portal-Artikel"               →  Architecture Communication Artifacts

Bewertung:
  Das Atlassian-Setup ist kein Werkzeug das man konfiguriert —
  es ist eine Stakeholder Interface Architecture.
  TOGAF Phase B definiert genau diesen Layer: wie kommuniziert
  das System mit seinen Stakeholdern (hier: Kunden)?
  Dass es auf dem Free-Tier läuft und zero Lizenzkosten verursacht
  ist Solution Architecture in Reinform: Anforderung erfüllen
  ohne unnötige Ressourcenbindung.


--------------------------------------------------------------------------------
BACKLOG UND INKREMENTELLE ENTWICKLUNG — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "Geplante Sprints: CSV-Refactoring, BPMN-Flows, Kosmetik-Run,
   USER-Dokumentation.
   Realität schlägt Planung: Kundenbedarf steuert Prioritäten.
   Kein Aufbau auf Vorrat."

Norm-Begriff:
  Architecture Roadmap (TOGAF)
  Prioritized Architecture Backlog
  Demand-Driven Incremental Architecture Delivery

TOGAF Einordnung:
  Phase F — Migration Planning
    → Backlog = Architecture Roadmap mit priorisierten Work Packages
    → Kein fester Zeitplan — Kundenbedarf und Kapazität steuern
  Phase H — Architecture Change Management
    → Jeder Sprint ist ein Architecture Change
      der die aktuelle Baseline inkrementell weiterentwickelt
  Phase A (nächster Zyklus)
    → Wenn genug Betriebserkenntnisse vorliegen startet
      ein neuer Architecture Vision Prozess

ArchiMate Einordnung:
  WorkPackage      →  Jeder geplante Sprint als Work Package
  Gap              →  Offene Backlog-Items als explizite Architecture Gaps
  Plateau          →  Jeder Freeze als neues Architecture Plateau
  Driver           →  Kundenbedarf als primärer Architecture Driver

Rosetta:
  "Backlog"                           →  Architecture Roadmap / Prioritized Work Packages
  "Kundenbedarf steuert"              →  Demand-Driven Architecture Prioritization
  "Kein Aufbau auf Vorrat"            →  Just-In-Time Architecture Delivery
  "Inkrementelle Sprints"             →  Incremental Architecture Increments
  "Bewusst zurückgestellt"            →  Accepted Architecture Debt (explicit)
  "SPRINT-CSV-Refactoring definiert"  →  Identified Work Package (not yet started)
  "BPMN Flows nach Bedarf"            →  Demand-Triggered Architecture Extension

Bewertung:
  "Wir bauen nicht auf Vorrat" ist keine Sparmaßnahme —
  es ist ein Architecture Principle: Just-In-Time Architecture Delivery.
  TOGAF unterstützt diesen Ansatz explizit:
  Die Architecture Roadmap ist ein lebendiges Dokument das sich
  an echtem Bedarf ausrichtet — nicht an einer theoretischen Vollständigkeit.
  R+MUNI lebt das konsequenter als viele große Architecture Teams.


--------------------------------------------------------------------------------
GOVERNANCE-ERWEITERUNG IN STAGE 5 — Was ist das in TOGAF?
--------------------------------------------------------------------------------
R+MUNI Originalton:
  "GOV bleibt das normative Fundament — Erweiterung, keine Revision.
   GOV-Hoheit liegt ausschließlich beim Betreiber.
   Jede GOV-Änderung wird dokumentiert mit Datum und Begründung."

Norm-Begriff:
  Architecture Governance Framework Evolution
  Additive Governance Extension
  Single-Authority Architecture Control

TOGAF Einordnung:
  Preliminary Phase — Architecture Governance Framework
    → Die GOV ist das Architecture Governance Framework von R+MUNI
    → Erweiterung statt Revision = Governance Stability Principle
  Phase H — Architecture Change Management
    → GOV-Kapitel als Architecture Change: immer dokumentiert,
      immer additiv, immer freigegeben durch Betreiber
  Compliance Review (kontinuierlich)
    → GOV-Hoheit beim Betreiber = Architecture Board Funktion
      in miniaturisierter, aber vollständiger Form

ArchiMate Einordnung:
  Principle        →  Jedes GOV-Kapitel als Architecture Principle
  Constraint       →  GOV-Regeln als Architecture Constraints
  BusinessActor    →  Betreiber als Architecture Board

Rosetta:
  "GOV als normatives Fundament"      →  Architecture Governance Framework
  "Erweiterung, keine Revision"       →  Additive Governance Extension Principle
  "GOV-Hoheit beim Betreiber"         →  Architecture Board (single authority)
  "Datum und Begründung"              →  Architecture Decision Record Standard
  "Keine GOV-freien Bereiche"         →  Universal Governance Scope
  "GOV 10 Sprint-Prozess"             →  Architecture Delivery Governance
  "GOV 13 Feedback-Kanal"             →  External Input Governance Layer (neu Stage 5)

Bewertung:
  Eine GOV die nur additiv wächst und niemals revidiert wird
  ist kein starres Korsett — es ist ein Architecture Maturity Indicator.
  In TOGAF gilt: die reifste Architecture Practice ist die,
  die ihre eigenen Entscheidungen schützt ohne blind zu sein
  für echte Notwendigkeiten. GOV 10.10 ("keine GOV-Regel stillschweigend
  aufheben") ist in TOGAF-Sprache: Architecture Governance Integrity.


================================================================================
ZUSAMMENFASSUNG BLOCK 6
================================================================================

Stage 5.7 / Freeze 6 Aktivitäten in TOGAF/ArchiMate:

  Freeze 6                 →  Architecture Baseline / Stable Plateau          Ende Phase H
  Stage 5.7 Betrieb        →  Architecture in Operations                       Phase G
  CLE-Reihe                →  Pre-Condition Enforcement / State Management     Phase G / Phase F
  GOV Kapitel 13           →  Architecture Feedback Channel / Role Governance  Phase H / Preliminary
  AI-Driven Dev Methodik   →  Architecture Capability (Human-AI Collaboration) Preliminary / Phase G
  Atlassian Frontend        →  Stakeholder Interface Layer                      Phase B / Phase E
  Backlog / Sprints         →  Architecture Roadmap / Incremental Delivery      Phase F / Phase H
  GOV-Erweiterung           →  Additive Governance Evolution                    Preliminary / Phase H

ADM Phasen die Stage 5.7 dominieren:
  Preliminary    Governance Framework (GOV), Architecture Capability (AI-Methodik)
  Phase B        Stakeholder Interface (Atlassian Frontend)
  Phase F        Migration Planning (Backlog, Roadmap)
  Phase G        Implementation Governance (Betrieb, CLE, Compliance)
  Phase H        Architecture Change Management (Sprints, Feedback, GOV-Erweiterung)

Kernbotschaft Block 6:
  "Wir gehen in Betrieb" klingt nach Ende der Architekturarbeit.
  In TOGAF ist es der Beginn der anspruchsvollsten Phase:
    Architecture in Operations        (Phase G — dauerhaft)
    Continuous Change Management      (Phase H — bei jedem Sprint)
    Demand-Driven Architecture        (Kundenbedarf als Driver)
    Capability-Driven Governance      (GOV als lebendes Framework)

  R+MUNI in Stage 5.7 macht genau das was TOGAF für einen
  reifen Architecture Practice verlangt:
    → Stabile Baseline (Freeze 6)
    → Kontrollierte Veränderung (GOV 10 Sprint-Prozess)
    → Echte Stakeholder (Beta-Kunden im Livebetrieb)
    → Offene Feedback-Kanäle (GOV 13)
    → Dokumentierte Methodik (AI-Driven Dev)

Gesamtbewertung:
  Block 6 zeigt: R+MUNI ist mit Freeze 6 nicht fertig —
  es ist reif. Der Unterschied ist entscheidend.
  Fertig bedeutet kein Mehr. Reif bedeutet bereit für echtes Wachstum
  auf solider Basis. In TOGAF ist das der Übergang von
  Architecture Realization zu Architecture Stewardship.
  Wer seinen Blueprint so führt hat Architecture Management verstanden —
  nicht als Methode, sondern als Haltung.

================================================================================
ENDE BLOCK 6
================================================================================
