# Decisions Protocol

## Trigger-Bedingungen für Decision-Log
Eine Decision wird geloggt wenn:
- Architektur-/Tool-/Workflow-Wechsel
- Trade-off mit nicht-trivialen Folgen
- Tool-Wechsel-Impuls (auch bei Verwerfen → Cooldown-Doku)
- Strategische Richtungsänderung
- Hiring/People-Entscheidung

Nicht jede Kleinigkeit. Aber lieber loggen als nicht.

## Process
1. AI schlägt vor: "Das klingt nach Decision. Soll ich loggen?"
2. User bestätigt
3. AI nutzt `_templates/decision.md`
4. Filename: `07_decisions/YYYY-MM-DD-<slug>.md` (Slug kebab-case, max 5 Wörter)
5. Frontmatter Pflicht

## Tagging-Schema (Frontmatter `tags:`)
- `decision/architecture` — Repo-Struktur, Tech-Stack, Vault-Layout
- `decision/tool` — Tool-Choice (Software, Service, Subscription)
- `decision/strategy` — Geschäftsrichtung, Markt, Produkt
- `decision/people` — Hiring, Team-Setup, Co-Founder-Aufgabenverteilung
- `decision/workflow` — Routinen, Prozesse, Methodik

Mehrere Tags erlaubt.

## Superseding
Neue Decision die alte ablöst:
- Neue Frontmatter `supersedes: [[07_decisions/<alte-slug>]]`
- Alte Decision Frontmatter `status: superseded`

## Review-Trigger
Falls Decision `review-date:` im Frontmatter hat: AI erinnert nicht aktiv (kein Cron). User kann via Glob/Dataview ablaufende reviewen.
