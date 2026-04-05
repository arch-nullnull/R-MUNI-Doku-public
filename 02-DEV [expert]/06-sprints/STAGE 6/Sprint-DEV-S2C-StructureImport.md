# SPRINT DEFINITION — BACKLOG

---

| Feld               | Wert                                                        |
|--------------------|-------------------------------------------------------------|
| Projekt            | R+MUNI Blueprint                                           |
| Sprint-Bezeichnung | SPRINT-S2C-StructureImport                                 |
| Datum              | 2026-03-15 (Backlog-Eintrag)                               |
| Stage              | 5 (Aktiv)                                                  |
| Status             | BACKLOG — bewusst zurückgestellt                           |
| Erstellt durch     | EUMAXL + Claude (Pair-Session)                             |
| Priorität          | Mittel — Automatisierung eines funktionierenden manuellen Prozesses |

---

## 1. Ausgangslage und Problemstellung

### 1.1 Ursprünglicher Wunsch

Ziel war es, die Blueprint-Ordnerstruktur (`structure.txt`) als ArchiMate-Elemente
in ein bestehendes Archi 5.8 Modell zu importieren — um das OEF-Modell mit
realen Strukturnamen zu versorgen ohne manuellen Aufwand.

### 1.2 Erarbeitete Erkenntnisse (2026-03-15)

Im Zuge der Umsetzung von HLP08 und dem ersten vollständigen Testlauf
wurden folgende Erkenntnisse gewonnen:

**Erkenntnis 1 — Der Prozess funktioniert grundsätzlich**

Der ID-Merge-Run (beschrieben in `HLP08_How2_ID-Merge-Run.md`) funktioniert
vollständig über den bestehenden XML-Flow und CSV-Flow. Das Ziel ist erreichbar.

**Erkenntnis 2 — OEF Type ≠ Archi CSV Import Type**

Der ArchiMate OEF-Standard verwendet andere Type-Bezeichnungen als
Archi 5.8 beim CSV-Import. CSV09 überträgt den OEF-Type unverändert
in die Master CSVs — das ist korrekt und GOV-konform.
Archi 5.8 akzeptiert `TechnologyArtifact` jedoch beim direkten CSV-Import nicht.

| OEF xsi:type | Archi CSV Type | Status |
|---|---|---|
| `TechnologyArtifact` | `Artifact` | ⚠️ nur bei direktem CSV-Import relevant |
| `ArchimateModel` | — | ❌ kein gültiger Import-Type — überspringen |
| `Composition` | `CompositionRelationship` | ⚠️ bereits in CSV09 behandelt |

**Erkenntnis 3 — Append-only ist der kritische Punkt**

Der CSV-Flow ist Append-only. Ohne explizites Leeren des Master-Stacks
vor einem neuen S2C-Run entstehen Mehrfacheinträge im Archi-Modell.
HLP08 erzeugt bei jedem Lauf neue temporäre UUIDs — CSV99 kann
diese nicht als Duplikate erkennen.

**Erkenntnis 4 — CSV09 und XML-Reihe sind frozen**

Kein Eingriff in bestehende Reihen zulässig (GOV-Konformität).
Die Type-Normalisierung muss in einer eigenen isolierten Reihe erfolgen.

**Erkenntnis 5 — Zwei-Run-Prozess ist notwendig**

Run 1: Nur elements.csv → Archi vergibt stabile IDs → OEF Export
Run 2: Alle drei Files → stabile IDs vorhanden → vollständiger Import

Dieser Prozess ist manuell funktionsfähig (How2 dokumentiert) —
die S2C-Reihe automatisiert ihn vollständig.

### 1.3 Warum zurückgestellt

Der manuelle Prozess funktioniert und ist im How2 dokumentiert.
Die S2C-Reihe ist eine Automatisierung — kein Blocker.
Der Sprint wird gestartet wenn der Automatisierungsbedarf durch
wiederholte manuelle Ausführung bestätigt ist.

---

## 2. Zieldefinition

### 2.1 Gesamtziel

Eine vollständige, isolierte Script-Reihe `S2C` (Structure to CSV/Archi)
die den kompletten ID-Merge-Run-Prozess von `structure.txt` bis zum
stabilen Archi-Modell vollautomatisch abbildet — ohne Eingriff in
bestehende Reihen und ohne manuelle Zwischenschritte.

### 2.2 Teilziele

