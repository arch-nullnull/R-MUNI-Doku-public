================================================================================
TMP – DOKUMENTTYPEN & TEMPLATES – PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : TMP_principles_S105
Tag             : #dev #principles #tmp #dokumenttypen #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-18
Letzte Änderung : 2026-04-14
Ablageort       : R+MUNI Doku-public\01-principles\TMP_principles_S105.md
================================================================================


1. ZWECK UND DESIGNPHILOSOPHIE
--------------------------------------------------------------------------------
Das R+MUNI Dokumentationssystem kennt keine freie Dokumentenform.
Jedes Dokument gehört zu einem definierten Typ — mit festem Zweck,
verbindlicher Struktur und klarer Ablage.

Kernprinzip: Form vor Sprache. Die Struktur eines Dokuments ist nicht
Gegenstand von Interpretation oder Kreativität. Sie ist vorgegeben,
prüfbar und stabil.

Dieses Principles-Dokument beschreibt alle verbindlichen Dokumenttypen
des R+MUNI Blueprints — ihren Zweck, ihre Regeln, ihre Ablage und ihr
Publizierungsverhalten.

Es richtet sich an DEV-Mitglieder die Dokumente erstellen, pflegen
und freigeben.


2. GRUNDREGELN FÜR ALLE DOKUMENTTYPEN
--------------------------------------------------------------------------------
Diese Regeln gelten für jeden Dokumenttyp ohne Ausnahme:

  - Ein Dokument behandelt genau ein klar abgegrenztes Thema.
  - Dokumenttypen dürfen nicht vermischt werden.
  - Jedes Dokument folgt dem verbindlichen Template seines Typs.
  - Abweichungen von der Struktur sind nur zulässig wenn sie
    explizit definiert und dokumentiert sind.
  - Formstabilität hat Vorrang vor sprachlicher Variation.
  - Dokumente mit Stage-Suffix (_S105, _S104 ...) tragen den
    Erstellungszustand als Information für DEV-interne Planung.
    Im öffentlichen Release-Zustand (Beta 1.0+) entfällt der Suffix.
  - Dokumente in Arbeit leben im privaten Repo (sprints-Ordner)
    bis zur expliziten Freigabe durch den Betreiber.
  - Die Freigabe für public ist ein bewusster, expliziter Akt —
    kein automatischer Vorgang.


3. REPO- UND ABLAGELOGIK
--------------------------------------------------------------------------------
R+MUNI nutzt drei getrennte Repositories mit klar definiertem Zweck:

  PUBLIC — R+MUNI Doku-public
    GitHub: https://github.com/arch-nullnull/MLAT-Doku-public
    Zugriff: jeder
    Inhalt:  normative, lernende und freigegebene Dokumentation
    Format:  ausschließlich .md

  INTERNAL — R+MUNI Doku-internal
    GitHub: https://github.com/arch-nullnull/R-MUNI-Doku-internal
    Zugriff: nur dedizierte DEV-Mitglieder
    Inhalt:  Arbeitsdokumentation, Backlog, Info, Sprints in Arbeit
    Format:  .md für strukturierte Typen, frei für Info

  CREATIVE — R+MUNI Doku-creative
    GitHub: https://github.com/arch-nullnull/R-MUNI-Doku-creative
    Zugriff: Sales + dedizierte DEV-Mitglieder
    Inhalt:  Creative Assets, Sales-Material
    Format:  frei

Sprints in Arbeit (Types 5–7 vor Freigabe) leben temporär in:
  R+MUNI Doku-internal\sprints\


4. DOKUMENTTYPEN — ÜBERSICHT
--------------------------------------------------------------------------------

  Type 1   GOV_Global          normatives Regelwerk
  Type 2   principles          Leitprinzipien einer Reihe oder eines Themas
  Type 3   how2                Anleitungen für Varianten und Flows
  Type 4   Rosetta-Stone       [DEAKTIVIERT — siehe Kapitel 8]
  Type 5   FREEZE              stabiler, freigegebener Versionsstand
  Type 6   Stage_Ziele         Begründung und Ziele hinter einem Stage
  Type 7   Sprint-DEV-Doku     abgeschlossener, gesyncter Sprint
  Type 8   Sprint-DEV-BACKLOG  Planung für spätere Stages und Zeitpunkte
  Type 9   Info                erklärendes Dokument ohne festen Typ — frei
  Type 10  Creative            Creative Asset — frei

Types 1–3, 5–8 haben verbindliche Templates.
Type 4 ist reserviert — deaktiviert, nicht neu zu belegen.
Types 9–10 haben kein Template — Format ist frei.

