---
name: gg
description: Lists the skills of the gg workflow and says which one comes next. Use when the user says "/gg", asks which gg skills exist, or asks how the gg workflow continues.
---

# The gg workflow skills

Every skill of this workflow carries the `gg_` prefix. Print the list
below, in this order — it is the order of a ticket's life.

- `/gg_ticket` — creates a ticket and adds the repos it needs
- `/gg_commit` — proposes a message and commits through `gg do commit`
- `/gg_push` — pushes the ticket branches with `gg do push`
- `/gg_publish` — prepares the release and hands `gg do publish` over to
  the user
- `/gg_cleanup` — removes what the published ticket left behind

A repo may carry more `gg_` skills than these. Look at
`.claude/skills/gg_*` and add what you find there, with the `description`
of its `SKILL.md` as the text.

## Say which skill comes next

Read the state of the current ticket and name the next step:

- No ticket folder yet → `/gg_ticket`
- Uncommitted work → `/gg_commit`
- Committed, not pushed → `/gg_push`
- Pushed and the pull requests are green → `/gg_publish`
- Published → `/gg_cleanup`

The review between push and publish is `gg do review` plus the
`/review-light` skill, not a `gg_` skill of this layer.

## Important

- Only list the skills, never run one of them unasked.
