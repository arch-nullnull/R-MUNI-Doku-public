================================================================================
SPRINT-DEV-DOKU – S6-Z3 STAGE-BEZEICHNUNG IN BETA-DOKUMENTEN
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : Sprint-DEV-S6-Z3-StageBezeichnung
Datum               : 2026-03-21
Stage               : S6 – AKTIV
Status              : Abgeschlossen — Implementierung dokumentiert
Erstellt durch      : EUMAXL + Claude (Pair-Session)
Vorgänger           : STAGE6_ZIELE.md
Nachfolger          : Zukünftige Feature DokuReview_AutoScript (siehe Backlog)

================================================================================
1. AUSGANGSLAGE UND KONTEXT
================================================================================

1.1 Ist-Zustand vor diesem Sprint
-----------------------------------
S6-Z3 war ein Ziel definiert in STAGE6_ZIELE.md, hatte aber noch keine
Implementierung. Externe Leser (Beta-Kunden, Stakeholder) konnten nicht
erkennen welche Dokumente in Beta-Status waren.

Relevante Artefakte vor dem Sprint:
  - STAGE6_ZIELE.md                     Status: definiert (Ziel S6-Z3 formuliert)
  - Bestehende Beta-Dokumente           Status: unmarkiert, kein Erkennungszeichen


1.2 Konkrete Diskrepanz oder Problemstellung
---------------------------------------------
  IST:  Beta-Dokumente haben keine Markierung ob sie Produktivstatus oder
        Beta-Status haben. Externe Leser wissen nicht ob ein Dokument
        zuverlässig ist oder noch überarbeitet werden kann.

  SOLL: Alle Beta-Dokumente erhalten eine sichtbare Stage-Kennung (_S6)
        im Header, sodass die Betaness sofort erkennbar ist.


1.3 Auslöser
-------------
Auslöser-Typ: Feature (GOV-Konformität und externe Transparenz)

Zweck: S6-Z3 Ziel aus STAGE6_ZIELE.md umsetzen.
Pragmatischer Ansatz gewählt: Manuelle Markierung jetzt, automatisiertes
Skript später (Backlog).

================================================================================
2. ENTSCHEIDUNGEN UND GRUNDSÄTZE DIESES SPRINTS
================================================================================

2.1 Format: Einfach nur _S6 ohne Subversionen
---------------------------------------------
Entscheidung:
  Stage-Kennung ist fix _S6 (keine Subversionen wie _S6.1, _S6.2 etc.)
  Versionshistorie über Archivierung steuern (Entwickler kopiert alte
  Versionen ins Archiv-Ordner wenn Dokument ersetzt wird)

Begründung:
  - Einfach und wartbar — keine Increment-Logik notwendig
  - Passt zu EUMAXL Arbeitsweise (pragmatisch, keine Automatisierung jetzt)
  - Alte Versionen sind trotzdem dokumentiert (manuell im Archiv)
  - Fokus bleibt auf Transparenz (Beta vs. Produktiv), nicht auf Versionierung

Verworfene Alternativen:
  Alternative A: _S6.0, _S6.1, _S6.2 pro Review-Zyklus
    Verworfen weil: Zu komplex für Stage 6, manuelle Inkremente fehlerträchtig,
    Nutzen gering (Alte Versionen sind sowieso archiviert)
  Alternative B: Automatisiertes Versionssystem sofort
    Verworfen weil: Overkill für Stage 6, Script-Setup ist Backlog-Feature

Auswirkung:
  Einfachere Dokumentation im Header-Block
  Weniger Fehlerquellen bei manueller Markierung
  Backlog-Feature DokuReview_AutoScript bleibt fokussiert


2.2 Platzierung: Im Header-Block neben anderen Metadaten
---------------------------------------------------------
Entscheidung:
  Stage-Kennung (_S6) steht im standardisierten Header-Block aller
  Beta-Dokumente, auf gleicher Ebene wie "Dokumenttyp", "Status", "Datum".
  Nicht versteckt, nicht optional.

Begründung:
  - Sichtbarkeit ist das Ziel (GOV 4.3)
  - Header-Block ist Standard-Platzierung (Template-Konvention)
  - Externe Leser sehen es sofort — kein Suchen notwendig

Auswirkung:
  Alle neuen Dokumente müssen Stage-Kennung im Header haben
  Bestehende Dokumente schrittweise nachziehen (optional, kein Blocker)


2.3 Kein Review-Feld im Header — nur "Letzte Änderung"
-------------------------------------------------------
Entscheidung:
  Es gibt kein separates "Letzte Review" Feld (wurde ursprünglich geplant,
  entfällt jetzt). Nur "Letzte Änderung" wird gepflegt.
  Ein Review ist implizit wenn der Inhalt überprüft und aktualisiert wurde.

