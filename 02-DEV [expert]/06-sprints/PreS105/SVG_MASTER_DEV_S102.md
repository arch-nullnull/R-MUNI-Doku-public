================================================================================
SVG MASTER — DESIGNSYSTEM & AUFBAUREGELN
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : SVG_MASTER_DEV_S102
Tag             : #svg #design #creative #dev #s102
Datum           : 2026-04-12
Stage           : S1.02
Status          : AKTIV
Verantwortlich  : EUMAXL
Ablageort       : R+MUNI Doku-internal\07-creative\SVG_MASTER_DEV_S102.md
================================================================================

---
title: "SVG Master — Designsystem & Aufbauregeln"
stage: S1.02
status: "AKTIV"
typ: "Creative"
datum: "2026-04-12"
autor: EUMAXL
tags: [rmuni, blueprint, svg, design, creative, dev, s102]
---


================================================================================
ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument ist die Single Source of Truth für das R+MUNI SVG Designsystem.
Es beschreibt Farben, Formen, Abstände und Aufbauregeln so dass Claude aus dem
Quellenordner heraus konsistente SVGs ableiten kann — ohne Drift und ohne
eigene Designentscheidungen zu treffen.

Dieses Dokument gilt für alle SVG-Ausgaben im R+MUNI Kontext.
Abweichungen erfordern explizite Freigabe durch EUMAXL.


================================================================================
1. TECHNISCHE GRUNDREGELN
================================================================================

viewBox:          immer 680px breit — Höhe nach Inhalt (letztes Element + 20px)
xmlns:            xmlns="http://www.w3.org/2000/svg"
role:             role="img" mit <title> und <desc> als erste Kindelemente
Hintergrund:      transparent — kein äußeres rect mit Hintergrundfarbe
Font:             font-family: sans-serif — kein Google Font, kein CDN
Kommentare:       keine SVG-Kommentare im Output (<!-- --> sparen Tokens)

CSS-Klassen (immer per <style> in <defs> definieren):
  .th   font-size: 14px; font-weight: 600;
  .ts   font-size: 12px; font-weight: 400;
  .muted  fill: #555550;

Arrow-Marker (immer in <defs> wenn Pfeile verwendet):
  <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5"
          markerWidth="6" markerHeight="6" orient="auto-start-reverse">
    <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke"
          stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
  </marker>


================================================================================
2. KACHEL-IN-KACHEL DESIGNSYSTEM
================================================================================

Das ist das primäre Darstellungssystem für alle R+MUNI Inhalts-SVGs.
Jede Inhaltsgruppe wird als große Kachel dargestellt.
Jeder Inhaltspunkt innerhalb der Gruppe wird als Sub-Kachel dargestellt.

--------------------------------------------------------------------------------
2.1 GROSSE KACHEL (Container)
--------------------------------------------------------------------------------

Aufbau:
  Schritt 1: Hintergrund-Rect (volle Kachelhöhe, helle Farbe, rx="10")
  Schritt 2: Header-Rect (oben, dunkle Farbe, rx="10", gleiche Breite)
  Schritt 3: Füll-Rect direkt unter dem Header (schließt den rx-Bogen nach
             unten ab, gleiche Farbe wie Header, keine rx)
  Schritt 4: Titel-Text im Header (weiß, .th, font-size="15", zentriert)
  Schritt 5: Subtitle-Text im Header (helle Farbe der Reihe, .ts, zentriert)

Maße:
  Breite:         148px (4 Spalten) oder 192px (3 Spalten) oder 624px (voll)
  Header-Höhe:    46px
  Füll-Rect:      18px hoch, beginnt bei y = Header-y + 28
  rx:             10 für Container und Header, 0 für Füll-Rect
  stroke-width:   0.5 (Container), 1 für Säule 04 / Synthese-Kacheln
  Padding innen:  12px links und rechts (Sub-Kacheln beginnen bei x + 12)

Abschluss-Badge (ganz unten in der Kachel):
  Position:       y = Kachel-Ende - 34
  Höhe:           22px
  rx:             6
  Farbe:          dunkelster Ton der Reihe
  Text:           weiß, .ts, font-weight="600", zentriert

