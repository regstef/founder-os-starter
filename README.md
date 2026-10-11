# Founder OS — Starter

Leeres Grundgerüst für ein persönliches Founder Operating System: Obsidian-Vault plus AI (Claude Code) in einem privaten GitHub-Repo. Keine Inhalte, nur Struktur, Regeln und Rituale. Das Onboarding richtet es in rund 25 Minuten auf dich ein.

## Was drin ist
- **Wissen** in Markdown: Personen und Firmen (`06_entities`), Projekte (`04_projects`), Nachschlagewerk (`03_domains`), Verlauf und Entscheidungen (`05_logs`), Ziele vom Quartal bis zur Woche (`02_reviews`).
- **Tasks** mit dem Plugin TaskNotes: eine Note je Vorhaben, Ansichten „Jetzt“, „Board“, „Warten“, „Someday“ und Kalender (`01_tasks`).
- **AI-Regeln** in `AGENTS.md` plus Skills in `.claude/skills/`, die bei Bedarf laden. Rituale (Tages-, Wochen- und Quartalsplanung, Founder-Lens) wählst du im Onboarding aus.
- **Git-Sync:** Obsidian committet und synchronisiert alle 10 Minuten mit GitHub und holt beim Start den neuesten Stand.

## Einrichten (≈ 20 Min, einmalig)
Voraussetzungen: Mac mit [Homebrew](https://brew.sh), [Obsidian](https://obsidian.md) ab Version 1.13, [Claude Code](https://claude.com/claude-code).

**1. GitHub-Zugang im Terminal**
```bash
brew install gh
```
```bash
gh auth login
```
Auswahl: GitHub.com → HTTPS → „Authenticate Git with your GitHub credentials?“ Yes → Login im Browser. Damit kann später auch Obsidian pushen.

**2. Eigenes privates Repo aus diesem Template**
Im Terminal in den Ordner wechseln, in dem der Vault liegen soll, nicht in iCloud Drive oder Dropbox (Cloud-Sync und Git vertragen sich nicht). Dann:
```bash
gh repo create mein-founder-os --private --template regstef/founder-os-starter --clone
```
Das legt das Repo in deinem GitHub-Account an und klont es. Den Namen kannst du frei wählen. Alternativ auf GitHub „Use this template“ → Private → danach klonen.

**3. Obsidian**
1. „Open folder as vault“ → den neuen Ordner wählen.
2. Einstellungen → Community-Plugins → Community-Plugins aktivieren.
3. „Durchsuchen“ → nacheinander installieren und aktivieren: **Obsidian Git**, **TaskNotes** und **Hidden Folders Access** (macht den Ordner `.claude/` mit den AI-Skills in Obsidian sichtbar). Die Einstellungen aller drei liegen schon im Repo.

**4. Sync testen**
`Cmd+P` → „Obsidian Git: Commit-and-sync“. Auf GitHub erscheint ein Commit „vault sync: …“. Ab jetzt läuft das automatisch.

**5. AI einrichten**
```bash
cd mein-founder-os && claude
```
Dann `/onboarding` eingeben. Das Interview fragt nach Rolle, Firma, Umgang mit sensiblen Daten, deinen Tools, den gewünschten Ritualen und deinen Zielen. Es schreibt alles erst nach deiner Bestätigung und zeigt dir dann den Alltag an echten Beispielen.

## Im Alltag
| Du willst | Du sagst zu Claude |
|---|---|
| Aufgabe festhalten | „Task: Angebot an X bis Freitag“ |
| Gespräch festhalten | „Notiz zum Call mit Y: …“ |
| Neues Vorhaben | „Neues Projekt: …“ |
| Gedanken parken | einfach reinschreiben, landet in `00_inbox/` |
| Session abschließen | „/session-close“ |

In Obsidian ist `01_tasks/tasks.base` das Task-Cockpit und `02_reviews/top-goal.md` das Wochenziel.

## Ordner
| Ordner | Wofür | Beispiel |
|---|---|---|
| `00_inbox/` | Rohes, das noch keinen Platz hat. Wird in der Wochenplanung sortiert. | Gedanke von unterwegs |
| `01_tasks/` | Deine Aufgaben, eine Note je Vorhaben. `tasks.base` ist das Cockpit, `kalender.base` die Wochenansicht. | „Angebot an X schicken“ |
| `02_reviews/` | Deine Ziele: `quartal.md` für das Quartal, `top-goal.md` für die Woche. | „Q4: 3 neue Kunden“ |
| `03_domains/` | Nachschlagewerk, das seinen Anlass überlebt, mit Unterordnern nach Herkunft (Firma, Recherche, Persönliches). | Preismodell, Marktrecherche |
| `04_projects/` | Woran du gerade arbeitest, ein Ordner je Projekt mit `INDEX.md`. | Website-Relaunch |
| `05_logs/` | Wie es dazu kam: Verlauf und Entscheidungen (⚖️), neueste oben, wird nie umgeschrieben. | Warum ihr Tool X gekündigt habt |
| `06_entities/` | Was jetzt über eine Person (`people/`) oder Firma (`companies/`) gilt, ein File je Person oder Firma. | Rolle, Stand, offene Gesprächspunkte |
| `08_archive/` | Erledigtes, nur noch zum Nachschlagen. | abgeschlossenes Projekt |
| `_templates/` | Vorlagen für Personen, Firmen und Projekte. | |
| `.claude/` | Skills der AI. In Obsidian sichtbar dank Hidden Folders Access. | `skills/weekly-planning/` |

Die Grundregeln der AI stehen in `AGENTS.md` im Hauptordner. Faustregel: Datiertes ins Log, Nachschlagbares nach `03_domains`, Gegenwart ins Entity, Arbeit ins Projekt, To-dos in Tasks. Du musst das nicht selbst sortieren, die AI schlägt den Ort vor.

## Gut zu wissen
- **Nur am Desktop getestet.** Obsidian Git läuft mobil nur eingeschränkt.
- **Codex statt Claude?** `AGENTS.md` und `.agents/skills/` liest Codex genauso.
- **Ritual später dazunehmen:** `/onboarding` erneut aufrufen.
- **Konflikte:** Schreiben Obsidian und AI gleichzeitig, kann Git einen Konflikt melden. Bei Entity- oder Projekt-Files zeigt die AI ihn dir, statt selbst zu entscheiden.
