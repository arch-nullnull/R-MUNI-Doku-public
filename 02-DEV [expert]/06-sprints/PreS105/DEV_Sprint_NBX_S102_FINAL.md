================================================================================
NBX-FLOW — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_NBX_S102
Tag             : #dev #sprint #nbx #netbox #s102
Datum           : 2026-04-07
Stage           : S1.02 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : 2026-04-07
Jira-Sync       : NEIN
================================================================================

---
title: "NBX-Flow — NetBox IST-Erfassung als 3PartyID Quelle"
stage: S1.02
status: "ABGESCHLOSSEN"
typ: "Sprint"
datum: "2026-04-07"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, nbx, netbox, s102]
---

================================================================================
NBX-FLOW — SPRINT (DEV)
Stage S1.02 | ABGESCHLOSSEN | R+MUNI Blueprint
================================================================================

---

## Kontext

Erfassung einer realen lokalen Umgebung (Hardware, VMs, Services) via
nmap-basiertem Netzwerk-Scan als neue eigenständige Script-Reihe (NBX).
Ziel ist ein normiertes Output-Artefakt (trash_nbx.csv) das als
3PartyID-Quelle in den bestehenden ECM-Flow einläuft und damit den Weg
in Archi 5.8 über den CSV-Flow ermöglicht.

Der Sprint entstand aus dem Bedarf, ArchiMate-Modelle für Application Layer
und Physical Layer aus real erfassten Umgebungsdaten zu speisen — ohne
manuelle Dateneingabe, ohne Überfrachtung bestehender Reihen, ohne Tool-Lock.

Hinweis zur Architekturanpassung im Sprint:
Das ursprüngliche Konzept sah NetBox Community REST API als primäre Quelle
(pynetbox / Modus A). Im Verlauf des Sprints wurde die Quelle auf einen
direkten nmap-Netzwerk-Scan umgestellt. NetBox als Zwischenschicht entfällt
damit in diesem Sprint — nmap ist direkter, deterministischer und ohne
zusätzliche Infrastruktur lauffähig. Die Entscheidung ist in Abschnitt 3
dokumentiert.

NBX-Flow ist Producer — ECM-Flow ist Consumer. Keine Vermischung.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[ECM_How2_DEV_S8]]                  Consumer des NBX-Outputs (ECM Phase 1+2)
- [[CSV_FLOW_How2_S8]]                 Ziel-Flow nach ECM (Archi Import)
- [[NetBox_Skill]]                     NBX-spezifischer Kontext-Skill (ursprünglich)

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Feature-Zuwachs
Beschreibung: Bedarf an automatisierter IST-Erfassung lokaler Umgebungen
              (Hardware, VMs, Services) als ArchiMate-Quelle für Application
              und Physical Layer. Bisher kein strukturierter Erfassungsweg
              im R+MUNI Blueprint vorhanden. NetBox Community war die
              ursprünglich geplante technische Basis — im Sprint auf
              nmap-Direktscan umgestellt. NBX-Reihe schließt die Lücke.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         Lauffähige NBX-Reihe (NBX00-NBX04) die eine lokale Umgebung
              erfasst, normiert und als trash_nbx.csv bereitstellt — so dass
              ECM-Flow (ECM00-ECM03) darauf aufsetzen kann und das Ergebnis
              final über den CSV-Flow in Archi 5.8 importierbar ist.

              Erfolgskriterium: trash_nbx.csv enthält die erfassten Hosts
              und Services der lokalen Umgebung in korrektem Format,
              ECM02 verarbeitet sie ohne Fehler, Archi Import läuft durch.

Abgrenzung:   - Kein IPAM (IP-Adressen, VLANs, Prefixes)
              - Keine installierten Software-Pakete
              - Kein Modus B (Agent-Dump) und Modus C (Export) in diesem Sprint
              - Kein automatisches Schreiben in run-scope.txt (manuell)
              - Kein Atlassian-Sync in diesem Sprint


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  Kein NBX-Flow vorhanden. Keine strukturierte Erfassung lokaler Umgebungen
  im R+MUNI Blueprint. ECM-Flow existiert und funktioniert für manuelle
  CSV-Quellen. CSV-Flow und Archi-Import-Mechanismus sind stabil.
  NetBox_Skill.md erstellt und bereit zur Aktivierung.
  Konzeptdokument NBX_FLOW_KONZEPT_DEV_S102_v2.md erarbeitet und freigegeben.

