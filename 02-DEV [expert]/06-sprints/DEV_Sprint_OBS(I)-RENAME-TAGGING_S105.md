================================================================================
OBS → OBSIDIAN Rename & Template-Tagging — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_OBS-RENAME-TAGGING_S105
Tag             : #dev #sprint #obs #obsidian #rename #tagging #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : IN ARBEIT
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================

---
title: "OBS → OBSIDIAN Rename & Template-Tagging"
stage: S105
status: "IN ARBEIT"
typ: "Sprint"
datum: "2026-04-14"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, obs, obsidian, rename, tagging, s105]
---

================================================================================
OBS → OBSIDIAN Rename & Template-Tagging — SPRINT (DEV)
Stage S105 | IN ARBEIT | R+MUNI Blueprint
================================================================================

---

## Kontext

Das Kürzel `OBS` ist im R+MUNI-System doppelt belegt:
- `OBS_*` Dokumente → Obsidian (Visualisierungs- und Navigationswerkzeug)
- `OBS` im Betriebskontext → OBS Studio (Streaming/Recording-Tool, explizit
  in FREEZE_1_04 Kap. 4 und STAGE105_ZIELE_S105 Kap. 4 erwähnt)

Der Konflikt führt in der Praxis zu wiederholter Verwechslung beim Laden
von Dokumenten aus dem Project Knowledge. Das Kürzel `OBS` triggert
OBS-Studio-Assoziationen bevor der Inhalt sichtbar ist.

Zweiter Gegenstand dieses Sprints: Das Frontmatter-Schema der OBS How2
enthält keinen Typ und kein Tag für Templates. Template-Dokumente sind
im Obsidian Graph-View nicht von regulären Dokumenten unterscheidbar —
kein `tag:#template`-Filter möglich.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                  normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]       operative Arbeitsmethode
- [[naming_and_structure_S104]]            Namenskonvention — verbindliche Basis
- [[OBS_How2_DEV_S8]]                      betroffenes Dokument (Umbenennung + Erweiterung)
- [[OBS_principles_Associate_S8]]          betroffenes Dokument (Umbenennung)
- [[TMP_principles_S105]]                  Dokumenttypen-Referenz (typ: Template)
- [[FREEZE_1_04]]                          Nachweis Doppelbelegung OBS
- [[STAGE105_ZIELE_S105]]                  Sprint gehört zu Z5 (Kleinere Carry-over)
- [[structure_R_MUNI_normal_]]             Quelle der Wahrheit — Dateinamen


================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Strukturbereinigung
Beschreibung: Namenskonflikt `OBS` (Obsidian vs. OBS Studio) führt zu
              wiederholter Verwechslung. Zusätzlich fehlt im bestehenden
              Frontmatter-Schema ein Mechanismus um Template-Dokumente
              im Obsidian Graph-View gezielt filtern zu können.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:       1. Alle `OBS_*` Dokumente auf `OBSIDIAN_*` umbenennen —
               Kürzel eindeutig, kein Konflikt mit OBS Studio.
            2. Frontmatter-Schema in OBS How2 (neu: OBSIDIAN How2) um
               `typ: Template` und `tags: [..., template]` erweitern —
               Templates im Graph-View filterbar.
            3. structure_R_MUNI_normal_.txt mit neuen Dateinamen
               synchronisieren.
            4. Alle [[Links]] auf OBS_* in betroffenen Dokumenten
               auf OBSIDIAN_* nachziehen.
            5. Beide Dokumente auf S105 heben (Header, Stage, Datum,
               Footer, FREEZE-Link, STAGE-Link).

Abgrenzung: Kein Eingriff in Obsidian-Inhalt (Kapitel, Flows, Prinzipien).
            Kein Rename weiterer Kürzel.
            Kein GOV-Authoring.
            OBS Studio Dokumente / Betriebskontext bleiben unberührt.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  - OBS_How2_DEV_S8.md         → Stage S8, Kürzel OBS, kein Template-Tag-Schema
  - OBS_principles_Associate_S8.md → Stage S8, Kürzel OBS, kein Ablageort-Feld
  - structure_R_MUNI_normal_.txt enthält beide Dateien unter OBS_* Namen
  - Frontmatter-Schema kennt keinen Wert `typ: Template`
  - Kein `#template`-Tag definiert → kein Graph-View-Filter möglich
  - [[Links]] in mehreren Dokumenten zeigen auf OBS_How2_DEV_S6 (veraltet)

