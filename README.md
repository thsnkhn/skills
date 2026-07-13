# Agent Skills

Reusable skills for AI coding agents, distributed through [skills.sh](https://skills.sh).

[![skills.sh](https://skills.sh/b/thsnkhn/skills)](https://skills.sh/thsnkhn/skills)

## Install

The [`skills` CLI](https://skills.sh/docs/cli) detects compatible agents on your machine and guides you through selecting skills and installation targets.

Browse this repository and install interactively:

```bash
npx skills add thsnkhn/skills
```

List the available skills without installing:

```bash
npx skills add thsnkhn/skills --list
```

Install a specific skill:

```bash
npx skills add thsnkhn/skills --skill linkedin-writer
npx skills add thsnkhn/skills --skill x-content-writer
```

Skills install into the current project by default. Add `--global` to make them available across projects.

## Available Skills

| Skill | Description |
|---|---|
| [`linkedin-writer`](skills/linkedin-writer) | Draft, rewrite, and critique natural LinkedIn posts in a bundled direct builder-operator voice grounded in real work and evidence. |
| [`x-content-writer`](skills/x-content-writer) | Draft, revise, critique, and plan Twitter/X posts, replies, quotes, and threads using an algorithm-informed content playbook. |

## License

MIT
