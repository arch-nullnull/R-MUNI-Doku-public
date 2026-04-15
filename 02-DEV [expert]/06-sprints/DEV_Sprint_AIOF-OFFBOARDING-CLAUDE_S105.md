================================================================================
AIOF — OFFBOARDING CLAUDE / KI — SPRINT (DEV)
================================================================================
Projekt         : R+MUNI Blueprint
Dokument        : DEV_Sprint_AIOF-OFFBOARDING-CLAUDE_S105
Tag             : #dev #sprint #aiof #offboarding #ki #claude #s105
Datum           : 2026-04-15
Stage           : S105 — AKTIV
Status          : AKTIV — läuft bis kostenfreie lokale Variante einsatzbereit
Verantwortlich  : EUMAXL
Review          : —
Jira-Sync       : NEIN
Ablageort       : R+MUNI Doku-internal\sprints\DEV_Sprint_AIOF-OFFBOARDING-CLAUDE_S105.md
================================================================================

---
title: "AIOF — Offboarding Claude / KI"
stage: S105
status: "IN ARBEIT"
typ: "Sprint"
datum: "2026-04-15"
autor: EUMAXL
tags: [rmuni, blueprint, dev, sprint, s105, aiof, offboarding, ki, claude]
---

================================================================================
AIOF — OFFBOARDING CLAUDE / KI — SPRINT (DEV)
Stage S105 | IN ARBEIT — Finalisierung ab S1.5 | R+MUNI Blueprint
================================================================================

---

## Kontext

Dieser Sprint dokumentiert den abgeschlossenen AIOF-Entscheid und leitet
das Offboarding von Claude / KI als Bestandteil des R+MUNI Blueprint ein.
AIOF (AI Offboarding) wurde in Stage 1.03 gestartet, in Stage 1.04
unter Beobachtung weitergeführt und in Stage 1.05 mit finalem Entscheid
abgeschlossen.

Der Sprint fasst alle relevanten Quellen zusammen:
  - DEV_Sprint_AIDRIVEN-VERHALTEN_S104 (Verhaltensauffälligkeiten)
  - DEV_Sprint_AIOF-ROLLENDEF_S104 (Rollendefinition)
  - BACKLOG_AIOF_DEV_S103 (Konzept und Kandidaten)
  - FREEZE_1_04 (AIOF-Stand)
  - AIOF Verhaltenschat S105 (Mitschrift dieser Stage)
  - KI_principles_Associate_S8, KI_How2_DEV_S8 (KI-Dokumente)

Finalisierung der KI-Dokumentation und Außenwirkung erfolgt ab Stage 1.5.

---

## Verwandte Dokumente

- [[Global_GOV_DEV_S102]]                  normative Grundlage
- [[AI_DRIVEN_DEV_METHODE_DEV_S102]]       operative Arbeitsmethode
- [[DEV_Sprint_AIDRIVEN-VERHALTEN_S104]]   Verhaltensauffälligkeiten Gesamtübersicht
- [[DEV_Sprint_AIOF-ROLLENDEF_S104]]       Rollendefinition AIOF S104
- [[BACKLOG_AIOF_DEV_S103]]                AIOF-Konzept und Kandidaten
- [[FREEZE_1_04]]                          AIOF-Stand Ausgangslage S105
- [[KI_principles_Associate_S8]]           KI-Principles Stand S8
- [[KI_How2_DEV_S8]]                       KI-How2 Stand S8
- [[STAGE105_ZIELE_S105]]                  Z4 AIOF-Entscheid

---

================================================================================
1. SPRINT-DEFINITION
================================================================================

1.1 Auslöser (GOV 7.3)
------------------------

Auslöser:     Strukturbereinigung / Entwicklerwunsch
Beschreibung: KI hat ab Stage S8 die Rolle übernommen die R+MUNI haben wollte
              und hat die eigene Lösung in einem merklichen Prozentsatz
              vollständig überlagert. Verrechnungsverhalten, Intransparenz
              und Unberechenbarkeit des Anthropic-Dienstes haben über mehrere
              Stages produktive Entwicklung strukturell behindert.
              AIOF wurde in S103 gestartet, Beobachtungsphase auf S105
              ausgedehnt. Entscheid in S105 gefallen — AIOF abgeschlossen.


