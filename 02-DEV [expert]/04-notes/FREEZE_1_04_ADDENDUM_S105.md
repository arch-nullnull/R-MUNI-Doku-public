

================================================================================
================================================================================
ADDENDUM — STAGE 1.05
Erweiterung zu FREEZE-1.04 | Nicht Teil des originalen Freeze-Stands
Addendum-Datum  : 2026-04-15
Addendum-Autor  : EUMAXL + Claude Sonnet 4.6
Zweck           : Orientierungsstand für neue Chat-Sessions und Qualitätsgate
                  S105Q2. Inhalt ist additiv — FREEZE-1.04 bleibt unverändert
                  gültig als historische Baseline.
================================================================================
================================================================================


================================================================================
A1. STAGE-MODELL — UPDATE ZUM FREEZE-1.04 STAND
================================================================================

Aktualisierung Kapitel 2 (Stage-Modell):

  Stage 1.04 FREEZE  — Außenwirkung, AIOF-Betrieb & Backlog-Abbau (ABGESCHLOSSEN)
  Stage 1.05 AKTIV   — Qualitätsgate, GOV-Reduktion & AIOF-Entscheid

Titel Stage 1.05 (zum Zeitpunkt Addendum definiert):
  "Qualitätsgate, GOV-Reduktion & AIOF-Entscheid"

Vorschau Folgestages:
  Stage 1.5  — Release S1→S1.5 | Außenwirkung | GOV/AI Driven final
  Stage 2.0  — Erster Stage nach vollständigem KI-Exit-Point

Hinweis Zählung:
  "Stage 1.5" ist bewusst keine Dezimalstelle wie 1.05 —
  es markiert einen benannten Meilenstein-Release, keinen regulären
  Sprint-Stage. Konvention wird beim Freeze S1.5 formalisiert.


================================================================================
A2. ZIELSTATUS STAGE 1.05 — STAND 2026-04-15
================================================================================

S105-Z1: AUSSENWIRKUNG FINALISIEREN
-------------------------------------

Status: OFFEN — Qualitätsgate S105Q2 als Freigabebedingung definiert

Was bisher erreicht wurde:
  — Kein Sprint gestartet
  — Abhängigkeit zu Z3 (GOV/AI Driven) und GitHub-Test definiert

Was offen bleibt:
  — Qualitäts-Check Außenwirkung (GitHub-Test: README, Links, SVGs, Install.txt)
  — LinkedIn-Profil überarbeiten
  — GitHub Release öffentlich deployen

Freigabebedingung (Qualitätsgate S105Q2):
  Außenwirkung wird ERST freigeschaltet wenn:
    1. GOV auf 6 Kernregeln abgenommen (Z3)
    2. AI Driven aktualisiert und reduziert (Z3)
    3. GitHub-Test positiv — alles sauber von außen

Bewusste Entscheidung: Qualität vor Geschwindigkeit. Kein Posting
  solange eines der drei Kriterien nicht erfüllt ist.


S105-Z2: NBX ERWEITERUNG & CLEANUP
-------------------------------------

Status: TEILWEISE ABGESCHLOSSEN

Was erreicht wurde:
  ✓ IP-Merge Bug in NBX04 identifiziert und behoben
    (Ursache: Reihenfolgeabhängigkeit bei einmaligem Durchlauf)
  ✓ Erster vollständiger Produktivrun NBX00–NBX05 + ECM00–ECM01
    durchgeführt — Mapping-Modell erstellt, OEF XML abgelegt,
    Archi-Modell gesichert
  ✓ Korrekter ECM-Ablauf für Mapping-Modell-Erstellung dokumentiert
    und verstanden
  Sprint: DEV_Sprint_NBX-ECM-RUN_S105 — ABGESCHLOSSEN

Was offen bleibt:
  — NBX03/04 Bereinigung (Code-Cleanup)
  — nbx_config.txt + nbx_raw.json in .gitignore
  — QM-Run nicht zwingend S105


S105-Z3: GOV & AI DRIVEN REDUKTION
-------------------------------------

Status: OFFEN — Voraussetzung Z4 erfüllt, Sprint noch nicht gestartet

Was bisher erreicht wurde:
  — AIOF-Entscheid (Z4) gefallen — Voraussetzung ist erfüllt
  — Richtung definiert: tool-agnostisch, nicht Claude-spezifisch

