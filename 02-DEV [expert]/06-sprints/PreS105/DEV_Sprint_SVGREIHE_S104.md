================================================================================
SVG REIHE — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_SVGREIHE_S104
Tag             : #dev #sprint #svg #creative #s104
Datum           : 2026-04-12
Stage           : S1.04 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-12
Jira-Sync       : NEIN
================================================================================

---
title: "SVG Reihe — Sprint DEV"
stage: S1.04
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-12"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, svg, creative, s104]
---

================================================================================
SVG REIHE — SPRINT (DEV)
Stage S1.04 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Erstellung einer vollständigen SVG-Visualisierungsreihe für R+MUNI im Rahmen
von Stage S1.02. Ausgangspunkt waren drei definierte SVG-Inhalte aus dem
Quelldokument svg_inhalte.md. Im Verlauf des Sprints wurden zusätzlich zwei
bestehende SVGs aus S103 auf das neue Designsystem adaptiert sowie ein
SVG-Master-Dokument als Single Source of Truth für alle künftigen SVGs erstellt.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]     operative Arbeitsmethode
- [[SVG_MASTER_DEV_S102]]                Designsystem — führend für alle SVG-Ausgaben
- [[svg_inhalte_S102]]                   Quelldokument mit Inhalten der SVG-Reihe

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------
Auslöser:     Feature-Zuwachs
Beschreibung: R+MUNI benötigt eine einheitliche visuelle Darstellung der
              Kernkonzepte (Säulen/Beine, Varianten, Leistungen) als SVG-Reihe
              für den öffentlichen Bereich. Bestehende SVGs aus S103 waren im
              dunklen Farbschema und nicht konsistent zum neuen Designsystem.


1.2 Zieldefinition (GOV 7.6)
------------------------------
Ziel:         Vollständige SVG-Reihe im neuen hellen Designsystem (Kachel-in-Kachel)
              plus Designsystem-Dokument als Single Source of Truth.
              Alle SVGs downloadbereit und inhaltlich korrekt nach Quelldokument.

Abgrenzung:   Kein Einbau in Obsidian oder GitHub in diesem Sprint.
              Keine Erstellung von .md Einbettungsdokumenten.
              Keine Anpassung der SVG-Inhalte über das Quelldokument hinaus
              ohne explizite Freigabe durch EUMAXL.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
SVGs aus S103 (munidell_tabelle, munidell_ki_empfehlung, toolbaukasten) im
dunklen Farbschema. Kein einheitliches Designsystem dokumentiert.
SVG-Inhalte für Säulen/Varianten/Leistungen in svg_inhalte.md vorhanden
aber noch nicht als SVG umgesetzt.

Soll-Zustand nach dem Sprint:
Alle SVGs im hellen Designsystem (Kachel-in-Kachel, SVG Master Farben).
SVG_MASTER_DEV_S102.md als Referenzdokument für künftige SVG-Erstellungen.
Alle Files downloadbereit ausgegeben.


1.4 Rolle (AI Driven Kap. 10)
------------------------------
Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 SVG_MASTER_DEV_S102.md — Designsystem Single Source of Truth
-----------------------------------------------------------------
Neues Referenzdokument erstellt das alle Designregeln für SVG-Ausgaben
in R+MUNI verbindlich festlegt: Farbreihen, Kachel-in-Kachel-Aufbau,
Layout-Koordinaten, Berechnungsformeln, Eingabeformat für neue SVGs.

Artefakte:    SVG_MASTER_DEV_S102.md — 07-creative
GOV-Konform:  JA


2.2 svg_saeulen.svg — Die vier Säulen
--------------------------------------
SVG mit vier Säulen des R+MUNI Toolstacks plus vollständiger Addon-Sektion.
Kachel-in-Kachel je Tool, ACHTUNG-Banner für kostenpflichtige 3Party Apps,
Archi Plugins als Patreon-pflichtig ausgewiesen.

Artefakte:    svg_saeulen.svg — 07-creative
GOV-Konform:  JA


2.3 svg_beine.svg — Die vier Beine
------------------------------------
Identisch zu svg_saeulen.svg, Titel geändert auf "Die vier Beine".
Auf expliziten Wunsch von EUMAXL als Alternativversion geführt.

Artefakte:    svg_beine.svg — 07-creative
GOV-Konform:  JA


2.4 svg_varianten.svg — Für wen ist R+MUNI?
--------------------------------------------
Drei Hauptvarianten (CARD, R+MUNI, DEV) als Kacheln mit Sub-Kacheln
je Inhaltspunkt. EXPERT als gestrichelte Ableitung extern unter DEV.
Reihenfolge: CARD → R+MUNI → DEV → EXPERT.

Artefakte:    svg_varianten.svg — 07-creative
GOV-Konform:  JA


2.5 svg_leistungen.svg — Optionale Leistungen
----------------------------------------------
Drei Leistungskacheln (SETUP, SCHULUNG, SUPPORT) mit Sub-Kacheln
je Inhaltspunkt. Inhalte nach expliziter Freigabe durch EUMAXL angepasst.

Artefakte:    svg_leistungen.svg — 07-creative
GOV-Konform:  JA


2.6 munidell_tabelle.svg — Die Munidell Stufen
-----------------------------------------------
Adaptation aus S103. Struktur 1:1 behalten, dunkles Farbschema auf
helles SVG-Master-Schema umgestellt. Titel geändert auf "Die Munidell Stufen".

