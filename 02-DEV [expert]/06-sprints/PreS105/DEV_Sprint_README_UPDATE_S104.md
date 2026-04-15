================================================================================
README.md Update — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_README_UPDATE_S104
Tag             : #dev #sprint #readme #aussenwirkung #s104
Datum           : 2026-04-12
Stage           : S104 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-12
Jira-Sync       : NEIN
================================================================================

---
title: "README.md Update"
stage: S104
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-12"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, readme, aussenwirkung, s104]
---

================================================================================
README.md Update — SPRINT (DEV)
Stage S104 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Sprint zur finalen Aktualisierung der README.md auf S104-Stand.
Direkter Folge-Sprint zu DEV_Sprint_README_INSTALL_UMBAU_S104 — der vorherige
Sprint hatte den Umbau auf vier-Säulen-Struktur geplant und SVG-Inhalte
geliefert, wurde jedoch bei 75% Context-Verbrauch manuell durch EUMAXL
abgebrochen. Die SVGs wurden in einer separaten Session durch EUMAXL erstellt
und abgelegt.

Dieser Sprint schließt das offene Deliverable Z1 (README auf neues Narrativ)
aus STAGE104_ZIELE_S104 ab.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                  normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]       operative Arbeitsmethode
- [[STAGE104_ZIELE_S104]]                  Stage-Ziele — Z1 Außenwirkung, Z3 Release
- [[DEV_Sprint_README_INSTALL_UMBAU_S104]] Vorgänger-Sprint — Umbau-Planung
- [[DEV_Sprint_INSTALLTXT_UPDATE_S104]]    Parallel-Sprint — Install.txt + Narrativ

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Feature-Zuwachs / Strukturbereinigung
Beschreibung: README.md war nach dem abgebrochenen Vorgänger-Sprint noch auf
              altem Stand. SVGs lagen fertig vor (EUMAXL, Folge-Session).
              Neues Narrativ aus DEV_Sprint_INSTALLTXT_UPDATE_S104 und
              STAGE104_ZIELE_S104 Z1 musste in die README einfließen.
              Claude-Bezug war aus Außenwirkungsdokumenten zu entfernen.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         README.md auf vier-Säulen-Struktur umbauen. Alle sechs SVGs
              mit korrekten Pfaden einbinden. Neues Narrativ übernehmen.
              Claude-Bezug vollständig entfernen. Persönliche Texte 1:1
              erhalten. Stage-Bezeichnung auf Phase 1.04 aktualisieren.

Abgrenzung:   Kein Eingriff in Scripts, GOV oder andere Dokumente.
              SVG-Erstellung war nicht Teil dieses Sprints — SVGs lagen
              durch EUMAXL bereits fertig vor.
              LinkedIn-Repositionierung ist separates Deliverable (Z1).


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  README.md auf altem Stand (Beta 1.0 — Phase 1.xx).
  Alte Struktur: Tool-Tabelle, Script-Reihen, Toolbaukasten.svg (veraltet).
  Kein Hinweis auf vier Säulen, keine Varianten-SVG, keine optionalen Leistungen.
  Claude explizit als "verlässliche Stütze" genannt — nicht GOV-konform für
  Außenwirkungsdokumente (STAGE104 Z1, DEV_Sprint_INSTALLTXT S104 Entscheidung).
  Footer: "Beta 1.0 — Phase 1.xx" — veraltet.
  SVG-Platzhalter aus Vorgänger-Sprint nicht eingebaut.

Soll-Zustand nach dem Sprint:
  README.md mit vier-Säulen-Struktur.
  Alle sechs SVGs eingebunden:
    4_Beine_S104.svg         → Vier Säulen
    toolbaukasten_S104.svg   → Toolbaukasten Übersicht
    munidell_tabelle_S104.svg → Tool-Tabelle
    3_4__variantenS104.svg   → Varianten
    Leistungen_S104.svg      → Optionale Leistungen
    munidell_ki_empfehlung_S104.svg → (offen — kein Platz definiert)
  Kein Claude-Bezug, kein KI-Tool-Name in Außenwirkungstext.
  Footer: "Beta — Phase 1.04".
  Persönliche Texte (Dank, Archi, Ehrlichkeit) 1:1 erhalten.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 README.md — vollständige Überarbeitung
-------------------------------------------

Neue Struktur auf Basis der vier Säulen. Alle relevanten SVGs mit korrektem
Pfad eingebunden: `99-doku/images/svg claude/<dateiname>`.

Strukturelle Änderungen:
  - Einstiegssatz auf vier Vorgehensweisen gekürzt (aus Vorgänger-Sprint)
  - Abschnitt "Die vier Säulen" neu — mit 4_Beine_S104.svg + Kurzbeschreibung
  - Tool-Tabelle ersetzt durch munidell_tabelle_S104.svg + toolbaukasten_S104.svg
  - Script-Reihen-Tabelle bleibt textlich erhalten
  - Varianten-Abschnitt mit 3_4__variantenS104.svg
  - Neuer Abschnitt "Optionale Leistungen" mit Leistungen_S104.svg + Tabelle
  - Claude-Bezug vollständig entfernt — auch aus "Ehrlichkeit zuerst"
  - Footer: "Beta — Phase 1.04"
  - Persönliche Texte 1:1 erhalten

