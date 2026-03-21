================================================================================
STAGE 7 – Real Beta & Ecosystem Expansion
Normative Definition und Geltungsbereich
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : STAGE7_ZIELE_S7
Datum           : 2026-03-21
Erstellt durch  : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
1. ZWECK VON STAGE 7
================================================================================

Stage 7 dient dem vollständigen Neustart des Beta-Betriebs auf sauberer
Basis — mit einem realen, aktiv genutzten Beta-Kontext, einer überarbeiteten
Onboarding-Struktur und dem gezielten Aufbau der Außenwirkung von R+MUNI.

Im Fokus stehen:
  - Neues Betakunden-Onboarding: strukturiert, reproduzierbar, dokumentiert
  - ASC als primärer Beta-Kontext: reale IT-Landschaft, echter Bedarf
  - Außenwirkung: GitHub Paketierung, README, Obsidian Vault öffentlich
  - Blueprint-Reife: AI-Driven Methodik, DEV Team, Toolbaukasten visuell
  - Kontinuierliche Verbesserung: Bugfixing, BPMN Flows, Feedbackschleifen

Stage 7 ist die erste Phase mit bewusst gesteuerter Außenwirkung
und einem vollständig neu aufgesetzten Beta-Betrieb —
kein Weitermachen, sondern Neustart auf reifer Basis.


================================================================================
2. AUSGANGSBASIS
================================================================================

Stage 7 baut auf dem eingefrorenen Stage-6-Zustand auf.

  - Stage-3-, Stage-4-, Stage-5- und Stage-6-Scripts sind read-only
  - Bestehende Logik gilt als normativ stabil
  - Erweiterungen erfolgen additiv, nicht modifizierend
  - Bugfixing ist zulässig — ohne Logikveränderung
  - ASC-Kontext ist vorbereitet — Onboarding startet in Stage 7

Ein Rückgriff auf Stage-3/4/5/6-Artefakte ist zulässig,
Eingriffe sind es nicht.
Ausnahme: Bugfixes mit expliziter Freigabe durch den Betreiber.

Bezug auf vorherigen Freeze:
  [[FREEZE-6_konsolidiert]]             Ausgangszustand für Stage 7


================================================================================
3. CHARAKTER VON STAGE 7
================================================================================

Stage 7 ist die erste Phase mit vollständig neu aufgesetztem Beta-Betrieb
und gezielt gesteuerter Außenwirkung.

  - Betakunde_01 wird sauber offgeboardet — kein stilles Auslaufen
  - ASC bringt eine reale IT-Landschaft mit (Domain, FTP, Homepage,
    Cloud-Speicher) — echter Kundenbedarf, keine Simulation
  - R+MUNI wird nach außen sichtbar: GitHub Paket, README, Obsidian Vault
  - DEV Team wird final fixiert — vom Wunschkonzert zur realen Gruppe
  - Methodik und Werkzeugkasten werden für Außenstehende verständlich

Stage 7 darf wachsen — nach außen, mit Struktur, ohne Rückkopplung.


================================================================================
4. ZULÄSSIGE INHALTE IN STAGE 7
================================================================================

4.1 Betakunden Offboarding — Betakunde_01 (S7-Z1)
---------------------------------------------------
  - Strukturierter Offboarding-Prozess für Betakunde_01 definieren
  - Atlassian-Zugang geordnet beenden oder auf PASSIV setzen
  - Offboarding als wiederholbares Artefakt im Blueprint dokumentieren
  - Erkenntnis aus Betakunde_01 Erfahrung festhalten (was hat gefehlt,
    was war gut, was würde beim nächsten Kunden anders gemacht)
  - Ziel: sauberer Abschluss — kein stilles Auslaufen, GOV-konform

Grenze: Keine Bewertung der Organisation von Betakunde_01.
        Erkenntnisse bleiben sachlich und blueprint-relevant.


4.2 Betakunden Onboarding — Neue Struktur (S7-Z2)
---------------------------------------------------
  - Onboarding-Prozess vollständig überarbeiten auf Basis S6-Erkenntnisse
  - R+MUNI Core Setup als reproduzierbares Paket definieren
  - Homepage-Integration evaluieren (ASC: Domain, FTP, Cloud-Speicher
    als reale Kundensituation — Erkenntnisse fließen in Blueprint)
  - Discord-Präsenz evaluieren (ASC: bestehender Channel als Ausgangspunkt)
  - Rollentrennung ASC: EUMAXL als Obmann strikt getrennt von DEV-Rolle
  - Ziel: neues Onboarding ist für jeden weiteren Beta-Kunden direkt
    anwendbar — kein individuelles Setup mehr

Grenze: Homepage und Discord sind Evaluierungs-Objekte, keine Pflicht.
        Erkenntnisse fließen in Blueprint — keine proprietären Lösungen.
        ASC-Rollentrennung (GOV 13.8) gilt ohne Ausnahme.


