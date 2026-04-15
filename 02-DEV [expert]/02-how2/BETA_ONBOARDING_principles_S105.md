================================================================================
BETA_ONBOARDING — PRINCIPLES (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : BETA_ONBOARDING_principles_S105
Tag             : #dev #principles #beta #onboarding #s105
Datum           : 2026-04-14
Stage           : S1.05 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-04-14
Letzte Änderung : 2026-04-14 — Erstellt | DEV_Sprint_BETA-DOKU-MERGE_S105 Z3
Ablageort       : 01-principles\BETA_ONBOARDING_principles_S105.md
================================================================================


1. ZWECK UND DESIGNPHILOSOPHIE
--------------------------------------------------------------------------------
Dieses Dokument beschreibt die Leitprinzipien für das strukturierte Onboarding
von Beta-Kunden in den R+MUNI Beta-Betrieb.

Onboarding ist kein einmaliges Event — es ist die Grundlage des gesamten
Beta-Lebenszyklus. Was hier eingerichtet und dokumentiert wird bestimmt
wie sauber der Betrieb läuft und wie reibungslos das Offboarding später
durchgeführt werden kann.

Dieses Dokument ersetzt [[BETA_ONBOARDING_Atlassian_Zugriffsmodell]] als
aktive Onboarding-Referenz. Atlassian ist ab Stage 1.04 explizit Addon —
kein Default-Setup. Das Tier-Modell (Minimal/Core/Addon) ist die
verbindliche Grundlage für jede Onboarding-Entscheidung.

Erstanwendung: ab Stage 1.05 — für alle neuen Beta-Kunden verbindlich.


2. GRUNDSÄTZE
--------------------------------------------------------------------------------

2.1 Tier vor Werkzeug
----------------------
Die Tier-Entscheidung (Minimal / Core / Addon) wird getroffen bevor
irgendein Werkzeug eingerichtet wird. Kein implizites Standard-Setup.
Kein Atlassian ohne explizite Addon-Entscheidung.

  Tier bestimmt Umfang — Umfang bestimmt Werkzeuge.
  Werkzeuge folgen — sie führen nicht.

2.2 Vollständige Dokumentation ist Pflicht
-------------------------------------------
Jedes Onboarding erzeugt eine Onboarding-Checkliste die vollständig
ausgefüllt wird. Diese Checkliste ist die Grundlage für den späteren
Offboarding-Prozess — ohne vollständige Onboarding-Doku ist sauberes
Offboarding nicht möglich.

  Onboarding ohne Checkliste    =  unvollständiges Onboarding
  Vollständige Checkliste       =  Voraussetzung für GOV-Konformität

2.3 Exitpoint-Gedanke — Kompetenz statt Abhängigkeit
------------------------------------------------------
R+MUNI richtet keine Abhängigkeiten ein — es baut Kompetenz auf.
Der Beta-Kunde soll nach dem Onboarding handlungsfähig sein,
nicht von R+MUNI-Zugängen abhängig.

  Lokal installierte Tools    →  bleiben beim Kunden
  Kundenseitige Artefakte     →  bleiben beim Kunden
  R+MUNI-seitige Zugänge      →  werden beim Offboarding sauber deaktiviert

2.4 Atlassian ist Addon — kein Default
----------------------------------------
Atlassian (Jira + Confluence + JSM) wird ausschließlich beim Addon-Tier
eingerichtet. Kein Beta-Kunde erhält automatisch Atlassian-Zugang.

  MINIMAL    →  kein Atlassian
  CORE       →  kein Atlassian
  ADDON      →  Atlassian optional — nur wenn explizit vereinbart

Begründung: IST-Situation des Kunden bestimmt ob Atlassian sinnvoll ist.
Referenz: [[BETA_ONBOARDING_Atlassian_Zugriffsmodell_S105]] (deprecated, Stage-4-Artefakt)

2.5 Kommunikation startet strukturiert
----------------------------------------
Jedes Onboarding beginnt mit einer definierten Kommunikation.
Kein stilles Einrichten ohne expliziten Kommunikationsstart.

  Kommunikationsweg:
    Erstkontakt / persönliches Gespräch → Onboarding-E-Mail → Zugangsdaten

  Dieser Weg ist verpflichtend — er bildet auch die Grundlage für
  die spätere Beurteilung ob ein stiller interner Abschluss beim
  Offboarding GOV-konform ist.

2.6 Onboarding ist ein wiederholbares Blueprint-Artefakt
---------------------------------------------------------
Das Onboarding wird nicht nur durchgeführt — es wird als
reproduzierbares Artefakt dokumentiert. Jeder folgende Beta-Kunde
soll anhand dieser Principles und der How2 ongeboardet werden können —
ohne individuelle Anpassung, ohne mündliche Übergabe.


3. TIER-MODELL
--------------------------------------------------------------------------------

3.1 Übersicht
--------------

  MINIMAL
    Umfang:    Lokale Installation + Basis-Dokumentation
    R+MUNI:    Kein aktiver Zugang von R+MUNI-Seite eingerichtet
    Atlassian: NEIN
    GitHub:    Lesezugang Public Repo — kein Schreibzugang
    Einsatz:   Für Kunden die eigenständig starten — minimale Begleitung

  CORE
    Umfang:    Minimal + GitHub Sync / Kollaborations-Zugänge
    R+MUNI:    GitHub Sync eingerichtet wenn vereinbart
    Atlassian: NEIN
    GitHub:    Lesezugang + ggf. Issues oder Discussions
    Einsatz:   Für Kunden mit aktivem Austausch — ohne Atlassian-Overhead

  ADDON
    Umfang:    Core + optionale Addon-Komponenten (z.B. Atlassian)
    R+MUNI:    Alle vereinbarten Addon-Zugänge eingerichtet
    Atlassian: NUR wenn explizit vereinbart — gemäß Zugriffsmodell Stage 4
    GitHub:    Vollständig nach Vereinbarung
    Einsatz:   Für Kunden mit komplexem Setup und aktiver Kollaboration

3.2 Tier-Entscheidung
----------------------
Die Tier-Entscheidung trifft EUMAXL gemeinsam mit dem Beta-Kunden
vor dem ersten Einrichten. Sie wird in der Onboarding-Checkliste
dokumentiert und ist Basis für den gesamten Beta-Lebenszyklus.

  Kein Tier-Wechsel ohne explizite Entscheidung + Dokumentation.
  Kein Tier-Upgrade implizit durch Nutzungsverhalten.


4. SCOPE DES ONBOARDINGS
--------------------------------------------------------------------------------

Was Onboarding umfasst:
  - Tier-Entscheidung treffen und dokumentieren
  - Vereinbarte Tier-Komponenten einrichten
  - Kommunikationsstart durchführen (Erstkontakt → E-Mail → Zugangsdaten)
  - Onboarding-Checkliste vollständig ausfüllen
  - Beta-Status intern auf AKTIV setzen

Was Onboarding explizit nicht umfasst:
  - Eingriff in DEV-Umgebung oder Blueprint-Logik
  - Einrichten von Werkzeugen die nicht zum gewählten Tier gehören
  - Atlassian ohne explizite Addon-Entscheidung
  - Zusagen zur Umsetzung von Feature-Wünschen
  - Änderung von GOV-Regeln oder Stage-Zielen


5. ZUSAMMENHANG MIT OFFBOARDING
--------------------------------------------------------------------------------
Onboarding und Offboarding sind gegenläufige Prozesse desselben
Beta-Kunden-Lebenszyklus.

  ONBOARDING    →  Zugänge einrichten, Tier festlegen, Kommunikation starten
  BETA-BETRIEB  →  Nutzung, Feedback, Iterationen
  OFFBOARDING   →  R+MUNI-Zugänge deaktivieren, Status dokumentieren, Lernen

Die Onboarding-Dokumentation ist die Grundlage für das Offboarding —
sie enthält was eingerichtet wurde und muss daher vollständig sein.

Bezug: [[BETA_OFFBOARDING_principles_DEV_S101]]


6. GOVERNANCE-BEZÜGE
--------------------------------------------------------------------------------
GOV 1.4    Implizite Entscheidungen unzulässig — Tier explizit dokumentieren
GOV 7.3    Onboarding als definierter Prozessschritt mit Auslöser
GOV 7.6    Ziel explizit: Beta-Kunde vollständig und dokumentiert onboarden
GOV 7.8    Dev-Doku verpflichtend — Onboarding-Checkliste ist Pflichtartefakt
Rückkopplungsschutz: Onboarding berührt keine Blueprint-Logik, keine Scripts


================================================================================
BEZÜGE
================================================================================
[[Global_GOV_DEV_S102]]                              normative Grundlage
[[BETA_OFFBOARDING_principles_DEV_S101]]             Offboarding-Gegenstück
[[BETA_ONBOARDING_How2_DEV_S105]]                    operative Anleitung
[[BETA_ONBOARDING_Atlassian_Zugriffsmodell_S105]]    deprecated — Stage-4-Artefakt
[[FREEZE_1_04]]                                      Atlassian-Addon-Nachweis
[[STAGE105_ZIELE_S105]]                              Stage-Kontext


================================================================================
BETA_ONBOARDING_principles_DEV | S1.05 | 2026-04-14 | R+MUNI Blueprint
================================================================================
