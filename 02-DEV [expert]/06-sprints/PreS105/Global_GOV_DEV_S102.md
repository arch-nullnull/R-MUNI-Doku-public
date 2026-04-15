================================================================================
R+MUNI GLOBAL GOVERNANCE
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Global_GOV_DEV_S102
Tag             : #gov #global #rmuni #dev #s102
Datum           : 2026-04-05
Stage           : S1.02 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN
================================================================================

---
title: "R+MUNI Global Governance"
stage: S1.02
status: "AKTIV"
typ: "GOV"
datum: "2026-04-05"
autor: EUMAXL
tags: [rmuni, blueprint, gov, global, dev, s102]
---

================================================================================
R+MUNI GLOBAL GOVERNANCE
Stage S1.02 | AKTIV | R+MUNI Blueprint
================================================================================

---

## Kontext

Verbindliche Governance für das R+MUNI Blueprint-Projekt. Definiert Regeln
für Architektur, Integration, Automatisierung und Ablage. Gilt für alle
Artefakte und Prozesse im System. KI-Verhalten und Naming sind in separaten
Dokumenten geregelt (AI_DRIVEN_DEV_METHODE, naming.md).

---

## Verwandte Dokumente

- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]        operative Arbeitsmethode, KI-Verhalten

---

## Inhalt

--------------------------------------------------------------------------------
1. ZWECK, INTENTION UND CHARAKTER DER GOVERNANCE
--------------------------------------------------------------------------------

1.1 Zweck dieser Governance
-----------------------------
Diese Governance definiert die verbindlichen Regeln, Prinzipien und Leitplanken
für das Blueprint-Projekt.

Ziel dieser Governance ist es:
- ein konsistentes, langfristig stabiles Architektur- und Integrationsmodell
  zu ermöglichen
- explizite, nachvollziehbare und auditfähige Entscheidungen sicherzustellen
- implizite Annahmen, verdeckte Logik und stillschweigende Abweichungen
  systematisch auszuschließen

Diese Governance ist kein Begleitdokument, sondern integraler Bestandteil
des Blueprint-Systems.


1.2 Abgrenzung zu Prozess- und Projektgovernance
--------------------------------------------------
Diese Governance ist:
- keine Projektmanagement-Governance
- keine Prozessbeschreibung
- keine Rollen- oder Verantwortlichkeitsdefinition
- keine Verhaltensregeldefinition für KI (→ AI_DRIVEN_DEV_METHODE)

Sie definiert ausschließlich:
- was modelliert, integriert und automatisiert werden darf
- wie Identität, Führung und Ableitung zu erfolgen haben
- welche Regeln unveränderlich gelten


1.3 Verbindlichkeit und Geltungsbereich
-----------------------------------------
Diese Governance gilt verbindlich für:
- alle Architektur-, Integrations- und Automatisierungsartefakte
- alle Modellierungs-, Synchronisations- und Re-Materialisierungsprozesse
- alle manuellen und automatisierten Eingriffe in das Blueprint-System

Es existieren keine governance-freien Bereiche.


1.4 Explizitheit als Grundprinzip
-----------------------------------
Für das gesamte Blueprint-System gilt:
- Entscheidungen werden explizit getroffen
- Regeln werden explizit formuliert
- Abweichungen werden explizit dokumentiert
- Ableitungen erfolgen explizit

Implizite Logik ist unzulässig.


1.5 Langfristige Perspektive
------------------------------
Diese Governance priorisiert:
- Stabilität über Komfort
- Nachvollziehbarkeit über Geschwindigkeit
- Disziplin über kurzfristige Optimierung

Kurzfristige Vereinfachungen rechtfertigen keine Abweichungen von den
definierten Regeln.


--------------------------------------------------------------------------------
2. GRUNDBEGRIFFE UND ABGRENZUNGEN
--------------------------------------------------------------------------------

