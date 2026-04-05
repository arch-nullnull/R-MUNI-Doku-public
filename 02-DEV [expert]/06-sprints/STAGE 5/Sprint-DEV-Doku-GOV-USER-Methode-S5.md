================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-GOV-USER-Methode-S5 — GOV Kap.13 + AI_DEV Kap.11-13 + USER-Reihe
Datum               : 2026-03-18
Stage               : 5 (aktiv)
Status              : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch      : Entwickler + Claude (Pair-Session)
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Feature-Zuwachs (Stage-5-Erweiterung)

Begründung   : Der Entwickler agiert in mehreren Rollen gleichzeitig —
               als R+MUNI DEV und als Beta-Tester in einer externen
               Atlassian-Umgebung. Erkenntnisse aus der Beta-Rolle sind
               wertvoll für R+MUNI, aber ohne strukturierten Kanal besteht
               das Risiko von Rollenvermischung und unkontrolliertem
               Wissenstransfer.

               Gleichzeitig fehlten bislang:
               - Governance-Regeln für externe Erkenntnisquellen
               - Eine methodische Erweiterung der AI Driven Dev Methode
                 für den Rollen-Parallelbetrieb
               - Eine anwenderorientierte Dokumentationsreihe (USER)
               - Eine verbindliche User/Kunden-Terminologie in der GOV

               Dieser Sprint schafft das vollständige Fundament für
               kontrollierten, sauberen Wissenstransfer von extern nach
               intern und von intern nach public.

Fachlicher   : Strukturierter Kanal für externe Erkenntnisse.
Mehrwert       Rollentrennung methodisch und governance-seitig verankert.
               Anwenderorientierte Dokumentation als Blueprint-Bestandteil.
               Klare Terminologie: User = gratis, Kunde = Service-Käufer.


1.2 Umfang dieses Sprints
--------------------------
Dieser Sprint umfasst vier zusammenhängende Deliverables:

  A  GOV Kapitel 13          Neue Governance für externe Erkenntnisquellen
                             und USER-Feedback-Kanal

  B  AI_DRIVEN_DEV Kap.11-13 Methodische Erweiterung: Rollen-Parallelbetrieb,
                             Template-Methodik, MLAT→USER Transfer-Workflow

  C  USER_principles_S5      Neue public Blueprint-Dokumentation für User

  D  USER_How2_S5            Neue public Blueprint-Dokumentation für User

  Zusätzlich: Terminologie-Korrektur User/Kunde durch alle betroffenen
  Dokumente (GOV Kapitel 11, 12, 13 + USER-Reihe)

  Zusätzlich: Skill mlat-context-handler als projektübergreifender
  Claude-Skill für Kontexttrennung


--------------------------------------------------------------------------------
2. DELIVERABLE A — GOV KAPITEL 13
--------------------------------------------------------------------------------

2.1 Zweck
----------
Verbindliche Governance-Regeln für den Umgang mit externen
Erkenntnisquellen und den USER-Feedback-Kanal.

2.2 Inhalt
-----------
  13.1  Zweck — externer Erkenntniskanal als GOV-Thema verankert
  13.2  Definition externe Erkenntnisquelle
  13.3  Kennzeichnungspflicht — MLAT-Prefix und Tags verbindlich
  13.4  Anonymisierungspflicht — was nie in R+MUNI-Outputs erscheinen darf
  13.5  Transfer-Logik — Dreistufenprozess: Erfahrung / Transfer / Freigabe
  13.6  USER-Dokumentationsreihe — Kürzel, Ablage, Charakter
  13.7  Kontext-Hygiene bei eingeschränktem AI-Einsatz
  13.8  Rollentrennung als Governance-Prinzip
  13.9  Verhältnis zu bestehenden GOV-Kapiteln
  13.10 Abschluss

2.3 Wesentliche Entscheidungen
--------------------------------
  ENTSCHEIDUNG: Kennzeichnungssystem mit MLAT-Prefix und Tags
  BEGRÜNDUNG:   Dokumente aus externen Umgebungen tragen immer MLAT-
                im Dateinamen oder Titel. Im Chat werden [MLAT] für
                reine Erfahrungsberichte und [MLAT→RMUNI] für expliziten
                Transfer verwendet. Ohne Kennzeichnung gilt alles als
                R+MUNI-intern.

  ENTSCHEIDUNG: Dreistufige Transfer-Logik
  BEGRÜNDUNG:   Stufe 1 (aufnehmen) → Stufe 2 (übersetzen) →
                Stufe 3 (Betreiber gibt frei). Kein automatischer
                Transfer ohne expliziten Auslöser.

  ENTSCHEIDUNG: USER-Reihe als eigene Dokumentenreihe mit Kürzel USER
  BEGRÜNDUNG:   Anwenderorientierte Doku ist strukturell anders als
                technische Blueprint-Doku. Eigenes Kürzel und eigener
                Ablageort verhindern Vermischung.

  ENTSCHEIDUNG: Anonymisierungspflicht explizit in GOV verankert
  BEGRÜNDUNG:   Echte Namen, Organisationen und externe Strukturen
                dürfen nie in R+MUNI-Outputs erscheinen. GOV-Verankerung
                macht die Regel verbindlich und auditierbar.


