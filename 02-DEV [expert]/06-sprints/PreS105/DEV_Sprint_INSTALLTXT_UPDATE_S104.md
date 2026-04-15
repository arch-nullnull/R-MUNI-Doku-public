================================================================================
Install.txt Update & Außenwirkung-Repositionierung — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_INSTALLTXT_UPDATE_S104
Tag             : #dev #sprint #installtxt #aussenwirkung #aiof #s104
Datum           : 2026-04-11
Stage           : S1.04 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-11
Jira-Sync       : NEIN
================================================================================

---
title: "Install.txt Update & Außenwirkung-Repositionierung"
stage: S1.04
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-11"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, installtxt, aussenwirkung, aiof, s104]
---

================================================================================
Install.txt Update & Außenwirkung-Repositionierung — SPRINT (DEV)
Stage S1.04 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Dieser Sprint adressiert zwei eng verknüpfte Themen: die inhaltliche
Aktualisierung der Install.txt auf S104-Stand sowie die daraus resultierende
Neuausrichtung der Außenwirkung von R+MUNI.

Die Install.txt war zuletzt auf Stage 8 / Beta 1.0 Stand (2026-03-28) und
spiegelte weder das neue Tool-Konzept noch den AIOF-Übergang wider.
Gleichzeitig hat Kundenfeedback aus dem Beta-Betrieb klar gezeigt dass die
bisherige Außendarstellung von R+MUNI als "User-Produkt" nicht funktioniert —
und eine Neupositionierung als Open Source Toolset notwendig ist.

Beides gehört zusammen: eine aktuelle Install.txt ist die erste sichtbare
Außenwirkung für jeden der R+MUNI zum ersten Mal lädt.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]     operative Arbeitsmethode
- [[FREEZE_1_03]]                        Ausgangszustand, AIOF-Kontext, offene Punkte
- [[STAGE104_ZIELE_S104]]                Z1 Außenwirkung, Z3 Release / Install.txt Check
- [[BACKLOG_AIOF_DEV_S103]]              AIOF-Kontext und KI-Tool-Empfehlungen

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------
Auslöser:     Feature-Zuwachs + Kundenbedarf + Entwicklerwunsch

Beschreibung: Drei gleichzeitige Auslöser haben diesen Sprint ausgelöst:

  1. AIOF-Übergang (Entwicklerwunsch):
     Mit dem Abschluss von Stage 1.03 und dem formalen Wechsel des KI-Tools
     war der Werkzeugkasten in der Install.txt inhaltlich veraltet.
     Neue Tools (Inkscape, OBS Studio, nmap), neue Tier-Logik und der
     AIOF-KI-Empfehlungsblock mussten eingearbeitet werden.

  2. Kundenfeedback (Kundenbedarf):
     Beta-Kundenfeedback hat ergeben dass R+MUNI von externen Betrachtern
     nicht als das verstanden wird was es ist. Die bisherige Darstellung als
     "Tool für jeden" oder als "User-Produkt" erzeugt Verwirrung.
     Niemand versteht auf Anhieb den Kern: R+MUNI ist ein Open Source Toolset
     das es ermöglicht Warum, Was, Wohin, Wer, Wie und Womit einer
     Organisation strukturiert abzubilden — ohne Lizenzkosten, ohne
     Datenbankserver, ohne Vendor Lock-in.

  3. Stage-104-Ziel Z3 (Feature-Zuwachs):
     Install.txt finaler Check aus CARD-Benutzerperspektive war explizites
     Deliverable in STAGE104_ZIELE_S104.md.


1.2 Zieldefinition (GOV 7.6)
------------------------------
Ziel:         Install.txt auf S104-Stand bringen — inhaltlich korrekt,
              strukturell neu, lizenzrechtlich sauber, CARD-tauglich.
              Außenwirkung auf neues Narrativ ausrichten:
              R+MUNI als Open Source Toolset — nicht als User-Produkt.

Abgrenzung:   Dieser Sprint ändert keine Scripts, keine Modelle und keine
              GOV-Dokumente. Er ändert ausschließlich die Install.txt.
              README-Anpassung ist separates Deliverable (Z1 noch offen).
              LinkedIn-Repositionierung ist separates Deliverable (Z1).


