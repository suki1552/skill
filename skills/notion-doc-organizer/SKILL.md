---
name: notion-doc-organizer
description: Use this skill when the user wants to organize, clean up, restructure, or de-duplicate content in Notion - e.g. "정리해줘 이 노션 페이지", "clean up my Notion docs", "organize this Notion database", "이 노션 문서 구조 좀 정리해줘", or "merge these duplicate Notion pages". Not for creating a single new page from scratch with no existing content to reorganize.
---

# Notion Doc Organizer

Reorganizes existing Notion pages/databases into a clean, consistent structure without losing content.

## Workflow

1. **Locate the target.** Use `notion-search` or `notion-fetch` to find the page(s)/database the user means. If the user gives a URL, fetch it directly. If scope is ambiguous ("정리해줘 노션" with no page named), ask which page/workspace area, or search recently edited pages (`notion-fetch` on a parent page, or ask the user for a link).

2. **Read before touching.** Fetch the full current content (`notion-fetch`, `notion-query-data-sources` / `notion-query-database-view` for databases) so you understand the existing structure, headings, and any properties/tags in use. Never restructure blind.

3. **Diagnose common issues:**
   - Inconsistent or missing heading hierarchy (H1/H2/H3 not nested logically)
   - Duplicate pages or repeated sections covering the same topic
   - No table of contents on long pages
   - Inconsistent formatting (mixed bullet/numbered lists for the same kind of content, inconsistent callouts)
   - Stale/orphaned pages not linked from anywhere
   - Database entries missing properties other entries have (inconsistent schema use)

4. **Propose a plan before large changes.** For anything beyond trivial fixes (reordering a couple of blocks), summarize the intended reorganization (new structure, what gets merged/moved/archived) and get user confirmation before applying it - merges and moves are hard to undo cleanly.

5. **Apply changes:**
   - Structural edits within a page: `notion-update-page`
   - Moving pages between parents: `notion-move-pages`
   - Combining duplicates: fold content into the canonical page via `notion-update-page`, then move the duplicate under the canonical page (or ask the user whether to archive it - don't delete outright).
   - New database views/organization: `notion-create-view`, `notion-update-data-source`

6. **Summarize what changed.** After applying, report: pages merged/moved, structural changes made, and anything flagged but left alone (e.g. "found 2 possible duplicates I wasn't sure about - confirm before I merge").

## Guardrails
- Don't delete or archive content without calling it out first - prefer merging/moving over destructive changes.
- Preserve original content when merging; don't summarize-away information to make pages shorter.
- If the workspace is large, work section by section rather than attempting a full reorg in one pass.
