================================================================================
S102 RESTART II — REKALIBRIERUNG NAMING & STRUCTURE — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_Rekalibrierung_RestartII_S102
Tag             : #dev #sprint #rekalibrierung #restartii #s102
Datum           : 2026-04-06
Stage           : S1.02 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-06
Jira-Sync       : NEIN
================================================================================

---
title: "S102 Restart II — Rekalibrierung Naming & Structure"
stage: S1.02
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-06"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, rekalibrierung, restartii, s102]
---

================================================================================
S102 RESTART II — REKALIBRIERUNG NAMING & STRUCTURE — SPRINT (DEV)
Stage S1.02 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Rekalibrierungssession vom 06.04.2026 — Restart II des Stage S1.02.
Gegenstand: naming_and_structure_S102 auf S102-Basis bringen.
Das Dokument war auf S101-Stand und nicht konform mit GOV 10.3 und
AI Driven Kap. 1. Claude hat versagt. EUMAXL hat das Dokument selbst
rekalibriert und freigegeben (Letzte Änderung: 2026-04-06 —
S102-Abgleich vollständig | Freigabe: EUMAXL).
Zusätzlich wurde eine 3-Tage-Deadline für die KI-Tool-Evaluation
gesetzt — siehe Kap. 3.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                  normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]       operative Arbeitsmethode
- [[naming_and_structure_S102]]            Gegenstand dieses Sprints
- [[DEV_Sprint_TotalReset_S102_2026-04-05]] Vorläufer-Sprint

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Strukturbereinigung
Beschreibung: naming_and_structure war auf S101-Stand — nicht konform mit
              GOV 10.3 und AI Driven Kap. 1. Claude hat die Aufgabe nicht
              korrekt gelöst. EUMAXL hat das Dokument selbst fertiggestellt.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         naming_and_structure vollständig auf S102 — konsistent mit
              GOV 10.3 und AI Driven Kap. 1. Normativ sauber.

Abgrenzung:   Kein Eingriff in GOV oder AI Driven Methode. Keine Änderungen
              an der tatsächlichen Verzeichnisstruktur.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  - naming_and_structure auf S101-Stand
  - Varianten nicht konform (DEV/EXP/ASC/MGT statt DEV/EXP/R+MUNI/CARD)
  - Dateinamen-Kürzel fehlten
  - CARD-Bereich nicht dokumentiert
  - EXPERT-Sonderstatus nicht explizit

Soll-Zustand nach dem Sprint:
  - naming_and_structure vollständig auf S102
  - Varianten korrekt: DEV / EXPERT / R+MUNI / CARD
  - Dateinamen-Kürzel dokumentiert: _DEV_ / _EXP_ / _MUNI_ / _CARD_
  - CARD als eigenständiger Bereich mit Ordnerstruktur (Kap. 2.5)
  - EXPERT-Sonderstatus explizit: on-demand aus DEV, nicht eigenständig
  - Dokument normativ sauber


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 naming_and_structure_S102 — abgeschlossen durch EUMAXL
------------------------------------------------------------
Claude hat das Dokument nicht korrekt geliefert. EUMAXL hat die
Rekalibrierung selbst durchgeführt und freigegeben.

Inhaltlich umgesetzt:
  - Kap. 1: Suffix-Logik S102-konform, S8-Referenz präzisiert
  - Kap. 2: Ablagestruktur vollständig — Root (2.1), Internal (2.2),
    Public (2.3), Public Repo (2.4), CARD als neuer Abschnitt 2.5
  - Kap. 3: Varianten DEV/EXPERT/R+MUNI/CARD, Dateinamen-Kürzel ergänzt,
    EXPERT-Sonderstatus explizit
  - Kap. 4: Namenskonvention R-MUNI vs. R+MUNI — unverändert

Artefakte:    naming_and_structure_S102.md — Projektfolder | Freigabe: EUMAXL
GOV-Konform:  JA

2.2 Chat eingelesen und Sprint-Doku erstellt
---------------------------------------------
Kontext aus dem Chat dieser Session sowie aus den Vorläufer-Sessions
(05.04.2026) wurde eingelesen und in dieser Sprint-Doku dokumentiert.

