# SPRINT DEV-DOKUMENTATION

---

| Feld               | Wert                                                        |
|--------------------|-------------------------------------------------------------|
| Projekt            | R+MUNI Blueprint                                            |
| Sprint-Bezeichnung | SPRINT-CLE-Reihe                                            |
| Datum              | 2026-03-15                                                  |
| Stage              | 5 (Aktiv)                                                   |
| Status             | Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)       |
| Erstellt durch     | EUMAXL + Claude (Pair-Session)                              |

---

## 1. Stage-Kontext und Sprint-Begründung

### 1.1 Stage-Modell (Ist-Zustand)

| Stage   | Status | Relevanz                        |
|---------|--------|---------------------------------|
| Stage 4 | FREEZE | Abgeschlossen 2026-03-09        |
| Stage 5 | AKTIV  | Dieser Sprint läuft in Stage 5  |

### 1.2 Auslöser (gemäß GOV 10.3 / 10.5)

**Auslöser-Typ:** Feature-Zuwachs / Infrastruktur

**Begründung:**  
Mit dem Aufbau der BPMN-Reihe (und weiterer zukünftiger Flow-Reihen) entsteht der Bedarf nach einem dedizierten, konsistenten Cleaning-Mechanismus für alle Artifact-Ordner. Bisher war das Leeren von Ordnern entweder manuell (Windows Explorer) oder über HLP03 als generischen Helfer möglich — aber ohne reihenspezifische, direkt aufrufbare Scripts.

Die CLE-Reihe schließt diese Lücke und schafft die Voraussetzung dafür, dass die BPMN-Reihe (und alle weiteren Flow-Reihen) sauber starten kann: mit leeren Ziel-Ordnern, reproduzierbar und ohne manuelle Eingriffe.

**Fachlicher Mehrwert:**  
- Jeder Artifact-Ordner hat ein dediziertes, direkt aufrufbares CLE-Script
- Kombinierte Scripts (z.B. CLE11 für alle XML-Child-Ordner) reduzieren den manuellen Aufwand
- Vollständige Log-Aufzeichnung für alle Cleaning-Aktionen
- Basis für den Scriptrunner (FLW-Reihe): CLE-Scripts können in Flows eingebunden werden
- Unabhängig von Modell-Typ (ArchiMate / BPMN) — universell einsetzbar

**Governance-Konformität:**  
Vollständig neue Script-Reihe (CLE-Präfix). Keine Änderung an bestehenden Scripts. Keine Eingriffe in Flow-Logik (CSV, XML, XLSX). Additiv und rückwärtskompatibel.

---

## 2. Zieldefinition (gemäß GOV 10.6)

**Ziel:**  
Die CLE-Reihe stellt für jeden relevanten Artifact- und Stages-Ordner ein dediziertes Python-Script bereit, das den Ordnerinhalt zuverlässig löscht (Ordner selbst bleibt erhalten), den Vorgang vollständig protokolliert und sowohl standalone als auch über den Scriptrunner (FLW) aufrufbar ist.

**Abgrenzung:**  
- Kein Eingriff in Ordnerstrukturen (kein `mkdir`, kein `rmdir`)
- Kein Eingriff in Modell-Dateien unter `00-model`
- Kein Eingriff in Script-Ordner (`01-artifacts\01-scripts`)
- Kein Eingriff in Konfigurations-Dateien (`root.cfg`, Mapping-Files)
- Ausschließlich Inhalt der definierten Ziel-Ordner wird gelöscht

**Überprüfbar:**  
Erfolgreich wenn nach Ausführung:
- Ziel-Ordner leer ist (Ordner selbst vorhanden)
- Log-Eintrag in `02-stages\99-logs\CLE<Nr>-<name>.log` vorhanden
- Konsolen-Ausgabe zeigt `[OK] ... bereinigt` für jeden Ziel-Ordner

---

## 3. Script-Übersicht und Ziel-Ordner

### 3.1 Architektur-Entscheidung

Die CLE-Reihe folgt dem etablierten Baukasten-Prinzip:
- **1 Script = 1 Outcome**
- **Kombinierte Scripts** für häufige Komplett-Cleanups (CLE11, CLE21, CLE31 etc.)
- **Einzelne Scripts** für gezielten Einsatz in Flows oder manuell
- **Inline root.cfg Auflösung** — keine Abhängigkeit zu CLE00 zur Laufzeit, jedes Script ist autark

Basis-Script CLE00 dient ausschließlich der Diagnose und schreibt ein Referenz-Log für die gesamte Reihe.

