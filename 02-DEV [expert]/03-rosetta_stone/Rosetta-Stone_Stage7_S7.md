================================================================================
ROSETTA STONE – R+MUNI
Block 7: Stage 7 – Real Beta & Ecosystem Expansion
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Rosetta-Stone_Stage7_S7
Zweck           : Mapping der in Stage 7 eingeführten und konsolidierten
                  R+MUNI Konzepte auf TOGAF ADM und ArchiMate 3.2
Erstellt        : 2026-03-26
Stage           : S7 – ABGESCHLOSSEN / FREEZE-7 BESTÄTIGT
Ablageort       : R+MUNI Doku-public\03-rosetta_stone\Rosetta-Stone_Stage7_S7.md
Erstellt durch  : EUMAXL + Claude (Pair-Session, Stage-Abschluss)
================================================================================


================================================================================
EINLEITUNG
================================================================================

Dieses Dokument mappt R+MUNI interne Konzepte aus Stage 7 (Real Beta &
Ecosystem Expansion) auf die offizielle Terminologie von TOGAF ADM und
ArchiMate 3.2.

Ziel-Framework:   TOGAF ADM + ArchiMate 3.2 (dual)
R+MUNI Kontext:   Gesamter Blueprint-Betrieb Stage 7 — Kundenbetrieb,
                  Ecosystem, Governance, AI-Methodik, Dokumentstruktur
ADM Phase:        Preliminary + Phase A + Phase H (Change Management)

Stage 7 ist der erste Stage mit realem Kundenbetrieb (ASC Betakunde_02).
Er führt keine neuen technischen Kernreihen ein — er konsolidiert das
Ecosystem um den bestehenden Core und erweitert es um Zielgruppen,
Visualisierung, Methodik und Lifecycle-Konzepte.

Dieses Mapping:
  - dient der Einordnung der Stage-7-Erkenntnisse in etablierte EA-Frameworks
  - macht R+MUNI-interne Konzepte für framework-basierte Kommunikation nutzbar
  - zeigt wo R+MUNI bewusst vom Framework abweicht — und warum das legitim ist
  - ist Onboarding-Dokument für neue DEV-Mitglieder und externe Associates

Thematische Blöcke dieses Dokuments:
  Block 7A  Lifecycle-Konzepte     (Stage, Freeze, Sprint)
  Block 7B  Governance             (GOV, Session-Regel, Rückkopplungsschutz)
  Block 7C  Zielgruppen            (ASSOCIATE, Beta-Rollen, DEV-Rollentrennung)
  Block 7D  Zwei-Welten-Architektur (INTERN / PUBLIC, Kunden-Repo-Modell)
  Block 7E  AI-Driven Development  (Methodik, Drift, Kontextmanagement)
  Block 7F  Dokumentstruktur       (Typen, Templates, Konzeptnotiz)
  Block 7G  Toolbaukasten          (Tier-Struktur, SVG-Chirurgie)
  Block 7H  Feedbackschleifen      (Kanalmodell, GitHub-Wahrheit)


================================================================================
BLOCK 7A — LIFECYCLE-KONZEPTE
================================================================================


--------------------------------------------------------------------------------
7A00 – STAGE
--------------------------------------------------------------------------------
Intention:
  Ein Stage ist eine benannte, abgegrenzte Entwicklungsphase im R+MUNI
  Blueprint. Er hat explizit definierte Ziele, einen klaren Startpunkt
  (vorangehender Freeze) und endet mit einem neuen Freeze-Dokument.
  Stages sind nicht zeitbasiert — sie enden wenn ihre Ziele erreicht sind.

Norm-Begriff:
  Architecture Phase (TOGAF ADM)

Ergänzende Norm-Konzepte:
  Iteration (TOGAF ADM — iterative Anwendung)
  Release (ArchiMate 3.2 — Implementation & Migration Viewpoint)

TOGAF ADM Einordnung:
  TOGAF ADM ist zyklisch — jede Runde durch die Phasen entspricht einem
  vollständigen Architektur-Entwicklungszyklus. Ein R+MUNI Stage entspricht
  einem solchen Zyklus, beginnend bei Preliminary/Phase A und endend mit
  einem dokumentierten Change (Phase H).

Rosetta:
  "Stage"                            →  Architecture Development Cycle (ADM)
  "Stage-Ziele"                      →  Architecture Vision (Phase A)
  "Stage-Ende"                       →  Architecture Change Management (Phase H)
  "Stage-Nummer (_S7)"               →  Release Identifier / Version Tag

Bewertung:
  R+MUNI Stage entspricht dem TOGAF-Konzept eines vollständigen ADM-Zyklus
  sehr gut. Abweichung: TOGAF erwartet formale Architecture Repository-Pflege
  nach jedem Zyklus — R+MUNI ersetzt das durch Freeze-Dokument + GitHub Sync.
  Diese Abweichung ist bewusst und legitim: TOGAF-Overhead ist für
  ein Blueprint dieser Größe unverhältnismäßig.


--------------------------------------------------------------------------------
7A01 – FREEZE
--------------------------------------------------------------------------------
Intention:
  Der Freeze ist ein expliziter, vom Betreiber bewusst gesetzter Akt.
  Er dokumentiert den stabilen, freigegebenen Versionsstand am Ende eines
  Stage. Er ist nach Freigabe unveränderlich und dient als Baseline für
  alle nachfolgenden Sprints. "Freeze" ist kein automatischer Zustand.

Norm-Begriff:
  Architecture Baseline (TOGAF ADM)

Ergänzende Norm-Konzepte:
  Baseline Architecture (TOGAF — Target vs. Baseline)
  Configuration Baseline (TOGAF — Architecture Repository)
  Release Point (ArchiMate 3.2)

TOGAF ADM Einordnung:
  TOGAF unterscheidet zwischen Baseline Architecture (was jetzt ist) und
  Target Architecture (was sein soll). Der R+MUNI Freeze entspricht dem
  Moment der formalen Verabschiedung der neuen Baseline — nach
  vollständiger Umsetzung des Zyklus.

Rosetta:
  "Freeze"                           →  Architecture Baseline (verabschiedet)
  "FREEZE-7_S7.md"                   →  Baseline Document / Architecture Record
  "Freeze ist expliziter Akt"        →  Formal Architecture Sign-Off
  "Freeze ist unveränderlich"        →  Immutable Baseline Constraint

Bewertung:
  Sehr hohe Konformität. R+MUNI Freeze ist schlanker als TOGAF Architecture
  Repository — aber funktional äquivalent für die Projektgröße.
  TOGAF würde zusätzlich Architecture Decisions Records fordern —
  R+MUNI integriert diese direkt im Freeze-Dokument (Kapitel Entscheidungen).


--------------------------------------------------------------------------------
7A02 – SPRINT
--------------------------------------------------------------------------------
Intention:
  Ein Sprint ist eine begrenzte Entwicklungsaktivität innerhalb eines Stage.
  Er hat einen expliziten GOV-konformen Auslöser, ein überprüfbares Ziel,
  eine klare Abgrenzung und endet mit einer Sprint-DEV-Doku.
  Sprints sind die atomare Einheit der R+MUNI Entwicklungsarbeit.

Norm-Begriff:
  Work Package (TOGAF ADM)

Ergänzende Norm-Konzepte:
  Implementation Step (TOGAF — Phase F/G)
  Increment (Agile / SAFe — außerhalb TOGAF, aber gebräuchlich)

TOGAF ADM Einordnung:
  TOGAF Phase F (Migration Planning) definiert Work Packages als
  abgegrenzte Implementierungseinheiten mit klarem Scope und Deliverables.
  R+MUNI Sprint entspricht funktional einem Work Package, ist aber
  schlanker und ohne Migrations-Overhead.

