# Notiz: AI Driven Blog — Memory & Chat-Archiv
**Session:** April 2026
**Ziel:** Einbauen in Blog-Serie "AI Driven" / Grundlage für Version 1.03

---

## Thema 1: Chat-Archiv-Hygiene (3-Stage-Modell)

**Beobachtung:**
- Archivierte Chats sind NICHT aus Memory/RAG ausgeschlossen — nur aus der Sidebar
- Claude.ai durchsucht archivierte Chats genauso wie aktive
- Viele ungefilterte Quick-Chats = hoher Background-Aufwand für Memory-Synthese (24h-Zyklus)

**3-Stage-Verhalten (Test):**
- Stage 1: aktiv (Sidebar sichtbar)
- Stage 2: archiviert (ausgeblendet, aber noch durchsuchbar)
- Stage 3: löschen vor nächster Session

**Ziel:**
Memory/RAG-Kosten reduzieren + testen wie gut Skills und Dokumentation
ohne ~400h angesammelten Chat-Kontext tragen.

---

## Thema 2: Incognito-Chat als Stresstest-Methode

**Idee:**
Vor dem echten History-Reset einen frischen Claude im Incognito-Chat
nur mit den vorhandenen Skills testen — kein Memory, kein Chat-Verlauf.

**Logik:**
- Funktioniert er → Skills/Doku tragen alleine → bereit für den Schnitt
- Strauchelt er → Doku-Lücken identifiziert → nachschärfen vor Reset

**Vorteil:** Kostet null History, ist jederzeit wiederholbar.

**Eventuelles Ziel:** Blog-Version 1.03

---

## Randnotiz: Claude-Verhalten dokumentiert

Claude schreibt Notizen standardmäßig in seine eigenen Erinnerungen (Memory),
nicht für den User. Verhalten bewusst beobachten und im Blog thematisieren:
*Wer profitiert eigentlich von "Notizen" — der User oder das Modell?*
