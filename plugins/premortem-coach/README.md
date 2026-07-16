# Pre-mortem Coach

A Claude Code skill that runs a pre-mortem coaching session for a software project, then writes up a kickoff document.

## What it does

You name a project. Claude jumps forward past a chosen horizon (six months by default) and adopts the premise that the project has failed. It then facilitates a structured session — one question at a time, working backwards from symptoms to causes — with rules designed to surface the risks you would not volunteer:

- It pushes past the risks you already knew about
- It asks at least one question about *your* role in the failure
- It challenges vague answers ("scope creep" is not a mechanism)
- It refuses to start the write-up until minimum ground is covered

At the end it produces a one-page kickoff document: project framing, risks ranked partly by how reluctant you were to name them, one specific mitigation per risk, early-warning signals you could notice in a given week, and open questions.

## Install

```
/plugin marketplace add dp-lewis/licence-to-skill
/plugin install premortem-coach@licence-to-skill
```

## Use

Just describe what you want in natural language — the skill triggers on intent, e.g.:

- "Run a pre-mortem on the migration project"
- "Stress-test this plan before we start"
- "Imagine this initiative failed in six months — help me work out why"

## Licence

MIT
