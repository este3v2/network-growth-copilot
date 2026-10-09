---
name: network-setup
description: One-time setup for the Network Growth Copilot. Asks a few questions (goal, name, folder, notes app, voice), then creates the contact folder, CONFIG.md and voice files so the other three skills work. Use right after installing the kit, or when the user says "set up the network copilot", "install network growth copilot", "network setup".
---

# network-setup - guided install

Goal: after about 10 minutes of questions the user can say "who should I contact next?" and get a real answer. You do the file work. They answer questions.

The templates live in `templates/` inside this skill's folder (the base directory announced when this skill loads). Never invent templates. Copy from there.

## Ground rules

- Ask one question at a time, in plain language. Offer a sensible default for each.
- Write only inside the folders the user chooses and `~/.claude/network-growth-copilot/`. Touch nothing else.
- Before overwriting any existing file, show the user and ask.
- Never ask for passwords, API keys or tokens. None are needed.

## Step 1: Questions

Ask in this order:

1. **Goal.** "In one or two sentences, what is this network for? For example: meet founders in logistics who might hire us, or build a speaking pipeline." Use the answer as `goal`.
2. **Name.** "What first name should I sign messages with?" Use as `sign_off`.
3. **Folder.** "Where should the contact folder live?" Default `~/network/people`. If they use Obsidian, suggest a folder inside their vault.
4. **Notes app.** "Do you use Obsidian?" If yes, also copy `people.base` (the board view) and tell them to open the parent folder as a vault. If no, skip it. Plain folders work fully.
5. **Weekly target.** "How many outreach messages do you want to send each week? I'll count confirmed ones. Say 'skip' to not track." Default 2.
6. **Priority doc.** "Do you have a note or file with your current priorities that I should read when ranking? Give a path, or say 'none'."
7. **Daily notes.** "Do you keep dated daily notes? If yes, give the folder and I'll save raw meeting text there. Otherwise 'none'."

## Step 2: Create files

1. Create the contact folder. Copy `templates/people/README.md` into it. Copy `templates/people/people.base` only if the user said yes to Obsidian, and change `file.inFolder("people")` to the real folder name.
2. Ask: "Do you want the fictional sample contact (Ana Garcia) so we can test? I'll tell you when to delete it." If yes, copy `templates/people/ana-garcia.md`.
3. Create `~/.claude/network-growth-copilot/voice/` and copy `templates/voice/avoid.md` and `templates/voice/networking-outreach.md` there.
4. Create `~/.claude/network-growth-copilot/CONFIG.md` from `templates/CONFIG.md`, filled with the user's answers and **absolute paths**. Set `voice_avoid` and `voice_outreach` to the files from step 3.

## Step 3: Voice interview

Say: "Drafts only sound like you if I know how you write. Four quick questions."

1. "Give me 5 to 10 words or phrases you would never write in a message." Write them into `voice/avoid.md` under the list, removing the example lines.
2. "Paste two or three real messages you sent that sounded like you." Put them under "Two or three messages that sounded like me" in `voice/networking-outreach.md`.
3. "How do you write to someone you just met? One sentence." Put it under "My own register".
4. "Anything different between LinkedIn and email for you?" Add to "Channel differences".

If the user wants to skip, say that drafting will refuse until the voice files are filled in, and move on.

## Step 4: Import contacts (optional)

Ask: "Want to add the first people now? Paste names, where you met, and company. One per line is fine." For each, create a person file from the template in `people/README.md`: `status: next`, `date` = the day they met (ask if unknown, otherwise use today and note "date is a proxy" as the first line of `notes`), leave `linkedin` and `email` blank unless given. Never guess either.

## Step 5: Finish

Show a short summary: what was created and where. Then give three things to try:

- "Who should I contact next?"
- "Draft a LinkedIn message to [a name you added]."
- "I just met [name] at [event]. [Describe what happened.]"

Remind them once: nothing is ever sent for them, and every change to a person file needs their approval.

## What this skill never does

- Never sends anything or contacts anyone.
- Never writes outside the chosen folders and `~/.claude/network-growth-copilot/`.
- Never overwrites an existing file without asking.
- Never guesses an email or LinkedIn address.
