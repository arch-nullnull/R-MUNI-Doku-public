================================================================================
SPRINT-DEV-S7-Z6-README-Doku
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV
Tag             : #sprint #doku #readme #associate #templates
Datum           : 2026-03-26
Stage           : S7 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================


================================================================================
1. AUSGANGSLAGE UND KONTEXT
================================================================================

1.1 Ist-Zustand vor diesem Sprint
-----------------------------------
- README.md im Haupt-Repo (R-MUNI) gut aber Stage 6 veraltet
- Install.txt auf Stage 5 Stand, Kundenstruktur nicht mehr aktuell
- R-MUNI-Doku-public: README quasi leer, index.md veraltet (bis Stage 5)
- Atlassian Helpcenter Page: Space EW gelöscht, blob-Links kaputt
- Kein einheitlicher Header-Standard über alle Dokumenttypen
- USER-Templates vorhanden aber mit historischem Overhead
- ASSOCIATE als Zielgruppen-Reihe noch nicht definiert

1.2 Ziel dieses Sprints
------------------------
S7-Z6: README und Dokumentationsbereich ausbauen.
Kombiniert mit Kundenstruktur-Fixierung und ASSOCIATE Template-Set.

Externe Leser sollen R+MUNI nach README-Lektüre ohne weitere Erklärung
verstehen. Einheitlicher Header-Standard für Obsidian-Filterbarkeit.


================================================================================
2. ENTSCHEIDUNGEN
================================================================================

2.1 index.md wird durch README.md ersetzt (R-MUNI-Doku-public)
----------------------------------------------------------------
Entscheidung: index.md killen — eine starke README statt zwei schwache Dateien.
Begründung: Gleiche Logik wie im Haupt-Repo — ein Einstiegsdokument reicht.
Auswirkung: README_Doku-public.md neu erstellt mit Script-Baukasten,
            Werkzeugkasten Tier-Struktur, Ordnerstruktur DEV,
            Dokumentationsstruktur-Erklärung (Freeze/Sprint/Backlog).

2.2 M2B Beschreibung korrigiert
---------------------------------
Entscheidung: M2B = Master ↔ BPMN — erstellt BPMN-Prozesshüllen nach Trigger.
Begründung: Falsch aus Dateinamen abgeleitet — Principles hätten gelesen
            werden sollen. Sofort korrigiert in beiden READMEs.
Auswirkung: Beide README-Dateien aktualisiert.

2.3 Atlassian Helpcenter Page
------------------------------
Entscheidung: EUMAXL hat Page selbst minimalistisch neu aufgebaut.
Begründung: Space EW ist weg, blob-Links kaputt — sauberer Schnitt besser
            als dead links. Bilder kommen später wenn neu aufbereitet.
Auswirkung: Page ist sauber und minimalistisch — kein Verlust an Funktion,
            temporärer Verlust an Außenwirkung bewusst akzeptiert.

2.4 Datumsformat bleibt YYYY-MM-DD
------------------------------------
Entscheidung: ISO-Format wird nicht geändert.
Begründung: Gesamter Blueprint verwendet YYYY-MM-DD — Scripts, Sortierung,
            Obsidian-Filter funktionieren damit korrekt. DD-MM-YYYY würde
            Sortierung brechen und inkonsistent mit allem Bestehenden sein.
Auswirkung: Keine Änderung.

2.5 Einheitlicher Header-Standard
-----------------------------------
Entscheidung: Alle Dokumenttypen bekommen identischen Header-Aufbau.
Felder: Projekt, Dokument, Tag, Datum, Stage, Status, Verantwortlich,
        Review, Jira-Sync — plus optionale Addon-Felder.
Begründung: Obsidian-Filterbarkeit, konsistente Struktur über DEV und
            Kundenumgebung hinweg.
Auswirkung: Alle neuen Templates nach diesem Standard.
            GOV-Header-Review kommt am Stage-Ende.

2.6 Neue Kundenstruktur in Install.txt
----------------------------------------
Entscheidung: Abschnitt 1.1 und 3.7 komplett ersetzt.
Neue Struktur:
  R+MUNI Apps\
  R+MUNI Archiv <Kundenkürzel>\
  R+MUNI <Kundenkürzel>\          GitHub Sync Kunden-Repo (opt. DEV-Freigabe)
  R+MUNI Doku <Kundenkürzel>\     GitHub Sync Kunden-Repo (opt. DEV-Freigabe)
  R+MUNI Archi <Kundenkürzel>\    GitHub Sync Kunden-Repo (opt. DEV-Freigabe)
  R-MUNI\                         DEV-Repo public
  R-MUNI-Doku-public\             DEV-Repo public
Begründung: Kunde hält eigene Repos — DEV-Zugriff nur auf explizite Freigabe.
Auswirkung: Install.txt Abschnitt 1.1 und 3.7 aktualisiert.

