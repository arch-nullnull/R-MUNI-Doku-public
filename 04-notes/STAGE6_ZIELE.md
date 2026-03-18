Stage 6 – Beta Feedback Integration & Blueprint Maturity
Normative Definition und Geltungsbereich
Datum: 2026-03-18

1. Zweck von Stage 6
Stage 6 dient der gezielten Einbindung von Beta-Kunden-Feedback in den
Entwicklungszustand und der strukturellen Reifung des Blueprints.
Im Fokus stehen:
	• Einbindung von Beta-Kunden-Feedback in den Entwicklungszustand
	• Feedbackschleifen definieren und dokumentieren (DEV und Kundensicht)
	• Reviewschleifen mit neuer Stage-Bezeichnung in der Beta-Phase
	• Obsidian-Nutzung im Blueprint – MD-Beziehungen für sichtbare Zusammenhänge
	• Template für Dokumententypen im Blueprint (Outcome aus Beta-Umgebung)
	• Toolbaukasten transparent für User — extern und intern sichtbar
Stage 6 ist die erste Phase in der externes Feedback strukturiert
in den Blueprint zurückfließt – kontrolliert, dokumentiert, GOV-konform.

2. Ausgangsbasis
Stage 6 baut auf dem eingefrorenen Stage-5-Zustand auf.
	• Stage-3-, Stage-4- und Stage-5-Scripts sind read-only
	• Bestehende Logik gilt als normativ stabil
	• Erweiterungen erfolgen additiv, nicht modifizierend
	• Bugfixing ist zulässig – ohne Logikveränderung
	• Feedback aus dem Beta-Betrieb ist zulässiger Auslöser für Sprints
Ein Rückgriff auf Stage-3/4/5-Artefakte ist zulässig, Eingriffe sind es nicht.
Ausnahme: Bugfixes mit expliziter Freigabe durch den Entwickler.

3. Charakter von Stage 6
Stage 6 ist die erste Phase mit strukturierter Feedbackverarbeitung
und gezielter Blueprint-Reifung.
	• Beta-Kunden geben aktiv Feedback – das fließt kontrolliert ein
	• DEV und Kundensicht werden bewusst getrennt behandelt
	• Blueprint-Dokumentation wird durch Templates standardisiert
	• Obsidian wird als Werkzeug für Zusammenhänge im Blueprint etabliert
	• Reviewschleifen machen den Beta-Status sichtbar und nachvollziehbar
Stage 6 darf reifen – strukturiert und rückkopplungssicher.

4. Zulässige Inhalte in Stage 6

4.1 Einbindung Beta-Kunden-Feedback (S6-Z1)
	• Feedback aus dem Beta-Betrieb wird strukturiert gesammelt und bewertet
	• Eingehende Rückmeldungen fließen als dokumentierte Auslöser in Sprints ein
	• Feedback-Kategorien: Bug, Feature Request, DEV Anfrage (gemäß Portal-Setup)
	• Kein stilles Einarbeiten – jeder Feedback-Input wird nachvollziehbar verknüpft
	• GOV-Regel: Feedback ist Input, kein Auftrag – Entwickler entscheidet
Grenze: Kein Feedback verändert normative Kernlogik ohne Stage-Entscheid.

4.2 Feedbackschleifen – How2 für GitHub, Jira, E-Mail (S6-Z2)
	• DEV-Sicht und Kundensicht werden bewusst getrennt dokumentiert
	• DEV-Feedbackschleife (intern):
		○ GitHub Issues als strukturierter Entwicklerkanal
		○ Jira als Tracking- und Priorisierungswerkzeug
		○ E-Mail als Fallback – definierter Umgang dokumentiert
	• Kundenfeedbackschleife (extern):
		○ JSM/CSM Portal als primärer Kanal (Bug / Feature / DEV Anfrage)
		○ Kunde erhält Rückmeldung – kein schwarzes Loch
		○ E-Mail nur nach Rücksprache – kein direkter Kanal ohne Grund
	• How2-Dokument für beide Schleifen wird im Blueprint abgelegt
	• Ziel: Feedbackweg ist für DEV und Kunde klar und nachvollziehbar

4.3 Reviewschleifen – Stage-Bezeichnung in Beta-Dokumenten (S6-Z3)
	• Alle Dokumente im Beta-Zustand erhalten eine sichtbare Stage-Bezeichnung
	• Format wird definiert und verbindlich – kein optionales Cosmetic
	• Ziel: Externer Leser erkennt sofort ob ein Dokument Beta-Status hat
	• Reviewschleife bedeutet: Dokument wird am Ende eines Sprints
	  oder Stage-Abschnitts auf Aktualität geprüft und Bezeichnung aktualisiert
	• Rückwirkend: bestehende Dokumente werden schrittweise nachgezogen
Grenze: Bezeichnung ist Transparenzmittel – keine inhaltliche Änderung.

