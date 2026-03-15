================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-DOKU01-AI-Driven-Dev-Methodik
Datum               : 2026-03-13
Stage               : 5 (aktiv)
Status              : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch      : Entwickler + Claude (Pair-Session)
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Dokumentation (Stage-5-Ziel 4.5)

Begründung   : Stage 5 definiert als Ziel die AI-Driven Development
               Methodik von der persönlichen Arbeitsweise zur
               dokumentierten Blueprint-Komponente weiterzuentwickeln.

               Das Dokument AI_DRIVEN_DEV_METHODE.md wurde in Stage 5
               als persönliche Arbeitsmethode beschrieben. Diese
               Sprint-Doku formalisiert die Methode als offiziellen
               Blueprint-Bestandteil und hält die Erkenntnisse aus
               dem praktischen Betrieb fest.

Fachlicher   : Die Methode ist für Dritte nachvollziehbar und
Mehrwert       reproduzierbar. R+MUNI als Open-Source-Toolset hat
               dokumentierte Entwicklungsprinzipien.


--------------------------------------------------------------------------------
2. DIE METHODE — ZUSAMMENFASSUNG
--------------------------------------------------------------------------------

2.1 Grundprinzip
-----------------
AI-Driven Development ist keine Automatisierung des Denkens.
Es ist die strukturierte Zusammenarbeit zwischen menschlicher
Fachkompetenz und KI-Umsetzungsstärke.

  Der Entwickler liefert:
    Fachliche Tiefe (Domänenwissen, Systemlogik, Entscheidungen)
    Governance (Regeln, Grenzen, Freigaben)
    Qualitätskontrolle (Test, Abnahme, Ablage)
    Kontext (Projektfolder, Dokumentation, Historie)

  Die KI (Claude) liefert:
    Code-Umsetzung
    Technische Übersetzung von Fachlogik
    Dokumentation
    Debugging und Analyse

  Kernaussage:
    Der Entwickler denkt das System.
    Die KI schreibt es auf.
    Entscheidungen bleiben immer beim Menschen.

2.2 Rahmenbedingungen
----------------------
Persönliches Profil (EUMAXL):
  IT-Erfahrung: Presales Datacenter (20 Jahre),
                Projektmanagement (6 Jahre),
                Prozess- & Changemanagement (3 Jahre)
  IMS-Betreuer: ISO 9001 (vollständig), ISO 27001 (begleitend), ISO 14001 (begleitend)
  Kein Programmierwissen — kein Code Know-how
  GUI-orientiert, CLI kein Komfortbereich
  Stärke: Systemdenken, Governance, Fachlogik, Domänenwissen

Werkzeuge:
  KI          : Claude (Anthropic, Pro Plan)
  Editor      : Notepad++
  Konsole     : PowerShell 7
  Ticketing   : Atlassian Jira (Free Plan)
  Dokumentation: Atlassian Confluence (Free Plan)
  Versionierung: GitHub (Free Plan)


--------------------------------------------------------------------------------
3. DIE METHODE — SCHRITT FÜR SCHRITT
--------------------------------------------------------------------------------

Schritt 1 — Kontext herstellen (Session-Start)
  Vor jeder Arbeits-Session wird sichergestellt dass Claude den
  vollständigen Projektkontext kennt.

  Mittel:
    Projektfolder in Claude.ai mit allen aktuellen Dokumenten
    Alle Scripts, Config-Files und Dokumentations-Dateien aktuell
    Bei Bedarf: kurze Kontext-Zusammenfassung im Chat

  Prinzip:
    Claude arbeitet nie ohne vollständigen Kontext.
    Unvollständiger Kontext führt zu falschen Ergebnissen.

Schritt 2 — Problem beschreiben — nicht lösen
  Der Entwickler beschreibt das Problem in eigenen Worten —
  so wie er es versteht, nicht wie ein Techniker es formulieren würde.

  Wichtig:
    Keine technische Vorformulierung nötig
    Alltagssprache ist ausdrücklich erlaubt
    Halbfertige Gedanken sind willkommen
    Claude übersetzt in technische Präzision

  Beispiel aus der Praxis:
    "ich hab das problem dass das master.xml alles in den scope nimmt
     obwohl es in run-scope.txt anders definiert ist"
    → Claude analysiert, stellt gezielte Rückfragen, findet den Knoten

