================================================================================
AIOF — ROLLENDEFINITION SONNET — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_AIOF-ROLLENDEF_S104
Tag             : #dev #sprint #aiof #rollendef #sonnet #s104
Datum           : 2026-04-10
Stage           : S1.04 — AKTIV
Status          : IN ARBEIT
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN
================================================================================

---
title: "AIOF — Rollendefinition Sonnet"
stage: S1.04
status: "IN ARBEIT"
typ: "Sprint"
datum: "2026-04-10"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, aiof, rollendef, sonnet, s104]
---

================================================================================
AIOF — ROLLENDEFINITION SONNET — SPRINT (DEV)
Stage S1.04 | IN ARBEIT | R+MUNI Blueprint
================================================================================

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]
- [[FREEZE_1_03]]
- [[BACKLOG_AIOF_DEV_S103]]

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

Auslöser:     Strukturbereinigung / Entwicklerwunsch
Ziel:         AIOF-Elemente mit ihren Vorgehensweisen verbindlich dokumentiert
Abgrenzung:   Keine inhaltliche Weiterentwicklung der Tools. Keine Evaluation.
Ist:          Keine dokumentierte Rollentrennung zwischen AIOF-Elementen.
Soll:         Jedes AIOF-Element hat seine dokumentierte Vorgehensweise.
Rolle:        DEV


================================================================================
2. AIOF — GRUNDPRINZIP
================================================================================

Jedes AI Office Element hat seine eigene Vorgehensweise
die auf ihr Modell optimiert ist.


================================================================================
3. SONNET (Claude.ai)
================================================================================

ERSTELLUNG PROJEKTFOLDER
  R+MUNI Skill einlesen (generelle minimale Infos)
  Relevante Skills für Run aktivieren (z.B. jArchi, Netbox etc.)
  Projektfolder einlesen:
    GOV
    AI_DRIVEN_DEV_CLO_Sxxx
    structure.txt
    readme.md
    Install.txt
    Principles
  Hinweis: Reduziert gegenüber S1.03 — Script only
  Relevante Templates im Quellenordner bereitstellen
  Relevante Script-Reihen bereitstellen (Python und jArchi)

OUTPUT
  .md
  .svg

ATLASSIAN-TRIGGER
  Codewort: "schlumpfen"
  Push in Jira als Story oder als Confluence-Beitrag
  (was kommt wird im Chat kommuniziert)


PROBLEM
  Kosten / Kosten / Kosten


================================================================================
4. SONNET 4.6 VIA GITHUB COPILOT PRO — OPTION OFFEN
================================================================================

Modell:   Claude Sonnet 4.6 (identisch zu CLO)
Billing:  GitHub Copilot Pro ($10/Monat) — nicht über claude.ai
Usecase:  Script-Entwicklung direkt in VS Code
          Model Picker: Chat, Edit, Agent Mode

EINSCHRÄNKUNGEN
  Kein Projektfolder-Load
  Kein Skill-Load
  EU-Verfügbarkeit Claude-Modelle ungeklärt (AT = EU)

ENTSCHEID
  EUMAXL — offen


================================================================================
5. COPILOT
================================================================================

PNG-Erstellung für Images
  Prompt mit 4 identen Bildern aus der Reihe
  4–6 Bilder
  Abbruch — neuer Chat

PROBLEM
  Hoher Drift
  Spielzeug AI


================================================================================
6. CHAT GPT
================================================================================

Wird optimiert anhand von:
  Bestehenden Infos aus CARD
  Claude-Vorgehensweise light

Usecase:
  Doku mit keinem Drift
  Blueprint mit Außenwirkung

Vorgehensweise:
  <folgt — Input durch EUMAXL>


================================================================================
7. GEMINI
================================================================================

Wird optimiert anhand von:
  Bestehenden Infos aus CARD
  Claude-Vorgehensweise light

Usecase:
  Doku mit keinem Drift
  Blueprint mit Außenwirkung

Vorgehensweise:
  <folgt — Input durch EUMAXL>


================================================================================
8. OFFBOARDING SONNET — DOKUMENTE ZU ÜBERARBEITEN
================================================================================

Vor Stage-Abschluss verpflichtend zu reviewen und anzupassen.
Reihenfolge nach EUMAXL-Kapazität — kein Zeitdruck, aber vor FREEZE_1.04.

GOV
  Kap. 9      KI-Tool-Rollentrennung als explizites Unterkapitel
  Kap. 6.10   Script-Entwicklung via KI-Modell — Führung bleibt bei EUMAXL
  Kap. neu    KI-Tool-Governance: welches AIOF-Element welche Aufgaben übernimmt

AI_DRIVEN_DEV_CLO_Sxxx (Nachfolger von AI_DRIVEN_DEV_S102 — Sonnet-spezifisch)
  Kap. 14     KI-Tool-Rollentrennung: Sonnet = Script, AIOF-Primärtool = offen
  Kap. 4      Session-Ablauf: Sonnet-Sessions ohne GOV / AI Driven Load
  Kap. 12     Kontext-Minimierung Sonnet explizit
  Basis für Projektfolder Script-Sessions

FREEZE_1.04
  Sonnet-Rolle vollständig eingearbeitet
  AIOF-Struktur (alle Elemente) dokumentiert
  Offboarding-Status festgehalten

NAMING_AND_STRUCTURE
  AIOF-Elemente in Dokumentationsstruktur aufnehmen


================================================================================
9. OFFENE PUNKTE
================================================================================

| Punkt                              | GOV-Bezug    | Status | Nächste Aktion           |
|------------------------------------|--------------|--------|--------------------------|
| Chat GPT Vorgehensweise            | —            | offen  | Input durch EUMAXL       |
| GOV überarbeiten (Kap. 9, 6.10, neu) | GOV 9.5, 6.11 | offen | EUMAXL / vor FREEZE_1.04 |
| AI_DRIVEN_DEV_CLO_Sxxx erstellen   | AI Driven    | offen  | EUMAXL / vor FREEZE_1.04 |
| NAMING_AND_STRUCTURE anpassen      | —            | offen  | EUMAXL / vor FREEZE_1.04 |
| FREEZE_1.04 — AIOF einarbeiten     | GOV 7.9      | offen  | Bei Stage-1.04-Abschluss |
| Modellversion 4.6 vs. 4.5          | GOV 6.11     | offen  | EUMAXL                   |


================================================================================
10. STAGE-ABSCHLUSS (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          NEIN — offen: Chat GPT Vorgehensweise
GOV-Konformität hergestellt:      NEIN — offen: AI Driven DEV Anpassung ausstehend
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               NEIN — Ablage durch EUMAXL
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH

---

## Bezüge

[[Global_GOV_DEV_S102]]
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]
[[FREEZE_1_03]]
[[BACKLOG_AIOF_DEV_S103]]

---

================================================================================
AIOF — ROLLENDEFINITION SONNET | S1.04 | 2026-04-10 | R+MUNI Blueprint
================================================================================
