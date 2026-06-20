---
type: view
ai-write: false
---
# Wochenansicht

Diese Woche fällig oder geplant, inkl. Überfälligem aus Vorwochen. Gruppiert nach Datum. Cancelled + Someday ausgeschlossen.

```tasks
(due before next week) OR (scheduled before next week)
not done
status.type is not CANCELLED
status.type is not NON_TASK
group by happens
```

## Nächste Woche

Für Freitag-Engpassrunde: Blick nach vorn.

```tasks
(due next week) OR (scheduled next week)
not done
status.type is not CANCELLED
status.type is not NON_TASK
group by happens
```
