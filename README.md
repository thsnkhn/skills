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
npx skills add thsnkhn/skills --skill write-like-thsnkhn
npx skills add thsnkhn/skills --skill x-content-writer
```

Skills install into the current project by default. Add `--global` to make them available across projects.

## Reclaim

Run a manual, read-only audit of disk use and repeated storage growth. The report identifies targeted cleanup options, required data to keep, and prevention settings. It does not delete files or install automation.

Install with the interactive CLI, then select `reclaim`:

```bash
npx skills add thsnkhn/skills
```

Invoke with `$reclaim`. You can request a whole-machine audit or limit it to a project.

## Available Skills

| Skill | Description |
|---|---|
| [`reclaim`](skills/reclaim) | Manually audit storage, dependencies, caches, containers, and application leftovers; report targeted cleanup and prevention options without changing anything. |
| [`linkedin-writer`](skills/linkedin-writer) | Draft, rewrite, and critique natural LinkedIn posts in a bundled direct builder-operator voice grounded in real work and evidence. |
| [`write-like-thsnkhn`](skills/write-like-thsnkhn) | Write everyday work messages, updates, feedback, requests, and agent prompts in Tahseen's direct operator voice. |
| [`x-content-writer`](skills/x-content-writer) | Draft, revise, critique, and plan Twitter/X posts, replies, quotes, and threads using an algorithm-informed content playbook. |

## License

MIT
