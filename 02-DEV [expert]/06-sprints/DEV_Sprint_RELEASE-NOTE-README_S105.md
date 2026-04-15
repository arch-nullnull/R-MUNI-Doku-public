================================================================================
RELEASE NOTE & README UMBAU — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_RELEASE-NOTE-README_S105
Tag             : #dev #sprint #release #readme #s105
Datum           : 2026-04-15
Stage           : S105 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================

---
title: "Release Note & README Umbau — Sprint"
stage: S105
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-15"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, s105, release, readme]
---

================================================================================
RELEASE NOTE & README UMBAU — SPRINT (DEV)
Stage S105 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Im Qualitätsrun S105Q2 wurden zwei inhaltliche Findings im README identifiziert:
Phase-Stand veraltet (1.04 statt 1.05) und persönliche Teile die nicht mehr zur
neuen Außenwirkung passen. R+MUNI wechselt in S105 bewusst den Charakter — vom
Lern- und Spaßprojekt zur professionellen Positionierung. Zusätzlich fiel die
Entscheidung zur Lizenzumstellung von GNU auf MIT.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S105]]                  normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S105]]       operative Arbeitsmethode
- [[FREEZE_1_04_ADDENDUM_S105]]            Qualitätsgate S105Q2 Kontext
- [[STAGE105_ZIELE_S105]]                  Z1 Außenwirkung

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Qualitätszuwachs + Entwicklerwunsch
Beschreibung: Qualitätsrun S105Q2 hat veralteten Phase-Stand und persönliche
              Teile im README identifiziert die vor dem Release bereinigt werden.
              Gleichzeitig Entscheid Lizenzwechsel GNU → MIT.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:       README clean und professionell für Außenwirkung.
            RELEASE_NOTE_S105.md als ehrliches Begleitdokument zum Release.
            Lizenz auf MIT umgestellt.

Abgrenzung: Kein inhaltlicher Eingriff in Säulen, Script-Tabelle oder SVG-Links.
            Kein LinkedIn-Posting — eigener Schritt Z1.
            Kein GitHub Release — nach Qualitätsgate.
            Kein Rosetta Stone — eigener Sprint nach Qualitätsrun.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  README zeigt Phase 1.04, enthält Danksagung und "Ehrlichkeit zuerst"-Abschnitt.
  Lizenz: GNU GPL-3.0.
  Kein Begleitdokument zum Release vorhanden.

Soll-Zustand nach dem Sprint:
  README zeigt Phase 1.05, ohne persönliche Teile, MIT-Lizenz referenziert.
  RELEASE_NOTE_S105.md existiert unter 04-notes\ mit persönlichem Anteil
  und ehrlicher Bilanz S1→S1.5.
  LICENSE-Datei manuell durch EUMAXL auf MIT getauscht.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle:                 DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 README Umbau
-----------------
Phase-Stand 1.04 → 1.05 (zwei Stellen).
Danksagung entfernt — in RELEASE_NOTE verschoben.
"Ehrlichkeit zuerst"-Abschnitt entfernt — in RELEASE_NOTE verschoben.
Lizenzhinweis auf MIT aktualisiert.
Link auf RELEASE_NOTE eingefügt.
"AI-driven entwickelt"-Satz bleibt — inhaltlich korrekt, S105 voll aktiv.

Artefakte:    README.md (Haupt-Repo Root)
GOV-Konform:  JA


2.2 RELEASE_NOTE_S105.md
----------------------------
Type 9 Info — Format frei, kein Template.
Persönliche Teile aus README übernommen.
Ehrliche Bilanz der Reise S1→S1.5.

Artefakte:    RELEASE_NOTE_S105.md → R+MUNI Doku-public\04-notes\
GOV-Konform:  JA


2.3 Lizenzwechsel
------------------
Entscheid: GNU GPL-3.0 → MIT.
README referenziert MIT.
LICENSE-Datei: manuell durch EUMAXL zu tauschen.

Artefakte:    LICENSE (manuell EUMAXL)
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Lizenzwechsel GNU → MIT
  Auslöser:    Bewusste Neupositionierung — MIT erlaubt breitere Nutzung ohne
               Copyleft-Pflicht. Niederschwelliger für KMU-Einsatz.
  Ergebnis:    MIT Lizenz ab S105 gültig
  Begründung:  R+MUNI soll genutzt werden — Lizenzbarrieren widersprechen dem
               Grundsatz "kostenlos und offen". MIT ist ehrlicher dazu.
  GOV-Bezug:   kein direkter Bezug
  Auswirkung:  LICENSE-Datei manuell tauschen vor GitHub-Sync
  Rückwirkung: NEIN

Entscheidung: Persönliche Teile aus README in RELEASE_NOTE
  Auslöser:    Charakterwechsel R+MUNI in S105 — professionelle Außenwirkung
  Ergebnis:    README clean, RELEASE_NOTE trägt den persönlichen Anteil
  Begründung:  Danksagung und "Ehrlichkeit zuerst" gehören erhalten als ehrliches
               Dokument der Projektreise — nicht im Haupt-README der Außenwirkung
  GOV-Bezug:   kein direkter Bezug
  Auswirkung:  RELEASE_NOTE wird mit Release veröffentlicht
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Keine Abweichungen.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Scope-Expansion erkannt — Sprint ohne Template gestartet,
  gestoppt auf Hinweis EUMAXL. Template nachgeladen, neu gestartet.

⚠ Verhaltenshinweis: Annahme zu AIOF/README-Satz — durch Nachlesen FREEZE_1_04
  korrigiert, kein Finding.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| LICENSE-Datei GNU → MIT tauschen | keiner | offen | Manuell EUMAXL vor Git-Sync |
| README-Link auf RELEASE_NOTE nach Sync prüfen | keiner | offen | GitHub-Test |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — README.md Root | RELEASE_NOTE_S105.md 04-notes\
GitHub-Sync:                      AUSSTEHEND — nach Qualitätsgate S105Q2
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Qualitätsrun hat konkrete Findings geliefert die direkt umsetzbar waren
  - Trennung README / RELEASE_NOTE sauber und ohne Inhaltsverlust

Was beim nächsten Mal anders gemacht werden sollte:
  - Template zuerst laden — nicht antizipieren ob es vorhanden ist

Erkenntnisse die Dokumente oder GOV verändern:
  - Keine

---

## Bezüge

[[Global_GOV_DEV_S105]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S105]]         operative Arbeitsmethode
[[FREEZE_1_04]]                            Ausgangszustand Stage 105
[[FREEZE_1_04_ADDENDUM_S105]]              Qualitätsgate S105Q2
[[STAGE105_ZIELE_S105]]                    Z1 Außenwirkung

---

================================================================================
RELEASE NOTE & README UMBAU — SPRINT (DEV) | S105 | 2026-04-15 | R+MUNI Blueprint
================================================================================
