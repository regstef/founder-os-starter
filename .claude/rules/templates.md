# Templates

Alle Files mit Frontmatter MÜSSEN ein Template aus `_templates/` nutzen.

## Mapping Filename → Template
| Filename-Pattern | Template |
|---|---|
| `01_daily/YYYY-MM-DD.md` | `_templates/daily.md` |
| `02_reviews/weekly/YYYY-WW.md` | `_templates/weekly-review.md` |
| `07_decisions/YYYY-MM-DD-<slug>.md` | `_templates/decision.md` |
| `06_entities/people/<slug>.md` | `_templates/entity-person.md` |
| `06_entities/companies/<slug>.md` | `_templates/entity-company.md` |
| `04_projects/<slug>/INDEX.md` | `_templates/project-index.md` |

## Templater-Variablen
- `<% tp.date.now("YYYY-MM-DD") %>` → ISO-Datum (für Frontmatter, Filenames)
- `<% tp.date.now("DD.MM.YYYY") %>` → Display-Datum (für File-Content-Header)
- `<% tp.date.weekNumber() %>` → KW

User nutzt Obsidian-Templater-Plugin. AI nutzt Template als Vorlage und ersetzt Variablen direkt (also AI schreibt bereits `2026-06-07` statt `<% tp.date.now("YYYY-MM-DD") %>`).

## Kein Free-Form
Files ohne Frontmatter sind NICHT erlaubt für:
- `01_daily/`
- `02_reviews/weekly/` (eigene Frontmatter mit `ai-write: false`)
- `04_projects/<slug>/INDEX.md`
- `06_entities/`
- `07_decisions/`

Optional Frontmatter erlaubt für:
- `00_inbox/` (Capture-Speed > Schema)
- `05_resources/` (Wissens-Snippets, oft externe Quellen)
- `03_domains/` (Domain-Pages, freie Struktur)
- `08_archive/` (erhält ursprüngliche Frontmatter)

Sonderfall `09_views/`: fixe Mini-Frontmatter (`type: view`, `ai-write: false`), kein Template.

## Frontmatter-Konventionen
- `stakeholders` (project-index): YAML-Liste mit quoted Wikilinks — `- "[[06_entities/people/<slug>]]"` bzw. `companies/<slug>`. Keine nackten Slugs, keine unquoted Wikilinks.
