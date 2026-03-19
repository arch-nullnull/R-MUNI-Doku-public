================================================================================
SPRINT-DEV-DOKU – TMP-Reihe
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : Sprint-DEV-TMP-Reihe
Datum               : 2026-03-18
Stage               : S6 – AKTIV
Status              : Abgeschlossen
Erstellt durch      : EUMAXL + Claude (Pair-Session)
Vorgänger           : [[FREEZE-6_S6]]
Nachfolger          : offen — nächster Sprint nach Betreiber-Entscheidung
================================================================================


================================================================================
1. AUSGANGSLAGE UND KONTEXT
================================================================================

1.1 Ist-Zustand vor diesem Sprint
-----------------------------------
Mit FREEZE-6 wurde Stage 5.7 auf sauberer technischer Basis eröffnet.
Das Scripting ist abgeschlossen, alle Reihen sind auf Stage-5-Konventionen.

Was fehlte:

  Das R+MUNI Blueprint hatte bis zu diesem Sprint kein explizites,
  normatives Dokument das Dokumenttypen, Templates und ihre Ablage- und
  Publizierungslogik beschreibt.

  Principles und How2 existierten für alle technischen Reihen (CLE, CSV,
  XML, HLP, M2B, ATL, FLW). Für die Dokumentation selbst — also das System
  das alle anderen Dokumente beschreibt — gab es keine eigene Reihe.

Konkrete Lücken vor dem Sprint:
  - Kein normatives Dokument das alle Dokumenttypen definiert
  - Keine verbindlichen Templates für DEV-Dokumente
  - Keine explizite Ablage- und Publizierungslogik (Repo / Ordner / Freigabe)
  - Keine dokumentierte Benennungskonvention für Dokumente
  - Obsidian als Visualisierungsebene nicht im Blueprint verankert
  - Zwei How2-Ausprägungen (DEV / USER) nicht formalisiert

Bezug: [[FREEZE-6_S6]]


1.2 Konkrete Diskrepanz
------------------------
  IST:  Dokumenttypen existierten implizit — jeder DEV kannte sie aus
        der Praxis, aber sie waren nirgends normativ beschrieben.
        Templates waren aus Beta-Kundenprojekten (MLAT) bekannt aber
        nicht für R+MUNI DEV adaptiert und abgelegt.

  SOLL: Vollständige, normative Beschreibung aller Dokumenttypen.
        Verbindliche Templates für jeden Typ.
        Klare Ablage- und Publizierungslogik.
        How2 für DEV zur korrekten Anwendung.


1.3 Auslöser
-------------
Auslöser-Typ: Strukturbereinigung + Dokumentationspflicht (Entwicklerwunsch, GOV 10.3)

Der Sprint entstand aus dem Wunsch Dokumentenstabilität über die Beta hinaus
zu sichern. Mit wachsendem Team und wachsender Kundenbasis werden implizite
Konventionen zur Fehlerquelle. Die TMP-Reihe macht sie explizit.

Zusätzlicher Auslöser: Beta-Erfahrungen aus dem MLAT-Kontext haben gezeigt
dass Templates und Dokumenttypen einen messbaren Beitrag zur Konsistenz
leisten. Dieser Erkenntnistransfer [MLAT→RMUNI] war ein bewusster Auslöser.


================================================================================
2. ENTSCHEIDUNGEN UND GRUNDSÄTZE DIESES SPRINTS
================================================================================

2.1 Kontextaufbau vor Umsetzung — kein Vorauspreschen
-------------------------------------------------------
Entscheidung:
  Der Sprint startete nicht mit sofortiger Dokumenterstellung.
  Zuerst wurde der vollständige Kontext zwischen Betreiber und Claude
  aufgebaut — Dokumenttypen, Repos, Pfade, Benennungen, Ausnahmen.
  Erst nach vollständiger Klärung begann die Umsetzung.

Begründung:
  Vorschnelle Umsetzung ohne Kontextklarheit erzeugt Dokumente die
  nachträglich korrigiert werden müssen. Der Kontextaufbau ist in dieser
  Methodik kein Overhead — er ist die eigentliche Arbeit.

Verworfene Alternativen:
  Alternative: Sofort loslegen, iterativ korrigieren
    Verworfen weil: Strukturdokumente mit falschen Grundannahmen erzeugen
    Folgefehler in allen Dokumenten die auf ihnen aufbauen.