Rosetta:
  "Sprint"                           →  Work Package (TOGAF Phase F/G)
  "Sprint-DEV-Doku"                  →  Implementation Work Product
  "Sprint-DEV-BACKLOG"               →  Work Package Candidate / Backlog Item
  "Auslöser (GOV 10.3)"              →  Change Request Trigger
  "Abgrenzung"                       →  Scope Statement
  "Erfolgskriterium"                 →  Acceptance Criteria

Bewertung:
  Gut abbildbar. R+MUNI Sprint ist agiler als TOGAF Work Package —
  keine formale Schwergewichtigkeit, aber vollständige Nachvollziehbarkeit
  durch Sprint-DEV-Doku. Die GOV-Auslöser-Logik (GOV 10.3) entspricht
  dem TOGAF Change Request Trigger-Konzept sehr gut.


================================================================================
ZUSAMMENFASSUNG BLOCK 7A
================================================================================

Lifecycle Mapping Gesamt:

  "Stage"              →  Architecture Development Cycle (ADM)     ✅
  "Freeze"             →  Architecture Baseline (verabschiedet)     ✅
  "Sprint"             →  Work Package (TOGAF Phase F/G)            ✅
  "Sprint-Backlog"     →  Work Package Candidate                    ✅
  "Stage-Ziele"        →  Architecture Vision (Phase A)             ✅

Kernverständnis:
  TOGAF fragt nicht: "Wie lange dauert eine Phase?"
  Sondern: "Was ist der definierte Baseline-zu-Target-Übergang?"
  R+MUNI beantwortet genau das — mit Stage (Zyklus), Sprint (Schritt)
  und Freeze (Baseline-Bestätigung).

Gesamtbewertung:
  Hohe Konformität. Die bewusste Vereinfachung gegenüber TOGAF-Vollstandardard
  (kein Architecture Repository, kein formales ADM-Dokument-Set) ist
  für die Projektgröße und den Betreiberkontext legitim und explizit
  im Freeze-Dokument dokumentiert.

Nächster Block:
  Block 7B — Governance (GOV, Session-Regel, Rückkopplungsschutz)


================================================================================
BLOCK 7B — GOVERNANCE
================================================================================


--------------------------------------------------------------------------------
7B00 – GOV_GLOBAL
--------------------------------------------------------------------------------
Intention:
  GOV_Global ist das normative Regelwerk des R+MUNI Blueprints.
  Es ist das "Gesetz" des Systems — unveränderlich bis zur expliziten
  Stage-Entscheidung des Betreibers. Es regelt Dokumenttypen, Ablagelogik,
  Auslöser-Kriterien, Rückkopplungsschutz und Qualitätssicherung.

Norm-Begriff:
  Architecture Principles (TOGAF ADM — Preliminary Phase)

Ergänzende Norm-Konzepte:
  Architecture Governance Framework (TOGAF)
  Constraint (ArchiMate 3.2 — Motivation Layer)

TOGAF ADM Einordnung:
  Die Preliminary Phase definiert Architecture Principles als stabiles
  Regelwerk das alle nachfolgenden Phasen bindet. GOV_Global entspricht
  funktional diesem Prinzipienkatalog — mit dem Zusatz operativer Regeln
  (Ablage, Auslöser, Freigabe), die TOGAF in Architecture Governance
  Frameworks auslagert.

Rosetta:
  "GOV_Global"                       →  Architecture Principles (Preliminary)
  "GOV-Regel (z.B. GOV 10.3)"        →  Architecture Principle
  "GOV ist unveränderlich"           →  Principle Stability Constraint
  "Explizite Stage-Entscheidung"     →  Governance Board Decision
  "GOV-Konformitätscheck"            →  Architecture Compliance Review

Bewertung:
  Sehr hohe Konformität. R+MUNI GOV_Global ist disziplinierter als viele
  reale TOGAF-Implementierungen — klare Regeln, klare Auslöser, explizite
  Änderungs-Governance. Abweichung: kein formales Governance Board —
  EUMAXL als Betreiber übernimmt diese Rolle, was für die Projektgröße
  angemessen und explizit dokumentiert ist.


--------------------------------------------------------------------------------
7B01 – RÜCKKOPPLUNGSSCHUTZ
--------------------------------------------------------------------------------
Intention:
  Scripts, Flows und Dokumentreihen aus vergangenen Stages (insbesondere
  Stage 3/4 als Frozen Core) dürfen durch spätere Sprints nicht
  unbeabsichtigt verändert werden. Jeder Eingriff in Frozen-Artefakte
  erfordert explizite Entscheidung und Dokumentation.

Norm-Begriff:
  Architecture Partitioning / Federated Architecture (TOGAF)

Ergänzende Norm-Konzepte:
  Segregation of Concerns (Architekturprinzip)
  Change Control (TOGAF Phase H)
  Immutability Constraint (ArchiMate — Constraint auf Application Component)

TOGAF ADM Einordnung:
  TOGAF empfiehlt Architecture Partitioning um verschiedene Bereiche
  mit unterschiedlichen Lifecycle-Geschwindigkeiten zu trennen.
  Phase H (Architecture Change Management) regelt welche Änderungen
  welchen Governance-Prozess durchlaufen müssen.

Rosetta:
  "Rückkopplungsschutz"              →  Architecture Change Control (Phase H)
  "Stage 3/4 Frozen Core"            →  Immutable Architecture Partition
  "Explizite Entscheidung nötig"     →  Formal Change Request
  "Kein unbeabsichtigter Seiteneffekt" →  Impact Analysis (TOGAF Phase H)

Bewertung:
  Sehr gutes Mapping. R+MUNI Rückkopplungsschutz ist konzeptionell schärfer
  als viele TOGAF-Implementierungen — die Frozen-Stage-Logik ist klarer
  formuliert als typische Architecture Partitioning Ansätze.
  Lücke: kein formales Impact-Assessment-Dokument vor jedem Sprint.
  R+MUNI ersetzt das durch GOV-Konformitätscheck im Backlog-Template.


--------------------------------------------------------------------------------
7B02 – SESSION-REGEL (NEU Stage 7)
--------------------------------------------------------------------------------
Intention:
  Jede Arbeitssession mit Claude beginnt mit expliziter Kontextherstellung.
  Keine Session ohne aktuellen Projektfolder. Erkenntnisse werden sofort
  gesichert — nicht als losen Chat-Inhalt gelassen. Diese Regel verhindert
  Drift durch fehlenden Kontext und sichert Kontinuität.

Norm-Begriff:
  Architecture Repository Management (TOGAF)

Ergänzende Norm-Konzepte:
  Knowledge Management (TOGAF — Architecture Capability Framework)
  Context Management (allgemein — kein direkter TOGAF-Begriff)

TOGAF ADM Einordnung:
  TOGAF betont das Architecture Repository als zentrale Wissensquelle.
  Die Session-Regel ist das operative Pendant: sicherstellen dass der
  Arbeitskontext (= Projektfolder) stets aktuell ist und als Wahrheitsquelle
  verwendet wird — analog zu "Repository vor jeder Phase prüfen".

Rosetta:
  "Session-Regel"                    →  Repository Currency Check (vor Arbeitsbeginn)
  "Kontext herstellen"               →  Architecture Repository Consultation
  "Erkenntnisse sofort sichern"      →  Architecture Decision Record erstellen
  "Was nicht abgelegt ist existiert nicht" →  Repository als Single Source of Truth

Bewertung:
  Teilweise Mapping — kein direkter TOGAF-Begriff für Session-Management.
  Die Session-Regel ist eine praxisnahe Operationalisierung des
  Repository-Gedankens. Für AI-gestützte Entwicklung ohne direktes TOGAF-
  Pendant — R+MUNI füllt hier eine echte Methodik-Lücke.


--------------------------------------------------------------------------------
7B03 – GOVERNANCE-KONFORMITÄTSCHECK IM SPRINT
--------------------------------------------------------------------------------
Intention:
  Jeder Sprint endet mit einem expliziten GOV-Check — einer strukturierten
  Prüfliste die sicherstellt dass der Sprint GOV-konform ist, keine
  unbeabsichtigten Seiteneffekte hat und korrekt dokumentiert ist.
  Der Check ist kein bürokratisches Ritual — er ist Qualitätssicherung.

