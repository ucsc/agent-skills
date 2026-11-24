# UC Santa Cruz agent skills

Three skills for AI coding agents, including OpenAI Codex, Claude Code, and Cursor, in the [skills.sh](https://skills.sh) format. Install only the ones you want, or install all three as a Codex plugin.

## Skills

| Skill | What it does |
| --- | --- |
| `ucsc-brand` | UC Santa Cruz visual identity: colors, typography, logo rules, voice, and the token values from the `ucsc-2022` theme. |
| `ucsc-spec` | Write and maintain feature specs as GitHub issues. Also moves an old `ROADMAP.md` into specs. Needs the `gh` command line tool. |
| `ucsc-git-commit` | Write and check short git commit messages: Conventional Commits format, plain English (ASD-STE100 rules), no repeated spec details, and no AI attribution. |

## Installation

### Install with the skills CLI

Works with Claude Code, Cursor, and other agents. Pick from a list:

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

### Install in the Claude desktop app

1. Open **Customize**, then the **Plugins** tab.
2. Click **Add**, then **Add marketplace**.
3. Enter `ucsc/agent-skills`.
4. Add the plugins you want. Each skill is its own plugin.

### Install in Claude Code

```
/plugin install ucsc-brand --marketplace ucsc/agent-skills
/plugin install ucsc-spec --marketplace ucsc/agent-skills
/plugin install ucsc-git-commit --marketplace ucsc/agent-skills
```

### Install in OpenAI Codex

With a Codex CLI that supports `codex plugin`, install the plugin to get all three skills (`ucsc-brand`, `ucsc-spec`, and `ucsc-git-commit`):

```sh
codex plugin marketplace add ucsc/agent-skills
codex plugin add ucsc-agent-skills@ucsc-agent-skills
```

Or use the skills CLI to choose skills for Codex:

```sh
npx skills add ucsc/agent-skills -a codex
```

To install all three without the selection prompt:

```sh
npx skills add ucsc/agent-skills -a codex --skill ucsc-brand ucsc-spec ucsc-git-commit -y
```

To install only one, pass its name to `--skill`:

```sh
npx skills add ucsc/agent-skills -a codex --skill ucsc-spec
```

The skills CLI installs into `.agents/skills/` in your current project. Add `-g` to install for all your projects.

In Codex, type `$` to choose an installed skill, or invoke `$ucsc-brand`, `$ucsc-spec`, or `$ucsc-git-commit` in a prompt. If the skills do not appear, restart Codex. The spec skill also needs an installed and authenticated `gh` command line tool.

See OpenAI's [skill documentation](https://developers.openai.com/codex/skills) and [plugin packaging documentation](https://developers.openai.com/plugins/build/plugins) for discovery and plugin setup.

### Check skills before installing

List the skills available from GitHub without installing them:

```sh
npx skills add ucsc/agent-skills --list
```

When checking changes in a local clone, run `npx skills add . --list` from the repository root. The list should contain exactly the three skills in the table above.

### Install in Google Gemini CLI

Use the skills CLI with the `gemini-cli` agent:

```sh
npx skills add ucsc/agent-skills -a gemini-cli
```

Or use Gemini's own command, one skill at a time:

```sh
gemini skills install https://github.com/ucsc/agent-skills.git --path skills/ucsc-spec
```

## Add a skill

Enable the repository's pre-commit hook once per clone:

```sh
git config --local core.hooksPath .githooks
```

The hook checks that each staged `skills/<skill-name>/SKILL.md` has a row in the staged README's Skills table. Stage the README update with the skill.

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
5. Add a plugin entry for the skill in `.claude-plugin/marketplace.json`. Copy an existing entry and change the name, description, and skill path.

Codex needs no new entry: its plugin includes every folder in `skills/`. To release a change to Codex plugin users, raise `version` in both `.codex-plugin/plugin.json` and `.agents/plugins/marketplace.json`.
