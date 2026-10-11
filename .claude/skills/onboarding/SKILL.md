---
name: onboarding
description: Ersteinrichtung des Founder-OS-Starters als geführtes Interview (manuell "/onboarding", „Vault einrichten“, „Onboarding“). Prüft das Setup (Git-Sync, Plugins), fragt Person, Firma, sensible Daten, Tools, Rituale und Ziele ab, ersetzt alle Platzhalter, legt Self- und Firmen-Entity an, entfernt abgewählte Rituale und zeigt den Alltag an echten Beispielen. Später erneut nutzbar, um ein abgewähltes Ritual zurückzuholen. ~25 Min.
---

# Onboarding

Ziel: Nach ~25 Minuten ist der Vault personalisiert und synchronisiert, und der User hat jede Grundbewegung einmal selbst gemacht. Ton: knapp, Deutsch, eine Frage-Gruppe pro Nachricht. **Jeder Write erst als Vorschau, dann Bestätigung** (Regel „Kein Auto-Write“ in `AGENTS.md`).

## 0. Setup-Check (AI, ohne Fragen)
Ausführen und in höchstens 4 Zeilen melden, was fehlt. Abhilfe steht in `README.md`, Schritte 1–4. Nichts davon blockiert das Interview; Schritt 3 prüft erneut.
- `git remote -v` → zeigt auf das eigene GitHub-Repo. Zeigt es auf `founder-os-starter`, wurde das Template geklont statt daraus ein Repo erzeugt; fehlt es ganz, gibt es noch kein GitHub-Repo. Beides: README Schritt 2, bis dahin nur lokal committen.
- `git log --oneline -5` → ein Commit „vault sync: …“ oder „vault backup: …“ zeigt, dass Obsidian Git läuft. Fehlt er → README Schritt 4.
- `find .obsidian/plugins -name main.js` → Obsidian Git, TaskNotes und Hidden Folders Access installiert? Fehlt eines → README Schritt 3.
- `grep -nE "\{\{[A-Z_]+\}\}" AGENTS.md CLAUDE.md` → offene Platzhalter. Keine mehr → Vault ist schon eingerichtet: nur Abschnitt „Ritual nachrüsten“ anbieten.

## 1. Interview (einzeln, kurze Antworten genügen)
1. **Person:** voller Name, Rolle in 1–2 Sätzen, E-Mail. Slug ableiten (`vorname-nachname`, lowercase, ASCII, ä→ae, ö→oe, ü→ue, ß→ss) und bestätigen lassen. Dazu: „Wie soll ich mit dir arbeiten: knapp oder ausführlich, und was nervt dich an AI-Antworten?“
2. **Firma:** Name, was sie tut (2 Sätze), Stadt. Slug ohne Rechtsform ableiten (`beispiel` statt `beispiel-gmbh`) und bestätigen lassen. Engstes Team, höchstens 5: Name, Rolle, Beziehung (Mitgründer, angestellt, extern) → Kern-Entities. Keine eigene Firma → Firmen-Teile entfallen (siehe Tabelle).
3. **Sensible Daten:** „Arbeitest du mit Gesundheits- oder Sozialdaten Dritter, etwa Klienten oder Patienten? Welche Kennung nutzt ihr statt Namen (z. B. Fallnummer `F-XXX-XXXX`)?“
4. **Tools:** „Wo leben Termine, Team-Wissen und Tasks außerhalb des Vaults?“ (z. B. Google Calendar, Notion-Wiki, Linear für Tickets, CRM für Fallarbeit). Selbst prüfen, welche davon in dieser Session als MCP-Tools verfügbar sind, und in einer Zeile nennen (nur zur Info, wird nicht gespeichert).
5. **Tasks:** das Modell in 3 Sätzen erklären (eine Note je Vorhaben, Pflicht-Datum, Löschen ist ein erlaubter Ausgang; Cockpit `01_tasks/tasks.base`) und festhalten: Was laut Frage 4 in einem anderen Tool lebt, wird nie zusätzlich Task-Note. Will der User Tasks lieber ganz extern führen: nicht im Onboarding umbauen, sondern als Task-Note „Tasks extern führen: Umbau planen“ festhalten (betrifft die Skills `tasks`, `session-close` und die Rituale), TaskNotes vorerst lassen.
6. **Rituale und Founder-Lens:** je eine Zeile vorstellen, Mehrfachauswahl, „keins“ ist erlaubt:
   - `weekly-planning`: sonntags 15 Min, Rückblick, Wochenziel aus dem Quartalsziel, Warten-Liste, Lösch-Review.
   - `quarterly-review`: zu Quartalsbeginn 30–45 Min, alte Ziele bewerten, 1–2 neue mit Messlatte.
   - `daily-briefing`: werktags 10 Min, Abgelaufenes entscheiden, ein Tagesziel mit Done-Kriterium. Bei Wahl: „Wann ist dein bester Fokusblock?“
   - `founder-lens`: Great CEO Within und Conscious Leadership als Pushback-Linse, wenn es hakt.