Templates aller aktiven Typen liegen in:
  R+MUNI Doku-public\98-templates\


5. TYPE 1 — GOV_GLOBAL
--------------------------------------------------------------------------------
Zweck:
  Definiert das normative Regelwerk des R+MUNI Blueprints.
  Es ist das "Gesetz" des Systems — unveränderlich bis zur
  expliziten Stage-Entscheidung des Betreibers.

Charakter:
  - Enthält Regeln und erklärende Inhalte — Erklärungen dienen dem Verständnis, Regeln sind verbindlich (GOV Kap. 3.8)
  - Jede Regel ist genau eine Aussage
  - Jede Regel ist prüfbar
  - Implizite Logik ist unzulässig

Ablage:
  Repo:    R+MUNI Doku-public
  Ordner:  00-governance\
  Datei:   GOV_Global_S<N>.md

Publizierung:
  Public — jeder
  Änderungen nur durch explizite Freigabe des Betreibers

Template:
  R+MUNI Doku-public\98-templates\GOV_Global_Template_S105.md


6. TYPE 2 — PRINCIPLES
--------------------------------------------------------------------------------
Zweck:
  Beschreibt die Leitprinzipien einer Reihe oder eines Themas.
  Principles erklären warum etwas so ist wie es ist — nicht wie
  es angewendet wird. Das ist Aufgabe der How2.

Charakter:
  - Beschreibt Designentscheidungen und ihre Begründung
  - Enthält keine operativen Schritt-für-Schritt-Anleitungen
  - Ist eigenständig lesbar ohne Kenntnis anderer Dokumente
  - Richtet sich an DEV und technisch versierte User

Benennung:
  <REIHE>_principles_S<N>.md
  Beispiel: CSV_principles_S105.md

Ablage:
  Repo:    R+MUNI Doku-public
  Ordner:  01-principles\
  Datei:   <REIHE>_principles_S<N>.md

Publizierung:
  Public — jeder

Template:
  R+MUNI Doku-public\98-templates\principles_Template_S105.md


7. TYPE 3 — HOW2
--------------------------------------------------------------------------------
Zweck:
  Beschreibt konkret wie etwas angewendet wird — Schritt für Schritt.
  How2 ist die operative Umsetzung der Principles.

Ausprägungen:
  How2 existiert in zwei klar getrennten Ausprägungen je Zielvariante:

  DEV  — technische Referenz für DEV
         Kompakte Script-Aufrufe, Ausgaben, Flags, Fehlerbilder
         Setzt technisches Grundverständnis voraus

  MUNI — erklärende Anleitung für R+MUNI Anwender
         Schrittweise Führung, Kontext, Erwartungsmanagement
         Setzt kein technisches Vorwissen voraus
         Entsteht aus anonymisierten Beta-Erfahrungen —
         nicht hier im DEV-Prozess, sondern in der Feedback-Schleife

  Beide Ausprägungen sind eigenständige Dokumente.
  Ein Dokument darf nicht beide Ausprägungen vermischen.

Charakter DEV:
  - Kompakte Referenz — Befehl, Ziel, Ausgabe
  - Kurzreferenz aller Scripts der Reihe
  - Typische Fehlerbilder und direkte Lösung
  - Varianten und Flags explizit dokumentiert

Charakter MUNI:
  - Schritt-für-Schritt mit Kontext und Begründung
  - Erwartungsmanagement am Anfang
  - Konkrete Beispiele aus der Praxis
  - Klare Voraussetzungen und typische Stolperfallen

Benennung:
  <REIHE>_How2_DEV_S<N>.md    Beispiel: CSV_How2_DEV_S105.md
  <REIHE>_How2_MUNI_S<N>.md   Beispiel: CSV_How2_MUNI_S105.md

Ablage:
  Repo:    R+MUNI Doku-public
  Ordner:  02-how2\
  Datei:   <REIHE>_How2_DEV_S<N>.md / <REIHE>_How2_MUNI_S<N>.md

Publizierung:
  Public — jeder

Templates:
  R+MUNI Doku-public\98-templates\how2_DEV_Template_S105.md
  R+MUNI Doku-public\98-templates\how2_MUNI_Template_S105.md


8. TYPE 4 — ROSETTA-STONE [DEAKTIVIERT]
--------------------------------------------------------------------------------
Status:
  TYPE 4 IST DEAKTIVIERT.
  Keine neuen Rosetta-Stone-Dokumente werden erstellt.
  Bestehende Dokumente in 03-rosetta_stone\ bleiben unverändert erhalten.
  Der Typ-Slot 4 bleibt reserviert — er wird nicht neu belegt.
  Eine spätere Reaktivierung ist möglich ohne Rückwirkung auf
  bestehende Dokumente.

