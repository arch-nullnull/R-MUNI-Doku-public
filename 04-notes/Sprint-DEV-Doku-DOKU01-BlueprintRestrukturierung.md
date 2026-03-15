================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt            : R+MUNI Blueprint
Sprint-Bezeichnung : SPRINT-DOKU01-BlueprintRestrukturierung
Datum              : 2026-03-12
Stage              : 5 (aktiv)
Status             : Dev-Dokumentation (nicht auditpflichtig per GOV 10.8)
Erstellt durch     : EUMAXL + Claude (Pair-Session)
Vorgänger-Sprint   : SPRINT-RMNP01-PortalSetup (2026-03-09)
================================================================================


--------------------------------------------------------------------------------
1. STAGE-KONTEXT UND SPRINT-BEGRÜNDUNG
--------------------------------------------------------------------------------

1.1 Stage-Modell (Ist-Zustand)
-------------------------------
Stage 3  FREEZE
         Stage 3 ist eingefroren. Änderungen ausschließlich für Bugfixing
         zulässig. Neue Features sind in Stage 3 nicht erlaubt.

Stage 4  FREEZE
         Stage 4 ist eingefroren. Alle Scripts und Logik read-only.
         Kein Eingriff zulässig außer explizit freigegebene Bugfixes.

Stage 5  AKTIV
         Erste Außenwirkungsphase. Realer Betrieb, Kundenkontakt,
         Ökosystem-Aufbau. Erweiterungen additiv, kein Eingriff in S3/S4.

1.2 Auslöser (gemäß GOV 10.3 / 10.5)
---------------------------------------
Auslöser-Typ : Architekturentscheid + Feature-Zuwachs (Stage-5-Ziel)

Vorgeschichte:  Im Blueprint lagen bisher zwei Ordner (00-concept und
                04-notes) die fachliche Dokumentation enthielten —
                Principles, How2-Guides, Sprint-Dokus, Governance.
                Diese Inhalte sind keine technischen Betriebsartefakte
                und werden von keinem Script gelesen oder referenziert.
                Sie gehören konzeptionell nicht in das Betriebssystem.

                Gleichzeitig entstand der Bedarf nach einer klaren
                intern/extern Trennung für Kundenprojekte — mit einem
                wiederholbaren Muster das für jeden Kunden identisch
                angewendet werden kann.

Entscheidung:   1. Blueprint wird auf reines Betriebssystem reduziert.
                   00-concept und 04-notes werden entfernt.
                2. Neuer eigenständiger Bereich C:\R+MUNI-Doku wird
                   aufgebaut mit drei Bereichen: Internal, Public, Creative.
                3. GitHub-Struktur wird als wiederholbares Kundenmuster
                   etabliert: ein public Repo für alle, ein private Repo
                   pro Kunde / pro EUMAXL.


--------------------------------------------------------------------------------
2. ZIELDEFINITION (gemäß GOV 10.6)
--------------------------------------------------------------------------------

Ziel 1 — Blueprint aufräumen
  00-concept und 04-notes aus C:\R+MUNI entfernen.
  structure.txt via HLP08 neu generieren.
  Install.txt manuell anpassen (Ablageort-Referenzen entfernen).

  Überprüfbar : Blueprint enthält keine Doku-Ordner mehr.
                HLP08 läuft fehlerfrei durch.
                CSV00 läuft fehlerfrei durch (Funktionstest).

Ziel 2 — R+MUNI-Doku Struktur aufbauen
  C:\R+MUNI-Doku anlegen mit drei Unterordnern:
    Internal  → fachliches Wissen, Entscheidungen, Sprint-Dokus (privat)
    Public    → aufbereitete Dokumentation für alle (öffentlich)
    Creative  → Roadmap, Geschäftsmodell, Ideen (nur lokal, kein GitHub)
  Obsidian pro Unterordner als Vault einrichten.
  .gitignore pro Unterordner für .obsidian/ anlegen.

  Überprüfbar : Ordnerstruktur vorhanden.
                Obsidian öffnet alle drei Vaults fehlerfrei.
                .obsidian/ erscheint nicht im GitHub Commit.

Ziel 3 — GitHub Repos anlegen
  EUMAXL/rmuni-docs-internal  → private repo
  EUMAXL/rmuni-docs-public    → public repo
  Lokale Verknüpfung beider Repos einrichten.

  Überprüfbar : Beide Repos auf GitHub vorhanden.
                git push in beide Repos erfolgreich.

Ziel 4 — Inhalte migrieren
  Bestehende Dateien aus 00-concept und 04-notes in die
  richtigen Bereiche von R+MUNI-Doku verschieben.
  Keine Datei geht verloren — alles wandert, nichts wird gelöscht.

  Überprüfbar : Alle Dateien aus 00-concept und 04-notes
                sind in R+MUNI-Doku auffindbar.