2.1 Zweck dieses Kapitels
---------------------------
Dieses Kapitel definiert die grundlegenden Begriffe für das Verständnis
und die korrekte Anwendung dieser Governance.

Alle Begriffe werden normativ verwendet.


2.2 Objekt
-----------
Ein Objekt ist eine eindeutig identifizierbare Einheit innerhalb des
Blueprint-Systems.

Ein Objekt besitzt eine stabile Identität und existiert unabhängig von
Darstellung, Tool oder Format.

Ein Objekt ist nicht gleichzusetzen mit seiner visuellen Darstellung.


2.3 Identität
--------------
Die Identität eines Objekts ist unabhängig von Name, Typ oder Darstellung.
Sie bleibt über alle Iterationen hinweg stabil und ist die Grundlage aller
Integrations- und Ableitungsprozesse.

Identität ist nicht interpretierbar.


2.4 Objekt-ID
--------------
Die Objekt-ID ist eindeutig, stabil und repository-weit gültig.
Sie ist der alleinige Referenzanker für Integration und Automatisierung.

Objektnamen oder Tool-IDs ersetzen keine Objekt-ID.



2.5 Führung
------------
Führung beschreibt, welche Quelle für eine Information verbindlich ist.
Sie wird explizit festgelegt und kann feldgenau variieren.

Ohne explizite Führungsdefinition existiert keine Führung.
Vollständige Regelung: Kap. 6.5.


2.6 Integration
----------------
Integration bezeichnet die kontrollierte Zusammenführung von Informationen
aus unterschiedlichen Quellen gemäß der definierten Führungslogik.

Integration ist regelbasiert, deterministisch und reproduzierbar.
Vollständige Regelung: Kap. 6.5.


2.7 Ableitung
--------------
Ableitung beschreibt die Überführung von Architektur- oder
Integrationsinformationen in andere Artefakte oder Formate.

Ableitung ist explizit definiert, nachvollziehbar und erzeugt keine
neue Identität. Sie wirkt nicht rück auf die Quelle.
Vollständige Regelung: Kap. 6.7.


2.8 Rückwirkung
-----------------
Rückwirkung bezeichnet jede Veränderung eines führenden Artefakts durch
ein abgeleitetes Artefakt.

Rückwirkungen sind grundsätzlich unzulässig, sofern nicht explizit geregelt.


2.9 Implizit vs. Explizit
---------------------------
Implizit bedeutet: nicht dokumentiert, nicht nachvollziehbar,
interpretationsabhängig.

Explizit bedeutet: klar formuliert, dokumentiert, reproduzierbar.

Diese Governance bevorzugt explizite Lösungen in allen Fällen.


--------------------------------------------------------------------------------
3. GOVERNANCE-VERSTÄNDNIS UND REGELCHARAKTER
--------------------------------------------------------------------------------

3.1 Governance als Regelwerk
------------------------------
Governance wird in diesem Projekt als verbindliches Regelwerk verstanden.

Governance definiert zulässige und unzulässige Zustände, legt unveränderliche
Prinzipien fest und begrenzt den Lösungsraum bewusst.

Governance ist kein Prozess, keine Empfehlung und keine Sammlung von
Best Practices.


3.2 Normativer Charakter
-------------------------
Alle in dieser Governance definierten Regeln sind normativ.

Sie sind verbindlich, gelten unabhängig von Kontext oder Bequemlichkeit
und sind nicht optional.

Abweichungen sind nur zulässig, wenn sie explizit geregelt sind.


3.3 Umgang mit Abweichungen
-----------------------------
Abweichungen von Governance-Regeln sind grundsätzlich unerwünscht.

Sofern Abweichungen zugelassen sind:
- Abweichungen müssen explizit benannt werden
- Abweichungen müssen nachvollziehbar begründet sein
- Abweichungen erzeugen keine Präzedenzwirkung

Implizite oder stillschweigende Abweichungen sind unzulässig.