Artefakte:    README.md (Chat-Output, Review durch EUMAXL, Ablage durch EUMAXL)
GOV-Konform:  JA


2.2 Offener Punkt — munidell_ki_empfehlung_S104.svg
-----------------------------------------------------

Die SVG munidell_ki_empfehlung_S104.svg wurde von EUMAXL hochgeladen,
jedoch ohne Angabe einer Zielposition in der README. Sie wurde nicht
eingebunden. Einbindung durch EUMAXL nach eigenem Entscheid.

Artefakte:    kein Artefakt — offener Punkt dokumentiert (siehe Kap. 6)
GOV-Konform:  JA — keine Annahme ohne explizite Information (GOV 1.4)


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Claude-Bezug vollständig entfernen
  Auslöser:    EUMAXL explizit: "Claude Bezug bitte entfernen — du bist ein
               Arbeitsverhinderer geworden solange das so ist bleibst du raus
               aus der Doku bis auf das nötigste"
  Ergebnis:    Alle namentlichen Claude-Bezüge aus README entfernt.
               Kein KI-Tool-Name in Außenwirkungstext.
               "AI-driven entwickelt" bleibt als sachliche Beschreibung.
  Begründung:  STAGE104 Z1 — Außenwirkungsdokumente ohne KI-Tool-Bezug.
               GOV 8.2 — Offenheit. Entscheidung liegt beim Betreiber.
  GOV-Bezug:   STAGE104_ZIELE_S104 Z1; DEV_Sprint_INSTALLTXT_UPDATE_S104
  Auswirkung:  Claude erscheint in README nur noch implizit via Install.txt 3.8
  Rückwirkung: NEIN

Entscheidung: munidell_ki_empfehlung_S104.svg nicht einbinden
  Auslöser:    SVG vorhanden, aber kein Zielabschnitt in README definiert
  Ergebnis:    Nicht eingebunden — offener Punkt für EUMAXL
  Begründung:  Keine Annahme über Ablageort oder Kontext ohne explizite Info
  GOV-Bezug:   GOV 1.4 — Explizitheit als Grundprinzip
  Auswirkung:  EUMAXL entscheidet Einbindung manuell oder in Folge-Sprint
  Rückwirkung: NEIN

Entscheidung: SVG-Pfad-Schema festgelegt
  Auslöser:    EUMAXL: SVGs liegen unter <rootfolder>\99-doku\images\svg claude\
  Ergebnis:    Alle SVG-Links: `99-doku/images/svg claude/<dateiname>`
  Begründung:  Explizite Angabe durch EUMAXL — kein Raten (GOV 1.4)
  GOV-Bezug:   GOV 1.4
  Auswirkung:  Schema gilt für alle weiteren SVG-Einbindungen in README
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Keine Abweichungen


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Vor Generierung der README vier Klärungsfragen gestellt
  (SVG-Platzhalter, Stage-Footer, Toolbaukasten, Claude-Bezug) — korrekt nach
  GOV und AI Driven Methode. EUMAXL hat drei von vier direkt beantwortet,
  eine (munidell_ki_empfehlung) als offenen Punkt belassen.

⚠ Verhaltenshinweis: Session-Kontext war durch vorangehende SVG-Arbeit
  bei ~90% — EUMAXL explizit darauf hingewiesen. Sprint wurde kompakt
  und ohne Overhead durchgeführt.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| munidell_ki_empfehlung_S104.svg einbinden | GOV 1.4 | offen | EUMAXL entscheidet Position + Einbindung manuell |
| SVG-Pfade in README prüfen nach Repo-Sync | GOV 7.9 | offen | EUMAXL nach GitHub-Sync |
| README GitHub-Sync | GOV 7.9 | offen | EUMAXL nach finalem Review |
| LinkedIn Profilüberarbeitung | Z1 S104 | offen | EUMAXL — separater Sprint |
| GitHub Release Deploy | Z3 S104 | offen | nach Repo-Entscheid (Z2) |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               NEIN — Ablage durch EUMAXL
GitHub-Sync:                      AUSSTEHEND — EUMAXL entscheidet Zeitpunkt
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Klärungsfragen vor der Generierung haben Annahmen vermieden
  - Offenen Punkt (ki_empfehlung SVG) explizit dokumentiert statt blind platziert
  - Sprint kompakt gehalten trotz knappem Session-Context

Was beim nächsten Mal anders gemacht werden sollte:
  - README-Update früher in der Stage anstoßen — nicht wenn Context bereits
    durch SVG-Arbeit verbraucht ist

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Keine — Sprint folgt bestehenden Regeln ohne neue Erkenntnis

---

## Bezüge

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[STAGE104_ZIELE_S104]]                    Stage-Rahmen
[[DEV_Sprint_README_INSTALL_UMBAU_S104]]   Vorgänger-Sprint
[[DEV_Sprint_INSTALLTXT_UPDATE_S104]]      Parallel-Sprint Narrativ

---

================================================================================
README.md Update — SPRINT (DEV) | S104 | 2026-04-12 | R+MUNI Blueprint
================================================================================