Abgrenzung:
  - Kein Eingriff in Stage 3 oder Stage 4 Scripts
  - Kein Eingriff in 01-model, 02-artifacts, 03-stages
  - root.txt bleibt unverändert
  - README.md im Blueprint Root bleibt unverändert
  - Creative-Bereich erhält kein GitHub Repo (bewusst, nur lokal)


--------------------------------------------------------------------------------
3. ARCHITEKTURENTSCHEID — TRENNUNG BETRIEB UND WISSEN
--------------------------------------------------------------------------------

3.1 Blueprint als reines Betriebssystem
-----------------------------------------
Entscheidung : C:\R+MUNI enthält ausschließlich technische Artefakte
               die für den Script-Betrieb notwendig sind.
               Fachliche Dokumentation gehört nicht in den Blueprint.

Begründung   : Kein Script referenziert 00-concept oder 04-notes.
               Die Ablageort-Angaben in den Doku-Dateien selbst
               (z.B. "Ablageort: 00-concept/02-how2/...") sind
               reine Metadaten — kein technischer Pfad.
               Trennung erhöht Klarheit und reduziert Komplexität
               für neue Nutzer die den Blueprint installieren.

Auswirkung   : structure.txt muss neu generiert werden (via HLP08).
               Install.txt muss manuell angepasst werden.
               Kein Script-Eingriff, kein Funktionsverlust.

3.2 Wiederholbares Kundenmuster via GitHub
-------------------------------------------
Entscheidung : Die GitHub-Struktur wird als standardisiertes Muster
               etabliert das für jeden Kunden identisch angewendet wird.

               EUMAXL/rmuni-docs-public    → einmal, für alle gleich
               EUMAXL/rmuni-docs-internal  → EUMAXL-eigenes Wissen
               EUMAXL/rmuni-docs-[kunde]   → pro Kunde ein eigenes
                                             private Repo, selbe Struktur

Begründung   : Public Repo ist der kostenfreie Unterbau — einmal gebaut,
               von jedem Kunden "mountbar". Internal variiert pro Kunde.
               Struktur ist das Produkt, nicht nur der Inhalt.
               Kein Mehraufwand bei neuem Kunden — Muster ist bekannt.

3.3 Obsidian als Wissens-Linse
--------------------------------
Entscheidung : Obsidian wird pro Unterordner als eigener Vault eingerichtet.
               Der .obsidian/ Konfigurationsordner wird via .gitignore
               aus allen Repos ausgeschlossen.

Begründung   : Obsidian liest bestehende .txt Dateien ohne Strukturänderung.
               Kein zweites System — nur eine andere Ansicht auf denselben
               Inhalt. Verlinkung, Suche und Graph-View als Mehrwert.
               .gitignore-Ausschluss verhindert Tool-spezifische Artefakte
               im Repo (Obsidian-Einstellungen sind nicht projektrelevant).

3.4 Creative ohne GitHub
--------------------------
Entscheidung : Der Creative-Bereich erhält kein GitHub Repo.
               Inhalte bleiben ausschließlich lokal.

Begründung   : Roadmap, Geschäftsmodell und Ideen sind persönlicher
               Denkraum ohne Versionierungsbedarf für Außenwirkung.
               Keine Backup-Notwendigkeit via GitHub — lokales Backup
               (z.B. HLP06) ist ausreichend.


--------------------------------------------------------------------------------
4. DATEI-INVENTAR UND MASSNAHMEN
--------------------------------------------------------------------------------

4.1 Zu entfernende Ordner aus C:\R+MUNI
-----------------------------------------

00-concept/                    ENTFERNEN  → Inhalt wandert nach R+MUNI-Doku
  00-governance/
    Global_GOV.txt             → R+MUNI-Doku/Internal/
  01-principles/
    AI_DRIVEN_DEV_METHODE.txt  → R+MUNI-Doku/Internal/
    ATL_FLOW_principles_S4.txt → R+MUNI-Doku/Internal/
    CSV_FLOW_principles_S3.txt → R+MUNI-Doku/Internal/
    FLOW_SCRIPTRUNNER_principles_S4.txt  → R+MUNI-Doku/Internal/
    HLP_principles_S3.txt      → R+MUNI-Doku/Internal/
    M2B_FLOW_principles_S3.txt → R+MUNI-Doku/Internal/
    SCRIPT-BAUKASTEN.txt       → R+MUNI-Doku/Internal/
    XML_FLOW_principles_S3.txt → R+MUNI-Doku/Internal/
  02-how2/
    ATL_FLOW_How2_S4.txt       → R+MUNI-Doku/Public/
    CSV_FLOW_How2_S3.txt       → R+MUNI-Doku/Public/
    FLOW_SCRIPTRUNNER_How2_S4.txt  → R+MUNI-Doku/Public/
    HLP09_How2_S4.txt          → R+MUNI-Doku/Public/
    HLP_How2_S3.txt            → R+MUNI-Doku/Public/
    M2B_FLOW_How2_S3.txt       → R+MUNI-Doku/Public/
    XML_FLOW_How2_S3.txt       → R+MUNI-Doku/Public/
  03-rosetta_stone/
    Rosetta_Stone_Block1_Views.txt         → R+MUNI-Doku/Public/
    Rosetta_Stone_Block2_Artifacts_Scripts.txt → R+MUNI-Doku/Public/
    Rosetta_Stone_Block3_Begriffe_Konzepte.txt → R+MUNI-Doku/Public/
    Rosetta_Stone_Block4_Stage4_Ablauf.txt → R+MUNI-Doku/Public/

