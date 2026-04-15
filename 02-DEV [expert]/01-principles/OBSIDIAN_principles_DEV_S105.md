================================================================================
OBSIDIAN – Obsidian im Blueprint nutzen — PRINCIPLES (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : OBSIDIAN_principles_DEV_S105
Tag             : #dev #principles #obsidian #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Letzte Änderung : 2026-04-14 — S105-Update | Umbenennung OBS → OBSIDIAN | DEV-Variante klargestellt
Ablageort       : R+MUNI Doku-public\01-principles\OBSIDIAN_principles_DEV_S105.md
================================================================================

---
title: "OBSIDIAN – Obsidian im Blueprint nutzen"
stage: S105
status: "AKTIV"
typ: "Prinzipien"
datum: "2026-04-14"
autor: EUMAXL
tags: [rmuni, blueprint, dev, obsidian, principles, s105]
---


ZWECK DIESES DOKUMENTS
--------------------------------------------------------------------------------
Zielgruppe: DEV — interne Arbeitsgrundlage.

Dieses Dokument erklärt:
  - Was Obsidian ist und wozu es im R+MUNI Blueprint dient
  - Was DEV davon hat
  - Was vor dem Start zu wissen ist
  - Was dieses Dokument nicht leistet

Hinweis Kürzel:
  Diese Reihe trägt das Kürzel OBSIDIAN_ — nicht OBS_.
  OBS ist im R+MUNI-Betriebskontext für OBS Studio reserviert.

Hinweis Variante:
  Dieses Dokument ist DEV. Eine R+MUNI-Variante existiert noch nicht
  (geplant ab Beta 2.0 / Phase 2).
  Dokumente mit _Associate_ im Namen aus Beta 1.0 gelten als technische
  Schuld — werden im Cleaning Run S106+ bereinigt.


================================================================================
1. WAS IST OBSIDIAN IM BLUEPRINT-KONTEXT?
================================================================================

Obsidian ist ein kostenloses Notiz- und Dokumentationswerkzeug das Textdateien
(.md) als Wissensnetz darstellt. Im R+MUNI Blueprint dient Obsidian als
optionale Visualisierungsebene — es zeigt wie Dokumente miteinander verknüpft
sind und hilft beim Navigieren durch die Dokumentation.

Kurz gesagt:
  Obsidian macht aus den Blueprint-Dokumenten eine navigierbare Wissenslandkarte.

Warum das relevant ist:
  Wer viele Dokumente hat verliert schnell den Überblick. Obsidian zeigt
  als Graph welche Dokumente zusammenhängen — ohne dass alles auswendig
  bekannt sein muss.


================================================================================
2. WAS DEV DAVON HAT
================================================================================

Obsidian ermöglicht:
  - Dokumentverknüpfungen visuell als Graph zu sehen
  - Schnell zwischen verwandten Dokumenten zu navigieren
  - Templates gezielt zu finden (tag:#template Filter)
  - Den Blueprint-Stand auf einen Blick zu erfassen

Was es nicht leistet:
  - Obsidian verändert keine Blueprint-Dateien — es liest nur
  - Obsidian ist kein Pflichtbestandteil — R+MUNI funktioniert ohne es


================================================================================
3. GRUNDPRINZIPIEN
================================================================================

3.1 Obsidian ist Lesewerkzeug — kein Eingriff
-----------------------------------------------
Obsidian öffnet die vorhandenen .md-Dateien und zeigt ihre Verknüpfungen.
Es verändert keine Dateien und greift nicht in die Blueprint-Logik ein.

Konkret bedeutet das:
  Obsidian kann jederzeit geöffnet und geschlossen werden — nichts geht
  verloren, nichts wird verändert.


3.2 Optional aber empfohlen
-----------------------------
Obsidian ist nicht zwingend. Wer es nutzt gewinnt Orientierung.
Wer es nicht nutzt verliert keine Funktionalität.


3.3 Lokale Installation — keine Cloud
---------------------------------------
Obsidian läuft lokal. Dokumente bleiben wo sie sind.
Keine Registrierung, keine Cloud, kein Abo erforderlich.


================================================================================
4. VORAUSSETZUNGEN
================================================================================

  - R+MUNI ist installiert und der erste Funktionstest war grün
  - [[Global_GOV_DEV_S102]] gelesen
  - Obsidian installiert (obsidian.md — kostenlos, keine Registrierung)
  - Vault zeigt auf Parent-Ordner aller R+MUNI Ordner


================================================================================
5. ABGRENZUNG UND GRENZEN
================================================================================

Was hier geregelt ist:
  - Obsidian als Visualisierungs- und Navigationshilfe
  - Grundprinzipien der Nutzung — DEV-Sicht

Was woanders geregelt ist:
  - Technische Konfiguration, SVG-Einbettung, Frontmatter-Schema
    → [[OBSIDIAN_How2_DEV_S105]]
  - Dokumenttypen und Template-Tagging
    → [[TMP_principles_S105]]
  - Namenskonventionen und Tiering
    → [[naming_and_structure_S104]]


================================================================================
BEZÜGE
================================================================================

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[FREEZE_1_04]]                            aktueller Ausgangszustand
[[STAGE105_ZIELE_S105]]                    Z5 — Cleaning Run, Carry-over
[[OBSIDIAN_How2_DEV_S105]]                 technische Konfiguration
[[TMP_principles_S105]]                    Dokumenttypen-Referenz
[[naming_and_structure_S104]]              Namenskonventionen und Tiering
[[DEV_Sprint_OBS-RENAME-TAGGING_S105]]     Sprint-Doku Umbenennung + Tagging


================================================================================
OBSIDIAN_principles | DEV | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