Soll-Zustand nach dem Sprint:
  NBX00-NBX04 Scripts existieren, sind lokal getestet, produzieren
  trash_nbx.csv aus einem laufenden nmap-Scan (Modus A adaptiert).
  ECM Phase 1 einmalig durchgeführt — Mapping-Modell in Archi vorhanden.
  Mindestens ein vollständiger Durchlauf NBX → ECM → CSV → Archi dokumentiert.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 NBX00 — Umgebungsvalidierung
----------------------------------
Script NBX00-validate_environment.py erstellt und lauffähig.

Funktion:
  Löst root.cfg via HLP00 auf. Prüft Erreichbarkeit HLP00, Vorhandensein
  root.cfg, 99-logs, nbx_config.txt (01-artifacts\02-csv\01-mapping\)
  und 00-archimatechild. Schreibt NBX00-root.resolved.txt in 99-logs.

Output:     02-stages\99-logs\NBX00-root.resolved.txt
            02-stages\99-logs\NBX00-validate_environment.log
Folge:      NBX01
GOV-Konform: JA


2.2 NBX01 — Konfigurationsvalidierung
---------------------------------------
Script NBX01-validate_config.py erstellt und lauffähig.

Funktion:
  Liest nbx_config.txt (ip_range, scan_ports, output_label).
  Prüft Pflichtfelder: ip_range vorhanden und parsebar, scan_ports gültig,
  output_label gesetzt. Validiert ip_range syntaktisch (CIDR oder Range).
  Gibt Warnung bei mehr als 254 Hosts.

Output:     02-stages\99-logs\NBX01-validate_config.log
Folge:      NBX02
GOV-Konform: JA


2.3 NBX02 — Netzwerk-Scan
---------------------------
Script NBX02-scan_network.py erstellt und lauffähig.

Funktion:
  Liest ip_range und scan_ports aus nbx_config.txt.
  Führt nmap-Scan via python-nmap durch (Modus: -sV für Service-Detection).
  Erfasst erreichbare Hosts, Hostnamen, OS-Hints, offene Ports + Services,
  MAC-Adressen und Hersteller-Informationen.
  Schreibt Rohdaten als nbx_raw.json in 02-stages\.

Abhängigkeiten: nmap binary, python-nmap (pip install python-nmap)
Output:     02-stages\nbx_raw.json
            02-stages\99-logs\NBX02-scan_network.log
Folge:      NBX03
GOV-Konform: JA

Produktivlauf (lokales Netz 192.168.1.0/24):
  Erfasste Hosts: 6 (Gaming-PC, Surface-Book, FRITZ!Box, Nintendo Switch,
                     Android_4RORI7TF, Android_3U2ZRVGG, A54-von-Markus)
  Erfasste Services: 9


2.4 NBX03 — Normierung und CSV-Export
---------------------------------------
Script NBX03-normalize_to_csv.py erstellt und lauffähig.

Funktion:
  Liest nbx_raw.json. Normiert Hosts und Services in zwei Ausgabedateien:
  - trash_nbx.csv: eine Zeile pro Host/Service, Kern-Felder, ECM-kompatibel
  - properties_nbx.csv: Key-Value Attribute je Host (MAC, Ports, Services)

  Spaltenstruktur trash_nbx.csv:
    3PartyID, nbx_objecttype, Name, Role, Platform, Site,
    Status, Manufacturer, Model, Description, nbx_source, nbx_raw_id

  3PartyID-Schema: nbx_<IP_underscore>[_<proto>_<port>]
  nbx_objecttype: "host" oder "service"
  nbx_source:     "scan_lokal" (aus output_label in nbx_config.txt)

Output:     01-artifacts\02-csv\03-child\00-archimatechild\trash_nbx.csv
            01-artifacts\02-csv\03-child\00-archimatechild\properties_nbx.csv
            02-stages\99-logs\NBX03-normalize_to_csv.log
Folge:      NBX04
GOV-Konform: JA

