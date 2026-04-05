================================================================================
TOOLBAUKASTEN – HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : TOOLBAUKASTEN_How2_DEV_S6
Tag             : #dev #how2 #toolbaukasten #s6 #s8
Datum           : 2026-03-26
Stage           : S8 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-21
Basis           : TOOLBAUKASTEN_principles_S6.md
Ablageort       : 00-concept/02-how2/TOOLBAUKASTEN_How2_DEV_S6.md
================================================================================


ZWECK DIESES DOKUMENTS
================================================================================

Praktische Developer-Anleitung zum R+MUNI Toolbaukasten.

Richtet sich an:
  → EUMAXL (Blueprint Developer)
  → Zukünftige Dev-Team-Mitglieder
  → Technische Partner bei Erweiterungen

Aufgaben:
  ✓ Wie installiere ich MINIMAL / DEFAULT / ADDON?
  ✓ Wie manage ich die Tools in der Praxis?
  ✓ Wie füge ich neue Tools hinzu (Governance)?
  ✓ Wie erkenne ich Probleme und handle sie?
  ✓ Wie dokumentiere ich Entscheidungen?

Voraussetzung:
  → TOOLBAUKASTEN_principles_S6.md gelesen und verstanden
  → Grundverständnis der Tier-Struktur (MINIMAL / DEFAULT / ADDON)


================================================================================
1. INSTALLATION & SETUP
================================================================================

1.1 MINIMAL-Installation (schneller Einstieg)
-----------------------------------------------

Wenn du R+MUNI schnell lauffähig machen willst:

Schritt 1: Archi 5.8 installieren
  → Download: https://www.archimatetool.com/download/
  → Installer ausführen
  → Nach Installation: jArchi Plugin installieren
    (Help → Manage Plug-ins → Install New → jArchi 1.11.0)
  → Archi neu starten

Schritt 2: Camunda Modeler installieren
  → Download: https://camunda.com/download/modeler/
  → ZIP entpacken nach: C:\Prototyping\R+MUNI Apps\camunda-modeler
  → Ordnernamen aus ZIP entfernen
  → Ausführbar

Schritt 3: Python 3.9+ installieren
  → Download: https://www.python.org/downloads/
  → Installer mit "Add Python to PATH" starten
  → Nach Installation: pip install lxml openpyxl
  → Terminal neu starten
  → Test: python --version

Schritt 4: OpenJDK 11+ installieren
  → Download: https://adoptium.net/
  → Installer ausführen
  → Test: java -version

Fertig! MINIMAL läuft jetzt.

Test-Befehl (im Blueprint Root):
  python 01-artifacts\01-scripts\CSV00-validate_environment.py
  
Erwartet: [CSV00] OK | root resolved


1.2 DEFAULT-Installation (produktiver Betrieb)
-----------------------------------------------

Zusätzlich zu MINIMAL:

Notepad++ + Plugins:
  → Download: https://notepad-plus-plus.org/
  → Installer ausführen
  → Plugins via Plugin Admin installieren (siehe Install.txt 3.1)

Git (2.53.0.2+):
  → https://git-scm.com/ (Installer)
  → Technischer Unterbau für VS Code + Claude Integration
  → Konfigurieren: git config --global user.name "Name"

GitHub (Core Component):
  → https://github.com/
  → Repository-Verwaltung, Backup, Team-Sync
  → Core Component im R+MUNI Standard-Setup

Obsidian:
  → Download: https://obsidian.md/download
  → Installer ausführen
  → Vault öffnen: R+MUNI <KUERZEL>\

draw.io:
  → Download: https://www.drawio.com/
  → Installer ausführen

Inkscape:
  → Download: https://inkscape.org/release/
  → Installer ausführen

PowerShell 7:
  → Download: https://github.com/PowerShell/PowerShell/releases
  → Installer ausführen
  → Test: pwsh --version

KeePass:
  → Download: https://keepass.info/
  → Installer ausführen
  → Neue Datenbank erstellen (.kdbx)
  → NICHT im Blueprint-Verzeichnis ablegen

Claude Desktop (für DEV):
  → Download: https://claude.ai/
  → Pro Abo empfohlen (20 USD/Monat)
  → Projektzugang konfigurieren

Fertig! DEFAULT läuft jetzt komplett.


1.3 ADDON-Installation (Use-Case abhängig)
--------------------------------------------

Atlassian Jira & Confluence (DEV-ONLY):
  → Nur wenn interne Dev-Prozesse brauchen
  → Setup: https://www.atlassian.com/
  → Free Plan bis 10 User
  → Installation: Cloud-basiert, keine lokale Installation