### 3.2 Nummern-Schema

| Gruppe          | Präfix  | Basis-Pfad-Variable | Bereich                        |
|-----------------|---------|---------------------|--------------------------------|
| Basis           | CLE00   | —                   | Root-Diagnose                  |
| XML             | CLE1x   | `<artifacts>`       | `01-artifacts\00-xml`          |
| CSV             | CLE2x   | `<artifacts>`       | `01-artifacts\02-csv`          |
| CSV Spezialfall | CLE26   | `<artifacts>`       | `01-artifacts\02-csv\04-import` — gezieltes Datei-Löschen |
| XLSX            | CLE3x   | `<artifacts>`       | `01-artifacts\03-XLSX`         |
| Reports         | CLE4x   | `<artifacts>`       | `01-artifacts\05-reports`      |
| Stages          | CLE5x   | `<stages>`          | `02-stages`                    |

### 3.3 Vollständige Script-Liste

#### CLE00 — Basis

| Script                  | Zweck                                       | Ziel-Ordner |
|-------------------------|---------------------------------------------|-------------|
| `CLE00-resolve_root.py` | Root-Auflösung, Diagnose, Referenz-Log      | — (kein Cleaning) |

#### CLE10–CLE15 — XML-Gruppe

| Script                      | Ziel-Ordner (relativ zu `<artifacts>`)                                           |
|-----------------------------|---------------------------------------------------------------------------------|
| `CLE10-xml_master.py`       | `00-xml\00-master`                                                              |
| `CLE11-xml_all_childs.py`   | `00-xml\03-child\00-archimatechild` + `00-xml\03-child\01-bpmnchild`           |
| `CLE12-xml_archimate_child.py` | `00-xml\03-child\00-archimatechild`                                          |
| `CLE13-xml_bpmn_child.py`   | `00-xml\03-child\01-bpmnchild`                                                  |
| `CLE14-xml_import.py`       | `00-xml\04-import`                                                              |
| `CLE15-xml_export.py`       | `00-xml\99-exports`                                                             |

#### CLE20–CLE26 — CSV-Gruppe

| Script                        | Ziel (relativ zu `<artifacts>`)                                                        | Modus          |
|-------------------------------|----------------------------------------------------------------------------------------|----------------|
| `CLE20-csv_master.py`         | `02-csv\00-master`                                                                     | Ordner-Clean   |
| `CLE21-csv_all_childs.py`     | `02-csv\03-child\00-archimatechild` + `02-csv\03-child\01-bpmnchild`                | Ordner-Clean   |
| `CLE22-csv_archimate_child.py`| `02-csv\03-child\00-archimatechild`                                                   | Ordner-Clean   |
| `CLE23-csv_bpmn_child.py`     | `02-csv\03-child\01-bpmnchild`                                                        | Ordner-Clean   |
| `CLE24-csv_import.py`         | `02-csv\04-import`                                                                     | Ordner-Clean   |
| `CLE25-csv_export.py`         | `02-csv\99-exports`                                                                    | Ordner-Clean   |
| `CLE26-csv_no_id.py`          | `02-csv\04-import\properties.csv` + `02-csv\04-import\relations.csv`               | **Datei-Delete** |

> **CLE26 Spezialfall:** Löscht gezielt nur `properties.csv` und `relations.csv` im Import-Ordner.
> `elements.csv` bleibt bewusst erhalten. Anwendungsfall: Integration von Archi-ID-losen Objekten
> in den Archi-OEF-XML-CSV-Archi Flow. Siehe Abschnitt 4.7.

#### CLE30–CLE35 — XLSX-Gruppe

| Script                         | Ziel-Ordner (relativ zu `<artifacts>`)                                        |
|--------------------------------|-------------------------------------------------------------------------------|
| `CLE30-xlsx_master.py`         | `03-XLSX\00-master`                                                           |
| `CLE31-xlsx_all_childs.py`     | `03-XLSX\03-child\00-archimatechild` + `03-XLSX\03-child\01-bpmnchild`       |
| `CLE32-xlsx_archimate_child.py`| `03-XLSX\03-child\00-archimatechild`                                          |
| `CLE33-xlsx_bpmn_child.py`     | `03-XLSX\03-child\01-bpmnchild`                                               |
| `CLE34-xlsx_import.py`         | `03-XLSX\04-import`                                                           |
| `CLE35-xlsx_export.py`         | `03-XLSX\99-exports`                                                          |

#### CLE40–CLE43 — Reports-Gruppe

