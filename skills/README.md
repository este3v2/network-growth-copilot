# The skills

Three do the work. A fourth, `network-setup`, runs once: it asks a few questions and builds your folder, config and voice files.

Each skill does one job. They share one data format (the person file in `people/`) and one config file (`CONFIG.md`). None of them sends anything.

```
 you talk to someone
        │
        ▼
 meeting-capture ──► person file (you paste the entry)
                           │
                           ▼
 network-next  ──► "who's next, why now"   (read-only)
                           │ you pick one person
                           ▼
 network-outreach ──► three drafts + a log line   (you send, you paste the log)
```

## 1. meeting-capture

**Job:** turn a conversation into a record on that person's file.

**You say:** `meeting-capture Ana Garcia` and paste a transcript, or just describe what happened.

**It does:** extracts the topic, the next action and the key insight. Hands you a block to paste under `## Interactions`. Creates the person file first if it doesn't exist. If `daily_notes_folder` is set, it also saves the raw text there.

**Example result:**
```
### 2026-10-02
- Topic: Met after her panel. Reporting backlog on her team.
- Next action: Send the case study this week, suggest a 30-minute call.
- Key insight: Her team rebuilds the same weekly report by hand.
```

**Never:** edits an existing person file, sends anything, or invents context.

## 2. network-next

**Job:** say which relationships deserve attention now, and why.

**You say:** `network-next`, or `network-next phone overview`.

**It does:** reads your `goal` and every person's stage and history. Returns at most three actions with the evidence for each, or a 15-line overview you can scan on your phone. Reports confirmed outreach touches this week if you set a target.

**Example result:**
```
Ana Garcia - Follow up - she asked for the case study, nothing sent yet - 2 Oct - high confidence
```

**Never:** drafts, sends, edits a file or changes a status. It only reads.

## 3. network-outreach

**Job:** draft one message to one person.

**You say:** `network-outreach Ana Garcia linkedin`.

**It does:** reads her file and your voice files, then returns three drafts in three tones, plus a log line for you to paste after sending. Picks LinkedIn or email from the fields you've filled in.

**Never:** sends a message, edits the file, or writes a generic message when the file has nothing specific to say.

## Setup helper: network-setup

**You say:** "Set up the network growth copilot".

**It does:** asks about your goal, name, folder, notes app, weekly target and voice, then creates the files from `network-setup/templates/`. Asks before overwriting anything.

## The rule behind all three

You approve every change to a person file, and you send every message. The files stay the one true record of what actually happened.

## Full rules

Each skill's `SKILL.md` has the complete rules: ranking order, action labels, boundaries and edge cases.
