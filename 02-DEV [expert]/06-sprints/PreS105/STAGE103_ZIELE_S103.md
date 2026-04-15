================================================================================
STAGE 103 – Phase 1.03 | Release Finalisierung & KI-Tool-Kalibrierung
Normative Definition und Geltungsbereich
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : STAGE103_ZIELE_S103
Tag             : #stage #ziele #s103 #produktiv #phase1 #release #review
Datum           : 2026-04-07
Stage           : S103 — AKTIV
Gültig für      : Phase 1.03 (innerhalb Phase 1.xx)
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt durch  : EUMAXL (mit KI-Input)
Basis           : FREEZE_1.02.md | STAGE102_ZIELE_S102.md | praktische Erfahrung Stage 1.02
================================================================================


================================================================================
1. ZWECK VON STAGE 103
================================================================================

Stage 103 dient der Fertigstellung des Public Release und der Synchronisierung
der in S102 entstandenen Emergency-Kalibrierungen mit dem KI-Tool-Nutzungsverhalten.

Im Fokus stehen:
  - Release (S103) finalisieren und public deployen
  - NBX Erweiterung (IP-Merge Script) und Cleanup
  - Beta-Feedback einarbeiten (Bugs + Features nach Bedarf und Dringlichkeit)
  - KI-Tool Kalibrierungen aus S102 synchronisieren (AI Driven Update)
  - Internen DEV Backlog prüfen

Stage 103 ist pragmatisch: nicht "besser machen" sondern "fertigmachen".


================================================================================
2. AUSGANGSBASIS & KONTEXT
================================================================================

Stage 103 baut auf dem abgeschlossenen Stage-102-Zustand auf (PARTIAL FREEZE).

Was erreicht wurde in S102:
  ✓ GOV + AI Driven Methode konsolidiert (S10nc-Reihe inaktiv, Exit-Szenario)
  ✓ NBX läuft funktional (16+ Objekte)
  ✓ BKO3 (Landwirtschaft) als erster echter CARD-Betakunde ongeboardet
  ✓ S10nc-Neutralisierung als Notfall-Triage durchgeführt (nicht strategisch)

Was NICHT erreicht wurde in S102:
  ✗ Release (S103) public deployment
  ✗ MUNIDELL SVG Header korrigiert
  ✗ Install.txt optimiert
  ✗ KI-Tool Emergency-Kalibrierungen dokumentiert
  ✗ Teamstruktur geklärt (Termine ausstehend)

Bezug auf vorherigen Freeze:
  [[FREEZE_1.02]]             Ausgangszustand für Stage 103 (PARTIAL FREEZE)
  [[STAGE102_ZIELE_S102]]     Was geplant war vs. was erreicht wurde


================================================================================
3. CHARAKTER VON STAGE 103
================================================================================

Stage 103 ist nicht "Completion" sondern "Realitäts-Release".

  - Release wird fertig, weil Qualität geliefert werden muss
  - NBX wird erweitert (IP-Merge) und bereinigt — kein Neubau
  - Beta-Feedback wird nach Dringlichkeit und Bedarf eingearbeitet
  - KI-Tool Kalibrierungen werden kontrolliert synchronisiert
  - Pragmatismus über Perfektion

Stage 103 dokumentiert nicht nur Erfolge — auch Lernpunkte aus Scheitern.


================================================================================
4. ZIELE VON STAGE 103
================================================================================

S103-Z1: RELEASE FINALISIEREN UND PUBLIC DEPLOYEN
----------------------------------------------------------

SUBSTANZ:
  • Install.txt — bereits korrigiert, finaler Check am Stage-Ende
  • README — Release-Info einbauen
  • HLP mkdir — am Ende prüfen abhängig von Release-Paket-Struktur
  • MUNIDELL SVG — Header auf korrekte Namen korrigieren (siehe Z4)
  • GitHub Deploy — manuell durch EUMAXL

DELIVERABLES:
  ✓ Install.txt finaler Check (Stage-Ende)
  ✓ README mit Release-Info
  ✓ HLP mkdir geprüft / bereinigt
  ✓ GitHub Release manuell deployed

SUCCESS CRITERIA:
  • Install.txt aus CARD-Benutzerperspektive lesbar
  • README nennt Release (S103) klar
  • GitHub Release öffentlich sichtbar und downloadbar

