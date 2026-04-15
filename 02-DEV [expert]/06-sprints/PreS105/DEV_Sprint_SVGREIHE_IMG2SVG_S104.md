================================================================================
SVG-REIHE IMG2SVG — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_SVGREIHE_IMG2SVG_S104
Tag             : #dev #sprint #svg #img2svg #s104
Datum           : 2026-04-12
Stage           : S1.04 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-12
Jira-Sync       : NEIN
================================================================================

---
title: "SVG-Reihe IMG2SVG — Sprint DEV"
stage: S1.04
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-12"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, svg, img2svg, s104]
---

================================================================================
SVG-REIHE IMG2SVG — SPRINT (DEV)
Stage S1.04 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Neue Script-Reihe SVG für die Konvertierung von Bilddateien (PNG, JPG und
gängige Rasterformate) nach SVG via Inkscape CLI. Bedarf entstanden aus dem
Workflow-Alltag: generierte Bilder (PNG) und abfotografierte Zeichnungen (JPG)
sollen ohne manuellen Inkscape-Eingriff automatisiert in SVG überführt werden.

Die Reihe folgt dem R+MUNI Grundprinzip konsequent: 1 Script = 1 Aufgabe =
1 Output. Jeder Schritt erzeugt ein nachvollziehbares Log-Artefakt in
02-stages\99-logs\. Die Reihe ist vollständig eigenständig lauffähig —
HLP00 als einzige externe Abhängigkeit, Pillow zusätzlich für SVG05.

Alle 7 Artefakte (svg_config.txt + SVG00–SVG06) wurden in dieser Session
entwickelt, getestet und durch EUMAXL freigegeben.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[naming_and_structure_S102]]        Namenskonventionen und Ablagestruktur
- [[DEV_Sprint_SVGREIHE_S102]]         Vorheriger SVG-Sprint — SVG-Designsystem

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Feature-Zuwachs
Beschreibung: Wiederkehrender manueller Aufwand beim Überführen von Raster-
              bildern in SVG. PNG (KI-generierte Visuals) und JPG (Fotos von
              Handzeichnungen) sollen per Script-Reihe automatisiert via
              Inkscape CLI verarbeitet werden. Quellordner, Zielordner und
              Inkscape-Pfad konfigurierbar — kein hardcoded Pfad,
              keine manuelle Einzelbearbeitung.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         Vollständige, lauffähige SVG-Reihe mit 7 Scripts und
              Konfigurationsartefakt svg_config.txt.

Abgrenzung:   - Kein SVG-Nachbearbeitungsschritt (kein Design-Eingriff)
              - Keine GUI, keine Fortschrittsanzeige
              - Kein FLW-Eintrag in dieser Session — Reihe zuerst stabil
              - SVG04 (Trace) als experimentell markiert
              - Keine Änderung an root.cfg-Struktur
              - Kein rekursives Scannen von Unterordnern


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  Keine SVG-Reihe vorhanden. Konvertierung erfolgte manuell in Inkscape.
  Kein konfigurierter Workflow, keine Protokollierung.

Soll-Zustand nach dem Sprint:
  SVG00–SVG06 in 01-artifacts\01-scripts\ abgelegt.
  svg_config.txt in <rootfolder>\99-doku\ abgelegt.
  Alle Scripts produktiv getestet und durch EUMAXL freigegeben.
  → ERREICHT


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 svg_config.txt
-------------------

Konfigurationsartefakt für die gesamte SVG-Reihe. Wird von SVG00 gelesen
und validiert. Alle nachfolgenden Scripts lesen dieselbe Config.

Felder:
  inkscape_exe        Vollständiger Pfad zur inkscape.exe (nicht aus root.cfg)
  svg_source_folder   Quellordner — beliebiger absoluter Pfad
  svg_target_folder   Zielordner — beliebiger absoluter Pfad
  svg_overwrite       true / false — Default false (sicherer Default)
  svg_formats         Kommaliste verarbeitbarer Endungen, case-insensitiv
  svg_trace_threshold Nur SVG04 — Helligkeitsschwelle 0.0–1.0
  svg_trace_mode      Nur SVG04 — brightness | edge | color

