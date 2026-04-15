# BPMN 2.0 — NBX-Flow
## Beschreibung zum Nachbauen in Camunda Modeler

```
Dokument  : BPMN_NBX-Flow_DEV_S105
Typ       : BPMN Beschreibung
Stage     : S1.05
Werkzeug  : Camunda Modeler (BPMN 2.0)
Basis     : NBX00–NBX05 Scripts
```

---

## 1. Überblick

Der NBX-Flow erfasst eine lokale Netzwerkumgebung via nmap-Scan und
produziert `trash_nbx.csv` als normiertes Output-Artefakt für den
nachgelagerten ECM-Flow.

**Ein Pool, ein Lane-Set, sequenzieller Ablauf mit Fehler-Exits.**

---

## 2. Pool & Lanes

**Pool-Name:** `NBX-Flow`

**Lanes (von oben nach unten):**

| Lane | Bedeutung |
|------|-----------|
| `EUMAXL` | Manuelle Schritte — Trigger, Konfiguration, Entscheid |
| `NBX-Scripts` | Automatisierte Script-Ausführung |
| `Filesystem` | Artefakte die entstehen oder gelesen werden |

---

## 3. Elemente im Detail

### 3.1 Start-Event

| Feld | Wert |
|------|------|
| Typ | **Start Event** (einfach, kein Trigger) |
| Name | `NBX-Flow starten` |
| Lane | EUMAXL |
| Beschreibung | Manueller Auslöser durch EUMAXL — bewusste Entscheidung, kein Zeitplan |

---

### 3.2 Task: NBX00 — Umgebung validieren

| Feld | Wert |
|------|------|
| Typ | **Script Task** |
| Name | `NBX00 — Umgebung validieren` |
| Lane | NBX-Scripts |
| Script | `NBX00-validate_environment.py` |
| Prüft | root.cfg, HLP00, 99-logs, nbx_config.txt, 00-archimatechild |
| Output | `NBX00-root.resolved.txt` → 99-logs |

**Boundary Event (Error) auf NBX00:**
- Typ: **Error Boundary Event**
- Name: `Pfad / Ordner fehlt`
- Verbindet zu: End Event `Fehler — Umgebung nicht bereit`

---

### 3.3 Task: NBX01 — Konfiguration validieren

| Feld | Wert |
|------|------|
| Typ | **Script Task** |
| Name | `NBX01 — Konfiguration validieren` |
| Lane | NBX-Scripts |
| Script | `NBX01-validate_config.py` |
| Liest | `nbx_config.txt` (ip_range, scan_ports, output_label) |
| Prüft | Pflichtfelder, CIDR-Syntax, Hostanzahl |
| Output | `NBX01-validate_config.log` → 99-logs |

**Boundary Event (Error) auf NBX01:**
- Typ: **Error Boundary Event**
- Name: `Konfiguration ungültig`
- Verbindet zu: End Event `Fehler — Konfiguration prüfen`

**Gateway nach NBX01:**
- Typ: **Exclusive Gateway**
- Name: `Mehr als 254 Hosts?`
- Ja-Pfad → **User Task** `Warnung bestätigen` (Lane: EUMAXL) → weiter zu NBX02
- Nein-Pfad → direkt weiter zu NBX02

---

### 3.4 Task: NBX02 — Netzwerk scannen

| Feld | Wert |
|------|------|
| Typ | **Script Task** |
| Name | `NBX02 — Netzwerk scannen` |
| Lane | NBX-Scripts |
| Script | `NBX02-scan_network.py` |
| Phase 1 | Ping-Sweep — alle aktiven Hosts finden |
| Phase 2 | Port-Scan mit Service-Detection (-sV) |
| Output | `nbx_raw.json` → 02-stages/00-archimatearchive |
| Hinweis | Laufzeit bis 5 Minuten — kein Timeout-Fehler erwartet |

**Boundary Event (Error) auf NBX02:**
- Typ: **Error Boundary Event**
- Name: `nmap nicht verfügbar / Scan-Fehler`
- Verbindet zu: End Event `Fehler — nmap prüfen`

**Gateway nach NBX02:**
- Typ: **Exclusive Gateway**
- Name: `Hosts gefunden?`
- Nein-Pfad → **User Task** `Warnung: keine Hosts — ip_range prüfen` (Lane: EUMAXL)
  - Nach Bestätigung → End Event `Abbruch — kein Scan-Ergebnis`
- Ja-Pfad → weiter zu NBX03

---

### 3.5 Task: NBX03 — Normieren und CSV schreiben

| Feld | Wert |
|------|------|
| Typ | **Script Task** |
| Name | `NBX03 — Normieren und CSV schreiben` |
| Lane | NBX-Scripts |
| Script | `NBX03-normalize_to_csv.py` |
| Liest | `nbx_raw.json` |
| Erzeugt | Hosts (nbx_objecttype: host) und Services (nbx_objecttype: service) |
| Output | `trash_nbx.csv` → 00-archimatechild (Host + Service Zeilen, noch ungemergt) |

**Boundary Event (Error) auf NBX03:**
- Typ: **Error Boundary Event**
- Name: `JSON leer oder ungültig`
- Verbindet zu: End Event `Fehler — NBX02 erneut ausführen`

---

### 3.6 Task: NBX04 — IP-Merge

| Feld | Wert |
|------|------|
| Typ | **Script Task** |
| Name | `NBX04 — IP-Merge` |
| Lane | NBX-Scripts |
| Script | `NBX04-ip_merge.py` |
| Durchlauf 1 | Alle Host-Zeilen einsammeln (ip → host-dict) |
| Durchlauf 2 | Alle Service-Zeilen zuordnen (ip aus nbx_raw_id: IP:Port) |
| Logik | Port-String aus Description-Spalte lesen (`Port 22/tcp`) |
| Output | `trash_nbx.csv` überschrieben — **eine Zeile pro Host**, open_ports aggregiert |
| Warnung | Services ohne zugehörigen Host werden geloggt und übersprungen |

