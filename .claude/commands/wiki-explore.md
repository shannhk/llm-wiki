---
description: Research and expand a wiki topic
allowed-tools: Read, Write, Edit, Bash, Glob, Grep, WebFetch, WebSearch
---

Read CLAUDE.md for all conventions and operations.

Read wiki/index.md to understand existing coverage.

The user wants to explore and expand a topic. Follow the EXPLORE operation:

1. Read the existing wiki page for the topic (if it exists)
2. Identify gaps, thin sections, and open questions from the Data gaps section
3. Search for additional information using web search, scraping, or other tools
4. Expand the page with new findings, always citing sources
5. Create new source pages in wiki/sources/ for any external material found
6. Update related concept and entity pages with cross-references
7. Set confidence based on source quality and corroboration
8. Set explored: false (always - only the human validates)
9. Update wiki/index.md and wiki/log.md

Be honest about confidence levels. Flag contradictions.
Don't make connections that aren't supported by sources.

$ARGUMENTS