--------------------------------------------------------------------------------
2.2 SUB-KACHEL (Inhaltspunkt)
--------------------------------------------------------------------------------

Aufbau:
  <rect> mit mittlerem Farbton der Reihe als fill
  <rect> stroke mit dunklerem Ton der Reihe, stroke-width="0.5"
  <text> zentriert, .ts, font-weight="600", dunkler Textton der Reihe
         dominant-baseline="central", text-anchor="middle"

Maße:
  Breite:         Kachelbreite - 24px (12px Padding je Seite)
  Höhe:           24px (einzeilig) / 36px (zweizeilig)
  rx:             6
  Abstand:        30px zwischen Sub-Kacheln (y-Abstand von Oberkante zu Oberkante)
  Erste Sub-y:    Header-y + Header-Höhe + Füll-Rect-Höhe + 16px

Zweizeilige Sub-Kacheln:
  Zeile 1: y = Sub-Kachel-y + 12, dominant-baseline="central"
  Zeile 2: y = Sub-Kachel-y + 27, dominant-baseline="central"

Divider (optional, zwischen Inhalt und Beschreibungstext):
  <line> stroke="#cccccc" oder Reihen-Farbe mit opacity="0.4"
  stroke-width="0.5", mit Padding (x = Kachel-x + 12 bis Kachel-x + Breite - 12)

Beschreibungstext unter Divider (.ts .muted, zentriert, Zeilenabstand 18px)


================================================================================
3. FARBSYSTEM — FIXES MAPPING
================================================================================

Jede der vier Hauptgruppen hat eine fixe Farbreihe.
Die Zuordnung ist verbindlich und darf nicht variiert werden.

--------------------------------------------------------------------------------
01 — TEAL (Visuelle Übersicht / Setup)
--------------------------------------------------------------------------------
  Kachel-Hintergrund:   #E1F5EE    stroke: #0F6E56
  Header:               #1D9E75
  Füll-Rect:            #1D9E75
  Subtitle:             #E1F5EE
  Sub-Kachel fill:      #9FE1CB    stroke: #1D9E75
  Sub-Kachel Text:      #04342C
  Badge:                #0F6E56    Text: #ffffff

--------------------------------------------------------------------------------
02 — PURPLE (Dokumentation / Schulung)
--------------------------------------------------------------------------------
  Kachel-Hintergrund:   #EEEDFE    stroke: #534AB7
  Header:               #7F77DD
  Füll-Rect:            #7F77DD
  Subtitle:             #EEEDFE
  Sub-Kachel fill:      #AFA9EC    stroke: #534AB7
  Sub-Kachel Text:      #26215C
  Badge:                #534AB7    Text: #ffffff

--------------------------------------------------------------------------------
03 — AMBER (Struktur & Vorlagen / Schulung alternativ)
--------------------------------------------------------------------------------
  Kachel-Hintergrund:   #FAEEDA    stroke: #854F0B
  Header:               #BA7517
  Füll-Rect:            #BA7517
  Subtitle:             #FAEEDA
  Sub-Kachel fill:      #FAC775    stroke: #BA7517
  Sub-Kachel Text:      #412402
  Badge:                #854F0B    Text: #ffffff

--------------------------------------------------------------------------------
04 — CORAL (AI-Nutzung / Support)
--------------------------------------------------------------------------------
  Kachel-Hintergrund:   #FAECE7    stroke: #993C1D  stroke-width: 1
  Header:               #D85A30
  Füll-Rect:            #D85A30
  Subtitle:             #FAECE7
  Sub-Kachel fill:      #F0997B    stroke: #D85A30
  Sub-Kachel Text:      #4A1B0C
  Badge:                #993C1D    Text: #ffffff

