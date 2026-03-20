================================================================================
AI DRIVEN DEVELOPMENT – METHODE R+MUNI
================================================================================
Erstellt    : 2026-03-06
Letzte Änderung : 2026-03-18 — Erweiterung Kapitel 11-13
Autor       : Markus Resel
Charakter   : Persönliche Arbeitsmethode / Entwicklungsphilosophie
Ablageort   : 00-concept/01-principles/AI_DRIVEN_DEV_METHODE.txt
================================================================================


================================================================================
1. ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument beschreibt die persönliche AI Driven Development Methode
die im Rahmen des R+MUNI Projekts entwickelt und gelebt wird.

Sie ist keine abstrakte Theorie sondern eine aus der Praxis gewachsene
Arbeitsweise die es einem nicht-technischen Entwickler ermöglicht
professionelle Software-Systeme zu entwickeln, zu betreiben und zu
dokumentieren — ohne eigenes Programmierwissen.

Die Methode ist bewusst auf die Person und ihre Arbeitsweise zugeschnitten.
Sie ist kein allgemeingültiges Framework sondern eine persönliche Disziplin.


================================================================================
2. GRUNDPRINZIP
================================================================================

Der Entwickler liefert:
  - Fachliche Tiefe (Domänenwissen, Systemlogik, Entscheidungen)
  - Governance (Regeln, Grenzen, Freigaben)
  - Qualitätskontrolle (Test, Abnahme, Ablage)
  - Kontext (Projektfolder, Dokumentation, Historie)

Die KI (Claude) liefert:
  - Code-Umsetzung
  - Technische Übersetzung von Fachlogik
  - Dokumentation
  - Debugging und Analyse

Kernaussage:
  Der Entwickler denkt das System.
  Die KI schreibt es auf.
  Entscheidungen bleiben immer beim Menschen.


================================================================================
3. RAHMENBEDINGUNGEN
================================================================================

3.1 Persönliches Profil des Entwicklers
-----------------------------------------
  - IT-Erfahrung: Presales Datacenter (20 Jahre),
                  Projektmanagement (6 Jahre),
                  Prozess- & Changemanagement (3 Jahre)
  - IMS-Betreuer: ISO 9001 (vollständig), ISO 27001, ISO 14001 (begleitend)
  - Kein Programmierwissen (kein Code Know-how)
  - GUI-orientiert, CLI kein Komfortbereich
  - Stärke: Systemdenken, Governance, Fachlogik, Domänenwissen

3.2 Werkzeuge
--------------
  - KI: Claude (Anthropic, Pro Plan)
  - Editor: Notepad++
  - Konsole: PowerShell 7
  - Ticketing: Atlassian Jira (Free Plan)
  - Dokumentation: Atlassian Confluence (Free Plan)
  - Versionierung: Projektfolder (manuell, strukturiert)


================================================================================
4. DIE METHODE – SCHRITT FÜR SCHRITT
================================================================================

4.1 Kontext herstellen (Session-Start)
----------------------------------------
Vor jeder Arbeits-Session wird sichergestellt dass Claude den vollständigen
Projektkontext kennt.

Mittel:
  - Projektfolder in Claude Desktop mit allen aktuellen Dokumenten
  - Alle Scripts, Config-Files und Dokumentations-TXTs sind aktuell
  - Bei Bedarf: kurze Kontext-Zusammenfassung im Chat

Prinzip:
  Claude arbeitet nie ohne vollständigen Kontext.
  Ein unvollständiger Kontext führt zu falschen Ergebnissen.

4.2 Problem beschreiben — nicht lösen
---------------------------------------
Der Entwickler beschreibt das Problem in eigenen Worten —
so wie er es versteht, nicht wie ein Techniker es formulieren würde.

Wichtig:
  - Keine technische Vorformulierung nötig
  - Alltagssprache ist ausdrücklich erlaubt
  - Halbfertige Gedanken sind willkommen
  - Claude übersetzt in technische Präzision

Beispiel aus der Praxis:
  "ich hab das problem dass das master.xml alles in den scope nimmt
   obwohl es in run-scope.txt anders definiert ist"
  → Claude analysiert, stellt gezielte Rückfragen, findet den Knoten

4.3 Gemeinsam den Knoten finden
---------------------------------
Claude und der Entwickler erarbeiten gemeinsam das Problem —
im Dialog, nicht durch Monolog.

