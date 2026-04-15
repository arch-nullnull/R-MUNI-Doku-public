================================================================================
OBS STUDIO — SETUP SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint / EUMAXL Personal Setup
Dokument        : SPRINT_OBSStudio_Setup_S102
Tag             : #dev #sprint #obs #obsstudio #youtube #twitch #s102
Datum           : 2026-04-10
Stage           : S102 — AKTIV
Status          : ABGESCHLOSSEN
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
================================================================================

---

## Kontext

OBS Studio neu aufgesetzt für YouTube Lernvideos (primär) und gelegentliches
Twitch-Streaming (sekundär). Vorheriges Setup und Backlog-Dokument wurden bei
Vault-Cleanup gelöscht. Neuaufbau aus bekanntem Stand — EUMAXL hat Streaming-
Erfahrung (ehem. Twitch Affiliate inkl. Voicemeeter / LAN-Audio / Delay-Sync).

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                  normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]       operative Arbeitsmethode
- [[naming_and_structure_S102]]            Namenskonventionen
- [[STAGE103_ZIELE_S103]]                  nächster Stage — Ausblick
- [[NBX_principles_DEV_S102]]              NBX-Reihe Kontext
- [[FREEZE_1_02]]                          Stage-Baseline

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser
-------------
Auslöser:     Entwicklerwunsch
Beschreibung: Streaming- und Recording-Setup für YouTube Lernvideos und
              gelegentliches Twitch-Streaming. Vault-Cleanup hatte
              vorheriges Backlog-Dokument gelöscht.

1.2 Zieldefinition
-------------------
Ziel:         OBS Studio vollständig einsatzbereit für:
              (A) Aufnahme von Lernvideos für YouTube
              (B) Live-Streaming auf Twitch (bei Bedarf)
              Beide Modi aktivierbar in unter 2 Minuten.

Abgrenzung:   - Kein Video-Editing-Workflow (separater Sprint)
              - Kein YouTube-Kanal-Setup (bereits vorhanden)
              - Keine Gaming-Szenen (bewusst zurückgestellt)

1.3 Hardware / Software Stack
------------------------------
  Hardware:
    - NVIDIA GeForce RTX 2080 Super → NVENC (Encoder)
    - Elgato 4K Pro Capture Card (Dual-PC Setup vorbereitet)
    - Webcam 1 + Webcam 2
    - 3-Monitor-Setup (Monitor 3 = HD Fernseher, Background-View)
    - Flipchart physisch → über Webcam eingefangen

  Software / Audio:
    - OBS Studio (statt ursprünglich geplant: Streamlabs OBS)
    - VCam (Hintergrund-Removal)
    - Logitech Pro Headset (USB direkt)
    - Kein Desktop Audio — bewusst ausgeschlossen
    - Kein Voicemeeter — bewusst vereinfacht
    - Alerts: Browser-Source via Streamlabs

  Zukunft (eigener Sprint):
    - Neuer PC → Elgato 4K Pro Einspeisung → Dual-PC Setup

1.4 Rolle
----------
Aktive Rolle:              DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE — ALLE PHASEN ABGESCHLOSSEN
================================================================================

2.1 Phase 1 — Basis & Szenen
------------------------------
OBS Studio installiert, Plugins eingerichtet, Stinger-Übergänge konfiguriert,
Szenen und Views angelegt, Twitch verbunden und Tags auf Coding umgestellt.

Artefakte:    kein separates Artefakt
GOV-Konform:  JA

2.2 Phase 2 — Quellen
-----------------------
Webcam 1 + 2 eingerichtet, VCam konfiguriert (Hintergrund-Removal),
Elgato 4K Pro eingerichtet, Logitech Pro Headset als Mikrofon eingerichtet,
alle Quellen in Szenen zugewiesen.

Artefakte:    kein separates Artefakt
GOV-Konform:  JA

2.3 Phase 3 — Branding & Overlays
------------------------------------
Altes Overlay-Set (5GB, gekauft + custom made, copyright-sauber) gesichtet.
Animierte Cam-Frames und Overlays importiert und auf Szenen angewendet.
YT-Szenen: ablenkungsfreies Layout ohne Stream-Overlay.

Artefakte:    kein separates Artefakt
GOV-Konform:  JA

2.4 Phase 4 — Aufnahme-Settings
----------------------------------
NVENC konfiguriert, 1080p60 VBR CQ18-20, MKV-Format, 250GB Temp-Storage.

Artefakte:    kein separates Artefakt
GOV-Konform:  JA

2.5 Phase 5 — Stream-Settings
--------------------------------
NVENC CBR 6000kbps, 1080p60, Twitch-Verbindung verifiziert.

Artefakte:    kein separates Artefakt
GOV-Konform:  JA

2.6 Phase 6 — Alerts
----------------------
Streamlabs Account (via Twitch-Login) gefunden, Alert-Box konfiguriert,
Browser-Source URL in OBS eingebunden.

