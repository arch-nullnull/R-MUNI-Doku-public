================================================================================
R+MUNI GLOBAL GOVERNANCE
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Global_GOV_DEV_S105
Tag             : #gov #global #rmuni #dev #s105
Datum           : 2026-04-15
Stage           : S1.05 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN
Ablageort       : R+MUNI Doku-public\00-governance\Global_GOV_DEV_S105.md
================================================================================

---
title: "R+MUNI Global Governance"
stage: S1.05
status: "AKTIV"
typ: "GOV"
datum: "2026-04-15"
autor: EUMAXL
tags: [rmuni, blueprint, gov, global, dev, s105]
---

================================================================================
LESEANWEISUNG
================================================================================

Dieses Dokument ist die arbeitende Governance — ausschließlich Regeln.
Keine Erklärungen. Keine Hintergründe. Keine Beispiele.

Erklärungen und Kontext: [[Global_GOV_STORY_S105]]
KI-Verhalten und Methode: [[AI_DRIVEN_DEV_METHODE_DEV_S105]]
Naming und Ablage:        [[naming_and_structure_S104]]

Dieses Dokument ist vollständig zu laden — kein Snippet-Betrieb.
Jede Regel gilt für sich. Keine Regel setzt eine andere voraus.


================================================================================
1. GELTUNGSBEREICH UND GRUNDPRINZIPIEN
================================================================================

1.1 Geltungsbereich
--------------------
Diese Governance gilt verbindlich für:
- alle Architektur-, Integrations- und Automatisierungsartefakte
- alle Modellierungs-, Synchronisations- und Ableitungsprozesse
- alle manuellen und automatisierten Eingriffe in das Blueprint-System

Es existieren keine governance-freien Bereiche.


1.2 Explizitheit
-----------------
- Entscheidungen werden explizit getroffen.
- Regeln werden explizit formuliert.
- Abweichungen werden explizit dokumentiert.
- Ableitungen erfolgen explizit.

Implizite Logik ist unzulässig.


1.3 Prioritäten
----------------
- Stabilität vor Komfort.
- Nachvollziehbarkeit vor Geschwindigkeit.
- Disziplin vor kurzfristiger Optimierung.

Kurzfristige Vereinfachungen rechtfertigen keine Regelabweichung.


================================================================================
2. REGELCHARAKTER
================================================================================

2.1 Verbindlichkeit
--------------------
Alle Regeln dieser Governance sind normativ.
Sie gelten unabhängig von Kontext, Werkzeug oder Bequemlichkeit.
Sie sind nicht optional.


2.2 Abweichungen
-----------------
- Abweichungen sind grundsätzlich unerwünscht.
- Abweichungen müssen explizit benannt sein.
- Abweichungen müssen nachvollziehbar begründet sein.
- Abweichungen erzeugen keine Präzedenzwirkung.

Implizite oder stillschweigende Abweichungen sind unzulässig.


2.3 Keine implizite Weiterentwicklung
--------------------------------------
- Neue Regeln entstehen nicht durch Gewohnheit.
- Neue Standards entstehen nicht durch Wiederholung.
- Neue Bedeutungen entstehen nicht durch Interpretation.

Änderungen erfolgen ausschließlich durch explizite Betreiberentscheidung.


================================================================================
3. VERBINDLICHE REGELN
================================================================================

Diese Regeln sind nicht verhandelbar.
Sie gelten systemweit, unabhängig von Kontext, Werkzeug oder Zweck.
Bei Widerspruch zwischen diesem Kapitel und anderen Kapiteln gilt dieses Kapitel.


3.1 Identität
--------------
- Jedes Objekt besitzt genau eine Identität.
- Identität ist ausschließlich über die Objekt-ID definiert.
- Namen, Typen oder Darstellungen sind nicht identitätsstiftend.
- Objekt-IDs sind stabil und dürfen nicht geändert werden.
- Automatische Erzeugung neuer Objekt-IDs ist unzulässig.


3.2 ID-Reparatur und Blockade
------------------------------
- ID-Reparatur ist nur zulässig wenn die Identität eindeutig rekonstruierbar ist.
- ID-Reparatur darf keine semantische Annahme erfordern.
- Ist Identität nicht eindeutig bestimmbar, ist der Vorgang zu blockieren.
- Blockade ist einem falschen Import vorzuziehen.