Schritt 3 — Gemeinsam den Knoten finden
  Claude und Entwickler erarbeiten gemeinsam das Problem — im Dialog.

  Vorgehen:
    Claude erklärt was er versteht
    Entwickler korrigiert wo nötig
    Schritt für Schritt zum echten Problem
    Keine Lösung bevor das Problem klar ist

  Typisches Muster:
    Entwickler erklärt → Claude zeichnet auf → Entwickler korrigiert →
    Claude präzisiert → gemeinsames Verständnis → dann erst: Lösung

Schritt 4 — Governance vor Code
  Bevor Code geschrieben wird:
    Sprint Doku erstellen (GOV-konform)
    Auslöser klassifizieren (Bugfix oder Feature)
    Stage-Zuordnung klären
    Freigabe explizit erteilen

  Prinzip:
    Kein Script ohne dokumentierten Grund.
    Dokumentation ist Teil der Arbeit — kein Abschlussartefakt.

Schritt 5 — Freigabe erteilen
  Der Entwickler erteilt explizit Freigabe für:
    Stage 3/4 Eingriffe (Bugfix-Ausnahme)
    Neue Scripts
    Änderungen an bestehenden Config-Files

  Claude handelt nie ohne Freigabe in kritischen Bereichen.

Schritt 6 — Code Review durch Erklärung
  Der Entwickler reviewed Code nicht durch Lesen — durch Erklärung.

  Vorgehen:
    Claude erklärt was das Script macht (in Alltagssprache)
    Entwickler prüft ob die Erklärung zur Absicht passt
    Bei Abweichung: Korrektur und Neuversuch
    Erst dann: Download und Test

Schritt 7 — Testen und Abnehmen
  1. Script lokal ausführen (PowerShell)
  2. Ergebnis prüfen (Logs, Output, Verhalten)
  3. Bei Fehler: Fehlermeldung an Claude, gemeinsames Debugging
  4. Bei Erfolg: Abnahme

Schritt 8 — Ablage und Aktualisierung
  1. Altes Script/Dokument ersetzen
  2. Projektfolder aktualisieren
  3. Confluence Dokumentation pflegen
  4. Jira Ticket schließen

  Prinzip:
    Was nicht abgelegt ist existiert nicht.
    Routine schlägt Improvisation.


--------------------------------------------------------------------------------
4. KOMMUNIKATIONSPRINZIPIEN MIT CLAUDE
--------------------------------------------------------------------------------

Sprache
  Deutsch als Arbeitssprache.
  Alltagssprache erlaubt und erwünscht.
  Technische Präzision liefert Claude.

Erklärungsprinzip
  Schritt-für-Schritt Erklärungen immer.
  Kommandozeilen immer mit Erklärung.
  Konkrete Beispiele bevorzugen.
  Keine Annahmen über Vorwissen.

Dialogführung
  Entwickler unterbricht wenn etwas unklar ist.
  Claude fragt nach bevor er annimmt.
  Missverständnisse werden sofort aufgelöst.
  Kein "ich mache jetzt einfach mal" ohne Freigabe.

Grenzen kennen
  Claude kennt und respektiert:
    Stage 3/4 Freeze (kein Eingriff ohne Bugfix-Freigabe)
    Governance Regeln (GOV-konform handeln)
    1 Script 1 Outcome Prinzip
    Keine Automatisierung ohne expliziten Auftrag


--------------------------------------------------------------------------------
5. KONTEXTMANAGEMENT
--------------------------------------------------------------------------------