Auswirkung:
  Längere Klärungsphase — dafür kein einziges Korrekturdokument nötig.
  Alle Dokumente entstanden auf Basis vollständiger Entscheidungsgrundlage.


2.2 TMP als Reihenname — keine neue Präfix-Erfindung
------------------------------------------------------
Entscheidung:
  Der Reihenname lautet TMP (für Templates / Dokumenttypen-Reihe).
  Einzelne Dokumenttypen behalten ihre logischen Namen (GOV, principles,
  how2 etc.) — TMP ist nur der Präfix für die Reihen-Dokumente selbst
  (TMP_principles, TMP_How2_DEV).

Begründung:
  Konsistenz mit der bestehenden Logik des Blueprints — logische Namen
  statt generische Präfixe. Die Ordnerstruktur macht die Zuordnung klar.

Verworfene Alternativen:
  Alternative A: DOC als Präfix
    Verworfen weil: zu generisch, kein Erkennungswert
  Alternative B: TMPL als Präfix
    Verworfen weil: Betreiber-Präferenz war TMP


2.3 Zwei How2-Ausprägungen — DEV und USER getrennt
---------------------------------------------------
Entscheidung:
  How2 wird in zwei klar getrennten Ausprägungen geführt:
  DEV (technisch, kompakt) und USER (erklärend, aus Beta-Erfahrungen).
  Beide sind eigenständige Dokumente — kein Mischen.

Begründung:
  DEV und User haben fundamental unterschiedliche Voraussetzungen und
  Informationsbedürfnisse. Ein Dokument das beiden gerecht werden will
  dient keinem gut.

  USER-How2 entsteht aus anonymisierten Beta-Erfahrungen — nicht im
  DEV-Prozess, sondern in der Feedback-Schleife. Dieser Zeitpunkt ist
  bewusst gewählt: erst wenn Erfahrungen vorliegen, nicht auf Vorrat.

Verworfene Alternativen:
  Alternative: Ein How2 mit DEV/USER-Sektionen
    Verworfen weil: Vermischt zwei Perspektiven in einem Dokument —
    widerspricht dem Prinzip "1 Dokument, 1 Thema".

Auswirkung:
  Benennung: <REIHE>_How2_DEV_S<N>.md / <REIHE>_How2_USER_S<N>.md
  TMP_principles_S6 Kapitel 7 aktualisiert.


2.4 Sprint-DEV-Doku hat volle Tiefe — nicht schlanker Nachweis
----------------------------------------------------------------
Entscheidung:
  Die Sprint-DEV-Doku ist explizit als vollständiges Arbeitsgedächtnis
  definiert — nicht als schlankes Nachweis-Dokument wie beim MLAT-Kunden.
  Script-Inhalte, Mermaid-Diagramme und Creative-Asset-Verlinkungen
  sind ausdrücklich erwünscht.

Begründung:
  Ein DEV-Mitglied muss diesen Sprint in einem Jahr ohne Rückfragen
  nachvollziehen können. Schlanke Dokumente erfüllen diesen Anspruch nicht.
  Die Tiefe skaliert mit der Komplexität — ein Bugfix ist kürzer,
  eine neue Reihe braucht volle Tiefe.

Verworfene Alternativen:
  Alternative: Einheitlich schlanke Sprint-Dokus wie beim Kunden
    Verworfen weil: DEV-Anforderungen an Nachvollziehbarkeit sind
    fundamental höher als User-Anforderungen.


2.5 Obsidian als explizit unterstützte Visualisierungsebene
------------------------------------------------------------
Entscheidung:
  Obsidian wird als optionale aber explizit unterstützte Visualisierungs-
  ebene im Blueprint verankert. Obsidian-Links in .md Dokumenten sind
  zulässig und erwünscht. .obsidian/ bleibt in .gitignore.

Begründung:
  EA-Modell-Ordnerstrukturen für Dokumentbezüge sind wartungsintensiv
  und schwer navigierbar. Obsidian löst dasselbe Problem auf File-Ebene —
  ohne zusätzliche Werkzeuge und vollständig GitHub-kompatibel.

Verworfene Alternativen:
  Alternative: Dokumentbezüge in EA-Modell abbilden
    Verworfen weil: Overhead, Werkzeugabhängigkeit, schwer skalierbar.
  Alternative: Keine explizite Verlinkung — nur Textverweise
    Verworfen weil: Nicht navigierbar, nicht visuell auswertbar.

