# SPRINT DEV-DOKUMENTATION

---

| Feld               | Wert                                              |
|--------------------|---------------------------------------------------|
| Projekt            | R+MUNI Blueprint                                 |
| Sprint-Bezeichnung | SPRINT-CSV98-CleanMaster                         |
| Datum              | 2026-03-13                                        |
| Stage              | 5 (Aktiv)                                        |
| Status             | Dev-Dokumentation (nicht auditpflichtig per GOV 10.8) |
| Erstellt durch     | EUMAXL + Claude (Pair-Session)                   |

---

## 1. Stage-Kontext und Sprint-Begründung

### 1.1 Stage-Modell (Ist-Zustand)

| Stage | Status | Relevanz |
|-------|--------|----------|
| Stage 4 | FREEZE | Abgeschlossen 2026-03-09 |
| Stage 5 | AKTIV  | Dieser Sprint läuft in Stage 5 |

### 1.2 Auslöser (gemäß GOV 10.3 / 10.5)

**Auslöser-Typ:** Bugfix + Quality Gate

**Begründung:**  
Beim ersten vollständigen CSV-Run mit zwei Archi-Modellen (MUNI EA + MUNI FLOW) wurde festgestellt, dass Archi 5.x beim CSV-Export bestimmte Elementnamen fehlerhaft escaped. Betroffen sind Namen die mit `00-` beginnen — Archi behandelt diese als Excel-Formel und schreibt sie als `="00-archimatechild"` statt `00-archimatechild`.

Zusätzlich wurde festgestellt, dass Copy-Paste aus externen Quellen (Word, OneNote) den Backtick-Accent `` ´ `` einschleust statt des korrekten Apostrophs `'`.

Beide Probleme landen unbereinigt in den Master CSVs und damit in jedem nachgelagerten Export und 3rd-Party-System.

**Fachlicher Mehrwert:**  
Ein dedizierter Cleaner (CSV98) stellt sicher, dass die Master CSVs als saubere Datenbasis für alle nachgelagerten Flows und Exporte dienen. Bekannte Qualitätsprobleme werden zentral und idempotent bereinigt — erweiterbar für weitere Problemklassen.

**Governance-Konformität:**  
Additiver neuer Script-Slot CSV98. Keine Änderung an bestehenden Scripts. Kein Eingriff in Append-Logik (CSV06) oder Export-Logik (CSV99).

---

## 2. Zieldefinition (gemäß GOV 10.6)

**Ziel:**  
`CSV98-clean_master.py` prüft die drei Master CSVs (`elements.csv`, `relations.csv`, `properties.csv`) auf bekannte Qualitätsprobleme, bereinigt diese direkt in den Dateien und erstellt einen lesbaren Report mit allen Fundstellen und durchgeführten Fixes.

**Abgrenzung:**  
Kein Eingriff in CSV-Struktur, Header oder Reihenfolge. Ausschließlich Feldwerte werden bereinigt. Master-Dateien werden direkt überschrieben — kein Backup, da Git als Versionskontrolle aktiv ist.

**Überprüfbar:**  
Erfolgreich wenn nach Ausführung:
- `CSV98-clean_master_report.txt` vorhanden ist
- Kein `="..."` mehr in `elements.csv` vorkommt
- Log zeigt `[CSV98] OK | X Fixes`

---

## 3. Ist-Zustand — Problemanalyse

### 3.1 FIX-01 — Formula-Prefix (Archi Export Problem)

Archi 5.x exportiert Elementnamen die mit `00-` beginnen mit Excel-Formel-Escaping:

```
Archi Export (fehlerhaft):   ="00-archimatechild"
Erwarteter Wert:              00-archimatechild
```

Betroffen: `elements.csv` — Feld `Name`  
Umfang im ersten Testlauf: **48 Treffer** in `MUNI_FLOWelements.csv`  
Ursache: Archi-internes CSV-Quoting behandelt `=` am Feldanfang als Formel-Marker.

### 3.2 FIX-02 — Backtick/Accent ´ (Copy-Paste Problem)

Copy-Paste aus Word, OneNote oder anderen Office-Quellen schleust den typografischen Akzent `` ´ `` ein statt des Standard-Apostrophs `'`:

```
Fehlerhaft:  "Library´s"
Korrekt:     "Library's"
```

Betroffen: alle drei Master CSVs — Feld `Documentation` und `Name`  
Ursache: Zeichensatz-Unterschied zwischen Office-Applikationen und UTF-8 CSV.

---

## 4. Lösung — Technische Umsetzung

### 4.1 Script-Slot CSV98

Einordnung in den CSV-Flow:

```
CSV05  →  CSV06  →  CSV98  →  CSV99
(Master    (Append   (Clean    (Export
 anlegen)   child)    master)   snapshot)
```

CSV98 sitzt nach dem Append (CSV06) und vor dem Export (CSV99) — das ist der einzig sinnvolle Zeitpunkt: nach dem Einlesen aller Quelldaten, vor der Weitergabe an 3rd-Party-Systeme.