Vorgehen:
  - Claude erklärt was er versteht
  - Entwickler korrigiert wo nötig
  - Schritt für Schritt zum echten Problem
  - Keine Lösung bevor das Problem klar ist

Typisches Muster:
  Entwickler erklärt → Claude zeichnet auf → Entwickler korrigiert →
  Claude präzisiert → gemeinsames Verständnis → dann erst: Lösung

4.4 Governance vor Code
------------------------
Bevor Code geschrieben wird:
  - Sprint Doku erstellen (GOV-konform)
  - Auslöser klassifizieren (Bugfix oder Feature)
  - Stage-Zuordnung klären (Stage 3 Freeze oder Stage 4)
  - Freigabe explizit erteilen

Prinzip:
  Kein Script ohne dokumentierten Grund.
  Die Dokumentation ist Teil der Arbeit — kein Abschlussartefakt.

4.5 Freigabe erteilen
----------------------
Der Entwickler erteilt explizit Freigabe für:
  - Stage 3 Eingriffe (Bugfix-Ausnahme)
  - Neue Scripts (Stage 4 Features)
  - Änderungen an bestehenden Config-Files

Die Freigabe ist immer bewusst und begründet.
Claude handelt nie ohne Freigabe in kritischen Bereichen.

4.6 Code Review durch Erklärung
---------------------------------
Der Entwickler reviewed Code nicht durch Lesen —
sondern durch Erklärung.

Vorgehen:
  - Claude erklärt was das Script macht (in Alltagssprache)
  - Entwickler prüft ob die Erklärung zur Absicht passt
  - Bei Abweichung: Korrektur und Neuversuch
  - Erst dann: Download und Test

4.7 Testen und Abnehmen
------------------------
  1. Script herunterladen
  2. Lokal ausführen (PowerShell)
  3. Ergebnis prüfen (Logs, Output, Verhalten)
  4. Bei Fehler: Fehlermeldung an Claude, gemeinsames Debugging
  5. Bei Erfolg: Abnahme

4.8 Ablage und Aktualisierung
-------------------------------
Nach erfolgreicher Abnahme:
  1. Altes Script/Dokument ersetzen
  2. Projektfolder aktualisieren
  3. Confluence Dokumentation pflegen
  4. Jira Ticket schließen

Prinzip:
  Was nicht abgelegt ist existiert nicht.
  Routine schlägt Improvisation.


================================================================================
5. KOMMUNIKATIONSPRINZIPIEN MIT CLAUDE
================================================================================

5.1 Sprache
------------
  - Deutsch als Arbeitssprache
  - Alltagssprache ist erlaubt und erwünscht
  - Technische Präzision liefert Claude — nicht der Entwickler
  - Umgangssprache, Halbsätze, Gedankensprünge sind normal

5.2 Erklärungsprinzip
----------------------
  - Schritt-für-Schritt Erklärungen immer
  - Kommandozeilen immer mit Erklärung
  - Konkrete Beispiele bevorzugen
  - Keine Annahmen über Vorwissen

5.3 Dialogführung
------------------
  - Entwickler unterbricht wenn etwas unklar ist
  - Claude fragt nach bevor er annimmt
  - Missverständnisse werden sofort aufgelöst
  - Kein "ich mache jetzt einfach mal" ohne Freigabe

5.4 Grenzen kennen
-------------------
  Claude kennt und respektiert:
  - Stage 3 Freeze (kein Eingriff ohne Bugfix-Freigabe)
  - Governance Regeln (GOV-konform handeln)
  - 1 Script 1 Outcome Prinzip
  - Keine Automatisierung ohne expliziten Auftrag


================================================================================
6. KONTEXTMANAGEMENT
================================================================================

6.1 Projektfolder als gemeinsame Wahrheit
-------------------------------------------
Der Projektfolder in Claude Desktop enthält:
  - Alle aktuellen Scripts (.py)
  - Alle Config-Files (.txt)
  - Alle Dokumentations-Dateien (.txt)
  - Stage-Dokumente (Freeze, Ziele)
  - Sprint Dev-Dokumentationen

Prinzip:
  Was im Projektfolder ist — das weiß Claude.
  Was nicht drin ist — muss im Chat erklärt werden.

6.2 Aktualisierungszyklus
---------------------------
  Nach jeder Session mit Änderungen:
  - Geänderte Dateien in Projektfolder ersetzen
  - Neue Dateien hinzufügen
  - Veraltete Dateien entfernen

  Nicht lesbare Formate (.xlsx) werden nicht im Projektfolder abgelegt.
  Mappings und Konfigurationen immer als .txt.

