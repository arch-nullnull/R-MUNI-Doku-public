================================================================================
SPRINT-DEV-DOKUMENTATION — R+MUNI BLUEPRINT
Sprint-DEV-S101-DEV-TMPL-RESYNC
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV-S101-DEV-TMPL-RESYNC
Tag             : #sprint #dev #templates #resync #s101
Datum           : 2026-03-29
Stage           : S1.01 — AKTIV
Status          : OFFEN
Auslöser        : GOV 10.3 — Strukturbereinigung / Entwicklerwunsch
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN
Erstellt durch  : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
1. AUSGANGSLAGE
================================================================================

In Stage 8 wurden die USER-Dokumente zu ASSOCIATE-Dokumenten migriert.
Fehlende ASSOCIATE-Varianten wurden aus bestehenden DEV-Dokumenten abgeleitet —
DEV-spezifische Inhalte wurden dabei entfernt (Entkernungslogik).

Ergebnis: Die ASSOCIATE-Welt ist vollständig und korrekt. ✓
Problem:  Die DEV-Welt verlor dabei ihre eigenständige Vollständigkeit.
          DEV-Templates existieren teils nur noch in verwässerter Form
          oder basieren auf dem Associate-Stand statt auf dem DEV-Stand.

Der letzte vollständige DEV-Stand liegt verteilt in Stage 7 und früheren Stages.
Betroffen sind alle zentralen Dokumenttypen:
  - principles (DEV-Variante)
  - how2 (DEV-Variante)
  - sprint (DEV-Variante)
  - GOV-Ergänzungen
  - Templates generell


================================================================================
2. ZIEL
================================================================================

Vollständige DEV-Dokumentumgebung wiederherstellen — parallel zur
bestehenden ASSOCIATE-Welt, ohne diese anzutasten.

Methode: Rückgriff auf pre-S8 DEV-Dokumente (letzter bekannter vollständiger
Stand) → Anreicherung auf S8-Standard (Header, Bezeichnungen, GOV-Ankerpunkte).

Grundsatz: NUR ADDITIV.
  - Kein Inhalt wird reduziert oder vereinfacht
  - DEV-Schärfe, GOV-Tiefe, technische Präzision bleiben erhalten
  - S8-Anreicherungen (Header-Standard, Associate-Terminologie wo passend,
    Stage-1-Referenzen) werden addiert — nie subtrahiert
  - ASSOCIATE-Dokumente bleiben unverändert


================================================================================
3. ABGRENZUNG
================================================================================

IN SCOPE:
  ✓ DEV-Varianten der fünf Dokumenttypen: principles, how2, sprint,
    GOV-Ergänzungen, Templates
  ✓ Suchlogik: letzter unentkerter Stand in DEV Repo (S7 oder früher)
  ✓ Header auf S8/S101-Standard bringen
  ✓ Inhaltlicher Abgleich: S8-Erkenntnisse addieren wo DEV-relevant
  ✓ Neue Ablagestruktur für DEV-Varianten definieren (parallel zu ASSOCIATE)

OUT OF SCOPE:
  ✗ ASSOCIATE-Dokumente — keine Änderung, kein Eingriff
  ✗ Elite / MGT Templates — eigener Sprint, eigene Phase
  ✗ MUNIEA-148 (strukturelle Zwei-Welten-GOV-Umsetzung) — separater Sprint
  ✗ Stage-3- bis Stage-8-Scripts — read-only, kein Eingriff
  ✗ Neue Inhalte erfinden — nur vorhandenes heben und anreichern


================================================================================
4. ARBEITSBLÖCKE
================================================================================

--------------------------------------------------------------------------------
Block A — Quellensuche: letzter vollständiger DEV-Stand
--------------------------------------------------------------------------------
Ziel: Für jeden betroffenen Dokumenttyp den letzten pre-S8 DEV-Stand
      im DEV Repo lokalisieren.

Vorgehen (EUMAXL führt durch — Claude kann nicht ins Repo schauen):
  A1  DEV Repo öffnen — Doku-Ordner
  A2  Für jeden Typ: letzten Stand VOR Stage-8-Entkernungsaktionen suchen
      Suchhinweis: Commits/Dateistände mit _S7 oder _S6 im Namen
      Relevante Ordner: 00-governance, 01-principles, 02-how2, 06-sprints
  A3  Gefundene Dokumente je Typ festhalten (Dateiname + Ablageort)
  A4  Kurz-Check je Dokument: "Hat es noch die volle DEV-Schärfe?"
      Kriterium: GOV-Referenzen vorhanden, technische Präzision erhalten,
      keine Vereinfachungen für Endkunden-Lesbarkeit

Ergebnis Block A: Quelldokument-Liste (5 Typen, je 1 Dokument als Basis)

--------------------------------------------------------------------------------
Block B — Abgleich: Was fehlt zum S8/S101-Standard?
--------------------------------------------------------------------------------
Ziel: Je Quelldokument delta zum S8-Standard ermitteln.

