================================================================================
TMP DOKUMENTTYPEN — HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : TMP_How2_DEV_S101
Tag             : #dev #how2 #tmp #dokumenttypen #s101
Datum           : 2026-03-31
Stage           : S1.01 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Ablageort       : R+MUNI Doku-public\02-how2\TMP_How2_DEV_S101.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[TMP_principles_S8]] gelesen und verstanden
- [[Global_GOV_DEV_S101]] bekannt — insbesondere Kapitel 10 (Sprint-Governance)
- Zugriff auf R+MUNI Doku-internal (sprints-Ordner) vorhanden
- Zugriff auf R+MUNI Doku-public vorhanden
- GitHub Sync eingerichtet und funktionsfähig


================================================================================
ÜBERSICHT
================================================================================

Diese How2 beschreibt wie DEV-Mitglieder Dokumente des R+MUNI Blueprint
korrekt erstellen, pflegen und freigeben.

Sie deckt ab:
  - Welches Template für welchen Anwendungsfall
  - Wo ein Dokument in Arbeit lebt
  - Wie ein Dokument freigegeben und publiziert wird
  - Was beim Ausfüllen eines Templates zu beachten ist

Sie deckt nicht ab:
  - Den inhaltlichen Aufbau der einzelnen Templates
    (→ DEV-Hinweisblock im jeweiligen Template)
  - Governance-Regeln des Gesamtsystems
    (→ [[Global_GOV_DEV_S101]])


================================================================================
SCHRITT 1 – DOKUMENTTYP BESTIMMEN
================================================================================

Vor jedem neuen Dokument: Typ klären.

  Ich will verbindliche Regeln festlegen              →  Type 1: GOV_Global
  Ich will Leitprinzipien einer Reihe beschreiben     →  Type 2: principles
  Ich will eine Anleitung erstellen                   →  Type 3: how2
  Ich will R+MUNI auf TOGAF / ArchiMate mappen        →  Type 4: Rosetta-Stone
  Ich will einen stabilen Stand einfrieren            →  Type 5: FREEZE
  Ich will Ziele eines Stage definieren               →  Type 6: Stage_Ziele
  Ich will einen abgeschlossenen Sprint dokumentieren →  Type 7: Sprint-DEV-Doku
  Ich will einen künftigen Sprint vorplanen           →  Type 8: Sprint-DEV-BACKLOG
  Ich brauche ein erklärendes Dokument ohne Typ       →  Type 9: Info (frei)
  Ich erstelle ein Creative Asset                     →  Type 10: Creative (frei)

Zweifelsfälle:
  Mehr als ein Typ trifft zu       →  Dokument aufteilen — ein Dokument, ein Typ
  Kein Typ trifft zu               →  Type 9 Info verwenden
  Neuer Typ scheint nötig          →  [[Global_GOV_DEV_S101]] prüfen, Betreiber fragen


================================================================================
SCHRITT 2 – RICHTIGES TEMPLATE ÖFFNEN
================================================================================

Templates liegen in:
  R+MUNI Doku-internal\infocfg\   (oder nach Ablageentscheidung des Betreibers)

Template je Typ:

  Type 1   GOV_Global_Template_S101.md
  Type 2   principles_Template_S101.md
  Type 3   how2_DEV_Template_S101.md        (für DEV / Poweruser)
  Type 4   Rosetta-Stone_Template_S101.md
  Type 5   FREEZE_Template_S101.md          (nur auf Wunsch Betreiber / Stage-Ende)
  Type 6   Stage_Ziele_Template_S101.md
  Type 7   Sprint-DEV-Doku_Template_S101.md
  Type 8   Sprint-DEV-BACKLOG_Template_S101.md
  Type 9   Kein Template — Format frei
  Type 10  Kein Template — Format frei

Beta-Kunden-Prozess:
  Onboarding   BETA_ONBOARDING_Checkliste_Template_S101.md
  Offboarding  BETA_OFFBOARDING_Checkliste_Template_S101.md
  Lessons LL   LL_Template_S101.md

Vorgehen:
  1. Template kopieren — niemals das Original bearbeiten
  2. Kopie in R+MUNI Doku-internal\sprints\ ablegen
  3. Dateinamen nach Konvention setzen (→ Schritt 3)


================================================================================
SCHRITT 3 – DATEI KORREKT BENENNEN
================================================================================

Benennungskonvention je Typ:

  Type 1   GOV_<TITEL>_S<N>.md
           Beispiel: GOV_Kunden_S101.md

  Type 2   <REIHE>_principles_S<N>.md
           Beispiel: CSV_principles_S101.md

  Type 3   <REIHE>_How2_DEV_S<N>.md
           Beispiel: CSV_How2_DEV_S101.md

  Type 4   Rosetta-Stone_<THEMA>_S<N>.md
           Beispiel: Rosetta-Stone_Phase-A_S101.md

  Type 5   FREEZE-<Stagenummer>_S<N>.md
           Beispiel: FREEZE-101_S101.md

  Type 6   Stage<Nummer>_Ziele_S<N>.md
           Beispiel: Stage101_Ziele_S101.md

  Type 7   Sprint-DEV-<BEZEICHNUNG>_S<N>.md
           Beispiel: Sprint-DEV-CSV-Refactoring_S101.md

  Type 8   Sprint-DEV-BACKLOG_<BEZEICHNUNG>_S<N>.md
           Beispiel: Sprint-DEV-BACKLOG_BPMN-Flows_S101.md

  Beta-Kunden:
           BETA_ONBOARDING_Checkliste_<BETAKUNDE_XX>_S<N>.md
           BETA_OFFBOARDING_Checkliste_<BETAKUNDE_XX>_S<N>.md
           LL_<BEZEICHNUNG>_S<N>.md

