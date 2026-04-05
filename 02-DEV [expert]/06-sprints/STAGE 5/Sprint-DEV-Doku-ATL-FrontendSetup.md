================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-ATL-FrontendSetup — Atlassian Stage 5
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
Auslöser-Typ : Feature-Zuwachs (Stage-5-Ziel 4.1)

Begründung   : Stage 5 ist die erste Außenwirkungsphase von R+MUNI.
               Das Atlassian Free Bundle (Jira + Confluence + JSM/CSM)
               dient als standardisiertes Kundeninterface.

               Ziel: Kunde arbeitet selbstständig im Atlassian-Frontend.
               R+MUNI bleibt das Tool — Atlassian ist die Arbeitsschicht.

Fachlicher   : Endkunden erhalten einen definierten Kanal für
Mehrwert       Feedback, Support und Dokumentationszugang.
               Team erhält eine strukturierte Arbeitsplattform.
               Setup ist wiederholbar als Onboarding-Artefakt.

Abgrenzung   : Atlassian Frontend ist Präsentations- und Arbeitsschicht.
               Keine Logik, keine Führung — R+MUNI Scripts laufen
               vollständig unabhängig davon.


--------------------------------------------------------------------------------
2. ATLASSIAN FREE BUNDLE — ÜBERSICHT
--------------------------------------------------------------------------------

2.1 Produkt-Scope (Free Plan)
------------------------------
  Jira Software Free
    Vorgangsverwaltung intern (Entwicklung, Bugtracking)
    Öffentlich sichtbar — keine Kundentrennung nötig (bewusst)

  Confluence Free
    Wissensbasis und Dokumentation
    Öffentliche Seiten via Share-Link (kein Login nötig)
    1 Space für alle Kunden und Team (Free Plan Limit)

  Jira Service Management / Customer Service Management (CSM) Free
    Endkunden-Portal für Feedback und Supportanfragen
    Portal-only Customers: unbegrenzt, kostenlos
    3 Request-Typen: Bug, Feature Request, DEV Anfrage

2.2 Free Plan Bewertung
------------------------
  Ergebnis: Free Plan trägt den vollständigen R+MUNI Use Case.

  JSM/CSM Free : Portal funktioniert, keine SLA nötig
  Confluence Free: Öffentliche Seiten als Wissensbasis
  Jira Free    : Public, keine Kundentrennung nötig

  Grenze Free Plan: NICHT erreicht für aktuelle Beta-Phase.
  Kein Upgrade erforderlich.

  Hinweis: Auf Atlassian Free Plan Einschränkungen achten.
  Kostenpflichtige Features werden in R+MUNI bewusst nicht genutzt.


--------------------------------------------------------------------------------
3. PORTAL-SETUP (SPRINT-RMNP01 — 2026-03-09)
--------------------------------------------------------------------------------

3.1 Entscheidung Portal-Scope
------------------------------
A+B Modell:

  A) Feedback & Support-Kanal
     Kunde meldet Probleme, stellt Fragen, verfolgt Status.
     Kanal: JSM/CSM Portal (Portal-only Customer, unbegrenzt, kostenlos)

  B) Onboarding & Wissens-Selbstbedienung
     Kunde findet Dokumentation und Anleitungen.
     Kanal: Confluence öffentliche Seiten (Share-Link, kein Login)
     Confluence-Anbindung an Portal: eigener Sprint (zurückgestellt)

  Bewusst ausgeschlossen:
     Vertriebsanfragen — nicht über Portal
     Direkter Kundenaccount — optional, kein Zwang

3.2 Request-Typen
------------------
  Bug
    Vorgangstyp: Problem
    Felder: Zusammenfassung (P), Beschreibung (P),
            Affected services (O), Attachment (O)

  Feature Request
    Vorgangstyp: Suggestion
    Felder: Zusammenfassung (P), Beschreibung (P),
            Impact (O), Attachment (O)

  DEV Anfrage
    Vorgangstyp: Question (neu angelegt)
    Felder: Zusammenfassung (P), Beschreibung (P)
    Hinweis: ob daraus eine Leistung wird — situativ, workloadabhängig

  Legende: P = Pflichtfeld, O = Optionales Feld

3.3 Technische Erkenntnis
--------------------------
CSM Standard-Formular "Contact" ist System-reserviert (E-Mail-Kanal,
KI-Agent). Nicht als eigenständige Portal-Option platzierbar.
Lösung: Neuer dedizierter Issue-Typ für DEV Anfrage angelegt.

3.4 Kundenzugriff
------------------
  Einstellung: JEDER (offen)
  Begründung : R+MUNI Philosophie — Offenheit und Ehrlichkeit.
               Kein Registrierungszwang, kein Kontrollaufwand.

3.5 Portal-URL (Endkunden-Einstieg)
-------------------------------------
  https://ims-blueprint-ticketsystem.atlassian.net/helpcenter/RMNP/

