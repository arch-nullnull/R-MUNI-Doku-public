================================================================================
R+MUNI GLOBAL GOVERNANCE — STORY
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Global_GOV_STORY_S105
Tag             : #gov #story #rmuni #s105
Datum           : 2026-04-15
Stage           : S1.05 — AKTIV
Status          : ENTWURF — Freigabe EUMAXL
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN
Ablageort       : R+MUNI Doku-public\00-governance\Global_GOV_STORY_S105.md
================================================================================

---
title: "R+MUNI Global Governance — Story"
stage: S1.05
status: "ENTWURF"
typ: "GOV"
datum: "2026-04-15"
autor: EUMAXL
tags: [rmuni, blueprint, gov, story, s105]
---

================================================================================
LESEANWEISUNG
================================================================================

Dieses Dokument erklärt die Governance — warum die Regeln so sind wie sie sind.
Es ist kein Arbeitsdokument. Es wird nicht im Sprint geladen.

Arbeitende Governance: [[Global_GOV_DEV_S105]]
Dieses Dokument ist für: Onboarding, neue DEV-Mitglieder, Release-Kontext,
                          eigenes Verständnis des Betreibers.


================================================================================
1. ZWECK, INTENTION UND CHARAKTER DER GOVERNANCE
================================================================================

1.1 Warum diese Governance existiert
--------------------------------------
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


1.2 Was diese Governance nicht ist
------------------------------------
Diese Governance ist:
- keine Projektmanagement-Governance
- keine Prozessbeschreibung
- keine Rollen- oder Verantwortlichkeitsdefinition
- keine Verhaltensregeldefinition für KI (→ AI_DRIVEN_DEV_METHODE)

Sie definiert ausschließlich:
- was modelliert, integriert und automatisiert werden darf
- wie Identität, Führung und Ableitung zu erfolgen haben
- welche Regeln unveränderlich gelten


1.3 Warum Explizitheit das Grundprinzip ist
--------------------------------------------
Implizite Logik ist die häufigste Quelle von Fehlern in komplexen Systemen.
Wenn Entscheidungen nicht dokumentiert sind, sind sie nicht reproduzierbar.
Wenn Regeln nicht formuliert sind, gelten sie nicht.
Wenn Abweichungen nicht dokumentiert sind, werden sie zur Norm.

Das Blueprint-System ist darauf ausgelegt dass jeder Stand rekonstruierbar ist —
ohne mündliche Überlieferung, ohne implizites Kontextwissen.


1.4 Warum Stabilität vor Komfort gilt
---------------------------------------
Diese Governance priorisiert:
- Stabilität über Komfort
- Nachvollziehbarkeit über Geschwindigkeit
- Disziplin über kurzfristige Optimierung

Hintergrund: Kurzfristige Vereinfachungen erzeugen langfristige Komplexität.
Jede Ausnahme die nicht explizit geregelt ist wird zur impliziten Regel.
Das Blueprint-System ist auf lange Laufzeit ausgelegt — nicht auf schnelle
Erstlieferung.


================================================================================
2. GRUNDBEGRIFFE UND ABGRENZUNGEN
================================================================================

2.1 Warum Begriffe normativ definiert werden
---------------------------------------------
Begriffe die nicht eindeutig definiert sind werden unterschiedlich interpretiert.
Unterschiedliche Interpretation erzeugt inkonsistente Umsetzung.
Inkonsistente Umsetzung untergräbt die Governance.

Alle Begriffe in diesem System werden daher normativ — das heißt verbindlich
und eindeutig — verwendet.


2.2 Objekt
-----------
Ein Objekt ist eine eindeutig identifizierbare Einheit innerhalb des
Blueprint-Systems.

Ein Objekt besitzt eine stabile Identität und existiert unabhängig von
Darstellung, Tool oder Format.

Ein Objekt ist nicht gleichzusetzen mit seiner visuellen Darstellung.

Hintergrund: Die Trennung von Objekt und Darstellung ist fundamental.
Dasselbe Objekt kann in Archi, als CSV, als SVG dargestellt werden —
es bleibt dasselbe Objekt mit derselben Identität.


2.3 Identität
--------------
Die Identität eines Objekts ist unabhängig von Name, Typ oder Darstellung.
Sie bleibt über alle Iterationen hinweg stabil und ist die Grundlage aller
Integrations- und Ableitungsprozesse.