Begründung:
  - Einfacher: nur ein Datum zu verwalten
  - Review ist kein separater Prozess sondern Teil der Überarbeitung
  - Komplexität sinkt, Zuverlässigkeit steigt

Verworfene Alternativen:
  Separate "Letzte Review" Feld
    Verworfen weil: Zwei Daten sind schwerer zu verwalten, Review ist
    oft implizit in der Überarbeitung enthalten

Auswirkung:
  Weniger Felder im Header
  Workflowt vereinfacht sich


2.4 Obsidian und Kompexe Automation erst in Zukunft
----------------------------------------------------
Entscheidung:
  Das ursprünglich in STAGE6_ZIELE.md als S6-Z4 geplante "Obsidian für
  Zusammenhänge" und die DokuReview_AutoScript sind nicht Teil dieses Sprints.
  Sie gehen ins Backlog.

Begründung:
  - S6-Z3 ist nur die Markierung, nicht die Verwaltung
  - Manuell funktioniert jetzt zuverlässig
  - Automation und Obsidian-Integration später wenn Bedarf größer wird

Auswirkung:
  S6-Z3 ist mit manueller Implementierung vollständig
  DokuReview_AutoScript und Obsidian sind Backlog-Einträge


================================================================================
3. SPRINT-ZIELE
================================================================================

3.1 Ziel 1 — S6-Z3 Dokumentation und Format definieren
--------
Klare Beschreibung:
  Es soll ein standardisiertes, dokumentiertes Format für die Stage-Kennung
  _S6 definiert werden. Das Format muss so einfach sein dass es jeder
  Entwickler ohne Fehler anwenden kann.

  IST                    →  SOLL
  Keine Markierung       →  Alle Beta-Docs haben _S6 im Header
  Verwirrung aussen      →  Externe Leser erkennen sofort: Beta-Status

Vorgehen:
  1. Format definieren: _S6 im Header-Block
  2. Platzierung spezifizieren: zwischen anderen Metadaten
  3. Workflow dokumentieren: Was macht Entwickler wann (neues Dok, Überarbeitung)
  4. Konkrete Beispiele geben

Begründung für dieses Vorgehen:
  - Dokumentation ist Voraussetzung für zuverlässige Anwendung
  - Konkrete Beispiele vermeiden Interpretationsspielraum
  - Workflow zeigt den praktischen Weg


3.2 Ziel 2 — Review-Schleife definieren
--------
Klare Beschreibung:
  Der Prozess für Review von Beta-Dokumenten soll dokumentiert werden.
  Review ist optional, wird von Entwickler entschieden, hat aber
  klare Schritte wenn es durchgeführt wird.

Vorgehen:
  1. Review-Schleife als Prozess beschreiben (Lesbar, Aktuell, Konsistent)
  2. Rhythmus definieren (keine festen Daten, nach Bedarf)
  3. Verantwortung klären (Entwickler entscheidet)
  4. Output dokumentieren (aktualisiertes Dokument, Notiz)


3.3 Ziel 3 — Backlog-Eintrag DokuReview_AutoScript erstellen
---------
Klare Beschreibung:
  Die Idee eines automatisierten Scripts (DokuReview_AutoScript) soll
  als Backlog-Eintrag dokumentiert werden sodass es später umgesetzt
  werden kann. Das Script soll automatisch prüfen welche Dokumente
  veraltet sind.

Vorgehen:
  1. Script-Idee spezifizieren
  2. Konfiguration skizzieren (review_interval_days)
  3. Output-Format definieren (Bericht mit Status der Dokumente)
  4. Abhängigkeiten festhalten
  5. Als Backlog-Eintrag ins STAGE6_BACKLOG_SPRINTS.md eintragen


================================================================================
4. ABGRENZUNG — WAS DIESER SPRINT NICHT TUT
================================================================================

Dieser Sprint tut explizit nicht:
  - Automatische Versionskontrolle implementieren
  - Obsidian-Vault aufbauen oder MD-Links erstellen
  - Alle bestehenden Dokumente nachträglich markieren
  - Review-Zwang für Beta-Dokumente einführen
  - Architektur für automatische Reviews schaffen
  - Komplexe Governance-Erweiterung in der GOV

Die Automation und das Obsidian-Setup sind bewusst Backlog-Features.
Diesen Sprint durchzuführen macht S6-Z3 AKTIV — nicht perfekt.


================================================================================
5. BETROFFENE ARTEFAKTE
================================================================================

Neu erstellt:
  Sprint-DEV-Doku_S6-Z3_StageBezeichnung.md
                                           Dokumentation des Sprints (dieses Dok)
  STAGE6_BACKLOG_SPRINTS.md                Backlog für geplante Sprints + Features

Geändert:
  STAGE6_ZIELE.md                          S6-Z3 Status aktualisieren (Implementiert)

