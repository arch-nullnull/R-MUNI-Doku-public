================================================================================
SPRINT-DEV-DOKUMENTATION — R+MUNI BLUEPRINT
Sprint-DEV-S101-Namenskonvention-GitHub-Sync
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV-S101-Namenskonvention-GitHub-Sync
Tag             : #sprint #dev #naming #github #sync #structure #s101
Datum           : 2026-03-31
Stage           : S1.01 — AKTIV
Status          : ABGESCHLOSSEN
Auslöser        : GOV 10.3 — Strukturbereinigung / Entwicklerwunsch
Verantwortlich  : EUMAXL
Jira-Sync       : NEIN
Erstellt durch  : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
1. AUSGANGSLAGE
================================================================================

Aus dem Offboarding Betakunde Associate01 (LL_Betakunde_Associate01_S101) ist hervorgegangen dass der
GitHub-Sync eine nützliche Namenskonvention erzeugt die bisher nicht
dokumentiert war. Parallel fehlte eine Single Source of Truth für
Ablagestruktur und Naming über alle R+MUNI Welten.

Zwei offene Punkte wurden in diesem Sprint zusammengeführt:

  1. Ablagestruktur und Naming — rollenübergreifend dokumentieren
     (war offenes Kriterium aus Sprint-DEV-S101-DEV-TMPL-RESYNC)

  2. Namenskonvention R-MUNI- vs. R+MUNI — soweit fixierbar festhalten,
     Rest als bewusst offen markieren
     (war Backlog-Eintrag BACKLOG_Namenskonvention-GitHub-Sync_DEV_S101)

Beziehung zu DEV-TMPL-RESYNC:
Dieser Sprint schließt den letzten offenen Punkt aus dem
Sprint-DEV-S101-DEV-TMPL-RESYNC ab (Ablagestruktur / Block D1).
Beide Sprints sind inhaltlich verknüpft — formal eigenständig.


================================================================================
2. ZIEL
================================================================================

Ein rollenübergreifendes Dokument `naming_and_structure_S101.md` das
als Single Source of Truth für Namenskonventionen und Ablagestruktur
aller R+MUNI Dokumente gilt.

Inhalt:
  - Suffix-Logik und Stage-Herkunft
  - Letzter stabiler Stand je Welt (Freeze 8 / R1)
  - Ablagestruktur aller relevanten Bereiche (Root, internal, public, Repo)
  - Pendant-Logik DEV / ASSOCIATE
  - ELITE / MGT als Platzhalter (noch nicht fixiert)
  - Namenskonvention R-MUNI- vs. R+MUNI (soweit fixierbar)

Abgrenzung:
  - Template-Logik wird nicht hier dokumentiert — gehört in How2/Principles
  - Keine Tiefe unterhalb Rubrikenebene — Rubriken mit Kurzbeschreibung
  - Keine Fixierung von ELITE/MGT — Platzhalter mit ⚠-Marker


================================================================================
3. ERGEBNIS
================================================================================

Erstellt: naming_and_structure_S101.md
Ablage:   C:\Prototyping\R+MUNI Doku\R+MUNI Doku-internal\04-notes\

Inhalt validiert gegen echte Verzeichnisstruktur (structure_full_all.txt).
Kein Inhalt erfunden — nur was in der realen Struktur vorhanden ist.

Backlog-Status:
  BACKLOG_Namenskonvention-GitHub-Sync_DEV_S101 → TEILWEISE UMGESETZT
  Begründung: Die Konvention R-MUNI- vs. R+MUNI ist im Dokument festgehalten
  soweit sie stabil ist. Vollständige Fixierung über alle Welten steht noch
  aus (Voraussetzung: weitere Beta-Kunden-Durchläufe). Backlog-Eintrag
  bleibt bestehen — Status auf IN BEARBEITUNG / TEILWEISE zu setzen.


================================================================================
4. LESSONS LEARNED
================================================================================

  - Ablagestruktur-Dokumentation profitiert massiv von echter Verzeichnisliste —
    ohne Struktur-Export entstehen zwangsläufig erfundene Ordner
  - Die Trennung "was gehört ins Ablage-Dokument / was gehört in How2"
    ist eine bewusste Entscheidung — Templates raus, Rubriken rein
  - ELITE/MGT früh als Platzhalter zu markieren verhindert spätere
    Rückwirkungen auf bereits fixierte Konventionen
  - R-MUNI- vs. R+MUNI ist kein Naming-Entscheid sondern ein
    Infrastruktur-Merkmal (GitHub-Limitierung) — das ändert die Einordnung


================================================================================
5. GOV-CHECK
================================================================================

GOV 10.3  Auslöser: Strukturbereinigung + Entwicklerwunsch             ✓
GOV 10.5  Fachlicher Mehrwert: Single Source of Truth vorhanden        ✓
GOV 10.6  Ziel explizit und überprüfbar: Dokument existiert            ✓
GOV 10.7  Zwischenschritte dokumentiert: iterative Validierung          ✓
GOV 10.8  Sprint-DEV-Doku: dieses Dokument                             ✓
GOV 10.10 Keine GOV-Regel stillschweigend aufgehoben                   ✓

Rückkopplungsschutz:
  ASSOCIATE-Dokumente: unverändert — kein Eingriff                     ✓
  Public Repo: kein Push ohne explizite Freigabe                       ✓
  Stage-3- bis Stage-8-Artefakte: nicht berührt                        ✓


================================================================================
BEZÜGE
================================================================================

[[naming_and_structure_S101]]                     Ergebnis dieses Sprints
[[BACKLOG_Namenskonvention-GitHub-Sync_DEV_S101]] Ursprungs-Backlog-Eintrag
[[Sprint-DEV-S101-DEV-TMPL-RESYNC]]               Verknüpfter Sprint
[[Global_GOV_DEV_S101]]                           Normative Grundlage
[[LL_Betakunde_Associate01_S101]]                 Ursprung des Backlog-Eintrags


================================================================================
Sprint-DEV-S101-Namenskonvention-GitHub-Sync | 2026-03-31
R+MUNI Blueprint | Stage 1.01 | Erstellt: EUMAXL + Claude (Pair-Session)
================================================================================
