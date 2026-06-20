# Wiki Navigation

Statische Strukturkarte. Keine Auto-Updates. Discovery via Tools.

## Ordnerstruktur

```
founder-operating-system/
├── CLAUDE.md                # AI Master-Guide
├── README.md                # Menschen
├── docs/                    # Repo-Meta-Doku (Specs, Plans) — außerhalb Vault
├── 00_inbox/                # Capture roh, ephemeral, fließt durch (AI read+write)
├── 01_daily/                # Daily Cockpit Notes
├── 02_reviews/
│   └── weekly/              # Friday-Reviews (Slow-Page, AI read-only)
├── 03_domains/              # Sales, People-Mgmt, Strategie, Health, Privat
├── 04_projects/<slug>/      # Projekte, INDEX.md mit Frontmatter
├── 05_resources/            # Wissen, Recherche
├── 06_entities/
│   ├── people/              # Personen-Entities, SSOT
│   └── companies/           # Firmen-Entities, SSOT
├── 07_decisions/            # ADRs, Decision-Log
├── 08_archive/              # Erledigt, abgelegt
├── 09_views/                # Tasks-Plugin-Views (Wochenansicht, Inbox-Triage, By-Source, Someday), AI read-only
├── raw/                     # READ-ONLY für AI. Source-Dumps (Transkripte, PDFs), immutable
└── _templates/              # Verbindliche Verträge
```

## AI Discovery
- File-Suche: `Glob` mit Pattern
- Content-Suche: `Grep` mit Regex
- Active Decisions: `Glob 07_decisions/*.md` + Frontmatter-Filter `status: active`
- Active Entities: `Glob 06_entities/**/*.md` + `relation:`-Filter
- Active Projects: `Glob 04_projects/*/INDEX.md` + `status: active`
- Neueste Friday-Reviews: `Glob 02_reviews/weekly/*.md`, sortiert desc

## raw/ Verbot
AI darf NIE Files in `raw/` überschreiben, verschieben oder löschen. Nur lesen.

## Obsidian-Navigation (User)
User nutzt Obsidian-File-Explorer, Graph-View, Dataview-Queries. AI nutzt Glob/Grep/LS — NICHT Obsidian-spezifische Features.

## Backlinks
Backlinks = primärer Discovery-Mechanismus für Entity-Historie. AI rendert keine Backlinks selbst — Obsidian erledigt das.

Erwähnungen finden: Es existieren zwei Link-Formen — Langform `[[06_entities/people/<slug>]]` (AI-Schreibstandard) und Kurzform `[[<slug>]]` (entsteht durch Obsidian-Autocomplete beim User). Beide sind gültig. AI sucht deshalb mit Grep-Pattern `\[\[([^\]|]*/)?<slug>` — findet beide Formen.
