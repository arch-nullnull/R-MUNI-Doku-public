================================================================================
NBX FLOW – PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : NBX_FLOW_principles_S105
Tag             : #dev #principles #nbxflow #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-04-06
Letzte Änderung : 2026-04-14 — S105-Update | Basis: NBX_principles_DEV_S102.md
Ablageort       : 01-principles\NBX_FLOW_principles_S105.md
================================================================================


1. ZWECK UND DESIGNPHILOSOPHIE
--------------------------------------------------------------------------------
Der NBX-Flow löst ein spezifisches Problem: Eine lokale Netzwerkumgebung
soll automatisch erfasst und als strukturierte, ECM-kompatible CSV-Daten
bereitgestellt werden — ohne manuelle Erfassung, ohne proprietäre Infrastruktur.

Kernprinzip: NBX produziert — ECM konsumiert. Keine Vermischung.
NBX kennt keine ArchiMate-Typen. ECM kennt keine Netzwerk-Scans.
Die Schnittstelle ist trash_nbx.csv — ein stabiles, einfaches Format.

Der Name NBX steht für NetBox-kompatibel. Das Datenmodell orientiert sich
bewusst an NetBox Community (Devices, Services, Properties) ohne NetBox
vorauszusetzen. Wenn NetBox in einem späteren Stage eingeführt wird,
ist der Anker bereits gesetzt — nur NBX02 wird dann ausgetauscht.


2. WAS DER FLOW LEISTET
--------------------------------------------------------------------------------
Der NBX-Flow ermöglicht:
  - Automatische Erkennung aller aktiven Hosts im konfigurierten IP-Bereich
  - Erfassung von Hostnamen, MAC-Adressen und Hersteller-Informationen
  - Erfassung offener Ports und Dienste (Services)
  - Normierte Ausgabe als trash_nbx.csv (ECM-kompatibel)
  - Erweiterte Attribute als properties_nbx.csv (mappbar in Archi)
  - Zusammenführung Host + Services via NBX04 IP-Merge (S105)
  - Übergabe-Report mit Statistik und nächsten Schritten (NBX05)
  - Reproduzierbarer Lauf — gleiche Umgebung ergibt gleiche Ausgabe

Der NBX-Flow leistet nicht:
  - Keine IP-Adressen-Verwaltung (IPAM) — NetBox-Scope, Folge-Sprint
  - Kein automatisches ArchiMate-Mapping — das ist Aufgabe des ECM-Flows
  - Kein Push in NetBox — reiner Producer, kein Writer
  - Kein Echtzeit-Monitoring — einmaliger Scan, kein Daemon
  - Keine installierten Software-Pakete — kein natives Konzept ohne Plugin


3. GRUNDPRINZIPIEN
--------------------------------------------------------------------------------

3.1 Ein Script — eine Wirkung
Jedes Script hat genau eine fachliche Aufgabe. Kein Script macht zwei
Dinge gleichzeitig. (GOV 6.10)

  NBX00 löst nur die Root-Umgebung auf — kein Scan, keine Validierung.
  NBX01 validiert nur die Config — kein Scan, keine Normierung.
  NBX02 scannt nur — keine Normierung, kein CSV.
  NBX03 normiert nur — kein Scan, kein Report.
  NBX04 merged IDs — eine Zeile pro Host, Services aggregiert.
  NBX05 reportet nur — keine Datenverarbeitung.

3.2 Kein ArchiMate im NBX-Flow
Der NBX-Flow kennt keine ArchiMate-Typen. Er produziert NetBox-nahe
Rohfelder. Das Mapping auf Device, SystemSoftware, ApplicationService
etc. ist Aufgabe des ECM-Flows via OEF Mapping-Modell. (GOV 4.3, 4.5)

  trash_nbx.csv enthält nbx_objecttype: host / service — keine
  ArchiMate-Konzepte. Das Mapping-Modell in Archi entscheidet wie
  ein "host" im Modell landet. EUMAXL trifft diese Entscheidung
  einmalig in Archi — nicht im Script.

