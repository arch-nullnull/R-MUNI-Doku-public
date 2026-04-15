================================================================================
ECM – EasyCSVMapper – HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : ECM_How2_DEV_S6
Tag             : #dev #how2 #ecm #easycsvmapper #s6 #s8
Datum           : 2026-03-26
Stage           : S8 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-21
Ablageort       : R+MUNI Doku-public\02-how2\ECM_How2_DEV_S6.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[Sprint-DEV-EasyMapper_S6]] gelesen — Konzept und Entscheidungen bekannt
- Python 3.10+
- root.cfg vorhanden und <rootfolder> korrekt gesetzt
- Scripts in 01-artifacts\01-scripts\
- Archi 5.8 installiert (manueller Import/Export-Schritt)
- trash_*.csv in 01-artifacts\02-csv\03-child\00-archimatechild\ abgelegt
- run-scope.txt enthält SOURCE=CSV + MODEL= + MAPPING= Tripel (nach ECM01-Phase)


ZWEI PHASEN — KURZ ERKLÄRT
--------------------------------------------------------------------------------
Phase 1  (einmalig pro neuer CSV-Quelle)
  Strukturerkennung → Mapping-Modell in Archi bauen → OEF Export
  Nur einmal nötig — danach direkt Phase 2

Phase 2  (regulärer Lauf, wiederholbar)
  Daten importieren mit bestehendem Mapping-Modell


================================================================================
KURZREFERENZ — ALLE SCRIPTS
================================================================================


── PHASE 1 — ERSTMALIGE STRUKTURERKENNUNG ──────────────────────────────────────

ECM00 – Umgebung validieren
  py .\ECM00-validate_environment.py
  → Prüft root.cfg, 99-mappingmodel\, 00-archimatearchive\, 00-archimatechild\
  → Meldet gefundene trash_*.csv Dateien
  → Ziel: 02-stages\99-logs\ECM00-root.resolved.txt

ECM01 – Müll-CSV Felder als Artifact-CSV ★ NUR PHASE 1
  py .\ECM01-csv_fields_to_artifacts.py
  → Liest trash_*.csv — erkennt Encoding + Trennzeichen automatisch
  → Schreibt alle Spaltenköpfe als Artifact-Elemente
  → Ziel: 01-artifacts\02-csv\04-import\elements.csv (Archi-importfertig)
  → Anwendungsfall: Einmalig — um Spaltenstruktur als Artefakte ins Modell zu bringen
                   damit Mapping-Modell in Archi visuell gebaut werden kann


── PHASE 2 — REGULÄRER LAUF ────────────────────────────────────────────────────

ECM00 – Umgebung validieren  (immer zuerst)
  py .\ECM00-validate_environment.py

ECM02 – Müll-CSV + OEF Mapping → Import-CSVs
  py .\ECM02-csv_to_mapping_to_csv.py
  → Liest MAPPING= aus run-scope.txt → findet OEF XML in 99-mappingmodel\
  → Wertet Associations aus (Element vs. Property)
  → Ziel: 01-artifacts\02-csv\04-import\elements.csv
          02-stages\00-archimatearchive\properties.csv  (geparkt, ID-los)
          02-stages\00-archimatearchive\relations.csv   (geparkt, nur Header)

ECM03 – ID-Merge  ★ NACH ARCHI EXPORT
  py .\ECM03-id_merge.py
  → Liest elements.csv (frischer Archi-Export MIT IDs)
  → Merged IDs in properties.csv via Reihenfolge-Join (pro Typ-Gruppe)
  → Ziel: 01-artifacts\02-csv\04-import\properties.csv (mit IDs)
          01-artifacts\02-csv\04-import\relations.csv
  → ACHTUNG: Nur ausführen NACHDEM Archi CSV-Export in 04-import\ erfolgt ist


================================================================================
VOLLSTÄNDIGER FLOW
================================================================================

PHASE 1 — einmalig pro neuer CSV-Quelle:

  py .\ECM00-validate_environment.py
  py .\ECM01-csv_fields_to_artifacts.py

  → Archi: elements.csv importieren (File → Import → CSV → 04-import\)
  → Archi: Property Definitions anlegen (manuell oder HLP10)
  → Archi: Mapping-Modell bauen
           Artifact-Elemente auf Ziel-Typen umwandeln
           Associations für Property-Felder ziehen
  → Archi: OEF Export → 00-model\00-archimate\99-mappingmodel\<n>.xml
  → run-scope.txt ergänzen:
           SOURCE=CSV
           MODEL=<dateiname>.csv
           MAPPING=<n>.xml


PHASE 2 — regulärer Lauf (wiederholbar):

  py .\ECM00-validate_environment.py
  py .\ECM02-csv_to_mapping_to_csv.py

  → Archi: elements.csv importieren (File → Import → CSV → 04-import\)
  → Archi: CSV Export nach 04-import\ (File → Export → CSV)

  py .\ECM03-id_merge.py

  → Archi: properties.csv + relations.csv importieren

