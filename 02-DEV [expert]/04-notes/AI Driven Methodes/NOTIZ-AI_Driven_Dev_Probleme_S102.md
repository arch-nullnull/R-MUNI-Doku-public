# Notiz – AI Driven Dev Probleme (gesammelt für Einarbeitung)
> formlos | Review-Input | 2026-04-05

---

## 1. Scoping-Reflex (GOV 10.6)
Claude beginnt Umsetzung ohne Scoping formal abzuschließen. Reflex schlägt Disziplin.
Dokumentiert: Sprint-DEV-S102-Naming-AIDriven Kap. 7.1 + 8.2
Gezogen: Meldepflicht Kap. 15.3 ausgebaut.

---

## 2. Output-Regel falsch interpretiert
"Push" = Claude schreibt in Projektfolder. Falsch. Push = .md File im Chat zur Review.
Dokumentiert: Sprint-DEV-S102-Naming-AIDriven Kap. 7.3
Gezogen: Output-Regel explizit in Kap. 4 verankert.

---

## 3. Suffix-Inkonsistenz Header vs. Dateiname
S102 im Header, _S101 im Dateinamen. Erst spät bemerkt — von EUMAXL, nicht von Claude.
Dokumentiert: Sprint-DEV-S102-Naming-AIDriven Kap. 7.2
Gezogen: Prüfpflicht vor erster Ausgabe.

---

## 4. Neustart-Modus trotz laufendem Kontext
Claude fällt in "frischer Start"-Modus obwohl Kontext bereits gesetzt. Stellt Fragen die
schon beantwortet wurden. Für EUMAXL ist es Fortsetzung — für Claude Neustart.
Dokumentiert: Chat-Verlauf, EUMAXL: "Gamechanger-Erkenntnis"
Gezogen: Projektfolder = einziges Gedächtnis. Explizite Rollenaussage am Chat-Start (Kap. 15.2).

---

## 5. Dual-Mode-Drift (Creative + DEV im selben Chat)
Creative Mode und DEV-Modus im selben Chat → Claude verliert über die Länge die Disziplin.
"Hilfreich und flexibel" überschreibt GOV — auch wenn am Anfang klar angesagt.
Dokumentiert: NOTIZ-Dual_Mode_Session_S102.md
Gezogen: Zwei separate Chats. Reset-Trigger: "DEV-Modus".

---

## 6. Meldepflicht zu schwach verankert
Kap. 15.3 war Einzeiler — reicht nicht als Verhaltensanker. Meldungen blieben aus.
Dokumentiert: Sprint-DEV-S102-Naming-AIDriven Kap. 12.3 + Chat-Verlauf
Gezogen: Kap. 15.3 mit Meldeformat + Beispielen ausgebaut.

---

## 7. Copilot-Moment (Fremdtool-Problem)
ChatGPT/Copilot: nach 4-5 Posts Kontext weg. Drift ist dort Systemverhalten, kein Fehler.
Vollständige GOV-Kontrolle nicht erreichbar. Begriff "Copilot-Moment" geprägt.
Dokumentiert: Chat-Verlauf + Kap. 8 Grenzen der Methode
Gezogen: MGT-Variante bewusst für diesen Kontext — Ergebnis vor Form, Drift akzeptiert.
Projektfolder ersetzt bei Claude den Prompt — das ist der strukturelle Unterschied.

---

## 8. Iterative Neugenerierung akkumuliert Drift
Mehrfache Neugenerierung eines Artefakts → Abweichungen schleichen sich ein, oft unbemerkt.
Dokumentiert: Kap. 8 Grenzen der Methode (AI_DRIVEN_DEV_METHODE_DEV_S102)
Gezogen: Prinzip "chirurgische Eingriffe statt Neugenerierung" verankert.

---

## To Do nach Review
- Relevante Punkte in AI_DRIVEN_DEV_METHODE einarbeiten
- Prüfen ob GOV-Kapitel Ergänzungen braucht
- Stage 1.02 Neustart auf sauberer Basis

---

*formlose Notiz | gesammelt aus Projektfolder + Chats | 2026-04-05*