Artefakte:    munidell_tabelle.svg — 07-creative
GOV-Konform:  JA


2.7 munidell_ki_empfehlung.svg — KI-Empfehlung je Munidell Stufe
------------------------------------------------------------------
Adaptation aus S103. Struktur auf Kachel-in-Kachel umgebaut.
Reihenfolge neu: CARD → R+MUNI → Expert → DEV.
Associate durch R+MUNI ersetzt.

Artefakte:    munidell_ki_empfehlung.svg — 07-creative
GOV-Konform:  JA


2.8 toolbaukasten.svg — R+MUNI Toolbaukasten
---------------------------------------------
Adaptation aus S103. Farbschema auf helles SVG-Master-Schema umgestellt.
Inhaltliche Bereinigung:
  Git 2.53+ aus Core ins Sideboard (zu VS Code)
  OpenJDK 21 entfernt (implizit durch Archi)
  O365/SharePoint entfernt
  Claude Pro entfernt
  OBS Studio als neue Kachel im Sideboard ergänzt
  jArchi Addons → Archi Addons umbenannt
  Alle Badges auf volle Breite angepasst
  Core neu auf 4+4 Layout ohne Lücken

Artefakte:    toolbaukasten.svg — 07-creative
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Kachel-in-Kachel als primäres Darstellungssystem
  Auslöser:    Bisherige Plaintext-Zeilen in Kacheln wirkten unstrukturiert
  Ergebnis:    Jeder Inhaltspunkt erhält eine eigene Sub-Kachel innerhalb
               der großen Kachel
  Begründung:  Optisch konsistenter, besser skalierbar, klar ablesbar
  GOV-Bezug:   GOV 4.2 — Trennung von Struktur und Darstellung
  Auswirkung:  Gilt als Standard für alle künftigen R+MUNI SVGs
  Rückwirkung: NEIN

Entscheidung: SVG_MASTER_DEV_S102 als führendes Designdokument
  Auslöser:    Ohne Referenzdokument entsteht Drift bei jeder neuen Session
  Ergebnis:    SVG_MASTER_DEV_S102.md im Projektordner 07-creative als
               Single Source of Truth für alle SVG-Ausgaben
  Begründung:  GOV 1.4 Explizitheit — Designentscheidungen müssen dokumentiert
               und reproduzierbar sein
  GOV-Bezug:   GOV 1.4, GOV 6.13
  Auswirkung:  Neue SVGs werden immer aus diesem Dokument abgeleitet
  Rückwirkung: NEIN

Entscheidung: Vier Säulen / Vier Beine als Parallelvariante
  Auslöser:    EUMAXL wünschte beide Titelversionen
  Ergebnis:    Beide Files geführt — identischer Inhalt, unterschiedlicher Titel
  Begründung:  Kein Mehraufwand, EUMAXL entscheidet über Verwendung
  GOV-Bezug:   kein direkter Bezug
  Auswirkung:  Beide Files in 07-creative ablegen
  Rückwirkung: NEIN

Entscheidung: Toolbaukasten inhaltliche Bereinigung
  Auslöser:    Git, OpenJDK, O365, Claude Pro im alten Toolbaukasten
               nicht mehr dem aktuellen Stand entsprechend
  Ergebnis:    Git ins Sideboard, OpenJDK und O365 entfernt,
               Claude Pro entfernt, OBS Studio ergänzt
  Begründung:  EUMAXL-Freigabe explizit erteilt je Änderung
  GOV-Bezug:   GOV 1.4
  Auswirkung:  toolbaukasten.svg entspricht nun aktuellem S102-Stand
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Output-Regel — SVG File vor Render
  GOV-Regel:   AI Driven Kap. 4 — SVG als File ausgeben
  Begründung:  Anfangs wurden SVGs nur gerendert ohne File-Ausgabe.
               Nach Hinweis von EUMAXL korrekt umgestellt auf
               File-Ausgabe + present_files als Standard.
  Wirkung:     Auf diese Session begrenzt — im SVG_MASTER dokumentiert


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Output-Regel verletzt — SVG nur gerendert ohne File.
  Korrektur eingeholt, danach konsequent als File ausgegeben.

⚠ Verhaltenshinweis: Farbfrage bei munidell_ki_empfehlung — DEV war
  bisher Coral, im Original dunkel-lila. Entscheidung für konsistentes
  SVG-Master-Farbsystem getroffen, EUMAXL informiert.

⚠ Verhaltenshinweis: Erste Version munidell_ki_empfehlung war Scope-Expansion
  (Kachel-in-Kachel ohne Auftrag). Nach Rückmeldung korrigiert auf
  Struktur-Erhalt mit reinem Farbwechsel.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| Ablage aller SVGs in 07-creative | GOV 10.2 | offen | EUMAXL legt ab nach Review |
| GitHub-Sync SVG-Reihe | GOV 10.4 | offen | EUMAXL entscheidet ob public |
| SVG_MASTER in Projektfolder aufnehmen | AI Driven Kap. 12 | offen | EUMAXL Push |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               NEIN — Ablage durch EUMAXL ausstehend
GitHub-Sync:                      AUSSTEHEND — EUMAXL entscheidet
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  -

Was beim nächsten Mal anders gemacht werden sollte:
  -

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  -

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[SVG_MASTER_DEV_S102]]              Designsystem SVG-Reihe

---

================================================================================
SVG REIHE — SPRINT (DEV) | S1.04 | 2026-04-12 | R+MUNI Blueprint
================================================================================