### 4.2 Fix-Regeln Architektur

Fix-Regeln sind als Liste von Tupeln implementiert — erweiterbar ohne Logikänderung:

```python
FIX_RULES = [
    ("FIX-01", "Beschreibung", check_fn, fix_fn),
    ("FIX-02", "Beschreibung", check_fn, fix_fn),
    # weitere Regeln einfach anhängen
]
```

Jede Regel besteht aus: ID, Beschreibung, Prüffunktion, Fix-Funktion.  
Anwendung: auf jeden Feldwert jeder Zeile aller drei Master CSVs.

### 4.3 FIX-01 Implementierung

```python
check_fn: re.match(r'^=".*"$', value)
fix_fn:   re.sub(r'^="(.*)"$', r'\1', value)
```

Beispiele:
- `="00-archimatechild"` → `00-archimatechild` ✓
- `="00-archimate"` → `00-archimate` ✓
- `Normaler Name` → unverändert ✓

### 4.4 FIX-02 Implementierung

```python
check_fn: "´" in value
fix_fn:   value.replace("´", "'")
```

### 4.5 Report

Lesbarer Report in `02-stages\99-logs\CSV98-clean_master_report.txt`:
- Pro Datei: Anzahl Fixes
- Pro Fix-Regel: Zeile, Feld, Vorher, Nachher
- Gesamtzahl aller Fixes

---

## 5. Konfiguration nach Fix

Keine Konfigurationsänderung erforderlich.  
CSV98 liest Root via `CSV00-root.resolved.txt` — Standard-Mechanismus.

**Ausführung:**
```powershell
py .\CSV98-clean_master.py
```

**Position im manuellen Flow:**
```powershell
py .\CSV06-append_child_to_master.py
py .\CSV98-clean_master.py
py .\CSV99-export_snapshot.py
```

---

## 6. Testergebnis

Testlauf 2026-03-13 (auf Basis der hochgeladenen `elements.csv`):

| Datei | Geprüfte Zeilen | FIX-01 Treffer | FIX-02 Treffer |
|---|---|---|---|
| elements.csv | 328 | 48 | 1 |
| relations.csv | — | — | — |
| properties.csv | — | — | — |

Befund bestätigt: 48 Formula-Prefix Treffer ausschließlich aus MUNI FLOW Modell.  
Status: **Script erstellt — Testlauf auf Live-System ausstehend**

---

## 7. Offene Punkte / Next Steps

### 7.1 Live-Testlauf CSV98

| | |
|---|---|
| Status | Offen |
| Aktion | CSV98 auf Live-System ausführen, Report prüfen, Archi-Reimport validieren |

### 7.2 Weitere Fix-Regeln

| | |
|---|---|
| Status | Laufend — wird bei Bedarf erweitert |
| Aktion | Neue Problemklassen aus dem Betrieb sammeln und als FIX-NN in CSV98 einpflegen |

### 7.3 FLW-Scripts (CSV98 in Scriptrunner)

| | |
|---|---|
| Status | Offen — FLW-Reihe noch nicht auf Stage 5 Struktur angepasst |
| Aktion | CSV98 in flowmapping.txt aufnehmen wenn FLW-Scripts bereinigt sind |

### 7.4 Stage-Ende Dokumentation

| | |
|---|---|
| Status | Ausstehend (gemäß GOV 10.9 verpflichtend zum Stage-Ende) |
| Aktion | Diese Dev-Dokumentation ist nicht auditpflichtig (GOV 10.8). Zum Stage-Ende ist eine vollständige governance-konforme Dokumentation zu erstellen. |

---

## 8. Governance-Konformitätscheck

| GOV-Ref | Kriterium | Status | Bemerkung |
|---|---|---|---|
| GOV 10.3 | Zulässiger Auslöser | ✓ OK | Bugfix + Quality Gate, Entwicklerfreigabe |
| GOV 10.5 | Fachlicher Mehrwert | ✓ OK | Saubere Master CSVs für alle nachgelagerten Flows |
| GOV 10.5 | Keine implizite Gov-Änderung | ✓ OK | Additiv, kein Eingriff in bestehende Scripts |
| GOV 10.6 | Ziel explizit definiert | ✓ OK | Abschnitt 2 |
| GOV 10.6 | Ziel überprüfbar | ✓ OK | Report + Log-Ausgabe |
| GOV 10.7 | Zwischenschritte | ✓ OK | Normativ zugelassen |
| GOV 10.8 | Dev-Doku erstellt | ✓ OK | Dieses Dokument |
| GOV 10.9 | Stage-Ende Doku | ⏳ OFFEN | Verpflichtend bei Stage-Abschluss |
| GOV 10.10 | Keine Gov-Regel aufgehoben | ✓ OK | Keine Architekturänderung |
| Stage 5 | Entwicklerfreigabe | ✓ OK | Explizite Freigabe durch EUMAXL |

---

*END OF SPRINT DEV-DOKUMENTATION*  
*SPRINT-CSV98-CleanMaster | Stage 5 | 2026-03-13*
