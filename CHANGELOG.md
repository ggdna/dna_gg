# Changelog

## 0.1.2 - 2026-08-20

### Fixed

- The quick check pipeline ran `npx @tssuite/gg-js`, which npm reports as
  deprecated ("Package no longer supported"). It now runs
  `npx @tssuite/ggwsm`, the package that replaced it.

## 0.1.1 - 2026-08-19

### Changed

- Inherit scripts from `dna_scripts` instead of shipping its own copies.
  Same files, same content — deduplicated across the family.