Ablageort:    <rootfolder>\99-doku\svg_config.txt
GOV-Konform:  JA


2.2 SVG00 — Umgebungsvalidierung
----------------------------------

Liest root.cfg via HLP00 und validiert svg_config.txt vollständig.
Prüft: rootfolder, svg_config.txt Pflichtfelder, inkscape_exe,
source_folder, target_folder (Warnung), svg_formats.
Kritische Fehler → Abbruch mit klarer Meldung.

Output:       SVG00-validate_environment.log
Artefakte:    01-artifacts\01-scripts\SVG00-validate_environment.py
GOV-Konform:  JA
Teststatus:   GRÜN — durch EUMAXL freigegeben


2.3 SVG01 — Inventarisierung Quellordner
-----------------------------------------

Scannt Quellordner (nur oberste Ebene, keine Rekursion).
Klassifiziert jede Datei: OK | RENAME_REQUIRED | SKIP.
RENAME_REQUIRED: Leerzeichen oder Sonderzeichen im Dateinamen.
SKIP: Dateiendung nicht in svg_formats.
Ausgabe als Tabelle mit festen Spaltenbreiten — Basis für alle
nachfolgenden Scripts (parse_inventar via Zeichenposition).

Output:       SVG01-inventory.log
Artefakte:    01-artifacts\01-scripts\SVG01-inventory.py
GOV-Konform:  JA
Teststatus:   GRÜN — durch EUMAXL freigegeben


2.4 SVG02 — Dateinamen-Bereinigung
------------------------------------

Liest RENAME_REQUIRED Einträge aus SVG01-inventory.log.
Bereinigungsregel: Leerzeichen → Unterstrich, Sonderzeichen entfernen
(außer Bindestrich, Unterstrich, Punkt). Kollisionsprüfung vor
Umbenennung — keine Überschreibung bei Kollision.
Umbenennung direkt im Quellordner.

Hinweis: Nach SVG02 muss SVG01 erneut ausgeführt werden um das
Inventar zu aktualisieren bevor SVG03/SVG04 gestartet wird.

Output:       SVG02-rename.log
Artefakte:    01-artifacts\01-scripts\SVG02-rename.py
GOV-Konform:  JA
Teststatus:   GRÜN — durch EUMAXL freigegeben


2.5 SVG03 — Embed-Konvertierung (Option A)
-------------------------------------------

Konvertiert alle OK/RENAME_REQUIRED Dateien aus SVG01-Inventar via
Inkscape CLI. Das Rasterbild wird als Base64-Objekt in SVG-Hülle
verpackt — kein Vektorisierungsschritt, kein Qualitätsverlust.
Overwrite-Logik via svg_overwrite. Timeout 60 Sekunden je Datei.

CLI: inkscape.exe "<quelle>" --export-type=svg --export-filename="<ziel>"

Erkenntnis aus Test: SVG-Ausgabegröße entspricht ~133% des Originals
durch Base64-Enkodierung — für große Bilder (>5MB) vor SVG03 SVG05
ausführen.

Output:       SVG-Dateien im svg_target_folder + SVG03-embed.log
Artefakte:    01-artifacts\01-scripts\SVG03-embed.py
GOV-Konform:  JA
Teststatus:   GRÜN — durch EUMAXL freigegeben


2.6 SVG04 — Trace-Konvertierung (Option B)
-------------------------------------------

Alternative zu SVG03 — Vektorisierung via Inkscape --actions Trace.
Erzeugt echte SVG-Pfade. Experimentell — Qualität bildinhaltabhängig.
Timeout 120 Sekunden je Datei (Trace dauert länger als Embed).

Erkenntnis aus Test: Trace liest keine Bildmetadaten oder Semantik —
nur Helligkeits-/Farbwerte werden zu Pfaden. Für Fotos und komplexe
KI-Bilder ungeeignet. Für Strichzeichnungen und Icons sinnvoll.

Versionshinweis: --actions String ist Inkscape-versionsabhängig.
Bei Fehler Inkscape-Version prüfen.

