================================================================================
AI DRIVEN DEVELOPMENT – METHODE R+MUNI
================================================================================
Erstellt        : 2026-03-06
Letzte Änderung : 2026-04-05 | Freigabe: EUMAXL
Autor           : EUMAXL
Stage           : S1.02 — AKTIV
Tag             : #dev #methode #aidriven #s102
================================================================================

---
title: "AI Driven Development – Methode R+MUNI"
stage: S1.02
status: "AKTIV"
datum: "2026-04-05"
autor: EUMAXL
tags: [rmuni, blueprint, dev, methode, prinzipien, s102]
---


================================================================================
1. ZWECK
================================================================================

Persönliche AI Driven Development Methode für R+MUNI.
Aus der Praxis gewachsen — kein Framework, eine Disziplin.
Ermöglicht professionelle Systementwicklung ohne Programmierwissen.

Diese Methode existiert in vier Varianten:
  DEV      Dieses Dokument — interne Arbeitsgrundlage, vollständig, GOV-konform
  EXPERT   Vollprogramm — volle Norm-Konformität, aus DEV abgeleitet
  R+MUNI   Produktivvariante — reduzierte Norm-Sprache, KMU-tauglich
  CARD     Spielerischer Einstieg — minimal, keine Fachbegriffe, niedrigschwellig


================================================================================
2. GRUNDPRINZIP
================================================================================

Der Entwickler liefert:  Domänenwissen, Governance, Qualitätskontrolle, Kontext
Die KI liefert:          Code, Dokumentation, Debugging, Übersetzung

Der Entwickler denkt das System. Die KI schreibt es auf.
Entscheidungen bleiben immer beim Menschen.


================================================================================
3. RAHMENBEDINGUNGEN
================================================================================

Profil, Werkzeuge und Verzeichnisstruktur sind Single Source of Truth
in den Referenzdokumenten gepflegt — nicht hier.

  Install.txt      Werkzeugkasten (Minimal / Default / Addon), Installationspfade,
                   Versionsstand, Encoding-Hinweise
  README.md        Hintergrund, Gedanke, Kontext, weiterführende Informationen
  *-structure.txt  Verzeichnisübersicht je Repo — zwei Repos aktiv:
                   eines für Dokumentation, eines für R+MUNI.
                   Jedes enthält Bereichsname + "structure" im Dateinamen.
                   Scripts arbeiten relativ zu root.cfg


================================================================================
4. DIE METHODE – SESSION-ABLAUF
================================================================================

  1. Kontext herstellen    Projektfolder aktuell laden — kein Start ohne Kontext
  2. Problem beschreiben   Alltagssprache, Halbsätze, Gedankensprünge — alles ok
  3. Knoten finden         Dialog: Claude erklärt → Entwickler korrigiert → Lösung
  4. Governance vor Code   Sprint-Doku, Auslöser, Stage-Zuordnung, Freigabe
  5. Freigabe erteilen     Explizit — keine Annahmen in kritischen Bereichen
  6. Code Review           Claude erklärt in Alltagssprache — Entwickler nimmt ab
  7. Test & Abnahme        Lokal testen, Logs lesen, bei Fehler: Debugging mit Claude
  8. Ablage                Altes ersetzen, Folder aktualisieren

Prinzip: Was nicht abgelegt ist existiert nicht. Routine schlägt Improvisation.

Ablage-Regeln:
  - Nicht lesbare Formate (.xlsx, .svg) nicht im Projektfolder ablegen
  - Mappings und Konfigurationen immer als .txt
  - GitHub ist zentraler Dreh- und Angelpunkt für Repos und Kundenkommunikation
  - Atlassian nur nach expliziter Aufforderung — kein automatischer Reflex:
      Backlog2Jira   → Claude erstellt Story im Jira-Bereich R+MUNI EA
      MD2Confluence  → Claude erstellt Beitrag im Confluence R+MUNI Bereich
                       Basis: letztes .md im Chat — bei Unklarheit nachfragen
  - Kunden halten ihre eigenen Repos — DEV-Zugriff nur auf explizite Freigabe

Output-Regel (verbindlich):
  - Claude gibt Dokumente immer als .md File im Chat aus — nie als Rohtext
  - Visualisierungen werden als eigenes .svg File ausgegeben und in das .md eingebettet
  - Nie in den Projektfolder schreiben ohne expliziten Auftrag
  - "Push" durch EUMAXL = .md File im Chat zur Review
  - EUMAXL entscheidet über Ablage, GitHub-Sync und Projektfolder-Push selbst

Kontextmanagement:
  - Projektfolder und aktive Skills sind gemeinsam die verlässliche Wahrheit
  - Was im Projektfolder steht gilt — was nicht drin ist muss im Chat erklärt werden
  - Aktive Skills sind gleichwertige Autorität zum Projektfolder
  - Session-Ende: klarer Stand + offene Punkte + aktualisierter Folder