3.4 Keine implizite Weiterentwicklung
--------------------------------------
Neue Regeln entstehen nicht durch Gewohnheit.
Neue Standards entstehen nicht durch Wiederholung.
Neue Bedeutungen entstehen nicht durch Interpretation.

Änderungen erfolgen ausschließlich durch bewusste, explizite Entscheidungen.


--------------------------------------------------------------------------------
4. ARCHITEKTUR- UND MODELLPRINZIPIEN
--------------------------------------------------------------------------------

4.1 Identitätsprimat
---------------------
Die Identität eines Objekts ist das zentrale Ordnungsprinzip des
Blueprint-Systems.

Alle Architektur- und Modellentscheidungen haben die Identität zu
respektieren.


4.2 Trennung von Struktur, Semantik und Darstellung
-----------------------------------------------------
Das Blueprint-System trennt strikt zwischen:
- Struktur (Objekte, Beziehungen, Rollen)
- Semantik (fachliche Bedeutung, Beschreibung)
- Darstellung (Visualisierung, Tool-spezifische Repräsentation)

Diese Trennung ist verbindlich und darf nicht aufgehoben werden.

Semantik darf nicht aus Struktur oder Darstellung implizit abgeleitet werden.


4.3 Explizitheit als Modellierungsprinzip
------------------------------------------
Alle relevanten Modellierungsentscheidungen sind explizit zu treffen.

Keine impliziten Annahmen. Keine verdeckte Logik. Keine stillschweigende
Interpretation.


4.4 Determinismus
------------------
Das Blueprint-System ist deterministisch aufgebaut.

Gleiche Eingaben führen zu gleichen Ergebnissen.
Integrations- und Ableitungsprozesse sind reproduzierbar.
Modellzustände sind eindeutig bestimmbar.

Nicht-deterministisches Verhalten ist unzulässig.


4.5 Tool-Unabhängigkeit
------------------------
Das Blueprint-Modell ist unabhängig von konkreten Werkzeugen oder Plattformen.

Keine Tool-Semantik im Architekturmodell.
Keine impliziten Tool-Abhängigkeiten.
Keine Vermischung von Architektur und Ausführung.

Werkzeuge dienen der Umsetzung, nicht der Definition der Architektur.


4.6 Architektur als Referenz, nicht als Ausführung
----------------------------------------------------
Architekturmodelle beschreiben Struktur, Rollen und Beziehungen.

Sie beschreiben nicht Ausführungslogik, technische Steuerung oder
Laufzeitverhalten.

Die Architektur ist Referenz, nicht Implementierung.


4.7 Beziehungsprimat der Objektstabilität
------------------------------------------
Die Stabilität von Objekten hat Vorrang vor der Präzision von Beziehungen.

Objekttypen werden nicht geändert um Beziehungen zu ermöglichen.
Ist keine normkonforme Beziehung zwischen zwei Objekten möglich, ist
Association als normkonformer Fallback zulässig.
Beziehungstypen werden nicht semantisch überladen.
Import-Regelwerk definiert Objekttypen fix — kontextabhängige
Uminterpretation eines Objekttyps ist unzulässig.



--------------------------------------------------------------------------------
5. ARTEFAKTROLLEN UND EBENENTRENNUNG
--------------------------------------------------------------------------------

5.1 Artefakt
-------------
Ein Artefakt ist eine konkrete Repräsentation von Informationen in einem
bestimmten Kontext, Format oder Werkzeug.

Ein Artefakt repräsentiert Objekte, besitzt aber keine eigene Identität.
Es ist kontext- und zweckgebunden und unterliegt einer klar definierten Rolle.


5.2 Führendes Artefakt
-----------------------
Ein führendes Artefakt definiert die verbindliche Wahrheit für bestimmte
Informationen.

Es ist explizit als führend definiert und besitzt keine implizite Führung.

Ohne explizite Definition existiert kein führendes Artefakt.