--------------------------------------------------------------------------------
3. DELIVERABLE B — AI_DRIVEN_DEV_METHODE KAPITEL 11–13
--------------------------------------------------------------------------------

3.1 Zweck
----------
Methodische Erweiterung der AI Driven Development Methode um drei
neue Kapitel die den Rollen-Parallelbetrieb und den Transfer-Workflow
als gelebte Methode beschreiben.

3.2 Inhalt
-----------
  Kapitel 11 — Rollen-Parallelbetrieb
    Ausgangslage, Kernproblem, Kennzeichnungssystem,
    Claude-Verhalten je Modus, Entwickler als Kontrollorgan,
    GOV-Referenz

  Kapitel 12 — Template-Methodik für AI-fähige Dokumente
    Ausgangslage (Compliance-Umgebungen ohne AI),
    Template-Prinzip, vier Pflichtfelder,
    Warum diese Struktur Drift verhindert,
    Templates generieren lassen, Qualitätskriterium

  Kapitel 13 — MLAT→USER Transfer-Workflow
    Zweck, fünfstufiger Workflow,
    Qualitätskriterien für den Transfer,
    Was transferiert werden darf / nicht,
    USER-Reihe als Transferziel

3.3 Wesentliche Entscheidungen
--------------------------------
  ENTSCHEIDUNG: Kapitel 11–13 als Erweiterung — Kapitel 1–10 unverändert
  BEGRÜNDUNG:   GOV-konform additiv. Die Methode bleibt stabil,
                neue Kapitel beschreiben neue Anwendungsfälle.

  ENTSCHEIDUNG: Vier Pflichtfelder als AI-fähiges Dokument-Standard
  BEGRÜNDUNG:   Zweck/Kontext, Ausgangslage, Erkenntnis/Entscheidung,
                Grenzen/Gültigkeitsbereich. Diese vier Felder verhindern
                Kontext-Drift wenn Dokumente ohne Claude entstehen und
                später in Claude-Sessions eingebracht werden.

  ENTSCHEIDUNG: Entwickler bleibt Kontrollorgan — Claude handelt nicht präventiv
  BEGRÜNDUNG:   Claude folgt der Kennzeichnung. Bei Rollenvermischung
                meldet der Entwickler — Claude korrigiert ohne Widerstand.
                Keine Eigeninitiative beim Transfer.


--------------------------------------------------------------------------------
4. DELIVERABLE C+D — USER_principles_S5 + USER_How2_S5
--------------------------------------------------------------------------------

4.1 Zweck
----------
Zwei neue public Blueprint-Dokumente die R+MUNI aus Anwenderperspektive
beschreiben — ohne Blueprint-Jargon, ohne interne Quellverweise,
standalone lesbar.

4.2 USER_principles_S5 — Inhalt
---------------------------------
  9 Prinzipien für alle R+MUNI User:
  1. Zweck und Charakter der USER-Reihe
  2. Zielgruppe — User ist jeder ohne Bedingung
  3. Grundhaltung gegenüber R+MUNI (kostenlos, Haltung)
  4. Prinzip der Explizitheit
  5. Prinzip Stabilität vor Komfort
  6. Prinzip schrittweise Erweiterung
  7. Prinzip dokumentierte Entscheidung
  8. Prinzip kontrolliertes Wachstum
  9. Prinzip offenes Feedback

4.3 USER_How2_S5 — Inhalt
---------------------------
  5 Abschnitte mit konkreten Handlungsanleitungen:
  1. Wie man mit R+MUNI startet (Erwartungen, Einstiegsreihenfolge)
  2. Wie man Dokumente aufbaut die funktionieren
     (vier Pflichtfelder, Templates, Drift-Vermeidung)
  3. Wie man in eingeschränkten Umgebungen arbeitet
     (Compliance, Vorbereitung, Weiterverarbeitung)
  4. Wie man Atlassian als User nutzt
     (Jira, Confluence, Support-Regelung, Fehler vermeiden)
  5. Wie man Feedback sinnvoll einbringt
     (gutes vs. schlechtes Feedback, Kanal, Prozess)

4.4 Wesentliche Entscheidungen
--------------------------------
  ENTSCHEIDUNG: USER-Dokumente sind public — kein interner Hinweis
  BEGRÜNDUNG:   USER_principles und USER_How2 sind offizieller Teil
                des Blueprints. Kein Hinweis auf Quellen, keine internen
                Verweise, kein Blueprint-Jargon.

  ENTSCHEIDUNG: USER_How2 ist interner Entwicklungs-Input — Ablage intern
  BEGRÜNDUNG:   Korrektur: beide Dokumente sind public. Interne Referenzen
                (aus externen Quellen destilliert) landen nie in diesen
                Dokumenten — sie sind die saubere Ausgabeebene.

  ENTSCHEIDUNG: Vier Pflichtfelder aus Kapitel 12 AI_DEV auch in USER_How2
  BEGRÜNDUNG:   Konsistenz zwischen Methode und User-Doku. User profitieren
                von derselben Struktur die der Entwickler intern verwendet.