Output:       SVG-Dateien im svg_target_folder + SVG04-trace.log
Artefakte:    01-artifacts\01-scripts\SVG04-trace.py
GOV-Konform:  JA — mit explizitem Versionshinweis
Teststatus:   GRÜN — läuft durch, Qualitätsurteil liegt beim Anwender


2.7 SVG05 — Resize / Compress
-------------------------------

Optionaler Schritt vor SVG03/SVG04. Optimiert Bilder auf A4 Querformat
bei 150 DPI (max 1754 × 1240px) via Pillow. Nur verkleinern — niemals
hochskalieren. Seitenverhältnis immer erhalten.
JPEG: Qualität 85%, optimize=True.
PNG: verlustfrei, optimize=True.
EXIF-Orientierung wird korrigiert (Handy-Fotos).
Originaldatei wird überschrieben — svg_overwrite=false schützt davor.

Nach SVG05 muss SVG01 erneut ausgeführt werden.

Erkenntnis aus Test:
  12.2 MB PNG → 2.4 MB nach Resize (Muni_Version_1.png, 4011x2965px)
  Kleine Dateien können minimal größer werden durch PNG-Metadaten-
  Neuschreiben — kein Fehler, Randfall bei sehr kleinen Dateien.

Abhängigkeit: pip install pillow

Output:       SVG05-resize.log
Artefakte:    01-artifacts\01-scripts\SVG05-resize.py
GOV-Konform:  JA
Teststatus:   GRÜN — durch EUMAXL freigegeben


2.8 SVG06 — Handoff-Report
----------------------------

Liest alle vorhandenen SVG-Reihe Logs (SVG00–SVG05) und gibt einen
konsolidierten Gesamtstatus aus. Prüft ob alle erwarteten SVG-
Zieldateien vorhanden sind (VORHANDEN / LEER / FEHLEND). Zeigt
Umbenennungen aus SVG02 explizit aus. Abschluss-Banner OK / WARNUNG.
Nicht ausgeführte Scripts werden als "nicht vorhanden" markiert —
kein Fehler, nur Info.

Output:       SVG06-handoff_report.log
Artefakte:    01-artifacts\01-scripts\SVG06-handoff_report.py
GOV-Konform:  JA
Teststatus:   GRÜN — durch EUMAXL freigegeben


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Reihenname SVG statt INK
  Auslöser:    Ursprüngliche Bezeichnung INK — auf Wunsch EUMAXL umbenannt
  Ergebnis:    Reihe heißt SVG (SVG00–SVG06)
  Begründung:  SVG beschreibt Zielformat und Zweck klarer als INK
  GOV-Bezug:   GOV 6.3 — Namen dienen der Lesbarkeit
  Auswirkung:  Alle Scripts, Config und Dokumentation tragen SVG-Präfix
  Rückwirkung: NEIN


Entscheidung: 1 Script = 1 Aufgabe konsequent — 7 Scripts
  Auslöser:    Erster Entwurf hatte zu viel Logik pro Script gebündelt —
               Korrektur durch EUMAXL
  Ergebnis:    7 Scripts mit je einer fachlichen Wirkung und einem Output
  Begründung:  GOV 6.10 explizit — deterministisch, nachvollziehbar
  GOV-Bezug:   GOV 6.10
  Auswirkung:  Jeder Schritt einzeln ausführbar, testbar, austauschbar
  Rückwirkung: NEIN


Entscheidung: Inkscape-Pfad in svg_config.txt, nicht in root.cfg
  Auslöser:    Designfrage — root.cfg oder reihenspezifische Config
  Ergebnis:    svg_config.txt — vollständiger absoluter Pfad
  Begründung:  root.cfg führt Blueprint-Systempfade. Inkscape ist externes
               Tool — gehört in Reihen-Config analog zu nbx_config.txt
  GOV-Bezug:   GOV 6.10, GOV 1.4 Explizitheit
  Auswirkung:  Kein Eingriff in root.cfg bei Inkscape-Pfadänderung
  Rückwirkung: NEIN


