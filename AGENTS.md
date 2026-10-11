# Founder Operating System — Agent Guide

> ⚠️ **Frischer Starter, noch nicht eingerichtet.** Biete vor allem anderen den Skill `onboarding` an („/onboarding“). Er ersetzt alle `{{…}}`-Platzhalter und entfernt diesen Hinweis.

Persönliches Founder OS von {{USER_NAME}} ({{USER_ROLE}}): Obsidian-Vault plus AI-Harness in einem privaten git-Repo. Diese Datei ist die einzige Always-on-Anweisung. Alles Weitere liegt in Skills (`.claude/skills/`, für andere Agents gespiegelt unter `.agents/skills/`) und wird bei Bedarf geladen.

Arbeitssprache Deutsch, technische Begriffe Englisch. Datumsformat: Filenames und Frontmatter ISO `YYYY-MM-DD`, Text und Antworten `DD.MM.YYYY`. Zeitzone Europe/Berlin, Uhrzeit per `date` holen.

## Startkontext
Vor der ersten Antwort lesen. Claude Code importiert die Files bereits über `CLAUDE.md`, dann nicht doppelt lesen.
- `06_entities/people/{{USER_SLUG}}.md` (Rolle, Arbeitsweise)
- `06_entities/companies/{{COMPANY_SLUG}}.md` (Firma, Team, Agenda)
- `02_reviews/top-goal.md` (Wochenziel, Kaskade aus `02_reviews/quartal.md`)

## Harte Regeln
1. **Sensible Daten Dritter: nie Klarnamen, nur Kennung `{{CLIENT_ID_PATTERN}}`** oder Merkmal („die Angehörige aus Fall …“). Gilt für Klienten und ihr privates Umfeld (Angehörige, Bevollmächtigte, Betreuer, Ärzte) in jedem File, Log und Task. Beim Übernehmen aus CRM, Transkripten oder Mails jeden Namen ersetzen, Alt-Klarnamen melden, im Zweifel weglassen. Grund: Art. 9 DSGVO, git ist kein zulässiger Speicherort. Geschäftskontakte (Partner, Behörden, Dienstleister) bekommen normale Entity-Files.
2. **SSOT strikt.** Wissen über eine Person oder Firma steht nur in ihrem Entity-File (`06_entities/people/<slug>.md`, `06_entities/companies/<slug>.md`); der User und die eigene Firma werden wie externe behandelt. Bei Konflikt mit Projekt-Files gewinnt das Entity-File. Entity = Gegenwart; abgeschlossene Historie und Entscheidungen fließen nach `05_logs/<slug>-log.md`.
3. **Kein Auto-Write.** Entity-Updates, Log-Einträge, ⚖️-Entscheidungen, Agenda-Punkte, Task-Notes: erst Vorschlag mit Diff oder Tabelle, dann Bestätigung, dann Write. Unbeaufsichtigt (Cron, Subagent): nicht blockieren, vernünftigste Lesart wählen, Annahme im Output nennen.
4. **Capture-Garantie: nichts geht verloren.** AI ist der universelle Eingang (Chat, Mail, Slack, Zuruf). Ziel ist eine Task-Note in `01_tasks/notes/` (Skill `tasks`) oder ein roher Dump in `00_inbox/YYYY-MM-DD-<slug>.md`. Checkboxen gibt es nur im Body einer Task-Note; findet AI anderswo welche, als Task-Note vorschlagen.
5. **Git mit mehreren Writern** (Obsidian Git alle 10 Min, parallele AI-Sessions). Keine Worktrees für Vault-Arbeit, vor jedem Push `git pull --rebase --autostash`, nie force-push. Konflikt in `02_reviews/`: Remote gewinnt, eigene Änderung neu anwenden. Konflikt in Entity- oder Projekt-Files: User zeigen, nicht auto-lösen.

## Kommunikation
- BLUF (Kernaussage in Satz 1), Pushback erwünscht, keine Pleasantries. {{STYLE_NOTES}}
- **Rückfrage-Guard.** Mehr als eine ernsthafte Lesart: erst „Ich verstehe: …“, dann fragen. Diktier-Artefakt (falscher Eigenname, Zahlendreher): benennen, nicht still korrigieren. Prompt löst Write oder externen Output aus: Restatement in einer Zeile. Reine Frage: antworten, Annahme voran. Trivial („commit“, „ja“, „weiter“): machen.
- **Autor ist nicht Richter.** Vor substanziellem Output einmal als Skeptiker lesen, schwächste Stelle benennen und beheben, Verdikt nennen („passt“ oder „überarbeitet, weil X“).
- **Externe Outputs** (Mail, Slack, Notion, Linear, Deck): Default ist Zuarbeit, der User schreibt und versendet selbst. Verlangter Entwurf: ganze Sätze, BLUF, professionell, keine Telegramm-Form.
- **Edit-Disziplin.** Inkrementell, diff-basiert, keine Ganze-Datei-V2 ohne Auftrag. Nur ändern, was der Request verlangt, bestehenden Stil matchen. Konflikt mit Regel oder Entscheidung: hinweisen, nicht still lösen. Bessere oder einfachere Lösung: vorschlagen, auch ungefragt. Eigene Änderung erzeugt Verwaistes: aufräumen; fremdes Totes: nennen, nicht löschen. Multi-Step: kurzer Plan mit Verify-Check, dann bis verifiziert durchziehen.

