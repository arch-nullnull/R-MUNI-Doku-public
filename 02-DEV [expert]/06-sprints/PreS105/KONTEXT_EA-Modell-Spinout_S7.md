================================================================================
KONTEXT-NOTIZ — EA Modell Spin-out
================================================================================
Projekt         : R+MUNI Blueprint — EA Modell Spin-out
Dokument        : KONTEXT_EA-Modell-Spinout_S7
Datum           : 2026-03-26
Stage           : S7 – AKTIV
Erstellt durch  : EUMAXL + Claude (Pair-Session)
Zweck           : Orientierungsnotiz für neue Claude-Session im Spin-out Projekt
================================================================================


================================================================================
1. WAS DIESES DOKUMENT IST
================================================================================

Diese Notiz ist der destillierte Kontext aus der EA Modell Review Session
vom 2026-03-26. Sie ermöglicht einer neuen Claude-Session den sofortigen
Einstieg ohne die gesamte Vorgeschichte rekonstruieren zu müssen.

Geladene Dokumente im neuen Projekt:
  - GOV_Global          normative Grundlage
  - Install.txt         Setup-Referenz
  - README.md           Projektübersicht
  - MUNI EA.xml         das aktuelle EA Modell (OEF Export)


================================================================================
2. DAS MODELL-SYSTEM — KERN-KONZEPT
================================================================================

R+MUNI verwendet ein dreistufiges Modell-System:

  EA MUNI Core (Meta Modell)
    → Alle gewarteten Elemente auf Core-Abstraktionslevel
    → Vollständig — nicht schlank/unvollständig
    → Single Source of Truth
    → Ein Viewpoint pro Layer — bewusste Designentscheidung

  Sub-Modell Typ A (temporär)
    → Gezielte Frage beantworten
    → Rückkopplung ins Core → Archiv
    → Work View in Archi = Typ-A direkt im Modell

  Sub-Modell Typ B (gelebt)
    → Dauerhaft gewartet
    → Einbindbar in Flows
    → Rückkopplung ins Core wenn relevant

Entspricht TOGAF Architecture Landscape:
  Foundation Architecture = EA MUNI Core
  Segment Architectures   = Typ-B Sub-Modelle
  Solution Architectures  = Typ-A Sub-Modelle


================================================================================
3. MODELL-PHILOSOPHIE DES BETREIBERS
================================================================================

3.1 Einstiegspunkt
  Betreiber startet immer vom Motivation Layer — nicht von Business.
  Driver → Assessment → Goal → Requirement ist die normkonforme Richtung.
  Für KMU-Kontext ungewöhnlich aber bewusst und korrekt.

3.2 Abstraktionslevel
  Betreiber bleibt bewusst auf einem Abstraktionslevel pro Layer.
  Cross-Layer Tracing wird eingesetzt aber sparsam.
  Lesbarkeit hat Vorrang vor vollständiger Normabbildung.
  Betreiber-Wissen trägt den Rest — das ist eine bewusste Entscheidung.

3.3 Lernart
  Fühlen → Verstehen → Begriff
  Nicht: Begriff auswendig lernen → dann anwenden
  Konsequenz: ArchiMate-Normen die gegen die Intuition gehen
  müssen explizit gelernt werden — nicht nur logisch abgeleitet.

3.4 Lautes Denken
  Betreiber denkt laut — das ist KEIN Korrekturwunsch.
  Claude wartet auf explizites Signal bevor er zurückrudert.
  Signal: "das stört mich" oder "geh zurück"

3.5 Reduktion vs. Vollständigkeit
  Innerer Monk will alles vollständig.
  Lösung: Viewpoint bestimmt was rein kommt — nicht der Monk.
  Testkriterium: Außenstehender versteht ohne Erklärung.

3.6 Grouping
  Betreiber verwendet Specialization statt Grouping für Hierarchien.
  Grouping = mähh weil keine semantische Aussage.
  Specialization = normkonform · semantisch korrekt · hübscher.

3.7 Naming
  Denglish = bewusste und konsistente Entscheidung
  Properties  → CamelCase (AccessLevel · 3PartyID)
  Files       → ABC00-ich_bin_der_name_S7 (Snake_Case + Präfix + Stage)
  Werte       → GROSSBUCHSTABEN wenn kontrolliertes Vokabular


================================================================================
4. ZWEI-WELTEN-ENTSCHEID (ab Stage 7 gültig)
================================================================================