Stage-Suffix:
  <N> = Stage in dem das Dokument erstellt wird
  Beispiel: Dokument erstellt in Stage 1.01 → _S101
  Der Suffix ist DEV-intern — er entfällt in der Release-Version (Cleaning Run)


================================================================================
SCHRITT 4 – DOKUMENT AUSFÜLLEN
================================================================================

Reihenfolge beim Ausfüllen:
  1. Header vollständig ausfüllen (Datum, Stage, Ablageort, Verantwortlich)
  2. DEV-Hinweisblock lesen — er enthält die Spielregeln für diesen Typ
  3. Platzhalter in <GROSSBUCHSTABEN> ersetzen
  4. Optionale Kapitel: behalten wenn relevant, entfernen wenn nicht
  5. DEV-Hinweisblock am Ende entfernen

Pflichtregeln beim Ausfüllen:
  - Ein Dokument behandelt genau ein Thema
  - Formstabilität hat Vorrang — Struktur nicht eigenmächtig ändern
  - Obsidian-Links dort einsetzen wo echte Bezüge bestehen
  - Keine leeren Platzhalter im fertigen Dokument lassen
  - Kommentarblöcke (<!-- ... -->) vollständig entfernen

Typische Fehler:
  Fehler: Platzhalter <BEZEICHNUNG> stehen lassen
    Lösung: Vor Freigabe vollständig prüfen — kein <> darf im Dokument verbleiben

  Fehler: DEV-Hinweisblock nicht entfernt
    Lösung: Vor Freigabe prüfen — Kommentarblöcke gehören nicht ins fertige Dokument

  Fehler: Optionale Kapitel leer lassen statt entfernen
    Lösung: Leere optionale Kapitel konsequent entfernen

  Fehler: Zwei Themen in einem Dokument
    Lösung: Aufteilen — ein Dokument, ein Typ, ein Thema


================================================================================
SCHRITT 5 – DOKUMENT IN ARBEIT VERWALTEN
================================================================================

Solange ein Dokument in Arbeit ist:
  Ablage:  R+MUNI Doku-internal\sprints\
  Status:  Im Datei-Header als "In Arbeit" oder aktuellen Status kennzeichnen
  Zugriff: Nur DEV-Mitglieder (internal Repo — privat)

Versionierung während der Arbeit:
  Kein eigenes Versioning — der sprints-Ordner ist der Arbeitsbereich
  GitHub Sync des internal Repos sichert den Arbeitsstand

Mehrere DEV-Mitglieder am selben Dokument:
  Abstimmung über Betreiber — kein paralleles Bearbeiten ohne Absprache
  Last-Write-Wins ist keine Strategie


================================================================================
SCHRITT 6 – FREIGABE UND PUBLIZIERUNG
================================================================================

Freigabe ist ein expliziter Akt des Betreibers — kein automatischer Vorgang.

Freigabeprozess:
  1. DEV signalisiert Fertigstellung an Betreiber
  2. Betreiber prüft Konformität mit Template und GOV
  3. Betreiber gibt explizit frei (mündlich oder schriftlich im Chat)
  4. Dokument wird in das public Repo verschoben

Zielordner je Typ nach Freigabe:

  Type 1   R+MUNI Doku-public\00-governance\
  Type 2   R+MUNI Doku-public\01-principles\
  Type 3   R+MUNI Doku-public\02-how2\
  Type 4   R+MUNI Doku-public\03-rosetta_stone\
  Type 5   R+MUNI Doku-public\04-notes\
  Type 6   R+MUNI Doku-public\04-notes\
  Type 7   R+MUNI Doku-public\04-notes\
  Type 8   R+MUNI Doku-internal\backlog\        ← bleibt internal
  Type 9   R+MUNI Doku-internal\infocfg\        ← bleibt internal
  Type 10  R+MUNI Doku-creative\               ← eigenes Repo, Sales + DEV

  Beta-Kunden:
  Onboarding / Offboarding Checklisten  R+MUNI Doku-internal\kunden\<BETAKUNDE_XX>\
  LL-Dokumente                          R+MUNI Doku-internal\notiz\

Nach Freigabe:
  - Dokument ist unveränderlich
  - Änderungen nur durch explizite Stage-Entscheidung des Betreibers
  - Original im sprints-Ordner kann archiviert oder gelöscht werden



================================================================================
BEZÜGE
================================================================================
[[TMP_principles_S8]]               Dokumenttypen — Zweck, Regeln, Ablage
[[Global_GOV_DEV_S101]]             normative Grundlage — insbesondere Kapitel 10
[[BETA_OFFBOARDING_How2_DEV_S101]]  Beta-Kunden Offboarding-Prozess


================================================================================
TMP_How2_DEV | S1.01 | 2026-03-31 | R+MUNI Blueprint
================================================================================
