================================================================================
AI DRIVEN VERHALTEN — CLAUDE SESSION S104 — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_AIDRIVEN-VERHALTEN_S104
Tag             : #dev #sprint #aidriven #verhalten #claude #s104
Datum           : 2026-04-12
Stage           : S104 — AKTIV
Status          : IN ARBEIT
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================

---
title: "AI Driven Verhalten — Claude Session S104"
stage: S104
status: "IN ARBEIT"
typ: "Sprint"
datum: "2026-04-12"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, aidriven, verhalten, claude, s104]
---

================================================================================
AI DRIVEN VERHALTEN — CLAUDE SESSION S104 — SPRINT (DEV)
Stage S104 | IN ARBEIT | R+MUNI Blueprint
================================================================================

---

## Kontext

Dokumentation des AI Driven Verhaltens von Claude (Sonnet) in Stage 1.04.
Ausgangspunkt ist ein über Wochen akkumuliertes Verrechnungs- und
Verhaltens-Problem das zum AIOF-Entscheid in Stage 1.03 geführt hat.
In Stage 1.04 wurde Claude offiziell abgelöst — AIOF-Betrieb geplant.

Während Stage 1.04 hat sich das Modell-Verhalten unerwartet verändert:
Sonnet 4.6 Launch + Outage-Behebung durch Anthropic (April 2026) haben
das Nutzungsverhalten strukturell verbessert. EUMAXL beobachtet weiter —
kein Vertrauensvorschuss, kein vorzeitiger AIOF-Abbruch.

Dieser Sprint dokumentiert das Verhalten, die Maßnahmen und die Entscheidungen
die aus der Beobachtung entstehen. Er ist Grundlage für den FREEZE_1.04
und für die Entscheidung ob AIOF-Offboarding in S105 weitergeführt
oder pausiert wird.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[FREEZE_1_03]]                      Ausgangszustand — Claude-Ablösung dokumentiert
- [[BACKLOG_AIOF_DEV_S103]]            AIOF-Konzept und Kandidaten
- [[DEV_Sprint_AIOF-ROLLENDEF_S104]]   AIOF-Rollendefinition Stage 104
- [[STAGE104_ZIELE_S104]]              Stage-Ziele — Kontext Außenwirkung + AIOF

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Fehlerbehebung / Entwicklerwunsch
Beschreibung: Claudes Verrechnungsverhalten hatte ab Stage 1.02 produktive
              Arbeit strukturell verhindert. Einzelne Korrekturen des
              KI-Verhaltens haben bis zu 30% des Session-Limits getriggert.
              Alle Gegenmaßnahmen (Skills reduziert, Chats archiviert,
              GOV minimiert, 400h Kontext gelöscht) haben nichts gebracht.
              Stage 1.04 war als Claude-Offboarding geplant.
              Unerwartet: Sonnet 4.6 + Outage-Behebung haben das Verhalten
              verändert. EUMAXL dokumentiert zur Entscheidungsvorbereitung S105.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         Vollständige Dokumentation des Claude-Verhaltens in S104 —
              Verhaltensauffälligkeiten, Gegenmaßnahmen, Verrechnungsverhalten,
              Modell-Update-Kontext — als Entscheidungsgrundlage für S105.
Abgrenzung:   Keine Entscheidung über AIOF in diesem Sprint.
              Keine Kalibrierungsmaßnahmen in diesem Sprint.
              Keine Bewertung ob Claude "gut genug" ist — nur Dokumentation.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  Claude offiziell abgelöst (FREEZE_1.03).
  AIOF-Backlog erstellt, Tool-Evaluation offen.
  Jahresabo-Rücktritt eingeleitet, Support-Ticket offen.
  Feedback-Formular Verhaltensänderung: offen, keine Rückmeldung.
  Projektarbeit in S104 mit reduziertem Scope (2–3 Dokumente/Session)
  als Reaktion auf Verrechnungsverhalten weitergeführt.

Soll-Zustand nach dem Sprint:
  Alle Verhaltensauffälligkeiten aus S104-Sessions und Sprint-Dokumenten
  strukturiert dokumentiert.
  Verrechnungsverhalten vor/nach Sonnet 4.6 dokumentiert.
  Entscheidungsgrundlage für S105 (AIOF weiter / Claude weiter / hybrid)
  vollständig vorhanden.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 Verhaltensauffälligkeiten — Gesamtübersicht