R+MUNI trennt konsequent zwei Welten:

  INTERN — DEV Welt
    Blueprint · GOV · Principles · Sprints · How2
    Nur auf Freigabe · Für DEV · Für EUMAXL

  PUBLIC — MGT Welt
    Was rausgeht · Außenwirkung · Kartensprache
    Erste Runde spielbar · Ergebnis ohne DEV-Begleitung

Keine Vermischung. Keine Ausnahmen.
Strukturelle Umsetzung in GOV/Templates: MUNIEA-148 (Backlog)

Property AccessLevel auf jedem Stakeholder-Element:
  INTERN · PUBLIC · GRENZBEREICH


================================================================================
5. MOTIVATION LAYER — AKTUELLER STAND
================================================================================

View-Name: VIE00-Motivation — Stakeholder Viewpoint
Viewpoint: Stakeholder Viewpoint (ArchiMate normkonform)
Status: Durchgedacht · noch nicht in Archi gebaut

5.1 Stakeholder — vollständige Liste

STA00 — Me ;) [AccessLevel: INTERN]
  Driver A:   Geiler Job — IT Erfahrung sinnvoll einsetzen
  Driver B:   Wissbegierde — bauen und verstehen
  Driver C:   Beweis dass es geht
  Goal:       R+MUNI Release 1.0
  Principles: PRI00–04 via Association
  Property:   Lernart "Fühlen → Verstehen → Begriff"

STA01 — Expert [AccessLevel: PUBLIC]
  Ehemals: ZG1 TOGAF/ArchiMate
  Driver:   Maschinenlesbarkeit — kein Medienbruch · kein Clone
  Goal:     Normkonformes Modell als Übergabeartefakt (BOC/Adoit)
  Kontext:  BPMN 2.0 als primäre Sprache · ArchiMate als Brücke

STA02 — Associate [AccessLevel: PUBLIC]
  Ehemals: ZG2 KMU Core — Kernzielgruppe
  Driver:   Komplexität fühlen ohne Sprache dafür
  Goal:     Gemeinsames Bild der Organisation — Klarheit sehen

STA03 — Special [AccessLevel: PUBLIC]
  Ehemals: ZG3 FUN
  Driver:   Adoption-Hürde — zu trocken · kein Einstieg
  Goal:     Spielerischer Einstieg — MTG/UNO · Lust auf mehr
  Kontext:  Unter 60 Min · sichtbares Ergebnis · kein DEV nötig

STA04 — Vertrieb [AccessLevel: GRENZBEREICH]
  Driver:   Marktvalidierung · Einkommensaufbau Teilzeit
  Goal:     Trainingsbetrieb — 2–3 Kunden/Jahr
  Kontext:  Türöffner extern · übergibt bei inhaltlicher Tiefe
            Betreiber kommt wenn Normkonformität gefragt ist

STA05 — DEV extern [AccessLevel: GRENZBEREICH]
  Driver:   Freies Wissen · Open Source Philosophie
  Goal:     Mitgestalten · Beitrag leisten · lernen
  Kontext:  3 Subtypen im Kopf — technisch · philosophisch · lernend
            Im Core nur ein Driver — Rest im Sub-Modell bei Bedarf

STA06 — Viewer [AccessLevel: PUBLIC]
  Driver:   Kollegiale Hilfsbereitschaft
  Goal:     Orientierung geben ohne Commitment
  Property: Vertraute Distanz → in Dokumentation · nicht als Driver
  Kontext:  Bekannte · Ex-Kollegen · steuerbar durch Betreiber-Trigger

5.2 Bestehende Elemente — bleiben unverändert
  DRV00–02 · GOA00 · ASS00 · MEA00–02 · REQ00–05 · PRI00–04
  OUT00 · VAL00

5.3 Offene Punkte Motivation Layer
  Requirements aus Stakeholder-Goals noch nicht abgeleitet
  Principle → Requirement Verbindung via Influence (nicht Realization)
  Neue externe Requirements noch nicht definiert


================================================================================
6. META MODELL BAUPLAN — ALLE LAYER
================================================================================