5.3 Architekturartefakte
-------------------------
Architekturartefakte beschreiben die strukturelle Referenz des
Blueprint-Systems.

Sie enthalten Objekte und deren Beziehungen, Rollen und Struktur.
Sie enthalten keine Ausführungslogik und keine Tool- oder Plattformsemantik.

Architekturartefakte sind führend für Struktur, nicht für Ausführung.


5.4 Integrationsartefakte
--------------------------
Integrationsartefakte dienen der Zusammenführung von Informationen.

Sie folgen der definierten Integrations- und Führungslogik.
Sie erzeugen keine neue Identität und verändern keine Architekturprinzipien.

Integrationsartefakte sind abgeleitet, nicht führend.


5.5 Abgeleitete Artefakte
--------------------------
Abgeleitete Artefakte materialisieren Informationen für spezifische Zwecke.

Sie besitzen keine Führungswirkung, erzeugen keine neue Wahrheit und wirken
nicht rück auf Architektur oder Integration.


5.6 Ebenentrennung
-------------------
Das Blueprint-System trennt strikt zwischen:
- Architektur
- Integration
- Ableitung / Ausführung

Diese Ebenen sind logisch getrennt und dürfen nicht vermischt werden.
Eine Ebene darf keine Regeln für eine andere Ebene definieren.
Rückwirkungen zwischen Ebenen sind normativ ausgeschlossen.




--------------------------------------------------------------------------------
6. VERBINDLICHE REGELN
--------------------------------------------------------------------------------

Die folgenden Regeln sind nicht verhandelbar.
Sie gelten systemweit, unabhängig von Kontext, Werkzeug oder Zweck.
Bei Widerspruch zwischen diesem Kapitel und Kap. 2–4 gilt dieses Kapitel.


6.1 Identität
--------------
- Jedes Objekt besitzt genau eine Identität.
- Identität ist ausschließlich über die Objekt-ID definiert.
- Namen, Typen oder Darstellungen sind nicht identitätsstiftend.
- Objekt-IDs sind stabil und dürfen nicht geändert werden.
- Automatische Erzeugung neuer Objekt-IDs ist unzulässig.


6.2 ID-Reparatur und Blockade
------------------------------
- ID-Reparatur ist nur zulässig, wenn die Identität eindeutig
  rekonstruierbar ist.
- ID-Reparatur darf keine semantische Annahme erfordern.
- Ist Identität nicht eindeutig bestimmbar, ist der Vorgang zu blockieren.
- Blockade ist einem falschen Import vorzuziehen.


6.3 Namen
----------
- Namen dienen ausschließlich der Lesbarkeit.
- Namen enthalten keine implizite Semantik.
- Namensänderungen verändern keine Identität.
- Namen dürfen nicht zur Steuerung von Integration oder Ableitung
  verwendet werden.



6.4 Führung und Integrationswahrheit
--------------------------------------
- Für jede Information existiert genau eine führende Quelle.
- Führung ist explizit festzulegen.
- Führung kann feldgenau definiert werden.
- Ohne definierte Führung ist keine Integration zulässig.
- Nicht-führende Informationen dürfen führende nicht überschreiben.


6.5 Integration
----------------
- Integration erfolgt ausschließlich regelbasiert.
- Integration erzeugt keine neue Identität.
- Integration erzeugt keine neue Semantik.
- Integration respektiert die definierte Führungslogik.
- Implizite Integration ist unzulässig.


6.6 CSV und Transportformate
-----------------------------
- CSV-Dateien sind reine Transportformate.
- CSV-Dateien enthalten keine implizite Semantik.
- CSV-Dateien erzeugen keine Identität.
- CSV-Dateien überschreiben keine führenden Informationen.


6.7 Ableitung
--------------
- Ableitung erzeugt keine neue Identität.
- Ableitung verändert keine führenden Informationen.
- Ableitung wirkt nicht rück auf die Quelle.
- Ableitung ist eine Einbahnstraße.