Unverändert (relevant zu erwähnen):
  Global_GOV_S5.md                         GOV 4.3 ist bereits definiert,
                                           keine Erweiterung nötig
  FREEZE-6.md                              Baseline bleibt stabil


================================================================================
6. UMSETZUNG — SCHRITT FÜR SCHRITT
================================================================================

Schritt 1 — Format definieren und dokumentieren
  Was konkret getan wird:
    - Header-Block-Struktur spezifizieren
    - Stage-Kennung Platzierung festlegen
    - Beispiele konkret aufschreiben
  
  Ergebnis:
    Klares Format dass Entwickler ohne Rückfragen anwenden kann


Schritt 2 — Workflow für Entwickler dokumentieren
  Was konkret getan wird:
    - Szenario 1: Neues Dokument anlegen
    - Szenario 2: Bestehendes Dokument überarbeiten
    - Szenario 3: Dokument wird ersetzt/archiviert
  
  Begründung der Reihenfolge:
    Neue Docs sind das häufigste Szenario → zuerst
    Überarbeitung ist der tägliche Fall → zweiter
    Archivierung ist selten → dritter
  
  Ergebnis:
    Entwickler weiß genau was zu tun ist in jedem Fall


Schritt 3 — Review-Schleife als optionaler Prozess definieren
  Was konkret getan wird:
    - Was ein Review bedeutet
    - Rhythmus (optional, nach Bedarf)
    - Verantwortung klar machen
    - Was aus einem Review entsteht
  
  Ergebnis:
    Review ist dokumentiert aber kein erzwungener Prozess


Schritt 4 — Backlog-Eintrag für DokuReview_AutoScript erstellen
  Was konkret getan wird:
    - Script-Idee dokumentieren
    - Konfiguration skizzieren
    - Output-Format zeigen
    - Abhängigkeiten beschreiben
  
  Ergebnis:
    Idea ist konserviert, kann später umgesetzt werden
    Keine Verlust von Gedanken


Schritt 5 — Dokumentation in S6-Z3 Sprint-DEV-Doku zusammenfassen
  Was konkret getan wird:
    - Dieses Dokument schreiben
    - GOV-Konformität prüfen
    - Bezüge setzen
  
  Ergebnis:
    Sprint ist vollständig dokumentiert


================================================================================
7. BEOBACHTUNGEN UND ERKENNTNISSE WÄHREND DER UMSETZUNG
================================================================================

7.1 Pragmatisches Format ist robuster als Komplexität
------
  Beobachtung:
    Während der Planung waren Subversionen (_S6.1, _S6.2) angedacht.
    In der Dokumentation wurde schnell klar: Das macht keinen Sense für
    Stage 6 wenn der Fokus auf Transparenz (Beta vs Produktiv) liegt.
  
  Auswirkung:
    Format ist jetzt simpler und fehlertoleranter.
    Alte Versionen werden manuell archiviert — ist ohnehin die Realität.
  
  Dokumentiert: Ja — in Entscheidung 2.1


7.2 Review ist implizit, nicht explizit nötig
------
  Beobachtung:
    Die ursprüngliche Planung hatte "Letzte Review" als separates Feld.
    Praktisch zeigt sich: Review ist oft Teil der Überarbeitung.
    Zwei separate Daten zu verwalten ist fehlerträchtig.
  
  Auswirkung:
    Workflow vereinfacht sich.
    Ein Feld ("Letzte Änderung") ersetzt zwei.
  
  Dokumentiert: Ja — in Entscheidung 2.3


================================================================================
8. ERGEBNIS
================================================================================

8.1 Erreichter Zustand
-----------------------
S6-Z3 ist mit einer manuellen, pragmatischen Implementierung umgesetzt.

Entstandene Artefakte:
  - Sprint-DEV-Doku_S6-Z3_StageBezeichnung.md   Dieses Dokument
  - STAGE6_BACKLOG_SPRINTS.md                   Backlog mit DokuReview_AutoScript

Geänderter Systemzustand:
  - Format für Beta-Dokument-Markierung ist definiert
  - Workflow ist dokumentiert
  - Externe Leser können ab sofort erkennen: Dieser Doc ist Beta

Entstandenes Wissen:
  - Warum das Format so gewählt wurde (für Zukunfts-Entwickler)
  - Wo die Grenzen sind (keine Automation, noch nicht)
  - Was die nächsten Schritte sind (DokuReview_AutoScript Backlog)


8.2 Abweichungen vom Plan
--------------------------
Keine wesentlichen Abweichungen.
  - Ursprüngliches Plan: Manuell implementieren ✓ Umgesetzt
  - Review-Schleife definieren ✓ Umgesetzt
  - Backlog-Eintrag für Automation ✓ Umgesetzt


================================================================================
9. TEST UND VALIDIERUNG
================================================================================

