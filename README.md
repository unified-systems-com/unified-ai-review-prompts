# Unified AI Review — Prompt Packs

Prompt packs for [Unified AI Review](https://github.com/unified-systems-com/unified-ai-review).
The machinery repo carries no prompt content; this repo carries no machinery. Consumers pin this
repo by full commit SHA in their shim, so a prompt change is a deliberate, reviewable pin bump —
and a PR under review can never edit the instructions being applied to it.

## Layout contract

```
packs/<pack-name>/prompt.md    # the system prompt for that pack
packs/<pack-name>/LICENSE      # optional: overrides the repo license for that pack
```

That is the whole contract. The machinery reads `packs/<pack>/prompt.md`; everything else in a
pack directory is documentation for humans.

## Packs

| Pack | What it reviews for | License |
| --- | --- | --- |
| `security` | Smuggled malicious changes first, hygiene second: cover-story mismatch, weakened controls, CI/build tooling, dependencies, reviewer config, unreviewable content, auth/data paths | Apache-2.0 (repo default) |

Security is the first pack, not the last — code-quality, best-practices, and standards packs
ride the same mechanism.

## Bring your own

Fork this repo (or make your own with the same layout), point your shim's `prompts-repo` /
`prompts-ref` at it, and the machinery applies your prompts instead. You inherit a pack's
license only if you build on that pack's files.

## Licensing

The repository default is **Apache-2.0** (see `LICENSE`). Individual packs MAY carry their own
`LICENSE` file, which governs that pack's contents — this is deliberate: it lets packs derived
from differently-licensed methodology (e.g. CC BY-SA material, with attribution) live here
without relicensing anything else. Third-party-derived material enters only as a vendored
snapshot reviewed at a pinned commit — never fetched from a third party at build or run time.
