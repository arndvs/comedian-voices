# Skill Output Contract v1

Every skill in this repo (and every skill emitted by the [voiceprint](https://github.com/arndvs/voiceprint) generator) follows this contract.

## Layout

```
skills/<slug>/
├── SKILL.md              # the loadable skill
└── <slug>-style-analysis.md  # the deep source analysis
```

## Frontmatter (both files)

```yaml
---
skill_version: 1
type: <violence-type>   # e.g. comedian, author, personal
name: <slug>
---
```

## Required sections (SKILL.md)

- **The Voice** — baseline register + "not X" contrasts
- **Comedic / writing architecture** — structural moves with micro-excerpts
- **Sentence-level mechanics**
- **Rhetorical moves**
- **Linguistic fingerprints**
- **Thematic obsessions**
- **Anti-patterns** ("What X Never Does")
- **Application sequence** — how to open, build, land
- **Provenance** — sources with years

## Rules

- Every quote is attributed (source, year, medium)
- Quotes are SHORT and evidence a pattern — never a full bit
- `skill_version: 1` is the contract version. Bump on breaking output changes in `voiceprint`.