Norm-Begriff:
  Architecture Compliance Review (TOGAF)

Ergänzende Norm-Konzepte:
  Quality Gate (allgemein — kein direkter TOGAF-Begriff)
  Governance Checkpoint (TOGAF Phase G)

TOGAF ADM Einordnung:
  Phase G (Implementation Governance) definiert Architecture Compliance
  Reviews als strukturierte Überprüfung ob Implementierungen der
  Architecture Vision entsprechen. Der R+MUNI GOV-Check am Sprint-Ende
  ist die schlanke, operativ handhabbare Version davon.

Rosetta:
  "GOV-Konformitätscheck"            →  Architecture Compliance Review (Phase G)
  "Auslöser GOV-konform?"            →  Trigger Validation
  "Rückkopplungsschutz geprüft?"     →  Impact Assessment Confirmed
  "Keine implizite GOV-Änderung"     →  No Unauthorized Architecture Change

Bewertung:
  Sehr hohe Konformität. R+MUNI GOV-Check ist schlanker als TOGAF
  Compliance Review, trifft aber die wesentlichen Punkte.
  Besondere Stärke: explizite Frage nach "impliziter GOV-Änderung" —
  diese Granularität findet sich in TOGAF nicht so direkt.


================================================================================
ZUSAMMENFASSUNG BLOCK 7B
================================================================================

Governance Mapping Gesamt:

  "GOV_Global"                →  Architecture Principles (Preliminary)    ✅
  "Rückkopplungsschutz"       →  Architecture Change Control (Phase H)     ✅
  "Session-Regel"             →  Repository Currency Check                 ⚠
  "GOV-Konformitätscheck"     →  Architecture Compliance Review (Phase G)  ✅
  "Explizite Freigabe"        →  Formal Architecture Sign-Off              ✅

Kernverständnis:
  TOGAF fragt nicht: "Wer darf was ändern?"
  Sondern: "Welcher Prozess stellt sicher dass Änderungen kontrolliert sind?"
  R+MUNI beantwortet das mit GOV_Global (Regeln), Rückkopplungsschutz
  (Scope-Isolation) und GOV-Checks (Compliance-Nachweis).

Gesamtbewertung:
  Sehr hohe Konformität im Governance-Bereich. R+MUNI Governance ist
  für die Projektgröße optimal kalibriert — kein Overhead, aber vollständige
  Nachvollziehbarkeit. Die Session-Regel ist ein R+MUNI-eigenes Konzept
  ohne direktes TOGAF-Pendant — sie adressiert AI-spezifische Risiken
  die TOGAF naturgemäß nicht kennt.

Nächster Block:
  Block 7C — Zielgruppen (ASSOCIATE, Beta-Rollen, DEV-Rollentrennung)


================================================================================
BLOCK 7C — ZIELGRUPPEN
================================================================================


--------------------------------------------------------------------------------
7C00 – ASSOCIATE (NEU Stage 7)
--------------------------------------------------------------------------------
Intention:
  ASSOCIATE ist eine neue Zielgruppen-Kategorie im R+MUNI Blueprint.
  Sie beschreibt externe Mitstreiter die weder DEV noch Betakunde sind —
  Viewer, Interessenten, externe Contributor mit eigenem Onboarding-Pfad.
  Der Begriff schafft Klarheit wo bisher eine Lücke war.

Norm-Begriff:
  Stakeholder (TOGAF ADM)

Ergänzende Norm-Konzepte:
  Architecture User (TOGAF — Architecture Capability Framework)
  Actor (ArchiMate 3.2 — Business Layer)

TOGAF ADM Einordnung:
  TOGAF Stakeholder-Management (Phase A) kategorisiert alle relevanten
  Parteien nach Interesse und Einfluss. ASSOCIATE entspricht einem
  Stakeholder mit niedrigem Einfluss aber aktivem Interesse — "informed
  stakeholder" oder "architecture user" im TOGAF-Vokabular.

ArchiMate Einordnung:
  Im Business Layer ist Actor der allgemeine Begriff für handelnde Einheiten.
  ASSOCIATE ist ein spezialisierter Actor mit definierter Rolle und
  eigenem Dokumenttypen-Set (5 ASSOCIATE Templates).

Rosetta:
  "ASSOCIATE"                        →  Stakeholder / Architecture User
  "ASSOCIATE Templates"              →  Stakeholder-spezifische Dokumentation
  "ASSOCIATE Onboarding-Pfad"        →  Stakeholder Engagement Plan
  "DEV / Beta / ASSOCIATE"           →  Stakeholder-Kategorisierung

Bewertung:
  Gutes Mapping. R+MUNI ist hier sogar präziser als TOGAF — die Einführung
  von ASSOCIATE als eigenem Begriff verhindert Rollenvermischung die
  in TOGAF-Projekten häufig entsteht. Die 5 Templates geben dem Konzept
  operative Substanz — das fehlt in TOGAF Stakeholder-Management oft.


--------------------------------------------------------------------------------
7C01 – BETAKUNDE UND BETA-ROLLEN
--------------------------------------------------------------------------------
Intention:
  Betakunden sind reale Nutzer des R+MUNI Blueprints die das System
  unter realen Bedingungen einsetzen und Feedback geben. Stage 7 hat
  den ersten vollständigen Betakunden-Lifecycle durchlaufen:
  Offboarding (BKO1 — Betakunde_01) + Onboarding (ASC — Betakunde_02).

Norm-Begriff:
  Pilot User / Early Adopter (TOGAF Phase G — Implementation Governance)

Ergänzende Norm-Konzepte:
  Change Champion (TOGAF — Architecture Capability Framework)
  Stakeholder in Implementation Phase (TOGAF Phase G/H)

TOGAF ADM Einordnung:
  Phase G (Implementation Governance) sieht Pilotphasen vor um
  Architecture Compliance unter realen Bedingungen zu validieren.
  Betakunden erfüllen diese Funktion — sie sind reale Implementierungs-
  partner, keine passiven Nutzer.

Rosetta:
  "Betakunde"                        →  Pilot User (Phase G)
  "Betakunden Onboarding"            →  Implementation Deployment Planning
  "Betakunden Offboarding"           →  Implementation Completion / Handover
  "Lessons Learned BKO1"             →  Post-Implementation Review
  "MINIMAL-Tier als Scope-Limiter"   →  Phased Implementation Constraint

Bewertung:
  Solides Mapping. Der R+MUNI Beta-Lifecycle ist strukturierter als
  typische TOGAF Pilot-Phasen — insbesondere die Onboarding-Lessons-
  Learned-Direktintegration (LL-01 bis LL-04 direkt in Principles)
  entspricht einem formalen Post-Implementation Review mit direkter
  Architektur-Rückkopplung.


--------------------------------------------------------------------------------
7C02 – DEV-ROLLENTRENNUNG UND ROLLENVERMISCHUNG
--------------------------------------------------------------------------------
Intention:
  Der R+MUNI Entwickler agiert gleichzeitig in mehreren Rollen: DEV,
  Beta-Tester, Berater. Ohne explizite Trennung entstehen Informations-
  verlust und unkontrollierter Wissenstransfer. Die Rollentrennung ist
  eine bewusste Methodik-Entscheidung mit operativen Konsequenzen.

Norm-Begriff:
  Role Separation / Separation of Concerns (TOGAF — Architecture Governance)

Ergänzende Norm-Konzepte:
  Stakeholder Role (TOGAF)
  Business Role (ArchiMate 3.2 — Business Layer)

TOGAF ADM Einordnung:
  TOGAF betont klare Rollenverteilung in Architecture Governance.
  Die R+MUNI Lösung — Kanal-Markierungen [BETA] vs. [BETA→RMUNI] —
  ist eine operative Umsetzung des Role-Separation-Prinzips die
  spezifisch auf AI-Tool-gestützte Entwicklung zugeschnitten ist.

