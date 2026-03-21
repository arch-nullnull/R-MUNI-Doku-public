================================================================================
HOW2 – FEEDBACKSCHLEIFEN IN R+MUNI (STAGE 6)
================================================================================
Projekt             : R+MUNI Blueprint
Dokument            : How2_Feedbackschleifen_S6
Datum               : 2026-03-21
Stage               : S6 – AKTIV
Status              : Dokumentiert (bestehende Praxis)
Erstellt durch      : EUMAXL + Claude (Pair-Session)
Bezug               : STAGE6_ZIELE.md (S6-Z2)

================================================================================
ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument beschreibt wie Feedback in R+MUNI fließt — sowohl intern
(DEV-Sicht) als auch extern (Kundensicht).

Das Setup ist bereits produktiv und bewährt. Dieses Dokument konserviert
die bestehende Praxis für Nachvollziehbarkeit und Onboarding neuer
Entwickler.

Charakter: Beschreibung der aktuellen, funktionierenden Realität.
Nicht ideal-theoretisch, sondern pragmatisch-werkend.

================================================================================
1. ÜBERBLICK — DIE FEEDBACKLANDSCHAFT
================================================================================

Es gibt zwei Feedbackschleifen in R+MUNI:

1. DEV-Schleife (intern)
   - Wohin: GitHub → Jira → Confluence → Implementierung
   - Wer: Entwickler, R+MUNI Team
   - Charaktere: Tickets, Diskussionen, Code Review

2. Kundenschleife (extern)
   - Wohin: Portal (README) → GitHub → Antwort via Portal/README
   - Wer: Beta-Kunden
   - Charaktere: Bugs melden, Feature-Requests, Fragen


Prinzip (zentral):
  GitHub ist immer die Quelle der Wahrheit.
  Alles andere (Jira, Confluence, Portal) sind Spiegel/Verlängerungen
  die Git-Hub-Input ansprechender oder fokussierter darstellen.

================================================================================
2. DEV-FEEDBACKSCHLEIFE (INTERN)
================================================================================

2.1 Einstiegspunkte für DEV-Feedback
-------------------------------------

DEV-Feedback kommt aus mehreren Quellen:

  a) GitHub Issues (direkt vom Entwickler oder vom Kunden via README)
  b) Jira Tickets (externe Meldung via Portal, wird manuell in Jira erfasst)
  c) Direkte Kommunikation (E-Mail, Chat, Konversation mit EUMAXL)


2.2 GitHub → Quelle der Wahrheit
---------------------------------

GitHub ist bewusst die zentrale Ablage:

  - Code ist dort (Repositories)
  - Issues werden dort festgehalten
  - README ist der primäre Einstieg für Kunden
  - MD-Dokumentation ist dort versioniert
  - GitHub ist öffentlich (Transparenz für Beta-Kunden)

Workflow GitHub:
  1. Entwickler oder Kunde öffnet Issue
  2. Issue wird mit Labels versehen (bug, feature, documentation, etc.)
  3. EUMAXL nimmt Issue zur Kenntnis
  4. EUMAXL priorisiert und plant
  5. Implementierung (lokal, in Git-Hub gepusht)
  6. Issue wird geschlossen mit Verweis auf Commit/PR

Vorteil:
  - Alles ist nachvollziehbar
  - Commits sind atomare Einheiten
  - History ist sauber


2.3 Jira → DEV-Backlog Spiegel
-------------------------------

Jira ist optionaler Spiegel des GitHub Backlogs:

  - Jira-Tickets können aus MD-Backlog-Einträgen geklont werden
  - Klone können fragmentiert sein (Jira-spezifische Anpassung)
  - Jira dient als schnelle Übersicht für das Team
  - Jira ist nicht Quelle der Wahrheit (GitHub ist)

Workflow Jira:
  1. EUMAXL hat GitHub Issue / Backlog-Eintrag
  2. Optional: Klone als Jira-Ticket für Team-Sicht
  3. Team sieht Jira für Übersicht und Status
  4. Aber Quelle der Wahrheit bleibt GitHub
  5. Jira kann ruhig fragmentiert sein (kein Sync-Zwang)

Wichtig:
  Jira ist KEIN automatischer Sync mit GitHub.
  Es ist eine manuelle Spiegel-Ablage auf EUMAXL Anweisung.
  Fragmentation ist akzeptabel weil Jira Notiz-Ordner ist, nicht Quelle.


