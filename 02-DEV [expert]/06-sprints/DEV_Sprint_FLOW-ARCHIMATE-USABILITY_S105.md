================================================================================
FLOW ARCHIMATE USABILITY — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_FLOW-ARCHIMATE-USABILITY_S105
Tag             : #dev #sprint #flow #archimate #usability #s105
Datum           : 2026-04-13
Stage           : S1.05 — AKTIV
Status          : IN ARBEIT
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Ablageort       : R+MUNI Doku-internal\sprints\
================================================================================

---
title: "FLOW Archimate Usability — Scriptreihen ohne How2 bedienbar machen"
stage: S1.05
status: "IN ARBEIT"
typ: "Sprint"
datum: "2026-04-13"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, flow, archimate, usability, s105]
---

================================================================================
FLOW ARCHIMATE USABILITY — SPRINT (DEV)
Stage S1.05 | IN ARBEIT | R+MUNI Blueprint
================================================================================

---

## Kontext

Die bestehenden Scriptreihen (NBX, ECM, CSV, FLW) sind technisch funktionsfähig
und in ihrer DEV-Dokumentation vollständig beschrieben. Der Gap liegt auf der
Kundenseite: Ein R+MUNI Kunde soll den Weg von der Erfassung bis zum fertigen
ArchiMate-View eigenständig durchlaufen können — ohne ein How2 vor sich
aufzuschlagen, ohne Rückfragen an DEV, ohne Schritt-für-Schritt-Anleitung.

Das Ziel ist nicht eine neue Anleitung. Das Ziel ist, dass die Scriptreihen
selbst so aufbereitet sind, dass sie den Benutzer durch den Prozess führen:
klare Ausgaben, verständliche Fehlermeldungen, sichtbarer Fortschritt,
nachvollziehbarer Endzustand — ArchiMate View ready.

Auslöser ist die Beobachtung aus dem NBX-ECM Produktivrun (S105): Auch mit
vollständiger DEV-Doku war der korrekte Ablauf (insbesondere Import-Pfad
und Erstlauf-Logik) nicht intuitiv erkennbar. Wenn das für DEV gilt,
gilt es umso mehr für R+MUNI Kunden.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]              normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
- [[DEV_Sprint_NBX-ECM-RUN_S105]]      Auslöser — Produktivrun Beobachtungen
- [[NBX_principles_DEV_S102]]          NBX Producer-Logik
- [[NBX_How2_DEV_S102]]                Technische NBX-Referenz
- [[STAGE105_ZIELE_S105]]              Stage-Kontext

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Feature-Zuwachs / Kundenbedarf
Beschreibung: R+MUNI Kunden sollen den vollständigen FLOW
              (Scan → CSV → Mapping → ArchiMate View) ohne geöffnetes
              How2-Dokument durchlaufen können. Die Scripts müssen
              selbsterklärend genug sein — durch ihre Ausgaben, ihre
              Fortschritts-Kommunikation und ihren Fehlermodus —
              dass kein externes Dokument parallel benötigt wird.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         R+MUNI Kunde führt NBX00–NBX05 → ECM00–ECM03 → Archi Import
              durch und erhält einen ArchiMate View — ohne How2 zu öffnen.

              Konkret messbar wenn:
              a) Script-Ausgaben zeigen klar wo der Lauf steht und was als
                 nächstes zu tun ist
              b) Fehlermeldungen nennen Ursache und direkte Lösung
              c) Handoff-Report (NBX05) enthält den vollständigen nächsten Schritt
                 für Archi-Import — ohne Zusatzwissen
              d) ECM01 Ausgabe macht klar was im Mapping-Modell zu tun ist
              e) Ein Testlauf durch eine unbegleitete Person ist fehlerfrei

Abgrenzung:   Kein Umbau der Script-Logik — nur Ausgabe-Qualität,
              Fehlermeldungen und Handoff-Texte werden angepasst.
              Kein neues Script — kein neues How2 Dokument.
              Keine Änderung am ArchiMate-Modell oder Mapping-Modell.
              BPMN Dokumentation ist NICHT Teil dieses Sprints.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  NBX00–NBX05 lauffähig (S105 Produktivrun bestätigt).
  ECM00–ECM03 lauffähig (S105 Produktivrun bestätigt).
  NBX05 Handoff Report: technisch korrekt, aber kein expliziter
    Archi-Import-Hinweis mit korrektem Quell-Pfad.
  ECM01 Ausgabe: Header als Artifacts korrekt, Erstlauf-Kontext
    nicht aus der Ausgabe erkennbar ohne How2-Kenntnis.
  Fehlermeldungen: technisch korrekt, aber nicht lösungsorientiert
    formuliert für Nicht-DEV-Nutzer.

Soll-Zustand nach dem Sprint:
  NBX05 Handoff Report enthält explizit:
    - Korrekten Quell-Pfad für Archi-Import (00-archimatechild\)
    - Nächsten Schritt für Erstlauf (Mapping-Modell aufbauen)
    - Nächsten Schritt für Folgeläufe (bestehendes Mapping verwenden)
  ECM01 Ausgabe kommuniziert Erstlauf-Kontext klar in der Konsole.
  Kritische Fehlermeldungen aller Reihen enthalten Ursache + Lösungsvorschlag.
  Manueller Testlauf durch Nicht-DEV-Person geplant oder dokumentiert
    als Validierungs-Anforderung.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle: DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

<!-- Wird laufend befüllt während des Sprints -->

2.1 Analyse — Gap-Identifikation Handoff und Ausgaben
------------------------------------------------------

Offen — wird in Sprint-Session erarbeitet.