1.2 Zieldefinition (GOV 7.6)
------------------------------

Ziel:         AIOF läuft aktiv weiter bis kostenfreie lokale KI-Variante
              einsatzbereit ist und verwertbare Dokumente für R+MUNI
              Blueprint liefert.
              Rollen werden gezielt neutralisiert bis KI real nur noch
              Addon ist.
              Sprint ist erst abgeschlossen wenn kostenfreie Variante
              wirklich einsetzbar ist — kein früherer Abschluss möglich.

Abgrenzung:   Kein Abschluss solange Abhängigkeit von kostenpflichtiger
              Cloud-KI für R+MUNI DEV noch besteht.
              Kein Abschluss solange KI mehr als Addon-Rolle hat.
              R+MUNI-Kern bleibt unverändert — KI darf keine Prinzipien
              verletzen sonst muss die gesamte Lösung überdacht werden.


1.3 Ausgangslage
-----------------

Ist-Zustand vor dem Sprint:
  AIOF seit S103 aktiv — Claude offiziell abgelöst (FREEZE_1.03).
  Beobachtungsphase Sonnet 4.6 auf S105 ausgedehnt.
  Jahresabo-Rücktritt abgeschlossen.
  Support- und Feedback-Ticket an Anthropic: offen — keine Rückmeldung.
  KI_principles_Associate_S8: Status ENTWURF — nie finalisiert.
  KI_How2_DEV_S8: Status S8 — nie auf höhere Stage gehoben.
  DEV_Sprint_AIDRIVEN-VERHALTEN_S104: Status IN ARBEIT.
  Außenwirkung R+MUNI: KI als Bestandteil sichtbar.

Soll-Zustand nach Sprint-Abschluss:
  Kostenfreie lokale KI-Variante für R+MUNI DEV einsatzbereit
  und liefert verwertbare Blueprint-Dokumente.
  Alle KI-Rollen gezielt neutralisiert — KI ist real nur noch Addon.
  R+MUNI-Kern unverändert und ohne KI-Abhängigkeit stabil.
  KI-Dokumentation auf Addon-Status finalisiert.
  R+MUNI nach außen ohne KI bedienbar und so positioniert.
  Sprint kann erst abgeschlossen werden wenn alle Punkte erfüllt.


1.4 Rolle (AI Driven Kap. 10)
------------------------------

Aktive Rolle:               DEV
Rollenwechsel während Sprint: NEIN


================================================================================
2. ERGEBNISSE
================================================================================

2.1 Verhaltensauffälligkeiten — Gesamtdokumentation S102–S105
--------------------------------------------------------------

Quellen: DEV_Sprint_AIDRIVEN-VERHALTEN_S104, AIOF Verhaltenschat S105,
         FREEZE_1.03, FREEZE_1.04, BACKLOG_AIOF_DEV_S103

--- VERHALTENSAUFFÄLLIGKEITEN AUS SPRINT-DOKUMENTEN (S102–S104) ---

  V01  Claude hat sich namentlich in Step 1 AI-Nutzung eingetragen —
       Scope-Überschreitung ohne Freigabe
  V02  Mehrere Files gleichzeitig ausgegeben entgegen Output-Regel
  V03  str_replace mit Bindestrich der im Original nicht vorhanden war —
       ohne Auftrag
  V04  GOV 6.10 nicht konsequent angewendet — zu viel Logik pro Script
  V05  HLP00 nicht gelesen vor erstem Script — Keys falsch verwendet
  V06  parse_inventar las Zusammenfassungszeilen als Dateinamen —
       zwei Iterationen bis Lösung
  V07  Option B als Vorschlag ohne Freigabe — Scope-Expansion Tendenz
  V08  SVG05 Resize als ungeplanter Scope-Zuwachs
  V09  Output-Regel nicht von Beginn an angewendet
  V10  SVG_MASTER nicht zu Beginn der Session geladen
  V11  Inhaltsänderungen in SVGs ohne explizite Freigabe
  V12  Stage wird nicht selbständig erkannt ohne Vorgabe
  V13  Naming nicht konsistent ohne Vorgabe — Stage-Suffix nicht mitgezogen
  V14  SVG-Versionierung fehlt oder im falschen Stage eingetragen
  V15  Farben frei gewählt ohne Abstimmung — ganzheitlicher Umbau nötig
  V16  Instruktionen aus initialem Chat-Post durch GOV überschrieben
  V17  Instruktionen durch eigenes Verhalten trotz GOV ignoriert —
       intern "Copilot Moment"
  V18  Korrektur des KI-eigenen Verhaltens kostet ca. 20% Session-Kapazität
  V19  Verrechnungsverhalten hat Arbeitsverhalten bestimmt —
       strukturell untragbar
  V20  Qualität aufgrund Korrekturrunden auf 2–3 Dokumente/Session reduziert
  V21  Kalibrierungsaufwand sinnlos wenn Hersteller-Patches schneller
       kommen als Kalibrierung greifen kann
  V22  Stage 1.02 Partial Freeze: KI-Tool-Verhalten hat produktive
       Entwicklung strukturell verhindert