BOC Group Integration (Enterprise):
  → Nur bei Customer-Bedarf
  → Requires: ADOIT oder ADONIS Lizenz
  → Setup: OEF Export aus Archi → BOC Import
  → Dokumentation: siehe Install.txt 4.2


================================================================================
2. TOOL-VERWALTUNG IN DER PRAXIS
================================================================================

2.1 Versionierung & Updates
---------------------------

Policy für Updates:

STABIL-Tools (automatisch updaten):
  ✓ Archi 5.8 — regelmäßig updaten (keine Breaking Changes)
  ✓ Python — LTS Updates empfohlen
  ✓ OpenJDK — LTS Versionen halten
  ✓ Notepad++ — aktiv gepflegt, safe
  ✓ Git — Standard-Updates
  ✓ KeePass — regelmäßig updaten

OPTIONAL-Tools (evaluate before update):
  ⚠ Claude — häufige Updates, neue Features
  ⚠ Obsidian — Core stabil, aber Sync/Publish optional
  ⚠ draw.io — regelmäßige Updates, check Release Notes

BLOCKER (sofort updaten):
  🔴 Sicherheits-CVE in allen Tools
  🔴 Kompatibilität-Brecher (zuerst testen!)


2.2 Abhängigkeits-Management
-----------------------------

Wenn du ein Tool installierst, checke seine Dependencies:

Beispiel Archi 5.8:
  ✓ Benötigt: OpenJDK 11+
  ✓ Optional: jArchi Plugin (benötigt OpenJDK 21)
  ✓ Optional: coArchi, excelArchi (Plugins)

Beispiel Camunda Modeler:
  ✓ Benötigt: OpenJDK
  ✓ Optional: Archi für Kontext

Beispiel PowerShell Scripts:
  ✓ Benötigt: Python 3.9+
  ✓ Benötigt: PowerShell 7+
  ✓ Optional: Git für Versionierung

→ Immer vor Installation: Abhängigkeitsmatrix prüfen (siehe Principles 6.)


2.3 Konfiguration & Persistenz
-------------------------------

Wo speichern sich Tool-Konfigurationen:

Archi Models:
  → 00-model\00-archimate\00-archimateactive\
  → Immer versionieren (Git)
  → Master-Quelle für alle Exporte

Python Scripts:
  → 01-artifacts\01-scripts\
  → Konfiguration via root.cfg und flowtriggers.txt
  → Test nach jedem Update

Notepad++:
  → Plugins-Konfiguration: lokal im Benutzerprofil
  → Backup empfohlen wenn custom Settings

Git Repositories:
  → .gitignore: .bak, .log, .lck, .obsidian/ ausgeschlossen
  → Commit nach Modell-Änderungen
  → Aussagekräftige Commit-Messages

KeePass:
  → Datenbank (.kdbx) separat sichern (nicht im Blueprint!)
  → USB verschlüsselt oder OneDrive


================================================================================
3. ENTSCHEIDUNGS-GOVERNANCE: NEUE TOOLS HINZUFÜGEN
================================================================================

3.1 Wann ein neues Tool in R+MUNI aufnehmen?
----------------------------------------------

Ein Tool wird Teil von R+MUNI wenn:

✓ Klarer Mehrwert erkannt (nicht "vielleicht nützlich")
✓ Kostenlos oder Patron-Modell (kein Vendor Lock-in)
✓ Open Source oder langfristig stabil
✓ Komplexität nicht unverhältnismäßig steigt
✓ GOV-Entscheid dokumentiert

Nicht aufnehmen wenn:
  ✗ Proprietär oder unklar lizenziert
  ✗ Vendor Lock-in wahrscheinlich
  ✗ Zu nischenspezifisch
  ✗ Bessere Alternative existiert


3.2 Tool-Entscheidungs-Prozess (Governance)
---------------------------------------------

Schritt 1: Identifiziere das Problem
  → Was ist die aktuelle Schmerz-Stelle?
  → Ist das ein Dev-Problem oder User-Problem?

Schritt 2: Evaluiere Alternativen
  → Mind. 2-3 Alternativen betrachten
  → Lizenz, Kosten, Komplexität vergleichen

Schritt 3: Dokumentiere die Entscheidungsgrundlage
  → Welches Tool? Warum dieses?
  → Welche Alternativen rejected? Warum?
  → Kosten und langfristige Stabilität?
  → Governance-Konformität?

Schritt 4: Implementiere & Test
  → Installation sauber dokumentieren
  → Test mit MINIMAL-Setup
  → Integration mit bestehenden Tools prüfen
  → Abhängigkeiten identifizieren