Entscheidung: Dateinamen-Bereinigung als eigener Script-Schritt SVG02
  Auslöser:    Leerzeichen und Sonderzeichen destabilisieren Inkscape CLI
  Ergebnis:    SVG02 als eigenständiger Bereinigungsschritt
  Begründung:  Trennung Erfassung / Bereinigung / Konvertierung —
               jeder Schritt hat prüfbaren Output
  GOV-Bezug:   GOV 6.10, GOV 1.4
  Auswirkung:  Umbenennungen im Log nachvollziehbar, in SVG06 ausgewiesen
  Rückwirkung: NEIN


Entscheidung: Zielordner nicht automatisch anlegen
  Auslöser:    Designentscheidung Fehlerbehandlung SVG00
  Ergebnis:    Fehlender Zielordner erzeugt Warnung — kein Auto-Create
  Begründung:  Verhindert unbeabsichtigtes Schreiben in falsche Pfade
  GOV-Bezug:   GOV 1.4, GOV 1.5 Stabilität über Komfort
  Auswirkung:  Anwender legt Zielordner vor erstem Lauf manuell an
  Rückwirkung: NEIN


Entscheidung: svg_overwrite=false als sicherer Default
  Auslöser:    Designentscheidung Fehlerbehandlung
  Ergebnis:    Vorhandene SVG werden standardmäßig nicht überschrieben
  Begründung:  Schutz vor unbeabsichtigtem Verlust manuell bearbeiteter SVGs
  GOV-Bezug:   GOV 1.5 Stabilität über Komfort
  Auswirkung:  Erster Lauf auf bestehende Ordner ist immer sicher
  Rückwirkung: NEIN


Entscheidung: SVG01 nach SVG02 und nach SVG05 erneut ausführen
  Auslöser:    SVG03 meldete "Quelldatei nicht gefunden" nach SVG02-Umbenennung
  Ergebnis:    Explizite Reihenfolgeregel — kein automatischer Inventar-Update
               in SVG02/SVG05 (Option B verworfen als Optimierung)
  Begründung:  GOV 6.10 — 1 Script = 1 Aufgabe. Inventar-Update ist
               Aufgabe von SVG01, nicht von SVG02 oder SVG05.
  GOV-Bezug:   GOV 6.10
  Auswirkung:  Reihenfolge dokumentiert in Script-Headern und Sprint-Doku
  Rückwirkung: NEIN


Entscheidung: SVG05 Resize als optionaler Schritt — eigenes Script
  Auslöser:    12MB PNG → 17MB SVG durch Base64 — nicht MD/Web-tauglich
  Ergebnis:    SVG05 als optionaler Resize/Compress Schritt vor Konvertierung
               Zielauflösung: 150 DPI, max 1754 × 1240px (A4 Querformat)
  Begründung:  Optionaler Schritt — nicht jedes Bild braucht Resize.
               Eigenes Script hält GOV 6.10 ein.
  GOV-Bezug:   GOV 6.10, GOV 1.4
  Auswirkung:  Workflow mit SVG05 deutlich schlanker — 12MB → 2.4MB getestet
  Rückwirkung: NEIN


Entscheidung: SVG06 Handoff-Report liest Logs statt eigene Prüflogik
  Auslöser:    Designentscheidung — Prüfung aus vorhandenen Logs ableiten
  Ergebnis:    SVG06 liest alle SVG-Reihe Logs und konsolidiert Status
  Begründung:  Logs sind Single Source of Truth für den Laufstatus.
               Keine doppelte Prüflogik — GOV 6.10.
  GOV-Bezug:   GOV 6.10, GOV 6.4 Führung
  Auswirkung:  SVG06 funktioniert auch wenn einzelne Scripts nicht
               ausgeführt wurden — zeigt nur was vorhanden ist
  Rückwirkung: NEIN


Entscheidung: SVG04 Trace — Versionsabhängigkeit explizit dokumentiert
  Auslöser:    Inkscape CLI --actions für Trace ist versionsabhängig
  Ergebnis:    Expliziter Hinweis im Script-Header — kein stilles Raten
  Begründung:  GOV 2.9 Implizit vs. Explizit
  GOV-Bezug:   GOV 2.9, GOV 1.4
  Auswirkung:  Bei Fehler: Inkscape-Version prüfen, ggf. Folge-Session
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Keine Abweichungen.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Erster Sprint-Entwurf hatte GOV 6.10 nicht konsequent
  angewendet — zu viel Logik pro Script. Nach Korrektur durch EUMAXL
  vollständig überarbeitet. Lerneffekt dokumentiert in Lessons Learned.