6.8 Artefaktrollen
-------------------
- Architekturartefakte sind führend für Struktur.
- Integrationsartefakte sind nicht führend.
- Abgeleitete Artefakte besitzen keine Führungswirkung.
- Ausführungsartefakte definieren keine Architektur.


6.9 Ebenentrennung
--------------------
- Architektur, Integration und Ableitung sind strikt getrennt.
- Eine Ebene definiert keine Regeln für eine andere Ebene.
- Rückwirkungen zwischen Ebenen sind unzulässig.


6.10 Automatisierung und Scripts
---------------------------------
- Scripts erfüllen genau eine fachliche Wirkung.
- Scripts sind deterministisch und reproduzierbar.
- Scripts interpretieren keine Modellinhalte.
- Scripts erzeugen keine neue Semantik.
- Scripts verändern keine Governance-Regeln.


6.11 Tool-Unabhängigkeit
-------------------------
- Architekturmodelle enthalten keine Tool-Semantik.
- Tool-spezifische Einschränkungen rechtfertigen keine Architekturänderungen.
- Werkzeuge besitzen keine Governance-Wirkung.
- Objekttypen sind stabil und werden nicht zur Ermöglichung von Beziehungen
  geändert.
- Ist keine normkonforme Beziehung möglich, ist Association als zulässiger
  Fallback zu verwenden.
- Beziehungstypen werden nicht semantisch überladen.


6.12 Qualität und Validierung
------------------------------
- Modellzustände müssen validierbar sein.
- Validierung ist deterministisch und reproduzierbar.
- Nicht validierbare Zustände sind unzulässig.
- Fehler dürfen nicht stillschweigend korrigiert werden.


6.13 Audit
-----------
- Alle relevanten Entscheidungen sind nachvollziehbar.
- Alle automatisierten Schritte sind reproduzierbar.
- Alle Abweichungen sind dokumentiert.
- Nicht auditierbare Zustände sind unzulässig.


--------------------------------------------------------------------------------
7. SPRINTS
--------------------------------------------------------------------------------

7.1 Zweck dieses Kapitels
----------------------------
Dieses Kapitel definiert die verbindlichen Regeln für den Einsatz von Sprints
innerhalb der MUNI-Governance.

Sprints sind kein Ersatz für die bestehende Governance, sondern eine explizit
geregelte Sonderform ihrer Anwendung.


7.2 Definition Sprint
-----------------------
Ein Sprint ist eine zeitlich begrenzte Umsetzungsphase, die auf ein vorab
explizit definiertes Ziel ausgerichtet ist.

Das Ziel ist verbindlich. Der Weg zum Ziel ist nicht vollständig vorgegeben.
Die vollständige Abbildung aller Zwischenschritte ist nicht erforderlich.

Ein Sprint ist kein governance-freier Raum.


7.3 Zulässige Auslöser für Sprints
-------------------------------------
Ein Sprint ist ausschließlich zulässig, wenn er durch einen der folgenden
Auslöser begründet ist:
- Fehlerbehebung
- Feature-Zuwachs
- Strukturbereinigung
- Kundenbedarf
- Entwicklerwunsch

Andere Auslöser sind unzulässig.


7.4 Fehler als Sprint-Auslöser
---------------------------------
Ein Sprint darf ausgelöst werden, wenn:
- ein fachlicher, struktureller oder technischer Fehler vorliegt
- der Fehler explizit benannt und abgegrenzt ist
- eine reguläre Umsetzung den Fehler nicht angemessen adressieren würde

Fehler im Sinne dieses Kapitels sind Abweichungen vom intendierten
Systemzustand, nicht Abweichungen von Governance-Regeln.


7.5 Feature-Zuwachs als Sprint-Auslöser
-----------------------------------------
Ein Sprint darf ausgelöst werden, wenn ein Feature-Zuwachs umgesetzt werden
soll.