Identität ist nicht interpretierbar.

Hintergrund: Wenn Identität interpretierbar wäre, wäre jede Integration
nicht-deterministisch. Das System würde bei jedem Lauf möglicherweise
andere Ergebnisse produzieren.


2.4 Objekt-ID
--------------
Die Objekt-ID ist eindeutig, stabil und repository-weit gültig.
Sie ist der alleinige Referenzanker für Integration und Automatisierung.

Objektnamen oder Tool-IDs ersetzen keine Objekt-ID.

Hintergrund: Namen ändern sich. Tool-IDs sind tool-spezifisch.
Nur die Objekt-ID ist stabil über alle Werkzeuge und alle Iterationen hinweg.


2.5 Führung
------------
Führung beschreibt, welche Quelle für eine Information verbindlich ist.
Sie wird explizit festgelegt und kann feldgenau variieren.

Ohne explizite Führungsdefinition existiert keine Führung.

Hintergrund: In einem System mit mehreren Quellen für dieselbe Information
(Archi-Modell, CSV, Jira, etc.) muss eindeutig definiert sein welche Quelle
Vorrang hat. Ohne diese Definition entstehen Konflikte die nicht
deterministisch auflösbar sind.


2.6 Integration
----------------
Integration bezeichnet die kontrollierte Zusammenführung von Informationen
aus unterschiedlichen Quellen gemäß der definierten Führungslogik.

Integration ist regelbasiert, deterministisch und reproduzierbar.

Hintergrund: Integration ist kein manueller Abgleich. Sie ist ein
definierter, reproduzierbarer Prozess. Nur dann ist das Ergebnis
verlässlich und auditierbar.


2.7 Ableitung
--------------
Ableitung beschreibt die Überführung von Architektur- oder
Integrationsinformationen in andere Artefakte oder Formate.

Ableitung ist explizit definiert, nachvollziehbar und erzeugt keine
neue Identität. Sie wirkt nicht rück auf die Quelle.

Hintergrund: Abgeleitete Artefakte (SVGs, Reports, CSVs) sind Repräsentationen
— keine neuen Wahrheiten. Wenn eine Ableitung rückwirken würde, wäre die
Führungslogik gebrochen.


2.8 Rückwirkung
-----------------
Rückwirkung bezeichnet jede Veränderung eines führenden Artefakts durch
ein abgeleitetes Artefakt.

Rückwirkungen sind grundsätzlich unzulässig, sofern nicht explizit geregelt.

Hintergrund: Rückwirkungen erzeugen Zyklen. Zyklen erzeugen
nicht-deterministisches Verhalten. Nicht-deterministisches Verhalten
ist im Blueprint-System unzulässig.


2.9 Implizit vs. Explizit
---------------------------
Implizit bedeutet: nicht dokumentiert, nicht nachvollziehbar,
interpretationsabhängig.

Explizit bedeutet: klar formuliert, dokumentiert, reproduzierbar.

Diese Governance bevorzugt explizite Lösungen in allen Fällen.

Hintergrund: Implizite Lösungen funktionieren solange alle Beteiligten
denselben Kontext teilen. Sobald der Kontext wechselt — neue Session,
neues Teammitglied, neues Werkzeug — versagen implizite Lösungen.


================================================================================
3. GOVERNANCE-VERSTÄNDNIS UND REGELCHARAKTER
================================================================================

3.1 Warum Governance als Regelwerk und nicht als Empfehlung
------------------------------------------------------------
Governance wird in diesem Projekt als verbindliches Regelwerk verstanden.

Governance definiert zulässige und unzulässige Zustände, legt unveränderliche
Prinzipien fest und begrenzt den Lösungsraum bewusst.

Governance ist kein Prozess, keine Empfehlung und keine Sammlung von
Best Practices.

Hintergrund: Empfehlungen werden situativ ignoriert. Regelwerke nicht.
Der Unterschied ist nicht akademisch — er entscheidet ob das System
unter Druck hält oder nicht. R+MUNI ist unter Druck entstanden.
Die Governance muss unter Druck halten.


3.2 Warum alle Regeln normativ sind
-------------------------------------
Alle in dieser Governance definierten Regeln sind normativ.

Sie sind verbindlich, gelten unabhängig von Kontext oder Bequemlichkeit
und sind nicht optional.

