---
name: meeting-notes
description: Use this skill when the user asks to take, organize, or summarize meeting notes - e.g. "write up notes from this meeting", "summarize this call", "turn this transcript into meeting notes", or "create a meeting notes doc". Produces a consistent, scannable meeting notes format with attendees, decisions, and action items.
---

# Meeting Notes

Turn raw meeting input (a transcript, bullet points, or a live recap from the user) into a clean, consistent meeting notes document.

## Workflow

1. **Gather the raw material.** Ask for or use whatever is available: a transcript, the user's rough notes, or a spoken recap. If key fields below are missing, ask briefly rather than guessing.
2. **Extract structure**, don't just reformat prose. Pull out:
   - Meeting title, date, and attendees
   - Purpose/agenda (one line, if identifiable)
   - Key discussion points (grouped by topic, not chronological transcript order)
   - Decisions made
   - Action items, each with an owner and, if mentioned, a due date
   - Open questions / unresolved items
3. **Write the output** using the template below. Omit sections with no content rather than leaving them empty.
4. **Keep it scannable.** Prefer short bullets over paragraphs. Don't editorialize or add commentary that wasn't discussed.

## Output template

```markdown
# <Meeting Title>

**Date:** <date>
**Attendees:** <names>

## Summary
<1-3 sentence summary of what the meeting was about and its outcome>

## Discussion
- <topic>: <key point(s)>

## Decisions
- <decision>

## Action Items
- [ ] <task> - @<owner> <due date if any>

## Open Questions
- <question>
```

## Notes

- If no clear owner is stated for an action item, note it as "unassigned" rather than guessing who owns it.
- If asked to save the notes to a file, use a descriptive filename like `YYYY-MM-DD-<topic>-meeting-notes.md`.
