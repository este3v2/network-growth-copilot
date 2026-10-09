# CONFIG

The only file you edit to make the three skills yours. Every skill reads it first.

Keep it in the folder where you run Claude Code, or in `~/.claude/network-growth-copilot/CONFIG.md`. If a skill can't find it, it asks you for the path.

```yaml
# Where your contact files live (one .md file per person)
people_folder: ./people

# Your voice files. Drafts follow these. See voice/ for the templates.
voice_avoid: ./voice/avoid.md
voice_outreach: ./voice/networking-outreach.md

# How you sign messages (first name only is a good default)
sign_off: YourName

# The one goal this network serves. One or two sentences. network-next uses it to break ties.
goal: "Meet and keep in touch with people in [your field] so that [what you want from it]."

# Optional. A file with your current priorities (a NEXT.md, a plan, a note). Leave blank if you have none.
priority_doc:

# Optional. Confirmed outreach touches per Monday-to-Sunday week. Leave blank to skip the weekly count.
weekly_touch_target: 2

# Optional. If set, meeting-capture also saves the raw transcript to a dated note here (YYYY-MM-DD.md). Leave blank to skip.
daily_notes_folder:
```

## Notes

- Paths can be absolute or relative to the folder you run Claude Code from.
- `goal` matters more than it looks. Without it, ranking falls back to dates and evidence only.
- Nothing here is a secret. No API keys are needed anywhere in this kit.