Abweichungen sind nur zulässig, wenn sie explizit geregelt sind.

Hintergrund: Eine Regel die optional ist, ist keine Regel.
Eine Regel die nur gilt wenn sie bequem ist, ist eine Empfehlung.
Das Blueprint-System braucht Regeln die auch dann gelten wenn
es unbequem ist — besonders dann.


3.3 Warum Abweichungen explizit dokumentiert werden müssen
-----------------------------------------------------------
Abweichungen von Governance-Regeln sind grundsätzlich unerwünscht.

Sofern Abweichungen zugelassen sind:
- Abweichungen müssen explizit benannt werden
- Abweichungen müssen nachvollziehbar begründet sein
- Abweichungen erzeugen keine Präzedenzwirkung

Implizite oder stillschweigende Abweichungen sind unzulässig.

Hintergrund: Nicht dokumentierte Abweichungen werden zur impliziten Regel.
Das untergräbt die Governance schrittweise — ohne dass es auffällt.
Jede Abweichung die explizit ist, bleibt kontrollierbar.


3.4 Warum keine implizite Weiterentwicklung
--------------------------------------------
Neue Regeln entstehen nicht durch Gewohnheit.
Neue Standards entstehen nicht durch Wiederholung.
Neue Bedeutungen entstehen nicht durch Interpretation.

Änderungen erfolgen ausschließlich durch bewusste, explizite Entscheidungen.

Hintergrund: Systeme die sich durch Gewohnheit weiterentwickeln verlieren
ihre Nachvollziehbarkeit. Irgendwann gilt eine Regel "weil man das immer
so gemacht hat" — ohne dass jemand sagen kann warum.
R+MUNI dokumentiert den Grund jeder Regel.


================================================================================
4. ARCHITEKTUR- UND MODELLPRINZIPIEN
================================================================================

Hinweis: Diese Prinzipien sind Hintergrund für die Regeln in Kap. 3 der
arbeitenden GOV. Sie erklären die Designentscheidungen — sie sind selbst
keine operativen Regeln.


4.1 Identitätsprimat
---------------------
Die Identität eines Objekts ist das zentrale Ordnungsprinzip des
Blueprint-Systems.

Alle Architektur- und Modellentscheidungen haben die Identität zu
respektieren.

Warum: Ohne stabiles Identitätsprimat ist keine verlässliche Integration
möglich. Alles andere — Namen, Typen, Darstellungen — kann sich ändern.
Die Identität darf es nicht.


4.2 Trennung von Struktur, Semantik und Darstellung
-----------------------------------------------------
Das Blueprint-System trennt strikt zwischen:
- Struktur (Objekte, Beziehungen, Rollen)
- Semantik (fachliche Bedeutung, Beschreibung)
- Darstellung (Visualisierung, Tool-spezifische Repräsentation)

Diese Trennung ist verbindlich und darf nicht aufgehoben werden.
Semantik darf nicht aus Struktur oder Darstellung implizit abgeleitet werden.

Warum: Vermischung dieser Ebenen erzeugt Abhängigkeiten die langfristig
nicht beherrschbar sind. Ein Tool-Wechsel sollte nie die Architektur
verändern müssen.


4.3 Explizitheit als Modellierungsprinzip
------------------------------------------
Alle relevanten Modellierungsentscheidungen sind explizit zu treffen.
Keine impliziten Annahmen. Keine verdeckte Logik. Keine stillschweigende
Interpretation.

Warum: Implizite Modellierungsentscheidungen sind nicht auditierbar.
Sie sind nicht reproduzierbar. Sie versagen wenn der Kontext wechselt.


4.4 Determinismus
------------------
Das Blueprint-System ist deterministisch aufgebaut.

Gleiche Eingaben führen zu gleichen Ergebnissen.
Integrations- und Ableitungsprozesse sind reproduzierbar.
Modellzustände sind eindeutig bestimmbar.

Nicht-deterministisches Verhalten ist unzulässig.

Warum: Ein System das bei gleichen Eingaben unterschiedliche Ergebnisse
produziert ist nicht verlässlich. Verlässlichkeit ist Grundvoraussetzung
für produktiven Einsatz.


4.5 Tool-Unabhängigkeit
------------------------
Das Blueprint-Modell ist unabhängig von konkreten Werkzeugen oder Plattformen.

