# Pre-mortem Coach

A reusable skill for Claude Code and GitHub Copilot that runs a pre-mortem
coaching session for a software project, then writes up a kickoff document.

## What it does

You name a project. The skill jumps forward past a chosen horizon (six months by
default) and adopts the premise that the project has failed. It then
facilitates a structured session — one question at a time, working backwards
from symptoms to causes — with rules designed to surface the risks you would
not volunteer:

- It pushes past the risks you already knew about
- It asks at least one question about *your* role in the failure
- It challenges vague answers ("scope creep" is not a mechanism)
- It refuses to start the write-up until minimum ground is covered

At the end it produces a one-page kickoff document: project framing, risks ranked partly by how reluctant you were to name them, one specific mitigation per risk, early-warning signals you could notice in a given week, and open questions.

## Install

### Claude Code

```text
/plugin marketplace add dp-lewis/licence-to-skill
/plugin install premortem-coach@licence-to-skill
```

### Copilot CLI

```text
copilot plugin marketplace add dp-lewis/licence-to-skill
copilot plugin install premortem-coach@licence-to-skill
```

## Use

Claude can invoke the skill directly with `/premortem-coach`.

In Copilot CLI, mention the skill in the prompt, for example `Use the
/premortem-coach skill to stress-test this plan before we start`.

It can also trigger from intent alone, for example:

- "Run a pre-mortem on the migration project"
- "Stress-test this plan before we start"
- "Imagine this initiative failed in six months — help me work out why"

## Licence

MIT
