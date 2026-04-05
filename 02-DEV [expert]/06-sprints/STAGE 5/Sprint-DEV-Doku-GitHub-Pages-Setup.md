# GitHub Pages – DEV Sprint Doku Setup

Diese Anleitung beschreibt, wie DEV‑Sprint‑Dokumentationen aus einem
GitHub Repository als GitHub Page veröffentlicht werden.

Ziel:
- DEV‑Sprints nach abgeschlossenen Fixes öffentlich anzeigen
- Keine CMS‑Logik, keine Publish‑Buttons
- Sichtbarkeit ausschließlich über Ordnerstruktur steuern

---

## 1. Grundprinzip

GitHub Pages rendert einen definierten Ordner eines Repositories
als statische Website.

- Ordner = Website
- Markdown-Dateien = Seiten
- index.md = Startseite

Alles außerhalb dieses Ordners ist nicht sichtbar.

---

## 2. Öffentlichen Ordner anlegen

Im Repository einen öffentlichen Ordner anlegen, z. B. public

Empfohlene Struktur:

public
  index.md
  sprint-5-5-cleaningrun.md
  sprint-csv98-cleanmaster.md
  sprint-xml-reihe-fix.md

Hinweis:
- Nur Dateien in diesem Ordner erscheinen auf der GitHub Page
- Interne oder unfertige Inhalte bleiben außerhalb

---

## 3. index.md als Anker erstellen

Die Datei index.md im öffentlichen Ordner dient als Startseite der Page.

Beispielinhalt:

# R+MUNI – DEV Sprint Dokumentation

Hier werden ausgewählte DEV‑Sprint‑Dokumentationen veröffentlicht,
nachdem Fixes abgeschlossen und getestet wurden.

Alle Inhalte sind Entwicklungsstände.
Kein Produktversprechen, keine Stabilitätsgarantie.

---

## 4. GitHub Pages aktivieren

1. Repository auf GitHub öffnen
2. Settings → Pages
3. Source konfigurieren:
   - Branch: main
   - Folder: public
4. Einstellungen speichern

Nach kurzer Zeit ist die Page unter der GitHub‑Pages‑URL erreichbar.

---

## 5. Veröffentlichung von DEV‑Sprints

Workflow:

1. DEV‑Sprint abgeschlossen und getestet
2. Sprint‑Doku als .md Datei erstellen
3. Datei in den öffentlichen Ordner verschieben
4. Commit und Push

Ergebnis:
- Die Seite aktualisiert sich automatisch
- Keine weitere Aktion notwendig

---

## 6. Sichtbarkeit steuern

- Datei im öffentlichen Ordner → öffentlich sichtbar
- Datei außerhalb → nicht sichtbar

Es gibt:
- keine Publish‑Buttons
- keine Auswahl im UI
- keine implizite Veröffentlichung

Sichtbarkeit erfolgt ausschließlich über Ablage.

---

## 7. Wichtige Hinweise

- GitHub Pages ist immer öffentlich
- Der Branch main ist der aktuelle gültige Stand des Repos
- GitHub Pages liest ausschließlich aus dem konfigurierten Ordner
- Markdown wird automatisch gerendert

---

## 8. Zielbild

- Transparente DEV‑Sprints
- Nachvollziehbarer Entwicklungsstand
- Klare Trennung zwischen intern und öffentlich
- Kein Tool‑Lock‑in, kein CMS

Der Ordner ist die Wahrheit.
[[SPRINT-5-5-FREEZE]]