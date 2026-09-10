---
name: ticket
description: Creates a gg ticket and adds the repos it needs. Use when the user says "/ticket", "new ticket", "fix bug X", or "implement feature Y".
---

# Create a ticket

All `gg do` commands run inside the workspace. Ask for the workspace
directory if none is known.

## 1. Ask for the ticket data

- Ticket ID, e.g. `GGS-145`
- Title, one imperative line, e.g. `Fix issue abc`

## 2. Create the ticket

```bash
cd ~/dev/ # workspace
gg do create ticket GGS-145 -m"Fix issue abc"
cd tickets/GGS-145
```

## 3. Choose the project management repo

Every ticket belongs to a project management (PM) repo: plans, decisions and
blog posts of a project, no code. Read the `index.md` of the repos in
`.ocean` and propose the PM repo the ticket belongs to. If none fits, ask
which repo to use or whether to create one.

After the confirmation, add it **before** any other repo:

```bash
gg do add pm_repo
```

Read `doc/guides/pm-repo-guide.md` of the PM repo if it exists: it says how
the PM repo is structured and how planning works there.

## 4. Choose the code repos

Read the `index.md` of the candidate repos in `.ocean`. Tell the user which
repos the ticket needs and what you roughly want to change in each one. If a
part belongs to a domain that has no repo yet, say so and ask whether to
create one. A ticket that is only planned may need no code repo at all.

After the confirmation:

```bash
gg do add repo1 repo2
```

## 5. Open the workspace

```bash
gg do code
```

## 6. Plan or implement

Ask the user whether the ticket is planned first. If yes, write the plan into
the PM repo as its `pm-repo-guide.md` describes (or as its other guides do)
and let the user confirm it. Then ask whether the ticket is
implemented now or only planned — in the latter case the ticket ends with
the PM repo alone.

## Important

- Never add repos without confirmation. Rather too few than too many — more
  can be added later.
- Do not start the implementation unasked.