1.3 Ausgangslage
-----------------
Ist-Zustand vor dem Sprint:
  Install.txt auf Stage 8 / Beta 1.0 Stand (2026-03-28).
  Alte 3-Tier-Logik: Minimal → Default → Addon.
  Kein AIOF-Block, kein KI-Toolset, keine Lizenzangaben.
  Fehlende Tools: Inkscape, OBS Studio, nmap.
  Veralteter KI-Abschnitt: Claude als "empfohlen" — nach Tool-Wechsel falsch.
  GitHub-Links unvollständig und ohne .git Suffix.
  Schnellstart veraltet — kein Varianten-Konzept, kein Doku-Repo-Link.
  Außenwirkung: R+MUNI positioniert als generisches "Tool für jeden".

Soll-Zustand nach dem Sprint:
  Install.txt auf S104-Stand.
  Neue 5-Stufen-Logik: Struktur & Vorlagen → Visuelle Übersicht →
    Dokumentation → KI-Einstieg → Addon.
  AIOF-KI-Empfehlungsblock mit allen Kandidaten inkl. Claude sachlich.
  Alle Tools mit korrekten GitHub/Projekt-Links und verifizierten Lizenzen.
  Schnellstart neu: 10 Schritte, Varianten-Auswahl, Release-Link, Doku-Link.
  Kostenfreiheit explizit kommuniziert (Addons ausgenommen).
  Außenwirkung: R+MUNI als Open Source Toolset — klar, ohne Fachbegriff-Overload.


1.4 Rolle (AI Driven Kap. 10)
------------------------------
Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 Install.txt — vollständige Überarbeitung
---------------------------------------------
Die Install.txt wurde von Grund auf neu strukturiert und inhaltlich auf
S104-Stand gebracht. Alle Änderungen wurden chirurgisch via str_replace
eingearbeitet — kein Neuschreiben ohne Freigabe.

Strukturelle Änderungen:
  - Alte 3-Tier-Logik ersetzt durch neue 5-Stufen-Logik
  - Schnellstart: 6 Schritte → 10 Schritte mit Varianten-Auswahl
  - Kostenfreiheits-Aussage prominent im Schnellstart verankert
  - Obsidian: nur noch Vault für 99-doku (nicht mehr mehrere Vaults)
  - GitHub Desktop: Sync-Übersicht auf kundenrelevante Repos reduziert
    (DEV-Repos raus — gehören nicht in die Install.txt)
  - PowerShell 7: von Addon zu Struktur & Vorlagen verschoben
  - KI-Toolset: aus Hauptbereich in Addon verschoben
  - Git: aus Default-Bereich in Claude-Addon-Block verschoben

Neue Inhalte:
  - Inkscape (GPL v2+) unter Visuelle Übersicht
  - nmap (NPSL) als Unterabschnitt Python / NBX-Abhängigkeit
  - OBS Studio (GPL v2) als Addon — Remote Streaming
  - LibreOffice (MPL 2.0) als Addon — Alternative Office-Lösung
  - Camunda 8 als Addon — Exitpoint für Enterprise BPMN
  - KI-Toolset Addon: Claude, ChatGPT Pro, Gemini Advanced,
    Copilot Pro, Ollama mit Kosten und Stärken
  - KI-Kalibrierung als eigener Addon-Abschnitt
  - 2FA-Hinweis für GitHub bei KeePass

Lizenz- und Link-Bereinigung:
  Alle Tools mit verifizierten Lizenzen und bevorzugten GitHub-Links:
    Archi         MIT           github.com/archimatetool/archi/releases
    GitHub Desktop MIT          github.com/desktop/desktop/releases
    PowerShell    MIT           github.com/PowerShell/PowerShell/releases
    VS Code       MIT           github.com/microsoft/vscode/releases
    Notepad++     GPL v2        github.com/notepad-plus-plus/notepad-plus-plus/releases
    Git           GPL v2        github.com/git/git/releases
    OBS Studio    GPL v2        github.com/obsproject/obs-studio/releases
    KeePass       GPL v2        keepass.info/download.html
    Inkscape      GPL v2+       gitlab.com/inkscape/inkscape/-/releases
    OpenJDK       GPLv2+CE      adoptium.net/de/
    nmap          NPSL          github.com/nmap/nmap
    Python        PSF License   github.com/python/cpython/releases
    Camunda       Apache 2.0    github.com/camunda/camunda-modeler/releases
    draw.io       Apache 2.0    github.com/jgraph/drawio-desktop/releases
    LibreOffice   MPL 2.0       libreoffice.org/download/download-libreoffice/
    Obsidian      proprietär    obsidian.md

Artefakte:    Install.txt — Blueprint Root
GOV-Konform:  JA


