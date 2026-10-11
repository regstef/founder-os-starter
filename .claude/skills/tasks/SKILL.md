---
name: tasks
description: Task-Modell mit TaskNotes (eine Note je Vorhaben in 01_tasks/notes/) — Felder, Status, Bündelung, Datums-Pflicht, Löschen als Ausgang, Anlegen, Erledigen, Verschieben, Lesen per Grep, Ansichten. Pflicht, bevor Tasks gelesen, angelegt, verschoben, erledigt oder ausgewertet werden.
---

# Tasks (TaskNotes)

Task-SSOT ist `01_tasks/notes/`. Harte Regeln (Capture-Garantie, kein Auto-Write) und welche Tasks woanders leben (Routing) stehen in `AGENTS.md`.

## Modell
- Ein Task = eine Note in `01_tasks/notes/` (flach, keine Projektordner), Filename = Titel, Tag `task` im Frontmatter.
- Status `open` | `waiting` | `someday` | `done`. Nur `done` zählt als erledigt. Erledigte schiebt das Plugin nach einem Tag nach `08_archive/tasks/`; Zählungen lesen beide Orte.
- Felder: `due` (Deadline) · `scheduled` (geplanter Arbeitstag bzw. Nachhak-Datum) · `dateCreated` · `completedDate` · `priority` (`normal` als Default, `high` für Tagesziel und Wochenprio) · `projects` (Liste, quoted Wikilink auf den Projekt-INDEX, Pflicht bei Projektbezug) · `postponed` (Zähler, pflegt nur AI). Kein Startdatum: „frühestens X“ → `scheduled`.
- Ansichten: `01_tasks/tasks.base` (🔥 Jetzt · 🗂 Board · ⏳ Warten · 💤 Someday) und `01_tasks/kalender.base` (📆 Woche · 📋 Agenda). Projekt-Sicht = Backlinks des INDEX.

## Format einer neuen Task-Note
Pfad `01_tasks/notes/<Titel als kurzer Satz>.md`, ohne `/ : * ? " < > |` im Titel.

```markdown
---
status: open
priority: normal
scheduled: 2026-10-12
dateCreated: 2026-10-11
projects:
  - "[[04_projects/<slug>/INDEX]]"
tags:
  - task
---
Kontext in 1–3 Zeilen, Entities als Wikilink.

- [ ] Schritt 1
- [ ] Schritt 2
```

## Bündelung (härteste Regel)
So wenige Notes wie möglich: eine pro Vorhaben oder pro Person, nicht pro Schritt. Schritte und Teilfristen als Checkliste im Body (zählen nicht als Task), `due` rollt auf den nächsten Schritt. AI zerlegt nie in Vorbereitungs-, Teil- oder Folge-Notes; was AI selbst erledigt, wird kein Task. Zu grob gibt es auch: Ein Container ohne eigenen Fertig-Zustand ist keine Task-Note, sondern ein Projekt.

## Datums-Pflicht
- Jede neue Note trägt `scheduled` (geplanter Arbeitstag, ohne Angabe heute, wie beim Anlegen im Plugin), `due` nur bei echter Deadline. Sonst taucht sie in 🔥 Jetzt nicht auf.
- `open` trägt `due` oder `scheduled`, sonst `someday` oder löschen. Erfahrungswert: mit Datum 9 von 9 erledigt, ohne Datum 7 von 8 versandet.
- `waiting`: Entity-Wikilink im Body (auf wen), `dateCreated` = seit wann, `scheduled` = Nachhak-Datum.
- Datum aus dem Kontext codieren; unklar, ob `due` oder `scheduled` → fragen.

## Löschen ist ein Ausgang
Streichen ist gleichwertig zu Erledigen.
- **Verfall:** `due` oder `scheduled` nach hinten gesetzt → `postponed` +1. Ab 2 ist Löschen der Default, Behalten braucht einen Grund.
- `waiting` über 21 Tage ohne Reaktion → löschen oder einmal nachhaken.
- De facto erledigt → sofort `done` oder löschen vorschlagen. Leitfrage: „Was passiert konkret, wenn das nie erledigt wird?“
- Löschen = File löschen; git behält die Historie.

## AI-Rezepte
- **Anlegen:** erst per Grep nach Stichwort und Entity in `01_tasks/notes/` prüfen, ob eine bestehende Note die Sache aufnimmt. Dann Vorschlag (Titel, Status, Datum, Projekt) → Bestätigung → File schreiben.
- **Erledigen:** `status: done` und `completedDate: <heute>`, sonst nichts ändern.
- **Verschieben:** neues Datum setzen, `postponed` +1.
- **Lesen:** Frontmatter per Grep, kein Plugin nötig. Offen: `grep -rl "^status: open" 01_tasks/notes`. Warten: `grep -rl "^status: waiting" 01_tasks/notes`. Abgelaufen: offene Notes mit `due` oder `scheduled` vor heute (Datum per `date`, ISO-Strings vergleichen).
- **Capture in Obsidian:** `Cmd+P` → „TaskNotes“ tippen → Befehl zum Anlegen einer Aufgabe. Deutsche Eingabe wie „Angebot an X morgen“ wird erkannt, neue Notes bekommen automatisch `scheduled: heute`.