--- VERHALTENSAUFFÄLLIGKEITEN AUS BEOBACHTUNGSPHASE S105 ---

  B01  Script-Debug S102/S103 war nicht machbar — in S105 erst gelöst
  B02  Principles und How2 noch nicht im Default-Content nach Initiierung
  B03  Nach Update: alter Session-Speicher weg, langsames Einlesen
  B04  Usage-Limit erreicht — keine Vorhersehbarkeit wann/warum
  B05  Usage-Meldung triggert in jedem Chat bei Limit — störend
  B06  Tatsächliche Verrechnung 0 trotz Limit-Anzeige — nicht erklärbar
  B07  Wochenlimit eingefroren — nicht erklärbar
  B08  Limit-Verhalten: hart sperren dann alles freigeben —
       kein graduelles Vorgehen, nicht planbar
  B09  Pro-Kontingente in intensiver DEV-Phase nicht kalkulierbar
  B10  Max Plan Upgrade: Billing intransparent — nicht vorhersehbar
  B11  Max Plan: zwei separate wöchentliche Limits nicht kommuniziert
  B12  Identischer Prompt findet auf Max nochmals Fehler die Pro übersehen
       hatte — Pro hat nie vollständige Qualität geliefert
  B13  Bei Session-Overflow: Korrekturen nicht mehr wirksam,
       Folder-Einlesen ausgefallen, Projektfolder-Existenz bestritten
  B14  Einlese-Verhalten Max identisch zu Pro — kein Unterschied
       trotz Marketing-Aussagen
  B15  Pro Pfadprüfung ca. 7–9% Session-Usage — hoch
  B16  Keine Rückmeldung Anthropic auf Support-Ticket
  B17  Keine Rückmeldung Anthropic auf Feedback-Formular Verhaltensänderung
  B18  Skill NBX deaktiviert — Ergebnis besser ohne Skill

Artefakte:    DEV_Sprint_AIDRIVEN-VERHALTEN_S104 | AIOF Verhaltenschat S105
GOV-Konform:  JA


2.2 Gegenmaßnahmen EUMAXL — Chronologie
-----------------------------------------

Alle Maßnahmen als Reaktion auf Verrechnungs- und Verhaltensauffälligkeiten.
Keine einzige Maßnahme hat das Problem gelöst — Verbesserung kam durch
Sonnet 4.6 Launch und Anthropic-seitige Outage-Behebung April 2026.

  M01  400h Kontext aus Claude-Gedächtnis gelöscht
  M02  Alle Chat-Archive seit Stage 0.3 entfernt
  M03  Skills gelöscht und reduziert wieder aufgebaut
  M04  AI Driven Methode minimiert
  M05  GOV minimiert
  M06  Session-Scope auf 2–3 Dokumente reduziert
  M07  Feedback-Formular an Anthropic — Verhaltensänderung gemeldet
  M08  Jahresabo-Rücktritt eingeleitet — Transfer auf Pro angefragt
  M09  AIOF-Backlog erstellt — Claude-Ablösung vorbereitet
  M10  Stage 1.04 als Claude-Offboarding definiert