2.4 Confluence → Kommunikationsverlängerung
-------------------------------------------

Confluence dient der ansprechenden, tieferen Kommunikation:

  - Technische Details die GitHub-Issue zu komplex wären
  - How-to Dokumentation für Entwickler
  - Tiefere Analysen zu Problemen
  - Integration-Tests und Erkenntnisse

Workflow Confluence:
  1. GitHub Issue vorhanden
  2. Technische Analyse/Lösung wird in Confluence ausgearbeitet
  3. Confluence-Seite wird im GitHub-Issue verlinkt
  4. Implementierung folgt
  5. Bei Abschluss: GitHub-Issue schließen mit Verweis auf Confluence

Vorteil:
  - Schönere Formatierung als GitHub Issues
  - Zusammenhänge lesbar darstellen
  - Erkenntnisse konservieren
  - Tiefere Integration-Tests dokumentieren


2.5 Externe Tickets / E-Mail → GitHub / Jira Routing
-----------------------------------------------------

Wenn Feedback von außen über Jira oder E-Mail kommt:

  Workflow:
  1. Kunde meldet über Portal (wird in Jira erfasst)
     oder meldet per E-Mail
  2. EUMAXL prüft den Input
  3. EUMAXL erstellt oder referenziert GitHub Issue
  4. Jira-Ticket wird mit GitHub-Issue-Link aktualisiert
  5. DEV-Schleife läuft über GitHub

  Regel: Alles was bleiben soll landet in GitHub.
  Jira ist Zwischenschicht für Notizen, nicht Speicher.


================================================================================
3. KUNDENFEEDBACK-SCHLEIFE (EXTERN)
================================================================================

3.1 Entry Point: Portal + GitHub README
---------------------------------------

Kunden erhalten Feedback-Instruktionen über zwei Wege:

  a) Portal (statische Seiten, manuell gepflegt)
  b) GitHub README (dynamisch, verlinkt auf Portal)

Workflow Kunde:
  1. Kunde liest GitHub README
  2. README verweist auf Portal für Details
  3. Kunde kann GitHub-Issue direkt öffnen (Quelle-Repos)
  4. Oder: Kunde nutzt Portal zum melden (wird in Jira erfasst)


3.2 Drei Kundenfeedback-Kanäle
------------------------------

Kanal 1: GitHub-Issue (direkt)
  - Kunde öffnet Issue im Repository
  - Direkter Kanal zur Quelle der Wahrheit
  - DEV antwortet auf GitHub
  - Keine Umleitung nötig

Kanal 2: Portal / JSM (strukturiert)
  - Kunde füllt Formular im Portal
  - Kategorien: Bug, Feature Request, Frage
  - Ticket landet in Jira (EUMAXL prüft)
  - EUMAXL erstellt GitHub Issue und verlinkt zurück

Kanal 3: E-Mail (Fallback, nicht geplant)
  - Sollte nicht regelmäßig vorkommen
  - Falls doch: EUMAXL nimmt auf, erstellt GitHub Issue
  - Ansonsten: Kunde wird auf GitHub / Portal verwiesen


3.3 Kundensicht: Was sieht der Beta-Kunde?
------------------------------------------

Aus Kundenperspektive sieht es so aus:

  "Ich will Feedback geben:"
  
  1. Ich öffne GitHub README (primary entry point)
     → Dort steht: "Report Bugs / Requests hier"
  
  2. Ich lese: "GitHub Issues oder Portal verfügbar"
     → GitHub: Direkt, schnell, öffentlich
     → Portal: Strukturiert, Kategorien, Antwort garantiert
  
  3. Ich wähle einen Weg:
     - GitHub Issue öffnen (Quelle-Repo direkt)
     - Portal-Formular ausfüllen (strukturiert)
  
  4. Ich bekomme Antwort:
     - GitHub: DEV antwortet auf Issue
     - Portal: EUMAXL oder Team antwortet (Jira-Ticket)


Kunde sieht nicht: Die interne Jira/Confluence Maschinerie.
Kunde sieht: GitHub ist Quelle, Portal ist Anleitung.


3.4 Feedback-Kategorien (Portal)
--------------------------------

