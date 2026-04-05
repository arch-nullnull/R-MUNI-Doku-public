================================================================================
TOTAL RESET — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_TotalReset_S102
Tag             : #dev #sprint #totalreset #gov #aidriven #skill #s102
Datum           : 2026-04-05
Stage           : S1.02 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-05
Jira-Sync       : NEIN
================================================================================

---
title: "Total Reset — GOV, AI Driven Methode und Skill Resync"
stage: S1.02
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-05"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, totalreset, s102]
---

================================================================================
TOTAL RESET — GOV, AI Driven Methode und Skill Resync
Stage S1.02 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Dieser Sprint dokumentiert den vollständigen Reset der R+MUNI Blueprint-Basis
nach einem Drift-bedingten Stage-Abbruch. Ein laufender Stage musste gestoppt
werden weil sich GOV, AI Driven Methode und der R+MUNI Visualization Skill
inhaltlich widersprochen haben und nicht mehr konsistent gearbeitet werden
konnte. Ein zweiter Anlauf in derselben Session scheiterte ebenfalls.
Entscheidung: Total Reset. Alle drei Dokumente werden in einer kontrollierten
Sequenz neu aufgebaut — GOV zuerst als normative Basis, dann AI Driven Methode,
dann Sprint-Templates — mit dem Skill als konstantem Referenzpunkt.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                  normative Grundlage — Ergebnis dieses Sprints
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]       operative Arbeitsmethode — Ergebnis dieses Sprints
- [[DEV_Sprint_Template_S102]]             Sprint-Template — Ergebnis dieses Sprints
- [[ASSOCIATE_Sprint_Template_S8]]         ASSOCIATE-Template — Ergebnis dieses Sprints

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Fehlerbehebung + Strukturbereinigung
Beschreibung: GOV, AI Driven Methode und R+MUNI Visualization Skill standen
              im Widerspruch zueinander. Die Inkonsistenzen hatten sich über
              mehrere Sessions akkumuliert ohne dass ein expliziter Resync
              stattgefunden hatte. Ein laufender Stage wurde durch Drift
              funktionsunfähig — ein zweiter Anlauf innerhalb derselben Session
              brachte keine ausreichende Stabilisierung. Entscheidung EUMAXL:
              Total Reset. Kein weiteres Patchwork — saubere Neubasis.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         GOV, AI Driven Methode und R+MUNI Visualization Skill sind nach
              Abschluss dieses Sprints vollständig konsistent. Alle drei
              Dokumente stehen als verlässliche gemeinsame Wahrheit. Die
              Sprint-Templates (DEV + ASSOCIATE) sind auf diesen Stand gebracht.
              Das System ist bereit für produktive Arbeit in S1.02.

