================================================================================
HLP HELPER SCRIPTS – HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : HLP_How2_S105
Tag             : #dev #how2 #hlp #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-02
Letzte Änderung : 2026-04-14 — S105-Update | HLP08–HLP10 + HLP99 ergänzt | Pfade geprüft
Ablageort       : 02-how2/HLP_How2_S105.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- Python 3.10+ (keine externen Pakete erforderlich)
- Scripts liegen in 01-artifacts/01-scripts/
- 02-stages/99-logs/ wird automatisch erstellt


KURZREFERENZ ALLER SCRIPTS
--------------------------------------------------------------------------------

HLP00 – Root und Umgebung loggen
  python HLP00_resolve_root.py
  → Zeigt und loggt: Script-Pfad, ROOT, OS, Python-Version, CWD
  → Log: 02-stages/99-logs/HLP00_resolve_root.log

HLP01 – Datei oder Ordner kopieren (Quelle bleibt)
  python HLP01_copy.py <quelle> <ziel>
  Beispiele:
    python HLP01_copy.py ordner_a/datei.txt ordner_b/datei.txt
    python HLP01_copy.py 01-artifacts/02-csv/00-master archiv/master-backup
  → Bei Ordner: rekursive Kopie. Ziel wird überschrieben wenn vorhanden.
  → Log: 02-stages/99-logs/HLP01_copy.log

HLP02 – Datei oder Ordner verschieben (Quelle wird gelöscht)
  python HLP02_move.py <quelle> <ziel>
  Beispiele:
    python HLP02_move.py temp/export.csv 01-artifacts/02-csv/03-child/00-archimatechild/export.csv
  → Zielverzeichnis wird automatisch erstellt
  → ACHTUNG: Quelle wird danach gelöscht
  → Log: 02-stages/99-logs/HLP02_move.log

HLP03 – Ordnerinhalt leeren (Ordner selbst bleibt)
  python HLP03_clean.py <ordner> [<ordner2> ...]
  Beispiele:
    python HLP03_clean.py 01-artifacts/02-csv/00-master
    python HLP03_clean.py 02-stages/00-archimatearchive 02-stages/01-bpmnarchive
  → ACHTUNG: Löscht ALLES im Ordner ohne Bestätigung
  → Mehrere Ordner in einem Aufruf möglich
  → Log: 02-stages/99-logs/HLP03_clean.log

HLP04 – Verzeichnisbaum dokumentieren
  python HLP04_dirlog.py <ordner> [<ordner2> ...]
  Beispiele:
    python HLP04_dirlog.py .
    python HLP04_dirlog.py 01-artifacts 02-stages
  → Zeigt und loggt Dateibaum mit Dateigrößen
  → Log: 02-stages/99-logs/HLP04_dirlog.log (akkumulierend)

HLP05 – Kontext- und Strukturdateien erstellen
  python HLP05_context_structure.py [<ordner>] [--context-only] [--structure-only]
  Beispiele:
    python HLP05_context_structure.py
    python HLP05_context_structure.py 01-artifacts --structure-only
  → context/context.json: Umgebungsmetadaten (OS, Python, Hostname, Pfade)
  → context/structure.json: Kompletter Dateibaum als JSON
  → Log: 02-stages/99-logs/HLP05_context.log

HLP06 – Backup erstellen
  python HLP06_backup.py [--src <ordner>] [--dest <ordner>] [--exclude <n> ...]
  Beispiele:
    python HLP06_backup.py
    python HLP06_backup.py --dest D:/backups
    python HLP06_backup.py --src 01-artifacts --dest ../backups --exclude temp
    python HLP06_backup.py --no-checksums   (schneller, keine SHA-256)
  → Standard-Quelle: Scriptverzeichnis (ROOT)
  → Standard-Ziel: ROOT/backups/
  → Archivname: MUNI_backup_YYYYMMDD_HHMMSS.zip
  → Enthält manifest.json mit SHA-256 Checksums
  → Log: 02-stages/99-logs/HLP06_backup.log

HLP07 – Backup wiederherstellen
  python HLP07_restore.py <backup.zip> [--dest <ordner>] [--dry-run] [--verify-only] [--no-verify]
  Beispiele:
    python HLP07_restore.py backups/MUNI_backup_20260302_120000.zip
    python HLP07_restore.py backup.zip --dest C:/restored --dry-run
    python HLP07_restore.py backup.zip --verify-only
  → Standard-Ziel: Original-Pfad aus manifest.json
  → --dry-run: zeigt was gemacht würde, schreibt nichts
  → --verify-only: prüft Checksums vorhandener Dateien ohne Extract
  → --no-verify: überspringt Checksum-Prüfung nach Restore
  → Log: 02-stages/99-logs/HLP07_restore.log