Auswirkung:
  TMP_principles_S6 Kapitel 16 — Obsidian-Option vollständig dokumentiert.
  Alle Templates enthalten Obsidian-Link-Platzhalter.


2.6 FREEZE_Template auf Abruf — nicht im regulären Lauf
--------------------------------------------------------
Entscheidung:
  Das FREEZE_Template_S6.md wird nicht im regulären Template-Durchlauf
  erstellt. Es wird auf dedizierten Wunsch des Betreibers oder am
  Stage-Ende erstellt.

Begründung:
  Freeze-Dokumente entstehen selten und kontextspezifisch. Ein Template
  auf Vorrat erzeugt keinen Mehrwert der den Aufwand rechtfertigt.

Auswirkung:
  Template-Liste: FREEZE_Template_S6.md — Status ⏸ auf Abruf.


2.7 Info und Creative ohne Template
------------------------------------
Entscheidung:
  Type 9 (Info) und Type 10 (Creative) erhalten kein verbindliches
  Template — Format ist frei.

Begründung:
  Beide Typen dienen als Auffangbecken für Inhalte die keiner festen
  Struktur folgen können oder sollen. Ein Template würde den Zweck
  dieser Typen aushöhlen.


================================================================================
3. SPRINT-ZIELE UND UMSETZUNG
================================================================================

3.1 Ziel 1 — TMP_principles_S6.md erstellen
---------------------------------------------
Vollständige normative Beschreibung aller 10 Dokumenttypen in einem Dokument.

Umfang:
  17 Kapitel
  Kapitel 1–2:   Designphilosophie und Grundregeln
  Kapitel 3:     Repo- und Ablagelogik (alle drei Repos)
  Kapitel 4:     Übersicht aller 10 Typen
  Kapitel 5–14:  Jeder Typ einzeln — Zweck, Charakter, Benennung,
                 Ablage, Publizierung, Template-Referenz
  Kapitel 15:    Lebenszyklus (Entwurf → Cleaning Run → Archiv)
  Kapitel 16:    Obsidian-Option
  Kapitel 17:    Abgrenzung

Korrekturen während Umsetzung:
  - Kapitel 11 (Type 7) nach erstem Entwurf korrigiert:
    Schlanker Nachweis → Vollständiges Arbeitsgedächtnis (→ Entscheidung 2.4)
  - Kapitel 7 (Type 3) nach How2-Ausprägungsentscheidung aktualisiert:
    Ein Template → Zwei Templates DEV/USER (→ Entscheidung 2.3)
  - Kapitel 16 hinzugefügt nach Obsidian-Entscheidung (→ Entscheidung 2.5)

Ergebnis: [[TMP_principles_S6]]  ✅


3.2 Ziel 2 — Templates für alle verbindlichen Typen erstellen
--------------------------------------------------------------
8 Templates — je eines pro Dokumenttyp mit verbindlicher Struktur.

Reihenfolge der Erstellung (Betreiber-Entscheidung):
  1. principles_Template_S6.md       ✅
  2. how2_DEV_Template_S6.md         ✅
  3. how2_USER_Template_S6.md        ✅
  4. GOV_Global_Template_S6.md       ✅
  5. Rosetta-Stone_Template_S6.md    ✅
  6. Stage_Ziele_Template_S6.md      ✅
  7. Sprint-DEV-BACKLOG_Template_S6.md  ✅
  8. Sprint-DEV-Doku_Template_S6.md  ✅

Nicht erstellt (bewusst):
  FREEZE_Template_S6.md              ⏸  auf Abruf
  Info_Template                      —  kein Template, Format frei
  Creative_Template                  —  kein Template, Format frei

Jedes Template enthält:
  - DEV-Hinweisblock mit Spielregeln (wird im fertigen Dokument entfernt)
  - Alle Pflichtkapitel des Typs
  - Optionale Kapitel mit expliziter Kennzeichnung
  - Obsidian-Link-Platzhalter wo sinnvoll
  - Mermaid-Platzhalter wo für den Typ relevant


3.3 Ziel 3 — TMP_How2_DEV_S6.md erstellen
-------------------------------------------
Schlanke, direkte Anleitung für DEV zur korrekten Anwendung der Templates.

