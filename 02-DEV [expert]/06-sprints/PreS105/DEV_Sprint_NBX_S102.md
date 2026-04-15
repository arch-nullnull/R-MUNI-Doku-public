================================================================================
NBX-FLOW — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_NBX_S102
Tag             : #dev #sprint #nbx #netbox #s102
Datum           : 2026-04-06
Stage           : S1.02 — AKTIV
Status          : IN ARBEIT
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================

---
title: "NBX-Flow — NetBox IST-Erfassung als 3PartyID Quelle"
stage: S1.02
status: "IN ARBEIT"
typ: "Sprint"
datum: "2026-04-06"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, nbx, netbox, s102]
---

================================================================================
NBX-FLOW — SPRINT (DEV)
Stage S1.02 | IN ARBEIT | R+MUNI Blueprint
================================================================================

---

## Kontext

Erfassung einer realen lokalen Umgebung (Hardware, VMs, Services) via NetBox
Community als neue eigenständige Script-Reihe (NBX). Ziel ist ein normiertes
Output-Artefakt (nbx_trash.csv) das als 3PartyID-Quelle in den bestehenden
ECM-Flow einläuft und damit den Weg in Archi 5.8 über den CSV-Flow ermöglicht.

Der Sprint entstand aus dem Bedarf, ArchiMate-Modelle für Application Layer
und Physical Layer aus real erfassten Umgebungsdaten zu speisen — ohne manuelle
Dateneingabe, ohne Überfrachtung bestehender Reihen, ohne Tool-Lock.

NetBox Community dient dabei als lokale Source of Truth.
Der NBX-Flow ist Producer — ECM-Flow ist Consumer. Keine Vermischung.

Skill-Basis: NetBox_Skill.md (aktiv laden zu Beginn jeder NBX-Session).

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[ECM_How2_DEV_S8]]                  Consumer des NBX-Outputs (ECM Phase 1+2)
- [[CSV_FLOW_How2_S8]]                 Ziel-Flow nach ECM (Archi Import)
- [[NetBox_Skill]]                     NBX-spezifischer Kontext-Skill

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
              im R+MUNI Blueprint vorhanden. NetBox Community bietet die
              technische Basis — NBX-Reihe schließt die Lücke.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         Lauffähige NBX-Reihe (NBX00-NBX04) die eine lokale Umgebung
              via NetBox REST API erfasst, normiert und als nbx_trash.csv
              bereitstellt — so dass ECM-Flow (ECM00-ECM03) darauf aufsetzen
              kann und das Ergebnis final über den CSV-Flow in Archi 5.8
              importierbar ist.

              Erfolgskriterium: nbx_trash.csv enthält die erfassten Devices,
              VMs und Services der lokalen Umgebung in korrektem Format,
              ECM02 verarbeitet sie ohne Fehler, Archi Import läuft durch.

Abgrenzung:   - Kein IPAM (IP-Adressen, VLANs, Prefixes)
              - Keine installierten Software-Pakete (kein natives NetBox-Konzept)
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
  nbx_trash.csv aus einer laufenden NetBox-Instanz (Modus A).
  ECM Phase 1 einmalig durchgeführt — Mapping-Modell in Archi vorhanden.
  Mindestens ein vollständiger Durchlauf NBX → ECM → CSV → Archi dokumentiert.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

<!-- Wird während des Sprints befüllt. -->

2.1 —
------
Noch nicht begonnen.


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: ECM als primärer Import-Mechanismus
  Auslöser:    NBX-Flow könnte theoretisch direkt Archi-kompatibles CSV erzeugen,
               müsste dann aber selbst wissen welcher NetBox-Typ welches
               ArchiMate-Konzept wird — eine hardcodierte Matrix.
  Ergebnis:    ECM-Flow übernimmt das Mapping via Archi Mapping-Modell (OEF).
               NBX-Flow produziert NetBox-Rohfelder ohne ArchiMate-Typen.
  Begründung:  Mapping gehört explizit in Archi (GOV 4.3 Explizitheit,
               GOV 4.5 Tool-Unabhängigkeit). ECM Phase 1 löst das sauber
               und nachvollziehbar — einmalig, visuell, durch EUMAXL.
  GOV-Bezug:   GOV 4.3, 4.5, 6.5
  Auswirkung:  nbx_trash.csv enthält keine ArchiMate-Typen. ECM Phase 1
               muss einmalig vor erstem produktiven Lauf durchgeführt werden.
  Rückwirkung: NEIN

Entscheidung: Modus A (REST API via pynetbox) als primärer Erfassungsmodus
  Auslöser:    Drei mögliche Modi (API / Agent-Dump / Export) — einer muss
               für Sprint 1 priorisiert werden.
  Ergebnis:    Modus A — direkte REST API Abfrage via pynetbox.
  Begründung:  Modus A ist der natürliche Weg nach netbox-agent Erfassung.
               netbox-agent schreibt in NetBox → NBX01 liest via API.
               Community-Standard (pynetbox). Reproduzierbar, deterministisch.
               Modi B und C als Folge-Sprint wenn Bedarf entsteht.
  GOV-Bezug:   GOV 6.10 (Scripts deterministisch und reproduzierbar)
  Auswirkung:  NetBox-Instanz muss lokal laufen für Sprint 1.
               nbx_config.txt mit URL + Token erforderlich.
  Rückwirkung: NEIN