Hintergrund:
  Der Type 4 wurde eingeführt um R+MUNI-Konzepte in TOGAF und
  ArchiMate zu übersetzen. Die Entscheidung zur Deaktivierung
  erfolgt in Stage 105 — der Ordner 03-rosetta_stone\ und alle
  bestehenden Inhalte bleiben als stiller Bestand erhalten.

Ordner:
  R+MUNI Doku-public\03-rosetta_stone\   (bleibt — read-only)

Neue Einträge:
  KEINE — Type 4 ist geschlossen.


9. TYPE 5 — FREEZE
--------------------------------------------------------------------------------
Zweck:
  Dokumentiert einen stabilen, freigegebenen Versionsstand.
  Ein Freeze ist ein expliziter Akt des Betreibers — kein automatischer
  Zustand. Er definiert was gilt, was ausgeschlossen ist und was
  bewusst zurückgestellt wurde.

Charakter:
  - Beschreibt den fixierten Zustand zum Freeze-Zeitpunkt
  - Enthält Geltungsbereich, Ausschlüsse und Validierung
  - Ist nach Freigabe unveränderlich
  - Dient als Baseline für nachfolgende Sprints

Benennung:
  FREEZE-<Stagenummer>_S<N>.md
  Beispiel: FREEZE-105_S105.md

Ablage:
  Während Arbeit: R+MUNI Doku-internal\sprints\
  Nach Freigabe:  R+MUNI Doku-public\04-notes\

Publizierung:
  Public nach expliziter Freigabe durch Betreiber

Template:
  R+MUNI Doku-public\98-templates\FREEZE_Template_S105.md


10. TYPE 6 — STAGE_ZIELE
--------------------------------------------------------------------------------
Zweck:
  Definiert Begründung, Charakter und Ziele eines Stage.
  Beantwortet warum dieser Stage existiert und was er leisten soll —
  nicht wie er technisch umgesetzt wird.

Charakter:
  - Strategisch, nicht operativ
  - Enthält Ausgangsbasis, Ziele und Abgrenzung
  - Wird zu Beginn eines Stage erstellt und bei Bedarf ergänzt
  - Ist nach Stage-Abschluss read-only

Benennung:
  Stage<Nummer>_Ziele_S<N>.md
  Beispiel: Stage105_Ziele_S105.md

Ablage:
  Während Arbeit: R+MUNI Doku-internal\sprints\
  Nach Freigabe:  R+MUNI Doku-public\04-notes\

Publizierung:
  Public nach expliziter Freigabe durch Betreiber

Template:
  R+MUNI Doku-public\98-templates\Stage_Ziele_Template_S105.md


11. TYPE 7 — SPRINT-DEV-DOKU
--------------------------------------------------------------------------------
Zweck:
  Vollständiges Arbeitsgedächtnis eines abgeschlossenen Sprints.
  Die Sprint-DEV-Doku muss es einem DEV-Mitglied ermöglichen den Sprint
  in einem Jahr ohne Rückfragen vollständig nachzuvollziehen —
  Kontext, Entscheidungen, Umsetzung, Ergebnis und offene Punkte inklusive.

  Sie ist kein schlankes Nachweis-Dokument — sie ist die vollständige
  Dokumentation einer Entwicklungsaktivität.

Charakter:
  - Beschreibt Ausgangslage, Motivation und Kontext vollständig
  - Enthält alle wesentlichen Entscheidungen mit Begründung
  - Dokumentiert verworfene Alternativen explizit
  - Enthält Script-Inhalte oder Auszüge wo sie für das Verständnis
    der Umsetzung relevant sind
  - Diagramme auf .md-unterstützter Basis (Mermaid o.ä.) sind
    ausdrücklich erwünscht wenn sie Zusammenhänge klären
  - Verlinkungen zu Creative-Assets im Doku-creative Repo sind zulässig
    und erwünscht wenn visuelle Materialien die Doku ergänzen
  - Enthält Validierung, Governance-Check und Lessons Learned
  - Baut explizit auf dem letzten Freeze auf und benennt die Delta
  - Wird nach Abschluss gesynct und ist dann unveränderlich

Tiefe:
  Die Dokumentationstiefe richtet sich nach der Komplexität des Sprints.
  Einfache Bugfixes können kürzer sein.
  Strukturelle Änderungen, neue Reihen oder Logikentscheidungen
  erfordern volle Tiefe — inkl. Vorher/Nachher, Script-Beispiele
  und expliziter Begründung jeder wesentlichen Entscheidung.

