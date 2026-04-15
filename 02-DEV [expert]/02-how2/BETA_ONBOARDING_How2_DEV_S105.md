================================================================================
BETA_ONBOARDING — HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : BETA_ONBOARDING_How2_DEV_S105
Tag             : #dev #how2 #beta #onboarding #s105
Datum           : 2026-04-14
Stage           : S1.05 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-04-14
Letzte Änderung : 2026-04-14 — Erstellt | DEV_Sprint_BETA-DOKU-MERGE_S105 Z3
Ablageort       : 02-how2\BETA_ONBOARDING_How2_DEV_S105.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[BETA_ONBOARDING_principles_S105]] gelesen und verstanden
- Interner Entscheid zum Onboarding ist gefallen
- Beta-Kunde ist identifiziert und Kontakt hergestellt
- Tier-Entscheidung (Minimal / Core / Addon) ist vorbereitet
- Sprint-DEV-Doku für diesen Onboarding-Vorgang angelegt


MODI — KURZ ERKLÄRT
--------------------------------------------------------------------------------
Das Onboarding läuft in drei Phasen:

  Phase 1 — Tier festlegen und Komponenten einrichten
  Phase 2 — Kommunikation starten und Zugang übergeben
  Phase 3 — Status dokumentieren und Abschluss formalisieren


================================================================================
KURZREFERENZ — ALLE SCHRITTE
================================================================================

── PHASE 1 — TIER FESTLEGEN UND KOMPONENTEN EINRICHTEN ─────────────────────────

SCHRITT 1 — Tier-Entscheidung treffen
  Frage:   Welches Tier passt zur IST-Situation des Beta-Kunden?
  Entscheidung gemeinsam mit Beta-Kunden — kein implizites Default.

  MINIMAL    →  lokale Installation + Basis-Doku, keine R+MUNI-seitigen Zugänge
  CORE       →  Minimal + GitHub Sync wenn vereinbart
  ADDON      →  Core + optionale Addon-Komponenten (z.B. Atlassian)

  Ergebnis:  Tier dokumentiert in Onboarding-Checkliste — Feld: Tier-Level

SCHRITT 2 — Komponenten einrichten
  Aktion:   Ausschließlich die zum gewählten Tier gehörenden Komponenten einrichten.
  Reihenfolge: von innen nach außen — zuerst lokale Basis, dann externe Zugänge.

  MINIMAL:
    - Installations-Anleitung bereitstellen ([[INST_principles_S105]])
    - GitHub Public Repo — Lesezugang kommunizieren (kein Einrichten nötig)

  CORE (zusätzlich zu Minimal):
    - GitHub Sync einrichten wenn vereinbart
    - Zugang zu GitHub Issues / Discussions wenn vereinbart

  ADDON (zusätzlich zu Core):
    - Atlassian NUR wenn explizit vereinbart:
        admin.atlassian.com → Benutzer einladen
        Produktzuweisung: Jira ✅ | Confluence ✅ | Service Collection ❌
        Portal-Zugang: nur über Portal-URL, kein Site-Root-Zugang
    - Weitere Addon-Komponenten nach Vereinbarung

  Prüfen:   Nach jedem Schritt — Zugang funktionsfähig?
  Notieren: Was eingerichtet wurde — für Onboarding-Checkliste Schritt 3

SCHRITT 3 — Onboarding-Checkliste ausfüllen
  Vorlage:  [[BETA_ONBOARDING_Checkliste_Template_S105]] (wenn vorhanden)
            sonst: manuell anlegen mit den Pflichtfeldern:
              Betakunde_XX | Tier-Level | Datum | Eingerichtete Komponenten
              Lokal installierte Tools | Kommunikationsweg | Status
  Ablage:   Sprint-DEV-Doku dieses Onboarding-Vorgangs


── PHASE 2 — KOMMUNIKATION STARTEN UND ZUGANG ÜBERGEBEN ────────────────────────

SCHRITT 4 — Onboarding-E-Mail versenden
  Inhalt:   Willkommen + Überblick was eingerichtet wurde + Zugangsdaten
            + Feedback-Kanal (Portal-URL) + nächste Schritte
  Ton:      Klar, einladend, kein Fachjargon
  Pflicht:  Dieser Schritt ist verpflichtend — kein stilles Einrichten.
            Der Kommunikationsweg (Gespräch → E-Mail → Zugangsdaten) ist
            Grundlage für spätere Offboarding-Entscheidungen.

