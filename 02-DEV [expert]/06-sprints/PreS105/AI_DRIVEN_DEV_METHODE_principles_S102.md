================================================================================
AI DRIVEN DEV METHODE — PRINCIPLES
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : principles_AI_DRIVEN_DEV_METHODE
Tag             : #principles #aidriven #dev #methode #s102
Datum           : 2026-04-06
Stage           : S1.02 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================


ZWECK DIESES DOKUMENTS
--------------------------------------------------------------------------------
Was erklärt dieses Dokument — und für wen.

Zielgruppe: DEV

Dieses Dokument erklärt:
  - Was AI Driven Development im R+MUNI-Kontext bedeutet
  - Welche Grundprinzipien jede Entwicklungssession tragen
  - Was der Entwickler mitbringen muss — und was die KI übernimmt
  - Was dieses Dokument nicht leistet (Ablauf → How2, Governance → GOV)


================================================================================
1. WAS IST AI DRIVEN DEVELOPMENT?
================================================================================

AI Driven Development ist eine persönliche Arbeitsmethode für professionelle
Systementwicklung ohne Programmierwissen. Entwickelt aus der Praxis — kein
Framework, keine Theorie, eine Disziplin.

Der Kern: Der Entwickler denkt das System. Die KI schreibt es auf.

Kurz gesagt:
  Domänenwissen + Governance beim Menschen — Code, Dokumentation, Debugging bei der KI.

Warum das relevant ist:
  Komplexe Systeme entstehen ohne klassische Programmierkenntnisse.
  Qualität, Entscheidungshoheit und Nachvollziehbarkeit bleiben beim Entwickler.
  Die KI ist Werkzeug — kein Entscheider.


================================================================================
2. WAS DIE ZIELGRUPPE DAVON HAT
================================================================================

AI Driven Development ermöglicht:
  - Professionelle Script-Entwicklung ohne Syntax-Kenntnisse
  - Strukturierte Dokumentation ohne Schreibaufwand
  - Debugging durch Dialog statt durch Code-Lesen
  - Reproduzierbare Entwicklung durch konsequente Governance

Was es nicht leistet:
  - Kein Ersatz für Domänenwissen — das bleibt beim Entwickler
  - Kein automatisches Testing — Testpflicht liegt beim Entwickler
  - Kein selbstständiges Ablegen oder Versionieren — das ist Entwickleraufgabe
  - Kein Betrieb ohne Kontext — ohne Projektfolder entsteht Drift


================================================================================
3. GRUNDPRINZIPIEN
================================================================================

3.1 Der Mensch entscheidet — immer
------------------------------------
Entscheidungen — inhaltlich, strukturell, normativ — liegen beim Entwickler.
Die KI macht Vorschläge, erklärt, formuliert. Sie entscheidet nicht.

Konkret bedeutet das:
  Kein "ich mache das jetzt einfach" ohne explizite Freigabe.
  Freigabe ist explizit — kein Nicken, kein Schweigen, kein Implizit.


3.2 Kontext vor Code
---------------------
Jede Session beginnt mit Kontext. Kein Kontext — keine verlässliche Arbeit.
Projektfolder und aktive Skills sind die gemeinsame Wahrheit.

Konkret bedeutet das:
  Projektfolder laden, dann beschreiben — nicht andersherum.
  Was nicht im Folder steht muss im Chat erklärt werden.


3.3 Governance vor Tempo
--------------------------
Governance ist kein Bremser — sie ist Qualitätssicherung.
Sprint-Doku, Stage-Zuordnung, Freigabe kommen vor dem Code.

Konkret bedeutet das:
  Kein Script fertig ohne Testlauf.
  Kein Sprint ohne Dokumentation.
  Kein Stage-Ende ohne Vollständigkeit.


3.4 Transparenz als Frühwarnsystem
------------------------------------
Die KI meldet aktiv wenn sie Scope überschreitet, Annahmen trifft oder abdriftet.
Meldungen sind erwünscht — auch wenn unbequem.

Konkret bedeutet das:
  "⚠ Verhaltenshinweis: Ich treffe hier eine Annahme — stimmt das so?"
  Meldungen sind kein Fehler — sie sind das System das funktioniert.


3.5 Was nicht abgelegt ist existiert nicht
-------------------------------------------
Erkenntnisse, Entscheidungen und Artefakte die nicht abgelegt sind
sind für den nächsten Sprint verloren.

Konkret bedeutet das:
  Erkenntnis → sofort Sprint oder Backlog anlegen.
  Artefakte → Ablageort im Sprint dokumentieren.
  Routine schlägt Improvisation.


3.6 Mittelmaß beim Kontext — kein Laden ohne Bedarf
-----------------------------------------------------
Zu wenig Kontext erzeugt Drift durch Annahmen.
Zu viel Kontext erzeugt Drift durch Überlastung.

Konkret bedeutet das:
  IMMER laden:    GOV, AI Driven Methode
  NUR BEI BEDARF: Scripts, How2, Sprint-Doku, weitere Principles
  NICHT LADEN:    veraltete .md, fremde Flow-Serien, mehrere Sprint-Dokus gleichzeitig


3.7 Anonymisierung — systemweit
---------------------------------
Echte Namen erscheinen nie in R+MUNI-Artefakten, Dokumentationen oder Chat-Outputs.
Weder Personen noch Kundenorganisationen.

Konkret bedeutet das:
  Personen       → User, Stakeholder, Team-Mitglied, Anwender
  Organisationen → nicht nennen — nur Typ (Betakunde, Kunde, Partner)
  Ausnahme: EUMAXL ist gesetztes Pseudonym — kein Realname.


================================================================================
4. VORAUSSETZUNGEN
================================================================================

Bevor du mit AI Driven Development arbeitest:
  - R+MUNI ist installiert und der erste Funktionstest war grün
  - root.cfg vorhanden und <rootfolder> korrekt gesetzt
  - Claude Pro (oder gleichwertiges Modell) verfügbar
  - Projektfolder aktuell und vollständig geladen
  - [[Global_GOV_S102]] gelesen — normative Grundlage bekannt
  - Bewusstsein: KI-Verfügbarkeit ist eine Abhängigkeit — Fallback kennen


================================================================================
5. ABGRENZUNG UND GRENZEN
================================================================================

AI Driven Development ist Teil von R+MUNI — aber nicht alles.

Was hier geregelt ist:
  - Zusammenarbeit zwischen Entwickler und KI
  - Prinzipien für Session-Ablauf, Kontext, Qualität und Governance
  - Grundverständnis für alle DEV-Rollen

Was woanders geregelt ist:
  - Konkreter Session-Ablauf, Script-Aufrufe → [[AI_DRIVEN_DEV_METHODE_How2_DEV_S102]]
  - Normative Grundlage für alle Entscheidungen → [[Global_GOV_S102]]
  - Werkzeuge, Versionen, Installationspfade → Install.txt
  - Verzeichnisstruktur und Repos → *-structure.txt


================================================================================
SUPPORT UND FEEDBACK
================================================================================

Fragen oder etwas unklar?

→ Ticketsystem: https://ims-blueprint-ticketsystem.atlassian.net/helpcenter/RMNP/


================================================================================
AI_DRIVEN_DEV_METHODE_principles | S1.02 | 2026-04-06 | R+MUNI Blueprint
================================================================================