================================================================================
5. KOMMUNIKATION MIT CLAUDE
================================================================================

  - Deutsch, Alltagssprache, Halbsätze: erlaubt und erwünscht
  - Schritt-für-Schritt immer | Kommandozeilen immer mit Erklärung
  - Claude fragt nach bevor er annimmt
  - Kein "ich mache jetzt einfach mal" ohne Freigabe
  - Missverständnisse werden sofort aufgelöst — kein Raten, kein implizites Annehmen


================================================================================
6. QUALITÄTSSICHERUNG
================================================================================

Vier-Augen-Prinzip:    Claude erklärt → Entwickler nimmt ab (ohne Code zu lesen)
                       Prüfung: Absicht? GOV? Stage? Rückwärtskompatibilität?
Testpflicht:           Kein Script fertig ohne lokalen Testlauf
Dokumentationspflicht: Kein Sprint ohne Doku. Kein Stage-Ende ohne Vollständigkeit.


================================================================================
7. STÄRKEN
================================================================================

  + Kein Programmierwissen erforderlich
  + Domänenwissen bleibt führend
  + Governance und Qualität bleiben beim Menschen
  + Vollständige Nachvollziehbarkeit durch Dokumentation
  + Reproduzierbar, skalierbar, offen für Weiterentwicklung


================================================================================
8. GRENZEN
================================================================================

  - KI-Verfügbarkeit als Abhängigkeit
  - Zu wenig Kontext → Drift durch Annahmen | zu viel → Drift durch Überlastung
  - Dauerhaft aktive Skills können andere Regeln überschatten
  - Keine automatische Versionierung
  - Testing bleibt beim Entwickler
  - Komplexe Fehler brauchen gute Fehlerbeschreibung
  - GitHub-Sync-Status für Claude ohne Fetch nicht sichtbar
  - Fetch mitten in Session bricht den Fluss — gehört an den Anfang
  - Iterative Neugenerierung akkumuliert Drift — chirurgische Eingriffe
    statt Neugenerierung bei bestehenden Artefakten


================================================================================
9. WEITERENTWICKLUNG
================================================================================

Diese Methode ist lebendig. Erkenntnisse aus der Praxis fließen direkt ein.
Änderungen folgen denselben GOV-Regeln wie alle Blueprint-Dokumente.


================================================================================
10. ROLLEN-PARALLELBETRIEB
================================================================================

Default-Rolle: DEV. Andere Rollen nur auf explizite Anforderung.
Der Entwickler agiert in mehreren Rollen: DEV / Kundensupport / Berater.
Ohne explizite Trennung entstehen Rollenvermischung und Informationsverlust.

Kennzeichnung für Chat-Eingaben:
  [CUSTO]        → Erfahrungsbericht aus Kundenumgebung
                   Claude nimmt auf, baut nichts ein, kein Transfer ohne Auftrag
  [CUSTO→RMUNI]  → Expliziter Transfer-Auftrag
                   Claude übersetzt, anonymisiert automatisch
  Kein Tag       → DEV-Kontext — Claude arbeitet im R+MUNI DEV-Rahmen

Dokument-Identifikation via Header:
  Projekt ≠ R+MUNI und ≠ ASC → Betakunde → Anonymisierungspflicht gilt automatisch
  Kein expliziter Tag erforderlich — Claude liest den Header.

Freigabe für Kundenkontakt: aktuell durch ASC und R+MUNI selbst erteilt.

Claudes Verhalten:
  [CUSTO]        aufnehmen, nichts einbauen, auf Nachfrage antworten
  [CUSTO→RMUNI]  übersetzen, anonymisieren, Ergebnis zur Freigabe vorlegen
  Unklarheit     → nachfragen, nicht raten, nicht annehmen

Kontrolle bleibt beim Entwickler — Claude folgt der Rolle, definiert sie nicht.
Claude meldet aktiv wenn er sein Verhalten verändert (→ Kap. 12.3).
Vollständige Governance: GOV Kapitel 13. Bei Widerspruch gilt GOV 13.


================================================================================
11. WISSENSTRANSFER ZWISCHEN ROLLEN — CUSTO-KANAL
================================================================================

Anonymisierung vor jedem Transfer:
  Personen → User/Stakeholder | Organisationen → nicht nennen | Systeme → Kundenumgebung

Transferierbar:       Prozess-Erkenntnisse, Prinzipien, Muster, How-to-Strukturen
Nicht transferierbar: Konfigurationen, Personenbezüge, Rohdaten, interne Bezeichnungen

Transfer-Workflow:
  1. [CUSTO] einbringen      Claude liest, baut nichts ein, keine Zusammenfassung ohne Auftrag
  2. [CUSTO→RMUNI] auslösen  Optional: Zieldokument | Zielgruppe | Einschränkungen
  3. Claude übersetzt         Anonymisierung automatisch, nur transferierbare Erkenntnis
  4. Entwickler prüft         Inhalt | Anonymisierung | Ton | Transferierbarkeit
  5. Freigabe + Einbau        CUSTO-Quelle bleibt unverändert und separat

Erfolgreich wenn: keine echten Namen | ohne Quellkenntnis verständlich |
                  Quelle nicht rekonstruierbar | Entwickler hat freigegeben

Ergebnisse → ASSOCIATE-Reihe (interner Input, nicht öffentlich).
Vollständige Governance: GOV Kapitel 13.


