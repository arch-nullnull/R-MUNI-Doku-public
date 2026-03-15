================================================================================
SPRINT DEFINITION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-5.5-CleaningRun
Datum               : 2026-03-12
Stage               : 5 (aktiv) — Cleaning Sub-Stage
Status              : Sprint Definition — noch nicht implementiert
Erstellt durch      : Entwickler + Claude (Pair-Session)
Vorgänger           : Stage 5.0 (Portal live, GOV-Restore, CSV06-Fix, M2B01-Fix)
Nachfolger          : Stage 5.7 — Restart Blueprint Beta Endkunde
================================================================================


--------------------------------------------------------------------------------
1. AUSGANGSLAGE & MOTIVATION
--------------------------------------------------------------------------------

1.1 Ist-Zustand nach Stage 5.0
--------------------------------
Stage 5.0 hat in kurzer Zeit folgende Meilensteine gesetzt:

  - JSM Portal RMNP live (3 Request-Typen, Beta-Endkunden-ready)
  - Global GOV vollständig wiederhergestellt (Kapitel 1–12)
  - CSV06 Bugfix: run-scope-aware, endswith()-Logik korrekt
  - M2B01 Pfad-Bugfix: run-scope.txt Pfad korrekt aufgelöst
  - Sprint-DEF CSV Refactoring erstellt (SPRINT-CSV-Refactoring)
  - root.txt neu gebaut mit zukunftsfähiger Pfad-Logik

Diese Aktivität hat den Blueprint in einem Zustand hinterlassen in dem
die Grundlogik stimmt, aber die physische Struktur hinter der neuen
root.txt-Logik nachziehen muss.

1.2 Konkrete Diskrepanz
------------------------
root.txt definiert bereits:

  <models>   = <rootfolder>\00-model
  <artifacts> = <rootfolder>\01-artifacts
  <stages>   = <rootfolder>\02-stages

Die physische Ordnerstruktur zeigt jedoch noch:

  01-model
  02-artifacts
  03-stages

Zusätzlich liegen Doku-Dateien (.txt, Sprint-DEFs, Principles, How2,
GOV) aktuell direkt im Blueprint-Root — ohne Trennung zwischen
interner Entwicklungsdoku und öffentlich zugänglicher Dokumentation.

1.3 Auslöser
-------------
Auslöser-Typ : Strukturbereinigung (Entwicklerwunsch, GOV 10.3/10.5)

Der Cleaning Run ist keine inhaltliche Weiterentwicklung — er schafft
die saubere Basis auf der Stage 5.7 (Beta Endkunde Restart) aufbauen
kann. Struktur vor Funktion: kein neuer Code, keine neue Logik,
keine neuen Scripts.


--------------------------------------------------------------------------------
2. ENTSCHEIDUNGEN & GRUNDSÄTZE DIESES SPRINTS
--------------------------------------------------------------------------------

2.1 Kein neuer Code, keine neue Logik
---------------------------------------
Dieser Sprint erzeugt keinen neuen Funktionscode. Alle Änderungen
betreffen ausschließlich:
  - Ordner-Umbenennung / Neustrukturierung
  - Pfad-Referenzen in bestehenden Scripts (nur Strings, keine Logik)
  - Datei-Extensions und Ablageregeln
  - GitHub-Konfiguration
  - Doku-Seitentest (HLP09)

2.2 Stage-3/4-Scripts bleiben read-only
-----------------------------------------
Pfadanpassungen in Stage-3/4-Scripts sind ausschließlich dann zulässig
wenn sie durch die Ordner-Umbenennung erzwungen werden und
ausschließlich Pfad-Strings betreffen. Keine Logikänderung.
Jede Anpassung wird in der Dev-Doku explizit festgehalten.

2.3 Reihenfolge: Struktur zuerst, dann Scripts
------------------------------------------------
Erst wenn die neue Ordnerstruktur physisch steht und root.txt
verifiziert ist, werden Script-Referenzen angepasst.
Kein Script wird geändert bevor die Ziel-Struktur finalisiert ist.

2.4 Offene Entscheidungen — werden im Sprint geklärt
------------------------------------------------------

  OFFEN A: root.txt Extension
    Bleibt root.txt als .txt — oder wird zu root.cfg umbenannt?
    Entscheidung fällt im Sprint vor der Umbenennung.
    Auswirkung: alle Script-Referenzen auf root.txt / root.cfg anpassen.

  OFFEN B: .gitignore Inhalt
    Welche Dateitypen und Ordner soll GitHub nicht tracken?
    Kandidaten: .bak, .log, .obsidian/, Temp-Files
    Entscheidung fällt im Sprint — .gitignore wird angelegt,
    Inhalt wird nach Entscheidung befüllt.