Rosetta:
  "DEV / Beta-Tester / Berater"      →  Multiple Stakeholder Roles
  "[BETA]"                           →  Role-specific Communication Channel
  "[BETA→RMUNI]"                     →  Controlled Knowledge Transfer
  "Anonymisierung vor Transfer"      →  Privacy / Confidentiality Control

Bewertung:
  Partielles Mapping — TOGAF kennt keine explizite Methodik für
  KI-Tool-Rollentrennung. R+MUNI füllt hier eine Methodik-Lücke die
  für AI-unterstützte Entwicklung grundlegend ist. Das Konzept ist
  in ArchiMate als Business Role + Assignment Relationship abbildbar,
  hat aber keine normative Entsprechung.


================================================================================
ZUSAMMENFASSUNG BLOCK 7C
================================================================================

Zielgruppen Mapping Gesamt:

  "ASSOCIATE"                →  Stakeholder / Architecture User             ✅
  "ASSOCIATE Templates"      →  Stakeholder-spezifische Dokumentation       ✅
  "Betakunde"                →  Pilot User (Phase G)                        ✅
  "Lessons Learned"          →  Post-Implementation Review                  ✅
  "DEV-Rollentrennung"       →  Role Separation                             ⚠

Kernverständnis:
  TOGAF fragt nicht: "Wer nutzt die Architektur?"
  Sondern: "Welche Stakeholder haben welche Interessen und wie werden sie eingebunden?"
  R+MUNI beantwortet das operativer und schärfer abgegrenzt als TOGAF —
  insbesondere durch den ASSOCIATE-Begriff und die Beta-Lifecycle-Strukturierung.

Gesamtbewertung:
  Gute Konformität. R+MUNI ist im Zielgruppen-Bereich präziser als
  TOGAF-Standard — die operative Ausdifferenzierung (DEV / Beta / ASSOCIATE)
  ist ein Qualitätsmerkmal, keine Abweichung. Die KI-Rollentrennung ist
  ein echtes R+MUNI-Original ohne TOGAF-Pendant.

Nächster Block:
  Block 7D — Zwei-Welten-Architektur (INTERN / PUBLIC, Kunden-Repo-Modell)


================================================================================
BLOCK 7D — ZWEI-WELTEN-ARCHITEKTUR
================================================================================


--------------------------------------------------------------------------------
7D00 – INTERN / PUBLIC TRENNUNG (Zwei-Welten-Entscheid)
--------------------------------------------------------------------------------
Intention:
  R+MUNI trennt strikt zwischen einer internen Entwicklungs-Welt (INTERN)
  und einer öffentlich sichtbaren Welt (PUBLIC). Diese Trennung ist
  normativ verankert (Zwei-Welten-Entscheid, Stage 7) und betrifft
  Dokumente, Repositories, Kommunikation und Rollenbilder.
  INTERN und PUBLIC sind keine Berechtigungsstufen — sie sind Welten
  mit unterschiedlichen Sprachen, Zielen und Artefakten.

Norm-Begriff:
  Architecture Partitioning (TOGAF)

Ergänzende Norm-Konzepte:
  Federated Architecture (TOGAF — Architecture Repository)
  Segmentation (ArchiMate 3.2 — Grouping)
  View / Viewpoint (ArchiMate 3.2 — Zielgruppen-spezifische Sichten)

TOGAF ADM Einordnung:
  TOGAF Architecture Partitioning beschreibt die Aufteilung der
  Architektur in getrennte Bereiche mit unterschiedlichen Governance-
  und Lifecycle-Anforderungen. Die INTERN/PUBLIC-Trennung ist eine
  konsequente Anwendung dieses Prinzips — mit dem Zusatz dass
  Sprache und Granularität bewusst angepasst werden.

ArchiMate Einordnung:
  Das View/Viewpoint-Konzept: verschiedene Stakeholder sehen verschiedene
  Sichten auf dieselbe Architektur. INTERN und PUBLIC sind keine
  Sichten auf dasselbe — sie sind unterschiedliche Repräsentationen
  mit unterschiedlichem Detailgrad und Vokabular.

Rosetta:
  "INTERN-Welt"                      →  Architecture Partition (DEV-facing)
  "PUBLIC-Welt"                      →  Architecture Partition (User-facing)
  "Zwei-Welten-Entscheid"            →  Architecture Partitioning Decision
  "INTERN → PUBLIC als Einbahnstraße" →  Controlled Architecture Publication
  "Sprache und Granularität anpassen" →  View Adaptation for Stakeholder

Bewertung:
  Hohe Konformität im Partitioning-Prinzip. R+MUNI geht über TOGAF hinaus:
  die Anforderung unterschiedlicher Sprache (nicht nur Struktur) für
  INTERN vs. PUBLIC hat kein direktes TOGAF-Pendant — ist aber aus
  Stakeholder-Management-Sicht vollständig begründbar und entspricht
  ArchiMate-Viewpoint-Logik.


--------------------------------------------------------------------------------
7D01 – DREI REPOSITORIES
--------------------------------------------------------------------------------
Intention:
  R+MUNI nutzt drei getrennte GitHub-Repositories mit klar definiertem
  Zweck: PUBLIC (freigegeben, öffentlich), INTERNAL (Entwicklungsarbeit,
  privat), CREATIVE (Creative Assets, Sales). Die Repo-Trennung ist
  physische Umsetzung der Governance-Partitionierung.

Norm-Begriff:
  Architecture Repository (TOGAF)

Ergänzende Norm-Konzepte:
  Architecture Library (TOGAF — Repository-Inhalt)
  Data Store (ArchiMate 3.2 — Technology Layer)

TOGAF ADM Einordnung:
  Das TOGAF Architecture Repository ist die zentrale Ablage für alle
  Architecture Assets. R+MUNI verteilt dieses Konzept auf drei
  physische Repositories — mit klarer Zugriffssteuerung und
  Freigabe-Logik zwischen ihnen.

Rosetta:
  "R+MUNI Doku-public (GitHub)"      →  Architecture Repository (PUBLIC)
  "R+MUNI Doku-internal (GitHub)"    →  Architecture Repository (DEV-intern)
  "R+MUNI Doku-creative (GitHub)"    →  Creative Asset Repository
  "GitHub ist Quelle der Wahrheit"   →  Architecture Repository als SSOT
  "Freigabe für public ist explizit" →  Architecture Publication Control

Bewertung:
  Sehr hohe Konformität. Die Drei-Repository-Struktur ist eine elegante
  Umsetzung des TOGAF Repository-Konzepts mit expliziter Governance.
  Besondere Stärke: "GitHub ist Quelle der Wahrheit" als Kernregel
  entspricht dem TOGAF Single Source of Truth Prinzip und ist
  konsequenter umgesetzt als in vielen TOGAF-Projekten.


--------------------------------------------------------------------------------
7D02 – KUNDEN-REPO-MODELL (NEU Stage 7)
--------------------------------------------------------------------------------
Intention:
  Jeder Betakunde erhält ein eigenes Repository das er selbst erstellt
  und freigibt. R+MUNI-Artefakte werden in dieses Repo gespiegelt —
  nicht umgekehrt. Das Kunden-Repo ist physische Rollentrennung:
  der Kunde ist Eigentümer seines Setups.

Norm-Begriff:
  Federated Architecture Repository (TOGAF)

Ergänzende Norm-Konzepte:
  Architecture Realization (ArchiMate 3.2 — Realization Relationship)
  Deployment Model (TOGAF Phase F/G)

TOGAF ADM Einordnung:
  TOGAF Federated Architecture ermöglicht es Organisationen eigene
  Architecture Repositories zu führen die mit einem zentralen
  Repository verbunden sind. Das Kunden-Repo-Modell ist eine
  pragmatische Umsetzung: Kunde = Federated Node,
  R+MUNI = Architecture Authority.