Abgrenzung:   Dieser Sprint erstellt kein naming.md — das ist ein separater
              Folgeschritt nach Stabilisierung der Basis. Keine inhaltliche
              Erweiterung von GOV oder AI Driven über den Resync-Bedarf hinaus.
              Kein Jira-Sync. Kein GitHub-Sync in diesem Sprint.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  - GOV enthielt veraltete Kapitel (Kap. 12 Teamstruktur, Kap. 15
    Rückkopplungsschutz, Kap. 16 Naming mit Phantom-Verweis auf nicht
    existentes Dokument)
  - GOV enthielt Lernnarrative und erklärende Unterkapitel die dem
    normativen GOV-Charakter widersprachen
  - AI Driven Methode kannte das Viewpoint-System des Skills nicht —
    interne Varianten-Logik (DEV/EXP/ASC/MGT) war nicht deckungsgleich
    mit Skill-Viewpoints (DEV/EXPERT/R+MUNI/CARD)
  - AI Driven Methode enthielt eine Skills-Regel ("grundsätzlich
    deaktiviert") die der aktiven Nutzung des R+MUNI Visualization Skills
    direkt widersprach
  - GOV definierte Claude-Verhalten ("Claude als Werkzeug") obwohl das
    Verhalten ausschließlich in AI Driven geregelt sein soll
  - GOV enthielt Anonymisierungsautomatismus-Regel die mit der
    Werkzeugdefinition in derselben GOV kollidierte
  - Sprint-Templates waren nicht auf S1.02-Stand
  - Kein Dokument referenzierte die anderen korrekt und vollständig

Soll-Zustand nach dem Sprint:
  - GOV ist bereinigt: nur normative Regeln, keine Narrative, keine
    Werkzeugdefinitionen, kein Phantom-Verweis, Kapitel konsistent
    nummeriert
  - AI Driven Methode ist auf Viewpoint-System des Skills ausgerichtet,
    Skills-Regel korrekt, Kapitelreferenzen stimmen
  - Skill ist unverändert — er war die stabilste Schicht und diente als
    Referenzpunkt für den Resync
  - Sprint-Templates sind auf S1.02, stage-agnostisch, GOV-konform
  - Alle drei Dokumente referenzieren einander ohne Widerspruch


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 AI Driven Methode DEV S102 — Vollständiger Resync
-------------------------------------------------------

Was entstanden ist:
  Vollständiger Resync der AI Driven DEV Methode gegen den R+MUNI
  Visualization Skill. Ausgangspunkt war ein systematischer Abgleich
  beider Dokumente — Widersprüche wurden identifiziert, je Punkt mit
  EUMAXL geklärt und dann eingearbeitet.

  Wesentliche Änderungen gegenüber Vorversion:
  - Kap. 1: Varianten-Logik auf Viewpoint-System des Skills ausgerichtet.
    Vier Viewpoints (CARD / R+MUNI / EXPERT / DEV) ersetzen die alte
    Varianten-Liste. EXPERT wird nicht eigenständig geführt — on-demand
    aus DEV abgeleitet.
  - Kap. 3: Repos explizit benannt — zwei aktive Repos, Referenzdokumente
    als Single Source of Truth verankert.
  - Kap. 4: Atlassian-Trigger präzisiert (nur auf explizite Aufforderung).
    Output-Regel ergänzt: SVG als eigenständiges File, Einbettung in .md.
    Kontextmanagement-Abschnitt überarbeitet — Skills als gleichwertige
    Autorität zum Projektfolder verankert.
  - Kap. 5: Einfrierungs-Regelung für Kommunikationsstil entfernt —
    war überholt und nicht mehr relevant.
  - Kap. 11+13 (alt): Entfernt. Inhalte die KI-Verhalten regelten und
    in GOV doppelt lagen wurden konsolidiert.
  - Umnummerierung: Nach Entfernung von Kap. 11+13 (alt) wurden alle
    nachfolgenden Kapitel neu nummeriert — lückenlos 1–15.
  - Kap. 14 (neu, früher Kap. 16): Copilot-Referenz entfernt.
    Tool-Rollentrennung auf aktuellen Stand.
  - Kap. 15 (neu, früher Kap. 17): Namensregel — unverändert, nur
    Umnummerierung.
  - Skills-Regel (früher Kap. 13.1 alt): Formulierung korrigiert.
    "Skills grundsätzlich deaktiviert" aufgehoben — der R+MUNI
    Visualization Skill ist dauerhaft aktiv und ist gleichwertige
    Autorität zum Projektfolder.

Artefakte:    AI_DRIVEN_DEV_METHODE_DEV_S102.md
GOV-Konform:  JA


2.2 GOV Harter Cut Beta 1.x — Bereinigung und Resync
------------------------------------------------------

Was entstanden ist:
  Erster harter Schnitt in der GOV-Geschichte des Projekts. Systematische
  Durchsicht aller Kapitel. Je Befund: Klärung mit EUMAXL, Entscheidung,
  Umsetzung. Ziel war eine normativ saubere, konsistente GOV die als
  verlässliche Basis bis Beta 2.0 trägt.

  Entfernte Kapitel und Inhalte:
  - Kap. 12 (Teamstruktur mit COLUMBO-Referenz): komplett entfernt.
    Operative Rolleninfo gehört nicht in eine normative GOV.
  - Kap. 15 (Rückkopplungsschutz Stage-3–8 read-only): komplett entfernt.
    Letzter Release-Stand ist eingefroren — Schutz läuft über den
    Release-Prozess, nicht über die GOV.
  - Alle Lern- und Reifeaspekt-Unterkapitel aus Kap. 1–8: entfernt.
    Narrative und Erklärungen widersprechen dem normativen GOV-Charakter.
  - Kap. 1.2 + 1.3 Lernprojekt-Narrative: entfernt.
  - Kap. 11.6 ("Support ist kein Mord"): entfernt. Motivierendes Statement
    ohne prüfbare Regel — gehört ins README.
  - Kap. 13.4 Anonymisierungsregel: entfernt. Wird ausschließlich in
    AI Driven geregelt.
  - Kap. 13.6 ASSOCIATE-Reihe: entfernt. Viewpoint-Logik lebt im Skill —
    nicht in der GOV.
  - GOV 16.4 Phantom-Verweis auf [[naming_and_structure_S101]]: entfernt.
    Naming wird nach Basis-Stabilisierung in eigenem naming.md geregelt.
  - Claude-Verhalten (GOV 15.2 "Claude als Werkzeug"): entfernt.
    KI-Verhalten wird ausschließlich über AI Driven geregelt.
  - Duplikate in Kap. 2–8 wo Kap. 9 vollständiger und konsistenter war.

  Angepasste Inhalte:
  - Kap. 9 (verbindliche Regeln): als primäre normative Ebene
    gekennzeichnet. Bei Widerspruch zu Kap. 2–4 gilt Kap. 9.
  - Kap. 10.13 (Stage-Bezeichnung): "ab Stage 7" ersetzt durch
    "ab Beta 1.x". Beispiel entfernt.
  - Kap. 14 (Repo-Prinzip, früher Zwei-Welten): auf Kernprinzip reduziert.
    INTERN = non-public Repo, PUBLIC = offenes Repo. Keine MGT/DEV-Sprache,
    keine Zielgruppen-Beschreibungen.
  - Kap. 14 Naming-Unterkapitel (14.2 CamelCase, 14.3 Sprachprinzip):
    komplett entfernt. Naming lebt in naming.md — noch zu erstellen.
  - Alle "Claude"-Referenzen in der GOV: ersetzt durch "KI".
    Tool-Agnostizität sichergestellt.
  - Kapitel nach Entfernungen neu nummeriert — lückenlos.

  Struktur nach Cut:
  - Kap. 1:  Zweck, Intention und Charakter der Governance
  - Kap. 2:  Grundbegriffe und Abgrenzungen
  - Kap. 3:  Governance-Verständnis und Regelcharakter
  - Kap. 4:  Architektur- und Modellprinzipien
  - Kap. 5:  Artefaktrollen und Ebenentrennung
  - Kap. 6:  Verbindliche Regeln
  - Kap. 7:  Sprints
  - Kap. 8:  Umgang mit Usern
  - Kap. 9:  Externe Erkenntnisquellen und Rollentrennung
  - Kap. 10: Repo- und Dokumentationsstruktur

Artefakte:    Global_GOV_DEV_S102.md
GOV-Konform:  JA


2.3 Sprint-Templates — Resync auf S1.02
----------------------------------------

Was entstanden ist:
  DEV Sprint Template und ASSOCIATE Sprint Template auf S1.02-Stand gebracht.
  DEV Template: stage-agnostisch (alle Stage-Referenzen als <STAGE>
  Platzhalter), GOV-Referenzen ohne Suffix, Obsidian-Tags angepasst.
  ASSOCIATE Template: analog angepasst.

Artefakte:    DEV_Sprint_Template_S102.md
              ASSOCIATE_Sprint_Template_S8.md (Basis, wird separat nachgezogen)
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Total Reset statt Patch
  Auslöser:    Stage-Abbruch durch Drift. Zweiter Anlauf in derselben
               Session ebenfalls nicht stabilisierbar.
  Ergebnis:    Vollständiger Reset. Keine inkrementelle Reparatur.
               Kontrollierte Sequenz: AI Driven → GOV → Templates.
  Begründung:  Patchwork auf einem inkonsistenten Fundament hätte weitere
               Drift produziert. Sauber neu ist schneller als weiter
               reparieren.
  GOV-Bezug:   GOV 7.3 (Fehlerbehebung als Sprint-Auslöser),
               GOV 7.4 (Fehler = Abweichung vom intendierten Systemzustand)
  Auswirkung:  Alle drei Basisdokumente auf konsistenten Stand. Basis
               für produktive Arbeit in S1.02 und Aufbau bis Beta 2.0.
  Rückwirkung: NEIN — kein bestehendes führendes Artefakt verändert.
               GOV und AI Driven waren selbst Gegenstand des Resets.

Entscheidung: KI-Verhalten ausschließlich in AI Driven — nicht in GOV
  Auslöser:    GOV enthielt Claude-Verhaltensdefinitionen die mit
               AI Driven kollidierten und konzeptionell fehl am Platz waren.
  Ergebnis:    Alle KI-Verhaltensregeln aus GOV entfernt.
               GOV ist tool-agnostisch. AI Driven ist einzige Autorität
               für KI-Verhalten.
  Begründung:  Saubere Trennung: GOV = was modelliert/integriert/automatisiert
               werden darf. AI Driven = wie mit der KI gearbeitet wird.
  GOV-Bezug:   GOV 1.2 (Abgrenzung — GOV ist keine Verhaltensregeldefinition
               für KI)
  Auswirkung:  GOV kürzer, klarer, normativer. AI Driven ist vollständige
               Autorität für Arbeitsweise.
  Rückwirkung: NEIN

Entscheidung: Skill als gleichwertige Autorität zum Projektfolder
  Auslöser:    AI Driven Methode enthielt Skills-Regel "grundsätzlich
               deaktiviert" — direkt im Widerspruch zur aktiven Nutzung
               des R+MUNI Visualization Skills.
  Ergebnis:    Skills-Regel korrigiert. Aktive Skills sind gleichwertige
               Autorität zum Projektfolder — explizit in Kap. 4 von
               AI Driven verankert.
  Begründung:  Der Skill ist die erste verlässliche kontrollierte Schicht
               gegen Drift — das muss in der Arbeitsmethode stehen.
  GOV-Bezug:   Kein direkter GOV-Bezug — AI Driven Kap. 4 und Kap. 12.
  Auswirkung:  Skill wird ab sofort immer zu Sessionstart geladen.
               Keine Unsicherheit mehr über Status des Skills.
  Rückwirkung: NEIN

Entscheidung: Harter Cut GOV — Lernnarrative, Teamstruktur, Rückkopplungsschutz raus
  Auslöser:    GOV enthielt Kapitel und Unterkapitel die keinen normativen
               Charakter hatten: Lernprojekt-Narrative, Motivationsstatements,
               operative Teamrollen, Rückkopplungsschutz über Stage-Nummern.
  Ergebnis:    Erster harter Cut in der GOV-Geschichte des Projekts.
               Alle nicht-normativen Inhalte entfernt. GOV schlanker
               und klarer als je zuvor.
  Begründung:  Eine GOV die gegen ihr eigenes Template verstößt ist keine
               GOV. Dieser Cut stellt die normative Integrität her.
  GOV-Bezug:   GOV 3.1 (Governance als verbindliches Regelwerk),
               GOV 3.2 (normativer Charakter)
  Auswirkung:  Gilt als Baseline bis Beta 2.0. Erweiterungen folgen
               denselben GOV-Regeln und müssen normativ sein.
  Rückwirkung: NEIN

Entscheidung: naming.md als separater Folgeschritt
  Auslöser:    GOV 16.4 verwies auf nicht-existentes naming_and_structure.md.
               Naming-Kapitel in GOV war inhaltlich nicht mehr korrekt.
  Ergebnis:    Naming-Kapitel aus GOV entfernt. naming.md wird nach
               Stabilisierung der Basis als eigener Sprint erstellt.
               Scope: Namen-only, kein Struktur-Kapitel (Struktur lebt
               in AI Driven).
  Begründung:  Erst Fundament stabilisieren, dann aufbauen.
  GOV-Bezug:   GOV 1.4 (Explizitheit als Grundprinzip)
  Auswirkung:  naming.md als offener Backlog-Punkt. Kein Phantom-Verweis
               mehr in der GOV.
  Rückwirkung: NEIN

Entscheidung: Alle Claude-Referenzen in GOV durch KI ersetzt
  Auslöser:    GOV soll tool-agnostisch sein. Claude-Referenzen verankern
               einen konkreten Tool-Namen in einer normativen Governance.
  Ergebnis:    Alle Vorkommen von "Claude" in der GOV durch "KI" ersetzt.
  Begründung:  Tool-Unabhängigkeit ist GOV-Prinzip (GOV 4.5).
               Die GOV soll nicht veralten wenn ein Tool wechselt.
  GOV-Bezug:   GOV 4.5, GOV 6.11
  Auswirkung:  GOV ist dauerhaft tool-agnostisch.
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Dokumentation erst nach Sprint-Abschluss
  GOV-Regel:   GOV 7.8 — Dev-Dokumentation während des Sprints.
  Begründung:  Der Sprint selbst war der Reset der Dokumentationsbasis.
               Während des Resets existierte keine stabile GOV als Grundlage
               für die Sprint-Dokumentation selbst. Die Sprint-Doku entstand
               daher unmittelbar nach Abschluss aller Artefakte — nicht
               parallel. Vollständige Rekonstruktion ist gegeben.
  Wirkung:     Auf diesen Sprint begrenzt. Kein Präzedenzfall.


================================================================================
5. VERHALTENSHINWEISE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis (GOV-Review Session): Scope-Expansion erkannt bei GOV
  Kap. 14 — voreilig als "raus" markiert ohne Rückfrage. EUMAXL korrigierte.
  Entscheidung: Kap. 14 bleibt, wird reduziert. Kein Schaden, aber Muster
  benannt und dokumentiert.

⚠ Verhaltenshinweis (AI Driven Session): Beim Abgleich AI Driven ↔ Skill
  wurden Widersprüche benannt ohne sofort zu schreiben — Freigabe je Punkt
  eingeholt. Meldepflicht eingehalten.

⚠ Verhaltenshinweis (Sprint-Template Session): Keine Verhaltensauffälligkeiten
  gemeldet — sauberer Durchlauf.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt                          | GOV-Bezug        | Status | Nächste Aktion                              |
|-------------------------------|------------------|--------|---------------------------------------------|
| naming.md erstellen           | GOV 1.4, 6.3     | offen  | Eigener Sprint nach Basis-Stabilisierung    |
| ASSOCIATE Template finalisieren| GOV 7.9          | offen  | Überprüfung ob weiterer Anpassungsbedarf    |
| GitHub-Sync GOV + AI Driven   | AI Driven Kap. 4 | offen  | EUMAXL entscheidet Zeitpunkt                |
| Skill-Update prüfen           | AI Driven Kap. 4 | offen  | Nächste Session: Skill gegen neue GOV prüfen|


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — Outputs dieser Session
GitHub-Sync:                      AUSSTEHEND — EUMAXL entscheidet
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Skill als stabiler Referenzpunkt während des gesamten Resets.
    Der Skill hat nicht gedriftet — er war die verlässliche Basis
    gegen die alles andere kalibriert wurde.
  - Sequenzierung: AI Driven zuerst, dann GOV, dann Templates.
    Diese Reihenfolge hat verhindert dass GOV-Änderungen die AI Driven
    Arbeit beeinflusst haben bevor AI Driven stabil war.
  - Entscheidung Total Reset: kein weiteres Patchwork. Die Konsequenz
    hat Zeit gespart und ein sauberes Ergebnis produziert.
  - Befunde strukturiert vorlegen und je Punkt Freigabe einholen —
    kein Schreiben ohne Entscheidung.
  - Meldepflicht funktioniert: Scope-Expansion bei GOV Kap. 14 wurde
    erkannt und gemeldet bevor Schaden entstand.

Was beim nächsten Mal anders gemacht werden sollte:
  - Resync GOV ↔ AI Driven ↔ Skill gehört an den Anfang eines neuen
    Stage — nicht erst wenn der Drift bereits zum Abbruch geführt hat.
    Präventiver Abgleich statt reaktiver Reset.
  - Skill-Konsistenzprüfung als fester Bestandteil des Stage-Starts
    etablieren — nicht als optionalen Schritt.

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Resync-Pflicht zu Stage-Beginn: Sprint / Backlog anlegen: JA
    → Offener Punkt: Etablierung eines Stage-Start-Checklisten-Formats
      das GOV ↔ AI Driven ↔ Skill Konsistenz als Pflichtschritt enthält.

---

## Bezüge

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode

---

================================================================================
TOTAL RESET — SPRINT (DEV) | S1.02 | 2026-04-05 | R+MUNI Blueprint
================================================================================
