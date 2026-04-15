================================================================================
BETA GITHUB NUTZUNG — BETA BETRIEB
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : BETA_GitHub_Nutzung_S105
Tag             : #dev #github #beta #repo #s105
Datum           : 2026-04-14
Stage           : S105 — AKTIV
Status          : AKTIV
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Erstellt        : 2026-03-09
Letzte Änderung : 2026-04-14 — S105-Update | Repo-Modell vollständig überarbeitet
                               auf Basis realer Beta-Erfahrungen (Beta 1.0)
Ablageort       : R+MUNI Doku-public\01-principles\BETA_GitHub_Nutzung_S8.md
================================================================================


1. ZWECK
--------
Dieses Dokument regelt die Nutzung von GitHub im Kontext von R+MUNI.
Es beschreibt welche Repositories existieren, wer sie hält, was drin ist
und wie sie zusammenspielen.


2. REPO-ÜBERSICHT
------------------

R+MUNI nutzt vier Repository-Typen:

  Repo 1   R-MUNI               PUBLIC   Blueprint-Produktivumgebung
  Repo 2   R-MUNI-Doku-public   PUBLIC   Öffentliche Dokumentationsbasis
  Repo 3   Doku-intern          PRIVATE  Vollständige DEV-Doku (EUMAXL)
  Custo    R+MUNI <Kürzel>      PRIVATE  Kundenumgebung (Kunde hält Repo)

Naming-Hinweis: GitHub-Repos heißen R-MUNI (Bindestrich) — GitHub unterstützt
kein +-Zeichen in Repository-Namen. Lokal bleibt der Name R+MUNI.


3. REPO 1 — R-MUNI (BLUEPRINT-PRODUKTIVUMGEBUNG)
--------------------------------------------------
  GitHub:       github.com/arch-nullnull/R-MUNI
  Sichtbarkeit: PUBLIC
  Owner:        EUMAXL

  Inhalt:
    Scripts (alle Reihen: CSV, XML, M2B, HLP, CLE, ATL, FLW, NBX, SVG ...)
    Ordnerstruktur (00-model, 01-artifacts, 02-stages)
    Konfigurationsdateien (root.cfg, mapping.txt, sync.txt etc.)
    Install.txt, README.md
    99-doku\ — nur was für README und Außenwirkung nötig ist
               keine Varianten-Doku hier

  Zweck:
    Öffentlicher Release-Stand des R+MUNI Toolsets.
    Basis für Installation — Nutzer lädt ZIP + Dir_Setup.bat,
    kein direktes Clonen für Installation.

  Grundsatz:
    Nur saubere, freigegebene Stände werden gepusht.
    Keine automatischen Pushes aus Scripts.
    DEV-Stände, Logs und firmenspezifische Inhalte kommen nie rein.


4. REPO 2 — R-MUNI-DOKU-PUBLIC (ÖFFENTLICHE DOKUMENTATIONSBASIS)
------------------------------------------------------------------
  GitHub:       github.com/arch-nullnull/R-MUNI-Doku-public
  Sichtbarkeit: PUBLIC
  Owner:        EUMAXL

  Inhalt:
    Drei Dokumentationsvarianten zur Auswahl:
      CARD      Spielerischer Einstieg — minimal, keine Fachbegriffe
      R+MUNI    Produktivvariante — Standard, KMU-tauglich
      DEV       Vollständig, GOV-konform — für Expert-Betrieb

  Zweck:
    Nutzer wählt seine Variante und übernimmt die relevante Doku
    in 99-doku\ der eigenen Produktivumgebung.
    Erst dann ist die Produktivumgebung vollständig.
    Dokumente können nachgeschärft werden wenn Drift entsteht
    oder das Verhalten nicht dem eigenen Kontext entspricht.

  Quelle:
    Wird manuell aus Repo 3 (Doku-intern) abgeleitet und reduziert.


5. REPO 3 — DOKU-INTERN (DEV-DOKU, PRIVAT)
--------------------------------------------
  Sichtbarkeit: PRIVATE
  Owner:        EUMAXL

  Inhalt:
    Vollständige DEV-Dokumentation über alle Stages.
    GOV, Principles, How2, Sprint-Dokumentation, Freeze-Dokumente.
    Historisch vollständig — keine Bereinigung über Stages.

  Zweck:
    Quelle der Wahrheit für alle Dokumentation.
    Basis aus der Repo 2 (Doku-public) manuell abgeleitet wird.
    Kein öffentlicher Zugang.


