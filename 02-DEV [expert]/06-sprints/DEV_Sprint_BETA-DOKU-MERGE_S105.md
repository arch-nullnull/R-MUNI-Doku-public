================================================================================
BETA-DOKU-MERGE — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_BETA-DOKU-MERGE_S105
Tag             : #dev #sprint #beta #merge #doku #s105
Datum           : 2026-04-14
Stage           : S1.05 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-14
Jira-Sync       : NEIN
================================================================================

---
title: "Beta-Doku-Merge S105"
stage: S1.05
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-14"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, beta, merge, doku, s105]
---

================================================================================
BETA-DOKU-MERGE — SPRINT (DEV)
Stage S1.05 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Die Beta-Kundendokumentation (Feedback, Feedbackschleifen, On- und Offboarding)
ist über mehrere Stages gewachsen und enthält veraltete Dokumente die im
Projektkontext irreführend wirken. Atlassian ist seit Stage 1.04 explizit
Addon — kein Default-Setup mehr. Außenwirkung für KI-Tool-Bezug wurde in
S104-Z1 aus öffentlichen Dokumenten entfernt.

Dieser Sprint bereinigt die Beta-Doku-Reihe: veraltete Dokumente werden
deprecated oder gelöscht, der aktuelle Stand wird als neue, saubere
Reihe etabliert. Der Sprint ist in Ziele (Z1–Z3) aufgeteilt, die
nacheinander in separaten Sessions abgearbeitet werden.

Hintergrund zur Aufteilung in Sessions:
  Die Dokumentenmenge (60+ Dokumente über mehrere Stages) ist zu groß
  um in einer Session vollständig und interpretationssicher zu bearbeiten.
  Bewusste Entscheidung: lieber mehrere saubere Sessions als eine
  fehlerhafte Gesamtlösung. Jede Session lädt den Sprint-Stand neu.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                  normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]       operative Arbeitsmethode
- [[FREEZE_1_04]]                          Ausgangszustand Stage 1.05
- [[STAGE105_ZIELE_S105]]                  Stage-Ziele — dauerhaft laufend: Beta/DEV-User
- [[HOW2_Feedbackschleifen_S8]]            aktive Feedbackschleifen-Referenz
- [[HOW2_S6-Z1_BetaFeedback_S6]]           veralteter Vorgänger — Löschkandidat
- [[BETA_ONBOARDING_Atlassian_Zugriffsmodell]]  Stage-4-Artefakt — Deprecated-Kandidat
- [[BETA_OFFBOARDING_principles_DEV_S101]] aktiv — behalten
- [[BETA_OFFBOARDING_How2_DEV_S101]]       aktiv — behalten
- [[TMP_principles_S105]]                  Dokumenttypen-Referenz
- [[TMP_How2_DEV_S105]]                    Dokumenterstellung How2

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Strukturbereinigung
Beschreibung: Beta-Doku-Reihe enthält veraltete Dokumente (Stage 4 / Stage 6
              Stand) die nicht als deprecated markiert sind und im aktiven
              Projektkontext irreführend wirken. Atlassian-Positionierung
              (jetzt Addon, nicht Default) ist in älteren Dokumenten nicht
              korrekt abgebildet.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         Beta-Doku-Reihe ist bereinigt — veraltete Dokumente entfernt
              oder deprecated, aktuelle Dokumente als neue Reihe etabliert,
              Atlassian-Addon-Stand korrekt abgebildet.

Abgrenzung:   Kein Eingriff in BETA_OFFBOARDING_principles/How2 (aktiv, korrekt).
              Kein Eingriff in GOV oder AI Driven (eigener Sprint S105-Z3).
              Kein Eingriff in Feedbackschleifen-Logik selbst —
              nur Dokumentenbereinigung.
              Keine Außenwirkung — rein interne DEV-Doku.


1.3 Ausgangslage
-----------------

Ist-Zustand:
  - HOW2_S6-Z1_BetaFeedback_S6: veraltet, durch S8-Nachfolger vollständig
    abgelöst, kein Deprecated-Vermerk
  - BETA_ONBOARDING_Atlassian_Zugriffsmodell: Stage-4-Stand, beschreibt
    Atlassian als Standard-Beta-Infrastruktur — widerspricht aktuellem
    Addon-Modell, kein Deprecated-Vermerk
  - HOW2_Feedbackschleifen_S8: aktiv, korrekt, ASC-validiert
  - BETA_OFFBOARDING_principles/How2_S101: aktiv, korrekt
  - Tier-Modell für neue Beta-Kunden (Minimal/Core/Addon): in Offboarding-
    Doku beschrieben, Onboarding-Pendant fehlt als eigenes aktuelles Dokument

