================================================================================
HLP HELPER SCRIPTS – PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : HLP_principles_S105
Tag             : #dev #principles #hlp #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-02
Letzte Änderung : 2026-04-14 — S105-Update | HLP08–HLP10 + HLP99 ergänzt | Pfade geprüft
Ablageort       : 01-principles/HLP_principles_S105.md
================================================================================


1. ZWECK UND DESIGNPHILOSOPHIE
--------------------------------------------------------------------------------
Die HLP-Scripts (HLP00–HLP10, HLP99) sind autarke, single-responsibility
Utilities für wiederkehrende Betriebsaufgaben im Blueprint-Umfeld:
Root-Auflösung, Dateisystemoperationen, Logging, Backup, Restore,
Struktur-Import, Report-Server und Ordner-Bootstrapping.

Kernprinzip: Jedes HLP-Script macht genau eine Sache. Es hat keine
Abhängigkeit zu anderen HLP-Scripts und keine Abhängigkeit zu Flow-Artefakten
(keine Nutzung von root.resolved.txt o.ä.).

HLP-Scripts sind Werkzeuge, keine Flow-Stages. Sie können in beliebiger
Reihenfolge und unabhängig voneinander aufgerufen werden.

Ausnahme: HLP08 und HLP99 nutzen HLP00 (get_root_cfg) als Root-Resolver.
Diese Abhängigkeit ist explizit und bewusst — HLP00 ist der einzige erlaubte
Import innerhalb der HLP-Reihe.


2. ROOT-AUFLÖSUNG
--------------------------------------------------------------------------------
HLP00–HLP07 lösen ROOT autark via:
  ROOT = os.path.dirname(os.path.abspath(__file__))

HLP08 und HLP99 nutzen get_root_cfg() aus HLP00_resolve_root.py.
Das ist die einzige erlaubte Import-Abhängigkeit innerhalb der HLP-Reihe.

HLP09 und HLP10 lösen ROOT über Path(__file__).resolve() — autark,
ohne Abhängigkeit zu anderen HLP-Scripts.

Relative Pfad-Angaben in Argumenten werden gegen ROOT aufgelöst via
abs_path() Hilfsfunktion. Absolute Pfade werden direkt verwendet.

Kein HLP-Script liest root.txt oder andere Flow-Artefakte.
Die weitgehende Autarkie ist bewusst – HLP-Scripts sollen auch dann
funktionieren wenn der Flow noch nicht ausgeführt wurde.


3. LOGGING-PRINZIP
--------------------------------------------------------------------------------
Alle HLP-Scripts schreiben Logs im Append-Modus nach:
  02-stages/99-logs/<ScriptName>.log

Logs werden nicht rotiert, nicht geleert. Sie akkumulieren über alle Läufe.
Jeder Eintrag hat einen Timestamp.

HLP04 ist der einzige Script der explizit für Logging-Zwecke gebaut ist
(Verzeichnisbaum-Dokumentation). Die anderen Scripts loggen als Nebeneffekt.


4. FEHLERVERHALTEN
--------------------------------------------------------------------------------
Alle HLP-Scripts geben bei Fehler eine klare Meldung aus und beenden mit
sys.exit(1). Kein Silent-Fail.

Wichtige Fehlerquellen:
  HLP01/HLP02: Quellpfad nicht gefunden → Abbruch
  HLP03: Ordner nicht gefunden → SKIP (kein Abbruch, nur Warnung)
  HLP06: Quellordner nicht gefunden → Abbruch
  HLP07: Backup-Archiv nicht gefunden → Abbruch
         manifest.json fehlt im Archiv → Abbruch (kein gültiges HLP06-Backup)
  HLP08: structure.txt nicht gefunden → Abbruch
  HLP09: webconfig.txt nicht gefunden → Abbruch
         Kein gültiger Eintrag in webconfig.txt → Abbruch
  HLP10: 01-artifacts/00-xml/00-master/master.xml nicht gefunden → Abbruch


5. DESTRUKTIVE OPERATIONEN – REGELN
--------------------------------------------------------------------------------
HLP02 (move): Löscht die Quelle nach dem Verschieben. Unwiderruflich.
HLP03 (clean): Löscht alle Inhalte eines Ordners. Der Ordner selbst bleibt.
               Mehrere Ordner können als Argumente übergeben werden.

Regel: HLP03 löscht Dateien UND Unterordner – inklusive aller Inhalte.
       Es gibt keine Bestätigungsabfrage. Vor destruktiven Operationen
       immer HLP06 Backup erstellen.