| Script                     | Ziel-Ordner (relativ zu `<artifacts>`)                                           |
|----------------------------|---------------------------------------------------------------------------------|
| `CLE40-reports_all.py`     | `05-reports\00-archimate` + `05-reports\01-bpmn` + `05-reports\99-html`        |
| `CLE41-reports_archimate.py` | `05-reports\00-archimate`                                                     |
| `CLE42-reports_bpmn.py`    | `05-reports\01-bpmn`                                                            |
| `CLE43-reports_html.py`    | `05-reports\99-html`                                                            |

#### CLE50–CLE53 — Stages-Gruppe

| Script                     | Ziel-Ordner (relativ zu `<stages>`)                                                          |
|----------------------------|---------------------------------------------------------------------------------------------|
| `CLE50-stages_all.py`      | `00-archimatearchive` + `01-bpmnarchive` + `99-logs`                                        |
| `CLE51-stages_archimate.py`| `00-archimatearchive`                                                                        |
| `CLE52-stages_bpmn.py`     | `01-bpmnarchive`                                                                             |
| `CLE53-stages_logs.py`     | `99-logs`                                                                                    |

---

## 4. Technische Umsetzung

### 4.1 Referenz-Scripts

| Referenz            | Verwendung in CLE                                  |
|---------------------|----------------------------------------------------|
| `HLP00_resolve_root.py` | Muster für root.cfg-Auflösung (inline übernommen) |
| `HLP03_clean.py`    | Muster für clean_folder-Logik                      |

### 4.2 Inline root.cfg Auflösung

Jedes CLE-Script (CLE10–CLE53) löst `root.cfg` **inline** auf — ohne Import von CLE00 oder HLP00. Dies macht jedes Script vollständig autark und in beliebiger Reihenfolge ausführbar.

```python
def _resolve_root() -> dict:
    script_dir = os.path.dirname(os.path.abspath(__file__))
    cfg_path   = os.path.abspath(os.path.join(script_dir, "..", "..", "root.cfg"))
    # ... parsen und auflösen
```

**Pfad-Logik:** Script liegt in `<rootfolder>\01-artifacts\01-scripts\` → zwei Ebenen hoch = `<rootfolder>` → dort liegt `root.cfg`.

### 4.3 clean_folder Funktion

Kernlogik identisch zu HLP03, aber mit integriertem Logging-Mechanismus (kein separater LOG_FILE am ROOT):

```python
def clean_folder(folder: str, log_path: str | None = None) -> None:
    # Prüft ob Ordner vorhanden → [SKIP] wenn nicht
    # Löscht Dateien:      os.remove()      → [DEL-F]
    # Löscht Unterordner:  shutil.rmtree()  → [DEL-D]
    # Fehler werden        geloggt          → [FEHLER]
    # Abschluss-Zeile:                      → [OK] X Datei(en), Y Unterordner
