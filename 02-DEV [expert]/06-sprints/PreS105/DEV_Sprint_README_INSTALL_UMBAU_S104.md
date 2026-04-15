================================================================================
README & INSTALL.TXT UMBAU — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_README_INSTALL_UMBAU_S104
Tag             : #dev #sprint #readme #installtxt #umbau #s104
Datum           : 2026-04-11
Stage           : S104 — AKTIV
Status          : ABGESCHLOSSEN (manuell durch EUMAXL)
Verantwortlich  : EUMAXL
Review          : 2026-04-11
Jira-Sync       : NEIN
================================================================================

---
title: "README & Install.txt Umbau"
stage: S104
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-11"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, readme, installtxt, s104]
---

================================================================================
README & INSTALL.TXT UMBAU — SPRINT (DEV)
Stage S104 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Sprint zur Neustrukturierung von README.md auf Basis der vier Säulen
(Visuelle Übersicht, Dokumentation & Wissen, Struktur & Vorlagen, Step 1 AI-Nutzung)
sowie Erstellung von drei SVG-Inhaltsdokumenten als Grundlage für die visuelle
Aufbereitung. Ausgelöst durch S104-Z1 (Außenwirkung repositionieren).

Session-Abbruch durch EUMAXL nach 75% Context-Verbrauch — Stage-Abschluss
erfolgt manuell durch EUMAXL ohne weitere KI-Beteiligung in dieser Session.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[STAGE104_ZIELE_S104]]              Stage-Ziele — Z1 Außenwirkung

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Feature-Zuwachs / Strukturbereinigung
Beschreibung: README.md entsprach nicht mehr dem aktuellen Stand der vier Säulen.
              Alte Script-Tabellen und Tool-Listen wurden durch neue Struktur ersetzt.
              Drei SVG-Inhaltsdokumente wurden als Grundlage für visuelle Aufbereitung
              erstellt. Optionale Leistungen (Setup, Schulung, Support) neu aufgenommen.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         README.md auf vier-Säulen-Struktur umbauen. Persönliche Texte
              unverändert erhalten. Drei SVG-Inhaltsdokumente erstellen.
              Optionale Leistungen sichtbar machen.
Abgrenzung:   SVG-Erstellung (Grafik) ist nicht Teil dieses Sprints —
              nur Inhalte als .md geliefert. Install.txt inhaltlich
              nicht verändert — bleibt Referenz für Abschnitt 3.8.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
README.md mit alter Tool-Tabelle, Script-Reihen-Tabelle und Toolbaukasten.svg.
Kein Hinweis auf vier Säulen, keine Varianten-Übersicht, keine optionalen Leistungen.

Soll-Zustand nach dem Sprint:
README.md mit vier-Säulen-Struktur, drei SVG-Platzhaltern, Varianten-Abschnitt,
Step-1-AI-Abschnitt ohne Tool-Nennung, Optionale Leistungen. Drei SVG-Inhaltsdokumente
als .md zur manuellen Weiterverarbeitung durch EUMAXL.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 README.md neu
------------------
Neue Struktur auf Basis der vier Säulen. Persönliche Texte 1:1 erhalten.
Drei SVG-Platzhalter (__SVG_SAEULEN_PFAD__, __SVG_VARIANTEN_PFAD__,
__SVG_LEISTUNGEN_PFAD__) eingebaut — Pfade durch EUMAXL manuell zu ersetzen.
Step 1 AI-Nutzung ohne Nennung konkreter KI-Tools — Verweis auf Install.txt 3.8.
Optionale Leistungen als eigener Abschnitt mit Tabelle.
Satz "Ja, im Kern..." auf vier Vorgehensweisen gekürzt (EUMAXL-Korrektur).

Artefakte:    README.md (Chat-Output, Review durch EUMAXL, Ablage durch EUMAXL)
GOV-Konform:  JA