HLP08 – structure.txt als ArchiMate XML erzeugen
  python HLP08_structure2xml.py
  → Liest structure.txt aus ROOT
  → Erzeugt ArchiMate OEF-konformes XML (Archi CSV-Import-Format)
  → Alle Ordner und Dateien als Artifact modelliert
  → Eltern-Kind Beziehungen als Composition
  → Output: 01-artifacts/00-xml/03-child/00-archimatechild/muni2import.xml
  → Basis: root.cfg (HLP00-Muster)
  → Detailablauf: siehe HLP08_How2_ID-Merge-Run_S105.md

HLP09 – Lokalen Report-Webserver starten
  python HLP09-serve_report.py [--no-browser]
  → Liest webconfig.txt aus 01-artifacts/05-reports/
  → Startet je einen HTTP-Server pro konfiguriertem Report
  → Alle Reports gleichzeitig, jeder auf eigenem Port
  → --no-browser: kein automatischer Browser-Start
  → Log: 02-stages/99-logs/HLP09-serve_report.log
  → Detailablauf: siehe HLP09_How2_S105.md

HLP10 – PropertyDefinitions in master.xml bereinigen
  python HLP10-cleanup_property_definitions.py
  → Bereinigt veraltete und doppelte PropertyDefinitions in master.xml
  → Behält ausschließlich aktuelle PropertyDefinition für "3PartyId"
  → Erstellt 01-artifacts/00-xml/00-master/master.xml.bak vor dem Schreiben
  → EINMALIG ausführen — bei Bedarf nach Archi-Importproblemen
  → Log: 02-stages/99-logs/HLP10-cleanup_property_definitions.log

HLP99 – Vollständige Ordnerstruktur anlegen
  python HLP99-mkdir.py
  → Legt alle R+MUNI Ordner gemäß structure.txt an
  → Basis: root.cfg (<rootfolder>)
  → Sicher: existierende Ordner werden nicht überschrieben
  → Einmalig bei Erstinstallation oder nach Reset ausführen


TYPISCHE ANWENDUNGSFÄLLE
--------------------------------------------------------------------------------

Vor einem riskanten Flow-Lauf sichern:
  python HLP06_backup.py
  → Danach Flow ausführen. Bei Fehler mit HLP07 wiederherstellen.

Master CSVs leeren vor sauberem Lauf:
  python HLP03_clean.py 01-artifacts/02-csv/00-master
  Danach CSV05 ausführen um Header wieder zu erzeugen.

Archiv-Verzeichnisse leeren nach abgebrochenem XML Flow:
  python HLP03_clean.py 02-stages/00-archimatearchive 02-stages/01-bpmnarchive

Aktuellen Stand dokumentieren:
  python HLP05_context_structure.py
  python HLP04_dirlog.py .

Datei aus Archiv ins active Verzeichnis schieben:
  python HLP01_copy.py 02-stages/01-bpmnarchive/MeinProzess.bpmn 00-model/01-bpmn/00-bpmnactive/MeinProzess.bpmn

Backup auf anderen Rechner übertragen und wiederherstellen:
  1. HLP06 auf Quellrechner ausführen
  2. ZIP auf Zielrechner kopieren
  3. python HLP07_restore.py backup.zip --dest <Zielpfad>

Neue Installation — Ordnerstruktur bootstrappen:
  python HLP99-mkdir.py
  → Alle Ordner werden angelegt. Danach HLP00 als Funktionscheck.

structure.txt als ArchiMate-Modell importieren:
  → Vollständiger Ablauf: HLP08_How2_ID-Merge-Run_S105.md

Reports lokal anzeigen:
  → webconfig.txt in 01-artifacts/05-reports/ konfigurieren
  → python HLP09-serve_report.py


PFADANGABEN – REGELN
--------------------------------------------------------------------------------
- Relative Pfade werden gegen ROOT aufgelöst (= Verzeichnis der HLP-Scripts,
  d.h. 01-artifacts/01-scripts/)
- Absolute Pfade werden direkt verwendet
- Alle HLP-Scripts verstehen beide Varianten automatisch


BACKUP WIEDERHERSTELLEN – DETAILABLAUF
--------------------------------------------------------------------------------
1. HLP07 liest manifest.json aus dem ZIP
2. Zeigt Backup-Info (Datum, Quelle, Dateianzahl, Größe)
3. Extrahiert alle Dateien nach Zielverzeichnis
4. Führt Checksum-Verifikation durch (SHA-256)
5. Meldet OK/FEHLER pro Datei

Bei Checksum-Fehler:
  → Meldung im Log + Konsole
  → Restore ist abgeschlossen aber Dateien sind möglicherweise korrumpiert
  → Anderes Backup verwenden oder Quelle prüfen

--dry-run zeigt den vollständigen Restore-Plan ohne eine Datei zu schreiben.
Empfohlen vor dem ersten Restore auf ein neues Zielsystem.


================================================================================
BEZÜGE
================================================================================

[[HLP_principles_S105]]              Designprinzipien und Fehlerverhalten
[[HLP08_How2_ID-Merge-Run_S105]]     Detailablauf Structure-Bootstrapping
[[HLP09_How2_S105]]                  Detailablauf Report-Server
[[naming_and_structure_S104]]        Namenskonvention Scripts


================================================================================
HLP HOW2 | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