7. **Ziele:** „Was soll dieses Quartal wahr werden? 1–2 Ziele, je mit Messlatte (Zahl oder Ereignis) und einer Wochen-Dosis, die du selbst steuerst.“ und „Was ist am kommenden Freitag objektiv fertig?“ (am Wochenende gilt die kommende Woche). Keine Antwort → leer lassen; später füllen `/quarterly-review` bzw. `/weekly-planning`, falls gewählt.

## 2. Schreiben (eine Vorschau für alles, dann „go“)
**Platzhalter** (in `AGENTS.md`, `{{SESSION_IMPORTS}}` in `CLAUDE.md`):

| Platzhalter | Quelle | Ohne Antwort |
|---|---|---|
| `{{USER_NAME}}`, `{{USER_SLUG}}` | Frage 1 | Pflicht |
| `{{USER_ROLE}}` | Frage 1–2, Kurzform „<Rolle> <Firma>, <Stadt>“, z. B. „Co-Founder und GF Beispiel GmbH, Berlin“ | ohne Firma: „<Rolle>, <Stadt>“ |
| `{{COMPANY_SLUG}}` | Frage 2 | ohne Firma: Zeile im Startkontext löschen |
| `{{CORE_ENTITIES}}` | Frage 2, je Zeile `` - <Name>: `06_entities/people/<slug>.md` (<Rolle>) `` | „Noch keine.“ |
| `{{STYLE_NOTES}}` | Frage 1, ein bis zwei Sätze | „Knapp, Listen statt Textwand, höchstens 5 Punkte je Liste.“ |
| `{{CLIENT_ID_PATTERN}}` | Frage 3 | Regel 1 streichen, Regeln neu nummerieren, `grep -rn "Regel 1" AGENTS.md .claude/skills` und Treffer anpassen |
| `{{CALENDAR}}`, `{{TEAM_WIKI}}` | Frage 4 | „den Kalender“ bzw. „Team-Wiki“ |
| `{{EXTERNAL_TASKS}}` | Frage 4–5 als Satz, z. B. „Tickets → Linear, Fallarbeit → CRM, nie doppelt als Task-Note.“ | Platzhalter entfernen |
| `{{SESSION_IMPORTS}}` | zwei Zeilen `@06_entities/people/<slug>.md` und `@06_entities/companies/<firma>.md` | ohne Firma: nur die Personen-Zeile |