Schritt 5: Dokumentiere das Resultat
  → Neue Version von TOOLBAUKASTEN_principles_S6.md
  → Install.txt aktualisieren
  → How2 Dokumente updaten
  → GOV-Eintrag wenn relevant


3.3 Beispiel: Neues Tool "XYZ" hinzufügen
-------------------------------------------

Angenommen: Du erkennst dass "XYZ Tool" für R+MUNI wertvoll wäre.

Dokumentation im Code:
  → TOOLBAUKASTEN_principles_S6.md
    - In welche Ebene (MINIMAL/DEFAULT/ADDON)?
    - Warum dieses Tool?
    - Kosten und Lizenz?
    - Abhängigkeiten?

Dokumentation in Install.txt:
  → Abschnitt 2 (MINIMAL) / 3 (DEFAULT) / 4 (ADDON)
  → Download-Link
  → Installationsschritte
  → Plugins oder Konfiguration?
  → Test-Befehl zum Validieren

Dokumentation in How2 Docs:
  → How2_DEV_S6: praktische Nutzung
  → How2_USER_S6: nur wenn User-relevant

Governance-Dokumentation:
  → Sprint-Dev-Doku: Warum wurde XYZ gewählt?
  → GOV-Update wenn nötig


================================================================================
4. PROBLEM-SOLVING & DEBUGGING
================================================================================

4.1 Tool funktioniert nicht — Was tun?
---------------------------------------

Allgemeines Debugging-Schema:

1. Prüfe die Abhängigkeiten
   → Ist OpenJDK korrekt installiert? (java -version)
   → Ist Python im PATH? (python --version)
   → Sind alle Plugins installiert?

2. Prüfe die Konfiguration
   → root.cfg aktuell? (rootfolder korrekt?)
   → Encoding UTF-8? (Notepad++ → Encoding prüfen)
   → Pfade in Scripts richtig?

3. Prüfe die Dateien
   → Existiert die Eingabe-Datei?
   → Ist sie nicht korrupt?
   → Richtige Dateityp (CSV, XML, XLSX)?

4. Führe Test aus (CSV00-validate_environment.py)
   → python 01-artifacts\01-scripts\CSV00-validate_environment.py
   → Logs prüfen: 02-stages\99-logs\

5. Isoliere das Problem
   → Tool einzeln testen (nicht im Flow)
   → Input-Datei minimal halten
   → Error-Message genau lesen

6. Dokumentiere & Escalate
   → Was war die Symptom?
   → Was hast du getestet?
   → Was war das Resultat?
   → Logs anhängen


4.2 Häufige Fehler & Lösungen
------------------------------

FEHLER: "python: command not found"
  LÖSUNG: Python PATH nicht richtig. Terminal neu starten nach Installation.
          Test: python --version

FEHLER: "jArchi Plugin funktioniert nicht"
  LÖSUNG: OpenJDK 21 erforderlich (nicht 11). Archi neu starten nach Update.

FEHLER: "UTF-8 Encoding Error in CSV Import"
  LÖSUNG: Dateien müssen UTF-8 sein (ohne BOM außer jira_ea_import.csv).
          Notepad++ → Encoding → UTF-8

FEHLER: "root.cfg nicht gefunden"
  LÖSUNG: root.cfg muss im Blueprint Root sein.
          Inhalt: rootfolder=C:\Prototyping\R+MUNI <KUERZEL>

FEHLER: "Archi Export funktioniert nicht"
  LÖSUNG: Archi-Datei möglicherweise korrupt. Backup laden.
          CSV-Export Plugin aktiviert? (Help → Manage Plug-ins)

FEHLER: "Git Push schlägt fehl"
  LÖSUNG: GitHub Credentials nicht konfiguriert.
          git config --global user.name / user.email


================================================================================
5. BEST PRACTICES FÜR DEVELOPER
================================================================================

5.1 Arbeiten mit Tools
----------------------

Archi ist der Master:
  → Alle Änderungen zuerst in Archi
  → Dann exportieren (nicht manuell in CSVs editieren)
  → CSV/XML sind abgeleitete, read-only (quasi)

Versionierung mit Git:
  → Nach größeren Änderungen committen
  → Aussagekräftige Commit-Messages
  → Regelmäßig pushen (kein großer Batch am Ende)

Dokumentation aktuell halten:
  → Install.txt: wenn neue Tool-Versions-Anforderungen
  → Principles: wenn Tier-Struktur ändert
  → How2 Docs: wenn praktische Handgriffe ändern

Logging & Error-Handling:
  → Python Scripts schreiben Logs in 02-stages\99-logs\
  → Error-Messages müssen verständlich sein (nicht "Error 42")
  → Stack-Traces helfen beim Debugging


5.2 Code-Qualität
------------------

