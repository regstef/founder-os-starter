---
type: daily
date: <% tp.date.now("YYYY-MM-DD") %>
---
# <% tp.date.now("DD.MM.YYYY") %>

![[02_reviews/wochenfokus#Aktuell]]

> [!check] Heute + Überfällig
> ```tasks
> (due on or before {{query.file.filenameWithoutExtension}}) OR (scheduled on or before {{query.file.filenameWithoutExtension}})
> not done
> status.type is not CANCELLED
> status.type is not NON_TASK
> sort by due
> group by path
> ```

> [!info] Views
> - [[09_views/wochenansicht|Wochenansicht]]
> - [[09_views/by-source|By Source]]
> - [[09_views/inbox-triage|Inbox-Triage]]
> - [[09_views/someday|Someday]]

## Morgen
- Wofür bin ich dankbar?
- Was würde diesen Tag wundervoll machen?
- Affirmation:
- Wenn es eine Sache gibt, die ich heute schaffen muss, welche?

## Inbox


## Abend
- Wofür heute dankbar:
- Was lief gut / Erfolg:
- Was schwer war / Lernpunkt:
- Morgen wichtig:
