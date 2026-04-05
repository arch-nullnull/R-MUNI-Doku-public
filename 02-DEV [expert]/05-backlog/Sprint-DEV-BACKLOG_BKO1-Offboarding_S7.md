================================================================================
SPRINT-DEV-BACKLOG – BKO1-Offboarding
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV-BACKLOG_BKO1-Offboarding_S7
Datum           : 2026-03-21
Stage           : S7 – AKTIV
Status          : BACKLOG — nicht gestartet
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN
================================================================================


================================================================================
1. MOTIVATION UND AUSLÖSER
================================================================================

Auslöser-Typ: Strukturbereinigung

Betakunde_01 ist seit Stage 6 faktisch inaktiv. Der vollständige
Kommunikationsweg wurde durchlaufen (persönliches Gespräch → Onboarding-E-Mail
→ Reminder). Adoption auf Kundenseite ist nicht erfolgt.
R+MUNI-seitig eingerichtete Zugänge sind noch aktiv — der dokumentierte
Status entspricht nicht der operativen Realität.

Erkannt in:    Freeze 6 Abschluss — Status Betakunde_01 als PASSIV dokumentiert
Erkannt am:    2026-03-21


================================================================================
2. ZIEL
================================================================================

Ziel:
  Betakunde_01 ist formal offgeboard — alle R+MUNI-seitig eingerichteten
  Zugänge deaktiviert, Status dokumentiert, Lessons Learned erfasst,
  Offboarding als wiederholbares Blueprint-Artefakt nutzbar.

Erfolgskriterium:
  - Alle R+MUNI-seitig eingerichteten Zugänge deaktiviert (nachweisbar)
  - Interner Status auf OFFBOARDED gesetzt mit Datum
  - Lessons Learned in Sprint-DEV-Doku vorhanden (sachlich, blueprint-relevant)
  - BETA_OFFBOARDING_principles_S7 und How2_DEV_S7 freigegeben
  - Sprint-DEV-Doku abgeschlossen und gesynct

Abgrenzung — nicht Teil dieses Sprints:
  - Kein Eingriff in DEV-Umgebung oder Blueprint-Logik
  - Keine externe Kommunikation an Betakunde_01
  - Keine Bewertung der Organisation von Betakunde_01
  - Keine kundenseitige Löschung ohne expliziten Kundenwunsch
  - Kein Onboarding-Redesign (separater Sprint S7-Z2)
  - Kein Einfluss auf ASC-Onboarding — läuft parallel, keine Abhängigkeit


================================================================================
3. FACHLICHER MEHRWERT
================================================================================

Mehrwert für: DEV / Blueprint-Reife / Skalierbarkeit

  - Blueprint-Konsistenz: Status entspricht technischer Realität
  - Exitpoint-Integrität gewahrt: Kunde behält seine Artefakte,
    R+MUNI zieht sich sauber zurück
  - Offboarding als reproduzierbares Artefakt für alle folgenden Beta-Kunden
  - Lessons Learned fließen in Onboarding-Redesign (S7-Z2)
  - GOV-konformer Abschluss: kein stilles Auslaufen

Ohne diesen Sprint:
  R+MUNI-Zugänge bleiben aktiv während der Kunde intern als inaktiv gilt.
  Erkenntnisse gehen verloren. Kein wiederholbares Offboarding-Muster.


================================================================================
4. ABHÄNGIGKEITEN UND VORAUSSETZUNGEN
================================================================================

Voraussetzungen:
  - EUMAXL hat Zugang zu allen R+MUNI-seitig eingerichteten Komponenten
                                                        Status: erfüllt
  - BETA_OFFBOARDING_principles_S7 vorhanden            Status: erfüllt
  - BETA_OFFBOARDING_How2_DEV_S7 vorhanden              Status: erfüllt
  - Onboarding-Dokumentation Betakunde_01 vorhanden     Status: prüfen
  - Interner Entscheid zum Offboarding gefallen          Status: erfüllt