3.3 Namen
----------
- Namen dienen ausschließlich der Lesbarkeit.
- Namen enthalten keine implizite Semantik.
- Namensänderungen verändern keine Identität.
- Namen dürfen nicht zur Steuerung von Integration oder Ableitung verwendet werden.


3.4 Führung und Integrationswahrheit
--------------------------------------
- Für jede Information existiert genau eine führende Quelle.
- Führung ist explizit festzulegen.
- Führung kann feldgenau definiert werden.
- Ohne definierte Führung ist keine Integration zulässig.
- Nicht-führende Informationen dürfen führende nicht überschreiben.


3.5 Integration
----------------
- Integration erfolgt ausschließlich regelbasiert.
- Integration erzeugt keine neue Identität.
- Integration erzeugt keine neue Semantik.
- Integration respektiert die definierte Führungslogik.
- Implizite Integration ist unzulässig.


3.6 CSV und Transportformate
-----------------------------
- CSV-Dateien sind reine Transportformate.
- CSV-Dateien enthalten keine implizite Semantik.
- CSV-Dateien erzeugen keine Identität.
- CSV-Dateien überschreiben keine führenden Informationen.


3.7 Ableitung
--------------
- Ableitung erzeugt keine neue Identität.
- Ableitung verändert keine führenden Informationen.
- Ableitung wirkt nicht rück auf die Quelle.
- Ableitung ist eine Einbahnstraße.


3.8 Artefaktrollen
-------------------
- Architekturartefakte sind führend für Struktur.
- Integrationsartefakte sind nicht führend.
- Abgeleitete Artefakte besitzen keine Führungswirkung.
- Ausführungsartefakte definieren keine Architektur.


3.9 Ebenentrennung
--------------------
- Architektur, Integration und Ableitung sind strikt getrennt.
- Eine Ebene definiert keine Regeln für eine andere Ebene.
- Rückwirkungen zwischen Ebenen sind unzulässig.


3.10 Automatisierung und Scripts
---------------------------------
- Scripts erfüllen genau eine fachliche Wirkung.
- Scripts sind deterministisch und reproduzierbar.
- Scripts interpretieren keine Modellinhalte.
- Scripts erzeugen keine neue Semantik.
- Scripts verändern keine Governance-Regeln.


3.11 Tool-Unabhängigkeit
-------------------------
- Architekturmodelle enthalten keine Tool-Semantik.
- Tool-spezifische Einschränkungen rechtfertigen keine Architekturänderungen.
- Werkzeuge besitzen keine Governance-Wirkung.
- Objekttypen sind stabil und werden nicht zur Ermöglichung von Beziehungen geändert.
- Ist keine normkonforme Beziehung möglich, ist Association als zulässiger Fallback zu verwenden.
- Beziehungstypen werden nicht semantisch überladen.


3.12 Qualität und Validierung
------------------------------
- Modellzustände müssen validierbar sein.
- Validierung ist deterministisch und reproduzierbar.
- Nicht validierbare Zustände sind unzulässig.
- Fehler dürfen nicht stillschweigend korrigiert werden.


3.13 Audit
-----------
- Alle relevanten Entscheidungen sind nachvollziehbar.
- Alle automatisierten Schritte sind reproduzierbar.
- Alle Abweichungen sind dokumentiert.
- Nicht auditierbare Zustände sind unzulässig.


================================================================================
4. SPRINTS
================================================================================

4.1 Definition
---------------
Ein Sprint ist eine zeitlich begrenzte Umsetzungsphase mit explizit
definiertem Ziel. Ein Sprint ist kein governance-freier Raum.


4.2 Zulässige Auslöser
-----------------------
Ein Sprint ist ausschließlich zulässig bei:
- Fehlerbehebung
- Feature-Zuwachs
- Strukturbereinigung
- Kundenbedarf
- Entwicklerwunsch

Andere Auslöser sind unzulässig.


4.3 Zieldefinition
-------------------
- Das Ziel ist explizit definiert.
- Das Ziel ist eindeutig einem zulässigen Auslöser zugeordnet.
- Das Ziel ist überprüfbar und abgegrenzt.

Ohne explizite Zieldefinition existiert kein Sprint.


4.4 Zwischenschritte
---------------------
Während eines Sprints:
- müssen Zwischenschritte nicht vollständig dokumentiert werden
- darf der Ablauf Lücken enthalten
- dürfen Entscheidungen situativ getroffen werden

Keine Abweichung von Governance-Regeln — ausschließlich eingeschränkte
Dokumentationspflicht während des Sprints.


