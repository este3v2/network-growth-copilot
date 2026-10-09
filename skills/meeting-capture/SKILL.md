---
name: meeting-capture
description: Logs a meeting or event conversation to a person's file. Use when the user says "log this meeting", "capture meeting with X", "I just met X", "save this transcript", or pastes a transcript or voice-note text. Takes a person name plus text, extracts topic, next action and key insight, and hands back a block to paste into that person's file. Creates the person file if it doesn't exist. Not for 1:1 message drafts (that's network-outreach).
---

# meeting-capture - turn a conversation into a record

One job: after you speak with someone, turn what happened into a clean entry on that person's file.

## Step 0: Load config

Find `CONFIG.md` (current folder first, then `~/.claude/network-growth-copilot/CONFIG.md`). If missing, ask the user for its path. Use `people_folder` and `daily_notes_folder` (optional).

## Step 1: Identify the person

Match `$ARGUMENTS` (a name) against filenames and `title` fields in `people_folder`. A first name or partial name is fine unless ambiguous, in which case ask which one.

If no match exists, say: "No file for [name] yet. Want me to create `[firstname-lastname].md` first?" If yes, create a minimal person file from the template in `people_folder/README.md` (frontmatter only, `status: next`, `date` = the day you met, `created` = today). If no, stop.

## Step 2: Get the text

If the user pasted a transcript or voice-note text in the same message, use it. Otherwise ask: "Paste the transcript, or just tell me what happened."

## Step 3: Extract

Pull:
1. **Topic**: 2 to 3 lines on what mattered, not the whole conversation.
2. **Next action**: one concrete next step if any (yours, theirs, or shared). If none, write "-".
3. **Key insight**: anything notable they revealed about context, goals, blockers or interests. If nothing stood out, write "-".

Do not invent. If the text is too thin to extract these, say so.

## Step 4: Save the raw text (only if `daily_notes_folder` is set)

Append to `daily_notes_folder/YYYY-MM-DD.md` (today) under a `## Meetings` heading, creating the file or section if missing:

```markdown
## Meetings

### [Person Name]

[the text, verbatim]
```

If `daily_notes_folder` is blank, skip this step and leave out the transcript link in Step 5.

## Step 5: Hand back the Interactions block

Do not write to the person file yourself. Hand back a ready-to-paste block:

```markdown
### YYYY-MM-DD
- Topic: [summary]
- Next action: [step or "-"]
- Key insight: [reveal or "-"]
```

If Step 4 ran, add a line `- Full transcript: [[YYYY-MM-DD#Meetings]]`.

Then one line: "Paste this under `## Interactions` in [person file], and update `status:` if it changed (for example next to waiting)."

## What this skill never does

- Never sends anything or drafts a follow-up. That's `network-outreach`.
- Never edits an existing person file. The one exception is creating a new file the user approved in Step 1.
- Never invents context that isn't in the text.
