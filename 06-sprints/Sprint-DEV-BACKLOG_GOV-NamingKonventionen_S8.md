================================================================================
SPRINT-DEV-BACKLOG – GOV Naming Konventionen
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV-BACKLOG_GOV-NamingKonventionen_S8
Datum           : 2026-03-26
Stage           : S7 – AKTIV
Status          : BACKLOG — nicht gestartet
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN — noch kein Ticket
================================================================================


================================================================================
1. MOTIVATION UND AUSLÖSER
================================================================================

Auslöser-Typ: Strukturbereinigung / Entwicklerwunsch

Im Zuge der EA Modell Review Session (S7, 2026-03-26) wurde erkannt dass
die Naming Konventionen für Properties und Files bisher nur implizit bekannt
waren und nie formal in der GOV dokumentiert wurden. Die Konventionen
existieren und werden konsistent angewendet — aber nur im Kopf des Betreibers.

Konkreter Anlass: Property AccessLevel wurde in der Session erstmals bewusst
als CamelCase definiert und von File Naming (Snake_Case) abgegrenzt. Ohne
GOV-Dokumentation besteht Drift-Risiko bei neuen Properties und Files sowie
bei künftigen DEV-Mitstreitern.

Erkannt in:    EA Modell Review Session S7 — Pair-Session EUMAXL + Claude
Erkannt am:    2026-03-26


================================================================================
2. ZIEL
================================================================================

Ziel:
  Die Naming Konventionen für Properties (CamelCase) und Files
  (Snake_Case mit Präfix-Schema) sind vollständig in GOV_Global dokumentiert
  und mit Beispielen belegt.

Erfolgskriterium:
  Ein neuer DEV-Mitstreiter kann ohne Rückfrage neue Properties und Files
  korrekt benennen — allein auf Basis der GOV.

Abgrenzung — nicht Teil dieses Sprints:
  - Keine Umbenennung bestehender Properties oder Files
  - Keine Änderung an Script-Logik oder Mapping-Files
  - Keine Überarbeitung anderer GOV-Kapitel
  - Kein Eingriff in Stage 3/4/5/6 Artefakte


================================================================================
3. FACHLICHER MEHRWERT
================================================================================

Mehrwert für: DEV · System-Stabilität · Skalierbarkeit

  - Naming ist explizit — kein implizites Betreiber-Wissen mehr
  - Neue Properties wie AccessLevel sind sofort korrekt benennbar
  - DEV-Mitstreiter können ohne Rückfrage arbeiten
  - Maschinenlesbarkeit wird durch konsistente Konvention gesichert
  - Grundlage für spätere Tool-Integration (ATL Flow · ECM · CSV)

Ohne diesen Sprint:
  Naming bleibt im Kopf des Betreibers. Bei wachsender DEV-Mannschaft
  oder nach längerer Pause entstehen inkonsistente Properties die
  nachträglich schwer zu bereinigen sind.


================================================================================
4. ABHÄNGIGKEITEN UND VORAUSSETZUNGEN
================================================================================

Voraussetzungen:
  - EA Modell Review abgeschlossen (Motivation Layer)    Status: in Arbeit
  - AccessLevel Property im Modell definiert             Status: offen
  - GOV_Global_S6 verfügbar                              Status: erfüllt

Blockiert durch:
  - Keine Blocker — kann unabhängig gestartet werden

Ermöglicht danach:
  - [[Sprint-DEV-BACKLOG_Zwei-Welten-Umsetzung_S7]]
    Zwei-Welten-Trennung braucht konsistente Property-Konvention
  - Onboarding neuer DEV-Mitstreiter ohne Naming-Rückfragen


================================================================================
5. GESCHÄTZTER UMFANG
================================================================================

Komplexität:   Gering
Risiko:        Gering — keine Script-Logik betroffen