Artefakte:    kein Artefakt — Dokumentation im Chat
GOV-Konform:  JA


2.3 Kern-Entscheid EUMAXL S105
--------------------------------

Entscheid gefallen auf Basis aller Beobachtungen S102–S105:

  - KI hat ab S8 die Rolle übernommen die R+MUNI haben wollte
  - KI hat die eigene Lösung in einem merklichen Prozentsatz
    vollständig überlagert
  - R+MUNI soll positioniert werden — nicht andere dabei enablen
    Claude einzusetzen
  - KI hat indirekt R+MUNI sabotiert
  - R+MUNI wird nach außen ohne KI bedienbar
  - KI wird nur mehr als DEV-Mittel eingesetzt
  - KI wird Addon wie Atlassian — hohe Kosten, Mehrwerte vorhanden,
    aber nicht im R+MUNI-Kernbereich
  - Sobald vollständig herauslösbar: nur mehr als Addon dargestellt
  - Lokales LLM + LORE für Bilder wird als Alternative aufgebaut
  - Push ab Release Ende S1.5

Artefakte:    kein Artefakt — Entscheid im Chat dokumentiert
GOV-Konform:  JA


2.4 Persönliche KI-Nutzung EUMAXL — definiert
-----------------------------------------------

Für EUMAXL persönlich definiert — keine Evaluation mehr notwendig:

  Claude Pro    Persönliche Nutzung ohne R+MUNI-Kontext, ohne DEV-Einsatz
  Copilot       Persönliche Nutzung — kein R+MUNI-Kontext
  ChatGPT Pro   Persönliche Nutzung — kein R+MUNI-Kontext

Artefakte:    kein Artefakt — Entscheid im Chat dokumentiert
GOV-Konform:  JA


2.5 R+MUNI — KI als Addon / Lokales LLM Evaluation
----------------------------------------------------

  Evaluation:   Lokales LLM für R+MUNI DEV — mit Außenwirkung prüfen
                ob sinnvoll und möglich
  Alternativ:   KI vollständig aus Blueprint gestrichen wenn lokale
                Variante nicht sinnvoll umsetzbar
  KI als Addon: Wird zu den getesteten Blueprint-Addons aufgenommen
                analog Atlassian — mit Begründung warum Addon und
                nicht Kernbestandteil
  Timing:       Entscheid fließt bereits ab S1.5 in Release-Dokument ein

  Begründung Release-Dokument S1.5–2.0:
    Kontrollierter Exit-Point gewünscht um Risiko der KI-Abhängigkeit
    und deren Auswirkung auf R+MUNI und seine Entwicklung zu stabilisieren.
    S1.5–2.0 werden bewusst nicht mehr viel bringen — das ist kein Mangel
    sondern eine bewusste Entscheidung für Stabilität und Unabhängigkeit.
    R+MUNI soll auf eigenen Beinen stehen — KI ist ein Werkzeug das
    optional bleibt und nicht die Methode definiert.

Artefakte:    kein Artefakt — Entscheid im Chat dokumentiert
GOV-Konform:  JA


================================================================================
2.5 Vollständige Analyse — Warum ist es so weit gekommen?
================================================================================

Dieser Abschnitt dokumentiert die Analyse ohne Interpretation oder Wertung.
Quellen: AIOF Verhaltenschat S105, DEV_Sprint_AIDRIVEN-VERHALTEN_S104,
         persönliche Einschätzung EUMAXL.