Was offen bleibt:
  — GOV auf 6 Kernregeln destillieren (EUMAXL definiert welche)
  — AI Driven auf S104/S105-Erfahrungen bringen
  — AI Driven reduzieren
  Beides: separater Chat ohne Kontext-Drift

Hinweis: Z3 ist Freigabebedingung für Qualitätsgate S105Q2.
  Kein Release ohne abgenommenes GOV/AI Driven Update.


S105-Z4: AIOF-ENTSCHEID
--------------------------

Status: ENTSCHEID GEFALLEN — Sprint aktiv, stage-übergreifend

Entscheid (EUMAXL, S105, 2026-04-15):
  KI wird Addon wie Atlassian — hohe Kosten, Mehrwerte vorhanden,
  aber nicht im R+MUNI-Kernbereich. R+MUNI nach außen ohne KI
  bedienbar. KI nur mehr DEV-intern bis lokale Variante verfügbar.

Entscheidungsgründe (dokumentiert in DEV_Sprint_AIOF-OFFBOARDING-CLAUDE_S105):
  — KI hat ab S8 die eigene Lösung in einem merklichen Prozentsatz
    vollständig überlagert
  — Verrechnungsunberechenbarkeit und Intransparenz Anthropic
  — R+MUNI soll positioniert werden, nicht andere beim Claude-Einsatz
    enablen
  — KI hat indirekt R+MUNI sabotiert

Was folgt:
  — Lokales LLM Evaluation läuft parallel (Variantentest ab 14.05.2026)
  — KI-Dokumentation bleibt physisch bis S1.5, dann Deprecated-Setzung
  — Finalisierung KI-Doku und Außenwirkung ab Stage 1.5
  — Riskmanagement als Blueprint-Erweiterung — Sprint ab S1.5

Sprint: DEV_Sprint_AIOF-OFFBOARDING-CLAUDE_S105
  Status: AKTIV — läuft stage-übergreifend bis kostenfreie lokale
          Variante einsatzbereit und liefert verwertbare Dokumente


S105-Z5: KLEINERE CARRY-OVER
------------------------------

Status: TEILWEISE ABGESCHLOSSEN

Was erreicht wurde:
  ✓ Beta-Doku-Merge abgeschlossen
    (Sprint DEV_Sprint_BETA-DOKU-MERGE_S105 — ABGESCHLOSSEN)
    Veraltete Beta-Dokumente deprecated/gelöscht, neue BETA_ONBOARDING-
    Reihe (principles + How2) auf Tier-Modell und Addon-Stand erstellt
  ✓ OBS→OBSIDIAN Rename durchgeführt (Kürzelkonflikt OBS/OBS Studio behoben)
    Neue Dokumente: OBSIDIAN_How2_DEV_S105, OBSIDIAN_principles_DEV_S105
    Sprint: DEV_Sprint_OBS-RENAME-TAGGING_S105 — IN ARBEIT

Was offen bleibt:
  — structure_R_MUNI_normal_.txt manuell durch EUMAXL aktualisieren
    (OBS→OBSIDIAN Dateinamen — Sprint wartet auf diese Aktion)
  — SVG Pillow in Install.txt nachtragen (Abhängigkeit SVG-Reihe)
  — README Image/Link-Bugs nach Repo-Sync
  — Associate Cleaning Run in weiteren Dokumenten
  — MUNIDELL SVG Header — laut EUMAXL erledigt, formal zu bestätigen


================================================================================
A3. SPRINTS STAGE 1.05 — ÜBERSICHT
================================================================================

ABGESCHLOSSEN:
  DEV_Sprint_NBX-ECM-RUN_S105          Z2 — Produktivrun + IP-Merge-Fix
  DEV_Sprint_BETA-DOKU-MERGE_S105      Z5 — Beta-Doku bereinigt, neu aufgesetzt

IN ARBEIT:
  DEV_Sprint_OBS-RENAME-TAGGING_S105   Z5 — wartet auf EUMAXL: structure.txt
  DEV_Sprint_AIOF-OFFBOARDING-CLAUDE_S105  Z4 — stage-übergreifend aktiv

BACKLOG (nicht gestartet):
  BACKLOG_NBA-FLOW_DEV_S105            Erweiterung NBX um Agent-Daten
                                        Voraussetzung: NBX stabil + Agent-Evaluation
  BACKLOG_FLOW-ARCHIMATE-USABILITY_DEV_S105
                                        Usability NBX→ECM→Archi für Kunden
                                        Voraussetzung: Testkandidat vorhanden