ABHÄNGIGKEITEN:
  • Keine blockierenden Abhängigkeiten


S103-Z2: NBX ERWEITERUNG & CLEANUP
----------------------------------------------------------

SUBSTANZ:
  • NBX läuft funktional — kein Neubau
  • Fehler S102: KI hat NBX03–04 + Config verändert → Logik kaputt
    Restore hat alten Stand zurückgebracht aber in unschönem Zustand
  • Neues Script NBX0x — IP-Merge zwischen NBX03 und NBX04
  • Reihe bereinigen / schön machen
  • Arbeitsregel: Änderungen nur chirurgisch, ein Script auf einmal,
    keine Config-Änderungen ohne expliziten Entscheid

DELIVERABLES:
  ✓ NBX0x (IP-Merge Script) entwickelt und eingebunden
  ✓ Reihe NBX00–NBX0x bereinigt
  ✓ nbx_config.txt + nbx_raw.json in .gitignore

SUCCESS CRITERIA:
  • NBX läuft sauber ohne Warnings
  • IP-Merge funktional zwischen NBX03 und NBX04
  • Qualitätskontrolle über properties_nbx.csv bestanden

ABHÄNGIGKEITEN:
  • Keine blockierenden Abhängigkeiten


S103-Z3: BETA-FEEDBACK VERARBEITEN
----------------------------------------------------------

SUBSTANZ:
  • Laufende Bug-Reports aus Beta-Umgebungen einarbeiten
  • Feature Requests aus Beta einarbeiten
  • Priorisierung nach Bedarf und Dringlichkeit

DELIVERABLES:
  ✓ Bugs eingearbeitet (nach Dringlichkeit)
  ✓ Features eingearbeitet (nach Bedarf)

SUCCESS CRITERIA:
  • Alle dringlichen Bugs adressiert
  • Feature Requests bewertet und dokumentiert

ABHÄNGIGKEITEN:
  • Eingehende Meldungen aus Beta-Umgebungen


S103-Z4: MUNIDELL SVG HEADER KORRIGIEREN
----------------------------------------------------------

SUBSTANZ:
  • MUNIDELL SVG läuft — nur Header auf korrekte Namen korrigieren

DELIVERABLES:
  ✓ SVG Header mit korrekten Namen

SUCCESS CRITERIA:
  • Header zeigt aktuelle korrekte Namen
  • Ready für README public

ABHÄNGIGKEITEN:
  • Gehört zu Z1 (Release)


S103-Z5: KI-TOOL KALIBRIERUNG SYNCHRONISIEREN
----------------------------------------------------------

SUBSTANZ:
  • Emergency-Kalibrierungen aus S102 in AI Driven einarbeiten
  • Kontrolliertes Review am Stage-Ende
  • AI Driven Update als Vorbereitung für S104

DELIVERABLES:
  ✓ AI Driven DEV mit S102-Kalibrierungen aktualisiert
  ✓ AI Driven Update für S104 bereit

SUCCESS CRITERIA:
  • Kalibrierungen aus S102 vollständig synchronisiert
  • AI Driven ist Basis für S104

ABHÄNGIGKEITEN:
  • Kein blockierender Abhängigkeitspfad — Review am Stage-Ende


S103-Z6: INTERNER DEV BACKLOG REVIEW
----------------------------------------------------------

SUBSTANZ:
  • Public Backlog ist immer aufgeräumt
  • Interner DEV Backlog wird durch EUMAXL geprüft
  • Status-Meldung im Chat reicht als Deliverable

DELIVERABLES:
  ✓ Status-Meldung: Interner DEV Backlog geprüft

SUCCESS CRITERIA:
  • EUMAXL hat internen Backlog gesichtet und Status gemeldet

ABHÄNGIGKEITEN:
  • Keine


S103-Z7: KI-NEUTRALISIERUNG (LAUFEND)
----------------------------------------------------------

SUBSTANZ:
  • Alle S103 Dokumente mit Außenwirkung: keine Claude-Nennung
  • AI Driven DEV intern: Claude-Nennung erlaubt für Kalibrierung (Ausnahme explizit)
  • Gilt laufend — kein eigener Sprint

DELIVERABLES:
  ✓ Alle neuen Dokumente mit Außenwirkung ohne Claude-Nennung