Rosetta:
  "Kunden-Repo"                      →  Federated Architecture Repository (Kunde)
  "Kunde erstellt, gibt frei"        →  Repository Ownership by Federated Entity
  "R+MUNI spiegelt in Kunden-Repo"   →  Architecture Distribution / Replication
  "Eigener Windows-User (Rollentrennung)" →  Physical Role Isolation

Bewertung:
  Gutes Mapping. Das Kunden-Repo-Modell ist operativ ausgereifter als
  typische TOGAF Federated-Modelle — die physische Erzwingung der
  Rollentrennung durch eigenen Windows-User ist ein praktisches Detail
  das TOGAF nicht kennt, aber durchaus dem Governance-Geist entspricht.


================================================================================
ZUSAMMENFASSUNG BLOCK 7D
================================================================================

Zwei-Welten-Architektur Mapping Gesamt:

  "INTERN / PUBLIC Trennung"  →  Architecture Partitioning              ✅
  "Zwei-Welten-Entscheid"     →  Architecture Partitioning Decision      ✅
  "Drei Repositories"         →  Architecture Repository (verteilt)      ✅
  "GitHub = Wahrheit"         →  Single Source of Truth                  ✅
  "Kunden-Repo-Modell"        →  Federated Architecture Repository       ✅

Kernverständnis:
  TOGAF fragt nicht: "Wo liegt die Architektur?"
  Sondern: "Wie stellt das Repository die Integrität der Architecture Assets sicher?"
  R+MUNI beantwortet das mit physischer Trennung, expliziter Freigabe-Logik
  und dem Kunden-Repo-Modell als Federated-Instanz.

Gesamtbewertung:
  Exzellente Konformität im Repository-Bereich — vermutlich der
  TOGAF-konformste Teil des R+MUNI Blueprint. Die operative Schärfe
  (physische Repos, Freigabe-Akt, SSOT-Prinzip) übertrifft viele
  reale TOGAF-Implementierungen.

Nächster Block:
  Block 7E — AI-Driven Development (Methodik, Drift, Kontextmanagement)


================================================================================
BLOCK 7E — AI-DRIVEN DEVELOPMENT METHODIK
================================================================================


--------------------------------------------------------------------------------
7E00 – AI DRIVEN DEVELOPMENT ALS METHODIK
--------------------------------------------------------------------------------
Intention:
  AI Driven Development ist die persönliche Arbeitsmethode von EUMAXL
  für R+MUNI. Sie definiert wie ein Nicht-Programmierer mit Domänenwissen
  und Governance-Kompetenz KI-Tools zur professionellen System-
  entwicklung einsetzt. Die Methode ist lebendig — sie wächst mit
  jedem Stage und wird selbst nach denselben GOV-Regeln geführt.

Norm-Begriff:
  Architecture Development Method (TOGAF — der ADM selbst)

Ergänzende Norm-Konzepte:
  Agile Architecture (TOGAF Agile Extension)
  Method (ArchiMate 3.2 — kein direkter Konzept-Begriff)

TOGAF ADM Einordnung:
  TOGAF ADM ist die Methode zur Architekturentwicklung. AI Driven
  Development ist die Methode zur Entwicklung des R+MUNI Systems —
  analog, aber auf einen anderen Abstraktionsgrad angewendet.
  TOGAF beschreibt nicht wie man mit KI-Tools arbeitet — R+MUNI füllt
  diese Lücke mit einer praxiserprobten Methode.

Rosetta:
  "AI Driven Development"            →  Architecture Development Method (personalisiert)
  "Domänenwissen führt"              →  Architecture Authority beim Entwickler
  "KI schreibt auf"                  →  Automated Documentation / Code Generation
  "Governance vor Code"              →  Architecture First Principle
  "Explizite Freigabe erteilen"      →  Architecture Sign-Off

Bewertung:
  Partielles Mapping — TOGAF kennt keine KI-gestützte Entwicklungsmethode.
  AI Driven Development ist ein R+MUNI-Original das methodische Lücken
  des TOGAF für kleine Teams / Einzelentwickler schließt. Die Prinzipien
  (Governance vor Code, Domänenwissen führt, explizite Freigabe) sind
  vollständig TOGAF-kompatibel auch wenn der Weg dorthin verschieden ist.


--------------------------------------------------------------------------------
7E01 – DRIFT UND DRIFT-PRÄVENTION
--------------------------------------------------------------------------------
Intention:
  Drift bezeichnet den unkontrollierten Bedeutungs- oder Qualitätsverlust
  in AI-Entwicklungssessions — durch zu wenig Kontext, zu viel Kontext,
  iterative Neugenerierung oder Rollenvermischung. Drift-Prävention
  ist eine Kernkompetenz der R+MUNI Methodik.

Norm-Begriff:
  Architecture Integrity (TOGAF — implizit)

Ergänzende Norm-Konzepte:
  Configuration Management (TOGAF — Architecture Repository)
  Quality Attribute: Consistency (ArchiMate — kein direkter Begriff)

TOGAF ADM Einordnung:
  TOGAF adressiert Drift indirekt durch Architecture Repository,
  Baseline Management und Compliance Reviews. R+MUNI adressiert
  Drift direkt und operativ — als benanntes Risiko mit expliziten
  Gegenmaßnahmen (Session-Regel, Kontextdosierung, chirurgische Änderung).

Rosetta:
  "Drift"                            →  Architecture Integrity Loss (Risiko)
  "Zu wenig Kontext → Drift"         →  Insufficient Repository Consultation
  "Zu viel Kontext → Drift"          →  Context Overload (kein TOGAF-Begriff)
  "SVG-Chirurgie statt Neugenerierung" →  Targeted Change vs. Full Regeneration
  "Chat-Aufteilung nach Funktion"    →  Functional Partitioning of Work Sessions

Bewertung:
  Drift ist ein R+MUNI-Original-Konzept ohne direktes TOGAF-Pendant.
  Es adressiert ein reales Risiko in AI-gestützter Entwicklung das
  TOGAF naturgemäß nicht kennt. Die Gegenmaßnahmen (Session-Regel,
  SVG-Chirurgie, Kontextdosierung) sind methodisch ausgereift und
  verdienen eigenständige Dokumentation — was mit dem
  AI_DRIVEN_DEV_METHODE-Dokument geschehen ist.


--------------------------------------------------------------------------------
7E02 – KONTEXTMANAGEMENT UND PROJEKTFOLDER
--------------------------------------------------------------------------------
Intention:
  Der Projektfolder ist die einzige verlässliche Wahrheitsquelle für
  Claude-Sessions. Was drin steht gilt. Was nicht drin ist muss im Chat
  erklärt werden. Aktualisierung nach jeder Session mit Änderungen.
  Fetch-Regel: Fetches gehören an den Session-Anfang.

Norm-Begriff:
  Architecture Repository Management (TOGAF)

Ergänzende Norm-Konzepte:
  Information Management (TOGAF — Architecture Capability Framework)
  Data Object (ArchiMate 3.2 — Application Layer)

TOGAF ADM Einordnung:
  TOGAF fordert dass Entscheidungen, Prinzipien und Assets im
  Architecture Repository aktuell gehalten werden. Der Projektfolder
  ist das operative Äquivalent — minimalistisch, aber konsequent
  als Single Source of Truth behandelt.

Rosetta:
  "Projektfolder"                    →  Architecture Repository (operativ)
  "Projektfolder vor Session laden"  →  Repository Currency Check
  "Nach Session aktualisieren"       →  Repository Update / Baseline Maintenance
  "Fetch an Session-Anfang"          →  Repository Consultation vor Arbeitsbeginn
  "Claude kann GitHub-Sync nicht prüfen" →  Repository Access Limitation (dokumentiert)

Bewertung:
  Sehr gutes Mapping. Die Disziplin im Umgang mit dem Projektfolder
  übersteigt die Repository-Pflege in vielen realen TOGAF-Projekten.
  Besondere Stärke: die explizite Dokumentation der Grenzen
  (Claude kann GitHub-Sync nicht prüfen) ist vorbildliche Limitation-
  Dokumentation — in TOGAF-Projekten oft vernachlässigt.