Soll-Zustand:
  - HOW2_S6-Z1_BetaFeedback_S6: gelöscht
  - BETA_ONBOARDING_Atlassian_Zugriffsmodell: Deprecated-Vermerk gesetzt,
    als Stage-4-Artefakt markiert — kein aktiver Referenz-Status
  - Neues BETA_ONBOARDING-Dokument (Principles) mit aktuellem Addon-Stand
    erstellt — Tier-Logik korrekt abgebildet
  - Neues BETA_ONBOARDING-Dokument (How2) als Prozessanleitung erstellt
  - Alle aktiven Beta-Doku-Dokumente auf S105-Namenskonvention


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. SPRINT-ZIELE — AUFGETEILT NACH SESSIONS
================================================================================

Jedes Ziel wird in einer eigenen Chat-Session bearbeitet.
Zu Beginn jeder Session: dieses Sprint-Dokument + die für das Ziel
relevanten Dokumente in den Kontext laden.

EUMAXL bestätigt Abschluss eines Ziels im nächsten Chat mit:
  "Z<N> erfüllt — bitte Z<N+1> starten"

--------------------------------------------------------------------------------
Z1 — HOW2_S6-Z1_BetaFeedback_S6 DEPRECATED SETZEN
--------------------------------------------------------------------------------

Status: ERLEDIGT — 2026-04-14

Aufgabe:
  Dokument HOW2_S6-Z1_BetaFeedback_S6 mit Deprecated-Vermerk versehen.
  Als abgelöst durch HOW2_Feedbackschleifen_S8 kennzeichnen.
  Kein aktiver Referenz-Status mehr.

  Physische Löschung erfolgt NICHT im Sprint — wird manuell durch EUMAXL
  am Ende des Gesamt-Runs durchgeführt, nach Archivierung aller alten Stände.
  Grund: Schutz vor versehentlichem Verlust noch stimmiger Inhalte durch
  Updates die nicht optimal gelaufen sind (Learning aus Stage 1–1.04).

Begründung Deprecated (bereits in Prüfung erarbeitet):
  Vollständig durch HOW2_Feedbackschleifen_S8 abgelöst.
  Nachfolger explizit als Ablösung konzipiert (Vorgänger-Feld gesetzt).
  S8 ist ASC-validiert, S6 ist rein theoretisch.
  E-Mail als Kanal in S6 noch vorhanden — in S8 explizit gestrichen.

Artefakte:   HOW2_S6-Z1_BetaFeedback_S105.md (deprecated, von EUMAXL abgelegt)
GOV-Konform: JA — Strukturbereinigung (GOV 7.3)


--------------------------------------------------------------------------------
Z2 — BETA_ONBOARDING_Atlassian_Zugriffsmodell DEPRECATED SETZEN
--------------------------------------------------------------------------------

Status: ERLEDIGT — 2026-04-14

Aufgabe:
  Dokument BETA_ONBOARDING_Atlassian_Zugriffsmodell mit
  Deprecated-Vermerk versehen. Als Stage-4-Artefakt kennzeichnen.
  Kein aktiver Referenz-Status mehr.

Begründung:
  Dokument ist Stage-4-Stand (2026-03-09).
  Beschreibt Atlassian als Standard-Beta-Infrastruktur.
  Atlassian ist seit Stage 1.04 explizit Addon — kein Default.
  Tier-Modell (Minimal/Core/Addon) existierte bei Erstellung noch nicht.
  Dokument ist historisch wertvoll als Artefakt des ersten Beta-Setups —
  daher deprecated statt gelöscht.

Artefakte:   BETA_ONBOARDING_Atlassian_Zugriffsmodell_S105.md (deprecated, von EUMAXL abgelegt)
GOV-Konform: JA — Strukturbereinigung, Deprecated-Vermerk ist korrekte
             Behandlung historischer Artefakte


--------------------------------------------------------------------------------
Z3 — BETA_ONBOARDING NEUE REIHE ERSTELLEN
--------------------------------------------------------------------------------

