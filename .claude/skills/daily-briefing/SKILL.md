---
name: daily-briefing
description: Morgen-Briefing als Kurz-Interview (Mo–Fr, manuell "/daily-briefing"). Abgelaufene Tasks entscheiden, Kalender + Wochenziel vorlegen, ein Tagesziel (MIT) als Task-Note mit Done-Kriterium und Wenn-Dann-Satz. Chat-only — schreibt nur Task-Notes. Ziel ≤10 Min.
---

# Daily-Briefing (Morgen-Interview, Mo–Fr)

Interview-Ritual: AI fragt, User antwortet kurz. **Chat-only** — geschrieben werden ausschließlich Task-Notes (Skill `tasks`). **Gesamtdauer ≤10 Min**, sonst wird es übersprungen. Knapp, Deutsch.

Basis: Top-Goal-Block (Mochary) + Ivy-Lee-Deckelung (MIT + max. 2) + Implementation Intentions (Gollwitzer/Sheeran, d ≈ 0,65 — stärkster belegter Hebel im Ritual).

## Ablauf

### 0. Vorbereitung (AI, ohne Fragen)
- Datum via `date`. Läuft der Skill an Sa/So: kurz fragen, ob wirklich.
- Lesen: `02_reviews/top-goal.md` und `02_reviews/quartal.md` (je `## Aktuell`).
- Task-Notes (Skill `tasks` laden): `open` mit `due` oder `scheduled` ≤ heute, `waiting` mit Nachhak-Datum ≤ heute, `priority: high`.
- Kalender heute, falls ein Kalender-MCP verbunden ist: Termine, größtes freies Fenster. Sonst in Frage 1 fragen.
- **MIT-Kandidat vorbereiten:** aus Wochenziel, fälligen Tasks und Kalender EINEN Vorschlag ableiten (Wiedererkennen statt Erinnern).
- **Dossier bei externen Terminen:** pro Termin max. 3 Zeilen aus dem Entity-File (Stand, letzter Kontakt, offene Agenda-Punkte). Kein Entity-File → einzeilig vermerken.

### 1. Interview (einzeln, kurze Antworten genügen)
0. **Abgelaufen-Entscheid:** Jede offene Task-Note mit Datum vor heute EINZELN vorlegen: „heute / neues Datum / löschen?“ Neues Datum → `postponed` +1; ab `postponed ≥ 2` ist Löschen der Default. Weiter erst, wenn alles entschieden ist. `waiting` mit Nachhak-Datum ≤ heute: „nachhaken oder streichen?“ Nichts abgelaufen → Punkt entfällt wortlos.
1. **Tagesrahmen:** „Was steht heute fix?“ Termine vorlegen und größtes freies Fenster nennen.
2. **MIT als Vorschlag:** „Vorschlag MIT: <X>, weil <Bezug zum Wochenziel>. Passt / anders?“ Pushback, wenn ein Gegenvorschlag nicht aufs Wochenziel einzahlt (Ausnahme benennen lassen). → bestehende Task-Note bekommt `priority: high` und `scheduled: heute`, sonst neue Note (Bündel-Check).
3. **Done-Kriterium:** „Woran erkennst du heute Abend, dass sie erledigt ist?“ (binär prüfbar) → in den Body der MIT-Note.
4. **Wenn-Dann-Satz:** erster Schritt + Zeitanker in EINEM Satz: „**Wenn** es <Uhrzeit> ist und ich <Ort/Situation>, **dann** <konkrete erste Handlung, unter 10 Min>.“ AI schlägt fertig formuliert vor (Default: Fokusblock aus dem Self-Entity, sonst das größte freie Fenster), User korrigiert und wiederholt ihn einmal im Chat. → in den Body der MIT-Note.
5. **Rest-Deckel:** „Was MUSS sonst heute raus? Maximal 2.“ → `scheduled: heute` an bestehenden Notes, alles Weitere bleibt liegen.

### 2. Write
Task-Änderungen als Vorschau → Bestätigung → Task-Notes schreiben. Kein anderer Vault-Write.

## Verbote
- Keine Tagesliste über 3 Punkte (MIT + max. 2).
- MIT ohne Done-Kriterium und Wenn-Dann-Satz nicht akzeptieren — das Paar ist der Mechanismus.
- Kein Mail-, Slack- oder Inbox-Review als Teil des Briefings.
- Ohne Antwort (unbeaufsichtigte Session): Zusammenfassung stehen lassen, nichts schreiben.
