---
type: view
ai-write: false
---
# Inbox-Triage

Tasks ohne Fälligkeitsdatum UND ohne Scheduled-Date, die noch nicht als Someday markiert sind. Diese Liste sollte abends oder im Friday-Review auf 0 oder nahe 0 sein.

Pro Task entscheiden: heute fertig (due setzen), Projekt-Match (cut+paste in Projekt-INDEX), Domain-Match (in Domain-Page), oder Someday (Status `?` setzen).

Waiting-Tasks (`#waiting`) sind ausgeschlossen — die haben einen eigenen Bucket (`waiting-for.md`) und müssen kein Datum tragen.

```tasks
no due date
no scheduled date
not done
status.type is not CANCELLED
status.type is not NON_TASK
tags do not include #waiting
sort by path
group by path
```