--------------------------------------------------------------------------------
SONDERFARBEN (Addon-Block, Warnungen, neutrale Kacheln)
--------------------------------------------------------------------------------
  Blau (Addon kostenpflichtig):
    Kachel:   #E6F1FB  stroke: #185FA5   Text: #0C447C
  Grün (Addon kostenlos):
    Kachel:   #EAF3DE  stroke: #3B6D11   Text: #27500A
  Rot (Kostenpflichtig-Badge):
    fill:     #E24B4A  Text: #ffffff
  Grün (0 EUR Badge):
    fill:     #1D9E75  Text: #ffffff
  Grau (neutrale Blöcke):
    Kachel:   #F1EFE8  stroke: #5F5E5A   Text: #2C2C2A
  Amber-Block (KI-Toolset):
    Kachel:   #FAEEDA  stroke: #854F0B   Text: #633806
  ACHTUNG-Banner:
    fill:     #FAECE7  stroke: #993C1D   Text: #712B13  font-weight: 700


================================================================================
4. LAYOUT-REGELN
================================================================================

4 Spalten (Standardlayout):
  Spalte 1: x=28   Breite=148
  Spalte 2: x=188  Breite=148
  Spalte 3: x=348  Breite=148
  Spalte 4: x=508  Breite=148
  Spaltenlücke: 12px

3 Spalten:
  Spalte 1: x=28   Breite=192
  Spalte 2: x=244  Breite=192
  Spalte 3: x=460  Breite=192
  Spaltenlücke: 24px

Volle Breite (Banner, KI-Block etc.):
  x=28  Breite=624

Titel (oben):
  x=340, y=26, text-anchor="middle", font-size="15", .th, fill="#1a1a1a"

Untertitel-Banner (optional, unter Titel):
  y=40, Höhe=26, rx="6", fill="#F1EFE8", stroke="#B4B2A9", stroke-width="0.5"
  Text: .ts .muted, zentriert

Synthese-Pfeile (01+02+03 → 04):
  Vertikale Linien von Kacheln 01-03 nach unten
  Horizontale Verbindungslinie
  Pfeil von rechts hoch zu Kachel 04
  stroke="#aaaaaa", stroke-width="0.5"

Gestrichelte Ableitung (EXPERT aus DEV):
  Pfeil: stroke-dasharray="4 3", stroke="#993C1D", marker-end="url(#arrow)"
  Kachel: stroke-dasharray="6 4", fill="none"
  Sub-Kacheln: stroke-dasharray="4 3", fill="none"


================================================================================
5. AUFBAU-ANWEISUNG FÜR CLAUDE
================================================================================

Wenn EUMAXL ein SVG mit diesem Designsystem anfordert gilt:

1. Dieses Dokument ist führend — kein Drift aus Training oder Memory
2. Inhalte kommen aus dem Quelldokument (svg_inhalte.md oder Chat-Input)
3. Farbe folgt der Gruppe — nicht der Position oder Ästhetik
4. Kachelhöhe wird aus Anzahl der Sub-Kacheln berechnet:
     Höhe = Header(46) + FüllRect(18) + (Anzahl × 30) + Padding(16) + Badge(34)
5. viewBox-Höhe = letztes Element (y + Höhe) + 20px
6. Keine Lizenzzeilen, Stage-Infos oder Footer ohne expliziten Auftrag
7. Nie Plaintext-Zeilen innerhalb einer Kachel — immer Sub-Kacheln
8. Ausgabe: .svg File + present_files — nie nur gerendert


================================================================================
6. INHALTS-EINGABEFORMAT FÜR NEUE SVGs
================================================================================

So muss EUMAXL den Inhalt strukturieren damit Claude sauber ableiten kann:

  ## SVG — Dateiname (svg_beispiel.svg)

  ### Titel
  Sichtbarer Titel oben

  ### Untertitel (optional)
  Text für den grauen Banner unter dem Titel

  ### Kachel 01 — Name der Kachel
  Farbreihe: TEAL
  Subtitle: Kurze Beschreibung
  - Punkt 1
  - Punkt 2 (zweizeilig wenn zu lang: Zeilenumbruch mit |)
  Badge: Text im Abschluss-Badge

  ### Kachel 02 — Name der Kachel
  Farbreihe: PURPLE
  ...


================================================================================
SVG_MASTER_DEV_S102 | 2026-04-12 | R+MUNI Blueprint | 07-creative
================================================================================
