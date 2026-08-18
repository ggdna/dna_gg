# dna_gg

The DNA layer for the `gg` CLI workflow: ticket, commit, push, review,
publish.

## Content

- `dna/doc/guides/develop-guide.md`,
  `develop-without-ai-guide.md`, `for-ai/ai-dev-guide.md` — the ticket
  driven workflow, with and without an AI
- `dna/doc/guides/install-guide/install-gg-guide.md`,
  `install-gg-workspace-guide.md` — install `gg` and set up a workspace
- `dna/doc/guides/create-repo-guide.md` — create a new repo and its
  branch rules
- `dna/scripts/` — the node scripts the guides call
  (`setup-github-repo.js`, `rename-class.js`, `wait-for-pr.js`,
  `delete-feature-branch.js`)
- `dna/dot-github/workflows/quick_check.yaml` — the quick check pipeline

## Usage

Declare it as a dev-dependency and initialize once:

```bash
pnpm add -D @ggdna/dna-gg   # TypeScript projects
dart pub add dev:dna_gg    # Dart projects
helix init
```

The placed test instantiates and verifies the DNA on every test run.

This layer inherits from
[dna_install](https://github.com/ggdna/dna_install) and
[dna_index](https://github.com/ggdna/dna_index); both come along as regular
dependencies. It extends the install overview of `dna_install`: a
`dna/doc/guides/install-guide.overrides.md` replaces the tagged section
`## [@tooling] Tooling`, adds `Install gg` and appends the `## Workspace`
section pointing at the gg workspace guide.

The parents are not on pub.dev or npm yet — until they are, a
`pubspec_overrides.yaml` resolves them from the sibling folders of the
workspace, and this package cannot be published.

## Development

This repo has `role: "dna"` in `dna/_dna.json`: the `dna/` folder is
authored by hand, never generated. The repo instantiates its own DNA — run
`dart test` after changes; commit first (a file the DNA would overwrite
must not carry uncommitted work).
