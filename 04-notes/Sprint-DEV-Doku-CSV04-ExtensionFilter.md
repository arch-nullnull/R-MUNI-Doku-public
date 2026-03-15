# SPRINT DEV-DOKUMENTATION

---

| Feld               | Wert                                              |
|--------------------|---------------------------------------------------|
| Projekt            | R+MUNI Blueprint                                 |
| Sprint-Bezeichnung | SPRINT-CSV04-ExtensionFilter                     |
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

**Auslöser-Typ:** Bugfix

**Begründung:**  
Beim ersten vollständigen CSV-Run mit zwei Archi-Modellen wurde festgestellt, dass `run-scope.txt` nach CSV04 unerwünschte Einträge enthielt. Archi erzeugt im Modell-Ordner neben den eigentlichen `.archimate` Dateien auch interne Hilfsdateien:

- `.archimate.bak` — Archi Backup-Dateien
- `log-0.txt` — Archi internes Log
- `log-0.txt.lck` — Archi Lock-Datei

Im OEF-Ordner lagen zusätzlich Archi Schema-Dateien die nicht Teil des Flows sind:

- `archimate3_Diagram.xsd`
- `archimate3_Model.xsd`
- `archimate3_View.xsd`

Alle diese Dateien landeten als gültige `SOURCE=archi` bzw. `SOURCE=OEF` Einträge in `run-scope.txt` und wurden von nachgelagerten Scripts verarbeitet.

**Fachlicher Mehrwert:**  
`run-scope.txt` enthält nach dem Fix ausschließlich fachlich relevante Einträge. Archi-interne Hilfsdateien und Schema-Dateien werden zuverlässig ausgefiltert — ohne manuelle Nachbearbeitung der `run-scope.txt`.

**Governance-Konformität:**  
Reiner Bugfix in CSV04. Keine Änderung an Logik oder Struktur der nachgelagerten Scripts. Keine Breaking Change — saubere `run-scope.txt` war immer das Ziel.

---

## 2. Zieldefinition (gemäß GOV 10.6)

**Ziel:**  
`CSV04-model-overview.py` liest und schreibt ausschließlich fachlich relevante Dateieinträge in `run-scope.txt`:

- `SOURCE=archi` → nur `.archimate` Dateien
- `SOURCE=OEF` → nur `.xml` Dateien
- `SOURCE=XLSX` → nur `.xlsx` Dateien
- `SOURCE=CSV` → nur `.csv` Dateien

**Abgrenzung:**  
Kein Eingriff in CSV01, CSV03 oder nachgelagerte Scripts. Ausschließlich CSV04 wird angepasst. Die Filterlogik ist in CSV04 zentral und vollständig — kein anderes Script muss nachfiltern.

**Überprüfbar:**  
Erfolgreich wenn `run-scope.txt` nach vollständigem Run (CSV00–CSV04) keine `.bak`, `.txt`, `.lck` oder `.xsd` Einträge mehr enthält.

---

## 3. Ist-Zustand — Problemanalyse

### 3.1 Fehlerquelle: read_scope_models() — kein Source-Filter

CSV04 las alle `MODEL=` Zeilen aus der bestehenden `run-scope.txt` ohne Prüfung der zugehörigen `SOURCE=` Zeile:

```python
# ALT — blind alle MODEL= Zeilen lesen
def read_scope_models(scope_path):
    models = []
    for line in f:
        if line.startswith("MODEL="):
            models.append(line.strip().split("=", 1)[1])
    return models
```

Ergebnis: Wenn eine `run-scope.txt` bereits `.bak` oder `log-0.txt` Einträge enthielt, wurden diese von CSV04 übernommen und weitergeschrieben.

### 3.2 Fehlerquelle: list_files() — kein Extension-Filter

CSV04 scannte die Child-Ordner ohne Extension-Filter:

```python
# ALT — alle Dateien im Ordner
def list_files(directory):
    return sorted(f for f in os.listdir(directory)
                  if os.path.isfile(os.path.join(directory, f)))
```

Ergebnis OEF-Ordner: `.xsd` Archi-Schema-Dateien wurden als `SOURCE=OEF` Einträge aufgenommen.

### 3.3 Konkrete Fundstellen im IST-Zustand

```
# run-scope.txt IST (fehlerhaft):
SOURCE=archi
MODEL=00-archimateactive/MUNI FLOW.archimate.bak   ← Backup

SOURCE=archi
MODEL=00-archimateactive/log-0.txt                 ← Archi internes Log

SOURCE=archi
MODEL=00-archimateactive/log-0.txt.lck             ← Archi Lock-Datei

SOURCE=OEF
MODEL=archimate3_Diagram.xsd                       ← Schema-Datei
SOURCE=OEF
MODEL=archimate3_Model.xsd                         ← Schema-Datei
SOURCE=OEF
MODEL=archimate3_View.xsd                          ← Schema-Datei
```

---

## 4. Lösung — Technische Umsetzung

### 4.1 Fix read_scope_models() — kontextbewusstes Lesen

