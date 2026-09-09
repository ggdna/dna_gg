<!--
@license
Copyright (c) dnaCopyrightHolder

Use of this source code is governed by terms that can be
found in the LICENSE file in the root of this package.
-->

# Development guide for AIs

## Ask the developer for the ticket infos

- Ask for the ticket ID
- Ask for the ticket title
- Ask for the ticket description

## Replace in this document

- Replace `~/dev/` by the workspace directory from the memory
- Ask for the workspace directory if none is known
- Replace `dnaJiraPrefix-145` by the ticket ID you asked for
- Replace `Fix issue abc` by the ticket title you asked for

## Create a ticket

```bash
cd ~/dev/ # workspace
gg do create ticket dnaJiraPrefix-145 -m"Fix issue abc"
cd tickets/dnaJiraPrefix-145
```

## Choose the project management repo

Every ticket belongs to a project management (PM) repo. It holds the plans,
decisions and blog posts of a project, but no code.

Look at the `index.jsonc` of each repo in .ocean and find the PM repo the
ticket belongs to: its summary or domain talks about project management or
planning, not about code. If one fits, propose it to the user. If none fits,
ask the user which repo to use, or whether to create a new PM repo.

After the user's confirmation, add the PM repo to the ticket **before** any
other repo:

```bash
gg do add pm_repo
```

## Add git repositories

Look at the `index.jsonc` of each repo in .ocean and decide which repos need to
be added to the ticket.
Make a plan for how you roughly want to implement the ticket.
If certain parts of the implementation belong to a domain that does not yet
exist in the .ocean folder, consider creating a new repository.
Ask the user about this. Also explain to the user what you roughly want to
change in which repo to implement the ticket and let them confirm that the
corresponding repos are added to the ticket.

If the ticket is only planned (see below), the PM repo may be the only repo
of the ticket.

After the user's confirmation, add the repos to the ticket:

```bash
gg do add repo1 repo2
```

## Open the workspace in Vscode

```bash
gg do code
```

## Plan (optional)

Ask the user whether the ticket is planned before it is implemented.

If yes, write the plan into the PM repo, following the guides of the PM repo:
the goal, the affected repos, the rough steps and open questions. Let the user
review the plan and revise it until they confirm it.

## Implement (optional)

Ask the user whether the ticket is implemented now, or whether it is only
planned. Some tickets are only planned; the implementation follows in a later
ticket.

- Implement: implement your features based on the guides
- Plan only: skip this step. The following steps then apply to the PM repo
  only.

## Commit

```bash
gg do commit
```

## Push

```bash
gg do push
```

## Review

Let the user confirm that the review phase is started.

```bash
gg do review
```

gg creates pull requests for each repo and prints the URLs to the
terminal.

Afterwards load the review-light skill and execute it.

## Publish

- Create a blog post for the current ticket
- Update the index.jsonc and README.md
- Create the configuration for gg do publish
- If the ticket was only planned, publish the PM repo only

Ask the user to run the following command **manually**:

```bash
gg do publish
```

gg triggers the pull request merge and publishes the changes to the
registry. Finally the version tag is created and pushed.
