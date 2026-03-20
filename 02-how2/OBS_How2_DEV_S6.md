================================================================================
OBS – Obsidian als DEV-Werkzeug im Blueprint – HOW2 (DEV)
Stage 6 | Aktiv | R+MUNI Blueprint
================================================================================
Erstellt    : 2026-03-19
Stage       : S6 – AKTIV
Ablageort   : R+MUNI Doku-public\02-how2\OBS_How2_DEV_S6.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[GOV_Global_S6]] gelesen – Obsidian ist Lesewerkzeug + Navigationshilfe,
  keine neue Logikschicht, kein Eingriff in Blueprint-Dateistruktur
- Obsidian installiert (obsidian.md – kostenlos)
- Vault zeigt auf Parent-Ordner aller R+MUNI Ordner
  (dort wo R+MUNI, R+MUNI Doku-public, R+MUNI Doku-internal etc. liegen)
- .obsidian/ in .gitignore aller Repos eingetragen
- Plugin "Dataview" installiert (optional, für spätere Abfragen)
- Plugin "Templater" installiert (optional, für Vorlagen-Automation)


================================================================================
OBSIDIAN IM BLUEPRINT – GRUNDPRINZIPIEN
================================================================================

Obsidian liest den Blueprint so wie er ist.
Keine neue Struktur, keine neuen Dateien die Git verschmutzen.
.obsidian/ liegt im .gitignore – Vault-Einstellungen bleiben lokal.

Obsidian macht drei Dinge die kein anderes Werkzeug kann:
  1. [[Links]] zwischen MD-Dokumenten sichtbar machen
  2. Graph-View: Abhängigkeiten zwischen Dokumenten visuell zeigen
  3. SVG und PNG direkt inline rendern ohne extra Viewer

Obsidian greift NICHT ein in:
  - R+MUNI Scripts oder Konfigurationen
  - Git-Sync oder GitHub-Struktur
  - Stage-3/4/5-Artefakte (read-only bleibt read-only)


================================================================================
VAULT EINRICHTEN
================================================================================

Schritt 1 – Vault öffnen:
  Obsidian starten → "Ordner als Vault öffnen"
  → Parent-Ordner wählen (dort wo alle R+MUNI Ordner nebeneinander liegen)
  → NICHT einen Unterordner wählen – sonst fehlen Cross-Links zwischen
    R+MUNI, R+MUNI Doku-public, R+MUNI Doku-internal etc.

Schritt 2 – .gitignore prüfen (in jedem Repo):
  .obsidian/ muss in .gitignore stehen
  → Vault-Einstellungen landen nicht in GitHub

Schritt 3 – Link-Format einstellen:
  Einstellungen → Dateien & Links
  → "Neue Link-Format": Relativer Pfad
  → "Wikilinks verwenden": AN


================================================================================
[[LINKS]] – KONVENTION
================================================================================

[[Links]] verbinden Blueprint-Dokumente direkt miteinander.
Obsidian zeigt diese Verbindungen im Graph-View.

Grundregel:
  Jedes Dokument verlinkt mindestens:
    [[GOV_Global_S6]]      – normative Grundlage
    [[FREEZE-6]]           – aktueller Ausgangszustand

Bezüge-Block am Ende jedes Dokuments (Pflicht):
  [[GOV_Global_S6]]                    normative Grundlage
  [[FREEZE-6]]                         aktueller Ausgangszustand
  [[<verwandtes Dokument>]]            <warum relevant>