Benennung:
  Sprint-DEV-<BEZEICHNUNG>_S<N>.md
  Beispiel: Sprint-DEV-CSV-Refactoring_S105.md

Ablage:
  Während Arbeit: R+MUNI Doku-internal\sprints\
  Nach Freigabe:  R+MUNI Doku-public\04-notes\

Publizierung:
  Public nach expliziter Freigabe durch Betreiber

Template:
  R+MUNI Doku-public\98-templates\Sprint-DEV-Doku_Template_S105.md


12. TYPE 8 — SPRINT-DEV-BACKLOG
--------------------------------------------------------------------------------
Zweck:
  Plant und beschreibt Sprints für spätere Stages und Zeitpunkte.
  Der Backlog ist kein Versprechen — er ist strukturierte Vorausschau.

Charakter:
  - Enthält Motivation, Ziel und Abgrenzung geplanter Sprints
  - Bleibt internal bis zur expliziten Entscheidung zur Umsetzung
  - Wird im DEV-Modus zusätzlich nach Jira gespiegelt
  - Kann jederzeit priorisiert, verschoben oder verworfen werden

Benennung:
  Sprint-DEV-BACKLOG_<BEZEICHNUNG>_S<N>.md
  Beispiel: Sprint-DEV-BACKLOG_BPMN-Flows_S105.md

Ablage:
  Repo:    R+MUNI Doku-internal
  Ordner:  backlog\
  Datei:   Sprint-DEV-BACKLOG_<BEZEICHNUNG>_S<N>.md

Publizierung:
  Bleibt internal — kein automatischer Public-Weg
  Jira-Sync im DEV-Modus aktiv

Template:
  R+MUNI Doku-public\98-templates\Sprint-DEV-BACKLOG_Template_S105.md


13. TYPE 9 — INFO
--------------------------------------------------------------------------------
Zweck:
  Aufnahme für alle erklärenden Dokumente die keinem anderen Typ
  entsprechen aber für DEV-interne Arbeit benötigt werden.

Charakter:
  - Kein verbindliches Template
  - Format ist frei
  - Dient der internen Orientierung und Kommunikation
  - Kein normatives Gewicht

Ablage:
  Repo:    R+MUNI Doku-internal
  Ordner:  infocfg\

Publizierung:
  Bleibt internal

Template:
  Keines — Format frei


14. TYPE 10 — CREATIVE
--------------------------------------------------------------------------------
Zweck:
  Aufnahme für alle Creative Assets und Sales-Materialien.

Charakter:
  - Kein verbindliches Template
  - Format ist frei
  - Richtet sich an Sales und ausgewählte DEV-Mitglieder

Ablage:
  Repo:    R+MUNI Doku-creative
  Ordner:  R+MUNI Doku-creative\

Publizierung:
  Privat — nur Sales + dedizierte DEV-Mitglieder

Template:
  Keines — Format frei


15. TEMPLATE-ABLAGE — 98-TEMPLATES
--------------------------------------------------------------------------------
Ab Stage 105 gibt es einen dedizierten Ordner für alle verbindlichen Templates:

  R+MUNI Doku-public\98-templates\

Dieser Ordner ist der einzige autoritative Ablageort für Templates.
Kein Template liegt mehr verstreut in 02-how2\ oder 04-notes\.

Inhalt:

  GOV_Global_Template_S105.md
  principles_Template_S105.md
  how2_DEV_Template_S105.md
  how2_MUNI_Template_S105.md
  FREEZE_Template_S105.md
  Stage_Ziele_Template_S105.md
  Sprint-DEV-Doku_Template_S105.md
  Sprint-DEV-BACKLOG_Template_S105.md

  Beta-Kunden-Prozess:
  BETA_ONBOARDING_Checkliste_Template_S105.md
  BETA_OFFBOARDING_Checkliste_Template_S105.md
  LL_Template_S105.md

  CARD Templates:
  CARD_principles_Template_S105.md
  CARD_How2_Template_S105.md
  CARD_Sprint_Template_S105.md
  CARD_Backlog_Template_S105.md
  CARD_Notes_Template_S105.md

Zugriffsregel:
  Templates sind public — jeder DEV-Zugriff ist lesend.
  Änderungen an Templates nur durch explizite Stage-Entscheidung des Betreibers.
  Templates werden niemals direkt bearbeitet — immer kopieren, dann ausfüllen.