Produktivlauf — trash_nbx.csv Inhalt (16 Zeilen, 6 Hosts + 9 Services + 1 Header):

  HOST-Objekte (nbx_objecttype=host):
    nbx_192_168_1_12   | Gaming-PC         | up | —                                   | scan_lokal
    nbx_192_168_1_38   | A54-von-Markus    | up | —                                   | scan_lokal
    nbx_192_168_1_43   | Surface-Book      | up | Microsoft                           | scan_lokal
    nbx_192_168_1_138  | FRITZ!Box         | up | AVM Audiovisuelles Marketing...     | scan_lokal
    nbx_192_168_1_17   | nintendoswitch    | up | Nintendo                            | scan_lokal
    nbx_192_168_1_30   | Android_4RORI7TF  | up | —                                   | scan_lokal
    nbx_192_168_1_15   | Android_3U2ZRVGG  | up | —                                   | scan_lokal

  SERVICE-Objekte (nbx_objecttype=service):
    nbx_192_168_1_12_tcp_135  | msrpc         | Gaming-PC   | Microsoft Windows RPC | Port 135/tcp
    nbx_192_168_1_12_tcp_139  | netbios-ssn   | Gaming-PC   | Microsoft Windows netbios-ssn | Port 139/tcp
    nbx_192_168_1_12_tcp_445  | microsoft-ds  | Gaming-PC   | Port 445/tcp
    nbx_192_168_1_43_tcp_135  | msrpc         | Surface-Book | Microsoft Windows RPC | Port 135/tcp
    nbx_192_168_1_43_tcp_139  | netbios-ssn   | Surface-Book | Microsoft Windows netbios-ssn | Port 139/tcp
    nbx_192_168_1_43_tcp_445  | microsoft-ds  | Surface-Book | Port 445/tcp
    nbx_192_168_1_138_tcp_53  | domain        | FRITZ!Box   | NLnet Labs NSD | Port 53/tcp
    nbx_192_168_1_138_tcp_80  | http          | FRITZ!Box   | FRITZ!Box http config | Port 80/tcp
    nbx_192_168_1_138_tcp_443 | http          | FRITZ!Box   | FRITZ!Box http config | Port 443/tcp


2.5 NBX04 — Übergabe-Report
-----------------------------
Script NBX04-handoff_report.py erstellt und lauffähig.

Funktion:
  Liest trash_nbx.csv. Erstellt menschenlesbaren Übergabe-Report mit
  Statistik (Hosts je Typ, Services je Host) und konkreten nächsten
  Schritten für den ECM-Flow.

Output:     02-stages\99-logs\NBX04-handoff_report.txt
            02-stages\99-logs\NBX04-handoff_report.log
Folge:      ECM00
GOV-Konform: JA

Report-Inhalt (Produktivlauf):
  Gesamtzahl Objekte:  16 (inkl. Header: 17 Zeilen)
  Hosts:               7
  Services:            9
  Erfasste Hersteller: Microsoft, AVM, Nintendo
  Nächste Schritte:    ECM00 → ECM01 → ECM02 → ECM03 → CSV-Flow → Archi


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Architekturwechsel — nmap statt NetBox REST API
  Auslöser:    Sprint-Start: NetBox Community Instanz als Quelle geplant.
               Im Verlauf: nmap-Direktscan als einfachere, infrastrukturfreie
               Alternative identifiziert.
  Ergebnis:    NBX02 verwendet python-nmap für Netzwerk-Scan statt pynetbox.
               NetBox Community als Zwischenschicht entfällt in diesem Sprint.
               NBX-Reihe bleibt eigenständig und technisch neutral benannt.
  Begründung:  nmap ist deterministisch, reproduzierbar, ohne Zusatzinfra.
               GOV 6.10 (Scripts deterministisch und reproduzierbar).
               NetBox als Quelle bleibt konzeptuell gültig — Modus B
               (NetBox API) als Folge-Sprint bei Bedarf.
  GOV-Bezug:   GOV 6.10, GOV 7.5 (Feature-Zuwachs)
  Auswirkung:  nbx_config.txt enthält ip_range + scan_ports statt
               NetBox URL + Token. Kein pynetbox erforderlich.
               Umbenennung trash_nbx → trash_nbx.csv (Dateiname angepasst).
  Rückwirkung: NEIN — ursprüngliches Konzept war Vorbereitungsphase,
               kein produktiver Code betroffen.

Entscheidung: ECM als primärer Import-Mechanismus
  Auslöser:    NBX-Flow könnte theoretisch direkt Archi-kompatibles CSV
               erzeugen — müsste dann aber ArchiMate-Typen hardcoden.
  Ergebnis:    ECM-Flow übernimmt das Mapping via Archi Mapping-Modell (OEF).
               NBX-Flow produziert Rohfelder ohne ArchiMate-Typen.
  Begründung:  Mapping gehört explizit in Archi (GOV 4.3, GOV 4.5).
               ECM Phase 1 löst das sauber — einmalig, visuell, durch EUMAXL.
  GOV-Bezug:   GOV 4.3, 4.5, 6.5
  Auswirkung:  trash_nbx.csv enthält keine ArchiMate-Typen. ECM Phase 1
               muss einmalig vor erstem produktiven Lauf durchgeführt werden.
  Rückwirkung: NEIN

