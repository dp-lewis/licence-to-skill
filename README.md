# licence to skill

A shared library of reusable skills for Claude Code and GitHub Copilot,
distributed as plugin marketplaces.

Each skill is a small, self-contained procedure: a checklist or workflow you'd
otherwise paste into chat over and over. The canonical instructions live in
`SKILL.md`; the surrounding manifests package them for each client.

## What's here

| Skill | Does |
| --- | --- |
| [`premortem-coach`](plugins/premortem-coach) | Runs a pre-mortem facilitation session and produces a kickoff doc with ranked risks. |

## Install

### Claude Code

```text
/plugin marketplace add dp-lewis/licence-to-skill
/plugin install premortem-coach@licence-to-skill
```

Invoke it with `/premortem-coach`, or let Claude load it automatically when
relevant.

### Copilot CLI

```text
copilot plugin marketplace add dp-lewis/licence-to-skill
copilot plugin install premortem-coach@licence-to-skill
```

Then start a session and invoke it with a prompt such as `Use the
/premortem-coach skill to run a pre-mortem on this project`, or let Copilot
load it automatically when relevant.

## Add a skill

Author the canonical skill in `plugins/<name>/skills/<name>/SKILL.md`, keep the
instructions portable between Claude and Copilot, then add the thin packaging
manifests for each client:

```text
plugins/<name>/
  .claude-plugin/plugin.json
  .github/plugin/plugin.json
  skills/<name>/SKILL.md
  README.md
```

Register the skill in both marketplace manifests: `.claude-plugin/marketplace.json`
and `.github/plugin/marketplace.json`.

See [CONTRIBUTING.md](CONTRIBUTING.md) for conventions and the full checklist.

## How it fits together

```text
.claude-plugin/marketplace.json   Claude marketplace manifest
.github/plugin/marketplace.json   Copilot marketplace manifest
plugins/<skill>/
  .claude-plugin/plugin.json      Claude plugin manifest
  .github/plugin/plugin.json      Copilot plugin manifest
  skills/<skill>/SKILL.md         Canonical skill instructions
  README.md                       Optional: longer explanation, examples
```

## Licence

[MIT](LICENSE).