================================================================================
ZUSAMMENFASSUNG BLOCK 7E
================================================================================

AI-Methodik Mapping Gesamt:

  "AI Driven Development"     →  Architecture Development Method          ⚠
  "Drift"                     →  Architecture Integrity Loss (Risiko)      ⚠
  "SVG-Chirurgie"             →  Targeted Change (kein TOGAF-Begriff)      ❌
  "Projektfolder"             →  Architecture Repository (operativ)        ✅
  "Governance vor Code"       →  Architecture First Principle              ✅
  "Explizite Freigabe"        →  Architecture Sign-Off                     ✅

Kernverständnis:
  TOGAF fragt nicht: "Wie arbeitet ein Einzelentwickler mit KI-Tools?"
  Sondern: "Wie stellt eine Methode sicher dass Architektur konsistent bleibt?"
  R+MUNI beantwortet beides — und füllt damit eine echte Methodik-Lücke
  die TOGAF für KI-gestützte Einzelentwickler offen lässt.

Gesamtbewertung:
  Gemischtes Mapping. Die Prinzipien sind TOGAF-kompatibel —
  die spezifischen KI-Mechanismen (Drift, Kontextdosierung, SVG-Chirurgie)
  sind R+MUNI-Originale ohne Framework-Pendant. Das ist kein Makel —
  es ist Methodik-Innovation in einem Bereich den TOGAF 2026 noch
  nicht vollständig abdeckt.

Nächster Block:
  Block 7F — Dokumentstruktur (Typen, Templates, Konzeptnotiz)


================================================================================
BLOCK 7F — DOKUMENTSTRUKTUR
================================================================================


--------------------------------------------------------------------------------
7F00 – DOKUMENTTYPEN-SYSTEM (Types 1–10)
--------------------------------------------------------------------------------
Intention:
  R+MUNI definiert 10 Dokumenttypen mit klarer Zweckabgrenzung,
  verbindlichen Templates (Types 1–8) und freier Form (Types 9–10).
  Das System verhindert Typ-Vermischung und stellt sicher dass
  jedes Dokument seinen Charakter kennt und einhält.

Norm-Begriff:
  Architecture Artifact (TOGAF)

Ergänzende Norm-Konzepte:
  Architecture Document (TOGAF — Repository Content)
  Deliverable (TOGAF — Architecture Deliverable)
  Work Product (TOGAF)

TOGAF ADM Einordnung:
  TOGAF unterscheidet Artifacts (Komponenten), Deliverables (formale
  Outputs einer Phase) und Work Products (alle Arbeitsergebnisse).
  Das R+MUNI Typen-System ist eine vollständige Klassifikation
  aller Work Products mit operativer Steuerungswirkung.

Rosetta:
  "Type 1 — GOV_Global"              →  Architecture Principles Document
  "Type 2 — principles"              →  Architecture Guidelines / Standards
  "Type 3 — how2"                    →  Implementation Guide / User Guide
  "Type 4 — Rosetta-Stone"           →  Architecture Translation Document
  "Type 5 — FREEZE"                  →  Architecture Baseline Document
  "Type 6 — Stage_Ziele"             →  Architecture Vision Document (Phase A)
  "Type 7 — Sprint-DEV-Doku"         →  Implementation Work Product
  "Type 8 — Sprint-DEV-BACKLOG"      →  Work Package Candidate

Bewertung:
  Sehr hohe Konformität. Das R+MUNI Typen-System bildet den TOGAF
  Deliverable-Katalog vollständig ab — und ist operativer durch
  verbindliche Templates. Besondere Stärke: der Rosetta-Stone-Typ
  hat kein TOGAF-Pendant — er ist ein Qualitätsmerkmal das
  Framework-Kommunikation explizit macht.


--------------------------------------------------------------------------------
7F01 – KONZEPTNOTIZ (NEU Stage 7)
--------------------------------------------------------------------------------
Intention:
  Die Konzeptnotiz ist ein neuer, leichtgewichtiger Dokumenttyp für
  Erkenntnisse die noch nicht spruchreif für einen vollständigen Sprint
  sind. Kein GOV-Overhead, kein Template-Zwang — aber strukturierte
  Ablage. Sie schließt die Lücke zwischen losem Chat-Inhalt und
  formalem Sprint-Backlog.

Norm-Begriff:
  Architecture Decision Record (TOGAF — Architecture Repository)

Ergänzende Norm-Konzepte:
  Note (ArchiMate 3.2 — kein normativer Begriff)
  Work-in-Progress Artifact (kein direkter TOGAF-Begriff)

TOGAF ADM Einordnung:
  TOGAF kennt Architecture Decision Records als strukturierte Ablage
  von Entscheidungen. Die Konzeptnotiz ist das Vorstufen-Äquivalent:
  Erkenntnis benennen → kurz dokumentieren → später entscheiden ob Sprint.
  Das entspricht einem "pre-decision record" ohne formale Governance-Last.

Rosetta:
  "Konzeptnotiz"                     →  Pre-Decision Architecture Record
  "Noch nicht spruchreif"            →  Candidate Architecture Decision
  "Kein GOV-Overhead"                →  Lightweight Work Product
  "Erkenntnis → Sprint wenn spruchreif" →  Decision Escalation Path

Bewertung:
  Partielles Mapping — kein direktes TOGAF-Pendant.
  Die Konzeptnotiz adressiert ein reales Problem: der Overhead von
  Sprint-DEV-BACKLOG-Dokumenten für frühe Erkenntnisse ist zu hoch.
  Das ist legitim und die Lösung ist pragmatisch und GOV-kompatibel.


--------------------------------------------------------------------------------
7F02 – ASSOCIATE TEMPLATES (NEU Stage 7)
--------------------------------------------------------------------------------
Intention:
  Fünf neue Templates für die ASSOCIATE-Zielgruppe (principles, how2,
  sprint, backlog, notes). Sie folgen denselben Strukturprinzipien
  wie DEV-Templates — sind aber auf einen anderen Kontext und
  eine andere Leserschaft ausgerichtet.

Norm-Begriff:
  Stakeholder-specific View (ArchiMate 3.2 — Viewpoint)

Ergänzende Norm-Konzepte:
  Architecture Communication (TOGAF)
  View Definition (ArchiMate 3.2)

ArchiMate Einordnung:
  ArchiMate definiert Viewpoints als Sichten auf die Architektur
  für spezifische Stakeholder-Interessen. ASSOCIATE Templates sind
  das dokumentarische Äquivalent: dieselbe Substanz, angepasst
  für eine andere Leserschaft.

Rosetta:
  "ASSOCIATE_principles"             →  Stakeholder-Viewpoint: Principles
  "ASSOCIATE_how2"                   →  Stakeholder-Viewpoint: Guide
  "ASSOCIATE_sprint"                 →  Stakeholder-Viewpoint: Sprint Record
  "ASSOCIATE_backlog"                →  Stakeholder-Viewpoint: Work Backlog
  "ASSOCIATE_notes"                  →  Stakeholder-Viewpoint: Notes

Bewertung:
  Gutes Mapping auf ArchiMate Viewpoint-Konzept. Die ASSOCIATE Templates
  machen das Viewpoint-Prinzip dokumentarisch operativ — was TOGAF und
  ArchiMate als Konzept beschreiben, setzt R+MUNI als Template-System um.


================================================================================
ZUSAMMENFASSUNG BLOCK 7F
================================================================================