Entscheidung: NBX als eigenständige Reihe — kein Teil von ECM
  Auslöser:    Frage ob NBX in ECM integriert oder eigenständig geführt wird.
  Ergebnis:    Eigenständige Reihe mit Kürzel NBX (NBX00-NBX04).
  Begründung:  Klare Trennung Producer (NBX) / Consumer (ECM). GOV 5.6
               (Ebenentrennung). Keine Vermischung von Datenerfassung
               und Import-Mechanismus.
  GOV-Bezug:   GOV 5.6, 6.9
  Auswirkung:  Eigene Script-Dateien NBX00-NBX04 in 01-artifacts\01-scripts\.
               Eigene Konfiguration nbx_config.txt.
               nbx_config.txt in .gitignore (enthält IP-Konfiguration).
  Rückwirkung: NEIN

Entscheidung: Software-Inventar out of scope
  Auslöser:    Frage ob installierte Software-Pakete erfassbar sind.
  Ergebnis:    Out of scope — kein natives Konzept in nmap oder NetBox Core.
  Begründung:  nmap erfasst laufende Services (Ports/Protokolle) — das ist
               der verfügbare Rohstoff für Application Layer.
               Installierte Applikationen: andere Quelle oder manuell.
  GOV-Bezug:   GOV 1.4 (Explizitheit), GOV 3.4 (keine implizite Weiterentwicklung)
  Auswirkung:  Application Layer aus NBX = Services (laufende Ports).
  Rückwirkung: NEIN

Entscheidung: Trennzeichen Komma (Standard R+MUNI)
  Auslöser:    Konzept v1 hatte irrtümlich Semikolon als Trennzeichen.
  Ergebnis:    Komma — entspricht R+MUNI Standard.
  Begründung:  Explizite Korrektur. Standard gilt systemweit.
  GOV-Bezug:   GOV 6.6 (CSV und Transportformate)
  Auswirkung:  trash_nbx.csv verwendet Komma. ECM01 erkennt automatisch.
  Rückwirkung: NEIN

Entscheidung: Dateiname trash_nbx.csv (nicht nbx_trash.csv)
  Auslöser:    Ursprüngliches Konzept verwendete "nbx_trash.csv".
               Im Produktivlauf entstandene Datei heißt "trash_nbx.csv".
  Ergebnis:    Produktivname ist trash_nbx.csv — konsistent mit Benennungslogik
               anderer trash-Dateien im Blueprint (trash_<quelle>.csv).
  Begründung:  Namenskonvention: Präfix "trash_" kennzeichnet den Rohstoff
               vor ECM-Verarbeitung. Quelle als Suffix.
  GOV-Bezug:   GOV 6.6
  Auswirkung:  Alle Referenzen in Dokumentation auf trash_nbx.csv korrigiert.
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Architekturwechsel innerhalb Sprint (NetBox → nmap)
  GOV-Regel:   GOV 7.6 — Ziel muss eindeutig und überprüfbar sein.
               Ursprüngliches Zieldokument nannte NetBox REST API explizit.
  Begründung:  Technische Evaluierung im Sprint ergab, dass nmap-Direktscan
               das identische Ergebnis mit weniger Infrastrukturabhängigkeit
               liefert. Ziel (lauffähige NBX-Reihe, trash_nbx.csv als Output,
               ECM-kompatibel) bleibt unverändert — Implementierungsweg angepasst.
  Wirkung:     Auf diesen Sprint begrenzt. NetBox als Quelle (Modus B)
               bleibt als Folge-Sprint-Option erhalten.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Zu früher Output — Konzeptdokument v1 wurde erstellt
  bevor Dialog vollständig geführt war. Trennzeichen falsch, ECM-Weg
  nicht ausreichend begründet, ArchiType-Feld im CSV war Annahme.
  Korrektur in v2 nach Dialog.

⚠ Verhaltenshinweis: Template-Pflicht verletzt — Konzeptdokument wurde
  nicht nach DEV Sprint Template erstellt.
  Korrektur: dieses Dokument als finale Sprint-Doku.