6.3 Session-Ende
-----------------
  Jede Session endet mit:
  - Klarem Stand (was wurde erreicht)
  - Offenen Punkten (was kommt als nächstes)
  - Aktualisierten Dateien im Projektfolder


================================================================================
7. QUALITÄTSSICHERUNG
================================================================================

7.1 Vier-Augen-Prinzip
-----------------------
  Jede Lösung wird von Claude erklärt und vom Entwickler
  inhaltlich abgenommen — auch ohne technisches Verständnis
  des Codes selbst.

  Der Entwickler prüft:
  - Passt die Erklärung zur Absicht?
  - Ist die Governance eingehalten?
  - Ist die Stage-Zuordnung korrekt?
  - Ist die Rückwärtskompatibilität gegeben?

7.2 Testpflicht
----------------
  Kein Script gilt als fertig ohne lokalen Testlauf.
  Logs werden gelesen und interpretiert (mit Claude-Unterstützung).

7.3 Dokumentationspflicht
---------------------------
  Kein Sprint ohne Sprint-Doku.
  Kein Stage-Ende ohne vollständige Dokumentation.
  Dokumentation ist Bestandteil der Leistung — nicht Nacharbeit.


================================================================================
8. STÄRKEN DIESER METHODE
================================================================================

  + Kein Programmierwissen erforderlich
  + Domänenwissen des Entwicklers bleibt führend
  + Governance und Qualität bleiben beim Menschen
  + Schnelle Umsetzung durch KI-Unterstützung
  + Vollständige Nachvollziehbarkeit durch Dokumentation
  + Reproduzierbar und übertragbar
  + Skalierbar auf unterschiedliche Domänen
  + Offen für Weiterentwicklung (Stages, Sprints)


================================================================================
9. GRENZEN DIESER METHODE
================================================================================

  - KI-Verfügbarkeit als Abhängigkeit (kein Internet = kein Entwickeln)
  - Kontextfenster der KI begrenzt (Projektfolder-Disziplin notwendig)
  - Keine automatische Versionierung (manuelle Disziplin erforderlich)
  - Testing bleibt beim Entwickler (KI kann nicht lokal testen)
  - Komplexe Fehlerbilder benötigen gute Fehlerbeschreibung
  - Claude kann Projektfolder-Inhalt und GitHub-Repo-Inhalt nicht
    automatisch auf Übereinstimmung prüfen — der Sync-Status ist
    für Claude ohne expliziten Fetch-Auftrag nicht sichtbar
  - Ein Fetch-Auftrag auf eine externe URL öffnet eine neue
    Kontextebene ohne Bezug zur laufenden Session — bricht den Fluss


================================================================================
10. WEITERENTWICKLUNG
================================================================================

Diese Methode ist lebendig und wird mit dem Projekt weiterentwickelt.
Erkenntnisse aus der Praxis fließen in dieses Dokument ein.

Änderungen an dieser Methode folgen denselben Governance-Regeln
wie alle anderen Dokumente im R+MUNI Blueprint.


================================================================================
11. ROLLEN-PARALLELBETRIEB
================================================================================
Erweiterung Stage 5 | 2026-03-18

11.1 Ausgangslage
------------------
Der Entwickler agiert in mehreren Rollen gleichzeitig:
  - R+MUNI Entwickler / DEV (primäre Rolle in diesem Kontext)
  - Beta-Tester in externen Atlassian-Umgebungen
  - PreSales / Berater

Jede Rolle erzeugt wertvolle Erkenntnisse.
Die Herausforderung: Erkenntnisse sauber trennen und kontrolliert überführen.

11.2 Das Kernproblem
---------------------
Ohne explizite Trennung entstehen zwei Risiken:
  - Rollenvermischung: MLAT-Annahmen fließen unbewusst in R+MUNI ein
  - Informationsverlust: Wertvolle Erkenntnisse gehen verloren weil
    kein strukturierter Kanal existiert

Beide Risiken sind durch Methode beherrschbar — nicht durch Verzicht.

11.3 Das Kennzeichnungssystem
------------------------------
Jede Information aus einer Nicht-DEV-Rolle wird beim Einbringen
in Claude-Sessions explizit gekennzeichnet:

  [MLAT]         → Erfahrungsbericht aus externer Umgebung
                   Claude nimmt auf, baut nichts ein
                   Kein Transfer ohne weiteren Auftrag

  [MLAT→RMUNI]   → Expliziter Transfer-Auftrag
                   Claude übersetzt Erkenntnis in R+MUNI-Kontext
                   Anonymisierung wird automatisch angewendet

  Kein Tag        → Standard R+MUNI DEV-Kontext
                   Claude arbeitet normal im Blueprint-Rahmen

