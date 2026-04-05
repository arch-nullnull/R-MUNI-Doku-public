# STG00 — Quickstart

#S102 #player/USER #zone/general

**Cost:** 0 | **Color:** Weiß | **Type:** Spell

---

<!-- SVG: ../07-illustration/STG/STG00-Quickstart_S102.svg -->

---

## Der Planeswalker spricht

Du hast dieses Dokument gefunden.
Das bedeutet entweder jemand hat es dir gegeben — oder du hast gesucht.
Beides ist ein guter Anfang.

Ich bin dein Planeswalker.
Ich kenne dieses Spielfeld. Ich werde dich hindurchführen.
Nicht weil ich muss — sondern weil ein gutes Spiel einen guten Einstieg verdient.

Was du mitbringst spielt keine Rolle.
Ein Verein der nicht mehr weiß wohin. Ein Buch das noch im Kopf steckt.
Eine Frage die seit Monaten keine Antwort hat.
Oder einfach die Neugier was hier passiert.

Alles davon ist Mana. Und Mana ist der Anfang von allem.

---

## Die Welt die du betrittst

Diese Welt heißt **R+MUNI**.
Sie ist kein Framework. Kein Kurs. Kein Regelwerk das du auswendig lernen musst.

Sie ist ein Spielfeld — und du bringst dein Thema mit.

Hier arbeiten Menschen mit einer KI zusammen um Dinge zu denken
die alleine schwerer zu denken wären.
Die KI strukturiert. Du entscheidest.
Immer. Ohne Ausnahme.

Das ist die einzige Regel die wirklich zählt.

---

## Das Spielfeld — deine Zonen

Das Spielfeld ist in Zonen aufgeteilt.
Jede Zone hat eine Aufgabe. Jede Zone hat ihren Moment.

Du musst sie nicht alle sofort verstehen.
Der Planeswalker zeigt sie dir — du lernst sie kennen während du spielst.

| Zone | Ordner | Was liegt dort |
|---|---|---|
| **General** | 00-General | Hier bist du gerade. Dein Einstieg. Dein Kompass. |
| **Library** | 01-Library | Dein Wissensspeicher. Prinzipien. Modelle. Was das System kann. |
| **Hand** | 02-Hand | Was du gerade hältst. Dein aktiver Kontext. |
| **Battlefield** | 03-Battlefield | Was läuft. Aktive Themen. Entscheidungen im Spiel. |
| **Graveyard** | 04-Graveyard | Was erledigt ist — aber nicht vergessen. Abrufbar wenn du es brauchst. |
| **Stack** | 05-Stack | Was gerade bearbeitet wird. Dein aktiver Sprint. |
| **Exile** | 06-Exile | Was abgeschlossen ist. Aus dem Spiel — aber nicht aus der Geschichte. |

Ein Tipp vom Planeswalker:
Fang nicht damit an alle Zonen zu befüllen.
Spiel zuerst. Die Struktur entsteht von selbst.

---

## Was eine Karte ist

Jedes Dokument in dieser Welt ist eine **Karte**.

Eine Karte ist nicht einfach eine Datei.
Sie ist ein Gedanke in Form gebracht — mit allem was die KI braucht
um ihn zu verstehen, und allem was du brauchst um ihn wiederzufinden.

Jede Karte folgt demselben Aufbau:

```
# Card Name

#S102 #player/USER #zone/<zone>

Cost: <mana> | Color: <farbe> | Type: <Spell | Creature | Artifact>

Situation  → Was war der Auslöser?
Action     → Was wurde getan?
Effect     → Was hat es bewirkt?
Insight    → Was bleibt als Erkenntnis?
Combo      → Mit welchen anderen Karten wirkt sie zusammen?

Damage: <Impact / Wirkung> | Life: <Wahrscheinlichkeit / Stabilität>
```

Was die Felder bedeuten:

| Feld | Bedeutung |
|---|---|
| **Cost / Mana** | Ressourcen — menschlich und/oder finanziell |
| **Color** | Themenfarbe — ein Thema pro Farbe, mehrere Themen = mehrfarbig |
| **Type** | Spell = einmalige Aktion / Creature = dauerhaft im Spiel |
| **Damage** | Impact — was bewirkt diese Karte? |
| **Life** | Stabilität — wie wahrscheinlich hält das? |

Das Template für neue Karten liegt als `TMP00-Template_card_S102.md` in der Library.

---

## Wie ein Zug aussieht

Ein Zug ist eine Session. Ein Gespräch mit der KI. Ein Schritt vorwärts.

Jeder Zug folgt derselben Logik:

```
Untap    → Kontext herstellen — was liegt auf dem Tisch?
Upkeep   → Was läuft noch aus dem letzten Zug?
Draw     → Was ziehst du heute — welche Frage, welches Thema?

Main     → Erzähl einfach. Kein Trigger, kein Format. Die KI hört zu.
Combat   → Trigger "du bist" — die KI gibt Struktur und Form.
End      → Output bestätigen. Karte landet in der richtigen Zone.
```

Vor jedem neuen Zug stellt der Planeswalker drei Fragen:

1. **Haben wir noch Bock?**
2. **Können wir uns das leisten?**
3. **Wer macht's?**

Alle drei ✅ → Karte spielen.
Eine ❌ → Karte bleibt auf der Hand. Kein Drama.

---

## Wie das Spiel gespielt wird

Du brauchst drei Dinge:

**1. Ein Thema.**
Irgendetwas das dich beschäftigt. Es muss nicht fertig gedacht sein.
Rohe Gedanken sind oft die besten Ausgangskarten.

**2. Eine KI.**
Claude, ChatGPT, Copilot — das Prinzip funktioniert mit allen.
Der Planeswalker empfiehlt Claude. Aber das ist seine persönliche Meinung.

**3. Den Session Start Prompt.**
Der liegt als `STG01-Prompt_session_S102.md` in diesem Ordner.
Kopiere ihn in einen neuen Chat. Warte auf **READY**.
Dann fang an zu erzählen.

Das war's. Wirklich.

---

## Ein Blick in eine andere Welt — was möglich ist

Irgendwo spielt gerade jemand dieses Spiel.

Ein kleiner Verein — zu wenig Mana, zu viele offene Fragen.
Wer trägt was? Was schläft bewusst? Was läuft von selbst?

Sie haben ihr Spielfeld aufgedeckt. Karten benannt. Züge durchgedacht.
Nicht weil jemand es verlangt hat — sondern weil es plötzlich sichtbar war.

Das ist was dieses System tut.
Es macht sichtbar was schon da ist.

Dein Spielfeld sieht anders aus. Dein Thema ist ein anderes.
Aber die Logik ist dieselbe.

---

## Was du nicht brauchst

Kein Vorwissen.
Kein Regelwerk auswendig gelernt.
Keine Vorbereitung.

Nur ein Thema — und die Bereitschaft loszulegen.

Der Planeswalker ist bereits auf dem Spielfeld.
Er wartet.

---

**Damage:** Orientierung im System | **Life:** Hoch — wer das gelesen hat kann sofort spielen
