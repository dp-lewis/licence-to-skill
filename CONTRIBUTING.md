# Contributing a skill

A skill is a single procedure an agent can follow on demand. Good skills are
narrow, well-scoped, and describe *when* to use them clearly enough that both
Claude and Copilot can pick them up automatically.

## Anatomy

```
plugins/<name>/
  .claude-plugin/plugin.json     Claude plugin manifest
  .github/plugin/plugin.json     Copilot plugin manifest
  skills/<name>/SKILL.md         Canonical frontmatter + procedure
  README.md                      Optional: longer explanation, examples
```

## Steps

1. **Author the canonical `SKILL.md`.** Create
   `plugins/<name>/skills/<name>/SKILL.md` first, then package it for each
   client.

   Keep the file in the shared subset that works well across tools:

   - Use `name`, `description`, and optional `license` or `allowed-tools`
     frontmatter.
   - Avoid Claude-specific placeholders such as `$ARGUMENTS`.
   - Write the body in tool-neutral language: refer to "the user prompt" or
     "the referenced file" rather than one client's UI affordances.

   If you already work in Claude, `skill-creator` can be a useful drafting
   tool, but treat its output as a starting point and normalize it before
   committing.

2. **Add both plugin manifests.** Each skill is its own plugin, so it needs
   `plugins/<name>/.claude-plugin/plugin.json` and
   `plugins/<name>/.github/plugin/plugin.json`, each with at least `name`,
   `description`, and `version`.

3. **Register it in both marketplaces.** Add matching entries to
   [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) and
   [`.github/plugin/marketplace.json`](.github/plugin/marketplace.json).

4. **Test it in both clients.**

   ```text
   /plugin marketplace add ./
   /plugin install <name>@licence-to-skill
   /<name>
   ```

   ```text
   copilot plugin marketplace add ./
   copilot plugin install <name>@licence-to-skill
   ```

   Then open a Copilot CLI session, run `/skills info <name>` to confirm the
   skill loaded, and invoke it with a prompt that names the skill, for example
   `Use the /<name> skill ...`.

## Writing a good SKILL.md

- **`description` is the most important line.** Lead with the primary use case
  and the phrases that should trigger it — this is how Claude and Copilot
  decide to load the skill automatically. Keep the combined description under
  ~1,500 characters.
- **The body is an ordered procedure** — steps, rules, and the expected output
  format. Keep it proportional to the task.
- **Keep it portable.** Prefer instructions that make sense in any chat or
  agent surface. If you need client-specific behavior, document it in the
  surrounding README or manifest rather than in the canonical `SKILL.md`.

## Frontmatter fields

| Field | Required | Notes |
| --- | :---: | --- |
| `name` | Yes | Unique skill identifier; keep it kebab-case and match the directory name. |
| `description` | Yes | What the skill does and when to use it. |
| `license` | No | Useful when the skill is shared outside this repo. |
| `allowed-tools` | No | Only list the minimum tools needed; prefer omitting it unless pre-approval materially helps. |

## Versioning

Bump the `version` in both plugin manifests and both marketplace entries when
you change a skill's behaviour:

- `plugins/<name>/.claude-plugin/plugin.json`
- `plugins/<name>/.github/plugin/plugin.json`
- `.claude-plugin/marketplace.json`
- `.github/plugin/marketplace.json`