Feature-Zuwachs kann ausgelöst sein durch:
- einen Entwicklerwunsch
- einen User-Wunsch
- einen Kundenbedarf

Für Feature-Zuwachs gilt:
- der Wunsch ist explizit zu benennen
- der fachliche Mehrwert ist zu beschreiben
- der Zuwachs erzeugt keine implizite Governance-Änderung

Feature-Zuwachs rechtfertigt keine Abweichung von Architektur-, Integrations-
oder Identitätsprinzipien.


7.6 Zieldefinition als zwingende Voraussetzung
-------------------------------------------------
Für jeden Sprint gilt verbindlich:
- das Ziel ist explizit definiert
- das Ziel ist eindeutig einem zulässigen Auslöser zugeordnet
- das Ziel ist überprüfbar und abgegrenzt

Ohne explizite Zieldefinition existiert kein Sprint.


7.7 Umgang mit Zwischenschritten
----------------------------------
Während eines Sprints gilt:
- Zwischenschritte müssen nicht vollständig dokumentiert werden
- der Ablauf darf Lücken enthalten
- Entscheidungen dürfen situativ getroffen werden

Diese Regelung stellt keine Abweichung von der Governance dar, sondern eine
normativ zugelassene Einschränkung der Dokumentationspflicht.


7.8 Dokumentation während des Sprints
----------------------------------------
Während eines Sprints werden ausschließlich Dev-Dokumentationen erstellt.

Sie dienen der späteren Nachvollziehbarkeit und müssen eine vollständige
Rekonstruktion ermöglichen.

Dev-Dokumentationen ersetzen keine finale Dokumentation.


7.9 Dokumentation zum Stage-Ende
-----------------------------------
Spätestens zum Stage-Ende eines Sprints gilt:
- vollständige Dokumentation ist verpflichtend
- alle relevanten Entscheidungen sind explizit nachzudokumentieren
- Governance-Konformität ist herzustellen und prüfbar

Ein Sprint gilt erst mit abgeschlossener Dokumentation als beendet.


7.10 Verhältnis zur bestehenden Governance
--------------------------------------------
Für Sprints gilt:
- keine Governance-Regel wird aufgehoben
- ausschließlich der Zeitpunkt der Dokumentation wird verschoben
- es entsteht keine neue Ausnahme- oder Präzedenzwirkung

Alle Ergebnisse eines Sprints unterliegen vollständig der bestehenden
Governance.


7.11 Session-Regel
--------------------
In stabilen, klar abgegrenzten Kontexten kann eine Session-Regel eine
formal dokumentierte Regel ersetzen.

Für die Session-Regel gilt:
- der Auslöser ist klar und explizit benannt
- der Kontext ist stabil und eindeutig
- die Wirkung ist auf die laufende Session begrenzt
- kein Backlog-Eintrag ist erforderlich

Eine Session-Regel erzeugt keine Governance-Wirkung über die Session hinaus.
Sie verändert keine bestehenden Regeln und schafft keine Präzedenz.


7.12 Stage-Bezeichnungskonvention für Dokumente
-------------------------------------------------
Alle Blueprint-Dokumente im Beta-Zustand erhalten das Suffix _S<N>,
wobei <N> die Beta-Stage-Bezeichnung zum Zeitpunkt der Erstellung bezeichnet.

Für die Konvention gilt:
- sie gilt für alle neuen Dokumente ab Beta 1.x
- sie ist einheitlich über alle Dokumentreihen anzuwenden
- sie dient der Nachvollziehbarkeit des Entstehungszeitpunkts
- sie ersetzt keine inhaltliche Versionierung

Die Konvention gilt nicht rückwirkend für Dokumente vor Beta 1.x.


--------------------------------------------------------------------------------
8. UMGANG MIT USERN
--------------------------------------------------------------------------------

8.1 Zweck dieses Kapitels
---------------------------
Dieses Kapitel definiert die verbindlichen Regeln für den Umgang mit
Usern im R+MUNI Livebetrieb.