| # | Ziel | Akzeptanzkriterium |
|---|---|---|
| 1 | Master-Stack automatisch leeren vor Run | S2C00 erkennt Bedarf und leert sauber |
| 2 | OEF XML aus structure.txt erzeugen | S2C01 erzeugt valides OEF 3.1 XML |
| 3 | Type-Normalisierung OEF→Archi | S2C02 korrigiert Types transparent |
| 4 | Master CSVs befüllen | S2C03 analog CSV09, isoliert |
| 5 | Quality Gate | S2C98 analog CSV98 |
| 6 | Snapshot für Archi Import | S2C99 erzeugt saubere 04-import Files |
| 7 | Run-1/Run-2 Logik automatisch | S2C00 erkennt ob erster oder Folgelauf |
| 8 | Folgeläufe stabil ohne Duplikate | Kein manueller Eingriff nötig |

---

## 3. Erarbeitete Architektur — S2C Reihe

### 3.1 Naming

`S2C` = Structure to CSV/Archi
Ablageort: `01-artifacts\01-scripts\` (wie alle Script-Reihen)

### 3.2 Script-Reihe

```
S2C00-prepare_run.py         Master-Stack leeren + Run-Typ erkennen (Run1 vs Run2)
S2C01-structure2oef.py       structure.txt → valides OEF 3.1 XML
S2C02-oef_normalize.py       OEF XML → Archi-Import-konformes XML (Type-Mapping)
S2C03-oef2mastercsv.py       Normalisiertes XML → Master CSVs (analog CSV09, isoliert)
S2C98-quality_gate.py        Quality Gate (analog CSV98)
S2C99-export_snapshot.py     Snapshot für Archi CSV Import (analog CSV99)
```

Phase 2 (nach erstem stabilen Archi-Import):
```
S2C10-jarchi_export.py       jArchi Script: OEF Re-Export aus Archi nach Import
S2C11-id_stabilize.py        ID-Mapping: temp UUIDs → stabile Archi IDs persistieren
```

### 3.3 S2C00 — Kernlogik prepare_run

S2C00 ist das Herzstück der Reihe. Es erledigt was heute manuell gemacht wird:

```
1. Prüfen ob muni2import.xml in run-scope.txt aktiv ist
2. Master CSVs leeren (nur Header behalten)
3. master.xml löschen wenn vorhanden
4. Run-Typ bestimmen:
   - Run 1: kein OEF-Export aus Archi vorhanden → nur elements.csv
   - Run 2+: OEF-Export vorhanden → alle drei Files
5. run-scope.txt automatisch anpassen nach Run 1
```

### 3.4 Type-Mapping Tabelle (S2C02)

Vollständig erarbeitetes Mapping OEF→Archi CSV:

| OEF xsi:type | Archi CSV Type | Aktion |
|---|---|---|
| `TechnologyArtifact` | `Artifact` | ersetzen |
| `ArchimateModel` | — | Zeile überspringen |
| `Composition` | `CompositionRelationship` | ersetzen |
| `Aggregation` | `AggregationRelationship` | ersetzen |
| `Association` | `AssociationRelationship` | ersetzen |
| `Realization` | `RealizationRelationship` | ersetzen |
| `Serving` | `ServingRelationship` | ersetzen |
| `Assignment` | `AssignmentRelationship` | ersetzen |
| `Flow` | `FlowRelationship` | ersetzen |
| `Triggering` | `TriggeringRelationship` | ersetzen |
| `Specialization` | `SpecializationRelationship` | ersetzen |
| `Influence` | `InfluenceRelationship` | ersetzen |
| `Access` | `AccessRelationship` | ersetzen |

*Hinweis: Relationship-Suffix bereits in CSV09 behandelt —
in S2C02 explizit nochmals für vollständige Isolation.*

### 3.5 Vollständiger automatisierter Ablauf

```
S2C00  → Master-Stack leeren, Run-Typ erkennen
S2C01  → structure.txt → muni2import.xml (OEF 3.1)
S2C02  → muni2import.xml → muni2import_normalized.xml
S2C03  → normalized XML → Master CSVs
S2C98  → Quality Gate
S2C99  → Snapshot → 04-import/

--- Archi manuell: CSV Import (Run1: elements only / Run2: alle) ---
--- Archi manuell: OEF Export nach Run1 ---

