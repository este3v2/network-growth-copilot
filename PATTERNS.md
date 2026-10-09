# Patterns behind the system

What I learned running this on my own network, in the order I would give it to someone starting. These are design decisions, so change them on purpose, not by accident.

## The shape

```
 WHO · REACH · CONTEXT · STAGE · SIGNAL · HISTORY     one file per person
        ▲                 ▲                  ▲
 meeting-capture    network-next     network-outreach     one job each
        └──────── you approve every write, you send every message ────────┘
```

## Patterns

**1. One file per person is the database.**
No tool to log in to, no sync, no schema migration. Claude reads the same files you can. If you stop using Claude tomorrow, you still have your network in plain text.

**2. Stage is the relationship, not a sales funnel.**
Five values: `next`, `waiting`, `engaged`, `later`, `done`. Everything revolves around it. Commercial intent lives in separate optional fields (`commercial_signal`, `commercial_state`, `commercial_trigger`) so a friendly contact is never mistaken for a deal.

**3. History is ground truth only.**
`## Interactions` records what happened. Plans, prep and guesses go in their own section. A guess inside a log stops being a record.

**4. Three actions, not a list.**
Surface three decisions. Show up to 15 records only as a compact scan on a phone. A long list is a dashboard in disguise, and nobody acts on it.

**5. Quality over volume.**
"Nice to connect" contacts decay on purpose. If there is no specific hook and no real reason to reach out, the skill says so and stays quiet.

**6. A message that could go to anyone is a failed message.**
Drafts must use a hook from the person's file. A thin file gets a note, not a made-up shared moment.

**7. The human sends. The human approves writes.**
The agent drafts and ranks. You send, and you paste the log entry back. This is what keeps the files honest: they record what you actually did, not what an agent assumed.

**8. One copilot, three playbooks. Not three agents.**
Capture, rank, draft. Each is a skill with a narrow job. Adding more agents adds hand-offs, and each hand-off is a place to lose context.

**9. Count touches and replies, not contacts.**
The measure is follow-ups sent and replies received. The size of the contact list tells you nothing about whether it works.

**10. Pull, don't push.**
You ask who's next. Nothing nudges you, and nothing runs on a schedule. That is a limit today, and it is also why there is nothing to maintain.

## Known gaps

- No batch replies across several people. Each draft is one person.
- No reminder when a contact goes quiet.
- No calendar block for outreach.
- Updating status and logging a sent message is manual: you paste.

If you build one of these, keep to the same bar capture had to clear: it must remove a step you keep skipping, not add one.
