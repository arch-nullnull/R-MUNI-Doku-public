================================================================================
TMP DOKUMENTTYPEN — HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : TMP_How2_DEV_S105
Tag             : #dev #how2 #tmp #dokumenttypen #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Letzte Änderung : 2026-04-14
Ablageort       : R+MUNI Doku-public\02-how2\TMP_How2_DEV_S105.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[TMP_principles_S105]] gelesen und verstanden
- [[Global_GOV_DEV_S105]] bekannt — insbesondere Kapitel 10 (Sprint-Governance)
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
    (-> DEV-Hinweisblock im jeweiligen Template)
  - Governance-Regeln des Gesamtsystems
    (-> [[Global_GOV_DEV_S105]])


================================================================================
SCHRITT 1 - DOKUMENTTYP BESTIMMEN
================================================================================

Vor jedem neuen Dokument: Typ klären.

  Ich will verbindliche Regeln festlegen              ->  Type 1: GOV_Global
  Ich will Leitprinzipien einer Reihe beschreiben     ->  Type 2: principles
  Ich will eine Anleitung erstellen                   ->  Type 3: how2
  Ich will R+MUNI auf TOGAF / ArchiMate mappen        ->  Type 4: DEAKTIVIERT — nicht verwenden
  Ich will einen stabilen Stand einfrieren            ->  Type 5: FREEZE
  Ich will Ziele eines Stage definieren               ->  Type 6: Stage_Ziele
  Ich will einen abgeschlossenen Sprint dokumentieren ->  Type 7: Sprint-DEV-Doku
  Ich will einen künftigen Sprint vorplanen           ->  Type 8: Sprint-DEV-BACKLOG
  Ich brauche ein erklärendes Dokument ohne Typ       ->  Type 9: Info (frei)
  Ich erstelle ein Creative Asset                     ->  Type 10: Creative (frei)

Zweifelsfälle:
  Mehr als ein Typ trifft zu       ->  Dokument aufteilen — ein Dokument, ein Typ
  Kein Typ trifft zu               ->  Type 9 Info verwenden
  Neuer Typ scheint nötig          ->  [[Global_GOV_DEV_S105]] prüfen, Betreiber fragen


================================================================================
SCHRITT 2 - RICHTIGES TEMPLATE ÖFFNEN
================================================================================

Alle Templates liegen ausschließlich in:
  R+MUNI Doku-public\98-templates\

Template je Typ:

  Type 1   GOV_Global_Template_S105.md
  Type 2   principles_Template_S105.md
  Type 3   how2_DEV_Template_S105.md         (für DEV)
           how2_MUNI_Template_S105.md        (für R+MUNI Variante)
  Type 4   DEAKTIVIERT — kein Template
  Type 5   FREEZE_Template_S105.md           (nur auf Wunsch Betreiber / Stage-Ende)
  Type 6   Stage_Ziele_Template_S105.md
  Type 7   Sprint-DEV-Doku_Template_S105.md
  Type 8   Sprint-DEV-BACKLOG_Template_S105.md
  Type 9   Kein Template — Format frei
  Type 10  Kein Template — Format frei

Beta-Kunden-Prozess:
  Onboarding   BETA_ONBOARDING_Checkliste_Template_S105.md
  Offboarding  BETA_OFFBOARDING_Checkliste_Template_S105.md
  Lessons LL   LL_Template_S105.md

CARD Templates:
  CARD_principles_Template_S105.md
  CARD_How2_Template_S105.md
  CARD_Sprint_Template_S105.md
  CARD_Backlog_Template_S105.md
  CARD_Notes_Template_S105.md

Vorgehen:
  1. Template in R+MUNI Doku-public\98-templates\ öffnen
  2. Template kopieren — niemals das Original bearbeiten
  3. Kopie in R+MUNI Doku-internal\sprints\ ablegen
  4. Dateinamen nach Konvention setzen (-> Schritt 3)


KEIN TEMPLATE IM GEWÜNSCHTEN FORMAT VORHANDEN — ESKALATIONSPFAD
--------------------------------------------------------------------------------

Ist kein passendes Template in 98-templates\ vorhanden, gilt dieser Pfad:

  Stufe 1 — Ohne Template starten (Prinzip-basiert)
    Dokument auf Basis der Principles des jeweiligen Typs erstellen.
    Formstabilität so gut wie möglich einhalten.
    Output erzeugen und prüfen.

  Stufe 2 — DEV-Dokumente laden, Verhaltensanpassung beobachten
    Ist der Output aus Stufe 1 nicht wie gewünscht:
    Relevante DEV-Dokumente (Principles, How2, GOV) vollständig in den
    Kontext laden. Erneut versuchen. Verhaltensänderung beobachten.

  Stufe 3 — GitHub Issue im Doku-Repo erstellen
    Ist der Output auch nach Stufe 2 nicht wie gewünscht:
    Issue im GitHub Doku-Repo öffnen.
    Issue enthält: betroffener Dokumenttyp | fehlende Vorlage | Problem-Beschreibung.
    Kein weiterer Versuch ohne explizite Betreiber-Entscheidung.