| Prüfpunkt                                    | Ergebnis      | Anmerkung               |
|----------------------------------------------|---------------|-------------------------|
| Format _S6 ist einfach und fehlerarm         | OK            | Keine Subversionen     |
| Platzierung im Header ist sichtbar           | OK            | Standard-Platzierung    |
| Workflow ist dokumentiert (3 Szenarien)      | OK            | Praktische Anwendung    |
| Review-Schleife optional definiert           | OK            | Nicht erzwungen         |
| Backlog-Eintrag DokuReview ist spezifiziert | OK            | Zukünftige Automation   |
| GOV 4.3 Anforderung erfüllt                  | OK            | Transparenz hergestellt |
| Extern: Beta-Status erkennbar                | OK            | _S6 im Header visible   |

Testmethode:
  - Dokumente durchgelesen und Format angewandt
  - Workflow praktisch durchgespielt (neues Dok, Überarbeitung, Archivierung)
  - GOV-Anforderungen gegengeprüft
  - Externe Lesbarkeit geprüft


================================================================================
10. OFFENE PUNKTE NACH SPRINT-ABSCHLUSS
================================================================================

| Thema                    | Status                        | Nächste Aktion                    |
|--------------------------|-------------------------------|-----------------------------------|
| DokuReview_AutoScript    | Backlog                       | Sprint-DEV-BACKLOG_DokuReview_S6 |
| Obsidian-Setup           | Backlog (S6-Z4)               | Zukünftiger Sprint                |
| Bestehende Docs markieren| Optional                      | Laufend nachziehen bei Änderung  |
| Archive-Struktur        | Informal definiert            | Nach Bedarf formalisieren         |


================================================================================
11. GOVERNANCE-KONFORMITÄTSCHECK
================================================================================

| GOV-Kriterium                              | Status      | Anmerkung                      |
|--------------------------------------------|-------------|--------------------------------|
| GOV 10.3  Auslöser zulässig               | OK          | Feature (Z3 umsetzen)          |
| GOV 10.5  Fachlicher Mehrwert benennbar   | OK          | Transparenz für externe Leser  |
| GOV 10.5  Keine implizite GOV-Änderung    | OK          | Nur Markierung, keine Logik    |
| GOV 10.6  Ziel explizit definiert         | OK          | Kapitel 3 definiert            |
| GOV 10.6  Ziel überprüfbar               | OK          | Kapitel 9 validiert            |
| GOV 10.7  Zwischenschritte dokumentiert   | OK          | Kapitel 6 Schritte             |
| GOV 10.8  Dev-Doku vollständig            | OK          | Dieses Dokument               |
| GOV 10.9  Stage-Ende Doku                 | OFFEN       | Fällig bei Stage-6-Abschluss   |
| GOV 10.10 Keine GOV-Regel aufgehoben      | OK          | Keine aufgehoben              |
| Rückkopplungsschutz eingehalten           | OK          | Stage-3/4 unberührt            |
| GOV 4.3 Stage-Bezeichnung erfüllt         | OK          | Transparenzmittel etabliert    |


================================================================================
12. LESSONS LEARNED
================================================================================

12.1 Was gut funktioniert hat
------------------------------
  - Pragmatisches Format ohne Subversionen ist wartbarer
  - Manuell umgesetzt in Stage 6 ist für Beta-Umgebung angemessen
  - Backlog-Eintrag konserviert die Automation-Idee ohne zu überlasten
  - Dokumentation macht die Entscheidungen nachvollziehbar


12.2 Was beim nächsten Mal anders gemacht werden sollte
--------------------------------------------------------
  - Keine wesentlichen Verbesserungen — Sprint war straightforward
  - Evtl: Template-basiert von Anfang an (das hätte Zeit gespart)


12.3 Erkenntnisse für das System
----------------------------------
  - Pragmatismus schlägt Perfektion in Beta-Phasen
  - Manuelle Prozesse können robust sein wenn dokumentiert
  - Backlog ist Tool um Ideen zu parken ohne sie zu vergessen


================================================================================
13. BEZÜGE UND VERLINKUNGEN
================================================================================

Ausgangspunkt:
  STAGE6_ZIELE.md                  Z3 Ziel definiert
  Global_GOV_S5.md                 GOV 4.3 Anforderung

Entstanden:
  STAGE6_BACKLOG_SPRINTS.md        Backlog mit DokuReview_AutoScript

Verwandte Dokumente:
  FREEZE-6.md                      aktuelle Baseline
  AI_DRIVEN_DEV_METHODE_S6.md      Entwicklungsmethode

Zukünftig abhängig:
  Sprint-DEV-BACKLOG_DokuReview_AutoScript_S6  wenn Automation gestartet wird


================================================================================
Sprint-DEV-Doku_S6-Z3_StageBezeichnung | S6 | 2026-03-21 | R+MUNI Blueprint
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