Blockiert durch:
  - Keine Blocker

Ermöglicht danach:
  - [[Sprint-DEV-S7-ASC-Onboarding]]   läuft parallel — keine Abhängigkeit
  - [[BETA_ONBOARDING_S7]]             Onboarding-Redesign baut auf
                                       Lessons Learned aus BKO1 auf

Parallelität:
  ASC-Onboarding (S7-Z2) und dieses Offboarding laufen parallel.
  Keines blockiert das andere.
  Deadline BKO1-Offboarding: 2026-04-01


================================================================================
5. GESCHÄTZTER UMFANG
================================================================================

Komplexität:   Gering
Risiko:        Gering — manueller Prozess, kein Eingriff in Blueprint-Logik

Grobe Einschätzung:
  Tier-Check + Deaktivierung: 15–30 Minuten (abhängig von eingerichteten
  Komponenten — aus Onboarding-Doku bestimmbar)
  Dokumentation: 30–60 Minuten (Status, Lessons Learned, Sprint-DEV-Doku)

Sonderfall-Notiz Betakunde_01:
  Betakunde_01 steht in einem persönlichen / beruflichen Nahverhältnis
  zum Betreiber. Phase 1 (Deaktivierung) wird bilateral abgestimmt.
  Phase 2 und 3 laufen unverändert — gemäß Principles Kapitel 7.1.

Besondere Risiken:
  - Onboarding-Doku Betakunde_01 muss auf Vollständigkeit geprüft werden
    bevor Tier-Check möglich ist


================================================================================
6. PRIORISIERUNG
================================================================================

Priorität:     Hoch
Zeitrahmen:    Bis 2026-04-01

Priorisiert durch:
  - Definierte interne Deadline
  - Saubere Basis für Stage 7 Beta-Neustart
  - Blueprint-Konsistenz als eigenständiges Ziel

Kann verschoben werden wenn:
  - Nicht anwendbar — Deadline 2026-04-01 ist gesetzt


================================================================================
7. GOVERNANCE-CHECK
================================================================================

| Kriterium                          | Status | Anmerkung                           |
|------------------------------------|--------|-------------------------------------|
| Auslöser GOV-konform (GOV 10.3)    | OK     | Strukturbereinigung                 |
| Fachlicher Mehrwert benennbar      | OK     | Siehe Kapitel 3                     |
| Ziel explizit und überprüfbar      | OK     | Siehe Kapitel 2                     |
| Abgrenzung definiert               | OK     | ASC explizit als parallel benannt   |
| Rückkopplungsschutz geprüft        | OK     | Kein Eingriff in Stage 3/4/5/6      |
| Keine implizite GOV-Änderung       | OK     | Keine GOV-Regel berührt             |


================================================================================
8. STATUS UND VERLAUF
================================================================================

2026-03-21  ERSTELLT     EUMAXL + Claude (Pair-Session)
                         Principles und How2 DEV parallel erstellt
                         Tier-basierte Offboarding-Logik eingearbeitet
                         Sonderfall Nahverhältnis in Principles Kap. 7.1
                         und Kapitel 5 dieses Dokuments dokumentiert


================================================================================
BEZÜGE
================================================================================
[[GOV_Global_S6]]                     normative Grundlage
[[FREEZE-6_konsolidiert]]             aktueller Ausgangszustand
[[TOOLBAUKASTEN_principles_S6]]       Tier-Struktur als Grundlage
[[INST_principles_S5]]                Exitpoint-Logik
[[BETA_OFFBOARDING_principles_S7]]    Principles für diesen Sprint
[[BETA_OFFBOARDING_How2_DEV_S7]]      Operative Anleitung
[[STAGE7_ZIELE_S7]]                   S7-Z1 Betakunde_01 Offboarding


================================================================================
Sprint-DEV-BACKLOG_BKO1-Offboarding | S7 | 2026-03-21 | R+MUNI Blueprint
================================================================================
