================================================================================
SPRINT DEV-DOKUMENTATION
================================================================================
Projekt            : R+MUNI Blueprint
Sprint-Bezeichnung : SPRINT-EXT01-ExterneKommunikation
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
Auslöser-Typ : Strategische Kurskorrektur (Stage-5-Erfahrung aus Livebetrieb)

Vorgeschichte:  Im Rahmen von SPRINT-RMNP01 wurde das Atlassian JSM/CSM
                Portal als Endkunden-Einstieg aufgebaut. Im Livebetrieb
                (2026-03-12) wurden folgende Free-Plan-Grenzen aufgedeckt:

                  - JSM Portal: kein anonymer Zugang ohne Login (Paid Feature)
                  - Confluence: keine öffentlichen Seiten ohne Login (Paid Feature)
                  - Confluence ↔ Jira Live-Verknüpfungen: eingeschränkt im Free

                Erkenntnis: Atlassian ist als Pflicht-Säule für Endkunden
                nicht vereinbar mit der R+MUNI Philosophie (kostenlos, offen,
                kein Zwang, tool-agnostisch).

Entscheidung:   Atlassian wird aus der Pflicht-Säule zur Option degradiert.
                Externe Kommunikation und öffentliche Außenseite werden
                auf GitHub / GitHub Pages / Obsidian verlagert.
                Atlassian bleibt im Blueprint als "wenn du es ohnehin hast"
                Option dokumentiert — kein Eingriff in bestehende Struktur.


--------------------------------------------------------------------------------
2. ZIEL DES SPRINTS
--------------------------------------------------------------------------------

Primärziel:
  Definition und Dokumentation der neuen externen Kommunikationsstrategie
  für R+MUNI auf Basis von GitHub / GitHub Pages / Markdown / Obsidian.

Nebenziel:
  Atlassian im Blueprint sauber als Option (nicht Pflicht) verankern.
  Neuen Tool-Stack und GitHub-Repo-Struktur dokumentieren.

Abgrenzung:
  - Kein Eingriff in Stage 3/4 Scripts
  - Atlassian-Setup bleibt erhalten — wird nicht abgebaut, nur neu bewertet
  - SPRINT-RMNP01 bleibt als dokumentierter Lernschritt im Blueprint
  - GitHub Pages Setup → eigener Sprint EXT02
  - Atlassian Migration zu Markdown → eigener Sprint EXT03


--------------------------------------------------------------------------------
3. KONZEPTENTSCHEIDUNGEN (Pair-Session)
--------------------------------------------------------------------------------

3.1 Strategische Grundsatzentscheidung
----------------------------------------
Entschieden: Atlassian = Option, nicht Säule

  Begründung:
  - R+MUNI Philosophie: kostenlos, offen, kein Zwang, tool-agnostisch
  - Atlassian Free zwingt Kunden in eine kostenpflichtige Welt
    sobald sie die Basisfunktionen wirklich nutzen wollen
  - EUMAXL will kein "Atlassian Enabler" sein
  - Kunden sollen nicht durch R+MUNI in eine Tool-Abhängigkeit geführt werden

  Was bleibt:
  - Atlassian bleibt als persönliches Arbeitsmittel von EUMAXL
  - JSM Portal RMNP bleibt aktiv als Feedback-Kanal (Option A)
  - Confluence bleibt für interne Blueprint-Dokumentation
  - Blueprint dokumentiert Atlassian als eine von mehreren Optionen

3.2 Neuer Tool-Stack externe Kommunikation
-------------------------------------------
Entschieden: Obsidian + GitHub + GitHub Pages

  Obsidian (kostenlos, lokal)
    → Markdown Editor mit Live-Preview
    → Bilder per Drag & Drop
    → Graph View für Verlinkungen
    → Git Plugin → direkter Push zu GitHub ohne Kommandozeile
    → Kein Cloud-Zwang, lokale Dateien
    → Bereits installiert: Version 1.12.4

  GitHub
    → Sync- und Backup-Tool — nicht primäre Außenseite
    → Versionierung aller Inhalte
    → GitHub Issues als offener Feedback-Kanal (Option B zu JSM Portal)
    → Zielgruppe ist entwicklerlastig — kein direkter Endkunden-Einstieg

  GitHub Pages
    → Markdown-Dateien werden automatisch zur fertigen Website
    → Kostenlos, kein Hosting, kein CMS, kein Aufwand
    → Elegante Brücke zwischen lokalem Obsidian und öffentlicher Außenseite
    → Aktivierung in EXT02

  Langfristig (Beta 1.0)
    → Eigene Domain + PHP Frontend oder Vereins-Subdomain
    → GitHub Pages als Zwischenlösung bis dahin

3.3 GitHub Repo-Struktur (finale Entscheidung)
------------------------------------------------
Entschieden: 5 Repos mit klarer Trennung Public/Private

  arch-nullnull/R-MUNI               PUBLIC  → Blueprint, Scripts, Kerndoku
  arch-nullnull/R-MUNI-Doku-public   PUBLIC  → Externe Doku, GitHub Pages Basis
  arch-nullnull/R-MUNI-MLAT          PRIVATE → Atlassian-spezifisches Setup
  arch-nullnull/R-MUNI-Doku-internal PRIVATE → Interne Notizen, Kundendoku
  arch-nullnull/R-MUNI-creative      PRIVATE → Blog-Ideen, Kreativkram

  Intern-Schutz via .gitignore:
    → intern/ und .obsidian/ werden nie nach GitHub gepusht
    → Inhalte aus intern/ können bei Bedarf manuell nach public verschoben werden

