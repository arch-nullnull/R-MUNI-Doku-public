================================================================================
CLAUDE EXIT SZENARIO — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_Claude-Exit_S10nc
Tag             : #dev #sprint #claudeexit #s10nc
Datum           : 2026-04-06
Stage           : S1.02 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-06
Jira-Sync       : NEIN
================================================================================

---
title: "Claude Exit Szenario — Sprint (DEV)"
stage: S1.02
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-06"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, claudeexit, s10nc]
---

================================================================================
CLAUDE EXIT SZENARIO — SPRINT (DEV)
Stage S1.02 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Alle Blueprint-Dokumente enthielten direkte und indirekte Hinweise auf das
bisher eingesetzte KI-Tool beim Namen — als Eigenname, in Verhaltensbeschreibungen,
in Rollendefinitionen und in Methodik-Abschnitten.

Ziel dieses Sprints ist die vollständige Neutralisierung aller solcher Hinweise.
Das Blueprint-System soll herstellerunabhängig und werkzeugagnostisch formuliert sein.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S10nc]]                normative Grundlage (neutralisiert)
- [[AI_DRIVEN_DEV_METHODE_DEV_S10nc]]     operative Arbeitsmethode (neutralisiert)
- [[naming_and_structure_S10nc]]          Ablagestruktur (neutralisiert)
- [[DEV_Sprint_Template_S10nc]]           Sprint-Template (neutralisiert)

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------
Auslöser:     Fehlerbehebung
Beschreibung: Nach Hotfixes des eingesetzten KI-Tools trat verändertes
              Nutzungsverhalten sowie Drift-Verhalten auf, das die aktive
              Entwicklung über mehrere Tage vollständig blockiert hat.
              Der Fehler liegt nicht beim Entwickler — er liegt im veränderten
              Verhalten des Werkzeugs nach externen Änderungen durch den Hersteller.
              Konsequenz: Vollständige Neutralisierung aller Eigennamen-Bezüge
              in den Blueprint-Dokumenten als strukturelle Fehlerbehebung.
              Ziel: Tool-Lock-Schutz, Herstellerunabhängigkeit, Entwicklungsstabilität.


1.2 Zieldefinition (GOV 7.6)
------------------------------
Ziel:         Alle Dokumente der S1.02-Reihe werden auf S10nc neu ausgegeben.
              Jeder direkte oder indirekte Hinweis auf das KI-Tool beim
              Eigennamen ist ersetzt durch neutrale Begriffe.
              Das Ergebnis ist herstellerunabhängig lesbar.

Abgrenzung:   Kein inhaltlicher Eingriff in GOV-Logik, Methodik oder
              Integrationsregeln. Connectoren, Atlassian-Bezüge und
              technische Integrationen bleiben unverändert.
              Keine Änderung an Suffix-Logik oder Stage-Modell.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  Alle S102-Dokumente enthalten den Eigennamen des KI-Tools als direkten
  Verweis — in Rollenbeschreibungen, Verhaltensregeln, Methodik-Kapiteln,
  Kontextmanagement und Sprint-Templates.

Soll-Zustand nach dem Sprint:
  Alle S10nc-Dokumente sind vollständig neutralisiert.
  Ersatzterminologie: "KI-Tool" für das Werkzeug, "das KI-Tool" in
  Verhaltensbeschreibungen, passive oder werkzeugagnostische Formulierungen
  wo sinnvoll.


1.4 Rolle (AI Driven Kap. 10)
------------------------------
Aktive Rolle:                DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 AI_DRIVEN_DEV_METHODE_DEV_S10nc.md
----------------------------------------
Vollständige Neutralisierung aller Eigennamen-Bezüge in der Methodik.
Betroffen: Kap. 4 (Session-Ablauf), Kap. 5 (Kommunikation), Kap. 13
(Verhaltenstransparenz), Kap. 14 (KI-Tool-Rollentrennung), Kap. 15 (Namensregel).

Artefakte:    AI_DRIVEN_DEV_METHODE_DEV_S10nc.md
GOV-Konform:  JA


2.2 Global_GOV_DEV_S10nc.md
-----------------------------
Neutralisierung der Bezüge in Kap. 7 (Sprints) und allen Verweisen auf
das KI-Tool als benanntes Werkzeug.

Artefakte:    Global_GOV_DEV_S10nc.md
GOV-Konform:  JA


2.3 naming_and_structure_S10nc.md
-----------------------------------
Neutralisierung der Bezüge in Abschnitt zu KI-Werkzeugen und Toolstack-Verweisen.

Artefakte:    naming_and_structure_S10nc.md
GOV-Konform:  JA


2.4 DEV_Sprint_Template_S10nc.md
----------------------------------
Neutralisierung des Verhaltenshinweis-Abschnitts (Kap. 5) im Template.

Artefakte:    DEV_Sprint_Template_S10nc.md
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Ersatzterminologie
  Auslöser:    Neutralisierung erfordert einheitliche Ersatzsprache
  Ergebnis:    "KI-Tool" als primärer Ersatz für den Eigennamen.
               "Das KI-Tool" in Verhaltensbeschreibungen.
               Passive Formulierungen wo werkzeugagnostisch sinnvoller.
  Begründung:  Passt zur bestehenden Denglish-Sprachlogik des Projekts.
               Kurz, eindeutig, herstellerunabhängig.
  GOV-Bezug:   GOV 4.5 (Tool-Unabhängigkeit), GOV 6.11
  Auswirkung:  Alle Folge-Dokumente ab S10nc verwenden diese Terminologie.
  Rückwirkung: NEIN

Entscheidung: Suffix S10nc
  Auslöser:    Neuer Dokumentstand erfordert eigenen Suffix
  Ergebnis:    S10nc kennzeichnet den neutralisierten Stand aller Dokumente
  Begründung:  Nachvollziehbarkeit des Entstehungszeitpunkts (GOV 7.12)
  GOV-Bezug:   GOV 7.12
  Auswirkung:  S10nc-Dokumente ersetzen S102-Dokumente als aktiven Standard
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Keine Abweichungen.
Sprint ist vollständig GOV-konform durchgeführt.


================================================================================
5. VERHALTENSHINWEISE KI-TOOL (AI Driven Kap. 13.1)
================================================================================

Keine Verhaltenshinweise während dieses Sprints.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| FREEZE_1_01.md — historisches Dokument | GOV 7.12 | offen | Entscheidung EUMAXL: neutralisieren oder as-is belassen als historischer Stand |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — S10nc-Reihe vollständig
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Enger Scope — klare Abgrenzung von Anfang an
  - Suffix-Konvention ermöglicht saubere Parallelhaltung alter und neuer Stände

Was beim nächsten Mal anders gemacht werden sollte:
  - Neutralisierung kann als Standard-Checkliste in künftige Templates einfließen

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - GOV 4.5 / 6.11 Tool-Unabhängigkeit wird durch diesen Sprint operativ bestätigt
    → kein neuer Sprint nötig, Erkenntnis dokumentiert

---

## Bezüge

[[Global_GOV_DEV_S10nc]]                  normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S10nc]]       operative Arbeitsmethode

---

================================================================================
CLAUDE EXIT SZENARIO — SPRINT (DEV) | S1.02 | 2026-04-06 | R+MUNI Blueprint
================================================================================
