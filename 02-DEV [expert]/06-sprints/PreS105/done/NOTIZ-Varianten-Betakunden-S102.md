# Notiz – Neue Varianten- und Betakunden-Struktur ab S102
> formlos | Orientierungsdokument | 2026-04-05

---

## Warum diese Notiz

Die Begriffe ASSOCIATE, ELITE und EXP wurden in S102 grundlegend überarbeitet.
Diese Notiz verhindert dass jeder neue Chat mit Begriffsklärung beginnt.
Gilt als vorübergehende Referenz bis naming_and_structure_S102.md
und AI_DRIVEN_DEV_METHODE_DEV_S102.md vollständig aktualisiert sind.

---

## Varianten-Modelle ab S102

| Kürzel | Name        | Was es ist                                                        |
|--------|-------------|-------------------------------------------------------------------|
| DEV    | Development | Intern — EUMAXL + Claude. Unverändert.                            |
| EXP    | Expert      | Kein eigenes Artefakt. Selbständiger Ableger aus DEV.             |
|        |             | Anleitung wie man ihn erstellt — EUMAXL baut ihn nicht aktiv.    |
| MUNI   | R+MUNI      | Ehemals ASSOCIATE. Außenwirkung, mit Begleitung.                  |
|        |             | Neues Kürzel, neuer Name. Born from MLAT + Kundenprojekt-Feedback.|
| CARD   | CARD        | Einstieg, selbstspielbar, ohne Begleitung.                        |

**ELITE entfällt vollständig.**
**EXP ist kein eigenes Produkt mehr — nur Ableger-Anleitung aus DEV.**
**MUNI ersetzt ASSOCIATE — Vollname und Dateinamen-Kürzel (`_MUNI_` statt `_ASC_`).**

---

## Betakunden — wer was nutzt

| Wer                   | Nutzt  | Seit       | Kontext                                    |
|-----------------------|--------|------------|--------------------------------------------|
| ASC                   | CARD   | laufend    | Vereins-Betakunde — Entwicklungsbasis CARD |
| FARM                  | CARD   | 2026-04-04 | Landwirtschaft + Biogas                    |
| MLAT + Kundenprojekte | R+MUNI | laufend    | Arbeit — Beta-Feedback MUNI                |
| EUMAXL                | DEV    | laufend    | Einziger DEV-Betauser                      |

**ASC-Content im Projektfolder:** bleibt unverändert und vollständig erhalten.
Freigabe für Public-Verwendung liegt vor. Kein Renaming, kein Bereinigen.

---

## Folder-Struktur IST-Stand — Doku-internal (00-internal)

```
00-internal\
  00-CARD [fun]\              ← CARD-Welt — Betakunden ASC + FARM
    00-General [gov]\         STG00–STG04 Session-Stack
    01-Exile [principles]\
    02-Stack [how2]\
    03-Hand [rosetta_stone]\  CON00–CON03 (IST/SOLL/WIE)
    04-Library [notes]\       TMP00, TMP01 Templates
    05-Graveyard [backlog]\   MTG-Altfiles — historisch, read-only
    06-Battlefield [sprint]\
    07-illustration [creative]\

  01-R+MUNI [normal]\         ← R+MUNI (MUNI) — ehem. ASSOCIATE
    00-governance\
    01-principles\            Inhalte noch mit ASSOCIATE-Naming (S8-Stand)
    02-how2\                  Inhalte noch mit ASSOCIATE-Naming (S8-Stand)
    03-rosetta_stone\
    04-notes\                 Normative Docs — naming_S102, AI_DRIVEN_S102
    05-backlog\
    06-sprints\               Sprint-Dokus S102 hier
    07-creative\

  02-DEV [expert]\            ← DEV-Welt intern — EUMAXL
    (gleiche Unterstruktur wie 01-R+MUNI)
    99-infocfg\

  99-CFG [info]\              Konfig-Dateien, Mappings
```

**Ordner-Klammern** = interne Beschreibung des Ordnerzwecks, nicht Teil des Namens.

---

## Folder-Struktur IST-Stand — R+MUNI Toolset (Vault)

```
R+MUNI\                       ← Hauptvault (Archi + Scripts + Doku)
  00-model\                   ArchiMate, BPMN, XY-Vision Modelle
  01-artifacts\
    00-xml\
    01-scripts\               Alle Python-Scripts (CLE, CSV, ECM, HLP, M2B, XML, ATL, FLW)
    02-csv\
    03-XLSX\
    04-flow\
    05-reports\
  02-stages\                  Archiv-Stände je Stage
  99-doku\                    Eingebettete Doku-Spiegelung (minimal: README + LICENSE)
```

---

## Public Repo IST-Stand

```
01-public\                    ← Aktuell bereinigt — fast leer
  README.md
  LICENSE
  .obsidian\
```

**Status:** Public Repo wurde bereinigt. Alte Inhalte entfernt.
Befüllung aus doku-internal steht noch aus — Teil des laufenden
Sprint-DEV-S102-Release-101.

---

## Was in den normativen Docs noch geändert werden muss

| Alter Begriff               | Neuer Begriff               | Betrifft                          |
|-----------------------------|-----------------------------|-----------------------------------|
| ASSOCIATE (Vollname)        | R+MUNI                      | naming, AI_DRIVEN, STAGE102_ZIELE |
| Associate (Variante)        | MUNI                        | naming, AI_DRIVEN, STAGE102_ZIELE |
| ELITE                       | — (entfällt)                | naming                            |
| EXP als eigenes Artefakt    | EXP = nur Ableger-Anleitung | naming, AI_DRIVEN                 |
| `_ASC_` (Dateinamen-Kürzel) | `_MUNI_`                    | naming (Dateinamen-Schema)        |

**Update-Reihenfolge:**
1. `naming_and_structure_S102.md`
2. `AI_DRIVEN_DEV_METHODE_DEV_S102.md`
3. `STAGE102_ZIELE_S102.md`
4. `Sprint-DEV-S102-Release-101.md`

**Nicht anfassen (historischer Stand):**
- `Sprint-DEV-S102-Naming-AIDriven.md`
- `Sprint-DEV-CARD-Reihe-Umbau_S102.md`
- Alle S8 und älter — Rückkopplungsschutz

---

## Dateinamen in doku-internal mit altem Naming — organisches Renaming

Folgende Files tragen noch ASSOCIATE/ASC im Namen.
Renaming beim nächsten Editieren — kein forciertes Bulk-Renaming.

**01-principles:** ASSOCIATE_principles_Template_S8, KI_principles_Associate_S8,
OBS_principles_Associate_S8 u.v.m. — alle S8-Stand.

**02-how2:** Associate_How2_S8, ASSOCIATE_How2_Template_S7,
ATL_FLOW_How2_Associate_S8 u.v.m. — alle S8-Stand.

**04-notes:** ASSOCIATE_Backlog_Template_S8, ASSOCIATE_Notes_Template_S8,
ASSOCIATE_principles_Template_S8, ASSOCIATE_Sprint_Template_S8 — alle S8-Stand.

Kein Handlungsbedarf solange diese Files nicht aktiv bearbeitet werden.

---

## Structure-Files

`Structure_R_MUNI.txt` und `Structure_DOKU.txt` wurden für diesen Chat
als Einmalreferenz bereitgestellt. Können nach Einarbeitung entfernt werden.

---

*formlose Notiz | Orientierung bis normative Docs aktualisiert | 2026-04-05*
*Erstellt: EUMAXL + Claude (Pair-Session)*
*Ersetzt durch: naming_and_structure_S102.md (wenn aktualisiert)*
