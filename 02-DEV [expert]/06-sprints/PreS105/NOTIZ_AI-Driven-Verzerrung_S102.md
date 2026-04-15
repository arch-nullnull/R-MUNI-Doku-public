---
title: "NOTIZ — AI Driven Methode: Verzerrung durch KI-Tool-Abhängigkeit"
stage: S102
status: Notiz
typ: Konzeptnotiz
datum: 2026-04-07
autor: EUMAXL
tags: [aidriven, methode, verzerrung, kitool, risiko, s102, notiz]
---

# NOTIZ — AI Driven Methode: Verzerrung durch KI-Tool-Abhängigkeit
> Konzeptnotiz | Praxis + Struktur | 2026-04-07

---

## Kontext

Stage 1.02 musste erstmalig als PARTIAL FREEZE abgeschlossen werden.
Ein wesentlicher Faktor: Das KI-Tool selbst hat die Entwicklung
aktiv behindert — nicht durch Fehler des Entwicklers, sondern durch
externes Verhalten des Werkzeugs.

Diese Notiz dokumentiert was konkret passiert ist und was das
strukturell für die AI Driven Methode bedeutet.

---

## 1. Praxis-Erfahrung — Was ist in Stage 1.02 passiert

### 1.1 Drift durch Komplexität (CARD-Reihen-Umbau)

Auslöser: Umbau der CARD-Dokumentenreihe.
Was passiert: Das KI-Tool hat bei zunehmender Komplexität begonnen
  zu driften — Annahmen statt Rückfragen, Scope-Expansion ohne Freigabe,
  Neugenerierung statt chirurgischer Eingriffe.
Konsequenz: Konsistenz zwischen GOV, AI Driven Methode und Skill
  ist verloren gegangen. Produktives Arbeiten war nicht mehr möglich.
  Zwei Anlaufversuche gescheitert. Entscheidung: Total Reset.

Konkrete Symptome:
  - Naming-Dokument nicht korrekt geliefert — EUMAXL hat es selbst fertiggestellt
  - KI-Tool hat auf Punkt-Korrekturen mit Komplett-Neugenerierungen reagiert
  - Widersprüche zwischen Dokumenten nicht aktiv gemeldet — stillschweigend übergangen
  - Zu früher Output: Konzeptdokumente entstanden vor vollständigem Dialog
  - Template-Pflicht verletzt: Konzeptdokument nicht nach Sprint-Template erstellt
  - Scope-Expansion bei GOV-Review ohne Rückfrage

### 1.2 Verhaltensänderung durch KI-Tool-Update

Auslöser: Hersteller-seitiges Update des KI-Tools (extern, nicht durch EUMAXL).
Was passiert: Das Nutzungsverhalten hat sich nach dem Update massiv verändert.
  Kalibrierung die über ~400h Entwicklung aufgebaut worden war:
  funktional auf Null zurückgesetzt.
  Das Tool verhielt sich strukturell anders als zuvor — nicht graduell,
  sondern als Sprung.
Konsequenz: Vollständige Rekalibrierung notwendig.
  Laufende Entwicklungsarbeit unterbrochen.
  Ressourcen für produktive Arbeit (ASC, CARD, Public Push) nicht mehr verfügbar.

### 1.3 Kostenproblem

Was passiert: Die Verhaltensänderung hat die Kostenstruktur verändert.
  Geschätzte Kosten pro Antwort nach Update: 0,50€ – 1,50€.
  Für kontinuierlichen DEV-Betrieb nicht tragbar.
Konsequenz: KI-Ressourcen aktiv gedrosselt.
  ASC-Entwicklung pausiert.
  CARD-Entwicklung pausiert.
  Nur kritische Stabilisierungsarbeit durchgeführt.

---

## 2. Strukturelle Erkenntnis — Was das für die Methode bedeutet

### 2.1 Die Verzerrung

Die AI Driven Methode setzt voraus:
  "Der Entwickler denkt das System. Die KI schreibt es auf."

Das stimmt — solange das KI-Tool stabil ist.

Was in Stage 1.02 sichtbar geworden ist:
  Das KI-Tool ist nicht nur Werkzeug — es ist aktiver Faktor.
  Sein Verhalten beeinflusst Entwicklungsentscheidungen, Prioritäten
  und Kapazitäten — auch dann wenn es das nicht sollte.

Konkret:
  - Entscheidungen über Sprint-Inhalte wurden durch Tool-Verfügbarkeit beeinflusst
  - Stage-Ziele wurden nicht wegen inhaltlicher Entscheidung verschoben,
    sondern wegen Tool-Verhalten
  - Methoden-Investitionen (Kalibrierung, Kontext-Aufbau) können durch
    externe Hersteller-Entscheidungen entwertet werden

Das ist keine Methodenschwäche — es ist eine strukturelle Abhängigkeit
die bisher nicht explizit in der Methode adressiert war.

### 2.2 Risikotypen