```

Ordner die nicht existieren werden mit `[SKIP]` übersprungen — kein Abbruch. Dies ist bewusst so gewählt damit Scripts in Flows sicher ausgeführt werden können, auch wenn einzelne Ziel-Ordner noch nicht befüllt wurden.

### 4.4 Log-Ablage

Alle CLE-Logs landen in:
```
<rootfolder>\02-stages\99-logs\CLE<Nr>-<name>.log
```

Log-Format (eine Zeile pro Ereignis):
```
[CLE10] 2026-03-15 10:23:45 | ===...===  Start CLE10
[CLE10] 2026-03-15 10:23:45 | Ziel-Ordner : C:\Prototyping\R+MUNI\01-artifacts\00-xml\00-master
[CLE10] 2026-03-15 10:23:45 |   [DEL-F]  ...elements.xml
[CLE10] 2026-03-15 10:23:45 | [OK]  ... bereinigt — 3 Datei(en), 0 Unterordner gelöscht, 0 Fehler.
[CLE10] 2026-03-15 10:23:45 | ===...===  Ende CLE10
```

### 4.5 Basispfad-Unterschied CLE4x vs. CLE5x

Ein wichtiger Unterschied in der Basispfad-Variable:

| Gruppe  | cfg-Variable   | Aufgelöster Pfad                          |
|---------|----------------|-------------------------------------------|
| CLE1x–CLE4x | `<artifacts>` | `<rootfolder>\01-artifacts`          |
| CLE5x   | `<stages>`     | `<rootfolder>\02-stages`                  |

CLE5x Scripts verwenden `cfg.get("<stages>", "")` — **nicht** `<artifacts>`. Die Ziel-Ordner sind damit direkt relativ zum Stages-Verzeichnis (z.B. `00-archimatearchive` ohne den `02-stages`-Prefix).

### 4.6 Hinweis CLE53 — Stages Logs

`CLE53-stages_logs.py` löscht den Inhalt von `02-stages\99-logs` — also auch alle bestehenden CLE-Logs. Das ist gewollt (Clean Slate vor neuem Run). Konsequenz: Nach Ausführung von CLE53 ist kein vorheriger Log mehr vorhanden. CLE53 selbst schreibt **kein** neues Log (da das Log-Ziel gerade geleert wurde). Nur die Konsolen-Ausgabe bleibt sichtbar.

### 4.7 CLE26 — Spezialfall Datei-Delete

**Anwendungsfall:** Wenn Archi-ID-lose Objekte (Elemente ohne Identifier) neu in den
Archi-OEF-XML-CSV-Archi Flow integriert werden sollen, dürfen `properties.csv` und
`relations.csv` im Import-Ordner nicht vorhanden sein — nur `elements.csv` mit den
neuen Objekten wird benötigt. CLE26 löscht gezielt nur diese zwei Dateien.

**Abgrenzung zu CLE24:**

| | CLE24 | CLE26 |
|---|---|---|
| Modus | Ordner-Clean | Datei-Delete |
| Löscht | gesamten Inhalt von `04-import` | nur `properties.csv` + `relations.csv` |
| Erhält | Ordner selbst | alle anderen Dateien inkl. `elements.csv` |
| Anwendung | Standard-Reset vor neuem CSV-Run | ID-loser Objekte-Import |

**Kern-Logik:** `delete_file()` statt `clean_folder()` — arbeitet auf Datei-Ebene:

```python
ZIEL_DATEIEN = [
    os.path.join("02-csv", "04-import", "properties.csv"),
    os.path.join("02-csv", "04-import", "relations.csv"),
]

def delete_file(filepath, log_path):
    # Datei nicht vorhanden → [SKIP]  (kein Abbruch)
    # Datei vorhanden       → os.remove() → [DEL-F]
    # Fehler                → [FEHLER]
```

Log-Format CLE26 (Unterschied zu Standard: `Ziel-Datei` statt `Ziel-Ordner`):
```
[CLE26] 2026-03-15 10:30:00 | =====  Start CLE26
[CLE26] 2026-03-15 10:30:00 | Modus: Gezieltes Datei-Löschen (kein Ordner-Clean)
[CLE26] 2026-03-15 10:30:00 | Ziel-Datei  : ...\04-import\properties.csv
[CLE26] 2026-03-15 10:30:00 |   [DEL-F]  ...\04-import\properties.csv
[CLE26] 2026-03-15 10:30:00 | Ziel-Datei  : ...\04-import\relations.csv
[CLE26] 2026-03-15 10:30:00 |   [DEL-F]  ...\04-import\relations.csv
[CLE26] 2026-03-15 10:30:00 | [OK]  Abgeschlossen — 2 Datei(en) gelöscht, 0 nicht vorhanden.
[CLE26] 2026-03-15 10:30:00 | =====  Ende CLE26
```

---

## 5. Ablage und Ausführung

### 5.1 Ablageort

Alle CLE-Scripts gehören nach:
```
<rootfolder>\01-artifacts\01-scripts\
```

### 5.2 Ausführung (PowerShell)

```powershell
# Einzelnes Script
py .\CLE10-xml_master.py

# Diagnose / Referenz-Log
py .\CLE00-resolve_root.py

# Typischer Einsatz vor einem neuen XML-Run
py .\CLE10-xml_master.py
py .\CLE11-xml_all_childs.py

# Kompletter Reset aller CSV-Ordner
py .\CLE20-csv_master.py
py .\CLE21-csv_all_childs.py
py .\CLE24-csv_import.py
py .\CLE25-csv_export.py