S2C00  → erkennt Run2, passt run-scope.txt an
... (Folgeläufe vollautomatisch)
```

### 3.6 Abgrenzung zum bestehenden How2

Der manuelle Prozess (`HLP08_How2_ID-Merge-Run.md`) bleibt gültig
und ist die Referenz für den S2C-Sprint. S2C automatisiert
exakt diesen Prozess — Schritt für Schritt, ohne Abweichung.

---

## 4. Abgrenzung

| In Scope | Out of Scope |
|---|---|
| Neue S2C-Reihe (vollständig isoliert) | Änderungen an CSV-Reihe |
| Type-Normalisierung OEF→Archi | Änderungen an XML-Reihe |
| Automatisierter ID-Merge-Run | Änderungen an HLP-Reihe |
| Master-Stack Guard (S2C00) | Änderungen an bestehenden Scripts |
| ID-Stabilisierung Phase 2 | GOV-Änderungen |
| jArchi Re-Export Phase 2 | Archi-interner Import (bleibt manuell) |

**HLP08 bleibt als Vorläufer erhalten** — S2C01 ist der saubere Nachfolger.
HLP08 wird nach erfolgreichem S2C-Sprint als deprecated markiert.

---

## 5. Technische Schulden die dieser Sprint adressiert

| TD | Beschreibung | Entstanden |
|---|---|---|
| TD-S2C-01 | OEF Type ≠ Archi CSV Type — kein automatisches Mapping | 2026-03-15 |
| TD-S2C-02 | Kein automatisierter Bootstrapping-Pfad | 2026-03-15 |
| TD-S2C-03 | ID-Stabilisierung nach erstem Import manuell | 2026-03-15 |
| TD-S2C-04 | Master-Stack muss manuell geleert werden vor S2C-Run | 2026-03-15 |
| TD-S2C-05 | XML07 ohne Konsolen-Output (Kosmetik) | 2026-03-15 |
| TD-S2C-06 | datetime.utcnow() DeprecationWarning XML05/XML06 | 2026-03-15 |

*TD-S2C-05 und TD-S2C-06 sind Kosmetik — gehören in Kosmetik-Run,
nicht zwingend in S2C-Sprint.*

---

## 6. Offene Entscheidungen

| # | Entscheidung | Optionen | Status |
|---|---|---|---|
| E-01 | Run1/Run2 Erkennung in S2C00 | OEF-Export vorhanden vs. Flag-File | Offen |
| E-02 | run-scope.txt Anpassung automatisch? | S2C00 schreibt vs. manuell bleibt | Offen |
| E-03 | HLP08 deprecated oder entfernen nach Sprint? | Deprecated markieren vs. löschen | Offen |
| E-04 | Phase 2 im selben Sprint oder eigener Sprint? | Ein Sprint vs. zwei Sprints | Offen |
| E-05 | Archi Import bleibt manuell oder via jArchi? | Manuell (Phase 1) vs. jArchi (Phase 2) | Phase 2 |

---

## 7. Voraussetzungen für Sprint-Start

- [x] Freeze 5.5 abgeschlossen
- [x] HLP08 als Vorläufer vorhanden und getestet
- [x] ID-Merge-Run manuell erfolgreich durchgeführt
- [x] How2 ID-Merge-Run dokumentiert (`HLP08_How2_ID-Merge-Run.md`)
- [x] Type-Mapping Tabelle vollständig erarbeitet
- [x] Bootstrapping-Prozess definiert und validiert
- [ ] Neues Claude-Projekt für Stage 5.7 angelegt
- [ ] Entscheidungen E-01 und E-02 getroffen vor Sprint-Start

---

## 8. Governance-Vorprüfung

| GOV-Ref   | Kriterium                     | Bewertung |
|-----------|-------------------------------|-----------|
| GOV 10.3  | Zulässiger Auslöser           | ✅ Automatisierung eines bestehenden manuellen Prozesses |
| GOV 10.5  | Fachlicher Mehrwert           | ✅ Vollautomatischer Bootstrapping-Prozess |
| GOV 10.5  | Keine implizite Gov-Änderung  | ✅ Neue isolierte Reihe, kein Eingriff |
| GOV 10.6  | Ziel explizit definiert       | ✅ Abschnitt 2 |
| GOV 10.6  | Ziel überprüfbar              | ✅ Kein manueller Eingriff nötig außer Archi-Import |
| GOV 10.10 | Keine Gov-Regel aufgehoben    | ✅ Additiv, keine bestehende Logik verändert |
| Stage 5   | Rückkopplungsschutz           | ✅ Stage-3/4-Scripts vollständig unberührt |

---

## 9. Referenzdokumente

| Dokument | Inhalt |
|---|---|
| `HLP08_How2_ID-Merge-Run.md` | Manueller Referenzprozess den S2C automatisiert |
| `Sprint-DEV-Doku-HLP08-structure2xml.md` | Technische Grundlage, Testergebnisse |
| `SPRINT-5-5-FREEZE.md` | Baseline auf der S2C aufbaut |

---

*SPRINT-DEF-S2C-StructureImport | Stage 5 | Backlog | 2026-03-15*
*Erstellt durch: EUMAXL + Claude (Pair-Session)*