7 Schritte:
  1. Dokumenttyp bestimmen — Entscheidungstabelle mit Zweifelsfällen
  2. Template öffnen — Tabelle Type→Template, Original nie bearbeiten
  3. Datei benennen — Konvention je Typ mit Beispiel
  4. Ausfüllen — Reihenfolge, Pflichtregeln, typische Fehler
  5. In Arbeit verwalten — Ablageort, Versionierung
  6. Freigabe und Publizierung — Prozess, Zielordner je Typ
  7. Jira-Sync — nur Type 8

Bewusst schlank gehalten: keine USER-How2 in diesem Sprint.
Begründung: USER-How2 entsteht aus Beta-Erfahrungen — der richtige
Zeitpunkt ist nach etabliertem Betrieb, nicht auf Vorrat.

Ergebnis: [[TMP_How2_DEV_S6]]  ✅


================================================================================
4. ABGRENZUNG — WAS DIESER SPRINT NICHT TUT
================================================================================

Dieser Sprint tut explizit nicht:
  - Keine USER-How2 für die TMP-Reihe — kommt aus Beta-Erfahrungen
  - Kein FREEZE_Template — auf Abruf
  - Keine Kundenseitige Dokumenttypen-Definition — eigenes Paket
  - Keine Anpassung bestehender Principles oder How2 auf neues Format
    (bestehende Dokumente bleiben wie sie sind — Cleaning Run macht das)
  - Keine Obsidian-Konfiguration oder Vault-Setup — nur Verankerung im Blueprint
  - Kein Jira-Ticket für diesen Sprint selbst — Backlog-Sync nur für Type 8

Wichtigster Ausschluss — Kundenseitige Templates:
  Die MLAT Beta-Kunden haben bereits funktionierende Templates und
  eine eigene Sync-Logik. Diese werden in einem separaten Arbeitspaket
  besprochen und dokumentiert — nach Fertigstellung der DEV-Seite.


================================================================================
5. BETROFFENE ARTEFAKTE
================================================================================

Neu erstellt:
  TMP_principles_S6.md               Normatives Principles-Dokument der TMP-Reihe
  principles_Template_S6.md          Template für Typ 2
  how2_DEV_Template_S6.md            Template für Typ 3 DEV
  how2_USER_Template_S6.md           Template für Typ 3 USER
  GOV_Global_Template_S6.md          Template für Typ 1
  Rosetta-Stone_Template_S6.md       Template für Typ 4
  Stage_Ziele_Template_S6.md         Template für Typ 6
  Sprint-DEV-BACKLOG_Template_S6.md  Template für Typ 8
  Sprint-DEV-Doku_Template_S6.md     Template für Typ 7
  TMP_How2_DEV_S6.md                 How2 für DEV zur Template-Anwendung
  Sprint-DEV-Doku_TMP-Reihe_S6.md   Dieses Dokument

Geändert:
  Keine bestehenden Dokumente geändert.

Unverändert (relevant zu erwähnen):
  Global_GOV_S5.md      kein Eingriff — TMP-Reihe ist additiv
  Alle Script-Reihen    kein Eingriff
  FREEZE-6              kein Eingriff — bleibt gültige Baseline


================================================================================
6. BEOBACHTUNGEN WÄHREND DER UMSETZUNG
================================================================================

6.1 MLAT-Referenzmaterial als Orientierung
-------------------------------------------
Der Betreiber stellte MLAT-Dokumente als Referenz bereit (Modus 1 —
kein automatischer Transfer). Die MLAT-Templates (FREEZE, Sprint, How2, GOV)
dienten als Qualitäts- und Stil-Referenz. Der Transfer war explizit
kontrolliert — keine MLAT-Strukturdetails wurden direkt übernommen.

Erkenntnis: Die MLAT-Seite ist bereits weiter als erwartet. Die DEV-Seite
holt mit diesem Sprint strukturell nach — und geht in Tiefe (Sprint-DEV-Doku)
deutlich über die Kundenseite hinaus.


6.2 Iterative Korrektur an TMP_principles
------------------------------------------
Type 7 (Sprint-DEV-Doku) war im ersten Entwurf zu nah an der Kunden-
perspektive — schlanker Nachweis statt vollständiges Arbeitsgedächtnis.
Korrektur nach Betreiber-Feedback: Kapitel 11 vollständig neu geschrieben.

