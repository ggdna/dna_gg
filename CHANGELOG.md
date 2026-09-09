# Changelog

## Unreleased

### Added

- `dna/CLAUDE.md` — points the agent to the ai-dev-guide and the skills;
helix 1.6 writes it into the managed block of the consumer's `CLAUDE.md`.

### Changed

- `ai-dev-guide` and `/ticket`: choose the project management repo right
after creating the ticket and add it first, plan the ticket in the PM repo
optionally, and make the implementation optional — a ticket may end with
the PM repo alone.
- `install-gg-workspace-guide`: `gg do init workspace` instantiates
`dna_gg` in the workspace folder.

## 0.2.0 - 2026-09-07

## 0.1.2 - 2026-08-20

### Fixed

- The quick check pipeline ran `npx @tssuite/gg-js`, which npm reports as
deprecated ("Package no longer supported"). It now runs
`npx @tssuite/ggwsm`, the package that replaced it.

## 0.1.1 - 2026-08-19

### Changed

- Inherit scripts from `dna_scripts` instead of shipping its own copies.
Same files, same content — deduplicated across the family.