Entscheidung: NBX als eigenständige Reihe — kein Teil von ECM
  Auslöser:    Frage ob NBX in ECM integriert oder eigenständig geführt wird.
  Ergebnis:    Eigenständige Reihe mit Kürzel NBX (NBX00-NBX04).
  Begründung:  Klare Trennung Producer (NBX) / Consumer (ECM). GOV 5.6
               (Ebenentrennung). Keine Vermischung von Datenerfassung
               und Import-Mechanismus.
  GOV-Bezug:   GOV 5.6, 6.9
  Auswirkung:  Eigene Script-Dateien NBX00-NBX04 in 01-artifacts\01-scripts\.
               Eigene Konfiguration nbx_config.txt neben root.cfg.
               nbx_config.txt in .gitignore (enthält API Token).
  Rückwirkung: NEIN

Entscheidung: Software-Inventar out of scope
  Auslöser:    Frage ob installierte Software-Pakete aus NetBox erfassbar sind.
  Ergebnis:    Out of scope — kein natives Konzept im NetBox Community Core.
  Begründung:  NetBox Community hat kein "Installed Software" Modell im Core.
               Services (laufende Ports/Protokolle) sind der verfügbare
               Rohstoff für Application Layer. Community bestätigt das explizit.
               Erweiterung via Plugin möglich — Folge-Sprint bei Bedarf.
  GOV-Bezug:   GOV 1.4 (Explizitheit), GOV 3.4 (keine implizite Weiterentwicklung)
  Auswirkung:  Application Layer aus NetBox = Services (dcim + virtualization).
               Installierte Applikationen: andere Quelle oder manuell.
  Rückwirkung: NEIN

Entscheidung: Trennzeichen Komma (Standard R+MUNI)
  Auslöser:    Konzept v1 hatte irrtümlich Semikolon als Trennzeichen.
  Ergebnis:    Komma — entspricht R+MUNI Standard.
  Begründung:  Explizite Korrektur. Standard gilt systemweit sofern nicht
               explizit anders formuliert.
  GOV-Bezug:   GOV 6.6 (CSV und Transportformate)
  Auswirkung:  nbx_trash.csv verwendet Komma. ECM01 erkennt Trennzeichen
               automatisch — kein Konflikt.
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Keine Abweichungen.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Zu früher Output — Konzeptdokument v1 wurde erstellt
  bevor Dialog vollständig geführt war. Trennzeichen falsch, ECM-Weg
  nicht ausreichend begründet, ArchiType-Feld im CSV war Annahme.
  Korrektur in v2 nach Dialog.

⚠ Verhaltenshinweis: Template-Pflicht verletzt — Konzeptdokument wurde
  nicht nach DEV Sprint Template erstellt. Korrektur: dieses Dokument.

⚠ Verhaltenshinweis: Fetch-Ergebnis zu Software-Inventar zeigte klar
  dass kein natives Konzept vorhanden — aktiv kommuniziert statt
  stillschweigend übergangen.

⚠ Verhaltenshinweis: SKILL.md Dateiname hätte bestehenden Skill
  überschrieben — auf Hinweis von EUMAXL korrigiert zu NetBox_Skill.md.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| NetBox Version der Zielumgebung klären | GOV 6.1 | offen | Zu Beginn Sprint klären — relevant für Modules vs. InventoryItem |
| nbx_config.txt in .gitignore eintragen | GOV 6.13 | offen | Erster Schritt in Sprint-Session |
| 02-stages/ bereits in .gitignore? | GOV 6.13 | offen | Prüfen ob nbx_raw.json automatisch ignoriert wird |
| run-scope.txt Ergänzung nach NBX03 | GOV 4.3 | offen | Manuell oder NBX04-Erweiterung — Entscheidung im Sprint |
| ECM Phase 1 Mapping-Modell bauen | keiner | offen | Nach erstem NBX03-Lauf — EUMAXL in Archi |
| Modi B und C | GOV 7.5 | offen | Folge-Sprint bei Bedarf |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          NEIN — Sprint läuft
GOV-Konformität hergestellt:      NEIN — Sprint läuft
Alle Entscheidungen dokumentiert: JA — Vorbereitungsphase vollständig
Artefakte abgelegt:               NEIN — Sprint läuft
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

<!-- Wird nach Sprint-Abschluss befüllt. -->

Was gut funktioniert hat:
  - —

Was beim nächsten Mal anders gemacht werden sollte:
  - —

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - Dialog vor Output — in AI Driven Kap. 4 verankert, in dieser Session
    nicht konsequent eingehalten. Kein GOV-Änderungsbedarf — Bewusstsein
    schärfen: JA

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[NetBox_Skill]]                     NBX-spezifischer Kontext-Skill
[[ECM_How2_DEV_S8]]                  Consumer des NBX-Outputs
[[CSV_FLOW_How2_S8]]                 Ziel-Flow nach ECM

---

================================================================================
NBX-FLOW — SPRINT (DEV) | S1.02 | 2026-04-06 | R+MUNI Blueprint
================================================================================