Grundsatz: Kein freies Erfinden. Kein stiller Workaround ohne Eskalation.


================================================================================
SCHRITT 3 - DATEI KORREKT BENENNEN
================================================================================

Benennungskonvention je Typ:

  Type 1   GOV_<TITEL>_S<N>.md
           Beispiel: GOV_Kunden_S105.md

  Type 2   <REIHE>_principles_S<N>.md
           Beispiel: CSV_principles_S105.md

  Type 3   <REIHE>_How2_DEV_S<N>.md
           Beispiel: CSV_How2_DEV_S105.md
           <REIHE>_How2_MUNI_S<N>.md
           Beispiel: CSV_How2_MUNI_S105.md

  Type 4   DEAKTIVIERT

  Type 5   FREEZE-<Stagenummer>_S<N>.md
           Beispiel: FREEZE-105_S105.md

  Type 6   Stage<Nummer>_Ziele_S<N>.md
           Beispiel: Stage105_Ziele_S105.md

  Type 7   Sprint-DEV-<BEZEICHNUNG>_S<N>.md
           Beispiel: Sprint-DEV-CSV-Refactoring_S105.md

  Type 8   Sprint-DEV-BACKLOG_<BEZEICHNUNG>_S<N>.md
           Beispiel: Sprint-DEV-BACKLOG_BPMN-Flows_S105.md

  Beta-Kunden:
           BETA_ONBOARDING_Checkliste_<BETAKUNDE_XX>_S<N>.md
           BETA_OFFBOARDING_Checkliste_<BETAKUNDE_XX>_S<N>.md
           LL_<BEZEICHNUNG>_S<N>.md

  CARD:
           CARD_<BEZEICHNUNG>_S<N>.md
           Beispiel: CARD_principles_EA_S105.md

Stage-Suffix:
  <N> = Stage in dem das Dokument erstellt wird
  Beispiel: Dokument erstellt in Stage 105 -> _S105
  Der Suffix ist DEV-intern — er entfällt in der Release-Version (Cleaning Run)

Hinweis Deprecated:
  _ASSOCIATE_ und _PUBLIC_ sind nicht mehr gültig.
  Bestehende Dokumente mit diesem Kürzel werden im Cleaning Run bereinigt.
  Neue Dokumente dürfen diese Kürzel nicht verwenden.


================================================================================
SCHRITT 4 - DOKUMENT AUSFÜLLEN
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

  Fehler: Template aus 04-notes\ oder 02-how2\ kopiert
    Lösung: Templates liegen ausschließlich in 98-templates\ — kein anderer Pfad gültig

  Fehler: _ASSOCIATE_ oder _PUBLIC_ im Dateinamen verwendet
    Lösung: _ASSOCIATE_ -> _CARD_ | _PUBLIC_ -> nicht mehr verwendet
            Beide Kürzel sind deprecated seit Stage 104


================================================================================
SCHRITT 5 - DOKUMENT IN ARBEIT VERWALTEN
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
SCHRITT 6 - FREIGABE UND PUBLIZIERUNG
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
  Type 4   DEAKTIVIERT — kein Zielordner
  Type 5   R+MUNI Doku-public\04-notes\
  Type 6   R+MUNI Doku-public\04-notes\
  Type 7   R+MUNI Doku-public\04-notes\
  Type 8   R+MUNI Doku-internal\backlog\        <- bleibt internal
  Type 9   R+MUNI Doku-internal\infocfg\        <- bleibt internal
  Type 10  R+MUNI Doku-creative\               <- eigenes Repo, Sales + DEV

  Beta-Kunden:
  Onboarding / Offboarding Checklisten  R+MUNI Doku-internal\kunden\<BETAKUNDE_XX>\
  LL-Dokumente                          R+MUNI Doku-internal\notiz\

  CARD:
  CARD-Dokumente                        R+MUNI Doku-internal\00-CARD [fun]\

Nach Freigabe:
  - Dokument ist unveränderlich
  - Änderungen nur durch explizite Stage-Entscheidung des Betreibers
  - Original im sprints-Ordner kann archiviert oder gelöscht werden


================================================================================
BEZÜGE
================================================================================
[[TMP_principles_S105]]              Dokumenttypen — Zweck, Regeln, Ablage
[[Global_GOV_DEV_S105]]              normative Grundlage — insbesondere Kapitel 10
[[naming_and_structure_S104]]        Namenskonventionen und Varianten-Tiering
[[BETA_OFFBOARDING_How2_DEV_S105]]   Beta-Kunden Offboarding-Prozess


================================================================================
TMP_How2_DEV | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
