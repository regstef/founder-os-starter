---
type: view
ai-write: false
---
# Waiting For

Tasks, auf die du wartest (`#waiting`) — Zuarbeit, Antwort, Lieferung von anderen. Verlinkte Entität zeigt, auf WEN. Sortiert nach Created → ältestes Warten oben (hängt am längsten).

Mit `⏳`-Nachhak-Datum versehene Tasks tauchen zusätzlich in der Wochenansicht auf, wenn das Nachfassen fällig ist.

Im Friday-Review durchgehen: noch aktuell? Nachhaken? Erledigt?

```tasks
tags include #waiting
not done
status.type is not CANCELLED
sort by created
```