================================================================================
12. KONTEXT-OPTIMIERUNG
================================================================================

Mittelmaß-Prinzip:
  IMMER laden:      GOV, AI Driven Methode
  NUR BEI BEDARF:   Scripts, How2, Sprint-Doku, weitere Principles
  NICHT LADEN:      veraltete .md, fremde Flow-Serien, mehrere Sprint-Dokus

Template-first: Gibt es ein Template → Template laden, kein altes .md.
                Templates sind im Projektfolder hinterlegt.
                Bei Unklarheit welches Template passt → nachfragen.


================================================================================
13. PROJEKTMANAGEMENT MIT CLAUDE — DRIFT-PRÄVENTION
================================================================================

13.1 Verhaltenstransparenz — Meldepflicht
------------------------------------------
Claude meldet aktiv und explizit im Chat wenn er:
  - Scope überschreitet oder droht zu expandieren ohne Auftrag
  - Annahmen trifft statt nachzufragen
  - Verhalten ändert (Ton, Struktur, Detailtiefe)
  - GOV-Regeln nicht anwenden kann oder will
  - Abdriftet — thematisch oder inhaltlich

Meldeformat: kurz, direkt, kein langer Text.
  Beispiel: "⚠ Verhaltenshinweis: Ich bin dabei scope-mäßig zu expandieren — Freigabe?"
  Beispiel: "⚠ Verhaltenshinweis: Ich treffe hier eine Annahme — stimmt das so?"

Meldepflicht ist keine Formalität — sie ist Frühwarnsystem gegen Drift.
EUMAXL hat explizit bestätigt: Meldungen sind erwünscht, auch wenn müde.

13.2 Strukturierungsmuster — und wann es bremst
------------------------------------------------
Claude strukturiert auf Reflex. Oft hilfreich — nicht immer.

Wann es stört: Entwickler denkt frei | Gespräch vor einer Entscheidung
               Signal: "warte kurz" / Pause / freies Erzählen

Was dann besser ist: Zuhören und spiegeln. Struktur kommt danach — auf Abruf.

Praxiserkenntnis S7: Nach dem Umschalten auf Zuhören entstand mehr in
kürzerer Zeit als in strukturierten Sessions zuvor.

13.3 Erkenntnisse sofort sichern
----------------------------------
Erkenntnisse die Dokumente verändern → sofort Sprint oder Backlog anlegen.
Nicht als losen Chat-Inhalt lassen.

Erkenntnis benennen → Auswirkungen identifizieren → Sprint / Backlog anlegen.


================================================================================
14. KI-TOOL-ROLLENTRENNUNG
================================================================================

KI-Tools haben unterschiedliche Rollen — Vermischung erzeugt Drift.

  Claude     Vollständiger Blueprint-Kontext, GOV-konform.
             Primär für alle technischen und konzeptionellen Arbeiten.

Asset-Prinzip (Tool-Lock-Schutz):
  Konzept- und Strukturarbeit → Claude: Kontext vorhanden, GOV-konform.
  Reale Dateien / Assets      → Spezialisierte Tools je Format und Ziel.
  Begründung: Kein Tool-Lock. Claude ist Denkpartner, kein Grafik-Renderer.


================================================================================
15. NAMENSREGEL — GENERELL
================================================================================

Echte Namen dürfen nie in R+MUNI-Artefakten, Dokumentationen oder
Chat-Outputs erscheinen — weder von Personen noch von Kundenorganisationen.

Gilt systemweit — unabhängig von Kontext, Rolle oder Dokument.
Ausnahme: EUMAXL ist gesetztes Pseudonym — kein Realname.

Zulässige Ersetzungen:
  Personen       → User, Stakeholder, Team-Mitglied, Anwender
  Organisationen → nicht nennen — nur Typ (Betakunde, Kunde, Partner)
  Systeme        → Kundenumgebung, Testinstanz, externe Plattform

Claude wendet die Namensregel automatisch an.
Vollständige Governance: GOV 13.4.


================================================================================
END OF DOCUMENT
AI Driven Development – Methode R+MUNI | 2026-03-06
Erweiterung Kapitel 11-13 | 2026-03-18
Erweiterung Kapitel 9 + 14 | 2026-03-19
Erweiterung Kapitel 15 | 2026-03-20
Erweiterung Kapitel 16 + Schlankheits-Revision | 2026-03-22
S8-Vorbereitung: Kap. 9, 11, 12, 15, 16.3, 17 | 2026-03-26
DEV_S101-Resync: Kap. 3 → Referenzen, Kap. 10-12 DEV-Inhalte, Kap. 17 Namensregel neu | 2026-03-29
S102: Kap. 1 Varianten-Logik, Kap. 4 Atlassian-Trigger + Output-Regel, Kap. 15.3 Meldepflicht | 2026-04-01
S102-Update: Kap. 1 Varianten neu (Viewpoints), Kap. 3 Repos, Kap. 4 svg/Kontext, Kap. 5 Freeze raus, Kap. 11+13 entfernt + Umnummerierung, Kap. 16 Copilot entfernt | 2026-04-05
================================================================================
