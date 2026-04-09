---
description: Health-check the wiki
allowed-tools: Read, Write, Edit, Bash, Glob, Grep
---

Read CLAUDE.md for conventions.

Perform a full health check:
1. Find contradictions between pages (same topic, conflicting claims)
2. Find orphan pages (no inbound [[wikilinks]] from other pages)
3. Find broken [[wikilinks]] pointing to non-existent pages
4. Identify pages with missing frontmatter fields
5. Flag stale content (date_modified > 6 months ago)
6. Suggest new articles for frequently mentioned but unlinked concepts
7. Check for duplicate concepts under different names - propose merges
8. Fix automatically where possible (broken links, missing frontmatter)

Output report to wiki/lint-report-{date}.md.
Update wiki/log.md.