6. CUSTO-REPOS — KUNDENUMGEBUNGEN
-----------------------------------
Jeder Beta-Kunde hält sein eigenes Repository.
EUMAXL hat keinen automatischen Zugriff.

  Repo beim Kunden:
    R+MUNI <Kürzel>\         Vollständige Produktivumgebung — Scripts, Modelle,
                             Konfiguration, 99-doku mit gewählter Variante
                             und persönlichen Anpassungen

  Bei Freigabe durch den Kunden:
    EUMAXL synct R+MUNI <Kürzel>\ lokal in seinen eigenen R+MUNI-Ordner.
    Persönliche Anpassungen in 99-doku\ werden nicht automatisch
    überschrieben — nur auf expliziten Wunsch des Kunden.

  Freigabe-Modell:
    Kunde entscheidet selbst ob und wann EUMAXL Zugriff bekommt.
    Drei Service-Stufen möglich (wie in README beschrieben):
      — Temporär für Support-Einsätze
      — Dauerhaft für regelmäßige Updates
      — Erweiterter Service (Prio-Ticket, DEV-Support, Pre-Release-Updates)

  Kundenmodelle und -daten:
    Alles liegt im einen Kunden-Repo — Modelle, Konfiguration, Doku.
    Werden nicht veröffentlicht.
    Werden nicht in Repo 1 oder 2 eingecheckt.
    Unterliegen keiner Open-Source-Lizenz.
    Gehören ausschließlich dem Kunden.

  ⚠ Bekannte Herausforderung (Beta 1.0 → Beta 1.5):
    Struktur-Updates am Blueprint können zu Klärungsbedarf führen —
    welche Dateien sind betroffen, was verändert sich, wann wird gezogen.
    Solange die Blueprint-Struktur noch in Bewegung ist entstehen
    Abstimmungsaufwände beim Sync.
    Ziel: mit Strukturfixierung bis Beta 1.5 deutlich reduziert.

  Grundsatz:
    Kein Sync in Kundenumgebungen ohne Rücksprache.
    Neu erstellte, noch nicht gepushte Inhalte beim Kunden
    dürfen nicht unbeabsichtigt überschrieben werden.


7. ENTWICKLUNGS-GRUNDREGEL
----------------------------
  ┌──────────────────────────────────────────────────────────────┐
  │  Entwicklung an R+MUNI findet in Repo 3 (privat) statt.     │
  │                                                              │
  │  Repo 1 und Repo 2 (PUBLIC) erhalten nur freigegebene,      │
  │  geprüfte Stände — keine aktiven Entwicklungsstände.         │
  └──────────────────────────────────────────────────────────────┘


8. FEEDBACK AUS DER BETA
--------------------------
Erkenntnisse aus dem Beta-Betrieb die den Blueprint verbessern:
  → werden als GitHub Issue in Repo 1 (R-MUNI) eingetragen
  → Umsetzung erfolgt in Repo 3 bzw. direkt in den Scripts
  → freigegebener Stand fließt in Repo 1 und/oder Repo 2

  Regel: Kein direktes Eingreifen in Repo 1 oder 2 durch Beta-Kunden.
         Feedback ja — direkter Commit nein.


9. ZUSAMMENFASSUNG
-------------------

  Frage                                  | Antwort
  ---------------------------------------|------------------------------------------
  Wo wird R+MUNI entwickelt?             | Repo 3 — Doku-intern (privat)
  Was ist in Repo 1 (R-MUNI)?            | Blueprint-Kern — Scripts, Struktur, Release
  Was ist in Repo 2 (Doku-public)?       | Doku-Varianten zur Auswahl (CARD/MUNI/DEV)
  Wohin kommt die gewählte Variante?     | 99-doku\ im Kunden-Repo (ein Repo, alles drin)
  Wer hält das Kunden-Repo?             | Kunde — EUMAXL nur auf Einladung
  Werden Kundendaten veröffentlicht?     | Nein — immer privat, Eigentum des Kunden
  Wie kommt Feedback rein?               | GitHub Issues in Repo 1
  Kein Sync ohne Rücksprache?            | Korrekt — Kunde entscheidet


================================================================================
BETA_GitHub_Nutzung | S105 | 2026-04-14 | R+MUNI Blueprint
================================================================================
