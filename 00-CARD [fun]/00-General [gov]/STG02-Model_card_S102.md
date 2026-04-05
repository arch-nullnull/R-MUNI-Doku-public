# STG02 — Model_card

#S102 #player/USER #zone/library

**Cost:** 0 | **Color:** Weiß | **Type:** Spell

---

## Grundidee

Innerhalb des R+MUNI-Systems existiert eine eigene Arbeitswelt.
Sie orientiert sich an der Logik eines Kartenspiels — nicht als Regelwerk,
sondern als **Denkmodell und Arbeitslinse**.

Das Modell hilft dabei Projekte, Ressourcen und Entscheidungen
verständlich und spielerisch zu strukturieren.

---

## Zentrale Begriffe

| Begriff | Bedeutung im Projektkontext |
|---|---|
| **Deck** | Aktueller Projektzustand — alles was dazu gehört |
| **Karte** | Ein Dokument, eine Entscheidung, ein Vorhaben |
| **Zug** | Konkrete Maßnahme oder Session |
| **Hand** | Aktuelle Optionen — was gerade zur Verfügung steht |
| **Mana** | Ressourcen — menschlich und/oder finanziell |
| **Land** | Wer oder was Mana liefert — Personen, Budgets, Infrastruktur |
| **Combo** | Wenn mehrere Karten zusammenspielen und mehr bewirken als einzeln |
| **Schlummer** | Karten die existieren aber bewusst nicht gespielt werden |
| **Color** | Themenfarbe — ein Thema pro Farbe, mehrere Themen = mehrfarbig |

---

## Karten-Typen

| Type | Bedeutung |
|---|---|
| **Land** | Personen / Supporter — liefern Mana |
| **Creature** | Lokation — Keller, Halle, Grundstück etc. |
| **Artifact** | Ressource — frei einsetzbar, standalone oder in Abhängigkeit |
| **Instant** | Einmalige Aktion — Bewerb, Event |
| **Enchantment** | Dauerhafte Aktion — Training, Mähen, laufende Aktivitäten |

Weitere Typen entstehen wenn die Komplexität es verlangt.

---

## Saison-Prinzip

Die Entwicklung läuft in Saisonen — kurz **Stage**.

Ein Stage beschreibt eine Entwicklungsperiode und dient der Orientierung
welche Phase des Decks gerade aktiv ist.

Technisch über einen minimalen Marker:

```
#S102
```

Der Marker erscheint im Header jeder Karte.
Er ersetzt kein komplexes Statussystem — er gibt Orientierung.

---

## Prinzip der Minimalität

Das Modell folgt bewusst einem minimalen Strukturprinzip.

Karten enthalten nur so viel Metadaten wie notwendig damit:
- Orientierung möglich bleibt
- Werkzeuge funktionieren
- der Arbeitsfluss nicht gestört wird

Die eigentliche Komplexität entsteht nicht in der Dokumentstruktur
sondern in der **inhaltlichen Arbeit am Deck**.

---

**Damage:** Gemeinsames Verständnis der Arbeitswelt | **Life:** Hoch — Basis für alle weiteren Karten
