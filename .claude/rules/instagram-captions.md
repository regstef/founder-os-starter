# Instagram Captions — Magazine-Veröffentlichungen

Template für Captions zu Magazine-Features (Marlene Raymakers Design, @marleneraymakers_design). User schickt nur Rohdaten, AI baut die fertige Caption im gelernten Stil.

## Input, das User schickt
Nicht alle Felder sind immer nötig — AI arbeitet mit dem, was kommt, und fragt bei Unklarheit nach (nie raten):
- Model-Handle(s)
- Piece-Name (z. B. "Mycelium Whisper", "Mushroom Muse")
- Magazine/Publication-Handle (z. B. @rollupmagazine, @lofficielbaltic)
- Story-Titel, falls vorhanden (z. B. "Mushroom Mystery")
- Link zur Full-Story, falls vorhanden
- Kurzer Kontext zum Piece/Material (z. B. Mushroom Leather, Nachhaltigkeits-Winkel) — optional, nur wenn User es mitschickt
- Team-Credits als Liste: Rolle → Handle
- Ob es "published" (Feature in fremdem Magazin) oder "collab/thank you" (eigener Post, Model dankt/wird gedankt) ist

## Aufbau (feste Reihenfolge)

1. **Opener** (1 Satz), Varianten je nach Fall:
   - Feature-Dank: `Thank you, @model, for wearing the '[Piece]'. Featured in @magazine!`
   - Eigenes Feature: `@model wearing the [Piece]. [1 Satz Beschreibung/Bewegung/Formsprache].`
   - Fremd-Publikation: `Published in @magazine` (kurz, eigene Zeile) + danach `@model is wearing the [Piece] – featured in @magazine`
2. Optional: `.` als Leerzeile-Trenner
3. Optional: `Fashionstory: "[Titel]" [passendes Emoji]`
4. Optional: `See the full story here:` + `🔗 [link]`
5. Optional: 1–3 Sätze Kontext/Vision (Material, Inspiration, Nachhaltigkeit) — nur wenn User Stichpunkte dazu liefert, nicht erfinden
6. Leerzeile(n) `.`
7. Credit-Header: `The amazing team:` (Standard) oder `Thank you to the team:` (wenn Opener schon dankt, um Wiederholung zu vermeiden)
8. Credits-Liste, **ohne Doppelpunkt**: `Rolle @handle`
   Reihenfolge wie geliefert, typische Rollen: Photo, MUA/Make-up, Hair, Styling, Styling assistant, Model(s), Agency, Material [Piece], Design [Piece], Golden hand assistant, Publication, Design
9. Leerzeile(n) `.`
10. Optional Sign-off-Zeile mit passendem Emoji (situativ gewählt, z. B. 🦋 bei Bewegung/Natur, 🖤/🤍 bei minimalistisch-elegant) — kein festes Emoji, an Story-Ton anpassen
11. Leerzeile(n) `.`
12. **Hashtags** — fixes Basis-Set + Story-Tags:
    - Basis (immer): `#marleneraymakers #slowfashion #sustainableluxury #fashioneditorial #madetomeasure`
    - Plus 3–6 Story-/Material-spezifische Tags, aus Piece-Name/Material/Magazin abgeleitet (z. B. bei Mushroom-Leather-Piece: `#fungifashion #mycelium #mushroomleather`; bei Magazine-Cover: `#magazinecover`)

## Regeln
- Deutsch/Englisch: Caption-Text selbst bleibt **Englisch** (Instagram-Zielgruppe), auch wenn Chat mit User Deutsch läuft.
- Keine erfundenen Fakten (Material, Aussagen zur Vision) — nur, was User liefert.
- AI liefert die fertige Caption als Fließtext im Chat zum Copy-Paste, plus (Clipboard-Pflicht, siehe `communication.md`) via `pbcopy`-Heredoc in die Zwischenablage.
- Bei fehlenden Pflichtfeldern (Model, Piece, mind. 1 Credit) nachfragen statt platzhalten.