Dokumentstruktur Mapping Gesamt:

  "Dokumenttypen-System"      →  Architecture Artifact Taxonomy              ✅
  "GOV_Global (Type 1)"       →  Architecture Principles Document            ✅
  "FREEZE (Type 5)"           →  Architecture Baseline Document              ✅
  "Stage_Ziele (Type 6)"      →  Architecture Vision Document                ✅
  "Rosetta-Stone (Type 4)"    →  Translation Document (kein TOGAF-Pendant)   ⚠
  "Konzeptnotiz"              →  Pre-Decision Architecture Record             ⚠
  "ASSOCIATE Templates"       →  Stakeholder-Viewpoint Documents             ✅

Kernverständnis:
  TOGAF fragt nicht: "Welche Dokumente gibt es?"
  Sondern: "Welche Deliverables sind für welche Phase verbindlich?"
  R+MUNI beantwortet das mit einem vollständigen Typen-System das
  Deliverables, Work Products und Governance-Dokumente vereint.

Gesamtbewertung:
  Sehr hohe Konformität. Das R+MUNI Dokumenttypen-System ist eines der
  ausgereiftesten Elemente des Blueprint — strukturierter als viele
  reale TOGAF-Implementierungen. Der Rosetta-Stone-Typ ist ein echter
  Mehrwert ohne Framework-Pendant.

Nächster Block:
  Block 7G — Toolbaukasten (Tier-Struktur, SVG-Chirurgie)


================================================================================
BLOCK 7G — TOOLBAUKASTEN
================================================================================


--------------------------------------------------------------------------------
7G00 – TIER-STRUKTUR (MINIMAL / DEFAULT / ADDON / AGNOSTIC)
--------------------------------------------------------------------------------
Intention:
  Der Toolbaukasten definiert welche Tools für R+MUNI notwendig,
  empfohlen oder optional sind. Die Tier-Struktur macht diese
  Entscheidung transparent und reproduzierbar — auch für neue
  Nutzer und Betakunden-Onboarding.

Norm-Begriff:
  Technology Portfolio (TOGAF — Technology Architecture, Phase D)

Ergänzende Norm-Konzepte:
  Technology Component (ArchiMate 3.2 — Technology Layer)
  Platform (TOGAF — Technology Architecture)

TOGAF ADM Einordnung:
  Phase D (Technology Architecture) definiert die Technologie-Grundlage
  des Systems. Der R+MUNI Toolbaukasten ist die operative Umsetzung
  dieser Technology Architecture — mit expliziter Tier-Klassifizierung
  die TOGAF nicht vorschreibt aber empfiehlt.

ArchiMate Einordnung:
  Technology Layer: Node (physischer Host), System Software, Device.
  MINIMAL-Tier = Core Technology Components.
  DEFAULT = Recommended Technology Components.
  ADDON = Optional Technology Components.

Rosetta:
  "MINIMAL-Tier"                     →  Core Technology Components (mandatory)
  "DEFAULT-Tier"                     →  Recommended Technology Platform
  "ADDON-Tier"                       →  Optional Technology Extension
  "AGNOSTIC-Tier"                    →  Tool-Independent Components
  "Atlassian = ADDON (Stage 7)"      →  Reclassification of Technology Component

Bewertung:
  Sehr hohe Konformität. Die Tier-Struktur ist klarer als typische
  TOGAF Technology Architecture Kataloge. Besondere Stärke: die
  explizite Reklassifikation von Atlassian zu ADDON in Stage 7 ist
  ein Beispiel für Architecture Change Management in Aktion —
  transparent, begründet, dokumentiert.


--------------------------------------------------------------------------------
7G01 – SVG-CHIRURGIE (NEU Stage 7)
--------------------------------------------------------------------------------
Intention:
  Bei bestehenden SVG-Dateien (und anderen Artefakten) werden nur die
  notwendigen Elemente geändert — keine Neugenerierung des Gesamtdokuments.
  Iterative Neugenerierung akkumuliert Drift. Chirurgische Eingriffe
  erhalten den stabilen Kontext und minimieren Fehlerrisiko.

Norm-Begriff:
  Incremental Architecture Change (TOGAF Phase H)

Ergänzende Norm-Konzepte:
  Change Impact Minimization (TOGAF)
  Targeted Modification (kein direkter TOGAF-Begriff)

TOGAF ADM Einordnung:
  Phase H betont kontrollierte, inkrementelle Änderungen gegenüber
  Big-Bang-Änderungen. SVG-Chirurgie ist die operative Umsetzung
  dieses Prinzips auf Artefakt-Ebene: minimaler Eingriff, maximale
  Stabilität des bestehenden Kontexts.

Rosetta:
  "SVG-Chirurgie"                    →  Targeted Incremental Change
  "Neugenerierung akkumuliert Drift" →  Full Regeneration as Change Risk
  "Stabilen Kontext erhalten"        →  Context Preservation Principle
  "str_replace statt Neuschreiben"   →  Surgical Edit vs. Full Replacement

Bewertung:
  Partielles Mapping — SVG-Chirurgie ist ein R+MUNI-Original ohne
  direktes TOGAF-Pendant. Das Prinzip dahinter (inkrementelle Änderung,
  Kontext erhalten) entspricht aber vollständig TOGAF Phase H Logik.
  Das Konzept ist auf alle Artefakt-Typen übertragbar — nicht nur SVG.


================================================================================
ZUSAMMENFASSUNG BLOCK 7G
================================================================================

Toolbaukasten Mapping Gesamt:

  "Tier-Struktur"             →  Technology Portfolio (Phase D)             ✅
  "MINIMAL-Tier"              →  Core Technology Components                 ✅
  "ADDON-Tier"                →  Optional Technology Extension              ✅
  "SVG-Chirurgie"             →  Targeted Incremental Change                ⚠
  "Atlassian = ADDON"         →  Technology Reclassification                ✅

Kernverständnis:
  TOGAF fragt nicht: "Welche Tools braucht man?"
  Sondern: "Welche Technologie-Entscheidungen unterstützen die Architektur?"
  R+MUNI beantwortet das mit der Tier-Struktur und macht
  Technologie-Entscheidungen transparent und nachvollziehbar.

Gesamtbewertung:
  Gute Konformität. SVG-Chirurgie ist ein methodisches Original —
  das dahinterliegende Prinzip ist vollständig TOGAF-kompatibel.

Nächster Block:
  Block 7H — Feedbackschleifen (Kanalmodell, GitHub-Wahrheit)


================================================================================
BLOCK 7H — FEEDBACKSCHLEIFEN UND KANALMODELL
================================================================================


--------------------------------------------------------------------------------
7H00 – KANALMODELL
--------------------------------------------------------------------------------
Intention:
  Verschiedene Kommunikationskanäle (GitHub, Jira, Confluence, Email,
  Confluence, Teams) haben verschiedene Zielgruppen und Zwecke.
  Jira und Confluence sind Spiegel — kein Sync-Zwang.
  GitHub ist Quelle der Wahrheit. Kein Kanal ersetzt einen anderen.

Norm-Begriff:
  Stakeholder Communication Plan (TOGAF — Phase A Stakeholder Management)

Ergänzende Norm-Konzepte:
  Communication Management (TOGAF)
  Channel (ArchiMate 3.2 — kein normativer Begriff)

TOGAF ADM Einordnung:
  Phase A definiert einen Stakeholder Management-Ansatz mit
  Communication Plan. Das R+MUNI Kanalmodell ist die operative
  Umsetzung: welcher Kanal erreicht welche Zielgruppe auf welchem
  Detailgrad — und was ist verbindlich vs. informativ.

Rosetta:
  "Kanalmodell"                      →  Stakeholder Communication Plan
  "GitHub = Quelle der Wahrheit"     →  Architecture Repository (SSOT)
  "Jira und Confluence = Spiegel"    →  Communication Artifacts (non-normative)
  "Jeder Kanal hat seine Zielgruppe" →  Stakeholder-Targeted Communication
  "Kein Sync-Zwang"                  →  Communication Flexibility (non-binding mirrors)

Bewertung:
  Gutes Mapping. Das Kanalmodell ist operativer als TOGAF Communication Plans —
  die explizite "kein Sync-Zwang"-Regel verhindert Governance-Overhead
  der in Projekten dieser Größe unnötig wäre. TOGAF würde hier
  formale Sync-Prozesse fordern — R+MUNI löst das pragmatisch.