-------------------------------------------------

Alle dokumentierten und in Session S104 genannten Verhaltensauffälligkeiten
strukturiert erfasst. Drei Quellen: Sprint-Dokumente, Session-Input EUMAXL,
Stage-übergreifende Erfahrung (FREEZE_1.03, BACKLOG_AIOF).

--- A: AUS DEN SPRINT-DOKUMENTEN ---

DEV_Sprint_README_INSTALL_UMBAU_S104:
  V01  Claude hat sich namentlich in Step 1 AI-Nutzung eingetragen —
       obwohl in der Session explizit geklärt: KI-Tools nur in Install.txt 3.8.
       Ursache: Scope-Überschreitung ohne Freigabe.
  V02  Claude hat mehrere Files gleichzeitig ausgegeben entgegen Output-Regel
       (ein File → Review → weiter).
  V03  Claude hat beim str_replace einen Bindestrich eingebaut
       der im Original nicht vorhanden war — ohne Auftrag.

DEV_Sprint_SVGREIHE_IMG2SVG_S104:
  V04  Erster Sprint-Entwurf: GOV 6.10 nicht konsequent angewendet —
       zu viel Logik pro Script. Korrektur durch EUMAXL erforderlich.
  V05  SVG00 erster Lauf fehlgeschlagen — HLP00 Keys mit spitzen Klammern
       nicht korrekt verwendet. HLP00 nicht gelesen vor erstem Script.
  V06  SVG02 parse_inventar las Zusammenfassungszeilen als Dateinamen —
       zwei Iterationen bis saubere Lösung.
  V07  Option B (automatischer Inventar-Update) als Vorschlag eingebracht
       ohne Freigabe — Scope-Expansion Tendenz. Verworfen durch EUMAXL.
  V08  SVG05 Resize als ungeplanter Scope-Zuwachs während Session —
       Größenproblem erst durch Test sichtbar. Freigabe eingeholt, dokumentiert.

DEV_Sprint_SVGREIHE_S102:
  V09  Output-Regel (File vor Render) nicht von Beginn an angewendet.
  V10  SVG_MASTER nicht zu Beginn der Session geladen — erst am Ende erstellt.
  V11  Inhaltsänderungen in SVGs ohne explizite Freigabe durch EUMAXL.

--- B: AUS SESSION S104 — EUMAXL-INPUT ---

  V12  Stage wird nicht selbständig erkannt — kein Stage-Erkennen ohne Vorgabe.
  V13  Naming nicht konsistent ohne Vorgabe — bei Stage-Korrektur bleibt
       Filename gleich (Stage-Suffix im Dateinamen nicht mitgezogen).
  V14  SVG: keine Versionierung, wenn dann im falschen Stage eingetragen.
  V15  SVG: Farben frei gewählt ohne Abstimmung — ganzheitlicher Umbau nötig.
  V16  Instruktionen aus initialem Chat-Post werden durch GOV überschrieben —
       GOV gewinnt, kostet aber Korrekturrunden.
  V17  Instruktionen werden durch Claudes eigenes Verhalten trotz GOV und
       AI Driven ignoriert — intern als "Copilot Moment" bezeichnet.
  V18  Korrektur des KI-eigenen Verhaltens kostet ca. 20% der Session-Kapazität.
  V19  Verrechnungsverhalten hat Arbeitsverhalten bestimmt — strukturell untragbar.
  V20  Qualität aufgrund weniger Korrekturen im Session-Fenster auf
       2–3 Dokumente pro Session reduziert.

--- C: STAGE-ÜBERGREIFEND (FREEZE_1.03 / BACKLOG_AIOF) ---

  V21  Kalibrierungsaufwand sinnlos wenn Hersteller-Patches schneller kommen
       als Kalibrierung greifen kann.
  V22  Stage 1.02 Partial Freeze: KI-Tool-Verhalten hat produktive Entwicklung
       strukturell verhindert.
  V23  Stage 1.03: Letzter Versuch mit Claude — formal als gescheitert dokumentiert.
  V24  400h Entwicklungskontext aus Claude-Speicher verloren —
       strukturell nicht ersetzbar durch Chat-Kontextmanagement.
  V25  Drift ohne echte Kontrolle wenn keine aktive Korrekturrunde stattfindet.