Python Scripts:
  → Folge dem r-muni-blueprint Skill (Naming, Struktur)
  → 1 Script = 1 Outcome (nicht Multi-Outcome)
  → Kommentare auf Deutsch, Code auch wenn möglich
  → Error-Handling: hart abbrechen mit aussagekräftiger Message

jArchi Scripts:
  → JavaScript gut formatieren (JSTool Plugin)
  → Dokumentiere Input & Output
  → Teste mit verschiedenen Modell-Größen

Dokumentation:
  → Warum wurde das so entschieden? (nicht nur Was)
  → Beispiele geben
  → Edge-Cases dokumentieren


5.3 Token-Effizienz (Claude-Sessions)
--------------------------------------

Da Claude DEV-Tool ist — Token-Bewusstsein ist wichtig:

Gut:
  ✓ Nur FREEZE und aktuelles Stage-Ziel laden
  ✓ Konkrete Probleme stellen (nicht ganze Logik erklären)
  ✓ Bereits funktionierende Teile nicht neu beschreiben
  ✓ Claude das Kontrollorgan sein lassen (verifiziert Output)

Nicht gut:
  ✗ Komplette alte Dokumentation jedes Mal laden
  ✗ Vage Anfragen ("mach mir ein Script")
  ✗ Alles nochmal erklären was schon im Blueprint steht
  ✗ Zu lange Kontexte für einfache Fragen

Faustregel:
  → Install.txt + FREEZE + aktuelle Ziele = genug Kontext
  → Rest ist Detail (nur bei Bedarf laden)


================================================================================
6. KOMMUNIKATION & DOKUMENTATION
================================================================================

6.1 Entscheidungen dokumentieren
---------------------------------

Immer wenn ein Tool oder eine Struktur-Entscheidung getroffen wird:

Format:
  WHAT:   Welches Tool / Struktur-Entscheidung?
  WHY:    Warum diese Entscheidung?
  WHEN:   Wann implementiert?
  WHERE:  Welche Dokumentation aktualisiert?
  STATUS: ALPHA / BETA / STABLE?

Ablageort:
  → Sprint-Dev-Doku (wenn Teil eines Sprints)
  → TOOLBAUKASTEN_principles_S6.md (wenn Tool-Entscheidung)
  → Install.txt (wenn Installation betroffen)
  → Entsprechende How2 Docs (wenn praktische Auswirkung)


6.2 Kommunikation mit Beta-Kunden
----------------------------------

Wenn Tool-Änderungen Beta-Kunden beeinflussen:

Transparent sein:
  ✓ Was ändert sich?
  ✓ Muss der Kunde was tun?
  ✓ Gibt es Fallback-Optionen?
  ✓ Kosten? Aufwand?

Dokumentation für Kunden:
  → How2_USER_S6 aktualisieren
  → Nicht: technische Gory Details
  → Ja: "Was muss ich tun? Was ändert sich für mich?"


================================================================================
7. ROADMAP: ZUKÜNFTIGE TOOL-KANDIDATEN
================================================================================

Diese Tools sind evaluiert aber noch nicht Teil von R+MUNI:

VS Code + MCP (optional für Zukunft)
  → Interessant wenn: größeres Dev-Team
  → Status: OPTIONAL, aktuell nicht in Verwendung
  → Nicht: Token-Overhead für aktuellen Setup

Monitoring & Logging (geplant Stage 7+)
  → ELK Stack für Runtime-Error Tracking
  → Status: NOT PLANNED für S6, später möglich

Versionskontrolle (optional)
  → Git ist empfohlen, aber nicht erzwungen
  → GitHub private Repos kostenlos
  → Status: RECOMMENDED, nicht MANDATORY

O365 Integration (geplant Stage 7+)
  → OneDrive, SharePoint, Teams Integration
  → Status: ROADMAP, noch nicht implementiert


================================================================================
ABSCHLUSS
================================================================================

Dieses Dokument ist die praktische Developer-Anleitung zum Toolbaukasten.

Es behandelt:
  → Installation (MINIMAL / DEFAULT / ADDON)
  → Tägliche Tool-Verwaltung
  → Governance bei neuen Tools
  → Problem-Solving
  → Best Practices
  → Dokumentation & Kommunikation

Nächstes Dokument:
  → TOOLBAUKASTEN_How2_USER_S6.md (vereinfacht, nicht technisch)


================================================================================
TOOLBAUKASTEN – HOW2 DEV
Status: ALPHA | Datum: 2026-03-21
R+MUNI Blueprint | Erstellt durch EUMAXL + Claude | Basis: TOOLBAUKASTEN_principles_S6.md
================================================================================