Keine Tool-Semantik im Architekturmodell.
Keine impliziten Tool-Abhängigkeiten.
Keine Vermischung von Architektur und Ausführung.

Werkzeuge dienen der Umsetzung, nicht der Definition der Architektur.

Warum: Tools wechseln. Archi könnte durch ein anderes Tool ersetzt werden.
Die Architektur darf davon nicht abhängen.


4.6 Architektur als Referenz, nicht als Ausführung
----------------------------------------------------
Architekturmodelle beschreiben Struktur, Rollen und Beziehungen.
Sie beschreiben nicht Ausführungslogik, technische Steuerung oder
Laufzeitverhalten.

Die Architektur ist Referenz, nicht Implementierung.

Warum: Wenn Architektur Ausführungslogik enthält, koppelt sie sich an
Implementierungsdetails. Das macht sie fragil und schwer wartbar.


4.7 Beziehungsprimat der Objektstabilität
------------------------------------------
Die Stabilität von Objekten hat Vorrang vor der Präzision von Beziehungen.

Objekttypen werden nicht geändert um Beziehungen zu ermöglichen.
Ist keine normkonforme Beziehung zwischen zwei Objekten möglich, ist
Association als normkonformer Fallback zulässig.
Beziehungstypen werden nicht semantisch überladen.

Warum: Ein falsch typisiertes Objekt erzeugt Folgefehler die schwer
zu lokalisieren sind. Eine generische Beziehung ist ehrlicher als
eine semantisch überladene Präzisionsbeziehung.


================================================================================
5. ARTEFAKTROLLEN UND EBENENTRENNUNG — HINTERGRUND
================================================================================

5.1 Was ein Artefakt ist
-------------------------
Ein Artefakt ist eine konkrete Repräsentation von Informationen in einem
bestimmten Kontext, Format oder Werkzeug.

Ein Artefakt repräsentiert Objekte, besitzt aber keine eigene Identität.
Es ist kontext- und zweckgebunden und unterliegt einer klar definierten Rolle.

Warum wichtig: Artefakte sind nicht die Wahrheit — sie repräsentieren sie.
Diese Unterscheidung ist fundamental für das Führungsprinzip.


5.2 Führendes Artefakt
-----------------------
Ein führendes Artefakt definiert die verbindliche Wahrheit für bestimmte
Informationen.

Es ist explizit als führend definiert und besitzt keine implizite Führung.
Ohne explizite Definition existiert kein führendes Artefakt.

Warum: Implizite Führung erzeugt Konflikte die nicht deterministisch
auflösbar sind. Führung muss eine bewusste Entscheidung sein.


5.3 Die drei Ebenen
--------------------
Das Blueprint-System trennt strikt zwischen:
- Architektur — beschreibt Struktur, Rollen, Beziehungen
- Integration — führt Informationen aus mehreren Quellen zusammen
- Ableitung / Ausführung — materialisiert für spezifische Zwecke

Diese Ebenen sind logisch getrennt und dürfen nicht vermischt werden.
Rückwirkungen zwischen Ebenen sind normativ ausgeschlossen.

Warum: Vermischung dieser Ebenen erzeugt Zyklen und nicht-deterministisches
Verhalten. Die Trennung ist der Schutz vor systembedingter Inkonsistenz.


================================================================================
6. SPRINTS — HINTERGRUND UND INTENTION
================================================================================

6.1 Warum Sprints explizit geregelt sind
-----------------------------------------
Sprints sind in vielen Projekten governance-freie Räume — das ist das Problem.
In R+MUNI ist ein Sprint explizit geregelt weil er sonst als Ausrede für
Regelabweichungen verwendet wird.

"Wir sind im Sprint" ist keine Begründung für eine Governance-Verletzung.
Das war eine bewusste Designentscheidung.


6.2 Warum die Dokumentationspflicht im Sprint eingeschränkt ist
----------------------------------------------------------------
Während eines Sprints müssen Zwischenschritte nicht vollständig dokumentiert
werden. Das ist kein Widerspruch zur Governance — es ist eine normativ
zugelassene Pragmatismus-Regel.

Hintergrund: Vollständige Echtzeit-Dokumentation bremst die Arbeit ohne
proportionalen Mehrwert. Was zählt ist dass das Ergebnis rekonstruierbar
ist — nicht dass jeder Zwischenschritt protokolliert ist.