Status: ERLEDIGT — 2026-04-14

Voraussetzung: Z2 abgeschlossen ✓

Artefakte:   BETA_ONBOARDING_principles_S105.md (neu erstellt, von EUMAXL abgelegt)
             BETA_ONBOARDING_How2_DEV_S105.md (neu erstellt, von EUMAXL abgelegt)
GOV-Konform: JA — neue Reihe gemäß TMP_How2_DEV_S105


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Split in drei Sessions statt einer Gesamtsession
  Auslöser:    Dokumentenmenge zu groß für interpretationssichere
               Bearbeitung in einer KI-Session (60+ Dokumente, mehrere Stages)
  Ergebnis:    Sprint wird in Z1/Z2/Z3 aufgeteilt, je eigene Session
  Begründung:  Lieber mehrere saubere Sessions als eine fehlerhafte
               Gesamtlösung. Entspricht AI Driven Kap. 16 (Drift-Prävention).
  GOV-Bezug:   GOV 7.7 — Zwischenschritte müssen nicht vollständig
               dokumentiert werden, Sprint-Ziel bleibt definiert
  Auswirkung:  EUMAXL bestätigt je Ziel-Abschluss explizit im Chat
  Rückwirkung: NEIN

Entscheidung: HOW2_S6-Z1_BetaFeedback_S6 deprecated setzen — Löschung manuell später
  Auslöser:    Vollständige inhaltliche Abdeckung durch S8-Nachfolger.
               Physische Löschung bewusst aus Sprint herausgehalten.
  Ergebnis:    Deprecated-Vermerk im Sprint, manuelle Löschung durch EUMAXL
               am Ende des Gesamt-Runs nach Archivierung.
  Begründung:  Learning aus Stage 1–1.04: keine physische Löschung während
               aktiver Runs — Schutz vor Verlust noch stimmiger Stände bei
               nicht optimal gelaufenen Updates.
  GOV-Bezug:   GOV 7.3 Strukturbereinigung
  Auswirkung:  Dokument bleibt physisch vorhanden bis EUMAXL manuell löscht
  Rückwirkung: NEIN

Entscheidung: BETA_ONBOARDING_Atlassian_Zugriffsmodell deprecated statt gelöscht
  Auslöser:    Erstes Beta-Kunden-Setup-Artefakt — historischer Kontext
               relevant für Betreiber-Erinnerung und LL-Nachvollziehbarkeit
  Ergebnis:    Deprecated-Vermerk, kein aktiver Referenz-Status
  Begründung:  Historischer Wert vorhanden, kein Informationsverlust-Risiko
               durch Behalten wenn klar als veraltet markiert
  GOV-Bezug:   GOV 7.3 Strukturbereinigung
  Auswirkung:  Neues Onboarding-Dokument (Z3) übernimmt aktive Rolle
  Rückwirkung: NEIN

Entscheidung: Atlassian-Addon-Stand in neuen Dokumenten korrekt abbilden
  Auslöser:    FREEZE_1_04 Kap. 1: Atlassian explizit als optionales
               Kundenfrontend — Tier-Modell Minimal/Core/Addon
  Ergebnis:    Neue Onboarding-Dokumente bilden Addon-Stand ab
  Begründung:  Kein Lügen, keine Außenwirkung, interne Wahrheit dokumentieren
  GOV-Bezug:   GOV 1.4 — implizite Entscheidungen unzulässig
  Auswirkung:  Neue Beta-Kunden werden nach aktuellem Modell ongeboardet
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Sprint-Dokumentation vor Sprint-Ausführung erstellt
  GOV-Regel:   GOV 7.8 — Dev-Dokumentation während des Sprints
  Begründung:  Sprint ist explizit als session-übergreifender Koordinations-
               rahmen angelegt. Vorab-Doku ist hier nicht Abweichung sondern
               Voraussetzung für saubere Session-Übergaben.
  Wirkung:     Auf diesen Sprint begrenzt — kein Präzedenzfall


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis (Prüfungs-Session): Kontextlücke erkannt —
  aktuelle S105-Principles und Tier-Modell-Stand nicht vollständig geladen.
  Ehrlich kommuniziert statt Interpretation. Aufteilung in Sessions
  aktiv empfohlen.

