================================================================================
INST – INSTALLATION & WERKZEUGKASTEN — HOW2 (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : INST_How2_DEV_S8
Tag             : #dev #how2 #inst #installation #s8
Datum           : 2026-03-26
Stage           : S8 — AKTIV
Status          : ENTWURF
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Hinweis         : Neu angelegt S8 — kein DEV-Gegenstück aus früheren Stages vorhanden
                  Operative Details → Install.txt | Konzept → INST_principles_S5
================================================================================


VORAUSSETZUNGEN
--------------------------------------------------------------------------------
- [[INST_principles_S5]] gelesen — Werkzeugkasten-Prinzip verstanden
- [[TOOLBAUKASTEN_principles_S6]] bekannt — Tier-Stufen bekannt
- Install.txt vorhanden und aktuell


================================================================================
1. ZWECK DIESES DOKUMENTS
================================================================================

Dieses Dokument ist die DEV-seitige Referenz für den Installations- und
Einrichtungsprozess von R+MUNI. Es ergänzt Install.txt um DEV-spezifische
Hintergründe, Entscheidungslogik und Troubleshooting.

Abgrenzung:
  - Schritt-für-Schritt Installation für Associate → [[INST_How2_Associate_S8]]
  - Werkzeugkasten-Konzept → [[TOOLBAUKASTEN_principles_S6]]
  - Konkrete Installationsschritte → Install.txt


================================================================================
2. INSTALLATIONS-TIERS IM DEV-ÜBERBLICK
================================================================================

2.1 Tier-Struktur
------------------
MINIMAL   Kern — Python 3, Archi 5.8, Camunda Modeler
          Ausreichend für Grundbetrieb ohne Atlassian-Integration

DEFAULT   Vollständiger Betrieb — MINIMAL + Git, GitHub, Obsidian,
          draw.io, Inkscape, PowerShell 7, Claude Pro, KeePass,
          Notepad++, Projektfolder

ADDON     DEV-only — Atlassian Jira + Confluence (Free Plan)
          Nur wenn Ticketing und Sprint-Verwaltung benötigt

Entscheidungsregel:
  Associate startet mit DEFAULT.
  ADDON nur auf expliziten Wunsch und nach Kapazitätsprüfung.


2.2 root.cfg — einzige Konfigurationsdatei
-------------------------------------------
root.cfg liegt im Blueprint Root.
Einzige Zeile die anzupassen ist: <rootfolder>=<Pfad>

Alle Scripts lesen ihren Pfad aus root.cfg — kein hardcoded Pfad
in irgendeinem Script. Wird root.cfg falsch gesetzt, scheitern alle Scripts.

DEV-Regel: Vor jedem Testlauf root.cfg prüfen.


================================================================================
3. TYPISCHE FEHLERBILDER BEI INSTALLATION
================================================================================

FEHLER: Python nicht im PATH
  → Scripts starten nicht, PowerShell zeigt "nicht erkannt"
  → Lösung: Python-Installation mit "Add to PATH" Option wiederholen

FEHLER: root.cfg falsch gesetzt (Leerzeichen, falscher Pfad)
  → Alle Scripts scheitern mit Pfadfehler
  → Lösung: root.cfg in Notepad++ öffnen, Pfad ohne Anführungszeichen,
            ohne abschließenden Backslash

FEHLER: Archi-Version falsch
  → Importfehler bei ArchiMate-Dateien
  → Lösung: Archi 5.8 verwenden — andere Versionen nicht getestet

FEHLER: Git nicht installiert bei DEFAULT-Setup
  → GitHub-Sync nicht möglich
  → Lösung: Git for Windows installieren, danach PowerShell neu starten


================================================================================
4. ABLAUF NEUES ASSOCIATE-SETUP (DEV-PERSPEKTIVE)
================================================================================

  Schritt 1: Install.txt an Associate übergeben
  Schritt 2: Associate führt Installation selbst durch
  Schritt 3: Funktionstest — Associate bestätigt grünen Stand
  Schritt 4: root.cfg-Pfad prüfen (häufigster Fehlerort)
  Schritt 5: Ersten Script-Lauf begleiten (optional, bei Bedarf)

Regel: Kein mündliches Handhalt — Install.txt muss selbsterklärend sein.
       Ist das nicht der Fall → Install.txt verbessern, nicht mehr erklären.


================================================================================
SUPPORT UND FEEDBACK
================================================================================

→ Ticketsystem: https://ims-blueprint-ticketsystem.atlassian.net/helpcenter/RMNP/


================================================================================
INST_How2 | DEV | S8 | 2026-03-26 | R+MUNI Blueprint
================================================================================