4.3 Feedbackschleifen ausbauen (S7-Z3)
----------------------------------------
  - Feedbackschleifen aus Stage 6 auf ASC-Kontext anwenden und validieren
  - Erkenntnisse aus aktivem Beta-Betrieb (ASC) strukturiert aufnehmen
  - Kanal-Struktur prüfen: Portal, GitHub Issues, E-Mail — was funktioniert
    im realen Vereinskontext?
  - How2-Dokumentation aktualisieren wenn neue Erkenntnisse entstehen
  - Ziel: Feedbackschleifen sind nicht nur dokumentiert sondern erprobt

Grenze: Feedback bleibt Input — kein direkter Eingriff in Kernlogik.
        GOV-Regel: Entwickler entscheidet über Umsetzung.


4.4 DEV Team Fixierung (S7-Z4)
--------------------------------
  - DEV Team final und verbindlich definieren — reale Personen, reale Rollen
  - Keine weiteren Änderungen nach Fixierung ohne Stage-Entscheid
  - Onboarding neuer Team-Mitglieder nach Blueprint-Standard
  - Rollen und Verantwortlichkeiten schriftlich festgehalten
  - Ziel: R+MUNI hat ein stabiles, dokumentiertes Team — kein Wunschkonzert

Grenze: Team-Fixierung ist keine GOV-Änderung.
        GOV-Hoheit bleibt ausschließlich beim Betreiber (EUMAXL).


4.5 GitHub Paketierung — Beta 1.0 Paket (S7-Z5)
-------------------------------------------------
  - GitHub Repository für öffentliches Beta-1.0-Paket aufsetzen
  - Paketinhalt definieren: was kommt rein, was bleibt intern
  - Clean-ZIP als Erstinstallations-Artefakt vorbereiten
  - Versionierungsstrategie für Beta-Releases definieren
  - Ziel: R+MUNI ist als Beta-1.0-Paket für neue Kunden direkt beziehbar

Grenze: Keine Kundenmodelle oder internen Daten im öffentlichen Repo.
        Paketierung ändert keine Blueprint-Logik.


4.6 README und Dokumentationsbereich ausbauen (S7-Z6)
-------------------------------------------------------
  - README vollständig überarbeiten — Einstieg für neue User optimieren
  - Alle Links prüfen und aktualisieren (GitHub Pages, Portal, externe Links)
  - Dokumentationsstruktur für externe Leser sichtbar machen
  - Ziel: Externer Leser versteht R+MUNI nach README-Lektüre ohne
    weitere Erklärung

Grenze: README ist Einstiegsdokument — keine vollständige Systemdoku.
        Technische Tiefe gehört in Principles und How2, nicht ins README.


4.7 Obsidian Vault öffentlich (S7-Z7)
---------------------------------------
  - Obsidian Vault in GitHub public bringen — navigierbare Blueprint-Doku
  - Entscheidung: welche Teile des Vaults sind öffentlich, welche bleiben intern
  - Verlinkungsstruktur prüfen — keine internen Referenzen im öffentlichen Teil
  - Ziel: Externer Leser kann Blueprint-Zusammenhänge navigieren ohne
    lokale Installation

Grenze: Keine internen Daten, keine Kundeninhalte im öffentlichen Vault.
        Obsidian bleibt Lesewerkzeug — keine neue Logikschicht.


4.8 Visuelle Aufbereitung Toolbaukasten (S7-Z8)
-------------------------------------------------
  - Toolbaukasten visuell aufbereiten — für Einsteiger und Sales-Kontext
  - Format offen: Diagramm, Infografik, interaktive Darstellung
  - Zielgruppe: nicht-technische Leser, potenzielle Kunden, Team-Onboarding
  - Ziel: Toolbaukasten ist auf einen Blick verständlich — ohne Doku-Lektüre

Grenze: Visuelle Aufbereitung ist Kommunikationsmittel — keine neue
        Dokumentationsebene mit normativer Wirkung.


4.9 AI-Driven Development Methodik Update (S7-Z9)
---------------------------------------------------
  - Erkenntnisse aus Stage 6 einarbeiten (Kapitel 15 aus Freeze 6)
  - Neue Variante testen: konkrete Session-Muster aus Stage 7 dokumentieren
  - ASC-Rollentrennung als neues Methodik-Muster aufnehmen (DEV ≠ Obmann)
  - Ziel: AI_DRIVEN_DEV_METHODE_S7 ist aktuell, erprobt und für
    Dritte reproduzierbar

Grenze: Methodik-Update ist additiv — keine Revision bestehender Kapitel
        ohne explizite Freigabe.


4.10 BPMN Flows parallel ausbauen (S7-Z10 — OPTIONAL)
-------------------------------------------------------
  - BPMN Default Flows für bestehende Script-Reihen schrittweise ergänzen
  - Kein Zwang — nur wenn Kapazität vorhanden
  - Jeder neue Flow ist eigenständig und additiv
  - flowmapping.txt wächst organisch mit
  - Ziel: Automatisierungsgrad steigt kontinuierlich wenn Luft da ist