HLP10: Modifiziert 01-artifacts/00-xml/00-master/master.xml direkt.
       Erstellt master.xml.bak im selben Verzeichnis vor dem Schreiben.
       Einmalig ausführen — danach kann das Script archiviert werden.


6. BACKUP-INTEGRITÄT (HLP06/HLP07)
--------------------------------------------------------------------------------
HLP06 erstellt ein vollständiges ZIP-Archiv mit eingebettetem manifest.json.
Das Manifest enthält SHA-256 Checksums aller Dateien.

Archivformat:
  backup/relative/pfad/zur/datei   (im ZIP)
  manifest.json                     (im ZIP root)

HLP07 liest ausschließlich HLP06-kompatible Archive. Ein Archiv ohne
manifest.json wird abgelehnt.

Nach dem Restore führt HLP07 automatisch eine Checksum-Verifikation durch
(kann mit --no-verify übersprungen werden).

DEFAULT_EXCLUDE in HLP06:
  .git, __pycache__, .venv, venv, node_modules, .idea, .vscode,
  .DS_Store, Thumbs.db

Zusätzliche Ausschlüsse via --exclude Argument möglich.


7. KEINE EXTERNE ABHÄNGIGKEITEN
--------------------------------------------------------------------------------
Alle HLP-Scripts (HLP00–HLP10, HLP99) verwenden ausschließlich Python stdlib:
  os, sys, shutil, zipfile, hashlib, json, platform, datetime, argparse,
  pathlib, re, uuid, xml.etree.ElementTree, xml.dom.minidom,
  http.server, socketserver, threading, webbrowser, socket

Keine pip-Pakete erforderlich. HLP-Scripts laufen auf jeder Python 3.10+
Installation ohne Vorbereitung.


8. SCRIPT-CHARAKTERISTIKA UND EINSATZGRENZEN
--------------------------------------------------------------------------------

HLP08 – structure.txt → ArchiMate XML
  Erzeugt bei jedem Lauf neue UUIDs. Master-Stack vor jedem Run leeren:
    01-artifacts/02-csv/00-master/ (elements, relations, properties)
    01-artifacts/00-xml/00-master/master.xml
  Kein Schutz gegen Duplikate wenn Master-Stack nicht geleert wurde.
  Detailprozess (2-Run-Verfahren): HLP08_How2_ID-Merge-Run_S105.md

HLP09 – Report-Server
  Kein Hintergrunddienst — läuft nur solange das Script aktiv ist.
  Beenden via STRG+C. Kein Restart automatisch bei Absturz.
  Config: 01-artifacts/05-reports/webconfig.txt
  Reports: 01-artifacts/05-reports/00-archimate/ und 01-bpmn/ und 99-html/
  Webconfig-Einträge ohne index.html werden übersprungen (Warnung, kein Abbruch).

HLP10 – PropertyDefinitions bereinigen
  Einmalig ausführen. Bei Mehrfachausführung keine negativen Effekte
  (idempotent), aber kein aktiver Nutzen mehr nach erstem Lauf.
  Nur PropertyDefinitions werden angefasst — alle anderen XML-Elemente
  in 01-artifacts/00-xml/00-master/master.xml bleiben unverändert.

HLP99 – Ordnerstruktur anlegen
  Sicher bei Mehrfachausführung — existierende Ordner werden nicht überschrieben.
  Pflegt keine Dateien — nur Verzeichnisstruktur.
  Einmalig bei Erstinstallation oder nach komplettem Reset.


9. GRENZEN DER HLP-SCRIPTS
--------------------------------------------------------------------------------
- Kein Verständnis von Blueprint-Semantik – reine Dateisystemoperationen
  (ausgenommen HLP08/HLP10 die XML-Semantik kennen)
- Kein Schutz gegen versehentliche Mehrfachausführung (HLP03 ist sofort)
- HLP06 Backup ist kein Versionierungssystem – last-write-wins im backups/
  Ordner wenn gleicher Timestamp (praktisch ausgeschlossen, da Sekunden-genau)
- HLP07 Restore überschreibt bestehende Dateien am Zielpfad ohne Warnung
- HLP05 context.json enthält Hostname – auf geteilten Systemen beachten
- HLP09 ist kein Produktionsserver — ausschließlich für lokale Nutzung


================================================================================
BEZÜGE
================================================================================

[[HLP_How2_S105]]                    Kurzreferenz und Anwendungsfälle
[[HLP08_How2_ID-Merge-Run_S105]]     Detailablauf Structure-Bootstrapping
[[HLP09_How2_S105]]                  Detailablauf Report-Server
[[naming_and_structure_S104]]        Namenskonvention Scripts


================================================================================
HLP PRINCIPLES | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
