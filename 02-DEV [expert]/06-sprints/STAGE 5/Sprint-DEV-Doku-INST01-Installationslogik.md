================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt             : R+MUNI Blueprint
Sprint-Bezeichnung  : SPRINT-INST01-Installationslogik — Werkzeugkasten & Setup
Datum               : 2026-03-17
Stage               : 5 (aktiv)
Status              : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch      : Entwickler + Claude (Pair-Session)
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Livebetrieb-Erkenntnis (Stage-5-Ziel 4.3 Bugfixing & Optimierung)

Begründung   : Erster realer Beta-Rollout hat strukturelle Schwächen in der
               Installationsroutine aufgedeckt:
                 - GitHub ZIP benennt Ordner zu R-MUNI um (Namenskonflikt)
                 - Repo-Clone für Kunden nicht zielführend
                 - Ordnerstruktur für Entwickler und Endkunde nicht getrennt
                 - Install.txt beschreibt nur Entwickler-Usecase, kein Kunde
                 - Kein Setup-Script für Ordneranlage vorhanden
                 - Tool-Liste ohne Pflicht/Optional Unterscheidung
                 - Git-Zweck nicht dokumentiert

               Diese Erkenntnisse machen eine strukturierte Überarbeitung der
               Installationslogik notwendig — noch in Stage 5 wegen
               Außenwirkung und aktivem Tester-Betrieb.

Fachlicher   : Verirrter Tester scheitert nicht mehr an der Installation.
Mehrwert       Klare Trennung Entwickler vs. Endkunde.
               Werkzeugkasten-Prinzip als wiederverwendbare Grundlage
               für spätere vollständige Installer-Lösung (INST01 Backlog).


1.2 Abgrenzung
---------------
Dieser Sprint ist KEIN vollständiger Installer-Sprint.
Der vollständige INST01 (Packaging, Varianten, GitHub Release) bleibt
im Backlog und startet erst bei Stage 7-8 wenn breiterer Rollout ansteht.

Dieser Sprint liefert:
  - Werkzeugkasten-Prinzip dokumentiert (Principles)
  - Ordnerstruktur-Script (Dir_Setup.bat)
  - Install.txt überarbeitet (Minimal / Default / Addon)

Dieser Sprint liefert NICHT:
  - Fertiges Installer-Paket
  - requirements_minimal.txt / requirements_full.txt
  - Vollständiges GitHub Playbook
  - GOV_Kunde Vorlage


--------------------------------------------------------------------------------
2. ERKENNTNISSE AUS DEM BETA-ROLLOUT
--------------------------------------------------------------------------------

2.1 GitHub Namens-Problem
--------------------------
GitHub ZIP entpackt Ordner mit R-MUNI statt R+MUNI.
Repo-Clone verbindet Kunden mit falschem Repo und falschem Namen.

Lösung: Dir_Setup.bat legt Ordner direkt mit korrektem Namen an.
        Kürzel-Suffix verhindert GitHub-Namenskonflikt dauerhaft.
        ZIP-Inhalt wird in bereits vorhandene Ordner entpackt.


2.2 Zwei Usecases — eine Install.txt
--------------------------------------
Die bisherige Install.txt kannte nur den Entwickler-Usecase.
Endkunde hat andere Anforderungen:
  - Kein GitHub nötig (hat Confluence/Jira)
  - Weniger Tools, keine Entwickler-Addons
  - Andere Ordnerstruktur (kein Doku-internal, kein Doku-public)

Lösung: Install.txt mit Minimal / Default / Addon Logik.
        Endkunde liest bis Default und hört auf.
        Entwickler liest alles.


2.3 Installation ist Phase A des Onboardings
---------------------------------------------
Erkenntnis aus dem Rollout: Bei der Installation werden bereits
strukturelle Entscheide getroffen die sofort in GOV_Kunde einfließen müssen
(Kürzel, Pfad, GitHub ja/nein, Doku-Option).

Konsequenz: Install.txt führt durch diese Entscheide.
            Dir_Setup.bat macht sie operativ.
            GOV_Kunde Vorlage folgt in INST01 Backlog.


2.4 Werkzeugkasten-Prinzip
---------------------------
Aus den Rollout-Erkenntnissen wurde das Baum-Modell entwickelt:
  Stamm    → absoluter Kern, jeder, immer
  Äste     → tragende Options-Entscheide pro Achse
  Addons   → additiv, kombinierbar
  Exitpoints → werden eigenständig, Mutterbaum darf wegfallen

Dieses Prinzip ist jetzt in INST_principles_S5.md fixiert und
gilt als Grundlage für den vollständigen INST01 Sprint.


