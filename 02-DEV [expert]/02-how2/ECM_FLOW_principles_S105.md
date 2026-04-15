================================================================================
ECM FLOW – PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : ECM_FLOW_principles_S105
Tag             : #dev #principles #ecmflow #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-21
Letzte Änderung : 2026-04-14 — S105-Update | Basis: ECM_principles_S8.md
Ablageort       : 01-principles/ECM_FLOW_principles_S105.md
================================================================================


1. ZWECK UND DESIGNPHILOSOPHIE
--------------------------------------------------------------------------------
Die ECM-Reihe (EasyCSVMapper) löst ein spezifisches Problem: externe CSV-Quellen
die unkontrolliert sind — unbekanntes Encoding, unbekannte Trennzeichen,
unbekannte Spaltenstruktur — sollen strukturiert ins ArchiMate-Modell gelangen.

Kernprinzip: Der Entwickler entscheidet die Bedeutung — das Script führt aus.
ECM erkennt Technik automatisch (Encoding, Trennzeichen), aber die fachliche
Entscheidung "welche Spalte wird welcher ArchiMate-Typ" trifft immer der Mensch.
Dieses Wissen wird einmalig als Mapping-Modell in Archi gebaut und danach
automatisch angewendet.

ECM ist vollständig additiv — kein Eingriff in bestehende Reihen.
Die bestehende CSV-Reihe bleibt unberührt. ECM liefert am Ende
Archi-importfertige CSVs — die Übergabe erfolgt über den bekannten
manuellen Archi-Import-Kanal.


2. ABGRENZUNG ZUR BESTEHENDEN CSV-REIHE
--------------------------------------------------------------------------------
Die CSV-Reihe (CSV00–CSV99) verarbeitet kontrollierte Quellen:
  - Archi-Exporte mit stabiler Struktur (SOURCE=archi)
  - XLSX-Dateien mit bekannten Spalten (SOURCE=XLSX)
  - Mapping via csvmapping.txt / propmapping.txt (Quell-Schema bekannt)

Die ECM-Reihe verarbeitet unkontrollierte externe Quellen:
  - Beliebige CSV-Dateien (SOURCE=CSV)
  - Encoding und Trennzeichen unbekannt → automatische Erkennung
  - Spaltenstruktur unbekannt → Mapping via OEF Modell (nicht via .txt)
  - Bedeutung der Spalten → wird einmalig in Archi definiert

Beide Reihen koexistieren — sie konkurrieren nicht.
Die ECM-Reihe berührt CSV03, CSV04 oder andere bestehende Scripts nicht.


3. DAS OEF MAPPING-MODELL
--------------------------------------------------------------------------------
Das Herzstück der ECM-Reihe ist das OEF Mapping-Modell.

Es ist kein Konfigurationsfile — es ist ein ArchiMate-Modell.
Gebaut in Archi, visuell prüfbar, maschinenlesbar über OEF XML.

Ablageort: 00-model\00-archimate\99-mappingmodel\
Format   : ArchiMate 3.1 OEF XML (.xml)
Namenskonvention: frei wählbar — wird in run-scope.txt als MAPPING= referenziert

Das Modell enthält:
  - Artifact-Elemente (Phase 1): Spaltenköpfe der Quell-CSV
  - ArchiMate-Elemente (Phase 2): Ziel-Typen nach manueller Umwandlung
  - Associations: Mapping-Semantik (wer wird Element, wer wird Property)

Das Mapping-Modell ist unveränderlich zwischen den Phasen eines Laufs.
Änderungen am Mapping erfordern einen neuen Phase-1-Durchlauf.


4. MAPPING-SEMANTIK — ASSOCIATION ALS SPRACHE
--------------------------------------------------------------------------------
Die Frage "wird dieses Feld ein Element oder ein Attribut?" wird in Archi
über ArchiMate Associations ausgedrückt:

  Element OHNE eingehende Association:
    → wird eigenständiges ArchiMate-Element
    → Ziel-Typ = xsi:type des Elements im OEF
    → Pro Datenzeile entsteht eine Instanz dieses Elements

  Element MIT eingehender Association von einem anderen Element:
    → wird Property (Attribut) des Ziel-Elements
    → Key = Spaltenname, Value = Wert aus CSV-Datenzeile
    → Pro Datenzeile entsteht eine Property-Zeile