3.6 Umsetzung — was wurde gemacht
-----------------------------------
  ✅ Altes RMUNI Service-Desk-Projekt in Papierkorb verschoben
  ✅ Neues CSM-Projekt angelegt
     Name: R+MUNI Portal | Key: RMNP | Typ: Customer Service Management
  ✅ Kundenerfahrung "R MUNI" konfiguriert
  ✅ Formular "Bug" erstellt (Vorgangstyp: Problem)
  ✅ Formular "Feature Request" erstellt (Vorgangstyp: Suggestion)
  ✅ Formular "DEV Anfrage" erstellt (neuer Vorgangstyp: Question)
  ✅ Kundenzugriff auf "Jeder" gesetzt
  ✅ Branding: Logo hinterlegt (Iteration folgt)
  ✅ Portal-URL verifiziert


--------------------------------------------------------------------------------
4. TEAM-SETUP IM ATLASSIAN BUNDLE
--------------------------------------------------------------------------------

4.1 User-Struktur (Stage 5, bis 10 User Free Plan)
----------------------------------------------------
  Betreiber (EUMAXL)
    Volle Rechte, Projektverantwortung
    Admin über alle Atlassian Produkte im Bundle

  Team User (COLUMBO — Einladung offen)
    Volle Atlassian-Rechte im R+MUNI Bundle
    Unterstützt im Atlassian-Umfeld
    Onboarding gemäß BETA ONBOARDING — MLAT Dokument

  Service User 1 (Claude)
    Konkrete Atlassian-Rolle wird in Stage 5 geklärt
    Option A: Rovo AI (Atlassian eigene KI-Integration)
    Option B: Prozessrolle (Benachrichtigungen, Ticket-Workflows)
    Status: OFFEN — kein Entscheid erforderlich für aktuelle Beta-Phase

  Service User 2
    Reserve — noch nicht vergeben

  Kunden
    Portal-only Customer (JSM) — unbegrenzt, kostenlos
    Kein Atlassian-Account nötig für Portal-Nutzung

4.2 Grundsatz Bundle-Nutzung
------------------------------
  Das Bundle wird optimal genutzt.
  Kein ungenutztes Potential, keine unnötige Komplexität.
  Free Plan reicht vollständig — kein Upgrade-Druck.


--------------------------------------------------------------------------------
5. CONFLUENCE — WISSENSBASIS
--------------------------------------------------------------------------------

5.1 Aktueller Stand
--------------------
  Confluence ist produktiv und unangetastet im Cleaning Run.
  Öffentliche Seiten via Share-Link verfügbar (kein Login).

5.2 Geplante Schritte (eigene Sprints)
---------------------------------------
  [ ] Confluence FAQ-Seite erstellen und an Portal verlinken
  [ ] Portal-URL in Confluence R+MUNI Hauptseite publizieren
  [ ] Strukturierter Aufbau der öffentlichen Wissensbasis
  [ ] How2 und Anleitungen aus Blueprint in Confluence überführen

5.3 Abgrenzung
---------------
  Confluence ist Präsentationsschicht — keine Logik.
  Verknüpfung mit Portal ist ein bewusster eigener Schritt.
  Kein Automatismus, kein Eingriff in Script-Logik.


--------------------------------------------------------------------------------
6. ERKENNTNISSE FÜR DEN BLUEPRINT
--------------------------------------------------------------------------------

  • CSM (Customer Service Management) ist die richtige Vorlage
    für externes Endkunden-Portal — nicht der klassische IT Service Desk

  • Contact/Standard Formular in CSM ist System-reserviert —
    eigene Formulare für Portal-sichtbare Request-Typen anlegen

  • Free Plan trägt R+MUNI Portal vollständig — kein Upgrade nötig

  • Offener Kundenzugriff ("Jeder") passt zur R+MUNI Philosophie
    und reduziert Onboarding-Aufwand auf null

  • Confluence bleibt bewusst getrennt vom Portal-Projekt —
    Verknüpfung ist ein eigener bewusster Schritt

  • Atlassian Free Plan Limits beachten:
    1 Space Confluence, 10 User, keine SLA, kein E-Mail-Kanal nötig


--------------------------------------------------------------------------------
7. OFFENE PUNKTE / NÄCHSTE SCHRITTE
--------------------------------------------------------------------------------

  [ ] Portal selbst testen (Inkognito-Fenster, alle 3 Formulare)
  [ ] Branding vervollständigen (Hauptfarbe, Symbol)
  [ ] Confluence FAQ-Seite und Verlinkung (eigener Sprint)
  [ ] Portal-URL in Confluence R+MUNI Hauptseite publizieren
  [ ] Erste Kunden-Kommunikation mit Portal-URL (Beta-Tester)
  [ ] Service User 1 Claude — Atlassian-Rolle klären (nicht dringend)
  [ ] Team User COLUMBO — Einladung und Onboarding (wenn bereit)


--------------------------------------------------------------------------------
8. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Feature-Zuwachs Stage-5-Ziel 4.1
GOV 10.5  Fachlicher Mehrwert        OK  Kundeninterface + Team-Plattform
GOV 10.5  Keine implizite Gov-Änd.   OK  Atlassian ist Arbeitsschicht, keine Logik
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 1
GOV 10.6  Ziel überprüfbar           OK  Portal-URL live, 3 Formulare verfügbar
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Atlassian ist Add-on-Schicht
Stage 5   Rückkopplungsschutz        OK  Kein Eingriff in Script-Logik


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-ATL-FrontendSetup | Stage 5 | 2026-03-13
R+MUNI Blueprint | Erstellt durch: Markus Resel + Claude (Pair-Session)
================================================================================