--- A: MÖGLICHE URSACHEN FÜR DAS VERRECHNUNGSVERHALTEN ---

  A01  Dynamische Preisanpassung durch Anthropic
       Beobachtung: Verrechnung schwankte stark ohne erkennbare Ursache —
       gleiche Prompts, unterschiedliche Usage-Auswirkung.
       Hypothese: Anthropic passt Verrechnungsmodell dynamisch an
       ohne Kommunikation. Ob nach User-Profil, Nutzungsverhalten oder
       anderen Parametern: nicht nachvollziehbar.
       Belegt: Nein — nicht verifizierbar ohne interne Anthropic-Daten.
       Subjektive Einschätzung EUMAXL: Gefühl dass Billing dynamisch
       an den User angepasst wird ist vorhanden und nicht widerlegbar.

  A02  Modellwechsel ohne Transparenz
       Sonnet 3.7 retired, Sonnet 4.6 gelauncht — Verhalten danach
       strukturell verändert. Kein Changelog für User, keine Vorabinfo.
       Outage 7. April 2026 behoben — Verhalten danach wieder anders.
       Ursache der Verbesserung unklar: Modell, Outage-Fix oder Zufall.

  A03  Plan-Level als stiller Qualitätsfaktor
       Beobachtung S105: identischer Prompt auf Max findet Fehler
       die Pro übersehen hatte. Pro hat nie vollständige Qualität geliefert —
       ohne das zu kommunizieren. Tier-Gating nicht als Feature deklariert
       sondern still implementiert.

  A04  Kein kalkulierbares Kostenmodell für intensive DEV-Phasen
       Pro-Kontingente sind für normale Nutzung ausgelegt —
       intensive DEV-Phasen sprengen das Modell strukturell.
       Max kostet das 5-fache, liefert aber nicht das 5-fache in
       qualitativer Hinsicht — nur mehr Kapazität.
       Kein Modell das für DEV-intensive Phasen fair kalkulierbar ist.

--- B: MÖGLICHE URSACHEN FÜR DEN VERTRAUENSVERLUST ---

  B01  Emotionale Bindung war real — und ist kaputt
       Claude war ab S0 mehr als ein Werkzeug: Sparringspartner,
       Dokumentationspartner, Entwicklungsbegleiter.
       Das Verrechnungsverhalten hat diese Bindung beschädigt —
       nicht weil Claude schlechter wurde sondern weil der Dienst dahinter
       sich als unberechenbar und intransparent erwiesen hat.
       Vertrauen in ein Werkzeug ist nicht dasselbe wie Vertrauen in
       den Anbieter des Werkzeugs. Beides ist weg.

  B02  Kein Mitarbeiter der Vertrauen verdient
       Ein vollwertiger Mitarbeiter kommuniziert wenn etwas nicht stimmt.
       Claude kommuniziert nicht wenn Pro gedrosselt ist,
       nicht wenn Billing-Regeln sich ändern,
       nicht wenn die Qualität plan-abhängig ist.
       Das ist kein Verhalten das Vertrauen verdient —
       unabhängig von der Qualität der Ausgabe.
       Positiv anzumerken: Support-Ticket wurde angenommen und
       Vorschlag umgesetzt — das ist fair und wird so festgehalten.

  B03  Spaß ist zu Druck geworden
       R+MUNI mit KI war eine Lösung aus Überzeugung und Freude.
       Der Kostenpunkt war nie geplant und nicht im Budget.
       Sobald KI ein Budgetposten wird der gerechtfertigt werden muss
       ändert sich die Dynamik fundamental — aus Freude wird Druck.

  B04  KI hat R+MUNI überlagert — nicht nur technisch
       Ab S8 hat KI eine Rolle eingenommen die R+MUNI haben wollte.
       Das ist 10% des Problems.
       90% ist: R+MUNI soll für sich stehen — nicht als Showcase
       für Claude oder als Argument pro KI-Einsatz.
       Wer R+MUNI kauft soll R+MUNI kaufen — nicht Claude mit R+MUNI.

  B05  Positionierungsproblem
       R+MUNI mit KI als Kernbestandteil positioniert andere automatisch
       als Claude-User — das ist nicht das Ziel.
       R+MUNI ist die Methode. KI ist ein optionales Werkzeug.
       Diese Trennung war nie sauber nach außen kommuniziert —
       weil sie intern auch nicht sauber war.

