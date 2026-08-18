# Adding a New Comedian

This is the workflow for turning raw source material (books, stand-up special transcripts, interviews) into a loadable comedian voice skill. The pipeline in `pipeline/` automates the deterministic parts; the analysis itself is agent-driven.

## The pipeline at a glance

```
preflight → scaffold → ingest → transcribe → extract → analyze (agent) → assemble
```

- **preflight** — config/environment checks
- **scaffold** — copies `skills/_template/` to `skills/<slug>/`
- **ingest** — lists raw source files (from `source/<slug>/`)
- **transcribe** — media in `source/<slug>/raw/` → text in `source/<slug>/transcripts/` (skips if none)
- **extract** — samples raw text → short excerpts; flags copyright-risk files
- **analyze** — **you**: run the writeprint generator + fill in the analysis and SKILL.md
- **assemble** — replaces `{{placeholders}}`, validates output

See `pipeline/SKILL.md` for full details.

## Steps

### 1. Drop your source material

Put the comedian's raw material in `source/<slug>/` (e.g. `source/jerry-seinfield/`):

- **Media** (video/audio of specials): `source/<slug>/raw/` — the pipeline transcribes these.
- **Text** (books, existing transcripts, interviews): directly in `source/<slug>/`.

`source/` is gitignored, so it stays local — only the distilled skill gets committed.

**Copyright:** raw books/transcripts must NOT be committed. See `pipeline/references/fair-use.md`. The extractor flags full works and refuses to proceed until you provide short curated excerpts.

### 2. Run the deterministic phases

```bash
python -m pipeline.scripts.preflight --config pipeline/config.example.json
python -m pipeline.scripts.run_pipeline --config pipeline/config.example.json --item <slug>
```

This scaffolds the folder, ingests sources, transcribes media (if any), and extracts short excerpts (flagged for copyright). If a source is flagged, replace it with curated short excerpts and rerun.

To transcribe media standalone (without the full pipeline), see `pipeline/scripts/INSTALL.md`:

```bash
python -m pipeline.scripts.transcribe source/<slug>/raw --output-dir source/<slug>/transcripts
```

### 3. Analyze (the agent step)

Run the writeprint generator (`writeprint/writeprint-generator.md`) against the extracted excerpts. Fill in the analysis file and SKILL.md sections — voice, architecture, mechanics, rhetorical moves, fingerprints, themes, anti-patterns, provenance.

### 4. Assemble & validate

```bash
python -m pipeline.scripts.run_pipeline --config pipeline/config.example.json --item <slug> --only assemble
```

This replaces remaining `{{placeholders}}` and fails if any unfilled tokens remain. Then verify:

- [ ] Voice section reads like the comedian (register + not-X contrasts)
- [ ] Comedic Architecture (moves with micro-excerpts)
- [ ] Sentence-Level Mechanics
- [ ] Rhetorical Moves
- [ ] Linguistic Fingerprints
- [ ] Thematic Obsessions
- [ ] Anti-patterns (What X Never Does)
- [ ] Application Sequence
- [ ] Provenance (sources with years)
- [ ] References / excerpt index present
- [ ] No `{{placeholder}}` tokens remain

### 5. Commit

One logical change per commit, conventional message:

```
feat(skills): add <comedian-slug> voice skill
```

