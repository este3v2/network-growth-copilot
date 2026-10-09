# People: the contact template

One file per person. The filename is `first-last.md`. The three skills read and write this format, so keep the field names exactly as they are.

## Template

```
---
title: First Last
tags: [contact]
created: YYYY-MM-DD
date: YYYY-MM-DD
where-met: event, talk or introduction
city:
country:
company:
linkedin: URL or blank
email: address or blank
status: next
commercial_signal:
commercial_state:
commercial_trigger:
notes: |
  Five lines at most: who they are, what they do, why they matter to your goal.
  Leave blank if you know nothing yet. Do not guess on an ambiguous name.
---

# First Last

## Interactions
### YYYY-MM-DD
- Topic:
- Next action:

## Related
```

## Status: the stage of the relationship

`status` is a **relationship** tracker, not a sales stage.

| Status | Meaning |
|---|---|
| `next` | New contact, or a touch is due and you have not made it yet |
| `waiting` | You sent something and the next move is theirs |
| `engaged` | An active conversation, with something you owe or are working on |
| `later` | Friendly, with no follow-up commitment right now |
| `done` | Finished, or no longer relevant. Kept as history |

When you send a message, move `next` to `waiting`. When they reply, move `waiting` to `engaged`.

## Fields worth knowing

- **`date`** is when you actually met them. It can be earlier than `created`, which is when you filed the record. Never leave it blank, because the table views sort by it. If you don't know the real date, copy `created` and write "date is a proxy" as the first line of `notes`.
- **`city` / `country`** are where they are based, not where you met. That's `where-met`.
- **`company`** is their current employer or venture, not a description.
- **`linkedin` / `email`**: fill only what you really have, never a guess. `network-outreach` uses them to pick the channel.
- **`commercial_signal`** is optional and evidence-based. `buyer-need` means they described a relevant problem. `referral-offer` means they offered an introduction. `partner-interest` means a collaboration was discussed. Blank means "not assessed", not "no value".
- **`commercial_state`** (`watch`, `active`, `parked`) and **`commercial_trigger`** (the evidence that would justify a commercial next step) are separate from `status`. A signal alone is not a deal. Never infer buying intent from a job title or friendliness.

## Interactions vs meeting prep

`## Interactions` holds only what actually happened, one dated entry each. Prep for an upcoming meeting goes in the same file under its own `## Meeting prep, YYYY-MM-DD` section, placed after `## Interactions`. Never mix the two, because a plan inside a log stops being a record. After the meeting, add a new Interactions entry and leave the prep section as it was.

## Optional fields network-next understands

`priority`, `next_action_due`, `snoozed_until`. Leave them out until you need them.