**Files** (Templates aus `_templates/`; `first-contact` nur, wenn bekannt, sonst leer):
1. Self-Entity `06_entities/people/<slug>.md`: `relation: self`, `company:` als quoted Wikilink; unter `## Rolle / Kontext` Rolle und E-Mail; unter `## Wichtig zu wissen` der Fokusblock (falls erfragt) und der Verweis „Arbeitsweise mit AI: `AGENTS.md`, Abschnitt Kommunikation“. Der Stilwunsch selbst steht nur in `AGENTS.md`.
2. Firmen-Entity `06_entities/companies/<firma>.md`: `relation: self`, `## Was sie tun`, Team als Wikilinks in `people:` und unter `## Kontakte`.
3. Je Kern-Person `06_entities/people/<slug>.md`: `relation` aus Frage 2, `company:` als quoted Wikilink, Rolle unter `## Rolle / Kontext`, sonst leer.
4. `AGENTS.md` und `CLAUDE.md`: Platzhalter laut Tabelle ersetzen, den ⚠️-Hinweis oben in `AGENTS.md` löschen.
5. Abgewählte Rituale: `git rm -r .claude/skills/<name>`, Zeile in `AGENTS.md` (Abschnitt Skills) anpassen. Weitere Verweise per `grep -rn "<name>" AGENTS.md .claude/skills` anpassen, außer im Skill `onboarding` (er nennt alle Rituale absichtlich).
6. Ziele in `## Aktuell`: `02_reviews/quartal.md` als `**Q<n> <Jahr>** — **Z1 <Ziel>:** Messlatte … · Wochen-Dosis …`, `02_reviews/top-goal.md` als `**KW <n> (<Mo>–<So>)** — <Ziel>. Done: <prüfbarer Zustand>`.
7. `05_logs/vault-log.md` mit Kopfzeile `System-Gedächtnis dieses Founder OS (Vault, Regeln, AI-Setup). Chronologisch absteigend, Entscheidungen mit ⚖️. Regeln: Skill \`logs\`.` und erstem Eintrag `- <Datum> ⚖️ **Founder OS eingerichtet.** Rituale: <Auswahl>. Sensible Daten: <Kennung oder keine>. Tasks außerhalb: <Tools>.`

## 3. Prüfen
- `grep -nE "\{\{[A-Z_]+\}\}" AGENTS.md CLAUDE.md` → 0 Treffer.
- Jeder `@`-Import in `CLAUDE.md` zeigt auf ein existierendes File. Jeder Skill in `AGENTS.md` hat einen Ordner in `.claude/skills/`, und umgekehrt.
- Setup-Check aus Schritt 0 wiederholen; Offenes als eine Zeile mit README-Schritt melden.

## 4. Tour am echten Beispiel (~5 Min)
Jede Bewegung in einem Satz erklären und den User sie sofort einmal echt machen lassen:
1. **Task:** „Task: <etwas, das diese Woche ansteht>“ → Vorschlag, nach OK anlegen; in Obsidian `01_tasks/tasks.base` öffnen, Ansicht 🔥 Jetzt (neue Notes tragen `scheduled: heute`, Skill `tasks`).
2. **Gespräch festhalten:** „Notiz zum Gespräch mit <Person>: …“ → Entity-Update und, falls relevant, Log-Eintrag als Vorschlag.
3. **Projekt:** „Neues Projekt: <Thema>“ → `04_projects/<slug>/INDEX.md` aus dem Template.
4. **Roher Gedanke:** alles ohne klares Ziel → `00_inbox/`, wird in der Wochenplanung sortiert.
5. **Session-Ende:** Im Alltag schließt „/session-close“ jede Session ab (prüft, committet, pusht). Jetzt einmal direkt: `git pull --rebase --autostash`, Commit „Onboarding: <Name>“ mit allem aus Schritt 2 und der Tour, nach Bestätigung pushen, dann `git log origin/main --oneline -1` → Commit ist auf GitHub. Ohne Remote: nur lokal committen und README Schritt 2 nennen.

Zum Schluss eine Zeile: das erste gewählte Ritual mit Wochentag, z. B. „Sonntag: /weekly-planning“.

## Ritual nachrüsten (Vault ist schon eingerichtet)
Abgewählte Rituale liegen in der Git-Historie: `git log --diff-filter=D --oneline -- .claude/skills/<name>` liefert den Lösch-Commit, `git checkout <hash>^ -- .claude/skills/<name>` holt den Ordner zurück. Zeile in `AGENTS.md` (Skills) ergänzen, Vorschau, Commit.

## Verbote
- Nichts erfinden und nichts aus anderen Quellen (CRM, Mail, fremde Vaults) übernehmen, nur was der User im Interview sagt. Unklares, etwa die Beziehung einer Person, erfragen.
- Kein Write vor „go“. Files löschen nur bei abgewählten Ritualen.
- Keine Klarnamen von Klienten, auch nicht als Beispiel.