04-notes/                      ENTFERNEN  → Inhalt wandert nach R+MUNI-Doku
  Sprint-DEV-Doku-*.txt        → R+MUNI-Doku/Internal/
  STAGE3_FREEZE.txt            → R+MUNI-Doku/Internal/
  STAGE4_FREEZE.txt            → R+MUNI-Doku/Internal/
  STAGE5_ZIELE.txt             → R+MUNI-Doku/Internal/
  ATL_CSV_Konfig_Jira_Mapping.txt → R+MUNI-Doku/Internal/

4.2 Anzupassende Dateien in C:\R+MUNI
---------------------------------------

structure.txt
  Aktion   : NEU GENERIEREN via HLP08 nach Entfernen der Ordner
  Hinweis  : HLP08_structure2csv.py liest structure.txt als Input —
             nach Neugenerierung stimmt der Stand wieder.

Install.txt
  Aktion   : MANUELL ANPASSEN in Notepad++
  Änderung : Zeile "Ablageort: 00-concept/Install.txt" im Header
             entfernen oder auf neuen Ablageort anpassen.
             Alle Verweise auf 00-concept und 04-notes prüfen
             und entfernen.

4.3 Neue Struktur C:\R+MUNI-Doku
----------------------------------

R+MUNI-Doku/
  Internal/
    .gitignore          (enthält: .obsidian/)
    [migrierte Dateien aus 00-concept/00-governance]
    [migrierte Dateien aus 00-concept/01-principles]
    [migrierte Dateien aus 04-notes]
  Public/
    .gitignore          (enthält: .obsidian/)
    [migrierte Dateien aus 00-concept/02-how2]
    [migrierte Dateien aus 00-concept/03-rosetta_stone]
  Creative/
    .gitignore          (enthält: .obsidian/)
    [neue Inhalte: Roadmap, Geschäftsmodell, Ideen]

4.4 Neue GitHub Repos (EUMAXL)
--------------------------------

rmuni-docs-internal
  Typ      : private
  Inhalt   : R+MUNI-Doku/Internal/
  Zweck    : EUMAXL-eigenes Wissen, Sprint-Dokus, Entscheidungen

rmuni-docs-public
  Typ      : public
  Inhalt   : R+MUNI-Doku/Public/
  Zweck    : Aufbereitete Doku für alle — How2, Rosetta Stone, Guides
  Hinweis  : Wird von Kunden "gemountet" — bleibt für alle gleich

rmuni-docs-[kunde]  (Muster für Kundenprojekte)
  Typ      : private
  Inhalt   : Kundeneigene Internal-Struktur (selbes Muster)
  Zweck    : Kundenspezifisches Wissen, separiert von EUMAXL-internem


--------------------------------------------------------------------------------
5. SCHRITT-FÜR-SCHRITT AUSFÜHRUNG
--------------------------------------------------------------------------------

PHASE 1 — Vorbereitung (vor allen Änderungen)
  [ ] Backup des gesamten C:\R+MUNI via HLP06 erstellen
  [ ] Backup von C:\R+MUNI-Doku falls bereits vorhanden

PHASE 2 — R+MUNI-Doku Struktur anlegen
  [ ] C:\R+MUNI-Doku anlegen
  [ ] Unterordner Internal, Public, Creative anlegen
  [ ] .gitignore pro Unterordner anlegen (Inhalt: .obsidian/)
  [ ] Obsidian: jeden Unterordner als Vault öffnen ("Open folder as vault")
      → .obsidian/ wird automatisch angelegt

