================================================================================
S8-Z1 — Beta 1.0 Release | Repo-Restrukturierung & Doku-Bereinigung — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV-Z1-Beta-1-Release-Besprechung_S8
Tag             : #dev #sprint #s8 #beta10 #repo #associate
Datum           : 2026-03-26
Stage           : S8 — AKTIV
Status          : ENTWURF
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================


================================================================================
1. AUSGANGSLAGE
================================================================================

Auslöser:
  Stage 8 ist eröffnet. S8-Z1 (Beta 1.0 Release) ist das primäre Ziel.
  Voraussetzung für den Release ist eine saubere, strukturell getrennte
  Repo-Landschaft, ein vollständig auf S8 gehobener Dokumentationsstand
  und eine konsequent durchgezogene Associate/DEV-Trennung.

Stand vorher:
  - Dokumente tragen gemischte Stage-Suffixe (_S5, _S6, _S7)
  - USER-Bezeichnung noch aktiv — Associate-Terminologie nicht konsequent
  - Fehlende Associate-Varianten für mehrere Reihen (nur DEV vorhanden)
  - Header nicht überall vollständig (Tags für Obsidian-Filter fehlen teils)
  - Historische Lücken und veraltete Inhalte im Projektfolder vorhanden
  - Kein offizielles versioniertes Release-Paket — nur manuelles ZIP
  - DEV-Inhalte und Release-Inhalte nicht getrennt

Stand danach (Ziel dieses Sprints):
  - Alle Dokumente reviewed, logisch geprüft, Header S8-konform
  - USER → Associate konsequent umbenannt
  - Fehlende Associate-Varianten angelegt (namentlich, Inhalt vorerst ident)
  - Alle Stage-Referenzen auf S8 gehoben
  - Public Repo = Beta 1.0 tauglich (DEV-Inhalte entfernt)
  - Neues R+MUNI DEV Repo aufgebaut (Kopie des S8-Stands)
  - README + Install.txt auf Associate migriert
  - Offizielles GitHub Release v1.0-beta erstellt


================================================================================
2. REPO-STRATEGIE (ENTSCHEID)
================================================================================

Zwei-Phasen-Vorgehen:

  PHASE 1 — Arbeit im Public Repo (bis alles sauber ist)
    Public Repo dient als Arbeitsrepo für die gesamte S8-Bereinigung.
    Neue / geänderte Stände während der Arbeit → NUR in Doku-internal.
    Public Repo enthält während Phase 1 den "in Arbeit"-Stand.

  PHASE 2 — Aufspaltung bei Fertigstellung
    Schritt 1: Kopie des fertigen S8-Stands → neues R+MUNI DEV Repo (public)
    Schritt 2: Alle DEV-Inhalte aus Public Repo entfernen
    Schritt 3: Public Repo = Beta 1.0 Release Stand (sauber, kein DEV-Overhead)
    Schritt 4: Offizielles GitHub Release v1.0-beta erstellen

  Versionsbezeichnung:
    DEV-Welt   → Stage 8 / S8
    Außenwelt  → R+MUNI BETA 1.0 | Tag: v1.0-beta


================================================================================
3. ARBEITSBLÖCKE & REIHENFOLGE
================================================================================

Abhängigkeiten:
  Block A → Block B → Block C → Block D
  Block A und B können parallel bearbeitet werden.
  Block C startet erst wenn A + B freigegeben sind.
  Block D startet erst wenn C abgeschlossen ist.


── BLOCK A — DOKU BEREINIGUNG & ASSOCIATE-MIGRATION ───────────────────────────

Schritt 1 — Inventar erstellen
  Alle Dokumente im Projektfolder erfassen:
    - Dokumentname
    - Typ (principles / how2 / GOV / Sprint / etc.)
    - Variante vorhanden: DEV / Associate / USER / keine
    - Header vollständig (Tag-Feld, alle Pflichtfelder)?
    - Stage-Stand (S5 / S6 / S7)?
  Ergebnis: vollständige Übersicht mit markierten Lücken

Schritt 2 — USER → Associate umbenennen
  Alle Dokumente mit _USER im Namen → _Associate
  Alle internen Referenzen auf USER-Bezeichnung prüfen und anpassen

