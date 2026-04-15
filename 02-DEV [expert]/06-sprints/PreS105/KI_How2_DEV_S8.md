================================================================================
KI – MIT KÜNSTLICHER INTELLIGENZ ARBEITEN — HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : KI_How2_DEV_S8
Tag             : #dev #how2 #ki #kuenstlicheintelligenz #s8
Datum           : 2026-03-26
Stage           : S8 — AKTIV
Status          : ENTWURF
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Hinweis         : Neu angelegt S8 — kein DEV-Gegenstück aus früheren Stages vorhanden
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[AI_DRIVEN_DEV_METHODE_S8]] gelesen — Grundprinzipien der Methodik bekannt
- [[KI_principles_Associate_S8]] bekannt — Zielgruppen-Kontext verstanden
- Zugang zu Claude Pro oder vergleichbarem KI-Tool


================================================================================
1. ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument beschreibt den operativen Einsatz von KI-Werkzeugen im
R+MUNI DEV-Kontext. Es ergänzt die AI_DRIVEN_DEV_METHODE um konkrete
Handlungsanweisungen für typische DEV-Aufgaben.

Abgrenzung:
  - Methodik und Philosophie → [[AI_DRIVEN_DEV_METHODE_S8]]
  - Associate-Nutzung → [[KI_How2_Associate_S8]]
  - Dieses Dokument: operative DEV-Referenz


================================================================================
2. KI-WERKZEUGE IM DEV-EINSATZ
================================================================================

2.1 Claude — primäres DEV-Werkzeug
------------------------------------
Claude ist das primäre KI-Werkzeug für alle technischen und konzeptionellen
Arbeiten im R+MUNI Blueprint.

Einsatzfelder:
  - Code generieren, debuggen, erklären
  - Dokumentation erstellen und reviewen
  - Entscheidungen strukturieren und dokumentieren
  - Sprint-Dokus verfassen
  - Kontext-Checks gegen GOV und Principles

Regel: Claude immer mit vollständigem Kontext starten.
       Projektfolder laden bevor komplexe Aufgaben beginnen.


2.2 Copilot — kontextfreies Explorationswerkzeug
-------------------------------------------------
Copilot wird bewusst ohne R+MUNI-Kontext eingesetzt.

Einsatzfelder:
  - Freie Exploration neuer Ideen
  - Sales-Dokumentation (ohne Blueprint-Interna)
  - Entscheidungsfindung ohne GOV-Overhead

Regel: Erkenntnisse aus Copilot-Sessions fließen als [BETA→RMUNI]
       kontrolliert in den R+MUNI Kontext ein — nie direkt.
       Vollständige Governance: [[Global_GOV_S8]] Kapitel 13.


2.3 Werkzeug-Disziplin
------------------------
Jedes KI-Werkzeug bleibt in seiner definierten Rolle.
Vermischung erzeugt Drift — GOV-konforme Trennung ist nicht optional.

Referenz: [[AI_DRIVEN_DEV_METHODE_S8]] Kapitel 17


================================================================================
3. SESSION-FÜHRUNG MIT CLAUDE
================================================================================

3.1 Session-Start
------------------
  Schritt 1: Projektfolder in Claude-Projekt laden (einmalig pro Projekt)
  Schritt 2: Rolle explizit definieren (Zielbegleitung / Sprint / Methodik)
  Schritt 3: Kontext benennen — Stage, Ziel, Abgrenzung

Beispiel:
  "Wir sind in Stage 8. Ziel ist S8-Z1 Beta 1.0 Release.
   Du hilfst mir heute beim Bereinigen der Dokumentation.
   Keine neuen Features, kein GOV-Umbau."


3.2 Freigabe-Disziplin
------------------------
  - Kein Output ohne explizite Freigabe durch EUMAXL
  - Strukturelle Änderungen → immer Rückfrage vor Ausführung
  - Inhaltliche Änderungen an bestehenden Dokumenten → Freigabe je Dokument

Regel: Was nicht freigegeben ist existiert nicht im Blueprint.


3.3 Verhaltenstransparenz (GOV-Anforderung)
--------------------------------------------
Claude meldet aktiv wenn er sein Verhalten verändert.
Referenz: [[AI_DRIVEN_DEV_METHODE_S8]] Kapitel 16.3


================================================================================
4. TYPISCHE FEHLERBILDER
================================================================================

FEHLER: Zu wenig Kontext gegeben
  → KI driftet in generische Antworten
  → Lösung: Stage, Ziel und Dokument explizit nennen

FEHLER: Kein Projektfolder geladen
  → KI kennt GOV, Principles und Entscheidungen nicht
  → Lösung: Immer mit aktuellem Projektfolder-Stand starten

FEHLER: Freigabe vergessen
  → KI hat Änderungen gemacht die nicht kontrolliert wurden
  → Lösung: Vier-Augen-Prinzip — Claude erklärt, EUMAXL nimmt ab

FEHLER: Rollenvermischung
  → DEV-Erkenntnisse fließen unkontrolliert in Copilot-Session
  → Lösung: Kanäle strikt trennen, [BETA→RMUNI]-Tag verwenden


================================================================================
SUPPORT UND FEEDBACK
================================================================================

→ Ticketsystem: https://ims-blueprint-ticketsystem.atlassian.net/helpcenter/RMNP/


================================================================================
KI_How2 | DEV | S8 | 2026-03-26 | R+MUNI Blueprint
================================================================================