Erkenntnis: Der Unterschied DEV vs. User ist nicht nur Stil — er ist
fundamental. DEV braucht Tiefe, der Kunde braucht Klarheit.


6.3 Obsidian — nicht geplant, aber logisch
-------------------------------------------
Obsidian als Visualisierungsebene war kein geplanter Sprint-Inhalt.
Es entstand organisch aus der Diskussion über Dokumentbezüge und
EA-Modell-Overhead. Die Entscheidung fiel während des Sprints —
und wurde sofort in TMP_principles Kapitel 16 verankert.

Erkenntnis: Gute Sprints haben Raum für Erkenntnisse die während der
Arbeit entstehen — solange sie dokumentiert und explizit entschieden werden.


================================================================================
7. ERGEBNIS
================================================================================

7.1 Erreichter Zustand
-----------------------
R+MUNI Blueprint hat jetzt eine vollständige, normative TMP-Reihe:

  - Alle 10 Dokumenttypen explizit definiert
  - 8 verbindliche Templates erstellt und abgelegt
  - Ablage- und Publizierungslogik für alle Typen normativ festgelegt
  - Benennungskonvention dokumentiert und mit Beispielen versehen
  - Obsidian als Visualisierungsebene im Blueprint verankert
  - How2 für DEV zur Template-Anwendung vorhanden
  - Zwei How2-Ausprägungen (DEV/USER) formal definiert

Die TMP-Reihe ist vollständig eigenständig lesbar ohne Kenntnis
anderer interner Entwicklungsdokumente.


7.2 Abweichungen vom Plan
--------------------------
Keine wesentlichen Abweichungen.

Korrekturen innerhalb des Sprints:
  - Type 7 Tiefendefinition: schlanker → vollständig (→ 6.2)
  - How2 Ausprägung: ein Template → zwei Templates (→ Entscheidung 2.3)
  - Obsidian: nicht geplant → explizit verankert (→ 6.3)

Alle Korrekturen wurden im Sprint selbst umgesetzt — kein offener
Korrekturbestand nach Abschluss.


================================================================================
8. TEST UND VALIDIERUNG
================================================================================

| Prüfpunkt                                              | Ergebnis | Anmerkung                        |
|--------------------------------------------------------|----------|----------------------------------|
| TMP_principles_S6 vollständig — alle 10 Typen         | OK       | 17 Kapitel                       |
| Alle 8 Templates erstellt und abgelegt                 | OK       | Betreiber hat je abgenommen      |
| Benennungskonvention in TMP_principles und How2 konsistent | OK   | Gegengeprüft                     |
| Obsidian-Option in Principles und Templates verankert  | OK       | Kapitel 16 + Link-Platzhalter    |
| How2 DEV vorhanden und vollständig                     | OK       | 7 Schritte                       |
| Kein Eingriff in bestehende Scripts oder GOV           | OK       | Additiver Sprint                  |
| Keine Platzhalter in finalen Dokumenten                | OK       | Betreiber-Abnahme je Dokument    |
| Stage-3/4-Scripts logisch unverändert                  | OK       | Kein Script berührt              |
| MLAT-Anonymisierung eingehalten                        | OK       | Modus 1 — kein unerlaubter Transfer |


================================================================================
9. OFFENE PUNKTE NACH SPRINT-ABSCHLUSS
================================================================================

| Thema                              | Status           | Nächste Aktion                              |
|------------------------------------|------------------|---------------------------------------------|
| FREEZE_Template_S6.md              | Auf Abruf        | Auf dedizierten Wunsch oder Stage-Ende      |
| USER-How2 für TMP-Reihe            | Zurückgestellt   | Nach etabliertem Betrieb aus Beta-Erfahrungen |
| Kundenseitige Templates + Sync     | Eigenes Paket    | Separates Arbeitspaket — Betreiber-Entscheidung |
| Bestehende Dokumente auf neues Format | Cleaning Run  | Vor Beta 1.0 Release                        |
| Obsidian Vault-Setup               | Nicht hier       | Optional — Betreiber entscheidet wann       |


================================================================================
10. GOVERNANCE-KONFORMITÄTSCHECK
================================================================================

