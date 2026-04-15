================================================================================
OBSIDIAN – Obsidian als DEV-Werkzeug im Blueprint – HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : OBSIDIAN_How2_DEV_S105
Tag             : #dev #how2 #obsidian #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-19
Letzte Änderung : 2026-04-14 — S105-Update | Umbenennung OBS → OBSIDIAN | SVG-Pfad korrigiert | Template-Tagging ergänzt
Ablageort       : R+MUNI Doku-public\02-how2\OBSIDIAN_How2_DEV_S105.md
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[Global_GOV_DEV_S102]] gelesen – Obsidian ist Lesewerkzeug + Navigationshilfe,
  keine neue Logikschicht, kein Eingriff in Blueprint-Dateistruktur
- [[OBSIDIAN_principles_DEV_S105]] gelesen
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

Hinweis Kürzel:
  Diese Reihe trägt das Kürzel OBSIDIAN_ — nicht OBS_.
  OBS ist im R+MUNI-Betriebskontext für OBS Studio reserviert.


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
    [[Global_GOV_DEV_S102]]      – normative Grundlage
    [[FREEZE_1_04]]              – aktueller Ausgangszustand

Bezüge-Block am Ende jedes Dokuments (Pflicht):
  [[Global_GOV_DEV_S102]]                    normative Grundlage
  [[FREEZE_1_04]]                            aktueller Ausgangszustand
  [[<verwandtes Dokument>]]                  <warum relevant>

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
  99-doku\07-creative\03-svg\

Namenskonvention:
  <reihe>_<beschreibung>_S<stage>.svg          SVG aus Archi-Export
  <reihe>_<beschreibung>_claude_S<stage>.svg   SVG von Claude generiert
  <reihe>_<beschreibung>_S<stage>.png          PNG Fallback

Einbettung im MD-Dokument (relativer Pfad aus Doku-public\02-how2\):
  ![Beschreibung](../../R+MUNI/99-doku/07-creative/03-svg/<datei>.svg)

Archi SVG-Export:
  Archi → View auswählen → Datei → Exportieren → Bild exportieren
  → Format: SVG
  → speichern in 99-doku\07-creative\03-svg\

Claude SVG speichern:
  SVG-Code aus Claude-Antwort kopieren
  → Notepad++ → neue Datei → einfügen → speichern als .svg
  → ablegen in 99-doku\07-creative\03-svg\

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
  stage: S105
  status: "<ENTWURF / AKTIV / ARCHIV>"
  typ: "<How2 / Sprint / GOV / Prinzipien / Backlog / Template>"
  datum: "<YYYY-MM-DD>"
  autor: EUMAXL
  tags: [rmuni, blueprint, s105]
  ---

Typen:
  How2          How2-Dokument (DEV oder MUNI)
  Sprint        Sprint-Dokumentation
  GOV           Governance-Dokument
  Prinzipien    Principles-Dokument einer Reihe
  Backlog       Sprint-DEV-BACKLOG
  Template      Template-Dokument — alle *_Template_* Dateien


── TEMPLATE-TAGGING ─────────────────────────────────────────────────────────────

Template-Dokumente brauchen einen eigenen Tag damit sie im Graph-View
gezielt gefiltert werden können.

Pflicht für alle *_Template_* Dateien:
  typ: "Template"
  tags: [..., template]

Beispiel vollständiges Frontmatter für ein Template:
  ---
  title: "CSV Flow How2 Template"
  stage: S105
  status: "AKTIV"
  typ: "Template"
  datum: "2026-04-14"
  autor: EUMAXL
  tags: [rmuni, blueprint, s105, template]
  ---

Graph-View Filter:
  tag:#template        → alle Template-Dokumente
  tag:#sprint          → nur Sprint-Dokumente
  path:02-how2         → nur How2-Dokumente
  path:01-principles   → nur Principles-Dokumente


── OPTIONALES REIHEN-FELD ───────────────────────────────────────────────────────

Für Reihen-spezifische Filterung ohne Pfad-Abhängigkeit:
  reihe: <kürzel>

Beispiel:
  reihe: csv    → alle CSV-Dokumente (How2, Principles, Sprint) auf einen Blick

Nicht Pflicht — einsetzen wo Reihen-Überblick im Graph-View sinnvoll ist.


