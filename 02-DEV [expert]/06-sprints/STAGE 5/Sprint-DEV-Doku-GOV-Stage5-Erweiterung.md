================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-GOV-Stage5-Erweiterung — Kapitel 11 + 12
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
Auslöser-Typ : GOV-Erweiterung (Stage-5-Ziel 4.4)

Begründung   : Stage 5 ist die erste Außenwirkungsphase von R+MUNI.
               Mit dem ersten Beta-Kunden im Livebetrieb und dem Aufbau
               eines R+MUNI Teams werden Regeln gebraucht die es in
               Stage 3/4 noch nicht gab:
                 - Wie geht R+MUNI mit Endkunden um?
                 - Wie wächst das Team strukturiert?
                 - Wer entscheidet was — und wie wird das festgehalten?

               Diese Erweiterung ist additiv — Kapitel 1-10 bleiben
               unverändert. Die Stage-5-Erweiterung wird mit Datum
               und Begründung formal dokumentiert.

Fachlicher   : Klare Regeln für Kundenkontakt und Team-Aufbau.
Mehrwert       Reproduzierbares Onboarding ohne mündliche Übergabe.
               GOV bleibt das normative Fundament — auch im Wachstum.


--------------------------------------------------------------------------------
2. GOV KAPITEL 11 — UMGANG MIT ENDKUNDEN
--------------------------------------------------------------------------------

Erweiterung Stage 5 | 2026-03-09

2.1 Zweck
----------
Verbindliche Regeln für den Umgang mit Endkunden im R+MUNI Livebetrieb.

  - Fairer, ehrlicher, transparenter Kundenkontakt
  - Klare Erwartungen ohne Versprechen die nicht haltbar sind
  - Offenheit als Grundprinzip — auch im Umgang mit Kritik

2.2 Grundhaltung
-----------------
R+MUNI ist und bleibt kostenlos. Das ist keine Marketingaussage.

  - Offenheit und Ehrlichkeit sind nicht verhandelbar
  - Kritik ist Feedback — kein Angriff
  - Kein Kunde wird zu Upgrade, Zahlung oder Entscheidung gedrängt
  - Kapazität ist eine legitime Absage — kein Erklärungszwang

2.3 Kommunikationskanal
------------------------
Primärkanal: R+MUNI Portal (Atlassian JSM/CSM, Free Plan)
  https://ims-blueprint-ticketsystem.atlassian.net/helpcenter/RMNP/

  - Zugang offen für jeden ohne Registrierungszwang
  - 3 Request-Typen: Bug, Feature Request, DEV Anfrage
  - Vertriebsanfragen: bewusst ausgeschlossen
  - Antworten über das Portal — kein E-Mail-Zwang

2.4 Umgang mit Kundenanfragen
------------------------------

  Bug
    Wird ernst genommen und geprüft.
    Rückmeldung sobald möglich — keine SLA, kein Versprechen.
    Bugfix erfordert explizite Freigabe durch Entwickler (GOV 10.4).

  Feature Request
    Wird gesammelt und bewertet.
    Kein Automatismus zur Umsetzung.
    Kundenwunsch kann Sprint-Auslöser sein (GOV 10.5).

  DEV Anfrage
    Wird gelesen und situativ bewertet.
    Ob daraus eine Leistung wird: Entwickler entscheidet.
    Kapazität und Workload sind legitime Entscheidungskriterien.
    Keine implizite Zusage durch Annahme der Anfrage.

2.5 Kundenfeedback als Blueprint-Input
----------------------------------------
Feedback aus dem Livebetrieb darf:
  - in Stage-5-Entwicklung einfließen
  - als Grundlage für GOV-Erweiterungen dienen
  - BPMN Default Flow Prioritäten beeinflussen

Feedback darf nicht:
  - Stage-3/4-Kernlogik verändern
  - ohne expliziten Entwicklerentscheid umgesetzt werden

2.6 Wertschätzung gegenüber dem Archi-Entwickler
--------------------------------------------------
Archi ist Open Source — kein Kaufmodell, freiwillige Beiträge.
R+MUNI wäre ohne Archi nicht möglich.

Grundsatz:
  Für jeden Beta-Kunden der Archi produktiv nutzt vermittelt
  EUMAXL bewusst ein Geschenk-Abo an den Archi-Entwickler.
  Das ist keine Marketing-Maßnahme — es ist gelebte Haltung.
  Verankert in Blueprint und README.