4.4 Obsidian-Nutzung im Blueprint (S6-Z4)
	• Obsidian wird als Werkzeug für MD-basierte Zusammenhänge im Blueprint eingeführt
	• Verlinkungen zwischen Dokumenten (MD-Links) machen Abhängigkeiten sichtbar
	• Ziel: Zusammenhänge zwischen GOV, Sprints, Stages und Artefakten
	  werden navigierbar – nicht nur lesbar
	• Obsidian ist Lesewerkzeug und Navigationshilfe – keine neue Logikschicht
	• Kein Eingriff in bestehende Dateistruktur oder Dateinamen
	• Obsidian-Vault liegt im Blueprint – portabel, kein Cloud-Zwang
Grenze: Obsidian ergänzt – ersetzt keine bestehenden Dokumentenformate.

4.5 Template für Dokumententypen im Blueprint (S6-Z5)
	• Outcome aus der Beta-Umgebung: welche Dokumententypen existieren real
	• Templates werden für die wichtigsten Typen definiert:
		○ Sprint Dev-Dokumentation
		○ Stage-Ziele Dokument
		○ GOV-Ergänzung
		○ How2-Dokument
		○ Freeze-Dokument
	• Jedes Template enthält: Pflichtfelder, optionale Felder, Beispielstruktur
	• Templates werden im Blueprint unter 00-concept abgelegt
	• Ziel: Neues Dokument hat sofort eine valide Grundstruktur –
	  kein Neuerfinden pro Sprint

4.6 Toolbaukasten transparent für User (S6-Z6)
	• Das Prinzip des R+MUNI Toolbaukastens wird auf zwei Ebenen sichtbar:

	Externe Ebene (User / Beta-Kunde):
		○ Eigene Seite im Externen Wiki — klar, ohne technischen Overhead
		○ Welche Tools es gibt und was sie kosten (Transparenz)
		○ Warum genau diese Tools gewählt wurden (Philosophie)
		○ Wie die Tools zusammenspielen (Zusammenhänge)
		○ Ziel: User versteht den Baukasten ohne Vorkenntnisse —
		  und vertraut der Entscheidungslogik dahinter

	Interne Ebene (DEV / Blueprint):
		○ Toolbaukasten-Prinzip wird in Sprint Dev-Dokus sichtbar verankert
		○ Jedes neue Tool erhält eine definierte Stelle im Blueprint
		○ Entscheidungsgrundlage (Warum dieses Tool) wird dokumentiert
		○ Kostenstruktur und Abhängigkeiten werden transparent gehalten

	• Grundsatz bleibt: R+MUNI läuft kostenlos — Tools sind Ergänzung,
	  kein Zwang und keine versteckte Abofalle
	• Wer ein Tool übernehmen möchte, findet den Weg selbst —
	  organisch, informiert, ohne Druck
Grenze: Toolbaukasten-Seite ist Transparenzartefakt — keine Werbung,
keine Empfehlung mit Eigeninteresse.

5. Umgang mit Stage-5-Erkenntnissen
Erkenntnisse aus Stage 5 und dem Beta-Betrieb dürfen:
	• in Stage 6 verwertet werden
	• als Grundlage für GOV-Erweiterungen dienen
	• Template-Definitionen informieren
Sie dürfen jedoch:
	• Stage-3/4/5-Artefakte nicht verändern
	• keine rückwirkende Logikverschiebung erzeugen
Stage 6 ist Reifung und Standardisierung, nicht Revision.

6. Rückkopplungsschutz
	• Stage-3/4/5-Scripts bleiben read-only
	• Bugfixes erfordern explizite Freigabe und Dokumentation
	• Feedback ist Input – kein direkter Eingriff in Kernlogik
	• Obsidian-Vault greift nicht in Blueprint-Dateistruktur ein
	• Templates sind Vorlagen – keine normativen Pflichtformate rückwirkend

7. Dokumentation in Stage 6
	• Stage 6 besitzt eigene Dokumentation im Claude-Projekt
	• Sprint-Bezeichnung: Sprint 6.x – keine andere Bezeichnung zulässig
	• Sprint Dev-Dokumentationen für alle Entwicklungsaktivitäten
	• GOV-Erweiterungen werden formal dokumentiert
	• Fokus: Feedbackintegration, Blueprint-Reife, Standardisierung

8. Abgrenzung zu späteren Stages
Nicht Teil von Stage 6 sind:
	• vollautomatische Feedbackverarbeitung ohne Entwicklerentscheid
	• vollständige Rückwärts-Migration aller Dokumente auf neue Templates
	• Obsidian als Pflicht-Werkzeug für alle Blueprint-Nutzer
	• Toolbaukasten als vollständige Produktdokumentation für alle Tools
	• Skalierung auf Multi-User Blueprint-Nutzung
Diese Themen wachsen aus Stage 6 heraus – sie sind Ergebnis, nicht Voraussetzung.

9. Formale Feststellung
Mit dieser Definition ist Stage 6:
	• logisch eröffnet
	• klar abgegrenzt von Stage 3, 4 und 5
	• rückkopplungssicher
	• GOV-konform
	• auf Feedbackintegration und Blueprint-Reife ausgerichtet
Stage 3, Stage 4 und Stage 5 bleiben fixiert und geschützt.
Stage 6 darf reifen, ohne zu verzerren.

================================================================================
Stage 6 – Beta Feedback Integration & Blueprint Maturity
ZIELE DEFINIERT | 2026-03-18
R+MUNI Blueprint | Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
