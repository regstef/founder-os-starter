---
name: logs
description: Gedächtnis-System in 05_logs/ — Log-Eintrag schreiben, ⚖️-Entscheidung formatieren, Überholt-Vermerk setzen, neues Log anlegen, Entity-Abfluss bei Schwellen-Überschreitung. Laden, bevor ein Log berührt, eine Entscheidung festgehalten oder ein Entity-File gekürzt wird.
---

# Logs (05_logs/) — Gedächtnis-System

Ein System für Historie UND Entscheidungen. Harte Regeln (SSOT, kein Auto-Write) stehen in `AGENTS.md`.

## Denkmodell (3 Ebenen)
| Ebene | Frage | Ort |
|---|---|---|
| Entity / Regel | Was gilt JETZT? | `06_entities/`, `AGENTS.md`, Skills (SSOT, wird überschrieben) |
| Log | Wie kam es dazu? | `05_logs/<slug>-log.md` (append-only, chronologisch absteigend) |
| — | Banales | gar nicht |

Abgrenzung zu `03_domains/`: Log = *wie kam es dazu* (chronologisch, append-only). `03_domains` = *wiederverwendbares Destillat* (zeitlos, wird überschrieben). Datiertes gehört ins Log, Nachschlagbares ins Domain-File.

## Log-Files
- Pro Subjekt ein Log: Entity-Logs (`<person>-log`, `<firma>-log`) plus `vault-log` (Vault, Regeln, AI-Setup, Meta).
- Anlegen erst beim ersten Eintrag, kein Vorrat. Suffix `-log` Pflicht (sonst Kurzlink-Kollision mit dem Entity-File).
- Kein Frontmatter-Zwang. Kopfzeile: Subjekt-Link + Verweis `Regeln: Skill \`logs\``.

## Wann was loggen
1. **Relevanter Punkt** in Zusammenarbeit mit Person, Firma oder Tool → Log-Eintrag, 1 bis 5 Zeilen: `- YYYY-MM-DD — <was>`
2. **Entscheidung** → gleicher Ort, markiert: `- YYYY-MM-DD ⚖️ **<Titel>.** <Kern + Begründung in 1 bis 2 Sätzen, verworfene Alternativen nur wenn lehrreich>`. Ersetzt sie eine frühere: im neuen Eintrag benennen, am alten Eintrag kursiven Vermerk *„Überholt <Datum>“* ergänzen.
3. Gilt das Ergebnis dauerhaft (Kondition, Deal, Rolle, Regel) → **zusätzlich** Entity, `AGENTS.md` oder Skill updaten. Log erklärt, SSOT gilt.
4. Relevanz-Test: „Will ich das in 3 Monaten nachlesen können?“ Nein → gar nicht loggen. Mikro-Entscheidungen (Plugin, Format, Deko): max. 1 Zeile im vault-log, im Zweifel weglassen.

## Entscheidungs-Trigger (AI)
Bei Geld, People, Strategie oder Richtung, Tool-Wechsel oder Wirkung über einen Monat: AI schlägt vor „Das klingt nach ⚖️-Eintrag in <log>. Loggen?“ User bestätigt. Kein Auto-Write.

## Entity-Abfluss (gegen unkontrolliertes Wachstum)
Schwellen (weich: AI schlägt vor, User bestätigt, nie Auto-Write):
- Einzelne Section (Beziehungs-Historie, Notizen) **über 20 Zeilen**
- File gesamt: Person **über 60 Zeilen oder 5 KB**, Company **über 100 Zeilen oder 8 KB**. Die Byte-Schwelle fängt Files mit sehr langen Zeilen.
Beim Überschreiten: abgeschlossene oder historische Einträge → Entity-Log verschieben (nicht kopieren), Entity behält Essenz + Verweis `[[05_logs/<slug>-log]]`. Trigger: (a) AI berührt das File, (b) Check-Punkt in der Wochenplanung. Self- und Firmen-Entity laden bei jedem Session-Start, dort am strengsten.
