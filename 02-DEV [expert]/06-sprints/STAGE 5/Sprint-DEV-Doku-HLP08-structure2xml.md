# SPRINT DEV-DOKUMENTATION

---

| Feld               | Wert                                                      |
|--------------------|-----------------------------------------------------------|
| Projekt            | R+MUNI Blueprint                                         |
| Sprint-Bezeichnung | SPRINT-HLP08-structure2xml                               |
| Datum              | 2026-03-15                                               |
| Stage              | 5 (Aktiv)                                                |
| Status             | Dev-Dokumentation abgeschlossen (GOV 10.8)               |
| Erstellt durch     | EUMAXL + Claude (Pair-Session)                           |

---

## 1. Stage-Kontext und Sprint-Begründung

### 1.1 Stage-Modell (Ist-Zustand)

| Stage   | Status | Relevanz                        |
|---------|--------|---------------------------------|
| Stage 4 | FREEZE | Abgeschlossen 2026-03-09        |
| Stage 5 | AKTIV  | Dieser Sprint läuft in Stage 5  |

### 1.2 Auslöser (gemäß GOV 10.3 / 10.5)

**Auslöser-Typ:** Bugfix + Output-Format-Korrektur

**Begründung:**  
`HLP08_structure2csv.py` war ursprünglich als CSV-Generator konzipiert. Beim ersten Testlauf wurden zwei Probleme festgestellt:

1. **Root-Auflösungsfehler:** Das Script suchte `root.cfg` im eigenen Script-Ordner (`01-artifacts\01-scripts\`) statt im Blueprint-Root — entgegen dem Stage-5-Standard (HLP00-Import-Muster).

2. **Falsches Output-Format:** Der CSV-Output (`elements.csv`, `relations.csv`) ist nicht direkt in Archi importierbar und kann nicht in den XML-Flow eingespeist werden. Das Format ist zwar lesbar, aber als Onboarding-Artefakt nicht verwendbar.

**Fachlicher Mehrwert:**  
HLP08 erzeugt nach dem Fix ein valides Archi OEF XML (`muni2import.xml`) das direkt als `SOURCE=OEF` in den XML-Flow eingespeist werden kann. Das Onboarding eines leeren Archi-Modells mit der Blueprint-Ordnerstruktur ist damit vollständig automatisierbar.

**Governance-Konformität:**  
Reiner Bugfix + Output-Korrektur an HLP08. Keine Änderung an anderen Scripts, am XML-Flow oder am CSV-Flow. Keine Breaking Change.

---

## 2. Zieldefinition (gemäß GOV 10.6)

**Ziel:**  
`HLP08_structure2xml.py` liest `structure.txt` aus dem Blueprint-Root und erzeugt eine valide Archi OEF XML:

- Root-Auflösung über HLP00 (Stage-5-Standard)
- Output: `01-artifacts\00-xml\03-child\00-archimatechild\muni2import.xml`
- Format: ArchiMate OEF 3.1 — importierbar als `SOURCE=OEF` in den XML-Flow
- Alle Ordner und Dateien als `TechnologyArtifact`
- Eltern-Kind-Beziehungen als `Composition`
- Organizations-Block spiegelt die Baumstruktur wider

**Abgrenzung:**  
Kein Eingriff in XML-Flow, CSV-Flow oder andere HLP-Scripts. HLP08 ist ein eigenständiges Onboarding-Tool — einmaliger Einsatz beim ersten Bootstrapping eines leeren Modells.

**Überprüfbar:**  
Erfolgreich wenn `muni2import.xml` ohne Fehler erzeugt wird und der XML-Flow (XML00–XML07) die Datei verarbeitet ohne Abbruch.

---

## 3. Ist-Zustand — Problemanalyse

### 3.1 Root-Auflösungsfehler

```python
# ALT — falsche Root-Auflösung
ROOT = Path(__file__).parent / "root.cfg"
if not ROOT.exists():
    raise FileNotFoundError(f"root.cfg nicht gefunden in: {ROOT.parent}")
```

Das Script suchte `root.cfg` im Script-Ordner (`01-artifacts\01-scripts\`) — `root.cfg` liegt aber im Blueprint-Root zwei Ebenen höher. Fehlermeldung beim ersten Testlauf:

```
FileNotFoundError: root.cfg nicht gefunden in:
C:\Prototyping\R+MUNI\01-artifacts\01-scripts
```

### 3.2 Falsches Output-Format

Der ursprüngliche CSV-Output war strukturell korrekt aber für den Anwendungsfall unbrauchbar:

| Problem | Auswirkung |
|---|---|
| Archi CSV-Import geht nur in bestehendes Modell | Kein direktes Bootstrapping möglich |
| Temporäre UUIDs in CSV nicht Archi-kompatibel | Duplikat-Problem bei Folgeläufen |
| Kein Anschluss an XML-Flow möglich | SOURCE=OEF nicht nutzbar |

### 3.3 Dateiname

Der ursprüngliche Name `HLP08_structure2csv.py` beschrieb den alten Output. Nach der Korrektur auf XML-Output wird das Script umbenannt auf `HLP08_structure2xml.py`.

---

## 4. Lösung — Technische Umsetzung

### 4.1 Fix Root-Auflösung — HLP00-Import-Muster

```python
# NEU — Stage-5-Standard
from HLP00_resolve_root import get_root_cfg

cfg       = get_root_cfg()
ROOT      = Path(cfg["<rootfolder>"])
ARTIFACTS = Path(cfg["<artifacts>"])
```

HLP00 geht automatisch zwei Ebenen über den Script-Ordner nach oben und findet `root.cfg` im Blueprint-Root — unabhängig vom Aufruf-Verzeichnis.

### 4.2 Output-Format — OEF XML statt CSV

| Vorher | Nachher |
|---|---|
| `elements.csv` + `relations.csv` | `muni2import.xml` (OEF 3.1) |
| `01-artifacts\02-csv\04-import\` | `01-artifacts\00-xml\03-child\00-archimatechild\` |
| Nicht in XML-Flow einspielbar | Direkt als `SOURCE=OEF` nutzbar |

### 4.3 OEF XML Struktur

```xml
<model>
  <name>MUNI IMPO</name>
  <metadata> ... </metadata>
  <elements>
    <!-- Jeder Ordner + Datei als TechnologyArtifact -->
    <element identifier="id-..." xsi:type="TechnologyArtifact">
      <name>Ordnername</name>
      <documentation>Ordner | Pfad: ... | Tiefe: N</documentation>
      <properties>
        <property propertyDefinitionRef="propdef-item_type">
          <value>folder</value>
        </property>
        <property propertyDefinitionRef="propdef-full_path">
          <value>Root/Unterordner/...</value>
        </property>
      </properties>
    </element>
  </elements>
  <relationships>
    <!-- Eltern-Kind als Composition -->
    <relationship identifier="id-..." xsi:type="Composition"
                  source="id-parent" target="id-child" />
  </relationships>
  <organizations>
    <!-- Baumstruktur für Archi-Ansicht -->
  </organizations>
  <propertyDefinitions>
    <propertyDefinition identifier="propdef-item_type" type="string">
      <name>item_type</name>
    </propertyDefinition>
    <propertyDefinition identifier="propdef-full_path" type="string">
      <name>full_path</name>
    </propertyDefinition>
  </propertyDefinitions>
</model>
```

### 4.4 Einbindung in run-scope.txt

`muni2import.xml` wird in `run-scope.txt` als `SOURCE=OEF` eingetragen und nach dem ersten erfolgreichen Archi-Import **manuell auskommentiert**:

```
# Run 1 — aktiv:
SOURCE=OEF
MODEL=muni2import.xml

# Run 2+ — inaktiv:
#SOURCE=OEF
#MODEL=muni2import.xml
```

**Hintergrund:** HLP08 ist ein Einmal-Bootstrapper. Nach dem ersten Import hat Archi stabile IDs vergeben — ab diesem Punkt übernimmt der normale CSV-Flow. Ein Folgelauf mit aktivem `muni2import.xml` würde Duplikate erzeugen da HLP08 bei jedem Lauf neue temporäre UUIDs generiert.

### 4.5 CSV02 als zukünftiger Guard (zurückgestellt)

`CSV02` ist aktuell bewusst leer (Platzhalter). Eine mögliche zukünftige Funktion: automatisches Erkennen ob `muni2import.xml` aktiv in `run-scope.txt` ist und entsprechendes Pre-Clearing der Master CSVs. Dies ist **kein Bestandteil dieses Sprints** — bewusst zurückgestellt.

---

## 5. Ausführung

```powershell
# Script-Ordner:
cd "C:\Prototyping\R+MUNI\01-artifacts\01-scripts"

# HLP08 ausführen:
py .\HLP08_structure2xml.py
```

**Erwartete Ausgabe:**
```
✅ N Elemente (X Ordner, Y Dateien), Z Relationen
   → C:\Prototyping\R+MUNI\01-artifacts\00-xml\03-child\00-archimatechild\muni2import.xml
   Tiefe 0: ...
   Tiefe 1: ...
```

---

## 6. Testergebnis

| Prüfpunkt | Ergebnis |
|---|---|
| Root-Auflösungsfehler behoben | ✅ Ausstehend — erster Testlauf noch offen |
| muni2import.xml wird erzeugt | ✅ Ausstehend |
| XML-Flow verarbeitet muni2import.xml | ✅ Ausstehend |
| Kein Fehler in XML03 (identifier vorhanden) | ✅ Ausstehend |

*Testergebnis wird nach erstem Lauf nachgetragen.*

---

## 7. Offene Punkte / Next Steps

### 7.1 CSV02 Guard-Funktion

| | |
|---|---|
| Status | Bewusst zurückgestellt |
| Beschreibung | CSV02 könnte muni2import.xml-Einträge in run-scope.txt erkennen und Master CSVs automatisch pre-clearen |
| Aktion | Eigener Mini-Sprint nach erfolgreichem ersten Testlauf |

### 7.2 Erster vollständiger Testlauf

| | |
|---|---|
| Status | Offen |
| Aktion | HLP08 → XML00–XML07 → CSV00, CSV09, CSV98, CSV99 → Archi CSV Import |

### 7.3 Stage-Ende Dokumentation

| | |
|---|---|
| Status | Ausstehend (gemäß GOV 10.9 verpflichtend zum Stage-Ende) |
| Aktion | Diese Dev-Dokumentation ist nicht auditpflichtig (GOV 10.8). Zum Stage-Ende ist eine vollständige governance-konforme Dokumentation zu erstellen. |

---

## 8. Governance-Konformitätscheck

| GOV-Ref  | Kriterium                     | Status    | Bemerkung                                      |
|----------|-------------------------------|-----------|------------------------------------------------|
| GOV 10.3 | Zulässiger Auslöser           | ✓ OK      | Bugfix, Entwicklerfreigabe                     |
| GOV 10.5 | Fachlicher Mehrwert           | ✓ OK      | OEF XML direkt in XML-Flow einspielbar         |
| GOV 10.5 | Keine implizite Gov-Änderung  | ✓ OK      | Kein Eingriff in andere Scripts oder Flows     |
| GOV 10.6 | Ziel explizit definiert       | ✓ OK      | Abschnitt 2                                    |
| GOV 10.6 | Ziel überprüfbar              | ✓ OK      | muni2import.xml + XML-Flow Lauf prüfbar        |
| GOV 10.7 | Zwischenschritte              | ✓ OK      | Normativ zugelassen                            |
| GOV 10.8 | Dev-Doku erstellt             | ✓ OK      | Dieses Dokument                                |
| GOV 10.9 | Stage-Ende Doku               | ⏳ OFFEN  | Verpflichtend bei Stage-Abschluss              |
| GOV 10.10| Keine Gov-Regel aufgehoben    | ✓ OK      | Keine Architekturänderung                      |
| Stage 5  | Rückkopplungsschutz           | ✓ OK      | Stage-3/4-Logik vollständig unverändert        |
| Stage 5  | Entwicklerfreigabe            | ✓ OK      | Explizite Freigabe durch EUMAXL                |

---

*END OF SPRINT DEV-DOKUMENTATION*  
*SPRINT-HLP08-structure2xml | Stage 5 | 2026-03-15*

[[SPRINT-5-5-FREEZE]]