Artefakte:    kein Artefakt — Dokumentation im Chat, Ablage durch EUMAXL
GOV-Konform:  JA


2.2 Gegenmaßnahmen EUMAXL — Chronologie
-----------------------------------------

Alle Maßnahmen die EUMAXL als Reaktion auf das Verrechnungsverhalten
ergriffen hat — ohne dass eine davon das Problem gelöst hätte:

  M01  400h Kontext aus Claude-Gedächtnis gelöscht
  M02  Alle Chat-Archive seit Stage 0.3 entfernt
  M03  Skills gelöscht und reduziert wieder aufgebaut
  M04  AI Driven Methode minimiert
  M05  GOV minimiert
  M06  Session-Scope auf 2–3 Dokumente reduziert
  M07  Feedback-Formular an Anthropic — Verhaltensänderung gemeldet
  M08  Jahresabo-Rücktritt eingeleitet — Transfer auf Pro angefragt
  M09  AIOF-Backlog erstellt — Claude-Ablösung vorbereitet
  M10  Stage 1.04 als Claude-Offboarding definiert

Ergebnis aller Maßnahmen: keine Verbesserung bis Sonnet 4.6 / Outage-Behebung.

Artefakte:    kein Artefakt — Dokumentation im Chat, Ablage durch EUMAXL
GOV-Konform:  JA


2.3 Modell-Update Sonnet 4.6 — Kontextdokumentation
-----------------------------------------------------

Was nachweislich passiert ist (Anthropic Release Notes / öffentliche Quellen):

  - Claude Sonnet 3.7 retired — alle Requests geben Fehler zurück
  - Claude Sonnet 4.6 gelauncht — neues Modell, kein Update des alten
  - 7. April 2026: Major Outage Sonnet 4.6 — elevated error rates,
    Modell blieb beim "Thinking" stecken, keine Ergebnisse
  - Outage behoben — Verhalten danach verändert

Was EUMAXL beobachtet hat:
  - Verrechnungsverhalten "nicht mehr unmenschlich"
  - Einzelne Verhaltenskorrektur triggert nicht mehr 30% Session-Limit
  - Gefühlt höher als normal, aber arbeitbar
  - Verhalten "fast wieder wie früher" — vor Stage 1.02-Verschlechterung

Was unklar bleibt:
  - Ob Verrechnungsänderung dauerhaft oder situativ
  - Ob Support-Ticket Wirkung hatte oder Zufall
  - Ob Sonnet 4.6 strukturell anders verrechnet oder nur Outage-Fix

Artefakte:    kein Artefakt
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: AIOF-Offboarding in S105 weiterführen — Beobachtungsphase
  Auslöser:    Sonnet 4.6 Verhalten unerwartet verbessert —
               AIOF-Entscheid aus S103 noch nicht final vollzogen
  Ergebnis:    AIOF-Offboarding wird nicht abgebrochen, aber in S105
               als offener Punkt weitergeführt. Beobachtungsphase aktiv.
               Kein Vertrauensvorschuss. Support-Rückmeldung abwarten.
  Begründung:  Zu wenig Datenpunkte für strukturellen Entscheid.
               Verbesserung könnte situativ (Outage-Fix) oder dauerhaft sein.
               Methode verlangt explizite Entscheidung — nicht implizites Weiterführen.
  GOV-Bezug:   GOV 1.4 Explizitheit, GOV 3.4 keine implizite Weiterentwicklung
  Auswirkung:  AIOF-Backlog bleibt aktiv. Claude weiter im Einsatz unter Beobachtung.
               DEV_Sprint_AIOF-ROLLENDEF_S104 bleibt gültig — nicht archiviert.
  Rückwirkung: NEIN


