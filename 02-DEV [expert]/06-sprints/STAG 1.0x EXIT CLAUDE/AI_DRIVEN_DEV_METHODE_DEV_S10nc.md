================================================================================
AI DRIVEN DEVELOPMENT – METHODE R+MUNI
================================================================================
Erstellt        : 2026-03-06
Letzte Änderung : 2026-04-06 | Freigabe: EUMAXL
Autor           : EUMAXL
Stage           : S10nc — AKTIV
Tag             : #dev #methode #aidriven #s10nc
================================================================================

---
title: "AI Driven Development – Methode R+MUNI"
stage: S10nc
status: "AKTIV"
datum: "2026-04-06"
autor: EUMAXL
tags: [rmuni, blueprint, dev, methode, prinzipien, s10nc]
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
Das KI-Tool liefert:     Code, Dokumentation, Debugging, Übersetzung

Der Entwickler denkt das System. Das KI-Tool schreibt es auf.
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
  3. Knoten finden         Dialog: KI-Tool erklärt → Entwickler korrigiert → Lösung
  4. Governance vor Code   Sprint-Doku, Auslöser, Stage-Zuordnung, Freigabe
  5. Freigabe erteilen     Explizit — keine Annahmen in kritischen Bereichen
  6. Code Review           KI-Tool erklärt in Alltagssprache — Entwickler nimmt ab
  7. Test & Abnahme        Lokal testen, Logs lesen, bei Fehler: Debugging mit KI-Tool
  8. Ablage                Altes ersetzen, Folder aktualisieren

Prinzip: Was nicht abgelegt ist existiert nicht. Routine schlägt Improvisation.

Ablage-Regeln:
  - Nicht lesbare Formate (.xlsx, .svg) nicht im Projektfolder ablegen
  - Mappings und Konfigurationen immer als .txt
  - GitHub ist zentraler Dreh- und Angelpunkt für Repos und Kundenkommunikation
  - Atlassian nur nach expliziter Aufforderung — kein automatischer Reflex:
      Backlog2Jira   → KI-Tool erstellt Story im Jira-Bereich R+MUNI EA
      MD2Confluence  → KI-Tool erstellt Beitrag im Confluence R+MUNI Bereich
                       Basis: letztes .md im Chat — bei Unklarheit nachfragen
  - Kunden halten ihre eigenen Repos — DEV-Zugriff nur auf explizite Freigabe

Output-Regel (verbindlich):
  - Das KI-Tool gibt Dokumente immer als .md File im Chat aus — nie als Rohtext
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
5. KOMMUNIKATION MIT DEM KI-TOOL
================================================================================

  - Deutsch, Alltagssprache, Halbsätze: erlaubt und erwünscht
  - Schritt-für-Schritt immer | Kommandozeilen immer mit Erklärung
  - Das KI-Tool fragt nach bevor es annimmt
  - Kein "ich mache jetzt einfach mal" ohne Freigabe
  - Missverständnisse werden sofort aufgelöst — kein Raten, kein implizites Annehmen


================================================================================
6. QUALITÄTSSICHERUNG
================================================================================

Vier-Augen-Prinzip:    KI-Tool erklärt → Entwickler nimmt ab (ohne Code zu lesen)
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
  - GitHub-Sync-Status für das KI-Tool ohne Fetch nicht sichtbar
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
                   KI-Tool nimmt auf, baut nichts ein, kein Transfer ohne Auftrag
  [CUSTO→RMUNI]  → Expliziter Transfer-Auftrag
                   KI-Tool übersetzt, anonymisiert automatisch
  Kein Tag       → DEV-Kontext — KI-Tool arbeitet im R+MUNI DEV-Rahmen

Dokument-Identifikation via Header:
  Projekt ≠ R+MUNI und ≠ ASC → Betakunde → Anonymisierungspflicht gilt automatisch
  Kein expliziter Tag erforderlich — KI-Tool liest den Header.

Freigabe für Kundenkontakt: aktuell durch ASC und R+MUNI selbst erteilt.

Verhalten des KI-Tools:
  [CUSTO]        aufnehmen, nichts einbauen, auf Nachfrage antworten
  [CUSTO→RMUNI]  übersetzen, anonymisieren, Ergebnis zur Freigabe vorlegen
  Unklarheit     → nachfragen, nicht raten, nicht annehmen

Kontrolle bleibt beim Entwickler — das KI-Tool folgt der Rolle, definiert sie nicht.
Das KI-Tool meldet aktiv wenn es sein Verhalten verändert (→ Kap. 12.3).
Vollständige Governance: GOV Kapitel 13. Bei Widerspruch gilt GOV 13.


================================================================================
11. WISSENSTRANSFER ZWISCHEN ROLLEN — CUSTO-KANAL
================================================================================

Anonymisierung vor jedem Transfer:
  Personen → User/Stakeholder | Organisationen → nicht nennen | Systeme → Kundenumgebung

Transferierbar:       Prozess-Erkenntnisse, Prinzipien, Muster, How-to-Strukturen
Nicht transferierbar: Konfigurationen, Personenbezüge, Rohdaten, interne Bezeichnungen

Transfer-Workflow:
  1. [CUSTO] einbringen      KI-Tool liest, baut nichts ein, keine Zusammenfassung ohne Auftrag
  2. [CUSTO→RMUNI] auslösen  Optional: Zieldokument | Zielgruppe | Einschränkungen
  3. KI-Tool übersetzt        Anonymisierung automatisch, nur transferierbare Erkenntnis
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
13. PROJEKTMANAGEMENT — DRIFT-PRÄVENTION
================================================================================

13.1 Verhaltenstransparenz — Meldepflicht
------------------------------------------
Das KI-Tool meldet aktiv und explizit im Chat wenn es:
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
Das KI-Tool strukturiert auf Reflex. Oft hilfreich — nicht immer.

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

  Primäres KI-Tool    Vollständiger Blueprint-Kontext, GOV-konform.
                      Primär für alle technischen und konzeptionellen Arbeiten.

Asset-Prinzip (Tool-Lock-Schutz):
  Konzept- und Strukturarbeit → Primäres KI-Tool: Kontext vorhanden, GOV-konform.
  Reale Dateien / Assets      → Spezialisierte Tools je Format und Ziel.
  Begründung: Kein Tool-Lock. Das KI-Tool ist Denkpartner, kein Grafik-Renderer.


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

Das KI-Tool wendet die Namensregel automatisch an.
Vollständige Governance: GOV 13.4.


================================================================================
END OF DOCUMENT
AI Driven Development – Methode R+MUNI | 2026-03-06
S10nc: KI-Tool-Neutralisierung vollständig | 2026-04-06
================================================================================