3.4 Obsidian Vault-Struktur
-----------------------------
Entschieden: Zwei separate Vaults

  Vault 1 — R+MUNI Blueprint (C:\Prototyping\R+MUNI)
    → Lesen und Editieren der bestehenden Blueprint-Dateien
    → Kein eigenes Git — Blueprint-Repo bereits vorhanden
    → .gitignore mit .obsidian/ damit Settings nicht ins Repo wandern

  Vault 2 — R+MUNI Doku (eigener Ordner)
    → Eigene Git-Repos (public + internal getrennt)
    → Obsidian als primärer Editor für alle externen Inhalte

3.5 Atlassian Neubewertung im Blueprint
-----------------------------------------
Neue Einstufung:

  JSM/CSM Portal   → Option A für Feedback (für Atlassian-User)
  Confluence       → Persönliches Arbeitsmittel EUMAXL, internes Wiki
  Jira             → Persönliches Ticketing EUMAXL, internes Backlog
  GitHub Issues    → Option B für Feedback (offen, kein Login)

3.6 Geschäftsmodell-Kontext
-----------------------------
  EUMAXL ist Produzent — nicht Verkäufer
  → Vertrieb und Marketing ist ausgelagert
  → Kunden sind Wiederverkäufer
  → Öffentliche Außenseite dient Wiederverkäufern als Referenz
  → Keine direkte Endkunden-Akquise durch EUMAXL selbst


--------------------------------------------------------------------------------
4. UMSETZUNG — ERLEDIGTE SCHRITTE
--------------------------------------------------------------------------------

  ✅ Strategische Entscheidung gefallen: Atlassian = Option, nicht Säule
  ✅ Obsidian installiert (Version 1.12.4)
  ✅ Vault 1 auf R+MUNI Blueprint Root angelegt
  ✅ Vault 2 für R+MUNI Doku angelegt
  ✅ .gitignore Konzept definiert (intern/ + .obsidian/)
  ✅ GitHub Repo-Struktur aufgebaut (5 Repos, Public/Private klar getrennt)
  ✅ GitHub Pages als elegante MD-zu-Website Lösung identifiziert


--------------------------------------------------------------------------------
5. OFFENE SCHRITTE — FOLGE-SPRINTS
--------------------------------------------------------------------------------

  EXT02 — GitHub Pages Setup
    [ ] GitHub Pages in R-MUNI-Doku-public aktivieren
    [ ] Erste index.md in Obsidian erstellen
    [ ] "Ich bin ein Code-Noob" Post von Confluence nach Markdown migrieren
    [ ] GitHub Issues Templates anlegen (Bug, Feature Request, Frage)

  EXT03 — Atlassian Migration
    [ ] Relevante Confluence-Inhalte nach Markdown migrieren
    [ ] Entscheiden was public und was internal bleibt
    [ ] Confluence "Externes Wiki" Startseite korrigieren
        → Satz "100% öffentlich erreichbar" entfernen


--------------------------------------------------------------------------------
6. ERKENNTNISSE FÜR DEN BLUEPRINT
--------------------------------------------------------------------------------

  • Free Plan Grenzen sind kein Bug — sie sind Atlassian's Geschäftsmodell
    → Wer Free nutzt muss mit Einschränkungen leben oder zahlen
    → Für R+MUNI Philosophie nicht akzeptabel als Pflicht-Säule

  • Tool-Agnostik ist ein aktiver Schutz für Kunden
    → Kein Tool darf zur impliziten Pflicht werden durch R+MUNI
    → GitHub ist offener, versioniert, kostenlos — passt besser

  • GitHub Pages ist keine Entwickler-Lösung — es ist eine elegante
    Markdown-zu-Website Pipeline ohne Hosting, CMS oder Aufwand
    → Obsidian schreiben → Git pushen → Website live
    → Für Beta-Phase ideal, Domain/PHP kommt bei 1.0

  • Obsidian + GitHub = wartbare Kombination ohne Vendor Lock-in
    → Markdown bleibt in der Hand des Entwicklers
    → Kein Abo, kein Upgrade-Druck, kein proprietäres Format

  • SPRINT-RMNP01 war kein Fehler — es war notwendige Erfahrung
    → Atlassian ausprobieren war richtig
    → Die Grenzen sind jetzt dokumentiert und für andere nutzbar
    → "Fail fast, document well" ist AI-Driven Development in Reinform

  • Atlassian bleibt wertvoll — als persönliches Arbeitsmittel
    → Jira für eigenes Ticketing — unersetzt
    → Confluence für interne Doku — gut genug
    → JSM Portal für Kunden die ohnehin Atlassian nutzen — okay
    → Pflicht für alle Kunden — nein


================================================================================
SPRINT-EXT01-ExterneKommunikation
ABGESCHLOSSEN | 2026-03-12
R+MUNI Blueprint | Stage 5 | Erstellt durch: EUMAXL + Claude (Pair-Session)
================================================================================
[[SPRINT-5-5-FREEZE]]