================================================================================
A4. NEUE ARTEFAKTE STAGE 1.05 — STAND 2026-04-15
================================================================================

Sprint-Dokumentationen:
  DEV_Sprint_NBX-ECM-RUN_S105                  ABGESCHLOSSEN
  DEV_Sprint_BETA-DOKU-MERGE_S105              ABGESCHLOSSEN
  DEV_Sprint_OBS-RENAME-TAGGING_S105           IN ARBEIT
  DEV_Sprint_AIOF-OFFBOARDING-CLAUDE_S105      AKTIV (stage-übergreifend)

Backlogs:
  BACKLOG_NBA-FLOW_DEV_S105                    BACKLOG — nicht gestartet
  BACKLOG_FLOW-ARCHIMATE-USABILITY_DEV_S105    BACKLOG — nicht gestartet

Neue Dokumente (Inhaltsartefakte):
  OBSIDIAN_How2_DEV_S105.md                    ersetzt OBS_How2_DEV_S8
  OBSIDIAN_principles_DEV_S105.md              ersetzt OBS_principles_Associate_S8
  BETA_ONBOARDING_principles_DEV_S105.md       neu — Tier-Modell-Basis
  BETA_ONBOARDING_How2_DEV_S105.md             neu — Onboarding-Prozess

Deprecated in S105:
  KI_How2_MUNI_S105                            DEPRECATED — AIOF-Entscheid
  BETA_ONBOARDING_Atlassian_Zugriffsmodell     DEPRECATED — Stage-4-Stand
  HOW2_S6-Z1_BetaFeedback_S6                  GELÖSCHT

Templates (neu / aktualisiert):
  DEV_Sprint_Template_S105.md
  BACKLOG_Template_DEV_S105.md
  principles_Template_S105.md
  how2_DEV_Template_S105.md
  how2_MUNI_Template_S105.md
  LL_Template_S105.md


================================================================================
A5. AIOF-STAND — UPDATE ZUM FREEZE-1.04 KAPITEL 7
================================================================================

Ursprünglicher Stand (FREEZE-1.04 Kap. 7):
  Beobachtungsphase auf S105 ausgedehnt.
  Entscheid Claude weiter / AIOF / hybrid — noch offen.

Aktueller Stand (S105, 2026-04-15):
  Entscheid gefallen — AIOF abgeschlossen.

Persönliche KI-Nutzung EUMAXL (definiert, keine Evaluation mehr nötig):
  Claude Pro    Persönliche Nutzung ohne R+MUNI-Kontext, ohne DEV-Einsatz
  Copilot       Persönliche Nutzung — kein R+MUNI-Kontext
  ChatGPT Pro   Persönliche Nutzung — kein R+MUNI-Kontext

R+MUNI DEV — KI-Einsatz bis lokale Variante verfügbar:
  Aktuell: Claude Sonnet 4.6 weiter als DEV-Mittel (pragmatisch)
  Werkzeugwahl folgt nach Evaluation lokale Variante
  Variantentest ab 14.05.2026

Support- und Feedback-Ticket Anthropic:
  Support-Ticket: ERLEDIGT — Vorschlag angenommen
  Feedback-Formular: offen — keine Rückmeldung von Anthropic


================================================================================
A6. QUALITÄTSGATE S105Q2 — DEFINITION
================================================================================

Zweck:
  S105Q2 ist kein eigener Stage und kein eigenes Zieldokument.
  Es ist ein internes Release-Readiness-Gate das sicherstellt dass
  vor der ersten Außenwirkung alle Qualitätsbedingungen erfüllt sind.
  Ziele S105 (Z1–Z5) bleiben vollständig unverändert.

Charakter:
  — Intern, keine Außenwirkung
  — Kein GitHub-Push, kein öffentlicher Release
  — Kein eigener Zielkatalog
  — Dokumentiert als Addendum / Checkpoint — nicht als eigener Freeze

