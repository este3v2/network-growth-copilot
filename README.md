# Network Growth Copilot: starter kit

You meet people faster than you can follow up with them. This is a small system for that: it tells you who to contact next, drafts the message in your voice, and leaves the sending to you.

```
 CAPTURE ─────► RANK ─────► DRAFT ─────► YOU SEND
 meeting-       network-    network-     always you,
 capture        next        outreach     never the agent
```

One markdown file per person. Three Claude Code skills. No CRM, no dashboard, no new tool to buy.

## Install

```
/plugin marketplace add este3v2/network-growth-copilot
/plugin install network-growth-copilot@network-growth-copilot
```

Then say: **Set up the network growth copilot**. It asks a few questions and builds your folder, config and voice files. Details and the manual route: [INSTALL.md](INSTALL.md).

## What's here

| Path | What it is |
|---|---|
| [INSTALL.md](INSTALL.md) | Install and first week |
| [skills/](skills/README.md) | The three skills plus the setup helper, explained |
| [skills/network-setup/templates/](skills/network-setup/templates) | Contact template, stage rules, board view, sample contact, voice files |
| [docs/index.html](docs/index.html) | Visual guide with prompts to try |
| [PATTERNS.md](PATTERNS.md) | The design decisions behind it |

## The data

```
 WHO      first name · surname · company · city · country
 REACH    linkedin · email
 CONTEXT  where-met · date met · notes
 STAGE    status: next · waiting · engaged · later · done
 SIGNAL   buyer-need · referral-offer · partner-interest   (optional)
 HISTORY  ## Interactions (dated) · ## Meeting prep
```

## Rules it keeps

- You send every message. Nothing goes out automatically.
- You approve every change to a person file.
- Drafts need a real hook from that person's file, or the skill says it has nothing to say.

## Needs

Claude Code or Codex, and a folder for notes. Obsidian is optional and adds a board view.

## What it doesn't do yet

No batch replies, no reminders when a contact goes quiet, no calendar blocks. See [PATTERNS.md](PATTERNS.md).

## Want it installed for you?

Reply to the welcome email.

## Licence

MIT. See [LICENSE](LICENSE).