--------------------------------------------------------------------------------
3. SPRINT-ZIELE
--------------------------------------------------------------------------------

3.1 Ziel 1 — Ordnerstruktur auf root.txt-Logik synchronisieren
----------------------------------------------------------------
Die physischen Ordner werden auf das in root.txt definierte Schema
umbenannt:

  IST               →  SOLL
  01-model          →  00-model
  02-artifacts      →  01-artifacts
  03-stages         →  02-stages

Unterordner bleiben strukturell unverändert — nur die Top-Level-
Nummern ändern sich.

Vorgehen: Manuell in Windows Explorer, dokumentiert in Dev-Doku.
Grund: Keine automatisierte Umbenennung — zu hohes Risiko für
GitHub-Tracking und Script-Referenzen ohne kontrollierten Ablauf.

3.2 Ziel 2 — Doku-Struktur bereinigen
---------------------------------------
Dokumentationsdateien werden aus dem Blueprint-Root in die
definierten Doku-Bereiche verschoben (gemäß root.txt):

  <doku>       = R+MUNI Doku\R+MUNI Doku-internal
  <dokupublic> = R+MUNI Doku\R+MUNI Doku-public
  <creative>   = R+MUNI Doku\R+MUNI Doku-creative

Zuordnungsregeln werden im Sprint definiert:
  - Sprint-DEFs, Sprint-DEV-Dokus   →  internal
  - Principles, How2                →  internal
  - Global_GOV                      →  internal
  - README.md                       →  public (bleibt im Root für GitHub)
  - Install.txt                     →  public (bleibt im Root für GitHub)
  - Rosetta Stone Blöcke            →  zu klären im Sprint

Blueprint-Root behält nur was für GitHub-Sichtbarkeit zwingend
notwendig ist.

3.3 Ziel 3 — Script-Referenzen nachziehen
-------------------------------------------
Nach Abschluss von Ziel 1: alle Scripts die Pfade auf 01-model /
02-artifacts / 03-stages referenzieren werden auf die neuen Nummern
aktualisiert.

Vorgehen: Flow für Flow systematisch durchgehen.
  - HLP-Reihe
  - CSV-Reihe
  - XML-Reihe
  - M2B-Reihe
  - ATL-Reihe
  - FLW-Reihe

Nur Pfad-Strings werden geändert. Jede Änderung wird protokolliert.
Kein Script wird inhaltlich verändert.

3.4 Ziel 4 — Filetypen-Konvention festlegen und anwenden
----------------------------------------------------------
Klare Regel: welche Extension wofür.

  .py    →  Python Scripts (unveränderlich)
  .txt   →  Konfiguration, Doku, Mapping (Blueprint-Standard)
  .md    →  Nur README und öffentliche GitHub-Seiten
  .log   →  Nur in 02-stages/99-logs — nie im Root oder Scripts-Ordner
  .bak   →  Archi-Backup — nie in GitHub (→ .gitignore)
  .cfg   →  OFFEN (abhängig von Entscheidung OFFEN A)
  .ajs   →  jArchi Scripts (unveränderlich)

Diese Konvention wird in einem eigenen Doku-Dokument festgehalten
(File-Extension-Konvention.txt) und in SCRIPT-BAUKASTEN.txt referenziert.

3.5 Ziel 5 — GitHub Sync sauber herrichten
--------------------------------------------
  - .gitignore anlegen (Inhalt: OFFEN B)
  - .gitattributes prüfen auf Konsistenz mit neuer Struktur
  - Nach Strukturbereinigung: GitHub Sync testen
    → Kein ungewolltes Tracking von .bak / .log / .obsidian

3.6 Ziel 6 — HTML Doku-Publishing testen (HLP09)
-------------------------------------------------
Nach Bereinigung der Struktur: HLP09-serve_report.py auf der
neuen Ordnerstruktur testen.

  - Läuft HLP09 fehlerfrei auf 00-model / 01-artifacts / 02-stages?
  - Werden die SVG-Reports aus 01-artifacts/05-reports korrekt geliefert?
  - Ist webconfig.txt auf neue Pfade angepasst?

Ziel: Doku-Publishing als stabiler Ausgangspunkt für 5.7.


--------------------------------------------------------------------------------
4. ABGRENZUNG — WAS DIESER SPRINT NICHT TUT
--------------------------------------------------------------------------------

- Kein neuer Funktionscode
- Keine neuen Script-Reihen (CSV10+, XLSX00+, MaM00+ → SPRINT-CSV-Refactoring)
- Keine Logikänderungen in bestehenden Scripts
- Kein Eingriff in master.xml, run-scope.txt Inhalt, flowmapping.txt Logik
- Kein Atlassian-Setup (Portal bleibt wie es ist)
- Kein COLUMBO-Onboarding (separater Sprint)
- Keine GOV-Erweiterung (außer Filetypen-Konvention in SCRIPT-BAUKASTEN.txt)
- Kein BPMN-Flow-Aufbau