⚠ Verhaltenshinweis: SVG00 erster Lauf fehlgeschlagen — HLP00 Keys mit
  spitzen Klammern (<rootfolder>) nicht korrekt verwendet. Nach Analyse
  von HLP00_resolve_root.py sofort korrigiert.

⚠ Verhaltenshinweis: SVG02 parse_inventar las Zusammenfassungszeilen als
  Dateinamen — zwei Iterationen bis saubere Zeichenposition-basierte
  Lösung mit zusätzlicher Punkt-Prüfung funktionierte.

⚠ Verhaltenshinweis: Option B (automatischer Inventar-Update in SVG02)
  als "sexy aber nicht für ersten Step" von EUMAXL verworfen —
  GOV-konform als offener Punkt für Folge-Sprint dokumentiert.

⚠ Verhaltenshinweis: SVG05 Resize kam als ungeplanter Schritt während
  der Session hinzu — Größenproblem (12MB→17MB) erst durch Test sichtbar.
  Sprint-Scope wurde mit EUMAXL-Freigabe erweitert. GOV 7.5 (Feature-Zuwachs
  während Sprint) — Entscheidung explizit dokumentiert.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt                              | GOV-Bezug     | Status | Nächste Aktion                        |
|-----------------------------------|---------------|--------|---------------------------------------|
| SVG01 Auto-Update nach SVG02/SVG05 | GOV 6.10     | offen  | Folge-Sprint bei Bedarf               |
| SVG04 Trace CLI verifizieren       | GOV 2.9      | offen  | Testlauf mit Strichzeichnung EUMAXL   |
| FLW-Eintrag SVG-Reihe             | keiner        | offen  | Folge-Sprint nach Stabilisierung      |
| Rekursion optional via Config      | GOV 1.4      | offen  | Folge-Sprint bei Bedarf               |
| CLE-Eintrag für 99-svg_TMP        | keiner        | offen  | EUMAXL entscheidet ob CLE nötig       |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — 01-artifacts\01-scripts\ + 99-doku\
GitHub-Sync:                      AUSSTEHEND — EUMAXL entscheidet
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Sprint-Dokument vor Script-Erstellung als Planungsgrundlage —
    Korrekturen möglich bevor Code entsteht
  - 1-Script-1-Aufgabe nach Korrektur durch EUMAXL konsequent durchgezogen —
    jeder Schritt einzeln testbar, Fehler sofort isolierbar
  - HLP00 nach Fehler sofort gelesen — Ursache (fehlende spitze Klammern)
    in einem Durchlauf gefunden und korrigiert
  - Produktiver Testlauf durch EUMAXL nach jedem Script —
    Fehler früh gefunden, nie akkumuliert

Was beim nächsten Mal anders gemacht werden sollte:
  - GOV 6.10 von Beginn an auf Reihen-Struktur anwenden —
    nicht erst nach Korrektur durch EUMAXL
  - HLP00 vor erstem Script lesen — Key-Format (<rootfolder>)
    wäre sofort bekannt gewesen
  - Tabellen-Parse-Logik mit festen Zeichenpositionen von Anfang an —
    split() ist bei Dateinamen mit Leerzeichen immer falsch

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - SVG-Reihe als neue Reihe in naming_and_structure_S102 eintragen:
    Sprint / Backlog anlegen: JA — EUMAXL entscheidet Zeitpunkt
  - Pillow als neue Abhängigkeit in Install.txt dokumentieren:
    Sprint / Backlog anlegen: JA — nächster Install.txt Sprint

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[naming_and_structure_S102]]        Namenskonventionen
[[DEV_Sprint_SVGREIHE_S102]]         Vorheriger SVG-Sprint

---

================================================================================
SVG-REIHE IMG2SVG — SPRINT (DEV) | S1.04 | 2026-04-12 | R+MUNI Blueprint
================================================================================