Warum Association?
  Association ist der universell zulässige ArchiMate-Beziehungstyp —
  keine Regel-Verletzung bei beliebigen Elementkombinationen.
  Die Semantik ist einfach, visuell sofort lesbar und deterministisch.


5. ZWEISTUFIGER IMPORT — DAS ID-PROBLEM
--------------------------------------------------------------------------------
ArchiMate-Elemente erhalten ihre stabilen IDs erst beim Import in Archi.
Properties brauchen diese IDs um korrekt zugeordnet zu werden.
Das macht einen zweistufigen Import notwendig:

  Stufe 1: Elemente importieren → IDs vergeben lassen
           elements.csv → 01-artifacts\02-csv\04-import\ (sofort)
           properties.csv + relations.csv → 02-stages\00-archimatearchive\ (geparkt)

  Stufe 2: IDs mergen → Properties importieren
           Archi CSV-Export → elements.csv mit IDs
           ECM03 merged IDs → properties.csv mit IDs → 01-artifacts\02-csv\04-import\

Dieser Zweischritt ist bewusst und dokumentiert — kein Workaround.
Er ist die saubere Lösung für das inhärente ID-Problem von Archi CSV-Importen.


6. REIHENFOLGE-JOIN — KRITISCHE REGEL
--------------------------------------------------------------------------------
ECM03 merged IDs via Reihenfolge-Join:
  Property-Zeile N gehört zu Element-Zeile N (pro Ziel-Typ-Gruppe).

Diese Logik setzt voraus:
  - Archi exportiert Elemente in der Reihenfolge in der sie importiert wurden
  - Zwischen ECM02-Import und ECM03-Lauf wurden keine Elemente in Archi
    umbenannt oder verschoben

Konsequenz bei Verletzung dieser Regel:
  Properties landen am falschen Element — kein sichtbarer Fehler,
  aber inhaltlich falsche Daten im Modell.

Empfehlung: Umbenennen erst nach vollständigem Phase-2-Lauf und Validierung.

Diese Einschränkung ist bekannt und bewusst akzeptiert.
Eine Automatisierung via jArchi (stabiler Name-ID-Lookup) ist als
Folge-Sprint definiert.


7. TRASH-KONVENTION
--------------------------------------------------------------------------------
Externe CSV-Quellen müssen mit dem Prefix trash_ benannt sein:
  trash_<quelle>.csv

Begründung:
  Der 00-archimatechild-Ordner enthält auch Archi-native Child-CSVs
  (CSV06-Quellen). Ohne Prefix-Filter würden ECM-Scripts alle CSVs
  verarbeiten — unerwünschtes Verhalten.

Genau eine trash_*.csv pro Lauf — bei mehreren bricht ECM ab.
Das ist kein Fehler sondern eine bewusste Schutzregel.

"Trash" ist keine Wertung — es beschreibt den Charakter der Quelle:
unkontrolliert, extern, noch ohne definierte Semantik im Modell.
Nach dem Mapping-Durchlauf ist die Semantik definiert — der Name bleibt.

Namenskonvention (S105 explizit):
  trash_<quelle>.csv — Quelle ist der erzeugende Flow.
  Beispiel: trash_nbx.csv (erzeugt durch NBX05)
  Diese Konvention ist implizit im NBX-Sprint entstanden und hier
  formal verankert.


8. IMPORT-PFAD — KRITISCHE REGEL (NEU S105)
--------------------------------------------------------------------------------
Die trash_*.csv muss in folgendem Verzeichnis abgelegt sein:
  01-artifacts\02-csv\03-child\00-archimatechild\

Das ist der einzige valide Quellpfad für ECM00–ECM03.

