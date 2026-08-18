# Comedian Voices

Agent **skills** for writing in the voice of famous stand-up comedians.

Each skill codifies the **structural moves**, **rhetorical patterns**, **anti-patterns**, and **voice** extracted from close analysis of a comedian's published work. Load a skill and an agent can produce writing that reads like that comedian — not by imitation of surface jokes, but by reproducing the underlying machinery of how they build, pace, and land material.

This repo is **content-only**: it ships curated `SKILL.md` skills. The tooling that generates and analyses them lives in the companion repository.

> **Generator** — for the pipeline that turns raw source material (books, transcripts, your own writing) into these skills, see [arndvs/voiceprint](https://github.com/arndvs/voiceprint). Clone `voiceprint`, drop raw material in `source/`, and it emits new `skills/` you can PR back here.

## What a skill contains

Every comedian skill is a two-part pair:

- **`<slug>-style-analysis.md`** — the deep source analysis: voice & tone, comedic architecture, sentence-level mechanics, rhetorical moves, linguistic fingerprints, thematic obsessions, anti-patterns, excerpt index.
- **`SKILL.md`** — the concise, loadable version agents apply immediately.

## Usage

Point your agent at the relevant skill folder, or copy the `SKILL.md` into your agent's skill directory.

## Adding a new comedian

See [CONTRIBUTING.md](CONTRIBUTING.md). In short: use the [voiceprint](https://github.com/arndvs/voiceprint) generator to produce a skill from source material, then submit it here as a PR.

## Structure

```
comedian-voices/
├── skills/                 # curated comedian skills (one folder per comedian)
│   ├── <comedian-slug>/
│   │   ├── SKILL.md
│   │   └── <comedian-slug>-style-analysis.md
│   └── schema.md           # the skill output contract (skill_version, two-file shape)
└── LICENSE
```

## License

MIT — see [LICENSE](LICENSE).
