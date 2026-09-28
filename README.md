# ux-automation

A collection of [Claude Agent Skills](https://code.claude.com/docs/en/skills) for UX/product work — audits, reviews, and automation that plug into Claude Code, Claude Desktop/Web, or any Agent-Skills-compatible client.

Maintained by [@hanie-fre](https://github.com/hanie-fre).

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

## How to install

Pick the option that matches how you use Claude.

### Option A — Claude Code (CLI), user-wide

Installs the skill for every project on your machine.

```bash
git clone https://github.com/hanie-fre/ux-automation.git
mkdir -p ~/.claude/skills
cp -r ux-automation/skills/ux-analyze-by-hani ~/.claude/skills/
```

Prefer to stay updated with `git pull` instead of re-copying? Symlink it instead:

```bash
git clone https://github.com/hanie-fre/ux-automation.git
mkdir -p ~/.claude/skills
ln -s "$(pwd)/ux-automation/skills/ux-analyze-by-hani" ~/.claude/skills/ux-analyze-by-hani
```

Restart Claude Code (or start a new session) and the skill is available — Claude will pick it up automatically whenever a request matches, or you can invoke it directly.

### Option B — Claude Code (CLI), one project only

Same as above but copy/symlink into `.claude/skills/` **inside that project's folder** instead of `~/.claude/skills/`:

```bash
cd /path/to/your/project
mkdir -p .claude/skills
cp -r /path/to/ux-automation/skills/ux-analyze-by-hani .claude/skills/
```

### Option C — Claude.ai (web/desktop app), Team/Enterprise plans

1. On GitHub, open [`skills/ux-analyze-by-hani`](skills/ux-analyze-by-hani), click **Code → Download ZIP** (or just zip that one folder locally) — make sure `SKILL.md` ends up at the **root** of the zip, not nested inside another folder.
2. In Claude, go to **Settings → Capabilities → Skills** (or **Customize → Skills** if you're publishing it for your whole organization).
3. Upload the zip.

Full details: [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude).

### Verifying it worked

Ask Claude something like *"audit the UX of this page"* or *"run a heuristic evaluation on my site"* — if the skill loaded correctly, Claude should recognize the request and start with the setup questions described in [`SKILL.md`](skills/ux-analyze-by-hani/SKILL.md).

## Adding a new skill

1. Create `skills/<skill-name>/SKILL.md` with YAML frontmatter (`name`, `description`) and the instructions body.
2. Add a `skills/<skill-name>/README.md` with a human-readable summary (copy the pattern from `ux-analyze-by-hani`).
3. Add any `references/` or `scripts/` the skill needs.
4. Add a row to the table above.

## License

See [LICENSE](LICENSE).
