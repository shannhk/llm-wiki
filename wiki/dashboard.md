---
title: "Wiki Dashboard"
tldr: "Dataview dashboard for browsing wiki stats and recent activity"
date_created: {{date}}
date_modified: {{date}}
explored: false
confidence: medium
---

# Wiki Dashboard

> Requires the [Dataview](https://github.com/blacksmithgu/obsidian-dataview) plugin for Obsidian.

## Recent Pages

```dataview
TABLE tldr, confidence, explored
FROM "wiki"
WHERE type
SORT date_modified DESC
LIMIT 20
```

## Unreviewed Pages

```dataview
TABLE tldr, type, confidence
FROM "wiki"
WHERE explored = false AND type
SORT date_modified DESC
```

## Pages by Type

```dataview
TABLE length(rows) AS Count
FROM "wiki"
WHERE type
GROUP BY type
SORT length(rows) DESC
```

## Low Confidence Pages

```dataview
TABLE tldr, type
FROM "wiki"
WHERE confidence = "low" OR confidence = "uncertain"
SORT date_modified DESC
```

## Recent Sources

```dataview
TABLE tldr, source_type, confidence
FROM "wiki/sources"
SORT date_created DESC
LIMIT 15
```

## Stale Pages (Modified 6+ Months Ago)

```dataview
TABLE tldr, type, date_modified
FROM "wiki"
WHERE type AND date_modified < date(today) - dur(6 months)
SORT date_modified ASC
```
