---
name: network-next
description: "Rank the next relationship actions or show a compact 15-record phone overview from your contact folder (one markdown file per person). Use for network reviews, follow-up priorities, 'who should I contact', 'network next', and phone overviews. Read-only: never sends messages or changes contact files."
---

# Network Next

Read the contact folder and answer: **what relationship action is worth attention now, and what evidence supports it?**

Keep the skill read-only and on demand. It can recommend or summarise. It never drafts outreach, sends messages, changes status, or writes contact history.

## Step 0: Load config

Find `CONFIG.md` (current folder first, then `~/.claude/network-growth-copilot/CONFIG.md`). If missing, ask the user for its path. Use `people_folder`, `goal`, `priority_doc` and `weekly_touch_target` from it.

## Load current intent

Before ranking, read:

1. `goal` from CONFIG.md.
2. `priority_doc`, if set.
3. Every `.md` file in `people_folder` except `README.md` and non-person records.

Use the goal to break ties. A dated commitment still outranks a vague, strategically interesting contact.

## Read relationship evidence

For each person, use frontmatter plus the `## Interactions` log.

- Treat `date` as the first meeting date, never as last-contact evidence when a later interaction exists.
- Derive `last_interaction` from the latest dated interaction heading.
- Reconcile the latest non-empty `Next action` against later entries. Later evidence can complete or replace an older action.
- Treat `priority` as optional. Missing priority is neutral.
- Recognise optional `next_action_due` and `snoozed_until` when present.
- A `not enriched` note lowers context confidence. It does not suppress known interaction evidence.
- Preserve uncertainty. If ownership, timing, or current state is unclear, surface a clarification action rather than inventing a deadline.

Exclude `done` records unless the user explicitly asks for history. Exclude `later` records unless a dated event or explicit review date has arrived. Consider `next`, `engaged`, and `waiting` records.

## Rank actions

Rank in this order:

1. Due or overdue commitments owned by the user.
2. Upcoming meetings or events that require preparation.
3. `engaged` relationships with an unresolved action owned by the user.
4. `waiting` relationships whose explicit review date has arrived, respecting later replies and snooze dates.
5. Fresh `next` relationships with a specific action and useful context.
6. A keep-in-touch candidate only when there is a real reason to reconnect or something relevant to share.

Within a tier, prefer current goal fit, stronger evidence, higher declared priority, relationship leverage, and more recent meaningful interaction. Do not use contact age, company prestige, or missing enrichment as a substitute for an actual reason to act.

Use only these action labels:

`Connect` · `Follow up` · `Invite` · `Share useful asset` · `Prepare for meeting` · `Research / enrich` · `Advance opportunity` · `Clarify current action`

## Count the weekly measure (only if `weekly_touch_target` is set)

Count only interaction entries that clearly confirm a completed outreach touch in the current local Monday-to-Sunday week: a message sent, call made, meeting held, reply sent, or introduction completed. Do not count drafts, recommendations, planned actions, imports, enrichment, or ambiguous notes.

Report `Confirmed touches this week: X/target`. If evidence is ambiguous, state the confirmed count and the number needing review rather than guessing. If the target is blank, skip this section.

## Choose the output mode

### Action mode (default)

Return at most three strong actions. Use four only when the fourth has comparable urgency and evidence.

For each person, give:

`Name - action - why now - evidence date - confidence`

Keep each item to one or two short lines. End with:

- confirmed touches this week against the target (if set);
- number surfaced against the total open pool;
- one warning if stale, conflicting, or missing evidence materially affected the ranking.

Do not pad the list.

### Phone overview mode

Use this mode when the user asks for `phone overview`, `show 15`, `compact overview`, or an equivalent scan.

Return up to 15 ranked open records. This is an overview, not 15 recommendations. Put the records in one fenced code block so phone clients render a compact monospace font.

Use one line per record:

`01 Name · ENG/NEXT/WAIT · Action · DD Mon`

The date is the evidence date used for ranking. Keep names and actions short enough to avoid wrapping. After the code block, report:

`15 of N open records shown · confirmed touches X/target`

If fewer than 15 records have reliable evidence, show fewer and say why. Do not turn the overview into a dashboard or add a separate database.

## Boundaries

- Never send or draft a message. Use `network-outreach` only after the user selects one person.
- Never edit a contact, interaction, due date, or status.
- Never treat a suggestion as a completed touch.
- Never touch records outside `people_folder`.
- Never run on a schedule or create autonomous outreach.
- Never expose email addresses, phone numbers, transcript text, or sensitive personal details in an overview unless the user explicitly asks.