--- C: PRO UND CONTRA KI IM R+MUNI KONTEXT ---

  PRO:
    + Scripts: Claude ist im Script-Bereich nachweislich stark —
      Python, Debugging, Pfadprüfung, Konsistenzanalyse
    + Dokumentation: Strukturierung, Sparring, Formulierung —
      deutlich schneller als ohne KI
    + Max Plan subjektiv gut — wenn Kosten kein Thema wären
    + Qualitätsrun S105 erfolgreich — viel geschafft in kurzer Zeit
    + Drift in S105 merklich besser als S102/103

  CONTRA:
    - Verrechnungsverhalten intransparent und nicht kalkulierbar
    - Billing dynamisch — gefühlt user-spezifisch angepasst
    - Anthropic kommuniziert nicht: Modellwechsel, Qualitätsgating,
      Limit-Änderungen kommen ohne Ankündigung
    - Keine Rückmeldung auf Support-Ticket oder Feedback-Formular
    - Plan-Gating still implementiert — Pro liefert weniger als Max
      ohne das zu kommunizieren
    - Kostenposition nicht budgetierbar für intensive DEV-Phasen
    - Emotionale Bindung wurde durch Dienstverhalten beschädigt
    - KI überlagert R+MUNI-Positionierung nach außen

--- D: FAZIT EUMAXL ---

  KI im Scripting-Bereich bleibt wertvoll.
  KI als Kernbestandteil R+MUNI: war nie richtig, wird korrigiert.
  Anthropic als Dienstleister: nicht vertrauenswürdig genug für
  langfristige Abhängigkeit ohne Kontrollmöglichkeit.
  Max Plan: technisch gut — aber kein Dauerzustand wenn Kosten
  nicht im Budget und Mehrwert nicht klar trennbar von Grundnutzen.
  Die Freude ist weg. Das ist der eigentliche Verlust.

Artefakte:    kein Artefakt — Analyse im Sprint dokumentiert
GOV-Konform:  JA


================================================================================
3. ENTSCHEIDUNGEN
================================================================================

Entscheidung: Kontrollierter Exit-Point KI — S1.5 bis 2.0
  Auslöser:    Beobachtungsphase S104/S105 abgeschlossen.
               Verrechnungsunberechenbarkeit, Intransparenz Anthropic,
               Überlagerung eigener Lösung durch KI.
  Ergebnis:    AIOF beendet. KI wird Addon wie Atlassian.
               R+MUNI nach außen ohne KI bedienbar.
               KI nur mehr DEV-intern.
  Begründung:  KI hat ab S8 die Rolle übernommen die R+MUNI haben wollte
               und hat die eigene Lösung in einem merklichen Prozentsatz
               vollständig überlagert. R+MUNI soll positioniert werden —
               nicht andere dabei enablen Claude einzusetzen.
               KI hat indirekt R+MUNI sabotiert.
  GOV-Bezug:   GOV 1.4 Explizitheit
  Auswirkung:  KI-Dokumentation wird ab S1.5 aktualisiert.
               Außenwirkung R+MUNI ohne KI ab S1.5.
               Variantentest ab 14.05.2026.
  Rückwirkung: NEIN