Artefakte:    kein separates Artefakt
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: OBS Studio statt Streamlabs OBS
  Auslöser:    OBS Studio bereits installiert und lauffähig beim Setup-Start
  Ergebnis:    OBS Studio wird verwendet
  Begründung:  Kein Cloud-Bedarf, EUMAXL kennt sich aus, Plugins decken
               alle Anforderungen ab — Alerts über Browser-Source
  GOV-Bezug:   GOV 10.3 — Entwicklerwunsch als zulässiger Auslöser
  Auswirkung:  Alerts via Browser-Source statt SLOBS-integriert — kein
               funktionaler Nachteil
  Rückwirkung: NEIN

Entscheidung: NVENC als Encoder
  Auslöser:    NVIDIA RTX 2080 Super verfügbar
  Ergebnis:    NVENC für Aufnahme (VBR CQ18-20) und Stream (CBR 6000kbps)
  Begründung:  Hardware-Encoding, CPU-schonend, hohe Qualität
  GOV-Bezug:   kein direkter Bezug
  Auswirkung:  Stabil und performant — kein Nachteil
  Rückwirkung: NEIN

Entscheidung: 1080p60 statt 4K
  Auslöser:    Storage-Situation (250GB Temp), Twitch-Limit, Use Case
  Ergebnis:    1080p60 für Aufnahme und Stream
  Begründung:  Coding-Content braucht keine 4K. Twitch-Limit ist 1080p60.
               Storage-effizient. Musik-freier Schnitt bei Bedarf.
  GOV-Bezug:   kein direkter Bezug
  Rückwirkung: NEIN

Entscheidung: Nur Voice — kein Desktop Audio, kein Voicemeeter
  Auslöser:    Use Case Lernvideos / Coding-Stream
  Ergebnis:    Logitech Pro USB direkt, kein Voicemeeter, kein Desktop Audio
  Begründung:  Copyright-Risiko eliminiert. Einfacher, stabiler.
               Hintergrundmusik bei Bedarf im Schnitt (royalty-free).
  GOV-Bezug:   kein direkter Bezug
  Rückwirkung: NEIN

Entscheidung: Gaming-Szenen zurückgestellt
  Auslöser:    Nicht Teil des R+MUNI Coding-Setups
  Ergebnis:    Keine Gaming Scene Collection in diesem Sprint
  Begründung:  Eigener Sprint bei Bedarf — 2-Minuten-Setup in OBS Studio
  GOV-Bezug:   kein direkter Bezug
  Rückwirkung: NEIN

Entscheidung: Altes Overlay-Set selektiv verwenden
  Auslöser:    5GB Overlay-Library auf PC 3 gefunden
  Ergebnis:    Cam-Frames (animiert) + Overlays verwendet.
               Soundboards / Meme-Assets → nicht verwendet.
  Begründung:  Alles gekauft oder custom made → copyright-sauber.
               Neutral für Coding-Content geeignet.
  GOV-Bezug:   kein direkter Bezug
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN
================================================================================

Abweichung: Tool-Wechsel Streamlabs OBS → OBS Studio
  GOV-Regel:   Sprint ursprünglich für Streamlabs OBS geplant
  Begründung:  OBS Studio bereits installiert — kein funktionaler Nachteil
  Wirkung:     Auf diesen Sprint begrenzt — kein Präzedenz


================================================================================
5. OFFENE PUNKTE / FOLGE-SPRINTS
================================================================================

| Punkt | Priorität | Nächste Aktion |
|-------|-----------|----------------|
| Dual-PC Setup (Elgato + neuer PC) | Mittel | Eigener Sprint wenn neuer PC da |
| Gaming Scene Collection | Niedrig | Bei Bedarf — kein Druck |


================================================================================
6. STAGE-ABSCHLUSS (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          JA
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               JA — diese Datei + Confluence-Seite
GitHub-Sync:                      NICHT ERFORDERLICH
Atlassian-Sync:                   ERLEDIGT


================================================================================
7. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Streaming-Erfahrung aus alten Jahren hat Setup massiv beschleunigt
  - Bewusste Vereinfachung (kein Voicemeeter, nur Voice) — stabil und sauber
  - Altes Overlay-Set vollständig und copyright-sauber — kein Neuaufbau nötig
  - OBS Studio + Browser-Source schlanker als Streamlabs OBS

Was beim nächsten Mal anders:
  - Sprint-Dokument von Anfang an auf OBS Studio auslegen
  - Overlay-Set-Standort früher dokumentieren (war auf PC 3)

Erkenntnisse die Dokumente verändern:
  - Gaming Scene Collection → eigener Sprint bei Bedarf: NEIN für jetzt
  - Dual-PC Setup Sprint anlegen wenn neuer PC eingetroffen: JA

---

## Bezüge

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[FREEZE_1_02]]                            Stage-Baseline S102
[[STAGE103_ZIELE_S103]]                    nächster Stage

---

================================================================================
SPRINT_OBSStudio_Setup_S102 | DEV | ABGESCHLOSSEN | 2026-04-10 | R+MUNI Blueprint
================================================================================