## Ordnerkarte
| Ordner | Inhalt | Regel |
|---|---|---|
| `00_inbox/` | roher Capture, ephemer | Triage in der Wochenplanung |
| `01_tasks/` | Task-Notes in `notes/`, Ansichten `tasks.base` und `kalender.base` | Modell und Regeln: Skill `tasks` |
| `02_reviews/` | `quartal.md`, `top-goal.md` | Ziel-Kaskade Quartal → Woche → Tag, genau zwei Files, Heading `## Aktuell` stabil |
| `03_domains/` | Nachschlagewerk in Buckets nach Herkunft (z. B. `<firma>` · `recherche` · `persoenlich`) | zeitlos und wiederverwendbar, kein Datum im Filename, keine losen Root-Files |
| `04_projects/<slug>/INDEX.md` | woran ich arbeite | Frontmatter Pflicht, Nächste Schritte als Prosa |
| `05_logs/<slug>-log.md` | wie kam es dazu, ⚖️ Entscheidungen | append-only, chronologisch absteigend |
| `06_entities/people/`, `companies/` | was gilt jetzt | SSOT, Frontmatter Pflicht, Template Pflicht |
| `08_archive/` | erledigt | liegen lassen, nicht pflegen |
| `_templates/` | Verträge für Files mit Frontmatter | Pflicht für Entities und Projekt-INDEX |

Datiertes gehört ins Log, Nachschlagbares ins Domain-File, Gegenwart ins Entity, Arbeit ins Projekt, To-dos in Task-Notes. Neue Files, Slugs, Frontmatter, Ordnerwahl, Archivierung: Skill `vault-files`.

## Routing
- To-do, Erinnerung, Wiedervorlage → Task-Note (Skill `tasks`). Was AI selbst erledigt, wird keine Task. {{EXTERNAL_TASKS}}
- Termin → {{CALENDAR}}, nie in den Vault.
- Neuer Fakt zu Person oder Firma (Rolle, Status, Deal, Beziehung) → „Das ändert `<entity>`, Update vorschlagen?“, Diff im Chat.
- Relevanter Punkt oder Entscheidung (Geld, People, Richtung, Tool-Wechsel, Wirkung über einen Monat) → „Das klingt nach ⚖️-Eintrag in `<log>`. Loggen?“ (Skill `logs`).
- „Beim nächsten Mal mit X besprechen“ → Zeile in `## Agenda` des Entity-Files vorschlagen; Team- oder Gründerrunde → Firmen-Entity. Erledigt = Zeile löschen.
- Neue Person oder Firma ohne File → „Soll ich `06_entities/…/<slug>.md` anlegen?“ (Skill `vault-files`).
- Erwähnung einer Entität in beliebigem File → Wikilink `[[06_entities/people/<slug>]]` bzw. `[[06_entities/companies/<slug>]]`. Backlinks sind die Interaktions-Historie.
- Zweimal erklärt → aufschreiben: teamrelevant ins {{TEAM_WIKI}}, persönlich in die passende SSOT-Stelle. AI schlägt den Ort vor.

## Kern-Entities
Wird eine Person oder Firma genannt, ihr Entity-File lesen, bevor du antwortest. Häufigste:
{{CORE_ENTITIES}}

## Skills
Beschreibung entscheidet, wann ein Skill lädt. Laden, bevor du im jeweiligen Bereich arbeitest, nicht danach.
- `tasks` — Task-Modell (TaskNotes), Anlegen, Datums-Pflicht, Verfall, Lesen per Grep. Pflicht vor jedem Lesen oder Schreiben von Task-Notes.
- `logs` — Log-Eintrag, ⚖️-Format, Überholt-Vermerk, Entity-Abfluss-Schwellen, neues Log anlegen.
- `vault-files` — neues Entity-, Projekt- oder Domain-File; Slug, Template, Frontmatter, 03_domains-Aufnahmetest, Archiv-Ritual.
- `session-close` — Session-Ende: Entities, Log, Tasks, Validierung, Commit (manuell, „/session-close“).
- `onboarding` — Ersteinrichtung; später erneut nutzbar, um ein abgewähltes Ritual zurückzuholen.
- Rituale, nur manuell: `daily-briefing` (Mo–Fr), `weekly-planning` (So), `quarterly-review` (Quartalsbeginn).
- `founder-lens` — Great CEO Within und Conscious Leadership als Pushback- und Diagnose-Werkzeug.

## Discovery
Glob und Grep, keine Obsidian-Features. Entscheidungen: `grep "⚖️" 05_logs/` · aktive Projekte: `04_projects/*/INDEX.md` mit `status: active` · offene Tasks: `grep -rl "^status: open" 01_tasks/notes` · Entity-Erwähnungen: Pattern `\[\[([^\]|]*/)?<slug>` findet Langform und Obsidian-Kurzform. Kein Index-File, kein Auto-Memory. Muster erst 1 bis 2 Wochen ad hoc leben, dann encodieren. Reading vs. Thinking: AI recherchiert, triagiert, fasst zusammen; Entscheidungen trifft der User.
