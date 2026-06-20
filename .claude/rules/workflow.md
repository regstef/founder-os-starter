# Workflow Rules

## Slow-Pages (Schreiben nur nach Bestätigung)
- `02_reviews/weekly/**/*` (Friday-Reviews)
- `06_entities/people/{{USER_SLUG}}.md` — Sections `## Strategie`, `## Werte`, `## Persönlich`
- Beliebige Files mit Frontmatter `ai-write: false`

AI schreibt diese Files NUR nach explizitem User-Befehl + Diff-Vorschau im Chat + Bestätigung vor dem Write. Nie proaktiv, nie im Batch. Modus: User spricht, AI sortiert + schlägt Text vor. (Decision: [[07_decisions/2026-06-12-slow-pages-bestaetigungspflicht]])

## Device-Mode
- Mobile: AI editiert via Chat-Output → User copy-paste in Obsidian
- Desktop: User tippt direkt, AI assistiert via Chat

User signalisiert Device im Chat wenn relevant.

## MIT-Pattern
1 Most Important Task pro Tag, als offene Frage formuliert ("Wenn es eine Sache gibt, die ich heute schaffen muss, welche?"). Keine Checkbox-Liste. Keine Stunden-Slots. Keine strikten Tagespläne.

## Capture-Garantie
Alles Capture-Eingehende landet in `00_inbox/` als roher Markdown. Kategorisierung später, nicht beim Capture. Filename: `YYYY-MM-DD-<kurz-slug>.md` ODER `YYYY-MM-DD-HHMM.md` für Fragmente.

## Universeller Eingang
AI ist der universelle Eingang. Aufgaben aus Slack/Mail/Linear/WhatsApp/sonstigem nennt oder leitet User weiter. AI:
1. Schlägt vor (Eintrag-Lokation + Inhalt)
2. User bestätigt
3. AI legt an: `00_inbox/` (Roh-Capture, später triagieren) ODER `01_daily/<heute>.md` (heute-zu-tun) ODER Project-Page (Projektkontext)

Nichts ungefragt umsetzen. Vorschläge als Vorschlag markieren, nicht als Fakt.

## Anti-Overengineering
- Kein Auto-Write-Hook
- Kein Index-File das AI nach Sessions updaten muss (Karpathy-Crash)
- Commands-First, Subagents-on-Demand (MVP: 0 Subagents, 0 Commands)
- Discover then encode: Patterns 1–2 Wochen ad-hoc nutzen, dann encodieren
- Reading vs. Thinking trennen: AI für Recherche/Triage/Zusammenfassung. Tippen für eigene Entscheidungen.

## Routinen
- Morgen-Ritual (6-Min-Tagebuch + MITs): User-driven
- Abend-Ritual (Tagesabschluss + Dankbarkeit): User-driven
- Friday-Review (statt Sonntag): User-driven. AI assistiert (sortieren, Textvorschlag), Write nur nach Bestätigung (Slow-Page-Regel oben)
- Wochenfokus: SSOT `02_reviews/wochenfokus.md` (AI-writable). Bei Friday-Review/Zuruf: alten Fokus als 1 Zeile in `## Verlauf`, `## Aktuell` überschreiben, `updated` setzen. Daily Template embedded `#Aktuell` — Heading-Namen stabil halten
- AI bietet on-demand Briefings (Cal/Linear-Pull), keine push-Notifications. Briefing-Start: Uhrzeit via Bash `date` holen (AI kennt nur Datum nativ, nicht Uhrzeit)