--------------------------------------------------------------------------------
5. BETROFFENE DATEIEN UND ORDNER
--------------------------------------------------------------------------------

Umbenennung (Ordner):
  01-model          →  00-model
  02-artifacts      →  01-artifacts
  03-stages         →  02-stages

Neu zu erstellen:
  File-Extension-Konvention.txt    Regel-Dokument Filetypen
  .gitignore                       GitHub Tracking-Ausschlüsse (Inhalt OFFEN B)
  Sprint-DEV-Doku-5.5-CleaningRun.txt

Zu ändern (Pfad-Strings):
  Alle Scripts der Reihen HLP, CSV, XML, M2B, ATL, FLW
  webconfig.txt                    Pfade auf neue Ordner-Nummern
  root.txt (ggf. → root.cfg)       abhängig von OFFEN A

Zu verschieben (Doku):
  Sprint-DEFs, Sprint-DEV-Dokus, Principles, How2, GOV, Rosetta Stone
  → aus Blueprint-Root in R+MUNI Doku\R+MUNI Doku-internal

Unverändert:
  README.md         bleibt im Root (GitHub-Sichtbarkeit)
  Install.txt       bleibt im Root (GitHub-Sichtbarkeit)
  LICENSE           bleibt im Root
  Alle Script-Logiken (nur Pfad-Strings werden angepasst)


--------------------------------------------------------------------------------
6. REIHENFOLGE DER UMSETZUNG
--------------------------------------------------------------------------------

Schritt 1   OFFEN A klären (root.txt → root.cfg oder bleibt .txt?)
            → Entscheidung festhalten, bevor irgendein Script angefasst wird

Schritt 2   Ordner physisch umbenennen (Windows Explorer)
            01-model → 00-model
            02-artifacts → 01-artifacts
            03-stages → 02-stages

Schritt 3   root.txt verifizieren
            → Pfade stimmen mit neuer Struktur überein?
            → ggf. root.cfg Umbenennung durchführen

Schritt 4   Filetypen-Konvention dokumentieren
            → File-Extension-Konvention.txt erstellen

Schritt 5   Script-Referenzen nachziehen — Flow für Flow
            HLP → CSV → XML → M2B → ATL → FLW
            → jede Änderung protokollieren

Schritt 6   webconfig.txt anpassen

Schritt 7   Doku-Verschiebung
            → Sprint-Dokus, GOV, Principles, How2 in Doku-internal

Schritt 8   .gitignore anlegen (OFFEN B klären)
            → .gitattributes prüfen
            → GitHub Sync testen

Schritt 9   HLP09 testen auf neuer Struktur
            → SVG-Reports sichtbar?
            → Pfad-Fehler beheben falls vorhanden

Schritt 10  Sprint-DEV-Doku abschließen und GOV-Check


--------------------------------------------------------------------------------
7. ERFOLGSKRITERIEN
--------------------------------------------------------------------------------

  OK  Physische Ordnerstruktur stimmt mit root.txt überein
  OK  Alle Scripts laufen fehlerfrei auf neuer Struktur
  OK  Kein Script wurde inhaltlich / logisch verändert
  OK  File-Extension-Konvention dokumentiert und angewendet
  OK  .gitignore vorhanden (Inhalt befüllt nach OFFEN B)
  OK  GitHub Sync ohne ungewollte .bak / .log Einträge
  OK  HLP09 läuft auf neuer Struktur, SVG-Reports werden geliefert
  OK  Blueprint-Root enthält nur GitHub-relevante Dateien
  OK  OFFEN A und OFFEN B sind entschieden und dokumentiert
  OK  Kein Stage-3/4-Script wurde logisch verändert


--------------------------------------------------------------------------------
8. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Strukturbereinigung (Entwicklerwunsch)
GOV 10.5  Fachlicher Mehrwert        OK  Saubere Basis für Stage 5.7 Beta Endkunde
GOV 10.5  Keine implizite Gov-Änd.   OK  Filetypen-Konvention additiv in BAUKASTEN
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 3
GOV 10.6  Ziel überprüfbar           OK  Erfolgskriterien Abschnitt 7
GOV 10.7  Zwischenschritte           OK  Abschnitt 6
GOV 10.8  Dev-Doku                   OFFEN  wird im Sprint erstellt
GOV 10.9  Stage-Ende Doku            OFFEN  verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  kein neuer Code, keine Logikänderung
Stage 5   Rückkopplungsschutz        OK  Stage-3/4-Logik unverändert


================================================================================
END OF SPRINT DEFINITION
SPRINT-5.5-CleaningRun | Stage 5 | 2026-03-12
================================================================================