```python
# NEU — SOURCE/MODEL Paare kontextbewusst lesen
def read_scope_models(scope_path):
    models = []
    current_source = None
    for line in f:
        if line.startswith("SOURCE="):
            current_source = line.split("=", 1)[1].strip().lower()
        elif line.startswith("MODEL="):
            model = line.split("=", 1)[1].strip()
            if current_source == "archi":
                if model.lower().endswith(".archimate"):
                    models.append(model)
    return models
```

Gefiltert werden: `.bak`, `log-0.txt`, `log-0.txt.lck` und alle anderen Nicht-Archimate-Dateien.

### 4.2 Fix list_files() — Extension-Filter pro Source-Typ

```python
# NEU — Extension-Filter Parameter
def list_files(directory, extensions=()):
    for f in sorted(os.listdir(directory)):
        if extensions and not f.lower().endswith(extensions):
            continue
        result.append(f)
```

Anwendung pro Source-Typ:

| Source | Extension-Filter | Gefiltert |
|---|---|---|
| OEF | `.xml` | `.xsd` Schema-Dateien |
| XLSX | `.xlsx` | alle anderen Dateitypen |
| CSV | `.csv` | alle anderen Dateitypen |

### 4.3 Erwartetes Ergebnis nach Fix

```
# run-scope.txt SOLL (sauber):
SOURCE=archi
MODEL=MUNI EA.archimate

SOURCE=archi
MODEL=MUNI FLOW.archimate

SOURCE=OEF
MODEL=MUNI EA.xml

SOURCE=OEF
MODEL=MUNI FLOW.xml

SOURCE=XLSX
MODEL=MUNI EA.xlsx

SOURCE=XLSX
MODEL=MUNI FLOW.xlsx

SOURCE=CSV
MODEL=MUNI EAelements.csv
...
```

---

## 5. Konfiguration nach Fix

Keine Konfigurationsänderung erforderlich. Der Fix ist vollständig in CSV04 gekapselt.

**Testlauf:**
```powershell
py .\CSV00-validate_environment.py
py .\CSV01-validate_model.py
py .\CSV03-resolve_run_scope.py
py .\CSV04-model-overview.py
```

---

## 6. Testergebnis

Testlauf 2026-03-13:

| Prüfpunkt | Ergebnis |
|---|---|
| `.bak` in run-scope.txt | nicht vorhanden ✓ |
| `log-0.txt` in run-scope.txt | nicht vorhanden ✓ |
| `.xsd` in run-scope.txt | nicht vorhanden ✓ |
| Archi-Modelle korrekt erkannt | MUNI EA.archimate, MUNI FLOW.archimate ✓ |
| OEF korrekt erkannt | MUNI EA.xml, MUNI FLOW.xml ✓ |

Status: **OK — Testlauf 2026-03-13 erfolgreich**

---

## 7. Offene Punkte / Next Steps

### 7.1 FLW-Scripts auf Stage 5 Struktur anpassen

| | |
|---|---|
| Status | Offen — bewusst zurückgestellt |
| Aktion | FLW00/01/02 auf neue Ordnerstruktur und root.cfg anpassen wenn FLW-Sprint startet |

### 7.2 Stage-Ende Dokumentation

| | |
|---|---|
| Status | Ausstehend (gemäß GOV 10.9 verpflichtend zum Stage-Ende) |
| Aktion | Diese Dev-Dokumentation ist nicht auditpflichtig (GOV 10.8). Zum Stage-Ende ist eine vollständige governance-konforme Dokumentation zu erstellen. |

---

## 8. Governance-Konformitätscheck

| GOV-Ref | Kriterium | Status | Bemerkung |
|---|---|---|---|
| GOV 10.3 | Zulässiger Auslöser | ✓ OK | Bugfix, Entwicklerfreigabe |
| GOV 10.5 | Fachlicher Mehrwert | ✓ OK | Saubere run-scope.txt ohne manuelle Nachbearbeitung |
| GOV 10.5 | Keine implizite Gov-Änderung | ✓ OK | Additiver Filter, keine Logikänderung |
| GOV 10.6 | Ziel explizit definiert | ✓ OK | Abschnitt 2 |
| GOV 10.6 | Ziel überprüfbar | ✓ OK | run-scope.txt Inhalt direkt prüfbar |
| GOV 10.7 | Zwischenschritte | ✓ OK | Normativ zugelassen |
| GOV 10.8 | Dev-Doku erstellt | ✓ OK | Dieses Dokument |
| GOV 10.9 | Stage-Ende Doku | ⏳ OFFEN | Verpflichtend bei Stage-Abschluss |
| GOV 10.10 | Keine Gov-Regel aufgehoben | ✓ OK | Keine Architekturänderung |
| Stage 5 | Entwicklerfreigabe | ✓ OK | Explizite Freigabe durch EUMAXL |

---

*END OF SPRINT DEV-DOKUMENTATION*  
*SPRINT-CSV04-ExtensionFilter | Stage 5 | 2026-03-13*