Begriffsdefinition:
  User    = jeder der R+MUNI nutzt — gratis, ohne Bedingung,
            unabhängig vom Nutzungsumfang
  Kunde   = wer explizit einen bezahlten Service in Anspruch nimmt


8.2 Grundhaltung gegenüber Usern
-----------------------------------
R+MUNI ist und bleibt kostenlos.

Für den User-Kontakt gilt:
- Offenheit und Ehrlichkeit sind nicht verhandelbar
- Kritik von Usern ist Feedback — kein Angriff
- Kein User wird zu einem Upgrade, einer Zahlung oder einer Entscheidung
  gedrängt
- Der Entwickler behält das Recht situativ zu entscheiden was er annimmt
  und was nicht — Kapazität ist eine legitime Absage



8.3 Umgang mit User-Anfragen
-------------------------------
Bug:
- wird ernst genommen und geprüft
- Rückmeldung erfolgt sobald möglich — keine SLA, kein Versprechen
- Bugfix erfordert explizite Freigabe durch den Entwickler (GOV 7.4)

Feature Request:
- wird gesammelt und bewertet
- kein Automatismus zur Umsetzung
- User-Wunsch kann Sprint-Auslöser sein (GOV 7.5)

DEV Anfrage:
- wird gelesen und situativ bewertet
- ob daraus eine Leistung wird entscheidet der Entwickler
- Kapazität und Workload sind legitime Entscheidungskriterien
- keine implizite Zusage durch Annahme der Anfrage


8.4 User-Feedback als Blueprint-Input
----------------------------------------
Feedback aus dem Livebetrieb darf:
- in die laufende Entwicklung einfließen
- als Grundlage für GOV-Erweiterungen dienen

Feedback darf nicht:
- Kernlogik verändern ohne expliziten Entwicklerentscheid
- ohne expliziten Entwicklerentscheid umgesetzt werden



--------------------------------------------------------------------------------
9. EXTERNE ERKENNTNISQUELLEN UND ROLLENTRENNUNG
--------------------------------------------------------------------------------

9.1 Zweck dieses Kapitels
---------------------------
Dieses Kapitel definiert die verbindlichen Regeln für den Umgang mit
Erkenntnissen aus externen Quellen und die Rollentrennung des Betreibers.


9.2 Definition: Externe Erkenntnisquelle
------------------------------------------
Eine externe Erkenntnisquelle ist jede Informationsquelle die außerhalb der
R+MUNI Entwicklerrolle entsteht — insbesondere Erfahrungen aus
Kundensupport, Begleitprojekten oder regulierten Umgebungen.

Externe Erkenntnisquellen sind wertvoller Rohstoff — aber kein direkter
Blueprint-Input.


9.3 Kennzeichnungspflicht
---------------------------
Externe Erkenntnisquellen sind beim Einbringen in den R+MUNI Kontext
explizit zu kennzeichnen.

Kennzeichnung für Chat-Eingaben:
- Tag [CUSTO] für reine Erfahrungsberichte aus Kundenumgebungen
- Tag [CUSTO→RMUNI] für explizit gewünschten Transfer

Kennzeichnung für Dokumente:
- Identifikation über den Dokument-Header
- Projekt ≠ R+MUNI → Anonymisierungspflicht gilt automatisch

Ohne Kennzeichnung gilt jede Information als R+MUNI-intern.
Unkennzeichnete externe Inhalte dürfen nicht in R+MUNI-Artefakte einfließen.


9.4 Transfer-Logik
---------------------
Der Transfer von externen Erkenntnissen in R+MUNI-Artefakte folgt einer
expliziten Dreistufenlogik:

  Stufe 1 — Erfahrungsbericht [CUSTO]:
  - Erkenntnis wird aufgenommen
  - kein automatischer Transfer in R+MUNI-Strukturen

  Stufe 2 — Transfer-Anfrage [CUSTO→RMUNI]:
  - Betreiber löst explizit einen Transfer aus
  - nur die transferierbare Prozess- oder Architektur-Erkenntnis fließt ein

  Stufe 3 — Freigabe durch Betreiber:
  - transferiertes Ergebnis wird vom Betreiber geprüft und freigegeben
  - erst nach Freigabe wird es in R+MUNI-Dokumentation übernommen