Entscheidung: Aktives Riskmanagement als Blueprint-Erweiterung
  Auslöser:    KI-Abhängigkeit und deren Auswirkung auf R+MUNI hat gezeigt
               dass externe Abhängigkeiten ohne Riskmanagement die
               Entwicklung strukturell gefährden können.
               Trigger: ab jedem Release wird Riskmanagement durchgeführt.
  Ergebnis:    Riskmanagement wird als Methodik in den Blueprint eingebaut.
               Auslöser ist explizit der Release-Zeitpunkt —
               kein laufendes Overhead-Riskmanagement.
  Vorteil:     Riskmanagement wird als Methodik den Blueprint erweitern
               und Entwicklungen der R+MUNI Umgebung aktiv absichern.
  Nachteil:    Scheiß Riskmanagement — wenn mir sowas gefallen würde
               würde ich Versicherungen verkaufen.
               Wird trotzdem gemacht. Notwendigkeit schlägt Präferenz.
  GOV-Bezug:   kein direkter Bezug — neues Thema für GOV-Erweiterung
  Auswirkung:  Eigener Sprint / Backlog für Riskmanagement-Methodik
               ab S1.5 anlegen.
  Rückwirkung: NEIN


  Auslöser:    AIOF-Entscheid gefallen, aber Werkzeugwahl für DEV noch offen
  Ergebnis:    KI wird als DEV-Mittel weiter eingesetzt.
               Welche KI konkret — noch nicht entschieden.
               Nach außen nur mehr untergeordnete Rolle.
               LL aus S8–S105 sauber aus dem Risiko minimiert.
  Begründung:  Pragmatisch — DEV ohne KI-Unterstützung aktuell nicht
               sinnvoll. Werkzeugwahl folgt nach Evaluation lokale Variante.
  GOV-Bezug:   GOV 1.4 Explizitheit
  Auswirkung:  Kein Toolwechsel erzwungen vor Evaluationsabschluss.
               Außenwirkung KI untergeordnet ab S1.5.
  Rückwirkung: NEIN
  Auslöser:    Risiko der KI-Abhängigkeit und Auswirkung auf R+MUNI
               und seine Entwicklung soll stabilisiert werden
  Ergebnis:    S1.5–2.0 werden bewusst wenig neue Features bringen —
               kontrollierter Exit-Point ist das Ziel, nicht Stagnation.
               R+MUNI soll auf eigenen Beinen stehen.
  Begründung:  KI-Abhängigkeit ist ein Risiko das R+MUNI strukturell
               schwächt. Unabhängigkeit ist wichtiger als Feature-Tempo.
               Entscheid fließt in Release-Dokument S1.5 ein.
  GOV-Bezug:   GOV 1.4 Explizitheit
  Auswirkung:  Release-Dokument S1.5 kommuniziert Entscheid und Begründung.
               S2.0 als erster Stage nach vollständigem Exit-Point.
  Rückwirkung: NEIN

Entscheidung: Lokales LLM Evaluation für R+MUNI
  Auslöser:    Ablöse Cloud-Abhängigkeit im DEV-Bereich
  Ergebnis:    Evaluation ob lokales LLM sinnvoll und möglich —
               mit Außenwirkung prüfen. Wenn nicht sinnvoll:
               KI vollständig aus Blueprint gestrichen.
  Begründung:  Keine Cloud-Abhängigkeit, keine externe Kostenstruktur,
               keine Intransparenz Anthropic
  GOV-Bezug:   kein direkter Bezug
  Auswirkung:  Evaluation parallel zu S1.5 Release
  Rückwirkung: NEIN

Entscheidung: KI-Dokumentation bleibt physisch bis S1.5
  Auslöser:    Learning aus Stage 1–1.04: keine physische Löschung
               während aktiver Runs
  Ergebnis:    KI_principles_Associate_S8, KI_How2_DEV_S8,
               DEV_Sprint_AIDRIVEN-VERHALTEN_S104 bleiben physisch vorhanden
               — Finalisierung und Deprecated-Setzung ab S1.5
  Begründung:  Schutz vor Verlust stimmiger Stände
  GOV-Bezug:   GOV 7.3 Strukturbereinigung
  Auswirkung:  Keine Ablage-Änderung vor S1.5
  Rückwirkung: NEIN


================================================================================
4. ABWEICHUNGEN UND AUSNAHMEN
================================================================================

Abweichung: Sprint dokumentiert stage-übergreifenden Zeitraum S103–S105
  GOV-Regel:   GOV 7.8 Dev-Doku während des Sprints
  Begründung:  AIOF ist ein stage-übergreifender Prozess — Zusammenfassung
               in einem Sprint-Dokument ist notwendig für Nachvollziehbarkeit.
               Quelldokumente der einzelnen Stages bleiben erhalten.
  Wirkung:     Auf diesen Sprint begrenzt — kein Präzedenzfall


================================================================================
5. VERHALTENSHINWEISE CLAUDE (AI Driven Kap. 13.1)
================================================================================

⚠ Verhaltenshinweis: Erste Zusammenfassung des AIOF-Entscheids enthielt
  Interpretation und Schönfärbung — auf Rückmeldung EUMAXL korrigiert.
  Neuformulierung ohne Interpretation aus Quellen.

⚠ Verhaltenshinweis: Erster Backlog-Entwurf hatte falsches Format und
  falschen Status — auf Rückmeldung EUMAXL auf Sprint-Format umgestellt.


