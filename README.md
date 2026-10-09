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
| [Visual guide](https://este3v2.github.io/network-growth-copilot/) | Install and usage with prompts to try |
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

## Not yet

- **Companies:** the unit is a person. A company is a field on each contact, and company maps live in separate notes. No company records or account view.
- No batch replies, no reminders when a contact goes quiet, no calendar blocks.
- Status and log updates are pasted by you. No importer for LinkedIn or CRM exports.
- Notion and other stores are untested. One person's network only, not a team tool.

The full table, with what's by design, is in the [visual guide](https://este3v2.github.io/network-growth-copilot/#). Want one of these? [Open an issue](https://github.com/este3v2/network-growth-copilot/issues) or send a pull request. See also [PATTERNS.md](PATTERNS.md).

## Want it installed for you?

Reply to the welcome email.

## Licence

MIT. See [LICENSE](LICENSE).
