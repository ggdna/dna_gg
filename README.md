# dna_gg

The DNA layer for the `gg` CLI workflow: ticket, commit, push, review,
publish.

## Guides

- `dna/doc/guides/develop-guide.md`,
  `dna/doc/guides/develop-without-ai-guide.md` — the ticket driven
  workflow, with and without an AI
- `dna/doc/guides/for-ai/ai-dev-guide.md` — the same workflow as
  instructions for an agent
- `dna/doc/guides/install-guide/install-gg-guide.md`,
  `dna/doc/guides/install-guide/install-gg-workspace-guide.md` — install
  `gg` and set up a workspace

## Skills

- `/ticket` — creates a ticket and adds the repos it needs
- `/commit` — proposes a message and commits through `gg do commit`
- `/push` — pushes the ticket branches
- `/publish` — releases the ticket
- `/cleanup` — removes what the ticket left behind

## Configuration

- `dna/dot-github/workflows/quick_check.yaml` — the quick check pipeline
  every pull request has to pass

## Layers

Builds on [dna_install](https://github.com/ggdna/dna_install) for the
install overview, [dna_index](https://github.com/ggdna/dna_index) for the
repo index every gg repo keeps, and
[dna_scripts](https://github.com/ggdna/dna_scripts) for
`setup-github-repo.js`, `rename-class.js`, `wait-for-pr.js` and
`delete-feature-branch.js`, which the guides above call.

It extends the `@tooling` section of the install overview through
`dna/doc/guides/install-guide.overrides.md`: it adds `Install gg` and
appends the `Workspace` section.

## Variables

- `dnaCopyrightHolder` — the name in the license header of every file
- `dnaCompany`, `dnaGitOrg`, `dnaGitOrgUrl` — the organization repos are
  created in
- `dnaJiraPrefix` — the prefix of a ticket id
- `dnaGitQuickCheckPipelineName` — the name the branch rules require
- `dnaPubDevPublisher` — the pub.dev publisher packages are transferred to

## Usage

Declare it as a dev-dependency and initialize once:

```bash
pnpm add -D @ggdna/dna-gg   # TypeScript projects
dart pub add dev:dna_gg     # Dart projects
helix init
```

The placed test instantiates and verifies the DNA on every test run.

## Development

The `dna/` folder is hand-authored source and is never generated. The repo
instantiates its own DNA — run `dart test` after changes; commit first, a
file the DNA would overwrite must not carry uncommitted work.