2.7 Zielgruppen-Modell definiert
----------------------------------
Entscheidung: Vier Zielgruppen — DEV, ASSOCIATE, EXPERT (Backlog), MGT (Backlog).
  DEV       — bleibt unverändert, für Entwickler und externe DEVs
  ASSOCIATE — neue Hauptzielgruppe Stage 7, ersetzt USER
  EXPERT    — DEV ohne DEV-Anteil (Backlog)
  MGT       — reduziert, kommt aus ASC (Backlog)
Auswirkung: ASSOCIATE Template Set erstellt (5 Dokumente).
            USER-Templates bleiben als historische Expert-Vorlage im DEV.

2.8 DEV Templates Header-Update
---------------------------------
Entscheidung: how2_DEV_Template und how2_USER_Template auf neuen Header-Standard.
Dateiname: _S6 → _S7.
Auswirkung: Beide Templates aktualisiert. USER-Template bleibt intern als
            Expert-Vorlage — wird nicht mehr aktiv ausgespielt.


================================================================================
3. BETROFFENE ARTEFAKTE
================================================================================

Neu erstellt:
  README_Doku-public.md              Ersetzt index.md + leere README
  ASSOCIATE_principles_Template_S7   Neues Template Set
  ASSOCIATE_How2_Template_S7         Neues Template Set
  ASSOCIATE_Sprint_Template_S7       Neues Template Set
  ASSOCIATE_Backlog_Template_S7      Neues Template Set
  ASSOCIATE_Notes_Template_S7        Neues Template Set

Aktualisiert:
  README_hauptrepo.md                Stage 6 → 7, M2B korrigiert
  Install.txt                        Stage 7, neue Kundenstruktur
  how2_DEV_Template_S7.md            Header-Standard, S6 → S7
  how2_USER_Template_S7.md           Header-Standard (bleibt intern)

Unverändert (bewusst):
  Global_GOV.md                      Review am Stage-Ende
  Alle Stage-3/4/5/6 Dokumente       Rückkopplungsschutz eingehalten
  Atlassian Helpcenter Page          Von EUMAXL direkt bearbeitet


================================================================================
4. OFFENE PUNKTE NACH SPRINT-ABSCHLUSS
================================================================================

| Thema | Status | Nächste Aktion |
|-------|--------|----------------|
| GOV Header prüfen | Offen | Am Stage-Ende |
| EXPERT Template Set | Backlog | Eigener Sprint |
| MGT Template Set | Backlog | Kommt aus ASC |
| GitHub Release / ZIP | Eigener Sprint | S7-Z5 |
| Obsidian Vault öffentlich | Offen | S7-Z7 |
| Bilder Atlassian Page | Offen | Wenn Flipcharts neu aufbereitet |


================================================================================
5. LESSONS LEARNED
================================================================================

5.1 Was gut funktioniert hat
------------------------------
- Punkt-für-Punkt Durcharbeiten vor Output — alle Abhängigkeiten erkannt
  bevor geschrieben wurde. Kein Restart nötig.
- Direkte Korrekturen (M2B, USER-Template) sofort eingearbeitet ohne Overhead.
- EUMAXL hat Atlassian Page selbst gefixed — pragmatisch und richtig.
- Datumsformat-Entscheidung sauber und begründet getroffen.

5.2 Was beim nächsten Mal anders
----------------------------------
- Principles lesen vor Beschreibungen schreiben — M2B wäre nicht falsch
  gewesen wenn M2B_FLOW_principles_S3.md gelesen worden wäre.
- Überstrukturierung am Anfang der Session — zu viele Fragen auf einmal
  bevor etwas entstanden ist. EUMAXL hat das direkt korrigiert.
  Verhaltensänderung dokumentiert und angepasst.

5.3 Erkenntnisse für das System
---------------------------------
- Einheitlicher Header-Standard ist jetzt etabliert — alle neuen Dokumente
  ab Stage 7 folgen diesem Standard.
- ASSOCIATE als Zielgruppen-Begriff ist definiert und im Blueprint verankert.
- Kunden-Repo-Modell (Kunde hält eigene Repos) ist dokumentierter Standard.


================================================================================
6. BEZÜGE UND VERLINKUNGEN
================================================================================

Ausgangspunkt:
  [[FREEZE-6_konsolidiert]]                   Baseline S7
  [[STAGE7_ZIELE]]                            S7-Z6 Definition

Entstanden:
  README_Doku-public.md
  ASSOCIATE_*_Template_S7.md (5 Dokumente)
  how2_DEV_Template_S7.md
  Install.txt (aktualisiert)
  README_hauptrepo.md (aktualisiert)

Verwandte Dokumente:
  [[Global_GOV]]                              Review am Stage-Ende
  [[BETA_GitHub_Nutzung_S5]]                  Zwei-Repo-Prinzip — Hintergrund
  [[Sprint-DEV-S7-Z3-Feedbackschleifen_S7]]  Vorgänger-Sprint


================================================================================
Sprint-DEV-S7-Z6-README-Doku | S7 | 2026-03-26 | R+MUNI Blueprint
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