3.3 Plattformunabhängigkeit
Der Flow läuft auf Windows und Linux gleichermaßen.
Externe Abhängigkeiten sind explizit dokumentiert.
Kein Script verwendet OS-spezifische APIs ohne expliziten Hinweis.

  nmap binary und python-nmap sind Pflicht-Voraussetzungen — beide
  plattformunabhängig. Install.txt führt alle Abhängigkeiten.

3.4 NetBox-Anker für spätere Integration
Das Datenmodell von trash_nbx.csv orientiert sich bewusst an NetBox.
Feldnamen, Objekttypen und die 3PartyID-Logik sind so gewählt dass
eine spätere NetBox-Integration nur NBX02 betrifft.

  Wenn NetBox produktiv eingeführt wird ersetzt NBX02 den nmap-Scan
  durch einen NetBox API-Call. NBX03–NBX05 und der gesamte ECM-Flow
  bleiben unverändert.


4. NBX04 — IP-MERGE DESIGN (NEU S105)
--------------------------------------------------------------------------------
NBX04 löst ein inhärentes Problem: NBX03 erzeugt separate Zeilen für
Host-Einträge und Service-Einträge. ECM erwartet eine Zeile pro Host.

Zwei-Durchlauf-Logik (S105):
  Durchlauf 1: Alle Host-Zeilen einsammeln (ip → host-dict)
  Durchlauf 2: Alle Service-Zeilen dem jeweiligen Host zuordnen

Diese Logik ist reihenfolgeunabhängig — deterministisches Ergebnis
unabhängig von der NBX03-Output-Reihenfolge. (GOV 6.7)

Port-String Rekonstruktion aus Description-Spalte:
  NBX03 schreibt `Port 22/tcp` sauber in die Description.
  NBX04 liest direkt dort — kein fragiles Rückwärts-Parsing der 3PartyID.

Ergebnis: trash_nbx.csv enthält nach NBX04 eine Zeile pro Host
mit allen zugehörigen Services aggregiert.


5. TRASH-KONVENTION UND ÜBERGABE AN ECM
--------------------------------------------------------------------------------
NBX03 schreibt trash_nbx.csv nach:
  01-artifacts\02-csv\03-child\00-archimatechild\

Das ist der einzige valide Quellpfad für den ECM-Flow.

Häufiger Fehler (aus Produktivrun S105 dokumentiert):
  Falsches Import-File — trash_nbx.csv aus 04-import\ statt 00-archimatechild\.
  Kein Script-Bug, kein sichtbarer Fehler — aber ECM verarbeitet einen alten Stand.
  Absicherung: ECM00 Log lesen — vollständiger Pfad der gefundenen trash_*.csv
  ist dort explizit ausgewiesen.

"Trash" ist keine Wertung — es beschreibt den Charakter der Quelle:
unkontrolliert, extern, noch ohne definierte Semantik im Modell.


6. GRENZEN DES NBX-FLOWS
--------------------------------------------------------------------------------
Der NBX-Flow ist Teil von R+MUNI — aber nicht alles.

Was hier geregelt ist:
  - Netzwerk-Scan und Host-Erfassung (NBX02)
  - Normierung auf ECM-kompatibles Format (NBX03)
  - IP-Merge zu einer Zeile pro Host (NBX04)
  - Übergabe an ECM-Flow via trash_nbx.csv und properties_nbx.csv (NBX05)

Was woanders geregelt ist:
  - ArchiMate-Mapping → [[ECM_FLOW_How2_S105]]
  - CSV → Archi Import → [[CSV_FLOW_How2_S105]]
  - Ordner bereinigen vor/nach NBX-Lauf → CLE-Reihe
  - IPAM, Tenancy, Circuits → Folge-Sprint (NetBox)
  - Agent-Anreicherung → NBA-Flow (Backlog)


================================================================================
BEZÜGE
================================================================================

[[ECM_FLOW_principles_S105]]       Consumer des NBX-Outputs
[[ECM_FLOW_How2_S105]]             ECM-Flow Ablauf
[[DEV_Sprint_NBX-ECM-RUN_S105]]    Produktivrun — Erkenntnisse S105
[[NBX_principles_DEV_S102]]        Vorgänger-Dokument (read-only)
[[Global_GOV_DEV_S102]]            normative Grundlage
[[FREEZE_1_04]]                    Ausgangszustand Stage 1.05


================================================================================
NBX_FLOW_principles | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