# Spezialfall: ID-lose Objekte in den Flow integrieren
# (elements.csv mit neuen Objekten liegt bereits in 04-import)
py .\CLE26-csv_no_id.py
# → nur properties.csv + relations.csv gelöscht, elements.csv bleibt erhalten
```

### 5.3 Einbindung in Scriptrunner (FLW)

CLE-Scripts sind für die Einbindung in `flowmapping.txt` vorbereitet. Beispiel für einen zukünftigen BPMN-Flow-Prolog:

```
# BPMN Flow — Cleaning Step
CLE13-xml_bpmn_child.py
CLE23-csv_bpmn_child.py
CLE33-xlsx_bpmn_child.py
# ... weiterer Flow
```

Die Einbindung in `flowmapping.txt` erfolgt in einem separaten Sprint wenn die BPMN-Reihe vollständig aufgebaut ist.

---

## 6. Testergebnis

Testlauf 2026-03-15 (Live-System EUMAXL):

| Script-Gruppe | Getestete Scripts | Ergebnis          |
|---------------|-------------------|-------------------|
| CLE00         | CLE00             | ✓ OK              |
| CLE1x         | CLE10–CLE15       | ✓ OK — alle Ordner korrekt geleert |
| CLE2x         | CLE20–CLE25       | ✓ OK — alle Ordner korrekt geleert |
| CLE26         | CLE26             | ✓ OK — properties.csv + relations.csv gelöscht, elements.csv erhalten |
| CLE3x         | CLE30–CLE35       | ✓ OK — alle Ordner korrekt geleert |
| CLE4x         | CLE40–CLE43       | ✓ OK — alle Ordner korrekt geleert |
| CLE5x         | CLE50–CLE53       | ✓ OK — alle Ordner korrekt geleert |

**Syntax-Prüfung:** Alle 20 Scripts — `python3 -m py_compile` → 20x OK, 0 Fehler.

**Besonderheit im Test:** Nicht vorhandene Ziel-Ordner wurden korrekt mit `[SKIP]` übersprungen — kein Abbruch, kein Fehler.

---

## 7. Offene Punkte / Next Steps

### 7.1 BPMN-Reihe aufbauen

| | |
|---|---|
| Status | Nächster Sprint — direkte Folge dieses Sprints |
| Aktion | BPMN Flow-Scripts aufbauen; CLE13, CLE23, CLE33, CLE42, CLE52 als Cleaning-Prolog verwenden |

### 7.2 Einbindung in flowmapping.txt

| | |
|---|---|
| Status | Offen — abhängig von FLW-Reihe Stage 5 Bereinigung |
| Aktion | CLE-Scripts in flowmapping.txt aufnehmen wenn BPMN-Flow-Reihe fertig |

### 7.3 Erweiterung für neue Artifact-Typen

| | |
|---|---|
| Status | Laufend — bei Bedarf |
| Aktion | Wenn neue Artifact-Ordner (z.B. CLE6x) hinzukommen: Schema beibehalten, structure.txt aktualisieren |

### 7.4 Stage-Ende Dokumentation

| | |
|---|---|
| Status | Ausstehend (gemäß GOV 10.9 verpflichtend zum Stage-Ende) |
| Aktion | Diese Dev-Dokumentation ist nicht auditpflichtig (GOV 10.8). Zum Stage-Ende ist eine vollständige governance-konforme Dokumentation zu erstellen. |

---

## 8. Governance-Konformitätscheck

| GOV-Ref  | Kriterium                        | Status   | Bemerkung                                              |
|----------|----------------------------------|----------|--------------------------------------------------------|
| GOV 10.3 | Zulässiger Auslöser              | ✓ OK     | Feature-Zuwachs, Infrastruktur, Entwicklerfreigabe     |
| GOV 10.5 | Fachlicher Mehrwert              | ✓ OK     | Voraussetzung für BPMN-Reihe, universell einsetzbar    |
| GOV 10.5 | Keine implizite Gov-Änderung     | ✓ OK     | Vollständig neue Reihe, kein Eingriff in bestehende Scripts |
| GOV 10.6 | Ziel explizit definiert          | ✓ OK     | Abschnitt 2                                            |
| GOV 10.6 | Ziel überprüfbar                 | ✓ OK     | Leere Ordner + Log-Ausgabe [OK]                        |
| GOV 10.7 | Zwischenschritte                 | ✓ OK     | Normativ zugelassen                                    |
| GOV 10.8 | Dev-Doku erstellt                | ✓ OK     | Dieses Dokument                                        |
| GOV 10.9 | Stage-Ende Doku                  | ⏳ OFFEN | Verpflichtend bei Stage-Abschluss                      |
| GOV 10.10| Keine Gov-Regel aufgehoben       | ✓ OK     | Keine Architekturänderung                              |
| Stage 5  | Entwicklerfreigabe               | ✓ OK     | Explizite Freigabe durch EUMAXL                        |

---

*END OF SPRINT DEV-DOKUMENTATION*  
*SPRINT-CLE-Reihe (inkl. CLE26 Spezialfall) | Stage 5 | 2026-03-15*
