# Tasks-Syntax (Obsidian Tasks-Plugin)

Gilt für jede `- [ ]`-Zeile im Vault.

## Datums-Marker (einzige gültige Form)
- `📅 YYYY-MM-DD` — Fälligkeit (Deadline)
- `⏳ YYYY-MM-DD` — Scheduled (geplanter Arbeitstag, keine Deadline)
- `🛫 YYYY-MM-DD` — frühester Start („frühestens X", „ab KW Y")
- `✅` — setzt Plugin beim Abhaken. AI schreibt nie manuell.
- `- [?]` — Someday/Backlog (Status NON_TASK)

## Verbote
- Fälligkeit NIE als Prose/Bold im Task-Text („**Mo 15.06.**", „vor Freitag", „bis 17.06.")
- Wochentag-Kontext im Text OK, ersetzt aber nie den 📅-Marker
- Marker stehen am Zeilenende, Reihenfolge: 🛫 ⏳ 📅

## Waiting-For (`#waiting`)
Tasks, auf die du auf Zuarbeit/Antwort/Lieferung von anderen wartest.
- Marker: Tag `#waiting` am Zeilenende
- **Pflicht:** Entity-Link auf die Person/Firma, auf die gewartet wird (`[[06_entities/...]]`) → Backlink = CRM
- **Pflicht:** `➕ YYYY-MM-DD` (Created) = seit wann gewartet
- Optional: `⏳ YYYY-MM-DD` = Nachhak-Datum (taucht dann in Wochenansicht auf)
- Beispiel: `- [ ] Vollmacht von [[06_entities/people/marcel-friedrich]] #waiting ➕ 2026-06-13`
- Waiting-Tasks brauchen KEIN due/scheduled — eigener Bucket (`09_views/waiting-for.md`), aus Inbox-Triage ausgeschlossen.

## Undatiert
Nur erlaubt in Daily-Note `## Inbox`. Überall sonst: Datum setzen oder `- [?]` oder `#waiting`.
Prüfung: Inbox-Triage-View (`09_views/inbox-triage.md`) soll gegen 0 laufen.

## AI-Pflicht beim Task-Anlegen
Erkennt AI ein Datum im Task-Kontext → als Marker codieren, nicht als Text.
Unklar ob due oder scheduled → fragen, nicht raten.