Hinweis zur Struktur:
  Der Ordner 98-templates\ ist neu ab Stage 105.
  Er ist in der naming_and_structure_S104 noch nicht enthalten.
  Er wird beim nächsten Structure-Update offiziell erfasst.


16. LEBENSZYKLUS EINES DOKUMENTS
--------------------------------------------------------------------------------
Jedes Dokument mit verbindlichem Template durchläuft diesen Zyklus:

  1. ENTWURF
     Dokument wird in R+MUNI Doku-internal\sprints\ erstellt.
     Stage-Suffix trägt den Erstellungszustand.
     Kein Public-Zugriff.

  2. REVIEW
     Betreiber prüft Konformität mit Template und GOV.
     Korrekturen erfolgen im internen Zustand.

  3. FREIGABE
     Expliziter Akt durch Betreiber.
     Dokument wird nach R+MUNI Doku-public verschoben.
     Ab diesem Zeitpunkt unveränderlich — außer bei
     expliziter Stage-Entscheidung.

  4. CLEANING RUN (vor Beta 1.0)
     Alle public Dokumente werden auf finale Stage-Konformität geprüft.
     Stage-Suffix entfällt in der Release-Version.
     DEV-interne Planung nutzt den Suffix weiterhin.

  5. ARCHIV
     Dokumente vergangener Stages werden nicht gelöscht.
     Sie bleiben als historische Referenz erhalten.


17. OBSIDIAN — OPTIONALE VISUALISIERUNGSEBENE
--------------------------------------------------------------------------------
Obsidian ist die optionale Visualisierungsebene des R+MUNI Blueprint.
Sie ist kein Pflichtbestandteil — aber ein explizit unterstützter Weg
für alle die Dokumentbezüge und Strukturzusammenhänge visuell erfassen
und navigieren wollen.

Grundidee:
  Dokumentbezüge werden nicht in EA-Modell-Ordnerstrukturen abgebildet —
  sondern auf File-Ebene direkt in den .md Dokumenten als Obsidian-Links.
  Obsidian visualisiert diese Links automatisch als Graph.

Obsidian-Links in .md Dokumenten:
  Standard Obsidian-Link:   [[Dokumentname]]
  Mit Alias:                [[Dokumentname|Anzeigetext]]
  Mit Abschnitt:            [[Dokumentname#Kapitel]]

  Beispiele:
    [[TMP_principles_S105]]
    [[FREEZE_1_05|Freeze Stage 105 Baseline]]
    [[Sprint-DEV-CleaningRun_S105#Ergebnis]]

Wo Obsidian-Links eingesetzt werden:
  - In Sprint-DEV-Dokus: Bezug auf referenzierte Freezes, Principles,
    Scripts und vorherige Sprints
  - In Principles: Querverweise auf verwandte Reihen und GOV-Kapitel
  - In How2: Verlinkung auf Voraussetzungs-Dokumente und Folgeschritte
  - In Freeze-Dokumenten: Bezug auf Stage_Ziele und Sprint-DEV-Dokus
    die in diesen Freeze geflossen sind

Verlinkung Creative-Assets:
  Dokumente im Doku-creative Repo können als relative Pfadlinks
  oder Obsidian-Links eingebunden werden wenn sie den Dokumentkontext
  visuell ergänzen.

Obsidian und GitHub:
  .obsidian/ ist in .gitignore ausgeschlossen — Workspace-Einstellungen
  bleiben lokal. Die .md Dateien mit ihren Links sind vollständig
  GitHub-kompatibel.

Konvention:
  Obsidian-Links sind optional — kein Dokument ist verpflichtet sie
  zu enthalten. Sie dürfen den Fließtext nicht ersetzen — der
  Dokumentinhalt muss auch ohne Obsidian vollständig lesbar sein.


18. ABGRENZUNG ZU ANDEREN DOKUMENTEN
--------------------------------------------------------------------------------
Dieses Dokument beschreibt ausschließlich:
  - Was die Dokumenttypen sind
  - Welche Regeln für sie gelten
  - Wo sie abgelegt werden
  - Wie sie publiziert werden

Dieses Dokument beschreibt nicht:
  - Wie Templates konkret ausgefüllt werden (→ How2)
  - Den Inhalt einzelner Templates (→ jeweiliges Template unter 98-templates\)
  - Operative Prozessschritte der Sprint-Arbeit (→ Sprint-DEV-Doku)
  - Governance-Regeln des Gesamtsystems (→ GOV_Global)


================================================================================
TMP PRINCIPLES | S105 | 2026-04-14
18 Kapitel | Dokumenttypen 1–10 | 98-templates eingeführt | Type 4 deaktiviert
================================================================================