--------------------------------------------------------------------------------
5. TERMINOLOGIE-KORREKTUR USER/KUNDE
--------------------------------------------------------------------------------

5.1 Entscheidung
-----------------
  User   = jeder der R+MUNI nutzt — gratis, ohne Bedingung,
           unabhängig vom Nutzungsumfang. Gleichgesinnte.
  Kunde  = wer explizit einen bezahlten Service in Anspruch nimmt
           (Installation, Wartung, individuelle Begleitung)

5.2 Betroffene Dokumente
-------------------------
  Global_GOV.md
    - Kapitel 11 umbenannt: "UMGANG MIT ENDKUNDEN" → "UMGANG MIT USERN"
    - 11.1–11.5: "Endkunde/Kunde" → "User" durchgehend
    - 11.6: "Beta-Kunden" → "User"
    - 11.7: Neu formuliert — Basis-Support für User, Profis für Komplexes,
            kein Druck auf kostenpflichtige Pläne
    - 12.2: "Kunden und weitere Team-User" → "User und weitere Team-Mitglieder"
    - 13.1/13.6/13.9/13.10: "Endkunden" → "User"
    - 10.5: "Kundenwunsch" → "User-Wunsch"

  USER_principles_S5.md + USER_How2_S5.md
    - Konsequente User-Terminologie von Anfang an

5.3 Was "Kunde" bleibt
-----------------------
  Der Begriff "Kunde" ist in GOV 11.1 als explizite Abgrenzung zu
  "User" definiert und bewusst erhalten — nur für den Fall eines
  bezahlten Service-Akts.


--------------------------------------------------------------------------------
6. DELIVERABLE E — SKILL mlat-context-handler
--------------------------------------------------------------------------------

6.1 Zweck
----------
Projektübergreifender Claude-Skill der die Kontexttrennung zwischen
R+MUNI DEV-Rolle und Beta-Tester-Rolle automatisch steuert.

6.2 Inhalt
-----------
  - Erkennungslogik: MLAT-Prefix, [MLAT] Tag, [MLAT→RMUNI] Tag
  - Drei Verhaltensmodi je Erkennungssignal
  - Anonymisierungsregel GOV-konform eingebaut
  - Entwickler als Kontrollorgan verankert

6.3 Ablage
-----------
  Typ:    .skill Datei (projektübergreifend)
  Status: Installierbar in Claude.ai unter Einstellungen → Skills
  Datei:  mlat-context-handler.skill

6.4 Wesentliche Entscheidungen
--------------------------------
  ENTSCHEIDUNG: Skill projektübergreifend — nicht nur im R+MUNI Projekt
  BEGRÜNDUNG:   Der Entwickler bringt MLAT-Dokumente aus verschiedenen
                Kontexten ein. Der Skill muss überall greifen.

  ENTSCHEIDUNG: Skill bewusst schlank — nur Trennlogik, kein Overhead
  BEGRÜNDUNG:   Einfach korrigierbar wenn zu restriktiv oder zu wenig.
                Ausprobieren → beobachten → anpassen.


--------------------------------------------------------------------------------
7. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Feature-Zuwachs Stage 5
GOV 10.5  Fachlicher Mehrwert        OK  Rollen-Methodik + GOV + USER-Reihe
GOV 10.5  Keine implizite Gov-Änd.   OK  Kapitel 1-12 unverändert (außer
                                         Terminologie-Korrektur mit Datum)
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 1
GOV 10.6  Ziel überprüfbar           OK  Alle Deliverables vorhanden
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Additiv, Terminologie-Korrektur
                                         explizit dokumentiert mit Datum
GOV 12.6  GOV-Änderung dokumentiert  OK  Datum + Begründung in GOV-Header
                                         und Fußzeile eingetragen


--------------------------------------------------------------------------------
8. OFFENE PUNKTE
--------------------------------------------------------------------------------

  OP-01  Ordnerstruktur für USER-Reihe noch nicht in structure.txt erfasst
         → User legt Ordner manuell an wenn USER-Reihe in Blueprint-Ordner
           integriert wird
         → structure.txt danach aktualisieren

  OP-02  Rosetta Stone Block 5 und weitere Blueprint-Dokumente verwenden
         noch "Endkunde/Kunde" an einzelnen Stellen
         → Terminologie-Bereinigung in separatem Sprint wenn relevant

  OP-03  Skill mlat-context-handler: erste Praxiserfahrungen ausstehend
         → Nach ersten Einsätzen evaluieren ob Anpassungen nötig sind


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-GOV-USER-Methode-S5 | Stage 5 | 2026-03-18
R+MUNI Blueprint | Erstellt durch: Markus Resel + Claude (Pair-Session)
================================================================================