SUCCESS CRITERIA:
  • Außenwirkung: KI-agnostisch
  • Intern AI Driven: Kalibrierung mit Claude-Nennung möglich

ABHÄNGIGKEITEN:
  • Keine (parallel)


================================================================================
5. RÜCKKOPPLUNGSSCHUTZ & GOVERNANCE
================================================================================

  - Stage-3 bis Stage-102-Artefakte: read-only ohne Ausnahme
  - Bugfixes erfordern explizite Freigabe und Dokumentation
  - Keine Logikänderung ohne expliziten Entscheid durch EUMAXL
  - S10nc bleibt inaktiv (nicht gepflegt, nur bei KI-Tool-Wechsel aktiviert)
  - GOV bleibt bei S102-Stand für aktive Nutzung


================================================================================
6. DOKUMENTATION IN STAGE 103
================================================================================

  - Sprint-Bezeichnung: Sprint-DEV-S103-<Kürzel> (falls Sprints nötig)
  - Sprint-Doku für Entwicklungsaktivitäten (GOV 10.8)
  - Alle Outputs als .md im Chat (nicht gepusht)


================================================================================
7. TIMING & KRITISCHER PFAD
================================================================================

KRITISCHER PFAD (seriell):
  1. Z1 (Release): Install.txt Check + README + GitHub Deploy
  2. Z2 (NBX): IP-Merge Script + Cleanup
  3. Z3 (Feedback): laufend nach Dringlichkeit
  4. Z4 (MUNIDELL): Teil von Z1

NICHT-KRITISCHER PFAD (parallel):
  • Z5 (KI-Kalibrierung): Review am Stage-Ende
  • Z6 (Backlog): Status-Meldung EUMAXL
  • Z7 (Neutralisierung): laufend


================================================================================
8. ERFOLGS-KRITERIEN FÜR S103-ABSCHLUSS
================================================================================

STAGE 103 IST ABGESCHLOSSEN WENN:

✓ Z1 Release public deployed
  • Install.txt finaler Check
  • README aktualisiert
  • GitHub Release sichtbar

✓ Z2 NBX IP-Merge Script funktional + Reihe bereinigt

✓ Z3 Beta-Feedback nach Dringlichkeit eingearbeitet

✓ Z4 MUNIDELL SVG Header korrigiert

✓ Z5 AI Driven mit S102-Kalibrierungen synchronisiert

✓ Z6 Interner DEV Backlog Status-Meldung erfolgt

FREEZE 1.03 kann geschrieben werden wenn alle ✓ erfüllt.


================================================================================
9. ABGRENZUNG ZU SPÄTEREN STAGES
================================================================================

Nicht Teil von Stage 103 sind:
  - Beta 2.0 Vorbereitung (gehört in S104+)
  - Weitere KI-Tool-Evaluationen (Entscheidung S104)
  - Expert-Dokumentation (geklärt: kein eigenes Artefakt)
  - Public Repo History-Reset (optional, nicht dringend)

Diese Themen sind Backlog für S104+.


================================================================================
10. FORMALE FESTSTELLUNG
================================================================================

Mit dieser Definition ist Stage 103:
  - logisch eröffnet
  - klar abgegrenzt von Stage 102 (Partial) und Stage 104+ (Beta 2.0)
  - rückkopplungssicher
  - GOV-konform
  - auf Release-Fertigstellung und KI-Kalibrierung ausgerichtet

Stage 3 bis 102 bleiben fixiert und geschützt.
Stage 103 darf pragmatisch arbeiten — fertig ist besser als perfekt.


================================================================================
BEZÜGE
================================================================================

[[Global_GOV_DEV_S102]]                       normative Grundlage
[[FREEZE_1.02]]                               Ausgangszustand — PARTIAL FREEZE
[[STAGE102_ZIELE_S102]]                       Was geplant war vs. erreicht
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]            Methodik-Basis
[[STAGE100_ZIELE_S100]]                       Phasen-Rahmen Phase 1.xx


================================================================================
STAGE 103 – Phase 1.03 | Release Finalisierung & KI-Tool-Kalibrierung
ZIELE DEFINIERT | 2026-04-07
R+MUNI Blueprint | Erstellt durch: EUMAXL (mit KI-Input)
================================================================================
