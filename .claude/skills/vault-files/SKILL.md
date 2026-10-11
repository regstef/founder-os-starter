---
name: vault-files
description: Neues File im Vault anlegen oder verschieben — Entity (Person, Firma), Projekt-INDEX, Domain-Destillat, Inbox-Dump, Log. Slug-Regeln, Template-Pflicht, Frontmatter-Konventionen, Ordnerwahl, 03_domains-Aufnahmetest, Projekt-Innenstruktur, Archiv-Ritual. Laden, bevor ein File erzeugt, umbenannt, verschoben oder archiviert wird.
---

# Vault-Files: anlegen, einordnen, archivieren

Ordnerkarte und harte Regeln (SSOT, sensible Daten, kein Auto-Write) stehen in `AGENTS.md`. Hier steht das Wie. Task-Notes: Skill `tasks`.

## Ordnerwahl
- **Flach oder Buckets?** Ungleichartiger Inhalt → Unterordner, keine losen Root-Files (`03_domains`, `04_projects`, `06_entities`). Gleichartige Einheiten → flach (`00_inbox`, `01_tasks/notes`, `02_reviews`, `05_logs`).
- Datiertes gehört ins Log, Nachschlagbares nach `03_domains`, „woran ich arbeite“ nach `04_projects`, Gegenwart einer Entität ins Entity-File, To-dos in Task-Notes.

## Templates (Pflicht für Files mit Frontmatter)
| Filename-Pattern | Template |
|---|---|
| `06_entities/people/<slug>.md` | `_templates/entity-person.md` |
| `06_entities/companies/<slug>.md` | `_templates/entity-company.md` |
| `04_projects/<slug>/INDEX.md` | `_templates/project-index.md` |

- Frontmatter Pflicht: `04_projects/<slug>/INDEX.md`, `06_entities/`, Task-Notes. Optional: `00_inbox/`, `03_domains/`, `05_logs/` (Kopfzeile statt Frontmatter, Skill `logs`), `08_archive/` (behält Original-Frontmatter).
- Den Platzhalter `{{date:YYYY-MM-DD}}` füllt in Obsidian das Core-Plugin Vorlagen („Vorlage einfügen“). AI ersetzt ihn beim Schreiben direkt: ISO `YYYY-MM-DD` in Frontmatter und Filenames, `DD.MM.YYYY` im Content.
- `stakeholders` (project-index): YAML-Liste mit quoted Wikilinks `- "[[06_entities/people/<slug>]]"` bzw. `companies/<slug>`. Keine nackten Slugs, keine unquoted Wikilinks.

## Entities
- **Neue Entität:** Person oder Firma ohne File → fragen „Soll ich `06_entities/.../<slug>.md` anlegen?“, bei Ja Template nutzen. Klienten und ihr privates Umfeld bekommen nie ein File (`AGENTS.md`, Regel 1).
- **Slug:** Person `vorname-nachname.md`, Firma `firma-name.md`; lowercase, ASCII, ö→oe, ü→ue, ä→ae, ß→ss, Leerzeichen → `-`.
- **Relation-Werte** Person: `self | co-founder | employee | freelancer | partner | prospect | customer | advisor | investor | friend`. Company: `self | partner | prospect | customer | competitor | vendor`.
- `company:` bei Person als quoted Wikilink, wenn die Company-Entity existiert, sonst Plaintext.
- `relation: prospect | customer` → `last-contact` bei jeder Interaktion updaten, `## Beziehungs-Historie` mit Datum ergänzen.
- **Agenda:** Gesprächspunkte fürs nächste Treffen in `## Agenda` des Entity-Files, 1 Zeile je Punkt, kein Datum, kein Done; erledigt = Zeile löschen. Neue Stände gehören in `## Beziehungs-Historie`, nicht als Sub-Bullets unter den Punkt. Team- und Gründerrunde → Firmen-Entity.
- **SSOT-Update:** neue Fakten (Rolle, Status, Deal, Beziehung) → „Das ändert `<file>`, Update vorschlagen?“, Diff im Chat, Write nach Bestätigung. Gilt analog für veraltete Regeln in `AGENTS.md` und Skills.
- Wächst das File über die Schwellen (Skill `logs`, Entity-Abfluss) → Abfluss vorschlagen.

## 03_domains: Aufnahme und Abfluss
Nachschlagewerk, kein Ablagekeller. Aufnahme nur, wenn alle drei stimmen: wiederverwendbar (Destillat, Dossier, Vorlage, Zahlen, Deck; nicht „was passiert ist“ → `05_logs/`, nicht „woran ich arbeite“ → `04_projects/`), kein Entity-Wissen, überlebt seinen Anlass.
- Buckets nach Herkunft (z. B. `<firma>` · `recherche` · `persoenlich`), passt nichts → nächstbester. Neuer Bucket erst ab 3 Files, kein Ordner pro Thema.
- Filenames: Themen-Slug ohne Datum. Datum im Namen = Historie-Signal → `05_logs/`. Ausnahmen: Transkripte `YYYY-MM-DD-<slug>-transkript.md`, versionierte Decks.
- Abfluss: nur noch Historie → `05_logs/`, Zweck erledigt → `08_archive/`. AI schlägt beim Berühren vor, nie Auto-Write.

## Projekte
- Task-SSOT ist `01_tasks/notes/` (Skill `tasks`). Der INDEX trägt Ziel, Status, Nächste-Schritte-Prosa, Notizen. Keine Checkboxen im INDEX; findet AI welche → als Task-Note vorschlagen (Bündel-Check).
- 1 lebendes File pro Denk-Strang, Stand-Datum im Header, nicht im Filename. Neuer Stand als eigenes File → Vorgänger sofort ins Archiv. Versendete Artefakte werden nicht überschrieben.
- Keine handgepflegte „Files in Projekt“-Liste (driftet). Rollen, die man am Namen nicht sieht, als Satz in `## Notizen`.
- **Archiv-Ritual:** 1. Offene Task-Notes mit `projects:`-Link auf diesen INDEX erledigen, löschen oder umhängen. 2. Wiederverwendbares nach `03_domains/` destillieren. 3. Rest komplett nach `08_archive/`. 4. ⚖️-Zeile im vault-log (Skill `logs`).

## Inbox
Roher Dump → `00_inbox/YYYY-MM-DD-<slug>.md`, kein Frontmatter nötig. Inbox ist Auffangnetz, Triage in der Wochenplanung; nichts ungefragt umsetzen, Vorschläge als Vorschlag markieren.
