# Contributing a Comedian Voice

This repo is **content-only** — it ships curated comedian `SKILL.md` skills. New skills are generated with the [voiceprint](https://github.com/arndvs/voiceprint) generator, then submitted here as a PR.

## Workflow

1. **Gather source material** — transcripts, books, interviews. Keep it local; never commit full works (see fair-use below).
2. **Generate the skill** with [voiceprint](https://github.com/arndvs/voiceprint):
   ```bash
   # in a voiceprint checkout
   python -m scripts.transcribe source/<slug>/raw --output-dir source/<slug>/transcripts   # optional
   python -m scripts.run_pipeline --config config.example.json --item <slug>
   # agent-driven analyze step, then:
   python -m scripts.run_pipeline --config config.example.json --item <slug> --only assemble
   ```
3. **Validate the output** against `skills/schema.md` (the contract): two files per skill, `skill_version` frontmatter, all sections present.
4. **Copy `skills/<slug>/` into this repo** and open a PR.

## Contribution checklist

- [ ] Folder `skills/<comedian-slug>/` with `SKILL.md` + `<slug>-style-analysis.md`
- [ ] `skill_version: 1` + `type:` frontmatter in both files
- [ ] Both `SKILL.md` as the loadable skill **and** the analysis as the depth doc
- [ ] Short attributed excerpts only — no reproduced full routines
- [ ] Source provenance in the analysis's excerpt index

## Copyright (fair use)

This repo ships **analysis and short quotes**, never full works.

- ❌ No full books, full specials, full transcripts, full albums
- ✅ Scattered short attributed excerpts (a few lines) that evidence a pattern
- ✅ If a reviewer could reconstruct a full routine from this repo, it's a violation

Generated output is AI-written **pastiche** — clearly labeled, never represented as the comedian's actual work.

## Commit convention

```
feat(skills): add <comedian-slug> voice skill
```