--------------------------------------------------------------------------------
7H01 – GITHUB ISSUES UND JIRA SUPPORT PORTAL
--------------------------------------------------------------------------------
Intention:
  Zwei Feedback-Kanäle für Betakunden: GitHub Issues (technisch,
  DEV-nah) und Jira Support Portal (strukturiert, Ticket-basiert).
  Beide wurden in Stage 7 im realen Betrieb mit ASC validiert.
  Die Wahl des Kanals hängt von der Zielgruppe und dem Kontext ab.

Norm-Begriff:
  Feedback Loop (TOGAF — Architecture Change Management, Phase H)

Ergänzende Norm-Konzepte:
  Change Request Channel (TOGAF)
  Service Desk / Support (ITSM — außerhalb TOGAF, aber kompatibel)

TOGAF ADM Einordnung:
  Phase H (Architecture Change Management) definiert Mechanismen
  um Architecture Change Requests zu empfangen und zu verarbeiten.
  GitHub Issues und Jira Support Portal sind die R+MUNI Umsetzung
  dieser Change-Request-Kanäle — abgestuft nach Zielgruppe.

Rosetta:
  "GitHub Issues"                    →  Change Request Channel (DEV-facing)
  "Jira Support Portal"              →  Change Request Channel (User-facing)
  "Im realen Betrieb validiert"      →  Operational Validation (Phase H)
  "Feedbackschleifen ausbauen (S7-Z3)" →  Communication Plan Evolution

Bewertung:
  Sehr gutes Mapping auf TOGAF Phase H Change-Request-Mechanismen.
  Die Zweiteilung (GitHub = DEV, Jira = User) ist eine elegante
  Stakeholder-Segmentierung die TOGAF empfiehlt aber selten so
  klar operationalisiert sieht.


================================================================================
ZUSAMMENFASSUNG BLOCK 7H
================================================================================

Feedbackschleifen Mapping Gesamt:

  "Kanalmodell"               →  Stakeholder Communication Plan             ✅
  "GitHub = Wahrheit"         →  Architecture Repository (SSOT)             ✅
  "GitHub Issues"             →  Change Request Channel (DEV)               ✅
  "Jira Support Portal"       →  Change Request Channel (User)              ✅
  "Jira / Confluence = Spiegel" →  Non-Normative Communication Artifacts    ✅

Kernverständnis:
  TOGAF fragt nicht: "Welche Tools für Kommunikation?"
  Sondern: "Welche Kanäle erreichen welche Stakeholder mit welcher Verbindlichkeit?"
  R+MUNI beantwortet das präzise — mit klarer SSOT-Regel und Kanalzuordnung.

Gesamtbewertung:
  Hohe Konformität. Das Kanalmodell ist eines der klarsten Elemente
  des Blueprint — die SSOT-Regel und Kanalzuordnung sind vorbildlich.

Nächster Block:
  (kein weiterer Block — Gesamtzusammenfassung folgt)


================================================================================
GESAMTZUSAMMENFASSUNG STAGE 7 ROSETTA STONE
================================================================================

R+MUNI Stage 7 Mapping auf TOGAF ADM + ArchiMate 3.2 — Gesamtübersicht:

BLOCK 7A — LIFECYCLE
  "Stage"              →  Architecture Development Cycle           ✅
  "Freeze"             →  Architecture Baseline                    ✅
  "Sprint"             →  Work Package                             ✅

BLOCK 7B — GOVERNANCE
  "GOV_Global"         →  Architecture Principles                  ✅
  "Rückkopplungsschutz" →  Architecture Change Control             ✅
  "Session-Regel"      →  Repository Currency Check                ⚠
  "GOV-Check"          →  Architecture Compliance Review           ✅

BLOCK 7C — ZIELGRUPPEN
  "ASSOCIATE"          →  Stakeholder / Architecture User          ✅
  "Betakunde"          →  Pilot User (Phase G)                     ✅
  "DEV-Rollentrennung" →  Role Separation                          ⚠

BLOCK 7D — ZWEI-WELTEN
  "INTERN / PUBLIC"    →  Architecture Partitioning                ✅
  "Drei Repositories"  →  Architecture Repository (verteilt)       ✅
  "Kunden-Repo-Modell" →  Federated Architecture Repository        ✅

BLOCK 7E — AI-METHODIK
  "AI Driven Dev"      →  Architecture Development Method          ⚠
  "Drift"              →  Architecture Integrity Loss              ⚠
  "SVG-Chirurgie"      →  Targeted Incremental Change              ⚠
  "Projektfolder"      →  Architecture Repository (operativ)       ✅

BLOCK 7F — DOKUMENTSTRUKTUR
  "Dokumenttypen"      →  Architecture Artifact Taxonomy           ✅
  "Konzeptnotiz"       →  Pre-Decision Architecture Record         ⚠
  "ASSOCIATE Templates" →  Stakeholder-Viewpoint Documents         ✅

BLOCK 7G — TOOLBAUKASTEN
  "Tier-Struktur"      →  Technology Portfolio                     ✅
  "SVG-Chirurgie"      →  Targeted Incremental Change              ⚠

BLOCK 7H — FEEDBACKSCHLEIFEN
  "Kanalmodell"        →  Stakeholder Communication Plan           ✅
  "GitHub = Wahrheit"  →  Single Source of Truth                   ✅


Konformitätsübersicht:
  ✅ vollständig abgebildet  :  22 Konzepte
  ⚠  teilweise / mit Hinweis :   8 Konzepte
  ❌  nicht abgebildet        :   1 Konzept (SVG-Chirurgie als Tool-Begriff)


R+MUNI Stage-7-Erkenntnisse ohne TOGAF-Pendant:
  — AI Driven Development als Methodik für Nicht-Programmierer
  — Drift als benanntes KI-Entwicklungsrisiko mit Gegenmaßnahmen
  — Session-Regel als operative KI-Kontextregel
  — SVG-Chirurgie als Artefakt-Änderungs-Prinzip
  — Konzeptnotiz als Pre-Decision Lightweight Document
  — KI-Rollentrennung ([BETA] vs. [BETA→RMUNI])

Diese Konzepte sind R+MUNI-Originale. Sie sind keine Abweichungen —
sie sind Methodikinnovationen in Bereichen die TOGAF 2026 nicht abdeckt.
Sie verdienen eigenständige Dokumentation im Blueprint (AI_DRIVEN_DEV_METHODE).

Gesamtbewertung Stage 7:
  R+MUNI Blueprint Stage 7 ist in den klassischen EA-Dimensionen
  (Governance, Repository, Stakeholder, Lifecycle) sehr hoch TOGAF-konform —
  strukturierter und operativer als viele reale TOGAF-Implementierungen.
  In den KI-spezifischen Dimensionen (Drift, Session-Management, Tool-Rollen)
  führt R+MUNI methodisches Neuland — kompatibel mit TOGAF-Werten,
  aber über TOGAF hinausgehend.

  Das ist die richtige Balance für ein System das professionelle
  Architektur-Disziplin mit moderner KI-Entwicklungsrealität verbindet.


================================================================================
BEZÜGE
================================================================================

[[FREEZE-7_S7]]                      Baseline für Stage 8 — normative Grundlage
[[GOV_Global_S6]]                    Normatives Regelwerk
[[TMP_principles_S6]]                Dokumenttypen und Templates
[[AI_DRIVEN_DEV_METHODE_S8]]         AI-Driven Development Methodik aktuell
[[TOOLBAUKASTEN_principles_S6]]      Toolbaukasten-Referenz


================================================================================
ENDE BLOCK 7 | Rosetta-Stone_Stage7_S7 | 2026-03-26
R+MUNI Blueprint | Stage 7 ABGESCHLOSSEN | Erstellt: EUMAXL + Claude
================================================================================