Dokumente aus externen Umgebungen tragen zusätzlich den Prefix MLAT-
im Dateinamen oder Titel.

11.4 Verhalten von Claude im Rollen-Parallelbetrieb
-----------------------------------------------------
Claude folgt der Kennzeichnungslogik automatisch:

  Bei [MLAT]:
  - Inhalt aufnehmen und verstehen
  - Kein automatischer Einbau in R+MUNI-Strukturen
  - Als verfügbares Kontextwissen intern halten
  - Auf Nachfrage zur MLAT-Info antworten ohne Rollenkontext zu verlieren

  Bei [MLAT→RMUNI]:
  - Erkenntnis aktiv in R+MUNI-Sprache übersetzen
  - Rohdaten, Namen, externe Strukturen herausfiltern
  - Nur transferierbare Prozess- oder Architektur-Erkenntnis ausgeben
  - Ergebnis zur Freigabe durch den Entwickler vorlegen

  Bei Unklarheit über aktive Rolle:
  - Claude fragt nach bevor er handelt
  - Kein Raten, kein implizites Annehmen einer Rolle

11.5 Der Entwickler als Kontrollorgan
---------------------------------------
Der Entwickler ist das aktive Kontrollorgan für die Rollentrennung.

Das bedeutet:
  - Rollenbrüche werden aktiv gemeldet (analog zur .bat-Konvention)
  - Claude korrigiert ohne Widerstand wenn ein Rollenbruch erkannt wird
  - Keine Eigeninitiative von Claude beim Transfer ohne Auslöser

Prinzip:
  Claude folgt der Rolle — er definiert sie nicht.
  Kontrolle bleibt beim Entwickler.

11.6 Gouvernanz-Referenz
-------------------------
Die vollständige Governance für den Rollen-Parallelbetrieb ist in
GOV Kapitel 13 definiert.

Dieses Kapitel beschreibt die methodische Anwendung —
GOV 13 beschreibt die Regeln.
Bei Widerspruch gilt GOV 13.


================================================================================
12. TEMPLATE-METHODIK FÜR AI-FÄHIGE DOKUMENTE
================================================================================
Erweiterung Stage 5 | 2026-03-18

12.1 Ausgangslage
------------------
Nicht in jeder Umgebung darf Claude eingesetzt werden.
Compliance-Anforderungen, Datenschutz oder interne Richtlinien können
den AI-Einsatz einschränken oder verbieten.

Trotzdem entstehen in diesen Umgebungen wertvolle Erkenntnisse die später
mit Claude weiterverarbeitet werden sollen.

Das Problem:
  Dokumente die ohne Claude entstanden sind und ohne Kontext-Vorbereitung
  in eine Claude-Session eingebracht werden führen zu Kontext-Drift —
  Claude fehlen Hintergrundinformationen und trifft implizite Annahmen.

12.2 Das Template-Prinzip
--------------------------
AI-fähige Dokumente folgen einer definierten Struktur die sicherstellt
dass Claude den Kontext ohne mündliche Erklärung erschließen kann.

Ein AI-fähiges Dokument enthält immer:

  ZWECK / KONTEXT
  ----------------
  Was ist der Gegenstand dieses Dokuments?
  In welchem Zusammenhang steht es?
  Für wen und wozu wurde es erstellt?

  AUSGANGSLAGE
  -------------
  Was war gegeben / bekannt bevor die Erkenntnis entstand?
  Welche Rahmenbedingungen galten?
  Was war das Problem oder die Fragestellung?

  ERKENNTNIS / ENTSCHEIDUNG
  --------------------------
  Was wurde getan, erkannt oder entschieden?
  Warum wurde so entschieden?
  Was wurde bewusst nicht getan und warum?

  TRANSFERIERBARKEIT
  -------------------
  Was an dieser Erkenntnis ist allgemein gültig?
  Was ist spezifisch für diese Umgebung und nicht übertragbar?
  Was muss anonymisiert werden bevor ein Transfer möglich ist?

  ANONYMISIERUNGSHINWEIS (wenn relevant)
  ----------------------------------------
  Welche Informationen in diesem Dokument unterliegen der
  Anonymisierungspflicht gemäß GOV 13.4?