Soll-Zustand nach dem Sprint:
  - OBSIDIAN_How2_DEV_S105.md        vorhanden, S105-konform
  - OBSIDIAN_principles_Associate_S105.md  vorhanden, S105-konform
  - structure_R_MUNI_normal_.txt aktualisiert
  - Frontmatter-Schema dokumentiert: typ: Template + tags: [..., template]
  - Alle bekannten [[Links]] auf neue Namen aktualisiert
  - Sprint-Doku abgeschlossen und abgelegt


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle:               DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 Umbenennung OBS → OBSIDIAN
--------------------------------

Entschieden: Kürzel `OBSIDIAN` statt `OBS` für alle Obsidian-Dokumente.
Begründung: Eindeutig, kein Konflikt, kein Schema verletzt
            (naming_and_structure: Kürzel frei wählbar).

Neue Dateinamen:
  OBS_How2_DEV_S8.md              → OBSIDIAN_How2_DEV_S105.md
  OBS_principles_Associate_S8.md  → OBSIDIAN_principles_Associate_S105.md

Artefakte:    OBSIDIAN_How2_DEV_S105.md
              OBSIDIAN_principles_Associate_S105.md
              R+MUNI Doku-public\02-how2\
              R+MUNI Doku-public\01-principles\
GOV-Konform:  JA


2.2 S105-Header-Update beider Dokumente
-----------------------------------------

Folgende Header-Felder in beiden Dokumenten korrigiert:

  Dokument        : OBS_* → OBSIDIAN_*_S105
  Tag             : #s8 / #s6 entfernt → #s105, #obs → #obsidian
  Stage           : S8 → S105
  Datum           : 2026-03-26 → 2026-04-14
  Ablageort       : OBS_*_S6.md → OBSIDIAN_*_S105.md
                    (principles: Ablageort-Feld neu hinzugefügt — fehlte)
  Footer          : S6/S8 → S105, Datum aktualisiert
  FREEZE-Link     : [[FREEZE-6]] → [[FREEZE_1_04]]
  STAGE-Link      : [[STAGE6_ZIELE]] → [[STAGE105_ZIELE_S105]]
  Frontmatter     : stage: S6 → S105, tags: s6 → s105

Artefakte:    siehe 2.1
GOV-Konform:  JA


2.3 Frontmatter-Schema — Template-Tagging
------------------------------------------

Erweiterung des Frontmatter-Schemas in OBSIDIAN_How2_DEV_S105.md:

  Neu dokumentierter Wert für `typ`:
    Template      Template-Dokument — alle *_Template_* Dateien

  Neues Pflicht-Tag für Templates:
    template      → ermöglicht tag:#template Filter im Graph-View

  Erweitertes Frontmatter-Beispiel für Template-Dokumente:
    ---
    title: "<Dokumenttitel>"
    stage: S105
    status: "<ENTWURF / AKTIV / ARCHIV>"
    typ: "Template"
    datum: "<YYYY-MM-DD>"
    autor: EUMAXL
    tags: [rmuni, blueprint, s105, template]
    ---

  Optional — Reihen-Filter:
    reihe: <kürzel>   → ermöglicht path-unabhängige Suche nach Reihe
    Beispiel: reihe: csv → alle CSV-Dokumente filterbar
    Status: dokumentiert als optional, kein Pflichtfeld

Artefakte:    OBSIDIAN_How2_DEV_S105.md (Kapitel FRONTMATTER – KONVENTION)
GOV-Konform:  JA


2.4 Cross-Reference Update
----------------------------