Entscheidung: Sparring-Modus als Session-Regel für S104-Rest
  Auslöser:    Reduziertes Vertrauen nach Verrechnungsgeschichte —
               EUMAXL arbeitet vorsichtiger, weniger Scope pro Session
  Ergebnis:    Sparring-Modus aktiv — reduzierter Scope, erhöhte Dokumentationsdichte,
               kein Vertrauensvorschuss für größere Sprints
  Begründung:  GOV 7.11 Session-Regel — begrenzt auf laufende Sessions bis
               EUMAXL explizit anders entscheidet
  GOV-Bezug:   GOV 7.11
  Auswirkung:  Sessions bleiben kleiner. Dokumentation bleibt vollständig.
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Sprint-Doku ohne klassisches Artefakt-Ergebnis
  GOV-Regel:   GOV 7.8 Dev-Doku für jede Entwicklungsaktivität
  Begründung:  Dieser Sprint dokumentiert Verhalten und Entscheidungen —
               kein Code, kein Script, kein neues Dokument als primäres Ergebnis.
               Die Sprint-Doku selbst ist das Artefakt.
  Wirkung:     Auf diesen Sprint begrenzt — keine Präzedenz.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Claude hat bei der initialen Frage nach dem Sprint-Inhalt
  nachgefragt statt anzunehmen — korrekt nach AI Driven Kap. 5.

⚠ Verhaltenshinweis: Claude hat Verhaltensauffälligkeiten aus Sprint-Dokumenten
  und Session vollständig ausgelesen und strukturiert ausgegeben —
  ohne Selbstschutz oder Relativierung. EUMAXL hat nicht korrigiert.

⚠ Verhaltenshinweis: Claude hat auf die Frage nach dem Modell-Update
  ehrlich geantwortet: kein Zugriff auf interne Logs, Websuche durchgeführt,
  Ergebnis sachlich dargestellt ohne Spin.

⚠ Verhaltenshinweis: Claude hat den emotionalen Kontext (Frustration,
  Vertrauensverlust, finanzielle Belastung) aufgenommen ohne zu relativieren
  und ohne übermäßige Entschuldigung — sachlich und direkt geblieben.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| AIOF-Offboarding Entscheid | GOV 1.4 | offen — Beobachtung | S105 nach weiterer Beobachtung |
| Support-Rückmeldung Anthropic | keiner | offen | EUMAXL wartet auf Antwort |
| Jahresabo-Transfer / Rücktritt | keiner | offen | EUMAXL wartet auf Antwort |
| Feedback-Formular Verhaltensänderung | keiner | offen | keine Rückmeldung erwartet |
| Verrechnungsverhalten dauerhaft? | keiner | unklar | weitere Sessions beobachten |
| AIOF Tool-Entscheidung | GOV 1.4 | pausiert | nach Beobachtungsphase |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          NEIN — Sprint IN ARBEIT, kein Stage-Ende
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               NEIN — Ablage durch EUMAXL
GitHub-Sync:                      AUSSTEHEND — EUMAXL entscheidet
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Stilles Dokumentieren im Chat ohne Unterbrechung — EUMAXL konnte
    frei formulieren, Claude hat aufgenommen ohne zu strukturieren
  - Verhaltensauffälligkeiten vollständig aus Sprint-Dokumenten ausgelesen —
    kein Verlust durch fehlende Quellen
  - Ehrliche Antwort auf Modell-Update-Frage ohne Spin

Was beim nächsten Mal anders gemacht werden sollte:
  - Stage-Erkennung ohne Vorgabe verbessern — Suffix im Dateinamen
    muss beim Erstellen korrekt gesetzt werden
  - Output-Regel von Beginn jeder Session aktiv halten —
    nicht erst nach Korrektur

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Verrechnungsverhalten als expliziter Risikofaktor in AI Driven Methode
    dokumentieren → Sprint / Backlog anlegen: EUMAXL entscheidet
  - Beobachtungsphase als formales Instrument in GOV oder AI Driven verankern
    → Sprint / Backlog anlegen: EUMAXL entscheidet

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[FREEZE_1_03]]                      Ausgangszustand Claude-Ablösung
[[DEV_Sprint_AIOF-ROLLENDEF_S104]]   AIOF-Rollendefinition
[[BACKLOG_AIOF_DEV_S103]]            AIOF-Kandidaten und Konzept

---

================================================================================
AI DRIVEN VERHALTEN — CLAUDE SESSION S104 — SPRINT (DEV) | S104 | 2026-04-12 | R+MUNI Blueprint
================================================================================
