================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-FLW-CleaningRun-5.5
Datum               : 2026-03-13
Stage               : 5 (aktiv)
Status              : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch      : Entwickler + Claude (Pair-Session)
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Stage-Modell (Ist-Zustand)
-------------------------------
Stage 4  FREEZE
         FLW00/01/02 entstammen Stage 4 und wurden bisher bewusst
         nicht angefasst — eigener Sprint war geplant.

Stage 5  AKTIV
         Cleaning Run 5.5 schließt die strukturelle Harmonisierung
         aller Scripts auf Stage-5-Konventionen ab.

1.2 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Strukturelle Bereinigung (Cleaning Run 5.5)

Begründung   : Im Zuge des Cleaning Run 5.5 wurden alle CSV-, XML-,
               ATL-, M2B- und HLP-Scripts auf Stage-5-Konventionen
               umgestellt. Die FLW-Reihe (FLW00/01/02) wurde dabei
               bewusst zurückgestellt und als letzter offener Punkt
               im selben Run abgeschlossen.

               Konkret enthielten alle drei Scripts veraltete Pfade
               und Konventionen aus Stage 4:
                 - root.txt statt root.cfg
                 - BLUEPRINT_ROOT= statt <rootfolder>=
                 - 03-stages statt 02-stages
                 - 02-artifacts statt 01-artifacts

Fachlicher   : Alle Scripts lesen einheitlich aus root.cfg.
Mehrwert       Keine Sonderbehandlung der FLW-Reihe mehr nötig.
               Fehlermeldungen und Pfadausgaben sind konsistent
               mit dem Rest der Blueprint-Toolchain.

Governance-  : Ausschließlich Pfad- und Konventions-Anpassung.
Konformität    Keine Logikänderung. FLW-Kernlogik (Scriptrunner,
               Discovery, Element-Mapping) bleibt vollständig
               unverändert.


--------------------------------------------------------------------------------
2. ZIELDEFINITION (gemäß GOV 10.6)
--------------------------------------------------------------------------------

Ziel         : FLW00-scriptrunner.py, FLW01-discover.py und
               FLW02-map_elements.py werden auf Stage-5-Konventionen
               gebracht:
                 - root.cfg statt root.txt
                 - <rootfolder>= statt BLUEPRINT_ROOT=
                 - 02-stages statt 03-stages
                 - 01-artifacts statt 02-artifacts

Abgrenzung   : Kein Eingriff in Scriptrunner-Logik, Flow-Steuerung,
               Discovery-Algorithmus oder Element-Mapping-Logik.
               Ausschließlich Pfad- und Schlüssel-Konventionen.

Überprüfbar  : Erfolgreich wenn FLW00 startet, root.cfg findet und
               einen definierten Flow (z.B. CSV-Trigger-Test)
               vollständig durchläuft ohne Fehler.


--------------------------------------------------------------------------------
3. IST-ZUSTAND — PROBLEMANALYSE
--------------------------------------------------------------------------------

3.1 Veraltete Konventionen (vor Fix)
--------------------------------------
Alle drei FLW-Scripts enthielten identische Muster aus Stage 4:

  root.txt                     → Konfigurationsdatei alt
  BLUEPRINT_ROOT=              → Schlüsselname alt
  "03-stages"                  → Ordnernummer alt
  "02-artifacts"               → Ordnernummer alt

Konkrete Fundstellen je Script:

  FLW00-scriptrunner.py
    Z 60:  """Liest BLUEPRINT_ROOT aus root.txt"""
    Z 66:  if line.startswith("BLUEPRINT_ROOT="):
    Z 73:  root_file = ... "root.txt"
    Z 403: os.path.join(... "03-stages", "99-logs", ...)
    Z 409: os.path.join(blueprint_root, "02-artifacts", "00-xml", ...)
    Z 410: os.path.join(blueprint_root, "02-artifacts", "01-scripts")
    Z 411: os.path.join(blueprint_root, "02-artifacts", "04-flow", ...)

  FLW01-discover.py
    Z 16:  Kommentar: 03-stages/99-logs/flw01-discover.log
    Z 64:  root_file = ... "root.txt"
    Z 76:  if line.startswith("BLUEPRINT_ROOT="):
    Z 331: os.path.join(blueprint_root, "02-artifacts", ...)
    Z 333: os.path.join(blueprint_root, "03-stages", ...)

  FLW02-map_elements.py
    Z 20:  Kommentar: 03-stages/99-logs/flw02-map_elements.log
    Z 83:  root_file = ... "root.txt"
    Z 95:  if line.startswith("BLUEPRINT_ROOT="):
    Z 360: os.path.join(blueprint_root, "02-artifacts", ...)
    Z 361: os.path.join(blueprint_root, "03-stages", ...)


--------------------------------------------------------------------------------
4. LÖSUNG — TECHNISCHE UMSETZUNG
--------------------------------------------------------------------------------