--------------------------------------------------------------------------------
3. DELIVERABLES DIESES SPRINTS
--------------------------------------------------------------------------------

3.1 INST_principles_S5.md (NEU)
---------------------------------
  Ablage  : R+MUNI Doku-public\01-principles\INST_principles_S5.md
  Inhalt  : Werkzeugkasten/Baum-Prinzip, Core vs. Addon Abgrenzungsregeln,
            Entwickler vs. Endkunde, Git vs. GitHub Begriffsklarheit,
            Exitpoint-Prinzip
  Status  : Fertig, abgelegt


3.2 Dir_Setup.bat (NEU)
------------------------
  Ablage  : R+MUNI <KUERZEL>\ (Blueprint Root)
  Inhalt  : PowerShell-freies BAT-Script, Doppelklick-fähig
            Fragt Installationsordner (Standard C:\Prototyping)
            und Kürzel (max. 4 Zeichen) ab
            Legt vollständige R+MUNI Ordnerstruktur an inkl.
            innerer Blueprint-Struktur (00-model, 01-artifacts, 02-stages)
            R+MUNI Apps wird NICHT angelegt (manuelle Tool-Installation)
  Status  : Fertig, getestet


3.3 Install.txt (ÜBERARBEITET)
--------------------------------
  Ablage  : R+MUNI <KUERZEL>\Install.txt
  Änderungen gegenüber Vorversion:
    - Struktur neu: Minimal / Default R+MUNI Setup / Addon
    - Schnellstart ganz oben
    - Kürzel-Logik in Verzeichnisübersicht dokumentiert
    - root.txt → root.cfg korrigiert
    - Ordnernummern 00/01/02 korrigiert
    - Dir_Setup.bat als erster Schritt
    - coArchi von Pflicht zu Addon verschoben (HLP06/07 ist lokale Alternative)
    - excelArchi + lightboxArchi als Addon gekennzeichnet
    - Notepad++ Plugins: kein Installer-Ordner mehr, nur Plugin Admin
      Ausnahme JSTool dokumentiert (nicht immer im Plugin Admin verfügbar)
    - Git-Zweck geklärt und dokumentiert (3 Funktionen)
    - AI-Modelle nach Office-Analogie strukturiert
    - Linux/macOS: ehrlich als nicht getestet markiert, Tester eingeladen
    - Exitpoints in Abschnitt 6 mit Verweis auf Principles
    - Versionshinweise bereinigt
  Status  : Fertig, abgelegt


3.4 Sprint-DEV-Doku-INST01 Backlog (AKTUALISIERT)
---------------------------------------------------
  Ablage  : R+MUNI Doku-internal\backlog\
  Inhalt  : Scope erweitert, Beta-Rollout Erkenntnisse dokumentiert,
            offene Tasks ergänzt, Git-Zweck als geklärt markiert,
            Timing auf Stage 7-8 gesetzt
  Status  : Fertig, abgelegt


--------------------------------------------------------------------------------
4. OFFENE PUNKTE → INST01 BACKLOG
--------------------------------------------------------------------------------

Folgende Punkte wurden erkannt aber bewusst zurückgestellt:

  - Vollständiger Werkzeugkasten mit allen Achsen ausarbeiten
  - GitHub Playbook (Namensregeln, Repo-Anlage, .gitignore)
  - GOV_Kunde Vorlage für Phase A Onboarding
  - requirements_minimal.txt + requirements_full.txt
  - Installer-Paket / GitHub Release (ab Beta 1.0)
  - Bash-Script für Linux (langfristig → Docker / Appliance löst das elegant)
  - O365 Eco System Integration (geplant, noch nicht implementiert)

Alle Punkte sind im Backlog-Dokument als Tasks erfasst.


--------------------------------------------------------------------------------
5. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Livebetrieb-Erkenntnis, Stage-5-Ziel 4.3
GOV 10.5  Fachlicher Mehrwert        OK  Tester-taugliche Installation
GOV 10.5  Keine implizite Gov-Änd.   OK  Kein Eingriff in Script-Kernlogik
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 1
GOV 10.6  Ziel überprüfbar           OK  3 Deliverables fertig und abgelegt
GOV 10.7  Zwischenschritte           OK  Pair-Session dokumentiert
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Additiv, keine Logikänderung
Stage 5   Rückkopplungsschutz        OK  Stage-3/4-Logik vollständig unverändert


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-INST01-Installationslogik | Stage 5 | 2026-03-17
R+MUNI Blueprint | Erstellt durch: Entwickler + Claude (Pair-Session)
================================================================================
