---
name: network-outreach
description: Drafts a ready-to-send LinkedIn message or email follow-up for one specific person in your contact folder. Use when the user asks to "draft a follow-up for X", "write a linkedin message to X", "draft an email to X", "help me message X", or to act on someone network-next just surfaced. Output is a draft only, it never sends anything. Not for public posts or newsletters, this is strictly 1:1 outreach to a named contact.
---

# network-outreach - drafts only

`network-next` decides *who* and *why*. This skill drafts the actual message once a human has picked someone. It never decides who to contact on its own.

## Step 0: Load config

Find `CONFIG.md` (current folder first, then `~/.claude/network-growth-copilot/CONFIG.md`). If missing, ask the user for its path. Use `people_folder`, `voice_avoid`, `voice_outreach` and `sign_off`.

## Step 1: Identify the person

Match `$ARGUMENTS` against filenames and `title` fields in `people_folder`. A first name or partial name is fine unless it is ambiguous, in which case ask which one.

If no match exists, say so. Do not draft for someone who isn't in the system. Point them at `meeting-capture` to create the file first.

## Step 2: Pull their context

Read the matched file's frontmatter (`where-met`, `city`, `country`, `company`, `date`, `linkedin`, `email`, `notes`) and the `## Interactions` log. This is the only source of the specific hook the message needs.

If both `linkedin` and `email` are blank, say so and stop. There's no channel to draft for. Suggest adding one to the file first.

## Step 3: Pick the channel

- If `$ARGUMENTS` names a channel ("linkedin message", "email"), use it, but only if the file has that field filled. If it doesn't, say so.
- Otherwise: `linkedin` filled and `email` blank means LinkedIn DM. `email` filled and `linkedin` blank means email. Both filled: ask which one, don't guess for a first-touch message.

## Step 4: Load voice and draft

Before writing anything, load in this order:
1. `voice_avoid`: words and phrases you never use.
2. `voice_outreach`: register, channel differences, tone options.

If either file is missing or still contains the template placeholders, say so and ask the user to fill it in first. A draft in a generic voice is worse than no draft.

Draft using the specific hook from Step 2: where you met, what was said, what is relevant right now. If the file doesn't give you anything specific enough, say that plainly instead of inventing a generic opener.

## Step 5: Output

Return three things, in this order:

1. **Three drafts, one per tone option** from `voice_outreach` (the template ships with Warm and short, Direct, Thoughtful), each labelled. Plain text, ready to paste, no markdown inside the message. For email, include a subject line above each body. If the file supports only one tone, say so and give one. Sign off with `sign_off`.
2. **The Interactions log line**, written for the first option as a placeholder. The user swaps in the one they actually send. Dated today, with the message content as the Topic so there is a real record of what was said:
   ```
   ### YYYY-MM-DD
   - Topic: [Channel] follow-up sent - "[the message, or a tight paraphrase if long]"
   - Next action:
   ```
3. **One short reminder:** "Draft only. Send it yourself. Once you do, paste the block above into the person's `## Interactions` section and change `status:` (next to waiting)."

Do not write anything to the file yourself, not even the Interactions line. The point is a record of what was actually sent, which this skill can't know until the human confirms it by pasting it in.

## What this skill never does

- Never sends the message. No API call, no email send. Copy and paste only.
- Never updates the person's file, including `status`.
- Never invents context that isn't in the file. A thin file gets a note saying so, not a made-up shared moment.
- Never uses public-content voices. This is a 1:1 register on purpose.