Bekannte [[Links]] die auf OBS_* zeigen und nachgezogen werden müssen:

  In OBSIDIAN_principles_Associate_S105.md (intern):
    [[OBS_How2_DEV_S6]]    → [[OBSIDIAN_How2_DEV_S105]]
    [[TMP_principles_S6]]  → [[TMP_principles_S105]]

  In OBSIDIAN_How2_DEV_S105.md (intern):
    [[FREEZE-6]]           → [[FREEZE_1_04]]
    [[STAGE6_ZIELE]]       → [[STAGE105_ZIELE_S105]]
    [[DUMMY_Blueprint_MD_Obsidian_S8]] → bleibt bis Cleaning Run
                             (Dokument existiert, kein roter Link)

  Weitere Dokumente die auf OBS_* verlinken:
    → Cleaning Run S105 (Z5 Associate Cleaning Run) prüft vollständig.
      Kein eigener Sprint erforderlich — gehört zum laufenden Carry-over.

Artefakte:    kein Artefakt — Links in den Dokumenten direkt korrigiert
GOV-Konform:  JA


2.5 structure_R_MUNI_normal_.txt Update
-----------------------------------------

Folgende Einträge zu aktualisieren:

  01-principles\:
    OBS_principles_Associate_S8.md  → OBSIDIAN_principles_Associate_S105.md

  02-how2\:
    OBS_How2_Associate_S8.md        → OBSIDIAN_How2_Associate_S105.md

  Hinweis: structure_R_MUNI_normal_.txt ist vom User zu pflegen —
           kein Script-Output, manuelle Anpassung durch EUMAXL.

Artefakte:    structure_R_MUNI_normal_.txt (manuell durch EUMAXL)
GOV-Konform:  JA — structure ist User-gepflegte Quelle der Wahrheit


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Kürzel OBSIDIAN statt OBS
  Auslöser:    Namenskonflikt mit OBS Studio — doppelte Belegung im selben
               Projekt-Kontext (FREEZE_1_04 Kap. 4, STAGE105 Kap. 4)
  Ergebnis:    Reihen-Kürzel für Obsidian-Dokumente ist ab S105 OBSIDIAN
  Begründung:  Eindeutig, kein Konflikt, naming_and_structure erlaubt
               freie Kürzelwahl. Längeres Kürzel vertretbar — Verwechslung
               kostet mehr als Länge.
  GOV-Bezug:   GOV 1.4 (Eindeutigkeit), naming_and_structure_S104 Kap. 4.1
  Auswirkung:  Alle künftigen Obsidian-Dokumente tragen Kürzel OBSIDIAN_.
               Bestehende OBS_* Dokumente gelten als deprecated.
  Rückwirkung: NEIN — alte Dateien werden im Cleaning Run bereinigt,
               kein rückwirkender Eingriff in bereits freigegebene Stände.

Entscheidung: Template-Tagging als Erweiterung How2 — kein eigenes Dokument
  Auslöser:    Fehlender Filtermechanismus für Templates im Graph-View
  Ergebnis:    typ: Template + tags: [..., template] als dokumentiertes
               Schema in OBSIDIAN_How2_DEV_S105.md
  Begründung:  Kein eigener Dokumenttyp nötig — bestehende Frontmatter-
               Konvention erweitern ist ausreichend und GOV-konform.
               TMP_principles_S105 kennt Template als Typ bereits — Konsistenz.
  GOV-Bezug:   GOV 1.4, TMP_principles_S105 Kap. 6
  Auswirkung:  Templates sind ab sofort mit tag:#template filterbar.
               Reihen-Filter (reihe:) optional dokumentiert.
  Rückwirkung: NEIN — bestehende Templates ohne Tag bleiben gültig bis
               Cleaning Run.

