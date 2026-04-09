---
description: Process new raw sources into the wiki
allowed-tools: Read, Write, Edit, Bash, Glob, Grep
---

Read CLAUDE.md for all conventions and operations.

Read wiki/index.md to understand existing coverage.

PHASE 0 - SORT CLIPPINGS:
Check raw/clippings/ for new files. For each, detect the type from
the source URL or content, then move to the correct subfolder:
- X/Twitter URL -> raw/bookmarks/
- YouTube URL -> raw/bookmarks/
- Reddit URL -> raw/bookmarks/
- Web article/blog -> raw/articles/
- PDF -> raw/papers/
- Plain text / idea / no URL -> raw/ideas/
Remove from raw/clippings/ after moving.

Then scan all of raw/ for unprocessed source files (any file not yet
summarized in wiki/).

PHASE 1 - RESOLVE:
For each unprocessed source, detect if it contains a URL or unresolved reference.
If so, fetch full content using the right tool and update the file in-place
(preserving original URL in frontmatter):
- YouTube URL (youtube.com, youtu.be): run yt-dlp to get transcript + metadata
- X/Twitter URL (x.com, twitter.com): fetch via X API. If image attached, download to raw/assets/images/ with descriptive name and analyze content. If video attached, extract transcript via yt-dlp and download thumbnail.
- Web URL / Reddit URL: scrape with scrapling
- PDF file: read directly
- Bookmark dump (list of URLs): parse each URL, create one file per URL in raw/, resolve each
- Plain text / notes: already resolved, skip

PHASE 1.5 - MEDIA EXTRACTION:
For any source with attached images or video:
- Download images to raw/assets/images/ with descriptive kebab-case names
- Analyze image content (diagrams, screenshots, infographics, data)
- Extract video transcripts via yt-dlp --write-auto-sub --skip-download
- Add media references to raw file frontmatter
- Images often contain the actual information - capture the visual knowledge

PHASE 2 - CLASSIFY & COMPILE:
For each source (now containing full content + media):
1. Classify the source type (transcript, paper, report, article, tweet, reddit, notes)
2. Create a source summary in wiki/ using type-specific extraction (include image analysis and embeds)
3. Identify concepts, entities, and projects mentioned
4. Create new wiki pages for concepts appearing in 2+ sources
5. Create stub pages for single-mention concepts
6. Update existing pages by appending new information
7. Add [[wikilinks]] to connect new content to existing pages
8. Include Counter-arguments and Data gaps sections where required
9. Update wiki/index.md with new entries and TLDRs
10. Append to wiki/log.md with date, operation type, pages touched

Never leave a [[wikilink]] pointing to nothing - create stubs.
Never rewrite existing pages from scratch - append and update.

Report when done: sources processed, pages created, pages updated,
cross-links added.