Vorgehen pro Dokument:
  B1  Header prüfen — S8-Standard vorhanden?
      Pflichtfelder: Projekt, Dokument, Tag, Datum, Stage, Status,
                     Verantwortlich, Erstellt durch
  B2  Stage-Referenzen prüfen — noch auf altem Stand (S6/S7)?
      → auf S101 aktualisieren
  B3  Terminologie-Check — "USER" noch vorhanden?
      → auf "Associate" (wo Endkundenbezug) bzw. DEV-Kontext behalten
  B4  Inhaltliche S8-Erkenntnisse prüfen die DEV-relevant sind:
      - Zwei-Repo-Modell (DEV intern / Public)
      - Session-Regel
      - Rückkopplungsschutz S3–S8
      - GOV-Verhaltensregeln für Claude (Stage 8 NEU)
      Fehlende Erkenntnisse werden addiert — nicht bestehende ersetzt

Ergebnis Block B: Delta-Liste je Dokument (was wird addiert)

--------------------------------------------------------------------------------
Block C — Umsetzung: DEV-Dokumente auf S101 bringen
--------------------------------------------------------------------------------
Ziel: Je Quelldokument eine vollständige DEV-Variante _S101 erstellen.

Reihenfolge (empfohlen — Abhängigkeiten):
  C1  GOV-Ergänzungen zuerst — normative Basis für alle anderen
  C2  principles — Grundlage für how2 und sprint
  C3  how2 — operativer Leitfaden
  C4  sprint — Dokumentvorlage
  C5  Templates generell — abschließend alle Header-Standards vereinheitlichen

Vorgehen je Dokument:
  - Quelldokument kopieren → neuer Name: *_DEV_S101.md
  - Header ersetzen (S101-Standard)
  - Delta aus Block B eintragen (additiv)
  - Inhaltliche DEV-Schärfe prüfen: vollständig? Falls ja → fertig
  - Ablage: DEV Repo (nicht Public Repo)

Ergebnis Block C: Fertige DEV-Dokumente (_DEV_S101) je Typ

--------------------------------------------------------------------------------
Block D — Abschluss & Ablagestruktur
--------------------------------------------------------------------------------
  D1  Ablagestruktur definieren:
      Vorschlag:
        R+MUNI Doku <KUERZEL>\00-governance\*_DEV_S101.md
        R+MUNI Doku <KUERZEL>\01-principles\*_DEV_S101.md
        R+MUNI Doku <KUERZEL>\02-how2\*_DEV_S101.md
        R+MUNI Doku <KUERZEL>\06-sprints\Sprint-DEV-Doku_Template_DEV_S101.md
      Pendant-Logik:
        *_ASSOCIATE_S101.md  ←→  *_DEV_S101.md (gleicher Ordner, Suffix trennt)

  D2  Rückkopplungsschutz bestätigen:
      - ASSOCIATE-Dokumente: unverändert ✓
      - S3–S8 Scripts: nicht berührt ✓
      - Public Repo: kein Push dieser Dokumente ✓

  D3  Sprint-DEV-Doku finalisieren (dieses Dokument)
  D4  Push → DEV intern


================================================================================
5. GOV-CHECK
================================================================================

GOV 10.3  Auslöser: Strukturbereinigung + Entwicklerwunsch             ✓
GOV 10.5  Fachlicher Mehrwert: DEV-Umgebung vollständig und nutzbar    ✓
GOV 10.6  Ziel explizit und überprüfbar: DEV-Varianten je Typ vorhanden ✓
GOV 10.7  Zwischenschritte dokumentiert: Blöcke A–D                    ✓
GOV 10.8  Sprint-DEV-Doku: dieses Dokument                             ✓
GOV 10.10 Keine GOV-Regel stillschweigend aufgehoben                   ✓

Rückkopplungsschutz:
  Stage-3- bis Stage-8-Artefakte: read-only — kein Eingriff            ✓
  ASSOCIATE-Dokumente: unverändert — kein Eingriff                     ✓
  Public Repo: DEV-Dokumente verbleiben im DEV intern                  ✓


================================================================================
6. ERFOLGSKRITERIUM
================================================================================

Sprint gilt als abgeschlossen wenn:

  ✓ Für alle fünf Dokumenttypen existiert eine vollständige DEV-Variante
    mit _DEV_S101 Suffix im DEV Repo
  ✓ Jede DEV-Variante hat den S101-Header-Standard
  ✓ Kein DEV-Inhalt wurde gegenüber dem Quelldokument reduziert
  ✓ S8-Erkenntnisse (DEV-relevante) sind eingearbeitet
  ✓ ASSOCIATE-Dokumente sind unverändert
  ✓ Ablagestruktur (Pendant-Logik) ist definiert und dokumentiert


================================================================================
BEZÜGE
================================================================================

[[FREEZE_8]]                         Ausgangszustand — letzter stabiler Stand
[[STAGE100_ZIELE_S100]]              Phasenrahmen Stage 1.xx
[[GOV_Global_S8]]                    Normative Grundlage (bis GOV_Global_S101)
[[AI_DRIVEN_DEV_METHODE_S8]]         Methodik-Basis


================================================================================
Sprint-DEV-S101-DEV-TMPL-RESYNC | 2026-03-29
R+MUNI Blueprint | Stage 1.01 | Erstellt: EUMAXL + Claude (Pair-Session)
================================================================================
