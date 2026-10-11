---
name: quarterly-review
description: Quartals-Review + -Planung als Interview (Quartalsbeginn, manuell "/quarterly-review"). Teil A: alte Ziele reviewen (Execution vs. Ergebnis, Lektion). Teil B: 1–2 neue Quartalsziele mit Messlatte + Wochen-Dosis. Schreibt 02_reviews/quartal.md. 30–45 Min.
---

# Quarterly-Review (Quartals-Interview)

Interview-Ritual, 30–45 Min. Basis: Radical Focus (Wodtke: 1 Objective, Confidence ~50 %), 12 Week Year (Lead vs. Lag, Execution getrennt vom Ergebnis), Pre-PMF-Warnung (kein OKR-Theater vor Product-Market-Fit — 1–2 Ziele als Lern- oder Umsatz-Hypothesen). Knapp, Deutsch.

SSOT: `02_reviews/quartal.md` (`## Aktuell` + `## Verlauf`). Kein separates File pro Quartal, keine Tools, plain Markdown.

## Ablauf

### 0. Vorbereitung (AI, ohne Fragen)
- `date` holen, Quartal bestimmen.
- Lesen: `02_reviews/quartal.md`, `02_reviews/top-goal.md` (kompletter `## Verlauf` des Quartals), Firmen-Entity (Lage, Kunden, Team), Domain-Files mit Zahlen (Finanzen, KPIs), aktive Projekte (`04_projects/*/INDEX.md`).
- Zahlen bereitlegen: Umsatz vs. Plan, Runway und Burn, Kundenstand, soweit im Vault vorhanden. Lücken als Frage, nicht schätzen.

### Teil A — Review altes Quartal (~15 Min; entfällt bei Erst-Planung)
1. Alte Ziele + Messlatten vorlegen: „Pro Ziel ✅/teilweise/❌ + die Zahl. Warum?“ → Review-Block für `## Verlauf`.
2. „Execution vs. Ergebnis: Wochen-Dosis geliefert? Wo gerissen — Verhalten oder Hypothese falsch?“ → 2–3 Diagnose-Bullets.
3. „Weiter / Stopp / Anders — je max 2 Punkte.“ → 3 Kurzlisten.
4. „Die eine Lektion des Quartals, ein Satz?“ → Learning-Zeile. Entscheidungs-Trigger prüfen (Skill `logs`).

### Teil B — Neues Quartal (~25 Min)
5. „Was muss in 12 Wochen wahr sein, damit die Firma messbar näher an Profitabilität oder Product-Market-Fit ist?“ Kandidaten sammeln, AI clustert und prüft jeden: zahlt er erkennbar darauf ein? Nicht klar ja → zurückstellen. → 3–5 Kandidaten.
6. „Davon: das EINE Engpass-Ziel? Höchstens ein zweites daneben?“ Hart deckeln bei 2 (max 3 nur mit expliziter Begründung). → Quartalsziele, qualitativ formuliert.
7. „Pro Ziel EINE Zahl oder ein binäres Ereignis als Messlatte — bei der du dir ~50 % gibst?“ (Confidence 5/10, kein Sandbagging) → je Ziel 1 Lag-Messgröße.
8. „Welche Wochen-Dosis kontrollierst du selbst dafür?“ (z. B. X Kundengespräche pro Woche) → je Ziel 1 Lead-Indikator. Danach: „Wochenziel für Woche 1?“ → `top-goal.md ## Aktuell`.

### Write
Diff-Vorschau `quartal.md` (Aktuell überschreiben, alter Block als Verlaufs-Eintrag) + `top-goal.md` → Bestätigung → Write.

## Verbote
- Mehr als 2–3 Ziele = keine Ziele. Startup-Default: eins.
- Ziele nicht mitten im Quartal umformulieren — Nachsteuern passiert im Wochenritual. Ziele ändern nur mit neuem Quartals-Interview + Begründung.
- OKR-Theater: keine Kaskaden, Gewichtungen, Scoring-Tools, keine reinen Lag-Metriken ohne kontrollierbare Wochen-Dosis.
- Teil A nie überspringen (außer Erst-Planung) — Review ist der Lernmechanismus.
- Ohne Antwort (unbeaufsichtigte Session): Vorbereitung stehen lassen, nichts schreiben.
