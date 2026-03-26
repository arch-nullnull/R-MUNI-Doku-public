================================================================================
SPRINT-DEV-BACKLOG – Jira Konventionen
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV-BACKLOG_Jira-Konventionen_S8.md
Datum           : 2026-03-26
Stage           : S8 – BACKLOG
Status          : BACKLOG — nicht gestartet
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN — Quelle war MUNIEA-147 (Jira-only, jetzt lokal gesichert)
================================================================================


================================================================================
1. MOTIVATION UND AUSLÖSER
================================================================================

Auslöser-Typ: Strukturbereinigung / GOV-Lücke

Jira-Tickets wurden in Stage 7 ohne feste Konvention erstellt — Issue-Typ
(Task / Story / Bug) und Beschreibungsformat variierten je nach Situation.
Das erzeugte Inkonsistenz und war nicht GOV-konform.

Das Ticket MUNIEA-147 dokumentierte die gewünschte Konvention, wurde jedoch
nie als lokales .md gesichert. Mit der Bereinigung des Jira-Backlogs zu
Stage-8-Beginn wird dieses Dokument als lokale Quelle der Wahrheit angelegt.

Erkannt in:    Stage 7, MUNIEA-147 (Jira-only)
Erkannt am:    2026-03-21
Lokal gesichert: 2026-03-26 (Stage-8-Start, Jira-Bereinigung)


================================================================================
2. ZIEL
================================================================================

Ziel:
  Die Jira-Ticket-Konventionen sind als verbindliches Kapitel lokal
  dokumentiert und für alle Stage-8-Sprints gültig.

Erfolgskriterium:
  Dieses Dokument ist lokal abgelegt. Jira wird ab Stage 8 nur noch
  explizit und gezielt bespiehlt — kein automatischer Sync-Reflex.

Abgrenzung — nicht Teil dieses Sprints:
  - Keine Änderung an bestehenden GOV-Kapiteln
  - Keine Umbenennung bestehender Tickets
  - Kein Tool-Sprint — reine Dokumentation


================================================================================
3. KONVENTION — VERBINDLICHER INHALT
================================================================================

Issue-Typ Mapping
-----------------
  BACKLOG-Eintrag          →  Task
  Bugfix                   →  Bug
  Feature-Idee / Wunsch    →  Story
  Teilaufgabe eines Sprint  →  Sub-Task

Pflicht-Beschreibungsstruktur (Markdown)
-----------------------------------------
  ## Motivation
  ## Ziel
  ## Erfolgskriterium
  ## Abgrenzung
  ## Referenz

Formatregeln
-------------
  - Immer ## Überschriften
  - Keine Tabellen in der Beschreibung
  - Referenz auf Blueprint-Dokument immer im letzten Abschnitt

Jira-Sync-Regel ab Stage 8
----------------------------
  - Jira wird nicht automatisch befüllt
  - Sync erfolgt nur explizit — auf Wunsch, in eigenem Arbeitsschritt
  - Auslöser: bewusste Entscheidung durch EUMAXL ("jetzt nach Jira")
  - Kein Jira-Eintrag ohne zugehöriges lokales .md als Quelle


================================================================================
4. FACHLICHER MEHRWERT
================================================================================

Mehrwert für: DEV / Konsistenz / Stage-8-Sauberkeit

  - Jira und lokale Doku sind nicht mehr auseinander
  - Neue Tickets entstehen nach einheitlichem Schema
  - Kein Konventionsverlust bei Stage-Wechsel
  - Quelle der Wahrheit ist lokal — Jira ist Spiegel, nicht Primärquelle

Ohne diesen Sprint:
  Jira bleibt Wildwuchs. Neue Tickets entstehen inkonsistent.
  Sync-Reflex bleibt unkontrolliert.


================================================================================
5. PRIORISIERUNG
================================================================================

Priorität:     Hoch — gilt ab Stage-8-Start sofort
Zeitrahmen:    Stage 8 — sofort gültig als Konvention

Priorisiert durch:
  Stage-8-Bereinigung + Jira-Sync-Neuausrichtung

Kann verschoben werden wenn:
  Nicht verschiebbar — Konvention gilt sofort, Sprint ist nur Dokumentation.


================================================================================
6. GOVERNANCE-CHECK
================================================================================

| Kriterium                          | Status  | Anmerkung                        |
|------------------------------------|---------|----------------------------------|
| Auslöser GOV-konform (GOV 10.3)    | OK      | Strukturbereinigung              |
| Fachlicher Mehrwert benennbar      | OK      | Siehe Kapitel 4                  |
| Ziel explizit und überprüfbar      | OK      | Konvention dokumentiert          |
| Abgrenzung definiert               | OK      | Nur Dokumentation, kein GOV-Eingriff |
| Rückkopplungsschutz geprüft        | OK      | Stage 3/4/5/6/7 unberührt        |
| Keine implizite GOV-Änderung       | OK      | Additive Konvention, keine Änderung |


================================================================================
7. STATUS UND VERLAUF
================================================================================

2026-03-21  ERSTELLT       MUNIEA-147 in Jira angelegt (EUMAXL)
2026-03-26  LOKAL GESICHERT  Als .md bei Jira-Bereinigung Stage-8-Start (EUMAXL + Claude)
2026-03-26  KONVENTION AKTIV  Gilt ab sofort für alle Stage-8-Sprints


================================================================================
BEZÜGE
================================================================================
[[GOV_Global_S6]]                    normative Grundlage
[[FREEZE-7_S7]]                      Ausgangszustand Stage 8
MUNIEA-147                           Ursprüngliches Jira-Ticket (wird gelöscht)


================================================================================
Sprint-DEV-BACKLOG_Jira-Konventionen_S8.md | S8 | 2026-03-26 | R+MUNI Blueprint
================================================================================
