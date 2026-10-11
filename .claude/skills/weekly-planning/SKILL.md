---
name: weekly-planning
description: Wochenplanung als Interview (So, manuell "/weekly-planning"). Rückblick-Zeile ins Top-Goal-Verlauf, neues Wochenziel aus den Quartalszielen, Kalender-Konflikte, Warten-Liste nachhaken, Lösch-Review der Task-Notes, Inbox-Triage. ~15 Min.
---

# Weekly-Planning (Sonntags-Interview)

Interview-Ritual, **~15 Min hart**. Kern: GTD „Get Current“ + Wochenscheibe aus dem 12 Week Year + Kopplung Quartal → Woche. Knapp, Deutsch.

## Ablauf

### 0. Vorbereitung (AI, ohne Fragen)
- `date` holen, KW bestimmen (alte + neue).
- Lesen: `02_reviews/top-goal.md`, `02_reviews/quartal.md`, `git log` seit Montag.
- Task-Notes (Skill `tasks` laden): seit Montag erledigt (`completedDate` in `01_tasks/notes/` und `08_archive/tasks/`), `open` mit Datum vor heute, `waiting`, `someday`, `postponed ≥ 2`, `open` ohne Datum.
- `00_inbox/`: Anzahl und Titel.
- Kalender nächste Woche, falls ein Kalender-MCP verbunden ist; sonst in Frage 5 fragen.

### 1. Interview (7 Fragen, einzeln)
1. **Execution-Check:** „Wochenziel KW <alt>: ✅/teilweise/❌ — der eine Satz warum?“ → 1 Zeile in `top-goal.md ## Verlauf`. Execution bewerten, nicht Selbstkritik.
2. **Energie:** „Größter Zeitfresser? Was hat Energie gegeben?“ (je 1 Stichwort) → Kurz-Suffix in dieselbe Verlaufszeile.
3. **Engpass:** Quartalsziele und Stand vorlegen: „Welches ist jetzt der Engpass?“ → Anker für Frage 4. Nie Wochenziel ohne Quartalsbezug.
4. **Wochenziel:** „Was ist Freitag 17:00 objektiv prüfbar fertig?“ Prüfbaren Zustand einfordern, keine Aktivität („an X arbeiten“ ablehnen). → `## Aktuell` überschreiben. Dazu höchstens 5 Wochenprio-Tasks: bestehende Task-Notes auf `priority: high` mit Datum in dieser Woche, fehlende anlegen (Bündel-Check).
5. **Kalender-Konflikte:** „Was kollidiert mit dem Ziel — was fliegt oder wird verschoben?“ → Absagen oder Verschiebungen als Liste, ggf. Task-Note.
6. **Fokuszeit:** „Wann liegen deine Blöcke für das Wochenziel?“ Stehen sie nicht im Kalender: Termin vorschlagen, anlegen nur nach Bestätigung und nur mit verbundenem Kalender-MCP; sonst trägt der User sie selbst ein.
7. **Aufräumen:** `waiting` vorlegen: „Wo hakst du nach?“ → Nachhak-Datum in `scheduled`; über 21 Tage ohne Reaktion → Default streichen. Dann Lösch-Review: `postponed ≥ 2`, `open` ohne Datum, `someday`, Überfälliges, jeweils mit Default „weg“. Behalten braucht einen Grund („Was passiert konkret, wenn das nie erledigt wird?“). Dann `00_inbox/`: je File „Task, Entity, Projekt, Domain oder weg?“. Abschließend Abfluss-Check (Skill `logs`), nur bei Treffer.

### 2. Write
Diff-Vorschau (`top-goal.md`) plus Task-Änderungen als Tabelle → Bestätigung → Write.

## Verbote
- Kein GTD-Vollprogramm (kein 2h-Review, kein Projekt-für-Projekt-Durchgang). Der 15-Min-Kern ist der überlebensfähige Teil.
- Wochenziel als Aktivität statt prüfbarem Zustand nicht akzeptieren.
- Keine separaten Weekly-Review-Files.
- Ohne Antwort (unbeaufsichtigte Session): Vorbereitung als Nachricht stehen lassen, nichts schreiben.