PHASE 3 — Inhalte migrieren (gemäß Datei-Inventar 4.1)
  [ ] Dateien aus 00-concept/00-governance → Internal/
  [ ] Dateien aus 00-concept/01-principles → Internal/
  [ ] Dateien aus 00-concept/02-how2       → Public/
  [ ] Dateien aus 00-concept/03-rosetta_stone → Public/
  [ ] Dateien aus 04-notes/                → Internal/
  [ ] Prüfen: alle Dateien angekommen, keine fehlt

PHASE 4 — Blueprint bereinigen
  [ ] 00-concept/ aus C:\R+MUNI löschen
  [ ] 04-notes/   aus C:\R+MUNI löschen
  [ ] Install.txt in Notepad++ anpassen (Ablageort-Zeile)
  [ ] HLP08 ausführen → structure.txt wird neu generiert
  [ ] CSV00 ausführen → Funktionstest Blueprint

PHASE 5 — GitHub einrichten
  [ ] EUMAXL/rmuni-docs-internal auf GitHub anlegen (private)
  [ ] EUMAXL/rmuni-docs-public   auf GitHub anlegen (public)
  [ ] Lokal: git init in R+MUNI-Doku/Internal/
             git remote add origin [URL rmuni-docs-internal]
             git push
  [ ] Lokal: git init in R+MUNI-Doku/Public/
             git remote add origin [URL rmuni-docs-public]
             git push
  [ ] Prüfen: .obsidian/ ist NICHT im Commit enthalten

PHASE 6 — Abschlusscheck
  [ ] Blueprint: CSV00 läuft fehlerfrei
  [ ] Blueprint: HLP08 läuft fehlerfrei
  [ ] structure.txt spiegelt neue Struktur korrekt
  [ ] R+MUNI-Doku: alle Dateien in Obsidian sichtbar und verlinkbar
  [ ] GitHub: beide Repos vorhanden und aktuell


--------------------------------------------------------------------------------
6. OFFENE PUNKTE / NEXT STEPS
--------------------------------------------------------------------------------

6.1 Install.txt inhaltlich überarbeiten
-----------------------------------------
Status   : Offen (nach Phase 4)
Aktion   : Install.txt nicht nur bereinigen sondern prüfen ob der
           Hinweis auf R+MUNI-Doku als eigenständigen Bereich
           ergänzt werden soll — für neue Blueprint-Nutzer hilfreich.

6.2 Obsidian Verlinkung aufbauen
----------------------------------
Status   : Offen (iterativ nach Migration)
Aktion   : In Obsidian Internal und Public schrittweise Verlinkungen
           zwischen Dokumenten aufbauen. Kein Pflichtschritt für
           den Sprint — kann iterativ erfolgen.

6.3 Kundenmuster dokumentieren
--------------------------------
Status   : Offen (eigener Sprint)
Aktion   : Das Muster rmuni-docs-[kunde] in einer eigenen
           Schritt-für-Schritt Anleitung dokumentieren damit
           der Onboarding-Prozess für neue Kunden standardisiert ist.

6.4 Stage-Ende Dokumentation
------------------------------
Status   : Ausstehend (gemäß GOV 10.9 verpflichtend zum Stage-Ende)
Aktion   : Diese Dev-Dokumentation ist nicht auditpflichtig (GOV 10.8).
           Zum Stage-Ende ist eine vollständige, governance-konforme
           Dokumentation zu erstellen.


--------------------------------------------------------------------------------
7. GOVERNANCE-KONFORMITÄTSCHECK
--------------------------------------------------------------------------------

GOV 10.3  Zulässiger Auslöser        OK  Architekturentscheid + Stage-5-Ziel
GOV 10.5  Fachlicher Mehrwert        OK  Klare intern/extern Trennung,
                                         wiederholbares Kundenmuster,
                                         Blueprint auf Betrieb reduziert
GOV 10.5  Keine implizite Gov-Änd.   OK  Kein Eingriff in Scripts oder Flows
GOV 10.6  Ziel explizit definiert    OK  Abschnitt 2 (4 Ziele)
GOV 10.6  Ziel überprüfbar           OK  Prüfkriterien je Ziel definiert
GOV 10.7  Zwischenschritte           OK  Normativ zugelassen (Phase 1–6)
GOV 10.8  Dev-Doku erstellt          OK  Dieses Dokument
GOV 10.9  Stage-Ende Doku            OFFEN  Verpflichtend bei Stage-Abschluss
GOV 10.10 Keine Gov-Regel aufgehoben OK  Naming-Convention und Blueprint-
                                         Struktur vollständig eingehalten
GOV 10.5  Keine Architekturabw.      OK  Additiv, kein Eingriff in S3/S4,
                                         kein Script-Eingriff


================================================================================
END OF SPRINT DEV-DOKUMENTATION
SPRINT-DOKU01-BlueprintRestrukturierung | Stage 5 | 2026-03-12
================================================================================
