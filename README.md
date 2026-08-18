# Comedian Voices

Agent skills for writing in the voice of famous stand-up comedians.

Each skill in this repo codifies the **structural moves**, **rhetorical patterns**, and **anti-patterns** extracted from close analysis of a comedian's published work. Load a skill and an agent can produce writing that reads like that comedian — not by imitation of surface jokes, but by reproducing the underlying machinery of how they build, pace, and land material.

## What a skill contains

Every comedian skill is a `SKILL.md` that documents:

- **Structural moves** — how the comedian opens, builds, escalates, and lands bits; their set architecture and callbacks.
- **Rhetorical patterns** — recurring sentence shapes, rhythm, repetition, misdirection, and word choice.
- **Anti-patterns** — things the comedian *never* does, which are as defining as what they do.
- **Voice fingerprint** — a compact, loadable summary an agent can apply immediately.

## Usage

Skills are written for agent frameworks that load `SKILL.md` files (Claude Code, Copilot, Codex, etc.). Point your agent at the relevant skill folder, or copy the `SKILL.md` into your agent's skill directory.

## Structure

```
comedian-voices/
├── README.md
└── skills/
    └── <comedian-slug>/
        ├── SKILL.md
        └── references/   # optional: source notes, excerpts, analysis
```

## License

MIT — see [LICENSE](LICENSE).