Analyse-Fragen:
  - Welche Script-Ausgaben sind aus Kundensicht unklar?
  - Wo fehlt der "nächste Schritt" in der Ausgabe?
  - Welche Fehlermeldungen sind technisch aber nicht lösungsorientiert?
  - Was muss NBX05 zusätzlich ausgeben damit Archi-Import ohne How2 gelingt?

Artefakte:    Analyse-Ergebnis im Sprint-Dokument (Abschnitt 2.x)
GOV-Konform:  wird geprüft


2.2 NBX05 Handoff Report — Erweiterung
----------------------------------------

Offen.

Geplante Erweiterung:
  Sektion "Nächster Schritt" explizit in NBX05-handoff_report.txt:
    ERSTLAUF:
      Import-Pfad: <rootfolder>\01-artifacts\00-xml\03-child\00-archimatechild\
      Archi: Datei öffnen → Als Mapping-Modell aufbauen → OEF exportieren
             → 99-mappingmodel\ ablegen
    FOLGELAUF:
      Import-Pfad: <rootfolder>\01-artifacts\00-xml\03-child\00-archimatechild\
      Archi: Mit bestehendem Mapping-Modell importieren → Modell aktualisiert

  Pfad-Auflösung: root.cfg → dynamisch, kein Hardcode.

Artefakte:    NBX05-handoff_report.py (angepasst)
GOV-Konform:  wird geprüft


2.3 ECM01 — Konsolen-Ausgabe Erstlauf-Kontext
----------------------------------------------

Offen.

Geplante Erweiterung:
  Nach erfolgreichem ECM01-Lauf Ausgabe:
    ===== NÄCHSTER SCHRITT =====
    Erstlauf:  Öffne Archi → Importiere aus 03-child\00-archimatechild\
               Baue das Mapping-Modell visuell auf
               Exportiere als OEF XML → ablegen in 99-mappingmodel\
    Folgelauf: Importiere mit bestehendem Mapping-Modell aus 99-mappingmodel\
    ============================

Artefakte:    ECM01-csv_fields_to_artifacts.py (angepasst)
GOV-Konform:  wird geprüft


2.4 Fehlermeldungen — Lösungsorientierte Formulierung
------------------------------------------------------

Offen.

Scope:
  Alle kritischen [FEHLER]-Ausgaben in NBX00–NBX05 und ECM00–ECM03
  werden auf Lösungsorientierung geprüft. Format-Ziel:

    [FEHLER]  <Was ist schief gelaufen>
    Ursache:  <Warum passiert das>
    Lösung:   <Was der Nutzer tun soll>

  Beispiel aktuell:
    [FEHLER]  nbx_config.txt nicht gefunden

  Beispiel Ziel:
    [FEHLER]  nbx_config.txt nicht gefunden
    Ursache:  Konfigurationsdatei fehlt oder falscher Pfad in root.cfg
    Lösung:   nbx_config.txt anlegen unter 01-artifacts\02-csv\01-mapping\
              Vorlage: nbx_config.txt im Projektordner (root-Ebene)

Artefakte:    Scripts NBX00–NBX05, ECM00–ECM03 (selektiv angepasst)
GOV-Konform:  wird geprüft


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

<!-- Wird laufend befüllt -->

Entscheidung: Kein neues How2 — Usability kommt aus den Scripts
  Auslöser:    Ziel ist Usability ohne geöffnetes Dokument
  Ergebnis:    Kein neues Dokument wird erstellt. Anpassungen nur in
               Script-Ausgaben, Handoff-Texten und Fehlermeldungen.
  Begründung:  Ein weiteres How2 löst das Problem nicht — es verlagert es.
               Wenn die Scripts selbst sprechen, entfällt der Dokument-Bedarf.
  GOV-Bezug:   GOV 6.10 (ein Script — eine Wirkung bleibt erhalten),
               GOV 3.4 (keine implizite Weiterentwicklung ohne Bedarf)
  Auswirkung:  Engerer Scope — klarer Fokus auf Output-Qualität
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Keine Abweichungen bisher.


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Sprint-Dokument als Temp erstellt auf Anfrage EUMAXL.
  Vollständige Befüllung der Ergebnis-Sektionen erfolgt im Sprint selbst —
  Platzhalter sind bewusst offen gelassen, kein Inhalt erfunden.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| Gap-Analyse Script-Ausgaben | GOV 7.6 | offen | In Sprint-Session durchführen |
| NBX05 Handoff-Text anpassen | GOV 6.10 | offen | Script anpassen nach Gap-Analyse |
| ECM01 Konsolen-Text erweitern | GOV 6.10 | offen | Script anpassen nach Gap-Analyse |
| Fehlermeldungen überarbeiten | GOV 1.4 | offen | Scope festlegen — welche zuerst |
| Validierungs-Testlauf | GOV 7.6 | offen | Nach Script-Anpassungen planen |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          NEIN — Sprint in Arbeit
GOV-Konformität hergestellt:      NEIN — Sprint in Arbeit
Alle Entscheidungen dokumentiert: Laufend
Artefakte abgelegt:               NEIN — Sprint in Arbeit
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

<!-- Wird nach Sprint-Abschluss befüllt -->

Was gut funktioniert hat:
  — offen —

Was beim nächsten Mal anders gemacht werden sollte:
  — offen —

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  — offen —

---

## Bezüge

[[Global_GOV_DEV_S102]]              normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]   operative Arbeitsmethode
[[DEV_Sprint_NBX-ECM-RUN_S105]]      Auslöser dieses Sprints

---

================================================================================
FLOW ARCHIMATE USABILITY — SPRINT (DEV) | S1.05 | 2026-04-13 | R+MUNI Blueprint
================================================================================
