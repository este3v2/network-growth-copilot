# Install

You need Claude Code. No API keys, no accounts. About 15 minutes, most of it answering questions.

## Option 1: plugin (recommended)

In Claude Code, run these two commands:

```
/plugin marketplace add este3v2/network-growth-copilot
/plugin install network-growth-copilot@network-growth-copilot
```

Then say:

> Set up the network growth copilot

Claude asks you a few questions, one at a time, and builds everything:

| It asks | It does |
|---|---|
| What is this network for? | Writes your goal into `CONFIG.md` |
| What name do you sign with? | Sets your sign-off |
| Where should the contact folder live? | Creates it, with the template |
| Do you use Obsidian? | Adds the board view, or skips it |
| Weekly outreach target? | Sets the weekly count, or turns it off |
| How do you write to someone you just met? | Builds your voice files from your answers |
| Who have you met recently? | Creates the first contact files |

Updates later: `/plugin marketplace update network-growth-copilot`.

## Option 2: clone and copy

```bash
git clone https://github.com/este3v2/network-growth-copilot.git
mkdir -p ~/.claude/skills
cp -R network-growth-copilot/skills/* ~/.claude/skills/
```

Then open Claude Code and say "Set up the network growth copilot". It does the same questions as the plugin.

Codex users: copy the folders under `skills/` into your Codex skills folder instead.

## Test it

1. "Who should I contact next?" should rank the sample contact, or yours.
2. "Draft a LinkedIn message to Ana Garcia." should return three drafts (if you kept the sample).
3. "I just met Ana at the Data Summit. We talked about her reporting backlog." should hand back an entry to paste.

Delete `ana-garcia.md` when you have your own people.

## Your first week

1. Add 20 people you have already met.
2. Ask who to contact next, twice.
3. Draft and send five follow-ups yourself. Paste each log line back.
4. Count follow-ups sent and replies received. That is the number to watch.

## Voice notes

Claude Code doesn't take audio. Dictate on your phone (or use a voice-memo transcript) and paste the text. A Telegram bot can automate capture, but it's an optional extra and not part of this kit.

## Other note apps

The skills read markdown files with frontmatter from any folder, so Obsidian is optional. It only adds the board view. Notion would need a Notion connector in Claude Code and hasn't been tested with this kit.

## Make it yours

All of it is plain text under `~/.claude/network-growth-copilot/`, or in your contact folder.

| To change | Edit |
|---|---|
| Goal, name, weekly target, folders | `CONFIG.md` |
| Words you never use | `voice/avoid.md` |
| Tone options, channel rules | `voice/networking-outreach.md` |
| Fields on a contact | `README.md` in your contact folder (keep the existing names) |
| Redo the questions | Say "Set up the network growth copilot" again. It asks before overwriting |

Keep the five status values (`next`, `waiting`, `engaged`, `later`, `done`). The skills rely on them.

## Remove it

`/plugin uninstall network-growth-copilot`. Your contact files stay where they are.

## If something breaks

First check: your `CONFIG.md` (at `~/.claude/network-growth-copilot/CONFIG.md`) points at a folder that exists, and the voice files are filled in, not template text. Nearly everything else is one of those two. Run the setup again if unsure. It asks before overwriting anything.
