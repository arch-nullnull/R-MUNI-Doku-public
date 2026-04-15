================================================================================
SVG-REIHE — PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : SVG_principles_DEV_S105
Tag             : #principles #svg #img2svg #dev #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-04-12
Letzte Änderung : 2026-04-14 — S105-Update | Basis: SVG_principles_DEV_S104.md
Ablageort       : 01-principles\SVG_principles_DEV_S105.md
================================================================================


ZWECK DIESES DOKUMENTS
--------------------------------------------------------------------------------
Was erklärt dieses Dokument — und für wen.

Zielgruppe: DEV

Dieses Dokument erklärt:
  - Was die SVG-Reihe ist und wozu sie dient
  - Welche Designentscheidungen ihr zugrunde liegen
  - Was der Anwender davon hat und was nicht
  - Was vor dem ersten Start bekannt sein muss


================================================================================
1. WAS IST DIE SVG-REIHE?
================================================================================

Die SVG-Reihe automatisiert die Konvertierung von Bilddateien (PNG, JPG und
weitere Rasterformate) in SVG — via Inkscape CLI. Was bisher manuell in
Inkscape gemacht wurde, läuft jetzt per Script: Ordner konfigurieren,
Script starten, SVG liegt im Zielordner.

Kurz gesagt:
  Rasterbild rein — SVG raus. Konfigurierbar, protokolliert, reproduzierbar.

Warum das relevant ist:
  R+MUNI nutzt SVG für Dokumentation, README und Obsidian-Einbettung.
  Manuelle Einzelkonvertierung in Inkscape ist bei mehreren Dateien
  zeitaufwendig und nicht reproduzierbar. Die SVG-Reihe schließt diese Lücke.


================================================================================
2. WAS DIE ZIELGRUPPE DAVON HAT
================================================================================

Die SVG-Reihe ermöglicht:
  - Automatisierte Batch-Konvertierung ganzer Ordner in einem Lauf
  - Zwei Konvertierungsoptionen: Embed (schnell) und Trace (vektorisiert)
  - Optionale Größenoptimierung vor der Konvertierung (A4, 150 DPI)
  - Vollständige Protokollierung — jeder Schritt nachvollziehbar
  - Dateinamen-Bereinigung vor der Konvertierung (Leerzeichen, Sonderzeichen)
  - Abschlussprüfung ob alle erwarteten SVGs vorhanden sind

Was es nicht leistet:
  - Kein Design-Eingriff — SVGs werden nicht nachbearbeitet
  - Kein Vektorisieren von Fotos zu brauchbaren Ergebnissen (→ Embed verwenden)
  - Kein rekursives Scannen von Unterordnern
  - Keine Semantik-Extraktion aus Bildinhalten
  - Keine GUI oder Fortschrittsanzeige


================================================================================
3. GRUNDPRINZIPIEN
================================================================================

3.1 Ein Script — eine Aufgabe
------------------------------
Jedes Script der SVG-Reihe erfüllt genau eine fachliche Wirkung und erzeugt
genau einen Output. Kein Script macht zwei Dinge gleichzeitig.

Konkret bedeutet das:
  SVG01 scannt — aber benennt nicht um.
  SVG02 benennt um — aber konvertiert nicht.
  SVG03 konvertiert — aber prüft nicht ob alles da ist.
  Wer einen Schritt überspringen will, kann das — die anderen laufen trotzdem.


3.2 Konfiguration an einem Ort
--------------------------------
Alle Parameter der SVG-Reihe stehen in einer einzigen Datei: svg_config.txt.
Kein Script enthält hardcoded Pfade oder Werte. Wer die Config ändert,
ändert das Verhalten aller Scripts — ohne Code anfassen zu müssen.

Konkret bedeutet das:
  Neuer Quellordner → eine Zeile in svg_config.txt ändern.
  Anderer Inkscape-Pfad → eine Zeile in svg_config.txt ändern.
  Alles andere bleibt unberührt.


3.3 Jeder Lauf ist protokolliert
----------------------------------
Jedes Script schreibt ein Log in 02-stages\99-logs\. Der Log enthält
was verarbeitet wurde, was übersprungen wurde und was fehlgeschlagen ist.
SVG06 liest alle Logs und gibt einen Gesamtstatus aus.

Konkret bedeutet das:
  Nach einem Lauf ist immer nachvollziehbar was passiert ist —
  auch Tage später. Kein stilles Verarbeiten, kein verlorener Status.