Schritt 3 — Fehlende Associate-Varianten anlegen
  Für jede Reihe die heute nur DEV hat:
    → Associate-Variante anlegen (namentlich)
    → Inhalt vorerst ident mit DEV — spätere Trennung explizit markieren
  Reihen betroffen: CSV_FLOW, XML_FLOW, M2B_FLOW, ATL_FLOW, HLP,
                    FLOW_SCRIPTRUNNER, CLE, INST, ECM, OBS, TMP
                    (finale Liste aus Schritt 1)

Schritt 4 — Review & Logik-Check je Dokument
  Checkliste je Dokument:
    □ Inhalt inhaltlich korrekt und aktuell?
    □ Widersprüche zu anderen Dokumenten?
    □ Verweise / Obsidian-Links noch gültig?
    □ Keine veralteten Stage-Referenzen (S5/S6/S7 Inhalte die S8 widersprechen)?

Schritt 5 — Header S8-konform bauen
  Standard-Header (Pflichtfelder):
    Projekt, Dokument, Tag, Datum, Stage, Status, Verantwortlich, Review, Jira-Sync
  Tags für Obsidian-Filter: vollständig und konsistent setzen
  Stage-Angabe: auf S8 heben

Schritt 6 — Stage-Referenzen & Suffix auf S8 heben
  Alle Stage-Angaben im Inhalt prüfen und aktualisieren
  Suffix-Regel: DEV-Dokumente tragen _S8
                Public-Dokumente (Beta 1.0) tragen keinen Suffix

Schritt 7 — Historische Lücken & falsche Infos bereinigen
  Konkrete Lücken aus Schritt 1 und 4 adressieren
  Jede Änderung mit kurzem Kommentar im Sprint festhalten


── BLOCK B — README + INSTALL.TXT AUF ASSOCIATE MIGRIEREN ─────────────────────

  Voraussetzung: Block A Schritt 2–3 abgeschlossen
                 (Associate-Terminologie etabliert bevor README umgebaut wird)

  README:
    - Außenperspektive anlegen: verständlich ohne Begleitung
    - Fragen die ein Fremder stellt: Was ist R+MUNI? Was kann es? Wie starte ich?
    - USER-Referenzen → Associate
    - Ehrlichkeit beibehalten (Beta = Beta)
    - Sprache: konsistent, erklärend, kein Insider-Jargon ohne Erklärung

  Install.txt:
    - USER-Referenzen → Associate
    - Inhalt auf S8-Stand prüfen
    - DEV-spezifische Infos bleiben erhalten (kein Verlust)


── BLOCK C — REPO-AUFSPALTUNG ──────────────────────────────────────────────────

  Voraussetzung: Block A + B vollständig abgeschlossen und freigegeben

  Schritt 1: Repo-Kopie-Methode entscheiden (Fork / neues Repo / manuell)
  Schritt 2: Neues R+MUNI DEV Repo erstellen und mit S8-Stand befüllen
  Schritt 3: DEV-Inhalte aus Public Repo entfernen
  Schritt 4: Gegenseitige Verlinkung der Repos im README prüfen
  Schritt 5: Public Repo = Beta 1.0 Stand — finaler Check


── BLOCK D — GITHUB RELEASE ERSTELLEN ──────────────────────────────────────────

  Voraussetzung: Block C abgeschlossen

  Schritt 1: GitHub Release auf Public Repo anlegen (Tag: v1.0-beta)
  Schritt 2: Release-Notes verfassen — kurz, klar, ehrlich
             Was ist Beta 1.0? Was ist drin? Was noch nicht?
  Schritt 3: Download-ZIP aus GitHub Release generieren
  Schritt 4: Abnahme-Check:
             Kann externer Betakunde R+MUNI selbstständig evaluieren?


================================================================================
4. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Zwei-Phasen-Repo-Strategie
  Ergebnis:   Public Repo = Arbeitsrepo für S8 → danach Aufspaltung
  Begründung: Sauberste Trennung — kein halbfertiger öffentlicher Stand
  Auswirkung: Neue Stände während S8 → nur in Doku-internal