| GOV-Kriterium                              | Status | Anmerkung                              |
|--------------------------------------------|--------|----------------------------------------|
| GOV 10.3  Auslöser zulässig               | OK     | Strukturbereinigung + Dokumentationspflicht |
| GOV 10.5  Fachlicher Mehrwert benennbar   | OK     | Dokumentenstabilität über Beta hinaus  |
| GOV 10.5  Keine implizite GOV-Änderung    | OK     | Additiver Sprint — kein GOV-Eingriff   |
| GOV 10.6  Ziel explizit definiert         | OK     | Kapitel 3                              |
| GOV 10.6  Ziel überprüfbar               | OK     | Kapitel 8                              |
| GOV 10.7  Zwischenschritte dokumentiert   | OK     | Kapitel 3 + Beobachtungen Kapitel 6   |
| GOV 10.8  Dev-Doku vollständig            | OK     | Dieses Dokument                        |
| GOV 10.9  Stage-Ende Doku                 | OFFEN  | Fällig bei Stage-6-Gesamtabschluss    |
| GOV 10.10 Keine GOV-Regel aufgehoben      | OK     | Keine GOV-Änderung in diesem Sprint   |
| Rückkopplungsschutz eingehalten           | OK     | Stage-3/4 unberührt                   |
| GOV 13    Rollentrennung MLAT/DEV         | OK     | Modus 1 eingehalten, kein Auto-Transfer |


================================================================================
11. LESSONS LEARNED
================================================================================

11.1 Was gut funktioniert hat
------------------------------
  - Vollständiger Kontextaufbau vor Umsetzungsstart — kein Korrekturdokument nötig
  - Betreiber-Abnahme je Dokument sofort nach Erstellung — kein Rückstau
  - Iterative Korrektur innerhalb des Sprints ohne Qualitätsverlust
  - Trennung DEV/USER von Anfang an als Strukturprinzip — zahlt sich aus
  - MLAT-Referenzmaterial als Qualitätsanker ohne Rollenvermischung

11.2 Was beim nächsten Mal anders gemacht werden sollte
--------------------------------------------------------
  - Obsidian-Verankerung früher im Sprint explizit thematisieren —
    nicht erst wenn es organisch auftaucht
  - Für große Template-Serien: Reihenfolge der Templates vorab gemeinsam
    festlegen statt iterativ entscheiden

11.3 Erkenntnisse für das System
----------------------------------
  - Implizite Konventionen sind die häufigste Fehlerquelle beim Onboarding
    neuer DEV-Mitglieder → TMP-Reihe adressiert das direkt
    Konsequenz: Bei jedem neuen Onboarding TMP_principles_S6 als
    Pflichtlektüre einplanen

  - DEV-Dokumentationstiefe und User-Dokumentationstiefe sind fundamental
    verschieden — nicht nur graduell
    Konsequenz: Beide Ausprägungen (DEV/USER) immer als eigenständige
    Dokumente planen — nie in einem Dokument vermischen

  - Obsidian-Graph als Navigationswerkzeug wird mit wachsender Dokumentenbasis
    zunehmend wertvoller
    Konsequenz: Obsidian-Links konsequent setzen ab jetzt — rückwirkend
    beim Cleaning Run nachziehen


================================================================================
12. BEZÜGE UND VERLINKUNGEN
================================================================================

Ausgangspunkt:
  [[FREEZE-6_S6]]                      Baseline für diesen Sprint

Entstanden in diesem Sprint:
  [[TMP_principles_S6]]                Normatives Principles-Dokument
  [[TMP_How2_DEV_S6]]                  How2 für DEV
  principles_Template_S6.md
  how2_DEV_Template_S6.md
  how2_USER_Template_S6.md
  GOV_Global_Template_S6.md
  Rosetta-Stone_Template_S6.md
  Stage_Ziele_Template_S6.md
  Sprint-DEV-BACKLOG_Template_S6.md
  Sprint-DEV-Doku_Template_S6.md

Normative Grundlage:
  [[GOV_Global_S6]]                    insbesondere Kapitel 10 + 13

Referenz (Modus 1 — MLAT, nicht transferiert):
  FREEZE_Template_MLAT_S1.md
  Sprint-Templates_MLAT_S1.md
  How2_Template_MLAT_S1.md
  GOV_MLAT_S2.md

Creative-Assets:
  Keine Creative-Assets für diesen Sprint.


================================================================================
Sprint-DEV-TMP-Reihe | S6 | 2026-03-18 | R+MUNI Blueprint
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