3.4 Sicher by Default
-----------------------
svg_overwrite=false ist der Standard. Vorhandene SVGs werden nicht
überschrieben solange der Anwender das nicht explizit aktiviert.
Der Zielordner wird nicht automatisch angelegt — er muss existieren.

Konkret bedeutet das:
  Ein versehentlicher Doppellauf überschreibt keine manuell
  nachbearbeiteten SVGs. Explizites Aktivieren liegt beim Anwender.


3.5 Embed vs. Trace — zwei Wege, zwei Zwecke
----------------------------------------------
Embed (SVG03): Das Rasterbild wird als Base64-Objekt in eine SVG-Hülle
verpackt. Schnell, verlustfrei, immer gleich. SVG ist größer als das
Original (~133% durch Base64). Für alle Bildtypen geeignet.

Trace (SVG04): Inkscape vektorisiert das Bild — echte SVG-Pfade,
editierbar in Inkscape. Funktioniert gut für Strichzeichnungen und Icons.
Für Fotos und komplexe KI-Bilder meist unbrauchbar.

Konkret bedeutet das:
  KI-generierte Visuals, Screenshots, Fotos → SVG03 Embed.
  Strichzeichnungen, Logos, Icons mit klaren Konturen → SVG04 Trace testen.


3.6 Größe optimieren vor Konvertierung
----------------------------------------
Ein 12MB PNG wird als Embed-SVG ca. 17MB groß — nicht geeignet für
Obsidian, README oder MD-Dokumentation. SVG05 optimiert das Bild vor der
Konvertierung auf A4 Querformat bei 150 DPI (max 1754 × 1240px).
Nur verkleinern — niemals hochskalieren. Seitenverhältnis bleibt erhalten.

Konkret bedeutet das:
  SVG05 vor SVG03/SVG04 ausführen wenn Bilder für Dokumentation bestimmt
  sind. Testergebnis: 12.2MB → 2.4MB (Faktor ~5).


3.7 Inventar als gemeinsame Basis
-----------------------------------
SVG01 erstellt das Inventar — alle nachfolgenden Scripts lesen es.
Nach SVG02 (Umbenennung) oder SVG05 (Resize) muss SVG01 erneut ausgeführt
werden damit das Inventar den aktuellen Stand widerspiegelt.

Konkret bedeutet das:
  SVG01 ist kein einmaliger Schritt — es ist der Taktgeber der Reihe.
  Wer diesen Schritt überspringt, arbeitet mit veralteten Dateinamen.


================================================================================
4. VORAUSSETZUNGEN
================================================================================

Bevor du mit der SVG-Reihe arbeitest:
  - R+MUNI ist installiert und HLP00 läuft grün (root.cfg vorhanden)
  - Inkscape ist installiert — Pfad zur inkscape.exe bekannt
  - svg_config.txt liegt in <rootfolder>\99-doku\ und ist befüllt
  - Quellordner mit Bilddateien existiert
  - Zielordner existiert (wird nicht automatisch angelegt)
  - Scripts liegen in 01-artifacts\01-scripts\
  - PowerShell 7 gestartet in 01-artifacts\01-scripts\
  - Pillow installiert wenn SVG05 verwendet wird:
    pip install pillow


================================================================================
5. ABGRENZUNG UND GRENZEN
================================================================================

Die SVG-Reihe ist Teil von R+MUNI — aber nicht alles.

Was hier geregelt ist:
  - Automatisierte Bild-zu-SVG Konvertierung via Inkscape CLI
  - Dateinamen-Bereinigung vor der Konvertierung
  - Größenoptimierung für Dokumentationszwecke
  - Protokollierung und Abschlussprüfung

Was woanders geregelt ist:
  - SVG-Design und Gestaltungsregeln → [[SVG_MASTER_DEV_S102]]
  - Ablage und Benennung von SVG-Artefakten → [[naming_and_structure_S104]]
  - Cleaning des Arbeitsordners → CLE-Reihe
  - Orchestrierung mehrerer Reihen → FLW-Reihe

Was die SVG-Reihe explizit nicht tut:
  - Vorhandene SVGs inhaltlich verändern
  - Bildanalyse oder Metadaten-Extraktion
  - Konvertierung von SVG zurück zu Raster


================================================================================
SUPPORT UND FEEDBACK
================================================================================

Fragen oder etwas unklar?

→ Ticketsystem: https://ims-blueprint-ticketsystem.atlassian.net/helpcenter/RMNP/


================================================================================
SVG_principles_DEV | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