Entscheidung: DEV-Freigabe durch EUMAXL für diesen Sprint
  Auslöser:    Claude-Intervention bei Umbenennung — Scope-Abklärung
  Ergebnis:    Freigabe erteilt, Sprint eröffnet
  Begründung:  Umbenennung berührt structure.txt und Cross-Links —
               kein trivialer Inline-Fix, Sprint-Doku GOV-konform erforderlich.
  GOV-Bezug:   GOV 7.3, 7.6
  Auswirkung:  Sprint läuft unter S105, gehört zu Z5
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Sprint-Eröffnung ohne vorherigen Backlog-Eintrag
  GOV-Regel:   GOV 7.3 — Sprint setzt definierten Auslöser voraus,
               üblicherweise aus Backlog oder explizitem Ziel
  Begründung:  Thema ist organisch aus laufender Pfadprüfungs-Session
               entstanden. EUMAXL hat DEV-Freigabe direkt erteilt.
               Sprint-Doku wird sofort erstellt — keine nachträgliche
               Rekonstruktion erforderlich.
  Wirkung:     Auf diese Session begrenzt. Kein Präzedenzfall.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Scope-Expansion erkannt — Freigabe eingeholt.
  Ausgangspunkt war Pfadprüfung OBS_How2 + OBS_principles gegen
  PROMPT_pfad_pruefung. Während der Analyse wurde erkannt dass
  Umbenennung structure.txt und Cross-Links berührt — kein Inline-Fix.
  Vor Umsetzung Sprint-Doku vorgeschlagen und DEV-Freigabe eingeholt.

⚠ Verhaltenshinweis: Namenskonflikt OBS/OBS Studio identifiziert.
  Konflikt war nicht explizit vom User benannt. Claude hat ihn aus
  FREEZE_1_04 und STAGE105_ZIELE selbstständig abgeleitet nach
  Einlesen der Dokumente. Intervention vor Umbenennung war korrekt.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| structure_R_MUNI_normal_.txt manuell aktualisieren | naming_and_structure Kap. 2 | offen | EUMAXL manuell nach Dateiumbenennung |
| Weitere OBS_*-Links in anderen Dokumenten prüfen | GOV 1.4 | offen | im laufenden Associate Cleaning Run S105 (Z5) |
| DUMMY_Blueprint_MD_Obsidian_S8 Link in How2 | — | offen | bleibt bis Cleaning Run — kein roter Link |
| Optionales reihe:-Feld in bestehenden Dokumenten nachtragen | — | offen | nach Kapazität, kein Pflichtfeld |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          NEIN — offen: 2.5 structure manuell durch EUMAXL
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               AUSSTEHEND — nach Dateiumbenennung durch EUMAXL
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Einlesen FREEZE + STAGE-Ziele vor Intervention — Namenskonflikt
    wurde dadurch aus dem Dokument selbst nachgewiesen, nicht nur vermutet.
  - Scope-Abgrenzung vor Sprint-Start — Template-Tagging und Rename
    als zwei saubere Ergebnisse statt vermischter Inline-Änderungen.

Was beim nächsten Mal anders gemacht werden sollte:
  - OBS-Konfusion wäre mit OBSIDIAN-Kürzel von Anfang an vermieden worden.
    Kürzel-Wahl bei neuen Reihen: Eindeutigkeit vor Kürze prüfen.

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Kürzel-Eindeutigkeitsprüfung bei Reihen-Eröffnung → Backlog-Hinweis
    für naming_and_structure S106: explizite Regel ergänzen.
    Sprint / Backlog anlegen: NEIN — nach Kapazität in naming_and_structure
    beim nächsten regulären Update mitgeben.

---

## Bezüge

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[naming_and_structure_S104]]              Namenskonvention
[[OBS_How2_DEV_S8]]                        Ausgangsdokument (deprecated nach Sprint)
[[OBS_principles_Associate_S8]]            Ausgangsdokument (deprecated nach Sprint)
[[OBSIDIAN_How2_DEV_S105]]                 Zieldokument (nach Umbenennung)
[[OBSIDIAN_principles_Associate_S105]]     Zieldokument (nach Umbenennung)
[[FREEZE_1_04]]                            Nachweis Doppelbelegung OBS
[[STAGE105_ZIELE_S105]]                    Z5 — Kleinere Carry-over

---

================================================================================
OBS → OBSIDIAN Rename & Template-Tagging — SPRINT (DEV) | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