Häufiger Fehler (aus Produktivrun S105 dokumentiert):
  Import aus 04-import\ statt 00-archimatechild\ — ECM verarbeitet
  dann einen alten Stand ohne Fehlermeldung.
  Kein Script-Bug — Layer-8-Fehler. Kein sichtbarer Fehler im Ablauf.
  Ergebnis: Mapping basiert auf veralteten Daten.

Absicherung:
  ECM00 meldet gefundene trash_*.csv Dateien mit vollem Pfad im Log.
  Vor jedem Lauf: Log lesen und Pfad bestätigen.


9. PROPERTY DEFINITIONS
--------------------------------------------------------------------------------
Archi verhält sich inkonsistent wenn Properties importiert werden bevor
die Property Definitions im Modell registriert sind.

Aktueller Stand: Property Definitions werden manuell angelegt.
Hilfreich: HLP10-cleanup_property_definitions.py für Bereinigung.
Geplant: Automatisierung via jArchi (eigener Folge-Sprint).

Python ist nicht der richtige Kanal für Archi-interne Operationen wie
das Anlegen von Property Definitions. jArchi ist dafür der saubere Weg.
Python-Stunts um Archi zu zwingen sind tool-abhängig und fragil.


10. GRENZEN DER ECM-REIHE
--------------------------------------------------------------------------------
ECM kann aktuell:
  - Eine trash_*.csv pro Lauf verarbeiten
  - Elemente und Properties erzeugen
  - Encoding und Trennzeichen automatisch erkennen

ECM kann aktuell nicht:
  - Mehrere CSV-Quellen in einem Lauf verarbeiten
  - Relations zwischen gemappten Elementen erzeugen
    (relations.csv bleibt leer — Grundlage vorhanden)
  - Property Definitions automatisch anlegen (→ jArchi)
  - Den manuellen Archi-Import-Schritt ersetzen (→ jArchi)
  - Duplikate erkennen oder behandeln

Diese Grenzen sind bewusst gesetzt — ECM löst das definierte Problem
ohne überzukomplexieren. Erweiterungen erfolgen additiv wenn Bedarf entsteht.


11. SCRIPT-LÄNGE UND REFACTORING
--------------------------------------------------------------------------------
ECM02 und ECM03 sind mit ~300 Zeilen an der Grenze des Blueprint-Standards
(1 Script = 1 Outcome, überschaubar).

Gemeinsame Funktionen (Encoding-Erkennung, Trennzeichen-Erkennung,
OEF-Parser) kommen in mehreren Scripts vor und sind Kandidaten für
eine HLP-Auslagerung im nächsten Cleaning Run.

Dieser Zustand ist bekannt und dokumentiert — kein Blocker,
aber ein geplanter Folgeschritt.


12. PRODUCER/CONSUMER-TRENNUNG
--------------------------------------------------------------------------------
Der ECM-Flow ist ein reiner Consumer — er produziert keine Rohdaten.

Producer-Rollen:
  NBX-Flow (NBX00–NBX05): produziert trash_nbx.csv aus Netzwerk-Scan
  NBA-Flow (Backlog):      produziert angereicherte Daten via Agent
  Manuelle Quellen:        beliebige externe CSV-Dateien

ECM konsumiert immer genau eine normierte trash_*.csv — unabhängig
davon welcher Producer sie erzeugt hat.

Diese Trennung ist strukturell — kein NBX-Script kennt ECM,
kein ECM-Script kennt NBX. Die Verbindung ist die Datei.


================================================================================
BEZÜGE
================================================================================

[[DEV_Sprint_NBX-ECM-RUN_S105]]   Produktivrun — Erkenntnisse Import-Pfad
[[ECM_principles_S8]]              Vorgänger-Dokument (read-only)
[[Global_GOV_DEV_S102]]            normative Grundlage
[[CSV_FLOW_principles_S105]]       bestehende CSV-Logik (Abgrenzung)
[[NBX_principles_DEV_S102]]        Producer-Logik NBX
[[FREEZE_1_04]]                    Ausgangszustand Stage 1.05


================================================================================
ECM_FLOW_principles | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
