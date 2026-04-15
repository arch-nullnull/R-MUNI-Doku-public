================================================================================
NBX — PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : NBX_principles_DEV_S102
Tag             : #principles #nbx #dev #s102
Datum           : 2026-04-06
Stage           : S1.02 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================

---
title: "NBX — Principles"
stage: S1.02
status: "AKTIV"
typ: "Prinzipien"
datum: "2026-04-06"
autor: EUMAXL
tags: [rmuni, blueprint, dev, nbx, principles, s102]
---

================================================================================
NBX — PRINCIPLES
Stage S1.02 | AKTIV | R+MUNI Blueprint
================================================================================

---

## Kontext

Der NBX-Flow ist eine eigenständige Script-Reihe die eine lokale Netzwerk-
umgebung automatisch erfasst und als strukturierte CSV-Daten bereitstellt.
Das Ergebnis läuft direkt in den ECM-Flow ein und landet damit in Archi 5.8
als ArchiMate-Modell. Das Dokument erklärt was der NBX-Flow ist, warum er
so aufgebaut ist wie er ist, und was er nicht leistet.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[DEV_Sprint_NBX_S102]]              Sprint-Dokumentation NBX
- [[ECM_How2_DEV_S8]]                  Consumer des NBX-Outputs
- [[NBX_How2_DEV_S102]]                technische Referenz

---

## Inhalt

ZWECK DIESES DOKUMENTS
--------------------------------------------------------------------------------
Zielgruppe: DEV

Dieses Dokument erklärt:
  - Was der NBX-Flow ist und wozu er dient
  - Warum er als eigenständige Reihe geführt wird
  - Welche Designentscheidungen getroffen wurden und warum
  - Was dieser Flow nicht leistet und wo die Grenzen liegen


================================================================================
1. WAS IST DER NBX-FLOW?
================================================================================

Der NBX-Flow ist eine Python Script-Reihe (NBX00–NBX04) die ein lokales
Netzwerk automatisch scannt, alle erreichbaren Geräte und ihre Dienste
erfasst und das Ergebnis als normierte CSV-Dateien bereitstellt.

Kurz gesagt:
  Netzwerk scannen → Geräte erfassen → CSV produzieren → Archi importieren.

Warum das relevant ist:
  Manuelle IST-Erfassung einer Umgebung ist fehleranfällig, zeitaufwendig
  und veraltet sofort. Der NBX-Flow automatisiert den ersten Schritt —
  die Erfassung — und liefert eine reproduzierbare Basis für das
  ArchiMate-Modell der Physical und Application Layer.

Warum der Name NBX:
  NBX steht für NetBox-kompatibel. Der Flow orientiert sich am Datenmodell
  von NetBox Community (Devices, Services, Properties) ohne NetBox vorauszusetzen.
  Wenn NetBox in einem späteren Stage eingeführt wird, ist der Anker bereits
  vorhanden — nur NBX02 wird dann ausgetauscht.


================================================================================
2. WAS DER FLOW LEISTET
================================================================================

Der NBX-Flow ermöglicht:
  - Automatische Erkennung aller aktiven Hosts im konfigurierten IP-Bereich
  - Erfassung von Hostnamen, MAC-Adressen und Hersteller-Informationen
  - Erfassung offener Ports und Dienste (Services)
  - Normierte Ausgabe als trash_nbx.csv (ECM-kompatibel)
  - Erweiterte Attribute als properties_nbx.csv (mappbar in Archi)
  - Reproduzierbarer Lauf — gleiche Umgebung ergibt gleiche Ausgabe

Was er nicht leistet:
  - Keine IP-Adressen-Verwaltung (IPAM) — das ist NetBox-Scope, Folge-Sprint
  - Keine installierten Software-Pakete — kein natives Konzept ohne Plugin
  - Kein automatisches ArchiMate-Mapping — das übernimmt der ECM-Flow
  - Kein Push in NetBox — der Flow ist reiner Producer, kein Writer
  - Kein Echtzeit-Monitoring — einmaliger Scan, kein Daemon


================================================================================
3. GRUNDPRINZIPIEN
================================================================================

3.1 Producer — Consumer Trennung
----------------------------------
Der NBX-Flow produziert — der ECM-Flow konsumiert. Keine Vermischung.
NBX weiß nichts über ArchiMate-Typen. ECM weiß nichts über Netzwerk-Scans.
Die Schnittstelle ist trash_nbx.csv — ein stabiles, einfaches Format.