Grenze: Kein Eingriff in bestehende Flows ohne explizite Freigabe.
        OPTIONAL bedeutet: kein Blocker für Stage-Abschluss.


4.11 Bugfixing & Optimierung R+MUNI Core (S7-Z11)
---------------------------------------------------
  - Bugfixing aus dem ASC-Betrieb ist explizit zulässig
  - Optimierungen ohne Logikveränderung sind erlaubt
  - Jeder Bugfix wird dokumentiert — kein stiller Fix
  - Rückkopplung auf Stage-3/4/5/6-Logik ist ausgeschlossen
  - Ziel: R+MUNI Core bleibt stabil unter realen Betriebsbedingungen

Grenze: Keine Veränderung der normativen Kernlogik ohne Stage-Entscheid.
        Bugfix ≠ Feature — Grenze ist explizit zu benennen.


================================================================================
5. UMGANG MIT ERKENNTNISSEN AUS VORHERIGEN STAGES
================================================================================

Erkenntnisse aus Stage 6 und früheren Stages dürfen:
  - in Stage 7 verwertet und weiterentwickelt werden
  - als Grundlage für GOV-Erweiterungen dienen
  - Onboarding- und Offboarding-Artefakte informieren
  - AI-Driven Methodik und Toolbaukasten-Dokumentation prägen

Sie dürfen jedoch nicht:
  - Stage-3/4/5/6-Artefakte verändern
  - rückwirkende Logikverschiebungen erzeugen
  - stillschweigend in Kernlogik einfließen

Stage 7 ist Expansion und Außenwirkung — nicht Revision.


================================================================================
6. RÜCKKOPPLUNGSSCHUTZ
================================================================================

  - Stage-3/4/5/6-Scripts bleiben read-only ohne Ausnahme
  - Bugfixes erfordern explizite Freigabe und Dokumentation
  - ASC-Erkenntnisse sind Input — kein direkter Eingriff in Kernlogik
  - Offboarding Betakunde_01 berührt keine Blueprint-Logik
  - GitHub Paketierung und README-Änderungen berühren keine Script-Logik
  - Obsidian Vault öffentlich: keine normativen Auswirkungen auf Blueprint


================================================================================
7. DOKUMENTATION IN STAGE 7
================================================================================

  - Stage 7 besitzt eigenes Claude-Projekt — neuer Kontext, sauberer Start
  - Sprint-Bezeichnung: Sprint-DEV-S7-<Kürzel> — keine andere Bezeichnung
  - Sprint Dev-Dokumentationen für alle Entwicklungsaktivitäten (GOV 10.8)
  - Offboarding und Onboarding als eigene Artefakte dokumentiert
  - ASC-Rollentrennung in jeder Session explizit gehalten (GOV 13.8)
  - Freeze 7 am Stage-Ende: erste Anwendung der neuen Freeze-Konvention

Fokus: Außenwirkung dokumentieren — was entsteht muss für Dritte
       nachvollziehbar und reproduzierbar sein.


================================================================================
8. ABGRENZUNG ZU SPÄTEREN STAGES
================================================================================

Nicht Teil von Stage 7 sind:
  - Vollständig automatisiertes Onboarding ohne manuelle Begleitung
  - Produktisierung mit Preismodell oder kommerziellem Vertrieb
  - Skalierbare Multi-Tenant-Architektur
  - Vollständige BPMN-Abdeckung aller Script-Reihen (wächst organisch)
  - Öffentliche Community-Infrastruktur (Forum, Support-Plattform)

Diese Themen wachsen aus Stage 7 heraus — sie sind Ergebnis, nicht
Voraussetzung. Stage 7 legt die Basis, nicht das fertige Gebäude.


================================================================================
9. FORMALE FESTSTELLUNG
================================================================================

Mit dieser Definition ist Stage 7:
  - logisch eröffnet
  - klar abgegrenzt von Stage 6
  - rückkopplungssicher
  - GOV-konform
  - auf Beta-Neustart, Außenwirkung und Blueprint-Expansion ausgerichtet

Stage 3, 4, 5 und 6 bleiben fixiert und geschützt.
Stage 7 darf wachsen — nach außen, mit Struktur, ohne zu verzerren.


================================================================================
BEZÜGE
================================================================================
[[GOV_Global_S6]]                    normative Grundlage (bis GOV S7 erstellt)
[[FREEZE-6_konsolidiert]]            Ausgangszustand — letzter stabiler Stand
[[BETA_ONBOARDING_Atlassian_S5]]     Onboarding-Basis (wird in S7 überarbeitet)
[[AI_DRIVEN_DEV_METHODE_S6]]         Methodik-Basis für S7-Update


================================================================================
Stage 7 – Real Beta & Ecosystem Expansion
ZIELE DEFINIERT | 2026-03-21
R+MUNI Blueprint | Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
