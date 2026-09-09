# Example

`dna_gg` is a DNA layer: it ships guides, skills and a `CLAUDE.md` block,
no code. Declare it as a dev dependency and instantiate it once:

```bash
dart pub add dev:dna_gg     # Dart projects
pnpm add -D @ggdna/dna-gg   # TypeScript projects
gg dna init
gg dna build
```

The placed test instantiates the layer on every test run. A gg workspace
gets it automatically from `gg do init workspace`.