2.2 Außenwirkung-Repositionierung — Entscheidung und Begründung
----------------------------------------------------------------
Im Zuge dieses Sprints wurde die Notwendigkeit einer grundlegenden
Repositionierung der R+MUNI-Außenwirkung formell dokumentiert.

Ausgangspunkt war ein konsistentes Signal aus dem Beta-Kundenfeedback:
Keiner der Beta-Kunden hat R+MUNI beim ersten Kontakt als das verstanden
was es ist. Die bisherige Sprache ("Tool für jeden", "Blueprint-System",
"EA-Werkzeugkasten") erzeugt Verwirrung statt Klarheit.

Das neue Narrativ:
  R+MUNI ist ein Open Source Toolset — kein User-Produkt, kein SaaS,
  keine App die man einfach installiert und benutzt.
  Es ist eine strukturierte Methodik mit Werkzeugen die es ermöglichen,
  die sechs Grundfragen einer Organisation klar abzubilden:

    Warum    — Motivation, Strategie, Ziele
    Was      — Fähigkeiten, Funktionen, Produkte
    Wohin    — Architektur, Zukunftsbild, Roadmap
    Wer      — Rollen, Teams, Verantwortlichkeiten
    Wie      — Prozesse, Abläufe, Methoden
    Womit    — Systeme, Tools, Infrastruktur

  Wer R+MUNI nutzt, bringt sein eigenes Domänenwissen mit.
  R+MUNI liefert die Struktur, die Sprache (ArchiMate, BPMN) und
  die Werkzeuge um dieses Wissen nachvollziehbar und auditfähig
  zu machen — ohne Vendor Lock-in, ohne Lizenzkosten.

Diese Repositionierung betrifft:
  - Install.txt: Struktur und Sprache bereits angepasst (dieser Sprint)
  - README.md: Narrativ-Anpassung ausstehend (Z1 — separater Sprint)
  - LinkedIn: Profilüberarbeitung ausstehend (Z1)
  - CARD-Bereich: öffentlicher Einstieg muss neues Narrativ transportieren

Artefakte:    kein separates Artefakt — Entscheidung in diesem Sprint
              dokumentiert, Umsetzung läuft in Z1-Sprints weiter
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Neue Tier-Logik für Install.txt
  Auslöser:    Alte Minimal/Default/Addon-Logik passte nicht mehr zum
               tatsächlichen Nutzungsweg und zur neuen Tool-Landschaft
  Ergebnis:    5-Stufen-Logik: Struktur & Vorlagen → Visuelle Übersicht →
               Dokumentation → KI-Einstieg → Addon
  Begründung:  Spiegelt den tatsächlichen Installations- und Nutzungsweg
               wider — von der Basis (Sync, Versionierung) über die
               Modellierung bis zur KI-Unterstützung
  GOV-Bezug:   GOV 1.4 — Explizitheit als Grundprinzip
  Auswirkung:  Alle zukünftigen Install.txt-Erweiterungen folgen dieser Logik
  Rückwirkung: NEIN

Entscheidung: Claude in KI-Toolset nicht verschweigen
  Auslöser:    Claude war primäres KI-Tool — vollständiges Weglassen wäre
               inhaltlich inkorrekt und GOV-widrig (implizite Auslassung)
  Ergebnis:    Claude als erster Eintrag im KI-Toolset, sachlich mit allen
               Plänen (Pro $20, Max 5x $100, Max 20x $200), Kontingent-
               Empfehlung Pro + €15 Reserve, und explizitem Hinweis auf
               mögliche Verrechnungsmodell-Änderungen
  Begründung:  Offenheit und Ehrlichkeit als nicht verhandelbare Grundhaltung
               (GOV 8.2). Kein Tool wird bevorzugt oder benachteiligt.
  GOV-Bezug:   GOV 8.2 — Grundhaltung gegenüber Usern
  Auswirkung:  Install.txt bleibt tool-agnostisch im Narrativ,
               aber vollständig in den Fakten
  Rückwirkung: NEIN

Entscheidung: GitHub Sync-Übersicht auf Kunden-Repos reduzieren
  Auslöser:    DEV-Repos (R-MUNI, R-MUNI-Doku-public) gehören nicht in
               eine Installations-Anleitung für Kunden und User
  Ergebnis:    Nur R+MUNI <Kundenkürzel>\ und R+MUNI Archiv <Kundenkürzel>\
               in der Sync-Übersicht — DEV-Repos entfernt
  Begründung:  Zwei-Welten-Prinzip (GOV / FREEZE 11): INTERN und PUBLIC
               strikt getrennt — DEV-Repos sind INTERN
  GOV-Bezug:   FREEZE_1_03 Kap. 11 — Zwei-Welten-Prinzip
  Auswirkung:  Klarere Trennung für Kunden und User sichtbar
  Rückwirkung: NEIN