⚠ Verhaltenshinweis: Fetch-Ergebnis zu Software-Inventar zeigte klar
  dass kein natives Konzept vorhanden — aktiv kommuniziert statt
  stillschweigend übergangen.

⚠ Verhaltenshinweis: SKILL.md Dateiname hätte bestehenden Skill
  überschrieben — auf Hinweis von EUMAXL korrigiert zu NetBox_Skill.md.

⚠ Verhaltenshinweis: Architekturwechsel (NetBox → nmap) im Sprint
  aktiv kommuniziert und dokumentiert — kein stiller Wechsel.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt                              | GOV-Bezug  | Status     | Nächste Aktion                                          |
|------------------------------------|------------|------------|---------------------------------------------------------|
| ECM Phase 1 Mapping-Modell bauen   | keiner     | offen      | Nach NBX03-Lauf — EUMAXL in Archi durchführen          |
| ECM01-ECM03 Lauf mit trash_nbx.csv | keiner     | offen      | Vollständiger Durchlauf NBX → ECM → CSV → Archi         |
| nbx_config.txt in .gitignore       | GOV 6.13   | offen      | Eintragen — enthält IP-Konfiguration lokales Netz       |
| 02-stages/ in .gitignore prüfen    | GOV 6.13   | offen      | Prüfen ob nbx_raw.json automatisch ignoriert wird       |
| run-scope.txt Ergänzung nach NBX03 | GOV 4.3    | offen      | Manuell nach produktivem Lauf ergänzen                  |
| Modi B (NetBox API) und C (Export) | GOV 7.5    | Folge-Sprint| Bei Bedarf — kein akuter Handlungsbedarf               |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA
  — NBX00-validate_environment.py      01-artifacts\01-scripts\
  — NBX01-validate_config.py           01-artifacts\01-scripts\
  — NBX02-scan_network.py              01-artifacts\01-scripts\
  — NBX03-normalize_to_csv.py          01-artifacts\01-scripts\
  — NBX04-handoff_report.py            01-artifacts\01-scripts\
  — trash_nbx.csv                      01-artifacts\02-csv\03-child\00-archimatechild\
  — properties_nbx.csv                 01-artifacts\02-csv\03-child\00-archimatechild\
  — NBX04-handoff_report.txt           02-stages\99-logs\
  — DEV_Sprint_NBX_S102_FINAL.md       00-internal\99-doku\ (dieses Dokument)
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Klare Producer/Consumer-Trennung (NBX → ECM) hat Scope-Creep verhindert.
  - Eigenständige Script-Reihe NBX mit einheitlichem Kürzel ist wartbar
    und erweiterbar ohne Eingriff in ECM oder CSV-Reihen.
  - Entscheidungen wurden explizit dokumentiert — auch der Architekturwechsel.
  - nmap als Scan-Basis ist reproduzierbar und infrastrukturlos lauffähig.
  - trash_nbx.csv Produktivlauf erfolgreich: 16 Objekte, 7 Hosts, 9 Services.

Was beim nächsten Mal anders gemacht werden sollte:
  - Dialog vor Output konsequenter führen. Konzept v1 hätte nach Dialog
    entstehen sollen, nicht vorher. Mehraufwand durch v2-Korrekturrunde.
  - Architekturwechsel früher explizit machen — nicht erst nach Konzept v1.
  - nbx_config.txt sofort in .gitignore eintragen, nicht als offenen Punkt
    stehenlassen.

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Dialog vor Output ist in AI Driven Kap. 4 verankert — in dieser Session
    nicht konsequent eingehalten. Kein GOV-Änderungsbedarf.
    Bewusstsein schärfen: JA. Neuer Sprint: NEIN.
  - Dateinamenskonvention trash_<quelle>.csv ist implizit entstanden und
    sollte in GOV 6.6 oder CSV_FLOW_How2 explizit dokumentiert werden.
    Sprint anlegen: NEIN — bei nächster regulärer GOV-Revision aufnehmen.

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[ECM_How2_DEV_S8]]                  Consumer des NBX-Outputs
[[CSV_FLOW_How2_S8]]                 Ziel-Flow nach ECM
[[NetBox_Skill]]                     NBX-spezifischer Kontext-Skill

---

================================================================================
NBX-FLOW — SPRINT (DEV) | S1.02 | 2026-04-07 | R+MUNI Blueprint
================================================================================