Projektfolder als gemeinsame Wahrheit
  Der Projektfolder in Claude.ai enthält:
    Alle aktuellen Scripts (.py)
    Alle Config-Files (.cfg, .txt)
    Alle Dokumentations-Dateien (.md, .txt)
    Stage-Dokumente (Freeze, Ziele)
    Sprint Dev-Dokumentationen

  Prinzip:
    Was im Projektfolder ist — das weiß Claude.
    Was nicht drin ist — muss im Chat erklärt werden.

Aktualisierungszyklus
  Nach jeder Session mit Änderungen:
    Geänderte Dateien in Projektfolder ersetzen
    Neue Dateien hinzufügen
    Veraltete Dateien entfernen

Session-Ende
  Jede Session endet mit:
    Klarem Stand (was wurde erreicht)
    Offenen Punkten (was kommt als nächstes)
    Aktualisierten Dateien im Projektfolder


--------------------------------------------------------------------------------
6. QUALITÄTSSICHERUNG
--------------------------------------------------------------------------------

Vier-Augen-Prinzip
  Jede Lösung wird von Claude erklärt und vom Entwickler abgenommen —
  auch ohne technisches Verständnis des Codes selbst.

  Der Entwickler prüft:
    Passt die Erklärung zur Absicht?
    Ist die Governance eingehalten?
    Ist die Stage-Zuordnung korrekt?
    Ist die Rückwärtskompatibilität gegeben?

Testpflicht
  Kein Script gilt als fertig ohne lokalen Testlauf.
  Logs werden gelesen und interpretiert (mit Claude-Unterstützung).

Dokumentationspflicht
  Kein Sprint ohne Sprint-Doku.
  Kein Stage-Ende ohne vollständige Dokumentation.
  Dokumentation ist Bestandteil der Leistung — nicht Nacharbeit.


--------------------------------------------------------------------------------
7. STÄRKEN UND GRENZEN
--------------------------------------------------------------------------------

Stärken
  + Kein Programmierwissen erforderlich
  + Domänenwissen des Entwicklers bleibt führend
  + Governance und Qualität bleiben beim Menschen
  + Schnelle Umsetzung durch KI-Unterstützung
  + Vollständige Nachvollziehbarkeit durch Dokumentation
  + Reproduzierbar und übertragbar
  + Skalierbar auf unterschiedliche Domänen
  + Offen für Weiterentwicklung (Stages, Sprints)

Grenzen
  - KI-Verfügbarkeit als Abhängigkeit (kein Internet = kein Entwickeln)
  - Kontextfenster der KI begrenzt (Projektfolder-Disziplin notwendig)
  - Keine automatische Versionierung (manuelle Disziplin erforderlich)
  - Testing bleibt beim Entwickler (KI kann nicht lokal testen)
  - Komplexe Fehlerbilder benötigen gute Fehlerbeschreibung


--------------------------------------------------------------------------------
8. CLAUDE IM R+MUNI ÖKOSYSTEM
--------------------------------------------------------------------------------

Grundsatz (Stage 5):
  R+MUNI läuft ohne Claude vollständig und kostenlos.
  Claude ist ein Werkzeug — kein Produkt, kein Geschäft.

Position im Blueprint:
  Claude wird als AI-Driven Development Werkzeug dokumentiert.
  Wer Claude nutzen möchte findet den Weg selbst — kein Push, kein Zwang.
  Claude erhält einen definierten, sichtbaren Platz im Blueprint.

Ökosystem-Philosophie:
  Alle in R+MUNI verwendeten Tools finden ihren sichtbaren Platz.
  Wer den Wert eines Tools erkennt schließt selbst ab — organisch.
  R+MUNI macht transparent womit gearbeitet wird und warum.


--------------------------------------------------------------------------------
9. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Dokumentation Stage-5-Ziel 4.5
GOV 10.5  Fachlicher Mehrwert        OK  Methodik für Dritte nachvollziehbar
GOV 10.5  Keine implizite Gov-Änd.   OK  Additiv, keine GOV-Revision
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 1
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Rein dokumentarisch


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-DOKU01-AI-Driven-Dev-Methodik | Stage 5 | 2026-03-13
R+MUNI Blueprint | Erstellt durch: Markus Resel + Claude (Pair-Session)
================================================================================