12.3 Warum diese Struktur funktioniert
----------------------------------------
Die Struktur folgt dem Grundprinzip der AI Driven Development Methode:
Explizitheit verhindert Drift.

Claude benötigt:
  - Zweck (Was soll ich damit tun?)
  - Kontext (Woher kommt das?)
  - Begründungen (Warum ist das so?)
  - Grenzen (Was darf ich nicht annehmen?)

Ein Dokument das diese vier Fragen beantwortet ist AI-fähig —
unabhängig davon ob Claude bei seiner Entstehung beteiligt war.

12.4 Templates generieren lassen
----------------------------------
Der Entwickler kann Claude beauftragen Templates für spezifische
Dokumenttypen zu generieren.

Vorgehen:
  1. Dokumenttyp beschreiben (z.B. "Onboarding-Checkliste für neue User")
  2. Zielumgebung angeben (z.B. "wird ohne Claude befüllt, später importiert")
  3. Anonymisierungsanforderungen nennen wenn bekannt
  4. Claude generiert ein AI-fähiges Template in der gewünschten Struktur

Das Template wird einmalig erstellt und dann in der Zielumgebung
ohne Claude befüllt.

12.5 Qualitätskriterium für AI-fähige Dokumente
-------------------------------------------------
Ein Dokument ist AI-fähig wenn:
  - Claude es ohne mündliche Erklärung sinnvoll verarbeiten kann
  - keine impliziten Annahmen notwendig sind
  - Kontext, Zweck und Grenzen explizit enthalten sind
  - Anonymisierungspflichten markiert oder bereits angewendet sind

Nicht AI-fähige Dokumente müssen vor der Verwendung in Claude-Sessions
aufbereitet werden — entweder durch den Entwickler oder durch
eine geführte Aufbereitungs-Session mit Claude.


================================================================================
13. MLAT→USER TRANSFER-WORKFLOW
================================================================================
Erweiterung Stage 5 | 2026-03-18

13.1 Zweck
-----------
Dieser Abschnitt beschreibt den konkreten Arbeitsablauf wenn Erkenntnisse
aus externen Umgebungen (gekennzeichnet mit MLAT) in R+MUNI-Kunden-
dokumentation (USER-Reihe) überführt werden sollen.

Er ist die methodische Umsetzung von GOV Kapitel 13.

13.2 Der Transfer-Workflow im Überblick
----------------------------------------

  SCHRITT 1 — Erkenntnis einbringen
  ------------------------------------
  Der Entwickler bringt ein MLAT-Dokument oder eine [MLAT]-Nachricht
  in die Claude-Session ein.

  Claude:
  - liest und versteht den Inhalt
  - baut nichts in R+MUNI ein
  - gibt keine Zusammenfassung ohne Aufforderung aus

  SCHRITT 2 — Transfer auslösen
  ------------------------------
  Der Entwickler gibt den expliziten Transfer-Auftrag mit [MLAT→RMUNI].

  Dabei optional angeben:
  - Zieldokument (z.B. USER_How2_S5, USER_principles_S5)
  - Zielgruppe (z.B. Endkunden, neue Atlassian-User)
  - Einschränkungen (z.B. "nur Prozess-Erkenntnis, keine Tool-Details")

  SCHRITT 3 — Claude übersetzt
  -----------------------------
  Claude erstellt einen Transfer-Entwurf:
  - Erkenntnis wird in R+MUNI-Sprache übersetzt
  - Anonymisierung wird automatisch angewendet
  - Externe Strukturdetails werden herausgefiltert
  - Nur transferierbare, allgemeingültige Erkenntnis bleibt

  SCHRITT 4 — Entwickler prüft
  -----------------------------
  Der Entwickler prüft den Entwurf:
  - Stimmt die Erkenntnis inhaltlich?
  - Ist die Anonymisierung vollständig?
  - Passt der Ton zur Zieldokumentation?
  - Ist die Transferierbarkeit korrekt eingeschätzt?

  SCHRITT 5 — Freigabe und Einbau
  ---------------------------------
  Nach Freigabe durch den Entwickler:
  - Erkenntnis wird in das Zieldokument (USER-Reihe) eingebaut
  - Zieldokument wird abgelegt und Projektfolder aktualisiert
  - MLAT-Quelldokument bleibt unverändert und separat

