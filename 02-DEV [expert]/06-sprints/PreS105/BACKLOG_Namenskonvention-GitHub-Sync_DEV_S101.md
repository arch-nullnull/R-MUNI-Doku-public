================================================================================
NAMENSKONVENTION GITHUB-SYNC — BACKLOG (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : BACKLOG_Namenskonvention-GitHub-Sync_DEV_S101
Tag             : #dev #backlog #naming #github #sync #s101
Datum           : 2026-03-31
Stage           : S1.01 — AKTIV
Status          : BACKLOG — nicht gestartet
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN — Jira nach explizitem EUMAXL-Input
Ablageort       : C:\Prototyping\R+MUNI Doku\R+MUNI Doku-internal\05-backlog\
================================================================================


================================================================================
1. AUSGANGSLAGE UND KONTEXT
================================================================================

Warum existiert dieser Backlog-Eintrag?
Aus dem Offboarding MLAT (LL_MLAT_S101) ist hervorgegangen dass der
GitHub-Sync eine nützliche Namenskonvention erzeugt die bisher nicht
dokumentiert ist: GitHub unterstützt kein +-Zeichen in Ordnernamen —
dadurch entsteht automatisch eine visuelle Unterscheidung:
  R-MUNI-<Kundenkürzel>  = DEV-Sync-Umgebung (GitHub-seitig)
  R+MUNI <Kundenkürzel>  = echte Kundeninstallation (lokal)
Diese Konvention ist über die Welten nicht einheitlich fixiert und
aktuell nirgendwo dokumentiert. Eine Fixierung ist heikel weil die
Konvention nicht in allen Kontexten gleich greift.

Was ist der gewünschte Zielzustand?
Die Namenskonvention ist in einem geeigneten Dokument festgehalten —
als Erweiterung von BETA_GitHub_Nutzung oder als eigenständiges
Dokument. Über die Welten (DEV-intern / Kundenumgebung) ist klar
geregelt was gilt und was kontextabhängig bleibt.

Warum jetzt noch nicht?
Die Konvention ist noch nicht stabil genug über alle Welten — eine
voreilige Fixierung würde Folgefehler erzeugen. Erst nach mehr
Praxiserfahrung mit weiteren Beta-Kunden sinnvoll zu dokumentieren.


================================================================================
2. SCOPE
================================================================================

Was gehört dazu:
  - Namenskonvention R-MUNI- vs. R+MUNI dokumentieren
  - Kontext je Welt klären (DEV-intern, Kundenumgebung, GitHub-Sync)
  - Entscheidung: Erweiterung BETA_GitHub_Nutzung oder eigenes Dokument
  - Ablageort und Dokumenttyp festlegen

Was gehört explizit nicht dazu:
  - Umbenennung bestehender Ordner oder Repos
  - Änderungen am Zwei-Repository-Prinzip
  - Neue Sync-Mechanismen oder Tools


================================================================================
3. VORAUSSETZUNGEN FÜR UMSETZUNG
================================================================================

Bevor dieser Backlog-Punkt gestartet werden kann:
  - Mindestens ein weiterer Beta-Kunden-Durchlauf zur Validierung
    ob die Konvention konsistent greift
  - Klärung ob BETA_GitHub_Nutzung auf S101 gehoben wird
    (dann Erweiterung dort) oder ob eigenes Dokument sinnvoller


================================================================================
4. OFFENE FRAGEN
================================================================================

| Frage | Wer klärt | Bis wann |
|-------|-----------|----------|
| Erweiterung BETA_GitHub_Nutzung oder eigenes Dokument? | EUMAXL | vor Sprint-Start |
| Gilt die Konvention auch für künftige Non-GitHub-Sync-Szenarien? | EUMAXL | vor Sprint-Start |


================================================================================
BEZÜGE
================================================================================
[[LL_MLAT_S101]]                    Ursprung dieses Backlog-Eintrags
[[BETA_GitHub_Nutzung_S8]]          Betroffenes Dokument
[[Global_GOV_DEV_S101]]             Normative Grundlage


================================================================================
NAMENSKONVENTION GITHUB-SYNC | DEV | S1.01 | 2026-03-31 | R+MUNI Blueprint
================================================================================
