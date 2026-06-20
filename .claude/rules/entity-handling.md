# Entity Handling

## SSOT Strikt
Entity-Wissen NUR in Entity-File. Niemals frei in anderen Files.

- Person → `06_entities/people/<slug>.md`
- Firma → `06_entities/companies/<slug>.md`

User selbst = `{{USER_SLUG}}.md`. Eigene Firma = `{{COMPANY_SLUG}}.md` (falls vorhanden). Behandlung gleich wie externe Entitäten.

## Links Pflicht
Erwähnung einer Entität in beliebigem File → `[[06_entities/people/<slug>]]` oder `[[06_entities/companies/<slug>]]`.

Obsidian-Backlinks ersetzen CRM-Datenbank. Interaktions-Historie = Backlinks im Entity-File.

## Neue Entität
Wenn neue Person/Firma erwähnt wird, die noch kein File hat:
1. AI fragt User: "Soll ich `06_entities/.../<slug>.md` anlegen?"
2. Bei Ja: Template aus `_templates/entity-person.md` oder `_templates/entity-company.md`
3. Frontmatter Pflicht — kein Free-Form

## Slug-Convention
- Person: `vorname-nachname.md` (lowercase, ASCII, Umlaute auflösen: ö→oe, ü→ue, ä→ae, ß→ss)
- Firma: `firma-name.md` (lowercase, ASCII, Leerzeichen → `-`)

## Frontmatter
Siehe `_templates/entity-person.md` und `_templates/entity-company.md`. Verbindlich.

### Relation-Werte (gelebtes Schema)
- Person: `co-founder | employee | freelancer | partner | prospect | customer | advisor | investor | friend`
- Company: `self | partner | prospect | customer | competitor | vendor`

### Company-Feld (Person)
Existiert Company-Entity → quoted Wikilink: `company: "[[06_entities/companies/<slug>]]"`. Nur wenn kein Entity-File existiert: Plaintext.

## Sales-CRM-Trigger
Wenn Person `relation: prospect | customer`:
- `last-contact` bei jeder Interaktion updaten (Frontmatter)
- Section `## Beziehungs-Historie` mit Datum + Kurz-Eintrag erweitern
- Phase 2 ggf. autonomer Sales-Agent (siehe Spec §6.5)