================================================================================
DOKUMENT-ABLAGE – ÜBERSICHT (DEV-SICHT)
================================================================================

  R+MUNI Doku-public\00-governance\           GOV-Dokumente        (public)
  R+MUNI Doku-public\01-principles\           Principles           (public)
  R+MUNI Doku-public\02-how2\                 How2-Dokumente       (public)
  R+MUNI Doku-public\03-rosetta_stone\        Rosetta Stone        (public)
  R+MUNI Doku-public\04-notes\                Notizen              (public)
  R+MUNI Doku-public\98-templates\            Templates            (public)

  R+MUNI Doku-internal\backlog\               Backlog-Dokumente    (private)
  R+MUNI Doku-internal\sprints\               Sprint-Dokus aktiv   (private)
  R+MUNI Doku-internal\infocfg\               Informelles DEV      (private)

  99-doku\07-creative\03-svg\                 SVG-Diagramme        (public, GitHub)


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
  tag:#template       nur Template-Dokumente
  tag:#sprint         nur Sprint-Dokumente
  path:02-how2        nur How2-Dokumente
  path:01-principles  nur Principles-Dokumente
  path:backlog        nur Backlog-Einträge

Was der Graph zeigt:
  Isolierte Knoten     → Dokument hat keine [[Links]] → nachpflegen
  Stark vernetzte Hubs → GOV und FREEZE sind korrekt zentral
  Sprint-Cluster       → Sprints hängen an ihren Backlog-Einträgen
  Template-Cluster     → tag:#template zeigt alle Templates gebündelt


================================================================================
FEHLERBILDER
================================================================================

Fehler: [[Link]] erscheint als roter Link
  Ursache: Dateiname stimmt nicht exakt oder Vault zeigt auf falschen Ordner
  Lösung:  Dateinamen im Explorer prüfen – exakt übernehmen
           Vault-Root prüfen: muss Parent aller R+MUNI Ordner sein

Fehler: SVG wird nicht angezeigt
  Ursache: Relativer Pfad stimmt nicht oder Datei liegt nicht am Ort
  Lösung:  Ablageort prüfen: 99-doku\07-creative\03-svg\
           Leerzeichen in Ordnernamen sind erlaubt

Fehler: Frontmatter wird nicht erkannt
  Ursache: Sonderzeichen im Wert ohne Anführungszeichen
  Lösung:  Alle Werte mit Leerzeichen in "Anführungszeichen" setzen

Fehler: .obsidian/ landet in GitHub
  Ursache: .gitignore fehlt oder .obsidian/ nicht eingetragen
  Lösung:  .gitignore in jedem Repo prüfen – ".obsidian/" eintragen

Fehler: OBS_* Links erscheinen rot nach Umbenennung
  Ursache: Alte [[OBS_*]] Links noch nicht auf [[OBSIDIAN_*]] aktualisiert
  Lösung:  Cleaning Run — alle OBS_* Links auf OBSIDIAN_* nachziehen
           Referenz: [[DEV_Sprint_OBS-RENAME-TAGGING_S105]]


================================================================================
ENTSCHEIDUNGSHILFE
================================================================================

Ich will...                                   Lösung
--------------------------------------------- --------------------------------
Neues Dokument anlegen                        Template aus 98-templates\ kopieren
                                              → [[TMP_How2_DEV_S105]]
Diagramm aus Archi sichern                    SVG → 99-doku\07-creative\03-svg\
Claude-Diagramm sichern                       SVG-Code → Notepad++ → .svg
                                              → 99-doku\07-creative\03-svg\
Abhängigkeiten sehen                          Graph-View → Strg+G
Dokument schnell finden                       Strg+O
Alle Templates sehen                          Graph-View → Filter: tag:#template
Alle Dokumente einer Reihe sehen              Graph-View → Filter: reihe:<kürzel>
Neues Backlog-Dokument anlegen                Doku-internal\backlog\
Aktiven Sprint dokumentieren                  Doku-internal\sprints\


================================================================================
BEZÜGE
================================================================================

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[FREEZE_1_04]]                            aktueller Ausgangszustand
[[STAGE105_ZIELE_S105]]                    Z5 — Cleaning Run, Carry-over
[[OBSIDIAN_principles_DEV_S105]]           Grundprinzipien dieser Reihe
[[TMP_principles_S105]]                    Dokumenttypen-Referenz
[[TMP_How2_DEV_S105]]                      Template-Nutzung
[[naming_and_structure_S104]]              Namenskonventionen und Tiering
[[DEV_Sprint_OBS-RENAME-TAGGING_S105]]     Sprint-Doku Umbenennung + Tagging


================================================================================
OBSIDIAN_How2_DEV | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