4.5 Dokumentation während Sprint
----------------------------------
Während eines Sprints werden ausschließlich Dev-Dokumentationen erstellt.
Sie müssen eine vollständige Rekonstruktion ermöglichen.
Sie ersetzen keine finale Dokumentation.


4.6 Dokumentation zum Stage-Ende
----------------------------------
Spätestens zum Stage-Ende gilt:
- vollständige Dokumentation ist verpflichtend
- alle relevanten Entscheidungen sind explizit nachzudokumentieren
- Governance-Konformität ist herzustellen und prüfbar

Ein Sprint gilt erst mit abgeschlossener Dokumentation als beendet.


4.7 Verhältnis zur Governance
-------------------------------
Während eines Sprints gilt:
- keine Governance-Regel wird aufgehoben
- ausschließlich der Zeitpunkt der Dokumentation wird verschoben
- es entsteht keine neue Ausnahme- oder Präzedenzwirkung

Alle Ergebnisse eines Sprints unterliegen vollständig der bestehenden Governance.


4.8 Session-Regel
------------------
In stabilen, klar abgegrenzten Kontexten kann eine Session-Regel eine
formal dokumentierte Regel ersetzen.

Voraussetzungen:
- der Auslöser ist klar und explizit benannt
- der Kontext ist stabil und eindeutig
- die Wirkung ist auf die laufende Session begrenzt

Eine Session-Regel erzeugt keine Governance-Wirkung über die Session hinaus.
Sie verändert keine bestehenden Regeln und schafft keine Präzedenz.


4.9 Stage-Bezeichnungskonvention
----------------------------------
Alle Blueprint-Dokumente im Beta-Zustand erhalten das Suffix _S<N>.
<N> bezeichnet die Beta-Stage zum Zeitpunkt der Erstellung.

- gilt für alle neuen Dokumente ab Beta 1.x
- einheitlich über alle Dokumentreihen
- dient der Nachvollziehbarkeit des Entstehungszeitpunkts
- ersetzt keine inhaltliche Versionierung
- gilt nicht rückwirkend für Dokumente vor Beta 1.x


================================================================================
5. REPO- UND DOKUMENTATIONSSTRUKTUR
================================================================================

5.1 Trennung internal / public
--------------------------------
- 00-internal und 01-public sind strikt getrennt — keine Vermischung.
- Inhalte aus 00-internal fließen nicht automatisch in 01-public.
- Jede Übernahme von 00-internal nach 01-public erfordert explizite Betreiberfreigabe.
- Public-Inhalte besitzen keine Governance-Wirkung auf 00-internal.


5.2 Varianten
--------------
Geführte Varianten:
  CARD     eigenständig geführt
  R+MUNI   eigenständig geführt
  DEV      eigenständig geführt — Basis für alle Ableitungen

EXPERT wird nicht eigenständig geführt.
EXPERT entsteht bei Bedarf als Extraktion aus DEV — on-demand.


5.3 Externe Erkenntnisquellen
-------------------------------
- Externe Erkenntnisse sind beim Einbringen explizit zu kennzeichnen.
- Tag [CUSTO] für Erfahrungsberichte aus Kundenumgebungen.
- Tag [CUSTO→RMUNI] für explizit gewünschten Transfer.
- Ohne Kennzeichnung gilt jede Information als R+MUNI-intern.
- Unkennzeichnete externe Inhalte dürfen nicht in R+MUNI-Artefakte einfließen.
- Kein Transfer ohne expliziten Auslöser durch den Betreiber.


5.4 Rollentrennung
-------------------
- DEV, Kundensupport und PreSales sind strikt getrennte Rollen.
- Erkenntnisse aus einer Rolle fließen nicht automatisch in eine andere.
- Bei Unklarheit über die aktive Rolle gilt Default: DEV.
- Rollenvermischung ohne explizite Kennzeichnung ist unzulässig.


================================================================================
BEZÜGE
================================================================================

[[Global_GOV_STORY_S105]]          Erklärungen, Kontext, Hintergründe
[[AI_DRIVEN_DEV_METHODE_DEV_S105]] KI-Verhalten, operative Arbeitsmethode
[[naming_and_structure_S104]]      Naming, Ablage, Struktur

================================================================================
R+MUNI GLOBAL GOVERNANCE | S1.05 | 2026-04-15 | R+MUNI Blueprint
================================================================================