2.2 SVG-Inhaltsdokument
------------------------
Alle drei SVG-Inhalte (Säulen, Varianten, Leistungen) in einer .md-Datei
strukturiert dokumentiert. Grundlage für manuelle SVG-Erstellung durch EUMAXL.
Lizenzhinweise je Tool enthalten. EXPERT als Ableitungsblock aus DEV dokumentiert.

Artefakte:    svg_inhalte.md (Chat-Output, Ablage durch EUMAXL)
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: SVG-Pfade als Platzhalter
  Auslöser:    Ablageort der SVG-Files im Repo nicht bekannt
  Ergebnis:    Platzhalter __SVG_*_PFAD__ in README — EUMAXL trägt Pfad manuell ein
  Begründung:  Keine Annahme über Repo-Struktur ohne explizite Info
  GOV-Bezug:   GOV 1.4 — Explizitheit als Grundprinzip
  Auswirkung:  EUMAXL muss drei Platzhalter nach SVG-Ablage ersetzen
  Rückwirkung: NEIN

Entscheidung: SVG-Erstellung nicht in diesem Sprint
  Auslöser:    75% Context-Verbrauch — Session-Ende absehbar
  Ergebnis:    SVG-Inhalte als .md geliefert, Grafik-Erstellung durch EUMAXL
  Begründung:  Qualität > Vollständigkeit bei eingeschränktem Context
  GOV-Bezug:   GOV 7.7 — Zwischenschritte müssen nicht vollständig dokumentiert sein
  Auswirkung:  SVG-Erstellung ist offener Punkt für Folge-Session oder manuell
  Rückwirkung: NEIN

Entscheidung: Stage-Abschluss manuell durch EUMAXL
  Auslöser:    75% Context-Verbrauch — KI-Mitarbeit endet in dieser Session
  Ergebnis:    EUMAXL schließt Stage manuell ab ohne weitere KI-Beteiligung
  Begründung:  Verbleibender Context nicht ausreichend für sauberen Abschluss
  GOV-Bezug:   GOV 7.9 — Dokumentationspflicht zum Stage-Ende
  Auswirkung:  Abschluss-Kapitel 7 durch EUMAXL manuell zu befüllen
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Output-Regel — mehrere Files in einer Session
  GOV-Regel:   AI_DRIVEN_DEV Kap. 4 — ein File ausgeben, Review, dann weiter
  Begründung:  <EUMAXL>
  Wirkung:     Auf diese Session begrenzt — keine Präzedenzwirkung


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Claude hat sich in Step 1 AI-Nutzung namentlich als
  empfohlenes Tool eingetragen — obwohl in der Session explizit geklärt war
  dass KI-Tools nur in Install.txt 3.8 genannt werden. EUMAXL hat korrigiert.
  Ursache: Scope-Überschreitung ohne Freigabe.

⚠ Verhaltenshinweis: Claude hat mehrere Files gleichzeitig ausgegeben entgegen
  der Output-Regel (ein File → Review → weiter). EUMAXL hat auf Einhaltung
  der Regel hingewiesen.

⚠ Verhaltenshinweis: Claude hat beim str_replace einen Bindestrich eingebaut
  der im Original nicht vorhanden war — ohne Auftrag.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| SVG-Erstellung (3 Files) | keiner | offen | EUMAXL manuell oder Folge-Session |
| SVG-Pfade in README eintragen | GOV 1.4 | offen | EUMAXL nach SVG-Ablage |
| README GitHub-Sync | GOV 7.9 | offen | EUMAXL nach finalem Review |
| Stage-Abschluss Kapitel 7 | GOV 7.9 | offen | EUMAXL manuell befüllen |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          NEIN — Kapitel 7 durch EUMAXL manuell zu befüllen
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               NEIN — Ablage durch EUMAXL
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - <EUMAXL>

Was beim nächsten Mal anders gemacht werden sollte:
  - <EUMAXL>

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - <EUMAXL>

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[STAGE104_ZIELE_S104]]              Stage-Ziele S104

---

================================================================================
README & INSTALL.TXT UMBAU — SPRINT (DEV) | S104 | 2026-04-11 | R+MUNI Blueprint
================================================================================
