# Founder OS — Starter

Wiederverwendbares Grundgerüst für einen persönlichen **Founder Operating System**-Vault: Obsidian-Vault + Claude-Code-Harness in einem privaten Git-Repo. Generisch, ohne Personen- oder Firmendaten. Personalisierung läuft über einen geführten Onboarding-Skill.

## Was drin ist
- **Ordnerstruktur** (`00_inbox` … `09_views`, `_templates`, `raw`) — leer, mit `.gitkeep`.
- **`_templates/`** — Daily, Weekly-Review, Decision, Entity (Person/Company), Project-Index.
- **`.claude/rules/`** — Arbeitsregeln (Kommunikation, Tasks-Syntax, Entity-Handling, Operating-Model, Tools-Routing, Workflow, …). Auto-Load beim Session-Start.
- **`.claude/skills/onboarding/`** — geführte Erst-Einrichtung.
- **`09_views/`** — Obsidian-Tasks-Views (Wochenansicht, Inbox-Triage, Waiting-For, Someday, By-Source).
- **`.obsidian/`** — Plugin-/App-Config (Tasks, Templater, Dataview), damit Views + Templates direkt funktionieren.

Platzhalter `{{...}}` markieren alles, was beim Onboarding personalisiert wird.

## Einrichten (3 Schritte)
1. **Repo holen:** „Use this template" (GitHub) oder `git clone … <dein-vault>`. Eigenen Remote setzen, alten entfernen.
2. **Obsidian:** Ordner als Vault öffnen. Plugins (Tasks/Templater/Dataview) sind vorkonfiguriert — ggf. bestätigen/aktivieren.
3. **Claude Code im Vault starten → `/onboarding`.** Der Skill interviewt dich (Name, E-Mail, Tools, Initiativen) und ersetzt alle Platzhalter, legt dein Self-Entity an und aktiviert die Session-Imports.

Danach: normaler Betrieb. `CLAUDE.md` ist der AI-Master-Guide, die Regeln in `.claude/rules/` laden automatisch.

## Secrets
`.env` ist gitignored — nie committen. `.env.example` zeigt das Schema; nur eintragen, was du nutzt.
