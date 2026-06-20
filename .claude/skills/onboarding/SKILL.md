---
name: onboarding
description: Geführte Erst-Einrichtung des Founder-OS-Starters. Personalisiert Platzhalter ({{...}}) in CLAUDE.md + Rules, legt das Self-Entity an, füllt Tools/Initiativen, aktiviert Session-Imports. Trigger "/onboarding", "Vault einrichten", "Starter personalisieren", "Onboarding".
---

# Onboarding (Founder-OS-Starter personalisieren)

Frischer Starter → personalisierter Personal-OS-Vault. Einmal pro Vault laufen.
Sprache Deutsch/terse. **Slow-Page-Disziplin:** jeder Write zuerst als Diff-Vorschlag im Chat, dann Bestätigung, dann schreiben. Nie im Batch ohne OK.

## Platzhalter-Set (das hier wird ersetzt)
| Platzhalter | Bedeutung | Default |
|---|---|---|
| `{{USER_NAME}}` | Voller Name | — |
| `{{USER_SLUG}}` | `vorname-nachname`, lowercase ASCII, Umlaute auflösen (ö→oe, ü→ue, ä→ae, ß→ss) | aus Name ableiten |
| `{{USER_EMAIL}}` | Haupt-E-Mail | — |
| `{{USER_CAL_EMAIL}}` | Kalender-E-Mail | = USER_EMAIL |
| `{{COMPANY_NAME}}` | Eigene Firma (Name) | leer = keine |
| `{{COMPANY_SLUG}}` | Firma-Slug (lowercase ASCII) | leer = keine |
| `{{TZ}}` | Zeitzone | Europe/Berlin |

## Phase A — Interview
Frag knapp ab (BLUF, eine Frage-Gruppe pro Schritt, nicht alles auf einmal):
1. Name → `{{USER_SLUG}}` selbst ableiten + bestätigen lassen.
2. Haupt-E-Mail + Kalender-E-Mail (oft gleich) + Zeitzone (Default Europe/Berlin).
3. Eigene Firma? Ja → Name + Slug, später Company-Entity. Nein → Firmen-Zeilen entfernen statt ersetzen.
4. Welche MCPs/Tools sind real verbunden? (Calendar / Linear / Notion / Slack / Gmail / weitere) → nur die behalten, Rest aus `tools.md` löschen.
5. Initiativen & Owner für `operating-model.md`? (eigene eintragen ODER Section auf Solo-Minimum kürzen). Bei Solo/privat: Initiativen-Liste reduzieren.
6. Kommunikations-Prefs: Defaults aus `communication.md` erben — Tweaks? (Sprache, Stil, Datumsformat sind schon gesetzt; nur fragen, ob etwas abweicht.)
7. API-Keys/.env nötig? Nur falls eigener Outreach/Enrichment-Workflow. Sonst überspringen.

## Phase B — Actions (je Diff-Preview + Confirm)
1. **Self-Entity** `06_entities/people/{{USER_SLUG}}.md` aus `_templates/entity-person.md`.
   - Frisch + minimal: `relation: self`, Name, Rolle/Kontext kurz, E-Mail, TZ. Sonst leer lassen — wächst organisch.
   - KEINE fremden CRM-Daten, keine Vergütungs-/Beziehungs-Historie von außen reinkopieren.
2. **Company-Entity** (nur falls Firma) `06_entities/companies/{{COMPANY_SLUG}}.md` aus `_templates/entity-company.md`, `relation: self`.
3. **Find/Replace** aller Platzhalter über: `CLAUDE.md`, `.claude/rules/entity-handling.md`, `.claude/rules/workflow.md`, `.claude/rules/tools.md`, `.claude/rules/operating-model.md`. Keine Firma → Firmen-Zeilen ersatzlos entfernen, nicht mit Leerstring füllen.
4. **tools.md** auf real verbundene Tools kürzen, `⚠️`-Banner entfernen.
5. **operating-model.md** Initiativen/Owner einsetzen (oder kürzen), `⚠️`-Banner entfernen.
6. **CLAUDE.md** Session-Start-Imports aktivieren: Self-Entity-Kommentarzeile zu echtem `@`-Import machen (Firma nur falls vorhanden). `⚠️`-Starter-Banner entfernen.
7. **.env** (optional) aus `.env.example` anlegen, falls Phase A.7 ja.

## Phase C — Verify (Bash)
```
grep -rn "{{" . --include='*.md' | grep -v '/_templates/'   # 0 Treffer (Templater <%...%> in _templates ist OK)
ls 06_entities/people/{{USER_SLUG}}.md                        # existiert
```
- CLAUDE.md `@`-Imports zeigen auf existierende Files (Self-Entity + wochenfokus, ggf. Firma).
- Hinweis an User (kein Auto-Run): `git add -A && git commit -m "chore: onboarding personalization"`.

## Danach
Onboarding fertig. Normaler Vault-Betrieb. Diesen Skill nicht erneut laufen (idempotent nur beim ersten Mal sinnvoll).
