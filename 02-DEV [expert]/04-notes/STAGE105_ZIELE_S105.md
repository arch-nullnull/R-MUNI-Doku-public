================================================================================
STAGE 105 – Ziele
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : STAGE105_ZIELE_S105
Tag             : #stage #ziele #s105
Datum           : 2026-04-13
Stage           : S105 — VORBEREITET
Status          : ENTWURF — Freigabe EUMAXL
Verantwortlich  : EUMAXL
Basis           : FREEZE_1_04 — Kapitel 5 (Offene Punkte)
Jira-Sync       : NEIN
================================================================================

---
title: "Stage 105 — Ziele"
stage: S1.05
status: "ENTWURF"
typ: "Ziele"
datum: "2026-04-13"
autor: EUMAXL
tags: [rmuni, blueprint, stage, ziele, s105]
---

================================================================================
STAGE 105 — ZIELE
Basis: Offene Punkte FREEZE_1.04
================================================================================

---

================================================================================
1. ZWECK VON STAGE 105
================================================================================

Stage 105 schließt was in Stage 104 offen geblieben ist und führt die
Beobachtungsphase Sonnet 4.6 weiter — mit dem expliziten Ziel zu entscheiden
ob AIOF weitergebaut wird oder auf Hold geht.


================================================================================
2. ZIELE
================================================================================

S105-Z1: AUSSENWIRKUNG FINALISIEREN (CARRY-OVER Z1/Z3 S104)
-------------------------------------------------------------

  • Qualitäts-Check Außenwirkung durchführen
  • LinkedIn-Profil überarbeiten
  • GitHub Release öffentlich deployen (nach Q-Check)

Abhängigkeit: Q-Check vor Release


S105-Z2: NBX ERWEITERUNG & CLEANUP (CARRY-OVER Z4 S104)
---------------------------------------------------------

  • IP-Merge Script zwischen NBX03 und NBX04 — Fix läuft, QM-Check
  • NBX03/04 bereinigen
  • nbx_config.txt + nbx_raw.json in .gitignore

Hinweis: NBX läuft soweit, QM-Run muss nicht zwingend S105 sein


S105-Z3: GOV & AI DRIVEN REDUKTION (BACKLOG S104)
--------------------------------------------------

  • GOV auf 6 Kernregeln destillieren — EUMAXL definiert welche
  • AI Driven auf S104-Erfahrungen bringen (Sparring)
  • AI Driven reduzieren — separater Chat ohne Kontext-Drift

Voraussetzung: Beobachtungsphase Sonnet 4.6 abgeschlossen
               AIOF-Entscheid getroffen (Z4)


S105-Z4: AIOF-ENTSCHEID
------------------------

  • Beobachtungsphase Sonnet 4.6 auswerten
  • Entscheid: Claude weiter / AIOF weiterbauen / hybrid / AIOF auf Hold

Hinweis: Dieser Entscheid beeinflusst Z3 (GOV-Reduktion tool-agnostisch
         oder Claude-spezifisch) und den gesamten S105-Charakter.


S105-Z5: KLEINERE CARRY-OVER (NACH KAPAZITÄT)
----------------------------------------------

  • SVG Pillow in Install.txt nachtragen
  • README Image/Link-Bugs nach Repo-Sync
  • Associate Cleaning Run in weiteren Dokumenten
  • MUNIDELL SVG Header — erledigt laut EUMAXL, formal bestätigen


================================================================================
3. KRITISCHER PFAD
================================================================================

  1. Z4 (AIOF-Entscheid) — beeinflusst Z3
  2. Q-Check (Z1) — vor Release
  3. Z1 Release — nach Q-Check
  4. Z3 GOV-Reduktion — nach Z4

Parallel / nach Kapazität:
  Z2 NBX, Z5 Kleinere Carry-over


================================================================================
4. DAUERHAFT LAUFEND — IN JEDEM STAGE
================================================================================

Diese Punkte laufen parallel ohne eigenen Sprint-Trigger.
Ereignisse werden im laufenden Stage mitdokumentiert —
historische Nachvollziehbarkeit ist explizites Ziel.

  Kunden-Feedback       Eingang und Bewertung laufend
                        Dringliches → Sprint-Auslöser
                        Sonstiges → Backlog oder verwerfen

  BPMN 2.0 Flows        Aufbau Scriptrunner FLOW — kontinuierlich
                        kein Zeitdruck, kein Abarbeitungsziel

  Videos & Streaming    Spontane Sessions nach Lust und Laune — OBS läuft
                        Kein Sprint nötig, kein Abarbeitungsziel

  Beta / DEV User       Aufnahme jederzeit möglich
                        Zeitpunkt wird im Stage mitdokumentiert


================================================================================
5. ABGRENZUNG
================================================================================

Nicht Teil von Stage 105:
  - Geplantes Demo-Video (strukturiert, für Außenwirkung) — wartet auf neuen DEV-Rechner
  - Beta 2.0 Vorbereitung (S106+)
  - Weitere AIOF-Infrastruktur ohne konkreten Anlass


================================================================================
BEZÜGE
================================================================================

[[FREEZE_1_04]]                       Ausgangszustand — Basis dieser Ziele
[[BACKLOG_GOV-AIDRIVEN-REDUKTION_DEV_S104]]   Z3-Grundlage
[[DEV_Sprint_AIOF-ROLLENDEF_S104]]    AIOF-Stand — Beobachtungsphase läuft
[[Global_GOV_DEV_S102]]               normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]    Methodik-Basis


================================================================================
STAGE 105 — ZIELE | ENTWURF | 2026-04-13 | R+MUNI Blueprint
================================================================================