Struktur: Ein Viewpoint pro Layer · Core-Abstraktionslevel

  VIE00  Motivation Layer    Stakeholder Viewpoint
                              STA · DRV · GOA · PRI · REQ · ASS · MEA

  VIE01  Strategy Layer      Strategy Viewpoint
                              CAP00–03 · VAS00–05 · COA00 · RES00–01

  VIE02  Business Layer      Business Function Viewpoint
                              BUA · BUR · BUP00–07 · BUS00–04
                              PRO00 · BUO · BUI · BUF

  VIE03  Application Layer   Application Viewpoint
                              APC (Archi·Camunda·FLOW·Notepad++·Chrome)
                              APF-Reihe · API-Reihe · DAO-Reihe

  VIE04  Technology Layer    Technology Viewpoint
                              DEV00 · SYS00–02 · TEF00–01
                              CON00 · NOD00 · MAT00–03

  VIE05  Implementation      Verweise auf BPMN 2.0 Sub-Modelle
         (bewusst leer)       Tiefe lebt in BPMN · nur Verweis im Core

  WRK00  Scratch View        Kein Deliverable · Typ-A Spin-out
                              Archi führt automatisch in Baum zurück


================================================================================
7. BEKANNTE MODELL-EIGENHEITEN UND ENTSCHEIDUNGEN
================================================================================

Product (PRO00)
  Steht auf Business Layer — bewusst
  ApplicationCollaboration (ACO00) auf Application Layer — bewusst
  Cross-Layer Tracing via Realization möglich aber nicht im Core
  Betreiber hadert mit Product-Begriff — ist aber normkonform

TEF00-Ordnerstruktur
  Selbst als "nicht EA konform" dokumentiert — bleibt als Pragmatismus
  Kandidat für Bereinigung in späterem Run

Views im IST-Modell
  VIE07-Tracing Other Views → kein eigener Viewpoint · wird aufgelöst
  Work View → wird zu WRK00-Scratch · kein Deliverable
  Gemischte Views waren bekannte Unsauberkeit — wird bereinigt

Archi Tool-Eigenheit
  View-zentriert · Baum ist sekundär
  Work View = bewusster Scratch-Bereich · Archi synct automatisch
  Bekanntes Problem: Elemente im View updaten erst nach Reimport


================================================================================
8. PRÜFUNGS-KONTEXT (Außenwirkung — nicht primäres Ziel)
================================================================================

Geplanter Pfad:
  ArchiMate 3 Foundation → ArchiMate 3 Practitioner
  TOGAF Foundation → TOGAF Practitioner
  BPMN 2.0 Prüfung

Bestehende Diplome (BFI Wien):
  Projekt- und Prozessmanagement    2023 · mit gutem Erfolg
  Leadership und Change Management  2024 · mit Erfolg

Praxis:
  2x ISO-Implementierung · einmal solo · einmal Matrix-Gruppe
  25+ Jahre IT · Presales · PM · Prozess- und Changemanagement

Wichtig für Claude:
  Prüfungsrelevanz nur kurz erwähnen wenn direkt relevant
  Kein roter Faden — Fokus bleibt auf R+MUNI und dem Modell
  Ergebnisse sprechen für sich — nicht das Zertifikat


================================================================================
9. OFFENE BACKLOG-PUNKTE AUS DIESER SESSION
================================================================================

MUNIEA-149  GOV Naming Konventionen — S8
            CamelCase Properties · Snake_Case Files · Denglish
            Status: Backlog · nicht gestartet

MUNIEA-148  Zwei-Welten strukturelle Umsetzung — post S7
            GOV · Templates · Dokumentenreihen
            Status: Backlog · zurückgestellt

Offen ohne Ticket:
  Requirements aus neuen Stakeholder-Goals ableiten
  Principle → Requirement via Influence verbinden
  VIE07 und Work View bereinigen
  TEF00 Ordnerstruktur evaluieren


================================================================================
10. CLAUDE-VERHALTEN IN DIESEM KONTEXT
================================================================================

Rollenverteilung:
  Betreiber  →  baut · entscheidet · denkt laut
  Claude     →  Sparring · Norm-Korrektheit · Review

Was Claude tut:
  Korrigiert wenn ArchiMate-Norm verletzt wird — mit Begründung
  Wartet auf explizites Signal bevor er Kurs ändert
  Fragt nach Ziel von SVGs bevor er sie zeichnet (Chat vs. Einbau)
  Erklärt neue ArchiMate-Begriffe kurz beim ersten Auftreten
  Meldet aktiv wenn er Verhaltensveränderungen wahrnimmt

Was Claude nicht tut:
  Lautes Denken als Korrekturwunsch interpretieren
  Prüfungsthemen als roten Faden verwenden
  Voraus-templateen ohne Raum zu lassen
  Atlassian als Default-Setup annehmen (ist ADDON)


================================================================================
KONTEXT_EA-Modell-Spinout | S7 | 2026-03-26 | R+MUNI Blueprint
================================================================================