```mermaid
graph TD
    A[ECM00] --> B[ECM01]
    B --> M1[Archi Import\elements.csv]
    M1 --> M2[Archi: Mapping\Modell bauen]
    M2 --> M3[OEF Export +\nrun-scope.txt]
    M3 --> P2

    subgraph P2[Phase 2 — wiederholbar]
        C[ECM00] --> D[ECM02]
        D --> E[Archi Import\elements.csv]
        E --> F[Archi CSV\Export]
        F --> G[ECM03]
        G --> H[Archi Import\properties + relations]
    end
```


================================================================================
KRITISCHE REGEL — REIHENFOLGE-JOIN
================================================================================

ECM03 matcht Properties via Reihenfolge — NICHT via Namen-Lookup.

  ZWISCHEN ECM02-Import und ECM03-Lauf KEINE Elemente in Archi umbenennen.
  Archi exportiert in Importreihenfolge — Umbenennung bricht den Join.

  Konsequenz bei Verletzung: falsche Properties am falschen Element.
  Kein Fehler sichtbar — falsches Ergebnis im Modell.

  Empfehlung: Erst nach vollständigem Phase-2-Lauf und Validierung umbenennen.


================================================================================
KONFIGURATION — run-scope.txt
================================================================================

ECM-Tripel Format (nach CSV04-Lauf manuell eintragen):

  SOURCE=CSV
  MODEL=<dateiname>.csv
  MAPPING=<oef-dateiname>.xml

MAPPING= referenziert direkt den Dateinamen (inkl. .xml Extension)
in 00-model\00-archimate\99-mappingmodel\

Beispiel:
  SOURCE=CSV
  MODEL=trash_test.csv
  MAPPING=trash_test.xml


================================================================================
ENCODING + TRENNZEICHEN ERKENNUNG
================================================================================

ECM01 und ECM02 erkennen automatisch:

Encoding (Reihenfolge):
  utf-8-sig → utf-8 → cp1252 → latin-1

Trennzeichen (Reihenfolge):
  ; → , → \t → |

Praxistest bestanden: cp1252 + Semikolon (Excel-Export, CRLF)

Bei Erkennungsfehler: Log prüfen — erkanntes Encoding und Trennzeichen
werden explizit ausgegeben.


================================================================================
FEHLERBILDER
================================================================================

Fehler: "Mehrere trash_*.csv gefunden"
  Ursache: Mehr als eine trash_*.csv in 00-archimatechild\
  Lösung:  Alle außer der gewünschten Datei entfernen — nur 1 pro Lauf

Fehler: "OEF XML nicht gefunden"
  Ursache: MAPPING= Wert in run-scope.txt stimmt nicht mit Dateiname überein
  Lösung:  Dateiname in 99-mappingmodel\ prüfen — MAPPING= inkl. .xml angeben
           Beispiel: MAPPING=trash_test.xml (nicht: MAPPING=trash_test)

Fehler: "ECM00-root.resolved.txt nicht gefunden"
  Ursache: ECM00 wurde nicht ausgeführt oder ist fehlgeschlagen
  Lösung:  ECM00 neu ausführen, Log prüfen

Fehler: "elements.csv (04-import) nicht gefunden" bei ECM03
  Ursache: Archi CSV-Export wurde noch nicht durchgeführt
  Lösung:  In Archi: File → Export → CSV → 04-import\ — dann ECM03 neu starten

Fehler: Properties landen am falschen Element
  Ursache: Element in Archi zwischen Import und ECM03 umbenannt
  Lösung:  Phase 2 komplett neu durchlaufen — ECM02 → Import → Export → ECM03

Fehler: root.cfg nicht gefunden
  Ursache: Script nicht aus Scripts-Ordner aufgerufen
  Lösung:  PowerShell in <rootfolder>\01-artifacts\01-scripts\ starten


================================================================================
ENTSCHEIDUNGSHILFE
================================================================================

Ich will...                                            Richtiges Script
------------------------------------------------------ -----------------------
Neue CSV-Quelle erstmalig verarbeiten                  ECM00 → ECM01 → [Archi]
Bekannte CSV-Quelle erneut importieren                 ECM00 → ECM02 → [Archi] → ECM03
Umgebung prüfen ohne Import                            ECM00
Encoding/Trennzeichen einer CSV prüfen                 ECM01 (Log lesen)
ID-Merge nach Archi-Export durchführen                 ECM03
Diagnose wenn nichts funktioniert                      ECM00 (Log prüfen)


================================================================================
BEZÜGE
================================================================================

[[Sprint-DEV-EasyMapper_S6]]     Designentscheidungen, vollständiger Kontext
[[Global_GOV_S8]]                Normative Grundlage
[[CSV_FLOW_How2_S8]]             Bestehender CSV-Flow (Übergabe-Kanal)
[[FREEZE-6]]                     Script-Konventionen, Ordnerstruktur


================================================================================
ECM_How2_DEV | S6 | 2026-03-21 | R+MUNI Blueprint
================================================================================
