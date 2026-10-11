---
name: session-close
description: Session sauber abschließen (manuell "/session-close" oder „Session abschließen“). Prüft, ob alles aus der Session im Vault gelandet ist — Entities, veraltete Aussagen in Domain- und Projekt-Files, Log und ⚖️, offene Zusagen als Task-Notes, externe Aktionen, Klarnamen, Abfluss-Schwellen. Ein Diff-Vorschlag, nach „go“ schreiben, committen, pushen. ~5 Min.
---

# Session-Close

Bündelt Prüfungen, die schon in `AGENTS.md` und den Skills `logs`, `tasks`, `vault-files` stehen. Keine neuen Regeln. Ziel: Der User sagt ein Wort, AI findet alles, was die Session verändert hat, und legt es als eine Liste vor.

## Ablauf

### 0. Sammeln (AI, ohne Fragen)
- `date` holen, `git pull --rebase --autostash`, `git status` und `git log --since=<Session-Start>` für bereits geschriebene Files.
- Session-Verlauf durchgehen und festhalten: genannte Personen und Firmen, neue Fakten (Rolle, Status, Deal, Kontakt, Zahl), Zusagen mit Datum, Entscheidungen, externe Aktionen (Mail, Slack, Termin), neu entstandene Files.

### 1. Validieren
Jede externe Aktion der Session einmal per Tool gegenprüfen, nicht aus dem Gedächtnis bestätigen: Mail im Gesendet-Ordner, Termin im Kalender, Slack-Post per Permalink, Commit per `git log`, Task-Note per `ls`. Fehlt etwas: benennen, nicht still nachholen.

### 2. SSOT prüfen
- **Entities:** Für jede genannte Person oder Firma das Entity-File lesen und mit dem Session-Stand vergleichen. Abweichung → Diff. Ohne File → „Soll ich anlegen?“ (Skill `vault-files`). Kontakte bei Behörden oder Dienstleistern mit nur einer Kontaktzeile bekommen kein File, die Zeile gehört ins passende Domain-File.
- **Veraltete Aussagen:** Mit Grep nach den Stichworten der Session suchen (Name, Datum, Frist, Betrag, Ansprechpartner) in `03_domains/`, `04_projects/`, `06_entities/`, `02_reviews/`. Jede Aussage, die die Session überholt hat, als Diff vorschlagen. Entity-Erwähnungen: Pattern `\[\[([^\]|]*/)?<slug>`.
- **Agenda:** Erledigte Punkte in `## Agenda` der betroffenen Entities → Zeile löschen vorschlagen; neue „mit X besprechen“ → Zeile vorschlagen.

### 3. Log prüfen (Skill `logs` laden)
- Relevanz-Test je Punkt: „Will ich das in 3 Monaten nachlesen können?“ Ja → Eintrag im Log des Subjekts, 1 bis 5 Zeilen.
- Geld, People, Richtung, Tool-Wechsel, Wirkung über einen Monat → ⚖️-Kandidat, als Frage vorlegen. Überholt eine frühere Entscheidung → Überholt-Vermerk mit vorschlagen.

### 4. Nichts verloren (Skill `tasks` laden)
- Offene Zusagen und nächste Schritte gegen `01_tasks/notes/` abgleichen (Grep nach Stichwort und Entity, Bündel-Check). Fehlt eine Task-Note → vorschlagen; was AI selbst erledigt, wird keine Task. Tasks, die laut Routing in `AGENTS.md` in ein anderes Tool gehören, als Hinweis an den User.
- Checkboxen außerhalb von Task-Notes, die in der Session entstanden sind → als Task-Note vorschlagen und aus dem File entfernen.
- Rohes, das nirgends hinpasst → `00_inbox/YYYY-MM-DD-<slug>.md`.

### 5. Hygiene
- **Klarnamen:** geschriebene oder geänderte Files auf Namen von Klienten und ihrem Umfeld prüfen (Regel 1 in `AGENTS.md`). Treffer melden.
- **Abfluss-Schwellen** der berührten Entities (Section > 20 Zeilen, Person > 60 Zeilen / 5 KB, Company > 100 Zeilen / 8 KB) → nur bei Treffer vorschlagen.
- Wikilinks für neu erwähnte Entities, Frontmatter bei neuen Files.

## Ausgabe
1. Eine Zeile Validierung („Mail 14.09. 15:49 versendet, 3 Task-Notes da“).
2. Diffs je File, gruppiert: Entities → Domain/Projekt → Log → Task-Notes. Leere Gruppen als eine Zeile („0 Entity-Änderungen, weil …“).
3. Offene Fragen (⚖️, neues File) höchstens 3, als Ja/Nein.
4. Schlusszeile: „go?“

Nach „go“: schreiben, `git pull --rebase --autostash`, commit mit Klartext-Message, push, Commit-Hash nennen. Danach höchstens drei Zeilen: was noch offen ist, mit Datum.

## Verbote
- Kein Write vor „go“ (Regel „Kein Auto-Write“). Kein Session-Recap als Prosa.
- Nicht aus dem Gedächtnis validieren, immer per Tool.
- Konflikt beim Pull in Entity- oder Projekt-Files: zeigen, nicht auto-lösen.
- Nichts erfinden, um Lücken zu füllen: unklarer Fakt → als Frage.