Kein Transfer ohne expliziten Auslöser durch den Betreiber.


9.5 Rollentrennung als Governance-Prinzip
-------------------------------------------
Der Betreiber agiert in mehreren Rollen:
- R+MUNI Entwickler / DEV
- Kundensupport / Begleitung
- PreSales / Berater

Diese Rollen sind strikt getrennt zu halten.

Erkenntnisse aus einer Rolle fließen nicht automatisch in eine andere.
Der Betreiber ist Kontrollorgan für die Einhaltung der Trennung.
Bei Unklarheit über die aktive Rolle gilt Default: DEV.

Rollenvermischung ohne explizite Kennzeichnung ist unzulässig.


9.6 Kontext-Hygiene bei eingeschränktem AI-Einsatz
-----------------------------------------------------
In Umgebungen in denen AI-Tools aus Compliance-Gründen nicht eingesetzt
werden dürfen gilt für Dokumente die später mit KI weiterverarbeitet
werden sollen:

Dokumente müssen so aufgebaut sein dass:
- der Kontext ohne mündliche Erklärung erschließbar ist
- jedes Dokument eine klare Zweck- und Quellenangabe enthält
- Entscheidungen und Begründungen explizit im Dokument stehen
- keine impliziten Annahmen vorausgesetzt werden


--------------------------------------------------------------------------------
10. REPO- UND DOKUMENTATIONSSTRUKTUR
--------------------------------------------------------------------------------

10.1 R+MUNI App
----------------
R+MUNI ist die Applikation — immer public, unveränderlich öffentlich zugänglich.
Der Dokumentationsbereich der App ist initial leer und wird aus 01-public
befüllt.


10.2 Dokumentationsstruktur
-----------------------------
Die Dokumentation ist in zwei Bereiche getrennt:

  00-internal:
  - ausschließlich EUMAXL
  - sync mit non-public GitHub Repo
  - enthält Blueprint, GOV, Scripts, Sprint-Dokumentation
  - keine externe Zugänglichkeit

  01-public:
  - öffentlich zugänglich
  - enthält reduzierte Ableitungen aus 00-internal
  - Inhalte werden in den Dokumentationsbereich der App kopiert


10.3 Varianten und Ableitungslogik
------------------------------------
Geführte Varianten im Dokumentationsbereich:
  CARD     eigenständig geführt
  R+MUNI   eigenständig geführt
  DEV      eigenständig geführt — Basis für alle Ableitungen

EXPERT wird nicht eigenständig geführt.
EXPERT entsteht bei Bedarf als Extraktion aus DEV auf eigenem
Abstraktionslevel — on-demand, kein dauerhafter eigener Dokumentationsbereich.


10.4 Verbindliche Grundregeln
------------------------------
- 00-internal und 01-public sind strikt getrennt — keine Vermischung
- Inhalte aus 00-internal fließen nicht automatisch in 01-public
- Jede Übernahme von 00-internal nach 01-public erfordert explizite
  Betreiber-Freigabe
- Public-Inhalte besitzen keine Governance-Wirkung auf 00-internal
- Entwicklung erfolgt lokal mit Repo-Sync oder direkt im Repo
  — temporäre DEV-Kopien sind zulässig

---

## Bezüge

[[AI_DRIVEN_DEV_METHODE_DEV_S102]]        operative Arbeitsmethode, KI-Verhalten

---

================================================================================
R+MUNI GLOBAL GOVERNANCE | S1.02 | 2026-04-05 | R+MUNI Blueprint
================================================================================
