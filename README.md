# ux-automation

A collection of [Claude Agent Skills](https://code.claude.com/docs/en/skills) for UX/product work — audits, reviews, and automation that plug into Claude Code, Claude Desktop/Web, or any Agent-Skills-compatible client.

## Skills in this repo

| Skill | Description |
|---|---|
| [`ux-analyze-by-hani`](skills/ux-analyze-by-hani) | Heuristic evaluation / UX audit of a live website — Nielsen's 10 heuristics, accessibility, and visual hierarchy — with scope, JTBD, weighted severity, and a structured report. |

## Repo structure

```
ux-automation/
├── README.md                    ← you are here
├── LICENSE
└── skills/
    └── ux-analyze-by-hani/
        ├── SKILL.md              ← required: frontmatter + instructions Claude loads
        ├── README.md              ← human-facing docs for this skill
        ├── references/            ← (optional) extra context files the skill reads
        └── scripts/                ← (optional) executables the skill can run
```

Each skill lives in its own folder under `skills/` and is self-contained: a `SKILL.md` with YAML frontmatter (`name`, `description`) plus the body instructions, and optionally `references/` and `scripts/` subfolders. This is the standard layout expected by Claude Code, Claude.ai, and third-party skill registries — adding a new skill means adding a new folder here, nothing else changes.

## Install via GitHub

**Claude Code (CLI):**

```bash
git clone https://github.com/<your-org>/ux-automation.git
mkdir -p ~/.claude/skills
cp -r ux-automation/skills/ux-analyze-by-hani ~/.claude/skills/
```

Or symlink instead of copy if you want to `git pull` updates:

```bash
ln -s "$(pwd)/ux-automation/skills/ux-analyze-by-hani" ~/.claude/skills/ux-analyze-by-hani
```

**Project-scoped instead of user-scoped:** copy/symlink into `.claude/skills/` inside a specific project instead of `~/.claude/skills/`.

**Claude.ai (web/desktop), Team/Enterprise:** zip the individual skill folder so `SKILL.md` sits at the root of the archive (not nested), then upload it under *Settings → Capabilities → Skills* (or *Customize → Skills* for org publishing). See [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude).

## Adding a new skill

1. Create `skills/<skill-name>/SKILL.md` with YAML frontmatter (`name`, `description`) and the instructions body.
2. Add a `skills/<skill-name>/README.md` with a human-readable summary (copy the pattern from `ux-analyze-by-hani`).
3. Add any `references/` or `scripts/` the skill needs.
4. Add a row to the table above.

## License

See [LICENSE](LICENSE).
