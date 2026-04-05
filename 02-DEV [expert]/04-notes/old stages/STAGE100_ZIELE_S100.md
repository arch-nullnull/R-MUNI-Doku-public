================================================================================
STAGE 100 – Phase 1.xx | Produktivbetrieb & freie Weiterentwicklung
Normative Definition und Geltungsbereich
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : STAGE100_ZIELE_S100
Tag             : #stage #ziele #s100 #produktiv #phase1
Datum           : 2026-03-29
Stage           : S100 — AKTIV
Gültig für      : Phase 1.00 – 2.00 (bis Beta 2.0, September 2026)
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt durch  : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
1. ZWECK VON STAGE 100
================================================================================

Stage 100 ist das Rahmenwerk für die gesamte Phase 1.00–2.00 —
gültig von Beta 1.0 Release bis Beta 2.0 (Ziel: September 2026).

Es beschreibt wie in dieser Phase gearbeitet wird — nicht was erreicht
werden muss. Einzelne Stages innerhalb der Phase (S101, S102, ...) erben
diesen Rahmen und konkretisieren ihn bei Bedarf.

Arbeit findet statt wenn sie sinnvoll ist und jemand sie anstoßen will.
Kein Tagesziel. Kein Abarbeitungsdruck. Session-basiert.

Im Fokus stehen:
  - Produktivbetrieb aufrechterhalten und stabil halten
  - Beta-Kunden weiter begleiten und ausbauen
  - DEV und Sales bei Bedarf onboarden und einbinden
  - Backlog-Sprints on demand — wenn jemand einen startet wird gearbeitet
  - Weiterentwicklung nach Lust und Kapazität — nicht nach Plan


================================================================================
2. AUSGANGSBASIS
================================================================================

Stage 100 baut auf dem abgeschlossenen Stage-8-Zustand (Beta-1.0-Release) auf.

  - Stage-3 bis Stage-8-Artefakte: read-only, kein Eingriff
  - Beta-1.0-Release (GitHub Release v1.0-beta): veröffentlicht, stabil
  - FREEZE_8: normativ gültig als Ausgangszustand für Phase 1.xx
  - Jira & Confluence: vorhanden, aber inaktiv —
    werden nur aktiviert wenn DEV oder Sales einsteigen und es brauchen

Bezug auf vorherigen Freeze:
  [[FREEZE_8]]             Ausgangszustand für Phase 1.xx


================================================================================
3. CHARAKTER VON STAGE 100
================================================================================

Stage 100 ist kein Sprint-Stage — er ist ein Phasen-Rahmen.

  - Gültig für alle Stages der Phase 1.xx (S101, S102, ...)
  - Kein Gesamtziel das Stage 100 abschließt
  - Arbeit entsteht durch Sessions — nicht durch Planung
  - Backlog-Sprints können jederzeit gestartet werden
  - Was nicht gestartet wird bleibt im Backlog — ohne Druck
  - Phase endet mit Beta 2.0 — Ziel September 2026

Stage 100 darf wachsen wenn es sich ergibt — und ruhen wenn nichts ansteht.


================================================================================
4. ARBEITSWEISE IN STAGE 101
================================================================================

4.1 Session-basierte Arbeit
-----------------------------
  - Jede Arbeitssession ist in sich abgeschlossen
  - Kein Carry-over-Druck zwischen Sessions
  - Ergebnisse werden dokumentiert wenn sie spruchreif sind


4.2 Backlog-Sprint-Lifecycle
------------------------------
  Auslösung:
  - DEV, EUMAXL oder externe Interessierte können ein public Backlog-Item
    jederzeit schnappen
  - Auslösung via Ticket — Jira oder GitHub Issue, nach Wahl des Bearbeiters
  - Externe werden gefragt ob sie ins DEV-Team einsteigen wollen —
    bei positivem Gefühl werden alle Zugänge vergeben

  Arbeitsbasis:
  - Wird pro Sprint-Start explizit entschieden:
    aktueller Produktivstand oder definierter Freeze-Stand

  Stage-Übergang:
  - Laufende Backlog-Sprints fallen bei Stage-Wechsel automatisch
    in den Backlog zurück — mit dem erreichten Entwicklungsstand
  - Kein offener Sprint blockiert einen Stage-Wechsel
  - Neustart im neuen Stage erfolgt aktiv und explizit


4.3 Releasezyklen
------------------
  Der Rhythmus für Phase 1.xx:

  4 Monate   Backlog-Phase   — freie Arbeit, Sprints on demand, kein Druck
  2 Monate   Sprint-Phase    — fokussierte Entwicklung Richtung Beta 2.0
  Review     4-Next-Beta     — Entscheid was in Beta 2.0 kommt
  Ziel       Beta 2.0        — September 2026

  Kein Item ist verpflichtend — der Zyklus gibt Struktur ohne Zwang.


4.3 DEV & Sales Onboarding
----------------------------
  - Onboarding erfolgt wenn konkrete Personen einsteigen
  - Jira & Confluence werden bei Bedarf aktiviert — nicht vorher
  - Kein Onboarding-Aufwand ohne konkreten Anlass


================================================================================
5. RÜCKKOPPLUNGSSCHUTZ
================================================================================

  - Stage-3 bis Stage-8-Artefakte: read-only ohne Ausnahme
  - Bugfixes erfordern explizite Freigabe und Dokumentation
  - Keine Logikänderung ohne expliziten Entscheid durch EUMAXL
  - Jira-Sync: nur explizit — kein automatischer Reflex
  - Rollentrennung GOV 13: DEV / ASC / EUMAXL strikt getrennt


================================================================================
6. DOKUMENTATION IN PHASE 1.XX
================================================================================

  - Sprint-Bezeichnung: Sprint-DEV-S1xx-<Kürzel>
  - Sprint-DEV-Dokumentation für alle Entwicklungsaktivitäten (GOV 10.8)
  - Dokumentation entsteht wenn Arbeit spruchreif ist — kein Vorab-Overhead
  - FREEZE je Stage am Stage-Ende: autarke Wissensbasis für Folge-Stage


================================================================================
7. FORMALE FESTSTELLUNG
================================================================================

Mit dieser Definition ist Stage 100:
  - logisch eröffnet
  - klar abgegrenzt von der Beta-Zählungslogik (S001–S008)
  - rückkopplungssicher
  - GOV-konform
  - als Phasen-Rahmen für 1.00–2.00 gültig bis Beta 2.0 September 2026

Stage 3 bis 8 bleiben fixiert und geschützt.
Stage 100 darf wachsen wenn es sich ergibt — ohne Zwang.


================================================================================
BEZÜGE
================================================================================
[[Global_GOV_S8]]                            normative Grundlage
[[FREEZE_8]]                                 Ausgangszustand — letzter stabiler Stand
[[AI_DRIVEN_DEV_METHODE_S8]]                 Methodik-Basis
[[Sprint-DEV-BACKLOG_Jira-Konventionen_S8]]  Jira-Konvention


================================================================================
STAGE 100 – Phase 1.xx | Produktivbetrieb & freie Weiterentwicklung
ZIELE DEFINIERT | 2026-03-29
R+MUNI Blueprint | Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