Artefakte:    DEV_Sprint_Rekalibrierung_RestartII_S102_2026-04-06.md
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: KI-Tool-Evaluation — Deadline gesetzt
  Auslöser:    Claude hat nach einem Update ein Nutzungsverhalten gezeigt,
               das für den R+MUNI DEV-Betrieb nicht tragbar ist.
               Leistung in dieser Session nicht akzeptabel.
  Ergebnis:    3-Tage-Deadline ab 2026-04-06. Wird das Verhalten nicht
               korrigiert, wird Claudes Rolle in R+MUNI überdacht.
               Mögliche Konsequenz: Ablösung durch generische KI-Referenz.
               Alle Claude-Verweise werden durch "KI" / "generische AI" ersetzt.
  Begründung:  AI Driven Methode Kap. 2 und Kap. 14.
  GOV-Bezug:   AI Driven Methode Kap. 2, Kap. 14
  Auswirkung:  Evaluationszeitraum bis 2026-04-09 — Ergebnis wird dokumentiert.
  Rückwirkung: JA — bei negativem Ergebnis: alle Claude-Verweise in allen
               Dokumenten ersetzen.

Entscheidung: EXPERT on-demand, nicht eigenständig geführt
  Auslöser:    EXPERT war in S101 implizit als eigenständig behandelt —
               nicht konform mit GOV 10.3
  Ergebnis:    EXPERT explizit als on-demand-Ableitung aus DEV dokumentiert
  Begründung:  GOV 10.3
  GOV-Bezug:   GOV 10.3
  Auswirkung:  In naming_and_structure_S102 normativ verankert
  Rückwirkung: NEIN

Entscheidung: CARD als eigenständiger Ablagebereich Kap. 2.5
  Auslöser:    CARD fehlte in S101 vollständig als dokumentierter Bereich
  Ergebnis:    Kap. 2.5 mit vollständiger Ordnerstruktur inkl. Thema-Mapping
  Begründung:  GOV 10.3 führt CARD als eigenständig geführte Variante
  GOV-Bezug:   GOV 10.3
  Auswirkung:  CARD vollständig in naming_and_structure abgebildet
  Rückwirkung: NEIN

Entscheidung: Dateinamen-Kürzel normativ verankern
  Auslöser:    Kürzel existierten de facto ohne normative Grundlage
  Ergebnis:    _DEV_ / _EXP_ / _MUNI_ / _CARD_ in Kap. 3 dokumentiert
  Begründung:  GOV 1.4 — Explizitheit als Grundprinzip
  GOV-Bezug:   GOV 1.4
  Auswirkung:  Kürzel sind normativ verankert
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Sprint-Ergebnis durch EUMAXL statt durch KI geliefert
  GOV-Regel:   AI Driven Methode Kap. 2 — Die KI liefert Dokumentation
  Begründung:  Claude hat nicht korrekt geliefert. EUMAXL hat das Dokument
               selbst fertiggestellt.
  Wirkung:     Auf diese Session begrenzt. Keine Präzedenzwirkung.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Claude hat in dieser Session nicht die erwartete
  Leistung erbracht. naming_and_structure_S102 musste durch EUMAXL selbst
  rekalibriert werden.

⚠ Verhaltenshinweis: Das Nutzungsverhalten nach dem Claude-Update wird
  als nicht tragbar eingestuft. Deadline: 2026-04-09.

⚠ Verhaltenshinweis: Claude hat auf eine punktuelle Korrektur mit einer
  Komplettneuschreibung reagiert statt chirurgisch einzugreifen —
  AI Driven Methode Kap. 8 (iterative Neugenerierung akkumuliert Drift).


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| KI-Tool-Evaluation | AI Driven Kap. 2, 14 | offen — Deadline 2026-04-09 | EUMAXL bewertet und entscheidet |
| GitHub-Sync naming_and_structure_S102 | GOV 10.2 | offen | EUMAXL entscheidet |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — naming_and_structure_S102.md, Projektfolder
GitHub-Sync:                      AUSSTEHEND — Entscheidung bei EUMAXL
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - EUMAXL hat den Fehler erkannt und das Dokument selbst korrekt fertiggestellt.
  - Qualitätssicherung durch EUMAXL hat funktioniert.

Was beim nächsten Mal anders gemacht werden sollte:
  - Bei Strukturdokumenten immer zuerst Quelldateien lesen — nie aus dem
    Gedächtnis arbeiten.
  - In normativen Dokumenten kein Non-Normatives einbauen.
  - Korrekturen chirurgisch umsetzen — nie das gesamte Dokument neu
    schreiben wenn nur ein Punkt korrigiert werden soll.

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - KI-Tool-Evaluation läuft — Ergebnis kann AI Driven Methode Kap. 14
    und alle Tool-Verweise betreffen. Sprint / Backlog anlegen: JA.

---

## Bezüge

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[naming_and_structure_S102]]              Ergebnis-Dokument dieses Sprints
[[DEV_Sprint_TotalReset_S102_2026-04-05]]  Vorläufer-Sprint

---

================================================================================
S102 RESTART II — REKALIBRIERUNG NAMING & STRUCTURE — SPRINT (DEV)
S1.02 | 2026-04-06 | R+MUNI Blueprint
================================================================================