Struktur ist einfach und selbsterklärend:

  [ BUG ]
    - Etwas funktioniert nicht richtig
    - Beschreibung + Schritte zur Reproduktion
    → Landet in Jira, wird zu GitHub Issue

  [ FEATURE REQUEST ]
    - Wunsch für neue Funktionalität
    - Beschreibung + Usecase
    → Landet in Jira, wird in Backlog-Analyse geleitet

  [ FRAGE / HILFE ]
    - Technische Frage
    - Wie funktioniert X?
    → Landet in Jira, wird an EUMAXL oder Dokumentation geleitet


================================================================================
4. ROLLEN UND VERANTWORTUNG
================================================================================

EUMAXL (Entwickler/Gatekeeper)
────────────────────────────
  Verantwortung:
  - GitHub Issues prüfen und triagieren
  - Jira-Tickets (extern eingegangen) zu GitHub-Issues verbinden
  - Confluence-Dokumentation für komplexe Themen schreiben
  - Portal-Inhalte manuell aktualisieren (dynamische Anpassungen)
  - DEV-Gruppen-Kommunikation koordinieren

  Entscheidungshoheit:
  - Wann wird Issue im Backlog priorisiert?
  - Welcher Dev-Story wird zugeordnet?
  - Wie wird Kunde antwortet (GitHub Kommentar oder Portal)?


DEV-Team
────────
  Verantwortung:
  - Jira-Tickets sehen für aktuelle Sprints
  - GitHub implementieren (Commits, PRs)
  - Code Review mit anderen Devs
  - (Derzeit: Nur EUMAXL, Rollen können später wachsen)


Kunden (Beta)
─────────────
  Verantwortung:
  - Feedback strukturiert einbringen (GitHub oder Portal)
  - Schritte zur Reproduktion geben wenn Bug
  - Ausreichend Details für Verständnis

  Erwartung:
  - GitHub: DEV antwortet zeitnah
  - Portal: Antwort in 2–5 Arbeitstagen


================================================================================
5. KONKRETE WORKFLOWS
================================================================================

5.1 Workflow A: Kunde meldet Bug über GitHub
──────────────────────────────────────────
  1. Kunde öffnet GitHub Issue im Core-Repository
  2. Beschreibung: Was tun, was erwartete, was ist falsch
  3. EUMAXL notiert: "Reproduzierbar? Welcher Step?"
  4. Kunde antwortet auf GitHub
  5. EUMAXL priorisiert: Backlog oder sofort fixen?
  6. Dev-Implementation (lokal)
  7. Commit mit Verweis auf Issue: "fixes #123"
  8. PR merged, Issue closes automatisch
  9. Kunde sieht auf GitHub: Issue ist geschlossen + Commit-Link


5.2 Workflow B: Kunde meldet Bug über Portal
──────────────────────────────────────────
  1. Kunde füllt Portal-Formular: Bug + Beschreibung
  2. Ticket landet in Jira
  3. EUMAXL prüft Jira-Ticket
  4. EUMAXL prüft Reproduzierbarkeit
  5. EUMAXL erstellt GitHub Issue (oder verlinkt existierenden)
  6. GitHub Issue wird im Jira-Ticket verlinkt
  7. Kunde erhält Benachrichtigung (via Portal): "Danke, Issue #234 wurde erstellt"
  8. Kunde kann auf GitHub folgen oder wartet auf nächste Mitteilung
  9. Bei Fix: GitHub-Issue geschlossen, Jira-Ticket geschlossen


5.3 Workflow C: Interne Erkenntnis → GitHub Issue
─────────────────────────────────────────────
  1. Dev oder EUMAXL entdeckt Problem bei Entwicklung
  2. Issue wird auf GitHub geöffnet
  3. Optional: Confluence-Seite für tiefere Analyse
  4. Implementierung folgt
  5. Issue geschlossen


5.4 Workflow D: Feature Request Kundenseite
──────────────────────────────────────────
  1. Kunde meldet Feature Request über Portal oder GitHub
  2. EUMAXL notiert: "Interessant, aber Backlog — nicht Priority"
  3. GitHub Issue mit Label "enhancement" + "backlog"
  4. Fließt in strategische Planung (später, nicht sofort)
  5. Bei Entscheidung zur Umsetzung: In Sprint aufnehmen


================================================================================
6. BESONDERHEITEN UND GRENZEN
================================================================================

6.1 GitHub ist öffentlich
-------------------------
  ✓ Vorteil: Transparenz, Kunden können mitverfolgen
  ✓ Vorteil: Suchbar für andere mit ähnlichen Problemen
  ✗ Limit: Keine internen Diskussionen dort (keine vertraulichen Infos)
  
  Regelung: Interne Details gehen in Confluence (privat) oder direkt
  zu EUMAXL, nicht in GitHub Issues.


