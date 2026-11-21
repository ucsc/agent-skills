# UC Santa Cruz agent skills

Skills for AI coding agents (Claude Code, Cursor, and others), in the [skills.sh](https://skills.sh) format. Install only the ones you want.

## Skills

| Skill | What it does |
| --- | --- |
| `ucsc-brand` | UC Santa Cruz visual identity: colors, typography, logo rules, voice, and the token values from the `ucsc-2022` theme. |
| `ucsc-spec` | Write and maintain feature specs as GitHub issues. Also moves an old `ROADMAP.md` into specs. Needs the `gh` command line tool. |

## Install

Pick from a list:

```sh
npx skills add ucsc/agent-skills
```

Install one skill:

```sh
npx skills add ucsc/agent-skills --skill ucsc-spec
```

Update installed skills:

```sh
npx skills update
```

## Add a skill

1. Make a folder: `skills/<skill-name>/`
2. Add a `SKILL.md` that starts with:

   ```markdown
   ---
   name: skill-name
   description: What the skill does and when an agent should use it.
   ---
   ```

   `name` must be lowercase, with hyphens, and match the folder name.
3. Put longer reference material in `skills/<skill-name>/references/` and point to it from `SKILL.md`.
4. Add a row to the table above.
