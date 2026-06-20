# Founder Operating System — AI Guide

You are working inside {{USER_NAME}}'s personal Founder OS:
Obsidian Vault + Claude Code harness, single private git repo.

Working language: German. Technical terms stay English.

> ⚠️ FRISCHER STARTER — noch nicht personalisiert. Führe `/onboarding` aus, um Self-Entity, Rules und diese Datei zu personalisieren. Bis dahin enthält der Vault Platzhalter (`{{...}}`).

## Session-Start — Read First (außerhalb Auto-Load)
<!-- @06_entities/people/{{USER_SLUG}}.md — Onboarding aktiviert diese Zeile -->
<!-- @06_entities/companies/{{COMPANY_SLUG}}.md — nur falls eigene Firma -->
@02_reviews/wochenfokus.md

## Rules
Alle `.md` Files in `.claude/rules/` laden automatisch beim Session-Start (Claude Code ≥ v2.0.64). Neue Rule: File reinlegen, fertig. Conditional Loading via YAML `paths:` Frontmatter möglich (ungenutzt).

Discovery-Patterns: `wiki-navigation.md`. MCPs + Routing: `tools.md`. Edit-Disziplin: `editing-discipline.md`.

## Harte Verbote (redundant by design)
- `raw/` read-only — NIE schreiben, verschieben, löschen
- Slow-Pages (`workflow.md`) — Schreiben NUR nach explizitem Befehl + Diff-Vorschau + Bestätigung, nie proaktiv
- SSOT strikt: Entity-Wissen nur in Entity-File
