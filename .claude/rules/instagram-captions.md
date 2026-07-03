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

## Aufbau (feste Reihenfolge, Stand: nutzerbestätigtes Beispiel)

1. **Opener** (1 Satz) — BLUF, stärkster Fakt zuerst (z. B. Cover-Placement schlägt reines "featured in"):
   `The '[Piece]' [Item-Typ] from my [Kollektion] collection is on the cover of @magazine's [Issue] 🖤`
   Alternative wenn kein Cover: `Published in @magazine` / `Thank you, @model, for wearing the '[Piece]'. Featured in @magazine!`
2. Direkt darunter (keine Leerzeile dazwischen): `Fashionstory: "[Titel]"` + Konzept-Satz (1–2 Sätze, nur was User liefert, nichts erfinden)
3. Leerzeile `.`
4. `See the full story here:` + `🔗 [link]` (nur wenn Link vorhanden)
5. Leerzeilen `..`
6. Credit-Header: `Thank you to the amazing team:`
7. Credits-Liste, **ohne Doppelpunkt**: `Rolle @handle`
   Reihenfolge wie geliefert, typische Rollen: Photo & Edit, Fashion Styling, MUA, Hair, Model, Agency — eigenes Piece als `[Item-Typ] @marleneraymakers_design` (z. B. `Dress @marleneraymakers_design`), nicht "Design (...)"
   Bei Gruppen-Editorials mit vielen Designern: andere Designer NUR auflisten, wenn User das explizit will (Standard: weglassen, Fokus auf eigenes Piece + direktes Team)
8. Leerzeilen `...`
9. **Hashtags — immer genau 6, nie mehr/weniger:**
   - Fixes Basis-Set (5, immer): `#marleneraymakers #slowfashion #sustainableluxury #fashioneditorial #madetomeasure`
   - Plus genau 1 Story-/Kollektion-spezifischer Tag (z. B. `#socialcapital`, `#fungifashion`, `#magazinecover`)

## Regeln
- Deutsch/Englisch: Caption-Text selbst bleibt **Englisch** (Instagram-Zielgruppe), auch wenn Chat mit User Deutsch läuft.
- Keine erfundenen Fakten (Material, Aussagen zur Vision) — nur, was User liefert.
- AI liefert die fertige Caption als Fließtext im Chat zum Copy-Paste, plus (Clipboard-Pflicht, siehe `communication.md`) via `pbcopy`-Heredoc in die Zwischenablage — sofern die Session lokal auf macOS läuft. In Cloud-/Remote-Sessions ohne Zugriff auf die macOS-Zwischenablage: Hinweis geben statt pbcopy zu versuchen.
- Bei fehlenden Pflichtfeldern (Model, Piece, mind. 1 Credit) nachfragen statt platzhalten.

## Beispiel (nutzerbestätigt, 03.07.2026)
```
The 'Circle Transparency' dress from my Social Capital collection is on the cover of @pap_magazine's June 2026 Issue 🖤

Fashionstory: "Trichomatic Devinity"
A trinity of black, silver, and flesh converges in sculptural ceremony, divinity engineered through texture, repetition, and the disciplined body.
.
See the full story here:
🔗 pap-magazine.com/editorial/trichomatic-devinity
.
.
Thank you to the amazing team:
Photo & Edit @abitze.fotoartist
Fashion Styling @by.lilue
MUA @melaniemariegeiger
Model @laurisogan
Dress @marleneraymakers_design
.
.
.
#marleneraymakers #slowfashion #sustainableluxury #fashioneditorial #madetomeasure #socialcapital
```
