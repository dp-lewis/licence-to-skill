# licence to skill

A shared library of reusable [Claude Code skills](https://code.claude.com/docs/en/skills),
distributed as a plugin marketplace.

Each skill is a small, self-contained procedure — a checklist or workflow you'd
otherwise paste into chat over and over. Install the ones you want and invoke
them with `/skill-name`, or let Claude load them automatically when relevant.

## What's here

| Skill | Does |
| --- | --- |
| [`explain-code`](plugins/explain-code) | Explains a file or the selected code in plain language. |
| [`premortem-coach`](plugins/premortem-coach) | Runs a pre-mortem facilitation session and produces a kickoff doc with ranked risks. |

## Install

Add this repo as a plugin marketplace, then install the skills you want:

```
/plugin marketplace add dp-lewis/licence-to-skill
/plugin install explain-code@licence-to-skill
```

Invoke a skill with `/explain-code`, or let Claude load it automatically when
it's relevant. Pull later updates with `/plugin marketplace update`.

## Add a skill

Use the **skill-creator** skill to author or improve a skill — it scaffolds the
`SKILL.md`, helps you write a strong description, and can test the result:

```
/skill-creator
```

Point it at `plugins/<your-skill>/skills/<your-skill>/SKILL.md`, then register
the skill by adding an entry to the `plugins` array in
[`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json).

See [CONTRIBUTING.md](CONTRIBUTING.md) for conventions and the full checklist.

## How it fits together

```
.claude-plugin/marketplace.json   Catalog users add with /plugin marketplace add
plugins/<skill>/
  .claude-plugin/plugin.json      Plugin manifest
  skills/<skill>/SKILL.md         The skill itself
  README.md                       Optional: longer explanation, examples
```

## Licence

[MIT](LICENSE).
