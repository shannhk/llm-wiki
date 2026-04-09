---
description: Research a question against the wiki
allowed-tools: Read, Write, Edit, Bash, Glob, Grep
---

Read CLAUDE.md for conventions.

Read wiki/index.md - scan TLDRs only to identify relevant pages.
Only load full pages that are relevant to the question.

Synthesize an answer with citations to specific [[wiki pages]].

Save the answer as wiki/{question-slug}.md with type: output frontmatter.
Update wiki/index.md with the new entry.
Append to wiki/log.md.

$ARGUMENTS