**Boundary Event (Error) auf NBX04:**
- Typ: **Error Boundary Event**
- Name: `CSV lesen/schreiben fehlgeschlagen`
- Verbindet zu: End Event `Fehler — Dateizugriff prüfen`

---

### 3.7 Task: NBX05 — Übergabe-Report erstellen

| Feld | Wert |
|------|------|
| Typ | **Script Task** |
| Name | `NBX05 — Übergabe-Report erstellen` |
| Lane | NBX-Scripts |
| Script | `NBX05-handoff_report.py` |
| Liest | `trash_nbx.csv` (gemergt), `properties_nbx.csv` (wenn vorhanden) |
| Output | `NBX05-handoff_report.txt` → 99-logs |
| Inhalt | Statistik je Objekt-Typ, nächste Schritte (ECM Phase 1 oder 2) |

**Boundary Event (Error) auf NBX05:**
- Typ: **Error Boundary Event**
- Name: `Report kann nicht geschrieben werden`
- Verbindet zu: End Event `Fehler — 99-logs prüfen`

---

### 3.8 Task: Report prüfen (manuell)

| Feld | Wert |
|------|------|
| Typ | **User Task** |
| Name | `Handoff-Report prüfen` |
| Lane | EUMAXL |
| Aktion | NBX05-handoff_report.txt lesen — Anzahl Hosts und Services plausibel? |

**Gateway nach Report-Prüfung:**
- Typ: **Exclusive Gateway**
- Name: `Ergebnis plausibel?`
- Nein-Pfad → **User Task** `Entscheid: erneut scannen oder abbrechen?` (Lane: EUMAXL)
  - Erneut scannen → zurück zu NBX02 (Sequence Flow mit Label `Erneut scannen`)
  - Abbrechen → End Event `Abbruch — manuell`
- Ja-Pfad → weiter zu ECM-Entscheid

---

### 3.9 Gateway: ECM-Phase bestimmen

| Feld | Wert |
|------|------|
| Typ | **Exclusive Gateway** |
| Name | `Mapping-Modell vorhanden?` |
| Lane | EUMAXL |
| Ja-Pfad | → End Event `NBX-Flow abgeschlossen — ECM Phase 2 starten` |
| Nein-Pfad | → End Event `NBX-Flow abgeschlossen — ECM Phase 1 starten` |

---

### 3.10 End Events (Übersicht)

| Name | Typ | Auslöser |
|------|-----|----------|
| `NBX-Flow abgeschlossen — ECM Phase 1 starten` | End Event (einfach) | Kein Mapping-Modell vorhanden |
| `NBX-Flow abgeschlossen — ECM Phase 2 starten` | End Event (einfach) | Mapping-Modell vorhanden |
| `Abbruch — kein Scan-Ergebnis` | End Event (einfach) | Keine Hosts gefunden, EUMAXL bricht ab |
| `Abbruch — manuell` | End Event (einfach) | Report nicht plausibel, EUMAXL bricht ab |
| `Fehler — Umgebung nicht bereit` | **End Event (Error)** | NBX00 Boundary |
| `Fehler — Konfiguration prüfen` | **End Event (Error)** | NBX01 Boundary |
| `Fehler — nmap prüfen` | **End Event (Error)** | NBX02 Boundary |
| `Fehler — NBX02 erneut ausführen` | **End Event (Error)** | NBX03 Boundary |
| `Fehler — Dateizugriff prüfen` | **End Event (Error)** | NBX04 Boundary |
| `Fehler — 99-logs prüfen` | **End Event (Error)** | NBX05 Boundary |

---

## 4. Sequence Flow — Hauptpfad

```
Start
  → NBX00 (Script Task)
  → NBX01 (Script Task)
  → Gateway: Mehr als 254 Hosts?
      Ja  → User Task: Warnung bestätigen → NBX02
      Nein → NBX02
  → NBX02 (Script Task)
  → Gateway: Hosts gefunden?
      Nein → User Task: Warnung → End Event Abbruch
      Ja   → NBX03
  → NBX03 (Script Task)
  → NBX04 (Script Task)
  → NBX05 (Script Task)
  → User Task: Handoff-Report prüfen
  → Gateway: Ergebnis plausibel?
      Nein → User Task: Entscheid
               Erneut scannen → NBX02
               Abbrechen → End Event Abbruch manuell
      Ja   → Gateway: Mapping-Modell vorhanden?
               Nein → End Event Phase 1
               Ja   → End Event Phase 2
```

---

## 5. Hinweise für Camunda Modeler

- **Error Boundary Events** immer als Non-Interrupting NEIN setzen —
  sie unterbrechen den Task und führen direkt zum Fehler-End-Event.
- **User Tasks** in Lane EUMAXL sind bewusste Haltepunkte —
  kein automatischer Weiterfluss.
- Der Rückpfeil von `Erneut scannen` zu NBX02 ist ein **normaler
  Sequence Flow** mit dem Label `Erneut scannen` — kein Loop-Marker.
- `trash_nbx.csv` taucht zweimal als Dateiartefakt auf:
  einmal nach NBX03 (ungemergt) und einmal nach NBX04 (gemergt, eine Zeile pro Host).
  Im Filesystem-Lane als **Data Object** mit unterschiedlichem Label darstellen:
  `trash_nbx.csv (roh)` und `trash_nbx.csv (gemergt)`.

---

```
BPMN_NBX-Flow_DEV_S105 | R+MUNI Blueprint | S1.05 | 2026-04-13
```