Grobe Einschätzung:
  Ein fokussierter GOV-Erweiterungsrun. Neues Kapitel in GOV_Global
  für Naming Konventionen. Betroffene Bereiche: GOV_Global · ggf.
  SCRIPT-BAUKASTEN wenn Script-seitige Konventionen tangiert werden.

  Kerninhalt des neuen GOV-Kapitels:

  Property Naming — CamelCase
    Regel:     Kein Leerzeichen · Kein Underscore · Kein Bindestrich
    Beispiele: AccessLevel · 3PartyID · SourceModel
    Werte:     GROSSBUCHSTABEN wenn kontrolliertes Vokabular

  File Naming — Snake_Case mit Präfix-Schema
    Regel:     ABC00-ich_bin_der_name_S7
               Präfix     = Typ-Kürzel + laufende Nummer
               Name       = Snake_Case · beschreibend
               Stage      = _S<N> als Suffix
    Beispiele: Sprint-DEV-BACKLOG_GOV-NamingKonventionen_S8.md
               CSV00-root.resolved.txt
               MUNI EA.archimate

  Denglish als bewusste Entscheidung dokumentieren:
    R+MUNI verwendet konsequent Denglish — Englische Begriffe
    wo etabliert (AccessLevel · Stage · Freeze) · Deutsche Begriffe
    wo sinnvoller (Grenzbereich · Betreiber). Mischen ist erlaubt
    wenn konsistent im jeweiligen Kontext.

Besondere Risiken:
  - Keine besonderen Risiken


================================================================================
6. PRIORISIERUNG
================================================================================

Priorität:     Mittel
Zeitrahmen:    Stage 8 — nach Abschluss EA Modell Review S7

Priorisiert durch:
  Entwicklerwunsch — erkannt in S7 Session.
  Kein akuter Blocker aber wachsendes Drift-Risiko bei
  zunehmendem DEV-Betrieb und neuen Mitstreitern.

Kann verschoben werden wenn:
  Kein neuer DEV-Mitstreiter aktiv wird und Betreiber
  alleiniger Nutzer bleibt. Dann weiter als implizites Wissen
  tragbar — aber nicht empfohlen.


================================================================================
7. GOVERNANCE-CHECK
================================================================================

| Kriterium                          | Status  | Anmerkung                        |
|------------------------------------|---------|----------------------------------|
| Auslöser GOV-konform (GOV 10.3)    | OK      | Strukturbereinigung              |
| Fachlicher Mehrwert benennbar      | OK      | Siehe Kapitel 3                  |
| Ziel explizit und überprüfbar      | OK      | Siehe Kapitel 2                  |
| Abgrenzung definiert               | OK      | Keine Umbenennung bestehender    |
| Rückkopplungsschutz geprüft        | OK      | Stage 3/4/5/6 unberührt          |
| Keine implizite GOV-Änderung       | OK      | Additiv — kein Eingriff          |


================================================================================
8. STATUS UND VERLAUF
================================================================================

2026-03-26  ERSTELLT    EUMAXL + Claude — Pair-Session EA Modell Review S7


================================================================================
NOTIZ — ERKENNTNISSE AUS DER SESSION (2026-03-26)
================================================================================

Folgende Konventionen wurden in der Session explizit besprochen
und sind Grundlage dieses Backlogs:

Property Naming:
  AccessLevel    →  CamelCase · korrekt
  3PartyID       →  CamelCase · bestehend · Referenz
  AccessLevel-Werte: INTERN · PUBLIC · GRENZBEREICH

File Naming:
  ABC00-name_S7  →  Präfix + Snake_Case + Stage-Suffix
  Beispiel:      Sprint-DEV-BACKLOG_GOV-NamingKonventionen_S8.md

Denglish-Entscheid:
  Bewusst und konsistent — kein Problem · muss nur dokumentiert sein

CamelCase vs Snake_Case:
  Zwei Kontexte · zwei Regeln · kein Mischen innerhalb eines Kontexts
  Properties     →  CamelCase
  Files          →  Snake_Case mit Präfix-Schema


================================================================================
BEZÜGE
================================================================================
[[GOV_Global_S6]]                         normative Grundlage
[[FREEZE-6_konsolidiert]]                 aktueller Ausgangszustand
[[Sprint-DEV-BACKLOG_Zwei-Welten-Umsetzung_S7]]   verwandter Backlog
[[SCRIPT-BAUKASTEN]]                      ggf. tangiert


================================================================================
Sprint-DEV-BACKLOG_GOV-NamingKonventionen | S8 | 2026-03-26 | R+MUNI Blueprint
================================================================================