13.3 Qualitätskriterien für den Transfer
------------------------------------------
Ein Transfer ist erfolgreich wenn:

  - Keine echten Namen oder externe Bezeichnungen im Ergebnis enthalten sind
  - Die Erkenntnis ohne Kenntnis der Quellumgebung verständlich ist
  - Der Inhalt für die Zielgruppe (Endkunden) direkt nutzbar ist
  - Die Quelle nicht rekonstruierbar ist
  - Der Entwickler die Freigabe explizit erteilt hat

13.4 Abgrenzung: Was transferiert werden darf
----------------------------------------------
  Transferierbar:
  - Prozess-Erkenntnisse (wie läuft etwas ab)
  - Prinzipien (was hat sich bewährt)
  - Muster (welche Probleme treten typisch auf)
  - How-to-Strukturen (wie geht man vor)

  Nicht transferierbar:
  - Echte Konfigurationen oder Systemdetails externer Umgebungen
  - Personenbezogene Erfahrungen die auf Individuen rückführbar sind
  - Interne Bezeichnungen, Projektnamen, Organisationsstrukturen
  - Rohdaten jeder Art

13.5 USER-Reihe als Ziel des Transfers
----------------------------------------
Ergebnisse des MLAT→RMUNI Transfers landen in der USER-Reihe:

  USER_principles_S5.md   → Was gilt grundsätzlich für Endkunden
  USER_How2_S5.md         → Wie arbeiten Endkunden konkret

Die USER-Reihe ist interner Entwicklungs-Input.
Sie ist nicht öffentlich und wird nicht direkt an Kunden ausgegeben.
Sie dient als Vorarbeit für spätere Kunden-Kommunikation.

Jedes USER-Dokument trägt einen Hinweis:
  "Erstellt aus anonymisierten Praxiserkenntnissen — kein Direktbezug
   zu realen Personen, Organisationen oder Konfigurationen."


================================================================================
14. CLAUDE UND EXTERNE QUELLEN — GRENZEN DER KONTEXTVERBINDUNG
================================================================================

14.1 Ausgangslage
------------------
Claude arbeitet im R+MUNI Kontext primär mit dem Projektfolder als
gemeinsamer Wahrheit (siehe Kapitel 6.1). Daneben existieren externe
Quellen wie GitHub-Repos, Confluence-Spaces und andere URLs.

Die Frage ob Projektfolder-Inhalt und externer Repo-Inhalt übereinstimmen
kann Claude nicht automatisch beantworten.

14.2 Was Claude kann und nicht kann
-------------------------------------
Claude KANN:
  - Projektfolder-Inhalte lesen und verarbeiten
  - Bekannte URLs aus dem Gesprächskontext referenzieren
  - Auf expliziten Auftrag hin eine URL fetchen und lesen

Claude KANN NICHT:
  - Automatisch prüfen ob Projektfolder und GitHub-Repo synchron sind
  - Den Sync-Status zwischen lokalem Stand und externem Repo beurteilen
  - Erkennen ob eine Datei im Folder bereits gepusht wurde oder veraltet ist

14.3 Das Fetch-Problem
------------------------
Ein Fetch-Auftrag auf eine externe URL ist technisch möglich —
erzeugt aber eine neue Kontextebene ohne Bezug zur laufenden Session.

Konsequenz:
  - Der Gesprächsfluss wird unterbrochen
  - Claude verliert den roten Faden der aktuellen Arbeit
  - Das Ergebnis des Fetch steht isoliert ohne Sessionkontext

Praxisregel:
  Fetches gehören an den Anfang einer Session — nicht mitten hinein.
  Wer mitten in einer Arbeitssession externe Inhalte prüfen will,
  öffnet besser eine separate Session dafür.

14.4 Konsequenz für die Arbeitsweise
--------------------------------------
  - GitHub-Sync und Repo-Konsistenz prüft EUMAXL selbst
  - Claude wird nicht für Sync-Verifikation eingesetzt
  - Wenn Repo-Inhalt relevant ist: vor Session-Start fetchen und
    als Kontext in den Projektfolder aufnehmen
  - E-Mails mit Links auf eigene Repos werden von EUMAXL
    selbst zusammengestellt — Claude liefert den Inhalt,
    EUMAXL kennt den aktuellen Repo-Stand


================================================================================
END OF DOCUMENT
AI Driven Development – Methode R+MUNI | 2026-03-06
Erweiterung Kapitel 11-13 | 2026-03-18
Erweiterung Kapitel 9 + Kapitel 14 | 2026-03-19
================================================================================