6.2 Jira ist fragmentiert — das ist ok
--------------------------------------
  ✓ Jira muss nicht 1:1 mit GitHub synced sein
  ✓ Jira ist Notiz-System, nicht Quelle der Wahrheit
  ✓ Divergenz ist akzeptabel
  
  Bsp: GitHub-Issue hat 3 Sub-Tasks, Jira-Ticket hat nur 1 Notiz.
  Das ist bewusst, kein Fehler.


6.3 Confluence ist für Tiefe
-----------------------------
  GitHub Issue: "CSV Import fehlgeschlagen — Fehler X"
  Confluence: "Tiefere Analyse, Root Cause, gelöste Alternative, Tests"
  
  Nicht alles gehört in kurze Issues. Confluence ist Lehr-Raum.


6.4 Portal wird manuell gepflegt
--------------------------------
  ✓ EUMAXL kontrolliert Portal-Inhalte manuell
  ✓ Keine automatische Sync aus GitHub (würde schiefgehen)
  ✓ Portal zeigt Status, Link zu GitHub, Kategorien
  ✓ Dynamische Anpassung ohne Doku-Nachzug nötig
  
  Beispiel: "Wir merzen gerade ein Thema auf" → Portal-Update sofort.
  GitHub-README muss nicht angepasst werden.


================================================================================
7. FEHLER VERMEIDEN
================================================================================

❌ NICHT TUN:
  - GitHub und Jira synced halten (Doppelarbeit)
  - E-Mail als primärer Kanal verwenden (wird übersehen)
  - Kundenfeedback nur in Jira speichern (nicht öffentlich)
  - Confluence als Ticket-System nutzen (dafür ist GitHub)
  - Portal-Formular automatisieren (EUMAXL kontrolliert manuell)

✓ TUN:
  - GitHub Issue öffnen bei jedem relevanten Feedback
  - Jira optional als Team-Übersicht nutzen
  - Confluence für tiefe Dokumentation
  - Portal statisch/manuell halten für Kontrolle
  - README in GitHub immer aktuell (Primary URL)


================================================================================
8. INTEGRATION-TESTING DER SCHLEIFEN
================================================================================

Die Feedbackschleifen sind integriert getestet worden:

  ✓ GitHub-Issue → Jira-Sync funktioniert (manuell, bewusst fragmented)
  ✓ Confluence-Links in GitHub-Issues funktionieren
  ✓ Portal-Formular → Jira-Ticket funktioniert
  ✓ Jira-Ticket → GitHub-Issue Verkettung funktioniert
  ✓ Kunde sieht kohärente Reise: Portal → GitHub → Antwort

Lesbar-Test:
  Beta-Kunde kann:
  - GitHub-README verstehen
  - Portal-Anleitung folgen
  - Wissen wo er meldet (GitHub oder Portal)
  - Auf Antwort warten ohne Verwirrung


================================================================================
9. ZUSAMMENFASSUNG FÜR SCHNELLEINSTIEG
================================================================================

Wenn jemand neu ist — kurz und knackig:

DEV-Schleife:
  → GitHub Issue ist Startpunkt
  → Optional: Jira-Ticket für Team-Sicht
  → Optional: Confluence für tiefe Analyse
  → Quelle der Wahrheit: GitHub

Kundenschleife:
  → Portal oder GitHub-Issue
  → Beides landet am Ende bei GitHub
  → EUMAXL routet intern
  → Antwort: GitHub Kommentar oder Portal-Mitteilung

Kernregel:
  "Alles relevante geht zu GitHub. GitHub ist öffentlich, transparent,
   versionskontrolliert. Der Rest ist Spiegel und Ergänzung."


================================================================================
10. BEZÜGE
================================================================================

STAGE6_ZIELE.md                   S6-Z2 Ziel (Feedbackschleifen definieren)
FREEZE-6.md                       Atlassian-Setup Beschreibung
Global_GOV_S5.md                  GOV 13 (Feedback-Kanäle)
README.md (GitHub)                Entry Point für externe Kunden


================================================================================
HOW2 – Feedbackschleifen in R+MUNI | S6 | 2026-03-21 | R+MUNI Blueprint
Dokumentiert nach: Bestehende funktionierende Praxis
Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