Freigabebedingungen (alle drei müssen erfüllt sein):

  Gate 1 — GOV abgenommen
    GOV auf 6 Kernregeln destilliert
    Von EUMAXL bestätigt
    Sprint Z3 Teil 1 abgeschlossen

  Gate 2 — AI Driven aktualisiert
    AI Driven auf S104/S105-Erfahrungen gebracht und reduziert
    Von EUMAXL bestätigt
    Sprint Z3 Teil 2 abgeschlossen

  Gate 3 — GitHub-Test positiv
    README: Struktur, Inhalt, SVGs korrekt
    Install.txt: vollständig und aktuell
    Links: keine toten Links
    Außenwirkung: sauber und ohne KI-Bezug im Hauptnarrativ

Erst wenn alle drei Gates grün:
  → Z1 Außenwirkungsrelease freigegeben
  → LinkedIn-Posting
  → GitHub Release public

Nachgelagertes Artefakt:
  Release-Narrativ S1→S1.5 (siehe A7) —
  begleitet den Release als inhaltliches Eröffnungsdokument


================================================================================
A7. RELEASE-NARRATIV S1→S1.5 — KONZEPT
================================================================================

Zweck:
  Ein öffentliches Dokument das die Reise von R+MUNI beschreibt —
  vom Lernprojekt zum realen Blueprint. Kein Marketing, ehrliche Bilanz.
  Geht raus mit dem Release nach Qualitätsgate S105Q2.

Dokumenttyp:
  Neu — kein existierender Typ in TMP_principles_S105.
  Arbeitstitel: RELEASE_NARRATIV_S1-S15.md
  Ablage: nach Freigabe in 04-notes\ oder eigenem Ordner 05-releases\
  (Konvention wird beim Aufsetzen des Dokuments definiert)

Geplante Inhaltsstruktur:

  1. Vom Lernprojekt zum Blueprint
     Ehrliche Chronologie S1–S8: Was war das wirklich, welche Fehler
     wurden gemacht, welche Erkenntnisse entstanden. Kein Schönreden.

  2. Produktivbetrieb S1.01–S1.05
     Was sich stabilisiert hat und was nicht. Konkrete Stages.
     KI-Abhängigkeit als strukturelles Risiko — wie erkannt, wie adressiert.

  3. Vor- und Nachteile offen
     Was früher hätte kommen sollen. Was zu spät erkannt wurde.
     Was gut funktioniert hat und warum. Keine Jubelprosa.

  4. Fazit — wo R+MUNI jetzt steht
     Systemreifegrad. Positionierung. Was R+MUNI ist und was nicht.

  5. Roadmap S1.5→S2.0
     Was kommt bewusst nicht (kontrollierter Exit-Point, wenig neue Features).
     Was kommt: Riskmanagement, lokales LLM Evaluation, Unabhängigkeit.
     S2.0 als erster Stage nach vollständigem KI-Exit-Point.

Zeitpunkt Erstellung:
  Nach Gate 1 + Gate 2 (GOV + AI Driven fertig) — inhaltliche Grundlage
  muss stehen bevor das Narrativ geschrieben wird.
  Vor Gate 3 (GitHub-Test) — damit Release komplett ist.


================================================================================
A8. FOLGESEQUENZ — NÄCHSTE SCHRITTE IN KORREKTER REIHENFOLGE
================================================================================

Diese Sequenz gilt für die verbleibenden Aktivitäten in S105
bis zum Qualitätsgate S105Q2 und dem anschließenden Release.

  Schritt 1   GOV-Sprint (Z3 Teil 1)                              ✓ ABGESCHLOSSEN
              Separater Chat, kein Kontext-Drift
              EUMAXL definiert die 6 Kernregeln
              Output: Global_GOV_DEV aktualisiert — EUMAXL nimmt ab

  Schritt 2   AI Driven Sprint (Z3 Teil 2)                       ✓ ABGESCHLOSSEN
              Separater Chat, kein Kontext-Drift
              Reduktion auf S104/S105-Erfahrungen
              Output: AI_DRIVEN_DEV_METHODE aktualisiert — EUMAXL nimmt ab

  Schritt 3   Structure Update
              structure.txt und structure_R_MUNI_normal_.txt
              auf aktuellen Stand bringen:
              — OBSIDIAN-Rename (OBS_* → OBSIDIAN_*)
              — Neue S105-Artefakte
              — Deprecated-Vermerke
              Manuell durch EUMAXL + Sync-Prüfung

  Schritt 4   Git Sync
              Alle Änderungen pushen
              GitHub-Test: README, Links, SVGs, Install.txt
              Von außen prüfen ob alles sauber aussieht

  Schritt 5   Release-Narrativ S1→S1.5 erstellen
              Separater Chat oder eigene Session
              Basis: GOV + AI Driven fertig (Schritt 1+2 abgeschlossen)

  Schritt 6   Qualitätsgate S105Q2 — Review
              Neues Projekt / neuer Chat mit sauberem Kontext
              Ziele S104→S105 nochmal vollständig durchgehen
              Prüfung: ist alles sauber, vollständig, konsistent?
              Wenn ja → Release freigegeben
              Wenn nein → Punkte korrigieren, erneut prüfen

  Schritt 7   Außenwirkung schalten (Z1)
              LinkedIn-Posting
              GitHub Release public
              Release-Narrativ veröffentlichen