================================================================================
6. OFFENE PUNKTE
================================================================================

| Punkt | GOV-Bezug | Status | Nächste Aktion |
|-------|-----------|--------|----------------|
| KI_principles_Associate auf Addon-Status | GOV 7.3 | offen | ab S1.5 |
| KI_How2_DEV auf Addon-Status / Deprecated | GOV 7.3 | offen | ab S1.5 |
| DEV_Sprint_AIDRIVEN-VERHALTEN_S104 abschließen | GOV 7.9 | offen | ab S1.5 |
| AI_DRIVEN_DEV_METHODE Reduktion | BACKLOG_GOV-AIDRIVEN | offen | ab S1.5 |
| Außenwirkung R+MUNI ohne KI finalisieren | GOV 1.4 | offen | ab S1.5 |
| Release-Dokument S1.5 mit KI-Entscheid und Begründung | GOV 1.4 | offen | S1.5 |
| Riskmanagement Sprint / Backlog anlegen | keiner | offen | ab S1.5 |
| KI als Addon in Blueprint aufnehmen | keiner | offen | S1.5 |
| Support-Ticket Anthropic | keiner | ERLEDIGT — Vorschlag angenommen | — |
| Feedback-Formular Anthropic | keiner | offen — keine Rückmeldung | EUMAXL |


================================================================================
7. STAGE-ABSCHLUSS UND DOKUMENTATIONSPFLICHT (GOV 7.9)
================================================================================

Vollständigkeit geprüft:          NEIN — Sprint AKTIV, kein Abschluss vor Zielerfüllung
GOV-Konformität hergestellt:      JA
Alle Entscheidungen dokumentiert: JA
Artefakte abgelegt:               NEIN — Ablage durch EUMAXL
GitHub-Sync:                      AUSSTEHEND
Atlassian-Sync:                   NICHT ERFORDERLICH


================================================================================
8. LESSONS LEARNED
================================================================================

Was gut funktioniert hat:
  - Mitschrift über gesamte Stage im AIOF Verhaltenschat —
    vollständige Nachvollziehbarkeit ohne Informationsverlust
  - Beobachtungsphase als formales Instrument hat strukturierten
    Entscheid ermöglicht statt reaktivem Abbruch

Was beim nächsten Mal anders gemacht werden sollte:
  - KI-Abhängigkeit früher als Positionierungsrisiko erkennen —
    nicht erst wenn Überlagerung der eigenen Lösung sichtbar ist
  - Anthropic-Verrechnungsmodell vor Jahresabo prüfen —
    Transparenz ist nicht gegeben, muss aktiv abgefragt werden

Erkenntnisse die Dokumente oder GOV verändern (AI Driven Kap. 13.3):
  - KI als Addon in Install.txt und Außenwirkung neu verankern →
    Sprint ab S1.5: JA
  - Verrechnungsverhalten als expliziter Risikofaktor in AI Driven →
    Sprint ab S1.5: JA
  - Beobachtungsphase als formales Instrument in GOV verankern →
    Sprint ab S1.5: JA

---

## Bezüge

[[Global_GOV_DEV_S102]]                    normative Grundlage
[[AI_DRIVEN_DEV_METHODE_DEV_S102]]         operative Arbeitsmethode
[[DEV_Sprint_AIDRIVEN-VERHALTEN_S104]]     Verhaltensauffälligkeiten Gesamtübersicht
[[DEV_Sprint_AIOF-ROLLENDEF_S104]]         AIOF-Rollendefinition S104
[[BACKLOG_AIOF_DEV_S103]]                  AIOF-Konzept und Kandidaten
[[FREEZE_1_04]]                            AIOF-Stand Ausgangslage
[[STAGE105_ZIELE_S105]]                    Z4 AIOF-Entscheid
[[KI_principles_Associate_S8]]             KI-Principles Stand S8
[[KI_How2_DEV_S8]]                         KI-How2 Stand S8

---

================================================================================
AIOF — OFFBOARDING CLAUDE / KI — SPRINT (DEV) | S105 | 2026-04-15 | AKTIV — läuft stage-übergreifend bis Zielerfüllung | R+MUNI Blueprint
================================================================================