4.1 Änderungsumfang
--------------------
Alle Ersetzungen wurden per Script automatisiert durchgeführt
und anschließend manuell verifiziert:

  Alt                                Neu
  ─────────────────────────────────────────────────────────
  "root.txt"                     →   "root.cfg"
  BLUEPRINT_ROOT=                →   <rootfolder>=
  startswith("BLUEPRINT_ROOT=")  →   startswith("<rootfolder>=")
  line[len("BLUEPRINT_ROOT="):]  →   line[len("<rootfolder>="):]
  "03-stages"                    →   "02-stages"
  "02-artifacts"                 →   "01-artifacts"
  03-stages/ (in Kommentaren)    →   02-stages/
  02-artifacts/ (in Kommentaren) →   01-artifacts/

4.2 Betroffene Dateien
------------------------
  FLW00-scriptrunner.py    Scriptrunner + pre_root Auflösung
  FLW01-discover.py        Discovery + Output-Pfade
  FLW02-map_elements.py    Element-Mapping + Output-Pfade

4.3 Unverändert
----------------
  Scriptrunner-Logik       Flow-Steuerung, run_script(), abort()
  Discovery-Algorithmus    XML-Scan, Typ-Erkennung, Regelwerk
  Element-Mapping-Logik    ArchiMate/BPMN Mapping-Logik
  Alle anderen Scripts     CSV, XML, ATL, M2B, HLP — unberührt


--------------------------------------------------------------------------------
5. ERGEBNIS NACH FIX
--------------------------------------------------------------------------------

Verifikation per automatisiertem Scan — alle drei Scripts:

  Treffer "root.txt"      : 0
  Treffer "BLUEPRINT_ROOT": 0
  Treffer "03-stages"     : 0
  Treffer "02-artifacts"  : 0

Stichprobe FLW00 Root-Auflösung (nach Fix):
  Z 60:  """Liest <rootfolder> aus root.cfg"""
  Z 66:  if line.startswith("<rootfolder>="):
  Z 73:  root_file = os.path.abspath(... "root.cfg")
  Z 409: os.path.join(blueprint_root, "01-artifacts", "00-xml", ...)
  Z 410: os.path.join(blueprint_root, "01-artifacts", "01-scripts")


--------------------------------------------------------------------------------
6. TESTERGEBNIS
--------------------------------------------------------------------------------

Testlauf 2026-03-13:

  Getesteter Flow : CSV-Trigger-Test via FLW00-scriptrunner.py
  Ergebnis        : Durchgelaufen ohne Fehler
  root.cfg        : Gefunden und korrekt geparst
  Pfade           : 01-artifacts / 02-stages — korrekt aufgelöst

Status: OK ✓


--------------------------------------------------------------------------------
7. OFFENE PUNKTE / NEXT STEPS
--------------------------------------------------------------------------------

7.1 Cleaning Run 5.5 — Abschluss
----------------------------------
Status   : ABGESCHLOSSEN
Alle Scripts (CSV, XML, ATL, M2B, HLP, FLW) sind auf
Stage-5-Konventionen. Kein Script enthält mehr root.txt,
BLUEPRINT_ROOT=, 03-stages oder 02-artifacts.

7.2 FLW in flowmapping.txt
----------------------------
Status   : Beobachten
Aktion   : Wenn SPRINT-CSV-Refactoring neue Flows einträgt,
           flowmapping.txt prüfen ob FLW-Einträge noch korrekt
           auf 01-artifacts zeigen.

7.3 SPRINT-CSV-Refactoring
---------------------------
Status   : Definiert, noch nicht gestartet
Aktion   : Nächster Sprint. CSV10+, XLSX00+, MaM00+ aufbauen.
           Sprint Definition: Sprint-DEF-CSV-Refactoring.txt

7.4 Stage-Ende Dokumentation
------------------------------
Status   : Ausstehend (gemäß GOV 10.9 verpflichtend zum Stage-Ende)
Aktion   : Dev-Dokumentation ist nicht auditpflichtig (GOV 10.8).
           Zum Stage-Ende ist vollständige governance-konforme
           Dokumentation zu erstellen.


--------------------------------------------------------------------------------
8. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Strukturelle Bereinigung Stage 5
GOV 10.5  Fachlicher Mehrwert        OK  Einheitliche Konventionen, kein Sonderfall
GOV 10.5  Keine implizite Gov-Änd.   OK  Keine Logikänderung
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 2
GOV 10.6  Ziel überprüfbar           OK  Testergebnis Abschnitt 6
GOV 10.7  Zwischenschritte           OK  Normativ zugelassen (Cleaning Run)
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Keine Architekturänderung
Stage 5   Rückkopplungsschutz        OK  FLW-Kernlogik unverändert


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-FLW-CleaningRun-5.5 | Stage 5 | 2026-03-13
================================================================================