SCHRITT 5 — Zugang prüfen und bestätigen
  Aktion:   Sicherstellen dass der Beta-Kunde alle eingerichteten Zugänge
            erreichen kann.
  Prüfen:   Rückmeldung vom Kunden einholen — kurze Bestätigung genügt.
  Notieren: Zugang-Bestätigung in Onboarding-Checkliste eintragen.


── PHASE 3 — STATUS DOKUMENTIEREN UND ABSCHLUSS ────────────────────────────────

SCHRITT 6 — Beta-Kunden-Status intern dokumentieren
  Ablage:  Sprint-DEV-Doku — Kapitel Ergebnis
  Eintrag:
    Betakunde_XX   Status: AKTIV — <YYYY-MM-DD>
                   Tier-Level: <MINIMAL / CORE / ADDON>
                   Eingerichtet: <Liste der eingerichteten Komponenten>
                   Kommunikationsweg abgeschlossen: JA
                   Onboarding-Checkliste: vorhanden — <Ablageort>

SCHRITT 7 — Sprint-DEV-Doku abschließen
  Enthält:  Tier-Entscheidung, eingerichtete Komponenten,
            Kommunikationsweg, Status, GOV-Check
  Aktion:   Status auf ABGESCHLOSSEN setzen
  Sync:     GitHub-Push wenn Sprint abgeschlossen

SCHRITT 8 — GOV-Check
  DEV-Umgebung berührt?              → NEIN erwartet
  Blueprint-Logik verändert?         → NEIN erwartet
  Atlassian ohne Addon-Entscheidung? → NEIN — wenn JA: sofort korrigieren
  Onboarding-Checkliste vorhanden?   → JA erwartet
  Kommunikationsweg abgeschlossen?   → JA erwartet
  Status-Dokumentation komplett?     → JA erwartet


================================================================================
FEHLERBILDER
================================================================================

Fehler: Atlassian wurde ohne explizite Addon-Entscheidung eingerichtet
  Ursache: Altes Reflexverhalten aus Stage 4 (Atlassian war damals Default)
  Lösung:  Tier-Entscheidung nachholen, Onboarding-Checkliste korrigieren,
           bei Bedarf Atlassian-Zugang wieder deaktivieren

Fehler: Onboarding-Checkliste fehlt
  Ursache: Onboarding ohne begleitende Dokumentation durchgeführt
  Lösung:  Nachträglich erstellen — GOV 7.8 gilt auch rückwirkend

Fehler: Kein Kommunikationsstart durchgeführt
  Ursache: Zugänge still eingerichtet ohne E-Mail
  Lösung:  E-Mail nachsenden — Schritt 4 nachholen, Datum notieren


================================================================================
ENTSCHEIDUNGSHILFE
================================================================================

Ich will...                                           Richtiger Schritt
----------------------------------------------------- ---------------------------
Tier festlegen                                        SCHRITT 1
Atlassian einrichten                                  SCHRITT 2 — nur bei ADDON
Onboarding-Checkliste anlegen                         SCHRITT 3
Kommunikation starten                                 SCHRITT 4
Zugang bestätigen lassen                              SCHRITT 5
Status intern dokumentieren                           SCHRITT 6
Onboarding formal abschließen                         SCHRITT 7–8
Prüfen ob DEV-Umgebung berührt wurde                  SCHRITT 8 GOV-Check


================================================================================
BEZÜGE
================================================================================
[[BETA_ONBOARDING_principles_S105]]              Designentscheidungen und Hintergrund
[[BETA_OFFBOARDING_How2_DEV_S101]]               Spiegelprozess — Offboarding
[[BETA_ONBOARDING_Atlassian_Zugriffsmodell_S105]] deprecated — Atlassian-Detail Stage 4
[[Global_GOV_DEV_S102]]                          normative Grundlage
[[INST_principles_S105]]                         Installations-Grundlage Minimal-Tier
[[FREEZE_1_04]]                                  Atlassian-Addon-Nachweis


================================================================================
BETA_ONBOARDING_How2_DEV | S1.05 | 2026-04-14 | R+MUNI Blueprint
================================================================================
