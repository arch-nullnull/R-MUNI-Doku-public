================================================================================
SPRINT DEV DOKUMENTATION – R+MUNI
Sprint: Public Rosetta Stone + Kostenaufstellung + Template S101
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : Sprint-DEV-S101-PublicStone-Kosten-Template
Erstellt        : 2026-03-29
Stage           : S1.01 – AKTIV
Ablageort       : R+MUNI Doku-internal\sprints\Sprint-DEV-S101-PublicStone-Kosten-Template.md
Erstellt durch  : EUMAXL + Claude (Pair-Session)
================================================================================


================================================================================
1. AUSLÖSER
================================================================================

Auslöser-Typ (GOV 10.3):
  Entwicklerwunsch + Außenwirkung

Beschreibung:
  R+MUNI hat mit Beta 1.0 erstmals eine öffentliche Doku-Struktur.
  Für den öffentlichen Rosetta-Stone-Ordner fehlte bisher jedes Dokument
  das die Entstehungsgeschichte und den Reifegrad für Außenstehende
  transparent macht — ohne Framework-Jargon, ohne Insider-Voraussetzung.

  Parallel dazu war die Rosetta-Stone-Vorlage noch auf S6-Stand.
  Stage 1.01 braucht eine saubere S101-Vorlage als Basis für alle
  zukünftigen Stones.

  Und die Investitionsaufstellung (Zeit + Geld) war nirgendwo dokumentiert —
  weder intern noch extern.


================================================================================
2. ZIEL
================================================================================

  1. Kostenaufstellung von null bis Beta 1.0 erarbeiten und dokumentieren
  2. Neues Rosetta-Stone-Template im S101-Format erstellen
  3. Öffentlichen Rosetta Stone "Die Entstehung" erstellen —
     Zielgruppe: nicht-technische Entscheider / Management
     Ton: ehrlich und direkt
     Ziel beim Leser: "Das will ich auch haben"

Erfolgskriterium (GOV 10.6):
  Drei fertige, downloadbare .md Dateien im S101-Format.
  Kein S6-Geist mehr im Header. Kein Framework-Jargon im Public Stone.


================================================================================
3. ABGRENZUNG
================================================================================

IN SCOPE:
  - Kostenaufstellung Zeit + Cash für Beta 1.0
  - Rosetta-Stone-Template S101 (ersetzt S6-Vorlage)
  - Öffentlicher Rosetta Stone "Entstehung" — Stage 1 bis 8, Reifegrad,
    ehrliche Aufzeichnung inkl. Seitenhieben

OUT OF SCOPE:
  - Änderungen an bestehenden Rosetta Stones (Blocks 1–8)
  - Änderungen an GOV oder Principles
  - Technische Script-Arbeit
  - Einspielen ins Repo (manuell durch EUMAXL)


================================================================================
4. AUSGANGSLAGE
================================================================================

  - Rosetta-Stone-Vorlage lag noch auf S6-Stand (Rosetta-Stone_Template_S6.md)
  - Kein öffentlicher Rosetta Stone vorhanden — Ordner 03-rosetta_stone
    in der public Doku war leer bzw. nur intern befüllt
  - Investitionsaufstellung existierte nur im Kopf — nirgendwo verschriftlicht
  - Stage-Bezeichnung S6 in Templates noch nicht auf S101 migriert


================================================================================
5. DURCHFÜHRUNG
================================================================================

Schritt 1 — Kostenaufstellung erarbeiten
  Im Dialog erarbeitet. Drei Blöcke definiert:
    A) Lernen, Verstehen, Methodik        ~140 Stunden
    B) Tool-DEV von null bis Beta 1.0     ~240 Stunden
    C) Betakunden & Öffentlichkeitsarbeit  ~90 Stunden
    Gesamt                                ~470 Stunden
    Cash                                  unter 1.000 EUR

  Cash-Detail bewusst nicht ausgeführt — nur Größenordnung nach außen.
  Begründung: für DEV-Zwecke ausreichend, soll nicht herausstechen.

Schritt 2 — Rosetta-Stone-Template S101 erstellen
  Vorlage S6 als Basis gelesen.
  S7 und S8 Stones als Referenz für aktuellen Header-Standard analysiert.
  Neue Vorlage erstellt mit:
    - Stage S1.01 durchgängig
    - "Erstellt durch" als Pflichtfeld mit Platzhalter
    - Sonderformen (Public Stone / FreezeReal) im DEV-Kommentar dokumentiert
    - GOV_Global_S101 + TMP_principles_S101 als Pflicht-Bezüge
  Datei: Rosetta-Stone_Template_S101.md