Link-Typen:
  [[Dokumentname]]                     – Link auf ein Dokument
  [[Dokumentname|Anzeigetext]]         – Link mit eigenem Anzeigetext
  [[Dokumentname#Abschnitt]]           – Link direkt auf einen Abschnitt

Was NICHT verlinkt wird:
  - Externe URLs → normale Markdown-Links: [Text](https://...)
  - Scripts, CSVs, CFGs → nur beschreiben, nicht verlinken


================================================================================
SVG EINBETTEN – KONVENTION
================================================================================

Ablageort für alle Diagramme:
  R+MUNI Doku-creative\images\r+muni\diagrams\

  Unterordner "diagrams" anlegen falls noch nicht vorhanden.

Namenskonvention:
  <reihe>_<beschreibung>_S<stage>.svg          SVG aus Archi-Export
  <reihe>_<beschreibung>_claude_S<stage>.svg   SVG von Claude generiert
  <reihe>_<beschreibung>_S<stage>.png          PNG Fallback

Einbettung im MD-Dokument (relativer Pfad):
  Aus Doku-public\02-how2\:
  ![Beschreibung](../../R+MUNI Doku-creative/images/r+muni/diagrams/<datei>.svg)

  Aus Doku-internal\backlog\ oder \sprints\:
  ![Beschreibung](../../R+MUNI Doku-creative/images/r+muni/diagrams/<datei>.svg)

Archi SVG-Export:
  Archi → View auswählen → Datei → Exportieren → Bild exportieren
  → Format: SVG
  → speichern in R+MUNI Doku-creative\images\r+muni\diagrams\

Claude SVG speichern:
  SVG-Code aus Claude-Antwort kopieren
  → Notepad++ → neue Datei → einfügen → speichern als .svg
  → ablegen in R+MUNI Doku-creative\images\r+muni\diagrams\

PNG als Fallback:
  Nur wenn SVG nicht möglich (externe Tools, Screenshots)
  SVG ist immer bevorzugt – PNG nur als letzter Ausweg


── WARUM SVG BEVORZUGT ─────────────────────────────────────────────────────────

  SVG ist XML       → Git trackt Änderungen zeilengenau
  SVG ist Text      → in Notepad++ lesbar und editierbar
  SVG skaliert      → scharf auf jedem Bildschirm und Ausdruck
  Archi exportiert  → SVG als natives Format
  Claude generiert  → SVG direkt in der Session
  Obsidian rendert  → SVG nativ inline ohne Plugin


================================================================================
FRONTMATTER – KONVENTION
================================================================================

Jedes Blueprint-MD-Dokument beginnt mit Frontmatter.
Obsidian liest Frontmatter und macht es durchsuchbar + filterbar.

Pflichtfelder:
  ---
  title: "<Dokumenttitel>"
  stage: S6
  status: "<ENTWURF / AKTIV / ARCHIV>"
  typ: "<How2 / Sprint / GOV / Prinzipien / Backlog>"
  datum: "<YYYY-MM-DD>"
  autor: EUMAXL
  tags: [rmuni, blueprint, s6]
  ---

Typen:
  How2          How2-Dokument (DEV oder USER)
  Sprint        Sprint-Dokumentation oder Backlog
  GOV           Governance-Dokument
  Prinzipien    Principles-Dokument einer Reihe
  Backlog       Sprint-DEV-BACKLOG


================================================================================
DOKUMENT-ABLAGE – ÜBERSICHT
================================================================================

  R+MUNI Doku-public\00-governance\           GOV-Dokumente        (public)
  R+MUNI Doku-public\01-principles\           Principles           (public)
  R+MUNI Doku-public\02-how2\                 How2-Dokumente       (public)
  R+MUNI Doku-public\03-rosetta_stone\        Rosetta Stone        (public)
  R+MUNI Doku-public\04-notes\                Notizen              (public)

  R+MUNI Doku-internal\backlog\               Backlog-Dokumente    (private)
  R+MUNI Doku-internal\sprints\               Sprint-Dokus aktiv   (private)
  R+MUNI Doku-internal\infocfg\               Informelles DEV      (private)

  R+MUNI Doku-creative\images\r+muni\diagrams\  Alle Diagramme SVG+PNG


================================================================================
GRAPH-VIEW NUTZEN
================================================================================

Graph-View öffnen:
  Obsidian → Strg+G (oder: Ansicht → Graph-Ansicht)

Was du siehst:
  Jeder Knoten = ein MD-Dokument im Blueprint
  Jede Linie   = ein [[Link]] zwischen zwei Dokumenten
  Zentrale Hubs = GOV, FREEZE – von allen anderen verlinkt

Nützliche Filter:
  tag:#sprint         nur Sprint-Dokumente
  path:02-how2        nur How2-Dokumente
  path:backlog        nur Backlog-Einträge

Was der Graph zeigt:
  Isolierte Knoten     → Dokument hat keine [[Links]] → nachpflegen
  Stark vernetzte Hubs → GOV und FREEZE sind korrekt zentral
  Sprint-Cluster       → Sprints hängen an ihren Backlog-Einträgen


================================================================================
FEHLERBILDER
================================================================================

Fehler: [[Link]] erscheint als roter Link
  Ursache: Dateiname stimmt nicht exakt oder Vault zeigt auf falschen Ordner
  Lösung:  Dateinamen im Explorer prüfen – exakt übernehmen
           Vault-Root prüfen: muss Parent aller R+MUNI Ordner sein

Fehler: SVG wird nicht angezeigt
  Ursache: Relativer Pfad stimmt nicht oder Datei liegt nicht am Ort
  Lösung:  Pfad prüfen – Leerzeichen in Ordnernamen sind erlaubt

Fehler: Frontmatter wird nicht erkannt
  Ursache: Sonderzeichen im Wert ohne Anführungszeichen
  Lösung:  Alle Werte mit Leerzeichen in "Anführungszeichen" setzen

Fehler: .obsidian/ landet in GitHub
  Ursache: .gitignore fehlt oder .obsidian/ nicht eingetragen
  Lösung:  .gitignore in jedem Repo prüfen – ".obsidian/" eintragen


================================================================================
ENTSCHEIDUNGSHILFE
================================================================================

Ich will...                                   Lösung
--------------------------------------------- --------------------------------
Neues Dokument anlegen                        DUMMY aus Doku-public\ kopieren
Diagramm aus Archi sichern                    SVG → Doku-creative\images\
                                              r+muni\diagrams\
Claude-Diagramm sichern                       SVG-Code → Notepad++ → .svg
                                              → diagrams\
Abhängigkeiten sehen                          Graph-View → Strg+G
Dokument schnell finden                       Strg+O
Neues Backlog-Dokument anlegen                Doku-internal\backlog\
Aktiven Sprint dokumentieren                  Doku-internal\sprints\


================================================================================
BEZÜGE
================================================================================

[[GOV_Global_S6]]                          normative Grundlage
[[FREEZE-6]]                               aktueller Ausgangszustand
[[STAGE6_ZIELE]]                           S6-Z4 Obsidian-Nutzung im Blueprint
[[DUMMY_Blueprint_MD_Obsidian_S6]]         MD-Vorlage für alle Dokumenttypen
[[Sprint-DEV-BACKLOG_Appliance-VM_S6]]     Beispiel vollständiges Backlog-Dokument


================================================================================
OBS_How2_DEV | S6 | 2026-03-19 | R+MUNI Blueprint
================================================================================