6.3 Warum Session-Regeln existieren
-------------------------------------
Session-Regeln erlauben situative Anpassungen ohne die Governance zu ändern.
Sie sind auf die laufende Session begrenzt und erzeugen keine Präzedenz.

Hintergrund: In der Praxis gibt es immer Situationen die nicht vollständig
durch statische Regeln abgedeckt sind. Die Session-Regel ist das
Ventil — kontrolliert, begrenzt, explizit.


================================================================================
7. USER-UMGANG — HINTERGRUND
================================================================================

7.1 Grundhaltung
-----------------
R+MUNI ist und bleibt kostenlos.

Für den User-Kontakt gilt:
- Offenheit und Ehrlichkeit sind nicht verhandelbar
- Kritik von Usern ist Feedback — kein Angriff
- Kein User wird zu einem Upgrade, einer Zahlung oder einer Entscheidung
  gedrängt
- Der Entwickler behält das Recht situativ zu entscheiden was er annimmt
  und was nicht — Kapazität ist eine legitime Absage

Warum: R+MUNI ist ein ehrliches Projekt. Die Außenwirkung muss das spiegeln.
Kein Marketing das nicht hält was es verspricht.


7.2 User-Feedback als Blueprint-Input
----------------------------------------
Feedback aus dem Livebetrieb darf:
- in die laufende Entwicklung einfließen
- als Grundlage für GOV-Erweiterungen dienen

Feedback darf nicht:
- Kernlogik verändern ohne expliziten Entwicklerentscheid
- ohne expliziten Entwicklerentscheid umgesetzt werden

Warum: User-Feedback ist wertvoll aber kein direkter Steuerungseingang.
Der Betreiber bleibt Kontrollorgan — Feedback ist Input, nicht Befehl.


================================================================================
8. EXTERNE ERKENNTNISQUELLEN — HINTERGRUND
================================================================================

8.1 Warum externe Erkenntnisse getrennt behandelt werden
---------------------------------------------------------
Erfahrungen aus Kundensupport, Begleitprojekten oder regulierten Umgebungen
sind wertvoller Rohstoff — aber kein direkter Blueprint-Input.

Ohne explizite Trennung vermischen sich Kundenspezifika mit generischen
Blueprint-Prinzipien. Das untergräbt die Übertragbarkeit des Systems.


8.2 Die Dreistufenlogik
------------------------
  Stufe 1 — Erfahrungsbericht [CUSTO]:
  - Erkenntnis wird aufgenommen
  - kein automatischer Transfer in R+MUNI-Strukturen

  Stufe 2 — Transfer-Anfrage [CUSTO→RMUNI]:
  - Betreiber löst explizit einen Transfer aus
  - nur die transferierbare Prozess- oder Architektur-Erkenntnis fließt ein

  Stufe 3 — Freigabe durch Betreiber:
  - transferiertes Ergebnis wird vom Betreiber geprüft und freigegeben
  - erst nach Freigabe wird es in R+MUNI-Dokumentation übernommen

Warum drei Stufen: Jede Stufe ist ein Kontrollpunkt.
Ohne Kontrollpunkte fließen Kundenspezifika unkontrolliert ein.


8.3 Kontext-Hygiene bei eingeschränktem AI-Einsatz
----------------------------------------------------
In Umgebungen in denen AI-Tools aus Compliance-Gründen nicht eingesetzt
werden dürfen gilt für Dokumente die später mit KI weiterverarbeitet
werden sollen:

Dokumente müssen so aufgebaut sein dass:
- der Kontext ohne mündliche Erklärung erschließbar ist
- jedes Dokument eine klare Zweck- und Quellenangabe enthält
- Entscheidungen und Begründungen explizit im Dokument stehen
- keine impliziten Annahmen vorausgesetzt werden

Warum: KI kann nur mit dem arbeiten was im Dokument steht.
Implizites Kontextwissen existiert für KI nicht.


================================================================================
BEZÜGE
================================================================================

[[Global_GOV_DEV_S105]]            arbeitende Governance — Regeln
[[AI_DRIVEN_DEV_METHODE_DEV_S105]] KI-Verhalten, operative Arbeitsmethode
[[naming_and_structure_S104]]      Naming, Ablage, Struktur

================================================================================
R+MUNI GLOBAL GOVERNANCE STORY | S1.05 | 2026-04-15 | R+MUNI Blueprint
================================================================================