Schritt 3 — Öffentlicher Rosetta Stone erstellen
  Alle 6 bestehenden Rosetta Stones (Block 1–6) sowie Stage 7 und 8 Stones
  und den FreezeReal S6 Stone als Quellen gelesen.
  Außerdem: README, Install.txt, FREEZE_8, AI_DRIVEN_DEV_METHODE_S8.

  Zielgruppe definiert: nicht-technische Entscheider / Management
  Ton definiert: ehrlich und direkt — wie das README
  Leserziel: "Das will ich auch haben"

  Inhaltliche Entscheidungen:
    - Kein Framework-Mapping — Sonderform "Public Stone"
    - Entstehungsgeschichte Stage für Stage mit Reifegrad-Einschätzung
    - Ehrliche Formulierungen inkl. Seitenhieben (Berater-Slide, "bitte nicht
      anfassen", "niemand muss da mehr rein")
    - Kostenaufstellung integriert — Cash nur als Größenordnung
    - Abschluss: ehrliches Lernfazit ohne Marketingsprache —
      "Das klingt nach Marketing. Es ist Erfahrungsbericht."

  Iterationen: 3 Entwürfe bis finale Version
    Entwurf 1: zu allgemein, kein Stage-für-Stage-Reifegrad
    Entwurf 2: S6-Header verwendet (Fehler erkannt)
    Entwurf 3: final — S101-Header, Stage-Reifegrad, Seitenhiebe, Kosten

  Datei: Rosetta-Stone_Entstehung_Public_S101.md


================================================================================
6. ERGEBNISSE
================================================================================

Deliverable 1:
  Rosetta-Stone_Template_S101.md
  Neue verbindliche Vorlage für alle Rosetta Stones ab Stage 1.01
  Ablage: R+MUNI Doku-public\03-rosetta_stone\

Deliverable 2:
  Rosetta-Stone_Entstehung_Public_S101.md
  Öffentlicher Rosetta Stone — Entstehungsgeschichte und Reifegrad
  Stage 1 bis 8 — für nicht-technische Entscheider
  Ablage: R+MUNI Doku-public\03-rosetta_stone\

Deliverable 3 (in diesem Dokument):
  Sprint-DEV-Doku als Nachweis und Ablage der Session-Erkenntnisse
  Ablage: R+MUNI Doku-internal\sprints\


================================================================================
7. ERKENNTNISSE
================================================================================

  - Die alte S6-Vorlage war im Projekt noch aktiv — Migration auf S101
    war überfällig und ist jetzt erledigt
  - "Public Stone" als Sonderform ist jetzt in der Vorlage verankert —
    damit geht diese Unterscheidung nicht verloren
  - Die Stage-für-Stage-Aufzeichnung mit Reifegrad ist das stärkste
    Element des Public Stone — ehrlicher als jeder Marketingtext
  - Kostenaufstellung gehört dokumentiert — auch wenn man die Zahlen
    nach außen bewusst weich hält
  - Iterationen bei kreativen Dokumenten sind normal und kein Fehler —
    drei Entwürfe für einen Public Stone ist angemessen


================================================================================
8. GOV-CHECK
================================================================================

GOV 10.3  Auslöser dokumentiert                                    ✅
GOV 10.5  Fachlicher Mehrwert benennbar                            ✅
           (Vorlage migriert, Public Stone erstellt, Kosten dok.)
GOV 10.6  Ziel vor Umsetzung definiert                             ✅
GOV 10.7  Zwischenschritte dokumentiert (Schritt 1–3)              ✅
GOV 10.8  Sprint-DEV-Doku erstellt                                 ✅
Rückkopplungsschutz: keine Scripts, keine Stage-3–8-Eingriffe      ✅
Rollentrennung GOV 13: keine externen Inhalte übernommen           ✅


================================================================================
9. OFFENE PUNKTE / NACHFOLGE
================================================================================

  - Beide Deliverables manuell ins Repo einspielen (EUMAXL)
  - Alte S6-Vorlage im Blueprint durch S101-Vorlage ersetzen (EUMAXL)
  - Prüfen ob weitere bestehende Stones auf S101-Header migriert werden
    sollen — Entscheidung bei EUMAXL (kein Sprint-Zwang)


================================================================================
BEZÜGE
================================================================================

[[GOV_Global_S101]]                  Normative Grundlage
[[FREEZE_8]]                         Ausgangszustand dieser Session
[[AI_DRIVEN_DEV_METHODE_S8]]         Methodik-Basis
[[Rosetta-Stone_Template_S101]]      Deliverable 1
[[Rosetta-Stone_Entstehung_Public_S101]]  Deliverable 2


================================================================================
ENDE | Sprint-DEV-S101-PublicStone-Kosten-Template | 2026-03-29
R+MUNI Blueprint | Stage 1.01 | Erstellt: EUMAXL + Claude
================================================================================