Konkret bedeutet das:
  NBX03 schreibt trash_nbx.csv nach 00-archimatechild\.
  ECM00 liest von dort. Kein direkter Aufruf zwischen den Reihen.
  Änderungen im NBX-Flow erfordern keine Änderungen im ECM-Flow
  solange das CSV-Format stabil bleibt.


3.2 Ein Script — eine Wirkung
-------------------------------
Jedes Script der NBX-Reihe hat genau eine fachliche Aufgabe.
Kein Script macht zwei Dinge gleichzeitig. (GOV 6.10)

Konkret bedeutet das:
  NBX00 löst nur die Root-Umgebung auf — kein Scan, keine Validierung.
  NBX01 validiert nur die Config — kein Scan, keine Normierung.
  NBX02 scannt nur — keine Normierung, kein CSV.
  NBX03 normiert nur — kein Scan, kein Report.
  NBX04 reportet nur — keine Datenverarbeitung.


3.3 Plattformunabhängigkeit
-----------------------------
Der Flow läuft auf Windows und Linux gleichermaßen.
Externe Abhängigkeiten sind explizit dokumentiert.
Wenn eine Library nur auf einem OS verfügbar ist wird das klar ausgewiesen.

Konkret bedeutet das:
  nmap binary und python-nmap sind Pflicht-Voraussetzungen — beide
  plattformunabhängig. Kein Script verwendet OS-spezifische APIs ohne
  expliziten Hinweis. Install.txt führt alle Abhängigkeiten.


3.4 Kein ArchiMate im NBX-Flow
--------------------------------
Der NBX-Flow kennt keine ArchiMate-Typen. Er produziert NetBox-nahe
Rohfelder. Das Mapping auf Device, SystemSoftware, ApplicationService
etc. ist Aufgabe des ECM-Flows via Archi Mapping-Modell. (GOV 4.3, 4.5)

Konkret bedeutet das:
  trash_nbx.csv enthält nbx_objecttype: host / service — keine
  ArchiMate-Konzepte. Das Mapping-Modell in Archi entscheidet wie
  ein "host" im Modell landet. EUMAXL trifft diese Entscheidung
  einmalig in Archi — nicht im Script.


3.5 NetBox-Anker für spätere Integration
------------------------------------------
Das Datenmodell von trash_nbx.csv orientiert sich bewusst an NetBox.
Feldnamen, Objekttypen und die 3PartyID-Logik sind so gewählt dass
eine spätere NetBox-Integration nur NBX02 betrifft.

Konkret bedeutet das:
  Wenn NetBox produktiv eingeführt wird ersetzt NBX02 den nmap-Scan
  durch einen NetBox API-Call. NBX03, NBX04 und der gesamte ECM-Flow
  bleiben unverändert. Der Anker ist bereits gesetzt.


================================================================================
4. VORAUSSETZUNGEN
================================================================================

Bevor du mit dem NBX-Flow arbeitest:
  - R+MUNI ist installiert und der erste Funktionstest war grün
  - Python 3.10+ verfügbar
  - nmap binary installiert (https://nmap.org/download.html)
    Windows: Standard-Installer, nach Installation Shell neu starten
  - python-nmap installiert: pip install python-nmap
  - nbx_config.txt angelegt unter:
    01-artifacts\02-csv\01-mapping\nbx_config.txt
  - ip_range im lokalen Netzwerk bekannt (z.B. 192.168.1.0/24)
  - Script wird als Administrator ausgeführt für vollständige ARP-Scans
    (empfohlen, nicht zwingend — ohne Admin werden WLAN-Geräte u.U. nicht erkannt)


================================================================================
5. ABGRENZUNG UND GRENZEN
================================================================================

Der NBX-Flow ist Teil von R+MUNI — aber nicht alles.

Was hier geregelt ist:
  - Netzwerk-Scan und Host-Erfassung (NBX02)
  - Normierung auf ECM-kompatibles Format (NBX03)
  - Übergabe an ECM-Flow via trash_nbx.csv und properties_nbx.csv

Was woanders geregelt ist:
  - ArchiMate-Mapping → [[ECM_How2_DEV_S8]]
  - CSV → Archi Import → [[CSV_FLOW_How2_S8]]
  - Ordner bereinigen vor/nach NBX-Lauf → CLE-Reihe
  - IPAM, Tenancy, Circuits → Folge-Sprint (NetBox)


================================================================================
SUPPORT UND FEEDBACK
================================================================================

Fragen oder etwas unklar?

→ Ticketsystem: https://ims-blueprint-ticketsystem.atlassian.net/helpcenter/RMNP/


================================================================================
NBX_principles_DEV_S102 | S1.02 | 2026-04-06 | R+MUNI Blueprint
================================================================================