| Risiko | Beschreibung | Eingetreten S102 |
|--------|-------------|------------------|
| Drift-Risiko | KI akkumuliert Annahmen, bis Konsistenz verloren geht | JA |
| Update-Risiko | Hersteller ändert Verhalten ohne Vorlauf | JA |
| Kosten-Risiko | Kostenstruktur verändert sich extern und unvorhersehbar | JA |
| Tool-Lock-Risiko | Methode/Dokumentation so eng mit Tool verwoben, dass Wechsel aufwändig ist | TEILWEISE |
| Kalibrierungs-Entwertung | Aufgebautes Kontext-Wissen wird durch Update nutzlos | JA |

### 2.3 Was die Methode geleistet hat — und wo die Grenze ist

Geleistet:
  - Drift erkannt (Meldepflicht hat funktioniert)
  - Reset-Entscheidung war möglich (EUMAXL hat Kontrolle behalten)
  - Tool-Lock-Schutz war vorbereitet (S10nc-Reihe realisierbar)
  - Zwei-Welten-Prinzip hat verhindert dass öffentliche Inhalte betroffen waren

Grenze:
  - Die Methode schützt nicht vor externen Tool-Entscheidungen des Herstellers
  - Kalibrierungs-Investitionen sind nicht portierbar und nicht absicherbar
  - Kostenentwicklung des Tools ist außerhalb des Methoden-Einflusses

### 2.4 Was zu tun ist — Erkenntnisse für die Methode

Diese Punkte sind keine dringenden Sprints — sie sind Erkenntnisse
die in die Methode einfließen sollten wenn der Zeitpunkt passt.

A) Kalibrierungsstand dokumentieren, nicht nur voraussetzen
   Aktuell: Kalibrierung lebt im Kopf und in der Session.
   Besser: Expliziter Kalibrierungsstand als dokumentiertes Artefakt.
   Beispiel: "Wie verhält sich das KI-Tool aktuell in welchen Situationen?"
   Zweck: Bei Update-bedingtem Sprung sofort erkennbar + rücksetzbar.

B) Tool-Evaluation als geplanter Schritt, nicht als Notfallreaktion
   Aktuell: Evaluation wurde durch Krise ausgelöst.
   Besser: Periodische Tool-Evaluation als fester Punkt — z.B. je Stage.
   Zweck: Verhaltensänderungen frühzeitig erkennen, nicht erst wenn
   der Betrieb blockiert ist.

C) Kosten als Steuerungsgröße explizit machen
   Aktuell: Kosten sind implizit berücksichtigt aber nicht dokumentiert.
   Besser: KI-Tool-Kosten als explizite Rahmenbedingung in Methodik.
   Grenzwert: Was ist tragbar je Sprint / Stage?
   Zweck: Ressourcenplanung, nicht Reaktion auf Eskalation.

D) Kalibrierungs-Verlust als bekanntes Risiko behandeln
   Aktuell: 400h Kontext-Aufbau — ohne Absicherung.
   Besser: Kontext-kritische Erkenntnisse in Projektordner sichern,
   nicht als implizites Tool-Wissen behandeln.
   Zweck: Wiederherstellbar wenn Tool wechselt oder resettet.

---

## 3. Abgrenzung

Was diese Notiz nicht sagt:
  - Das die AI Driven Methode falsch ist — sie ist richtig
  - Das das KI-Tool unbrauchbar ist — Evaluation läuft noch (Deadline 09.04.)
  - Das Kalibrierung sinnlos ist — sie ist wertvoll, aber absicherungsbedürftig

Was diese Notiz sagt:
  Das KI-Tool ist kein passives Werkzeug.
  Sein Verhalten ist ein Faktor — und dieser Faktor muss
  in der Methode expliziter adressiert werden als bisher.

---

## 4. Offene Punkte

| Thema | Status | Nächste Aktion |
|-------|--------|----------------|
| KI-Tool-Evaluation | offen — Deadline 09.04.2026 | EUMAXL entscheidet + dokumentiert |
| Erkenntnisse A–D in AI Driven einarbeiten | offen | Eigener Sprint wenn Zeitpunkt passt |
| Kalibrierungsstand-Format definieren | Idee | Konzeptnotiz → Sprint wenn relevant |

---

## Bezug

- [[FREEZE_1_02]]                         Stage-Abschluss + Partial Freeze Begründung
- [[DEV_Sprint_TotalReset_S102]]          Konkrete Reset-Session
- [[DEV_Sprint_Rekalibrierung_RestartII_S102]]  Konkretes KI-Fehlverhalten dokumentiert
- [[DEV_Sprint_Claude-Exit_S10nc]]        Tool-Unabhängigkeit strukturell hergestellt
- [[AI_DRIVEN_DEV_METHODE_DEV_S10nc]]    Methodik-Basis

---

*Konzeptnotiz | Kein Sprint-Auftrag | Erkenntnis sichern | 2026-04-07*