Entscheidung: Versionsbezeichnung
  Ergebnis:   DEV = S8 | Release = R+MUNI BETA 1.0 (Tag: v1.0-beta)
  Begründung: Klare Trennung DEV-Welt vs. Außenwelt
  Auswirkung: Stage-Suffixe entfallen im Public Repo nach Bereinigung

Entscheidung: USER → Associate
  Ergebnis:   USER-Bezeichnung wird vollständig durch Associate ersetzt
  Begründung: Associate = definierte Zielgruppe (Anwender ohne techn. Vorwissen)
              USER war intern und unscharf — Associate ist extern kommunizierbar
  Auswirkung: Alle Dokumente, Templates, Referenzen betroffen

Entscheidung: Associate-Varianten für alle Reihen
  Ergebnis:   Alle Reihen bekommen Associate + DEV Variante
              Inhalt vorerst ident — Trennung in Stage 1
  Begründung: Vollständigkeit für Beta 1.0 — kein blinder Fleck
  Auswirkung: Mehrere neue Dokumente entstehen (namentlich, Inhalt ident)

Entscheidung: Header-Standard S8
  Ergebnis:   Pflichtfelder: Projekt, Dokument, Tag, Datum, Stage, Status,
              Verantwortlich, Review, Jira-Sync
              Tags vollständig für Obsidian-Filter
  Begründung: In S7 erarbeitet — konsequente Umsetzung in S8
  Auswirkung: Alle bestehenden Dokumente werden auf Standard gehoben

Entscheidung: Rückkopplungsschutz
  Ergebnis:   Stage-3/4/5/6/7-Scripts bleiben read-only — kein Eingriff
  Begründung: GOV-konform, Rückkopplungsschutz Stage 8
  Auswirkung: Bereinigung betrifft nur Dokumentation — keine Scripts


================================================================================
5. OFFENE PUNKTE
================================================================================

| Punkt | Status | Nächste Aktion |
|-------|--------|----------------|
| Inventar aller Dokumente erstellen | offen | Block A Schritt 1 — Start |
| Finale Liste betroffener Reihen (fehlende Associate) | offen | aus Inventar |
| Repo-Kopie-Methode entscheiden | offen | Block C vorbereiten |
| Release-Notes Inhalt definieren | offen | Block D |


================================================================================
6. ABGRENZUNG
================================================================================

In diesem Sprint:
  ✓ Inventar + Review aller Dokumente
  ✓ USER → Associate Migration
  ✓ Fehlende Associate-Varianten anlegen
  ✓ Header S8-konform, Tags vollständig
  ✓ Alle Docs auf S8 gehoben
  ✓ README + Install.txt auf Associate migriert
  ✓ Repo-Aufspaltung durchführen
  ✓ GitHub Release v1.0-beta erstellen

Nicht in diesem Sprint:
  ✗ Kommunikationstexte für Außen (→ S8-Z2)
  ✗ Onboarding-Materialien überarbeiten (→ S8-Z3)
  ✗ AI-Driven Methodik Update (→ S8-Z4)
  ✗ BKO1-Offboarding Doku (→ S8-Z5)
  ✗ Associate-Inhalte von DEV inhaltlich trennen (→ Stage 1)
  ✗ Neue Scripts oder Features
  ✗ GOV-Umbauten


================================================================================
BEZÜGE
================================================================================
[[STAGE8_ZIELE_S8]]               S8-Z1 Zieldefinition
[[GOV_Global_S6]]                 Normative Grundlage
[[TMP_principles_S6]]             Repo-Logik, Suffix-Regel, Freigabe-Prozess
[[BETA_GitHub_Nutzung_S5]]        Zwei-Repository-Prinzip
[[AI_DRIVEN_DEV_METHODE_S8]]      Methodik-Basis für S8
[[FREEZE-7_S7]]                   Ausgangszustand für Stage 8
[[ASSOCIATE_principles_Template_S8]]  Associate Zielgruppen-Definition
[[ASSOCIATE_How2_Template_S7]]    Associate Template-Basis


================================================================================
Sprint-DEV-Z1-Beta-1-Release-Besprechung_S8 | DEV | S8 | 2026-03-26 | R+MUNI Blueprint
Status: ENTWURF — Freigabe durch EUMAXL ausstehend
================================================================================