Entscheidung: Außenwirkung-Repositionierung — neues Narrativ
  Auslöser:    Kundenfeedback: "keiner versteht es als User-Produkt"
               AIOF-Übergang: Chance zur Neupositionierung ohne alten Ballast
  Ergebnis:    R+MUNI wird als Open Source Toolset positioniert das die
               sechs Grundfragen (Warum/Was/Wohin/Wer/Wie/Womit) abbildet —
               nicht als fertiges User-Produkt
  Begründung:  Das bisherige Narrativ hat bei keinem Beta-Kunden funktioniert.
               Die tatsächliche Stärke von R+MUNI liegt nicht im
               "einfach benutzen" sondern im strukturierten Denken das es
               ermöglicht. Das neue Narrativ kommuniziert genau das.
  GOV-Bezug:   STAGE104_ZIELE_S104 Z1 — Außenwirkung repositionieren;
               GOV 8.2 — Offenheit und Ehrlichkeit
  Auswirkung:  README, LinkedIn und CARD-Bereich folgen in separaten Sprints.
               Install.txt bereits angepasst.
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Keine Abweichungen


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Mehrfach Annahmen getroffen statt nachgefragt —
  z.B. beim ersten Interpretationsversuch des "neuen Konzepts". Korrigiert
  nach explizitem Feedback von EUMAXL.

⚠ Verhaltenshinweis: Beim ersten Entwurf der neuen Konzept-Interpretation
  zu viel aus dem STAGE104-Dokument abgeleitet ohne Rückfrage.
  EUMAXL hat klar gestellt dass Install.txt varianten-unabhängig ist.

⚠ Verhaltenshinweis: Abschnittsnummern nach mehreren str_replace-Operationen
  kurzzeitig inkonsistent — selbst erkannt und korrigiert.

⚠ Verhaltenshinweis: Vor Lizenz-Einarbeitung Rückfrage ob Suche notwendig —
  korrekt, da Lizenzen nicht aus Trainingsdaten angenommen werden dürfen.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| README Narrativ-Anpassung auf neues Außenwirkungskonzept | Z1 S104 | offen | separater Sprint Z1 |
| LinkedIn Profilüberarbeitung | Z1 S104 | offen | EUMAXL — nach README |
| CARD-Bereich öffentlicher Einstieg mit neuem Narrativ | Z2 S104 | offen | nach Repo-Entscheid |
| GitHub Release Deploy v1.0 | Z3 S104 | offen | nach README + Narrativ |
| INST_principles_S104.md erstellen | Install.txt Referenz | offen | optionaler Folge-Sprint |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — Install.txt (Blueprint Root)
GitHub-Sync:                      AUSSTEHEND — EUMAXL entscheidet Zeitpunkt
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Chirurgische str_replace-Eingriffe statt Neugenerierung haben Drift
    verhindert und die Session sauber gehalten
  - Rückfragen vor unsicheren Annahmen haben mehrfach falsche Richtungen
    verhindert — besonders beim Konzept-Verständnis zu Beginn
  - Lizenzen online verifizieren statt aus Training annehmen war richtig
    und hat zwei potenzielle Fehler (Obsidian, nmap) verhindert

Was beim nächsten Mal anders gemacht werden sollte:
  - Beim ersten Lesen der Aufgabe "Skill einlesen, GOV einlesen" sofort
    alle relevanten Dokumente laden — nicht erst nach Nachfrage
  - Bei "neues Konzept" früher nach dem konkreten Dokument fragen
    statt selbst zu interpretieren

Erkenntnisse die Dokumente oder GOV verändern:
  - Außenwirkung-Repositionierung ist Sprint-würdig und dokumentiert:
    Sprint / Backlog anlegen: JA — README-Sprint als nächster Z1-Sprint

---

## Bezüge

[[Global_GOV_DEV_S102]]                normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]     operative Arbeitsmethode
[[FREEZE_1_03]]                        Ausgangszustand
[[STAGE104_ZIELE_S104]]                Stage-Rahmen
[[BACKLOG_AIOF_DEV_S103]]              AIOF-Kontext

---

================================================================================
Install.txt Update & Außenwirkung-Repositionierung — SPRINT (DEV)
S1.04 | 2026-04-11 | R+MUNI Blueprint
================================================================================