2.7 Optionales Kunden-Atlassian
---------------------------------
Kunden können ein eigenes Atlassian Free Bundle aufbauen.

  - Option, kein Standard, kein Zwang
  - Entwickler kann begleitend unterstützen — als bewusste Leistung
  - Kein Kunde wird zu einem kostenpflichtigen Atlassian-Plan gedrängt
  - Spezialisierte Atlassian-Expertise wird bei Bedarf weitervermittelt


--------------------------------------------------------------------------------
3. GOV KAPITEL 12 — UMGANG MIT DEM R+MUNI TEAM
--------------------------------------------------------------------------------

Erweiterung Stage 5 | 2026-03-09

3.1 Zweck
----------
Verbindliche Regeln für Aufbau und Betrieb des R+MUNI Teams ab Stage 5.

R+MUNI wächst vom Ein-Mann-Projekt zur strukturierten Zusammenarbeit.
Diese Regeln sichern dieses Wachstum ohne die Kernprinzipien zu gefährden.

3.2 Team-Struktur (Stage 5)
-----------------------------

  Betreiber (EUMAXL / Markus Resel)
    Volle Rechte und Projektverantwortung.
    Einzige Instanz für Stage-Entscheide und GOV-Änderungen.
    Einzige Instanz für Bugfix-Freigaben in Stage 3/4.

  Team User (COLUMBO — Einladung offen)
    Volle Atlassian-Rechte im R+MUNI Bundle.
    Unterstützt im Atlassian-Umfeld.
    Kein eigenständiger Stage-Entscheid ohne Betreiber-Freigabe.

  Service User 1 (Claude)
    AI-Unterstützung im Entwicklungs- und Dokumentationsumfeld.
    Konkrete Atlassian-Rolle wird in Stage 5 geklärt
    (Rovo AI oder Prozessrolle).
    Kein eigenständiger Entscheid ohne Betreiber-Freigabe.

  Service User 2
    Reserve — noch nicht vergeben.

  Kunden und weitere Team-User
    Nach Bedarf, innerhalb Free-Plan-Limits.

3.3 Onboarding neuer Team-Mitglieder
--------------------------------------
  - Blueprint ist die Grundlage — kein Wissenstransfer ohne Blueprint-Basis
  - Neue Mitglieder erhalten Dokumentationszugang vor erstem operativem Einsatz
  - Rollen und Rechte werden explizit vergeben — kein impliziter Zuwachs
  - Atlassian-Zugang gemäß BETA ONBOARDING — MLAT Dokument

3.4 Kommunikation im Team
---------------------------
  - Atlassian (Jira + Confluence) ist die primäre Arbeitsplattform
  - Entscheidungen werden dokumentiert — kein stiller Konsens
  - Betreiber hat das letzte Wort bei Konflikten

3.5 Wissenstransfer und Reproduzierbarkeit
-------------------------------------------
  - Blueprint so pflegen dass ein neues Mitglied ohne mündliche
    Übergabe arbeitsfähig wird
  - Sprint Dev-Dokumentationen vollständig und nachvollziehbar
  - GOV-Entscheide immer schriftlich festhalten

3.6 GOV-Hoheit
---------------
  - GOV-Hoheit liegt ausschließlich beim Betreiber
  - GOV-Erweiterungen sind additiv — keine Revision bestehender Kapitel
  - Jede GOV-Änderung mit Datum und Begründung dokumentiert
  - Team-Mitglieder können GOV-Änderungen vorschlagen — entscheiden nicht


--------------------------------------------------------------------------------
4. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  GOV-Erweiterung Stage 5 (Ziel 4.4)
GOV 10.5  Fachlicher Mehrwert        OK  Klare Regeln Kunden + Team
GOV 10.5  Keine implizite Gov-Änd.   OK  Kapitel 1-10 vollständig unverändert
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 1
GOV 10.6  Ziel überprüfbar           OK  Kapitel 11+12 in Global_GOV.txt enthalten
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Additiv, keine Revision


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-GOV-Stage5-Erweiterung | Stage 5 | 2026-03-13
R+MUNI Blueprint | Erstellt durch: Markus Resel + Claude (Pair-Session)
================================================================================
[[SPRINT-5-5-FREEZE]]