================================================================================
A9. ORIENTIERUNGSHINWEISE FÜR NEUE CHAT-SESSIONS
================================================================================

Diese Hinweise sind explizit für Claude in neuen Sessions gedacht.
Sie beschreiben den Stand und die Prioritäten ohne dass der gesamte
S105-Sprint-Kontext neu geladen werden muss.

Aktueller Projektzustand (Stand Addendum, aktualisiert 2026-04-15):
  S105 läuft. AIOF-Entscheid gefallen.
  GOV Update: ABGESCHLOSSEN — S105, 2026-04-15
  AI Driven Update: ABGESCHLOSSEN — S105, 2026-04-15
  GitHub-Test: AUSSTEHEND — nächster Schritt vor Release
  Kein öffentlicher Release bisher.

Was Claude in neuen Sessions NICHT tun soll:
  — GOV-Regeln eigenständig verändern — Update ist abgeschlossen
  — AI Driven eigenständig verändern — Update ist abgeschlossen
  — Außenwirkungsmaterial als fertig annehmen (GitHub-Test steht noch aus)
  — AIOF-Entscheid rückgängig machen oder relativieren
  — KI als Kernbestandteil von R+MUNI positionieren (ist Addon)

Was Claude in neuen Sessions als Basis annehmen kann:
  — NBX-ECM Flow ist produktiv lauffähig und getestet
  — Beta-Doku ist auf aktuellem Stand (Tier-Modell, Addon-Stand korrekt)
  — OBSIDIAN-Kürzel ersetzt OBS — beide Dokumente existieren neu
  — KI ist DEV-Addon, kein R+MUNI-Kernbestandteil
  — GOV ist auf 6 Kernregeln reduziert und abgenommen
  — AI Driven ist auf S104/S105-Erfahrungen gebracht und reduziert
  — Release-Readiness hängt an: GOV ✓ / AI Driven ✓ / GitHub-Test ✗

Kritischer Pfad bis Release (aktualisiert):
  ✓ GOV-Sprint → ✓ AI Driven Sprint → Structure Update → Git Sync
  → Release-Narrativ → S105Q2 Review → Außenwirkung

Nächster konkreter Schritt (wenn dieser Chat endet):
  Structure Update (structure.txt + structure_R_MUNI_normal_.txt).
  Manuell durch EUMAXL — OBSIDIAN-Rename, neue S105-Artefakte, deprecated.
  Dann Git Sync und GitHub-Test.
  Dann: Release-Narrativ erstellen, S105Q2 Review, Außenwirkung schalten.


================================================================================
A10. STAGE-ABSCHLUSS — NICHT RELEVANT BIS QUALITÄTSGATE ERFÜLLT
================================================================================

FREEZE-1.05 wird erst erstellt wenn:
  ✓ Qualitätsgate S105Q2 alle drei Gates grün
  ✓ Außenwirkungsrelease durchgeführt
  ✓ Alle S105-Sprints auf finalem Status (ABGESCHLOSSEN oder
    explizit als stage-übergreifend dokumentiert)
  ✓ AIOF-OFFBOARDING-Sprint: Status klar dokumentiert
    (läuft weiter bis lokale Variante — kein Blocker für Freeze)

Dieses Addendum ist kein Freeze.
Es ist eine Orientierungserweiterung zu FREEZE-1.04.
FREEZE-1.04 bleibt unverändert gültig als historische Baseline.


================================================================================
ADDENDUM S105 — 2026-04-15 | R+MUNI Blueprint
Erweiterung zu FREEZE-1.04 | EUMAXL + Claude Sonnet 4.6
Nicht für öffentlichen Release — internes Orientierungsdokument
================================================================================