⚠ Verhaltenshinweis (Z1-Session): Pflicht-Kontext nicht vollständig geladen
  vor Ausführung — STAGE105_ZIELE, PROMPT_pfad_pruefung, structure-Dateien,
  GOV und AI Driven fehlten. Drei Anläufe für Z1 notwendig.
  Ursache: Snippet-basiertes Laden aus Project Knowledge — naming_and_structure
  nicht vollständig verarbeitet → Dateinamen-Suffix _S105 beim ersten Anlauf
  nicht korrekt gesetzt. EUMAXL hat Z1 manuell als HOW2_S6-Z1_BetaFeedback_S105
  abgelegt. Cleaning Run durch EUMAXL erforderlich.

⚠ Verhaltenshinweis (Z1-Session): Stage-Feld im Header wurde als "S6 — HISTORISCH"
  gesetzt statt "S1.05 — AKTIV". Stage-Feld zeigt immer die aktuelle Arbeits-Stage,
  nicht die Herkunfts-Stage des Inhalts. Fehler durch EUMAXL korrigiert.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| Z1 HOW2_S6 deprecated setzen | GOV 7.3 | ERLEDIGT | — |
| Z2 Atlassian deprecated setzen | GOV 7.3 | ERLEDIGT | — |
| Z3 Neue Onboarding-Reihe erstellen | GOV 7.6 | ERLEDIGT | — |
| HOW2_S6-Z1_BetaFeedback physisch löschen | GOV 7.3 | offen | EUMAXL manuell nach Archivierung |
| GitHub-Sync alle neuen Artefakte | GOV 7.9 | offen | EUMAXL |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — durch EUMAXL
  — HOW2_S6-Z1_BetaFeedback_S105.md            deprecated, abgelegt EUMAXL
  — BETA_ONBOARDING_Atlassian_Zugriffsmodell_S105.md  deprecated, abgelegt EUMAXL
  — BETA_ONBOARDING_principles_S105.md          01-principles\
  — BETA_ONBOARDING_How2_DEV_S105.md            02-how2\
GitHub-Sync:                      AUSSTEHEND — EUMAXL
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Merge-Prüfung vor Sprint — klare Entscheidungsgrundlage für Z1/Z2/Z3
  - Ehrliche Kontextlücken-Kommunikation statt stiller Interpretation
  - Session-Splitting als bewusste Methodik statt erzwungener Vollständigkeit
  - Z2 und Z3 sauber in einem Anlauf — vollständiges Dokumentlesen vor Ausführung
    hat sich bewährt (Dokument als Ganzes via Project Knowledge geladen)

Was beim nächsten Mal anders gemacht werden sollte:
  - STAGE_ZIELE + PROMPT_pfad_pruefung + structure-Dateien + GOV + AI Driven
    als Pflicht-Kontext zu Sessionbeginn — nicht erst auf Nachfrage
  - Bei Dateinamen-Konventionen: naming_and_structure als Attachment hochladen
    statt auf Snippet-Basis zu vertrauen — Snippet war unvollständig
  - Stage-Feld Bedeutung: zeigt immer aktuelle Arbeits-Stage, nie Herkunfts-Stage

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Merge-Prüfung als eigener Prozessschritt vor Dokumenten-Neuanlage
    → kein eigener Sprint nötig, Hinweis für AI Driven Update S105 (Z3)
  - Snippet-Limitation bei naming_and_structure ist bekanntes Risiko —
    Empfehlung: kritische Konventionsdokumente als Attachment in Session laden

---

## Bezüge

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[FREEZE_1_04]]                            Ausgangszustand
[[STAGE105_ZIELE_S105]]                    Stage-Kontext
[[HOW2_Feedbackschleifen_S8]]              aktive Feedbackreferenz
[[BETA_OFFBOARDING_principles_DEV_S101]]   Strukturreferenz für Z3
[[BETA_OFFBOARDING_How2_DEV_S101]]         Strukturreferenz für Z3
[[BETA_ONBOARDING_principles_S105]]        neu erstellt Z3
[[BETA_ONBOARDING_How2_DEV_S105]]          neu erstellt Z3
[[TMP_How2_DEV_S105]]                      Dokumenttypen How2

---

================================================================================
BETA-DOKU-MERGE — SPRINT (DEV) | S105 | 2026-04-14 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================
