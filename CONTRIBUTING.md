# Contributing a skill

A skill is a single procedure Claude can follow on demand. Good skills are
narrow, well-scoped, and describe *when* to use them clearly enough that Claude
can pick them up automatically.

## Anatomy

```
plugins/<name>/
  .claude-plugin/plugin.json     Plugin manifest (name, description, version…)
  skills/<name>/SKILL.md         Frontmatter + the procedure itself
  README.md                      Optional: longer explanation, examples
```

## Steps

1. **Author it with skill-creator.** Run the `skill-creator` skill and let it
   scaffold and refine the skill for you:

   ```
   /skill-creator
   ```

   It writes the `SKILL.md`, helps you get the description right, and can test
   the result. Place the skill under `plugins/<name>/skills/<name>/SKILL.md`
   (kebab-case name — the directory name is what users type after `/`).

   `skill-creator` ships in Anthropic's official plugin marketplace. If you
   don't already have it, install it once:

   ```
   /plugin marketplace add anthropics/claude-plugins-official
   /plugin install skill-creator@claude-plugins-official
   ```

2. **Add the plugin manifest.** Each skill is its own plugin, so it needs
   `plugins/<name>/.claude-plugin/plugin.json` with at least `name`,
   `description`, and `version`. Copy an existing one as a starting point.

3. **Register it in the marketplace.** Add an entry to the `plugins` array in
   [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json). The
   `name` and `source` both equal the skill's directory name (the `pluginRoot`
   is already `./plugins`).

4. **Test it.**

   ```
   /plugin marketplace add ./
   /plugin install <name>@licence-to-skill
   /<name>
   ```

## Writing a good SKILL.md

- **`description` is the most important line.** Lead with the primary use case
  and the phrases that should trigger it — this is how Claude decides to load
  the skill automatically. Keep the combined description under ~1,500
  characters.
- **The body is an ordered procedure** — steps, rules, and the expected output
  format. Keep it proportional to the task.
- The `skill-creator` skill covers this in more depth; lean on it.

## Frontmatter fields

| Field | Required | Notes |
| --- | :---: | --- |
| `name` | No | Display name; the directory name drives the command. |
| `description` | Recommended | What the skill does and when to use it. |
| `argument-hint` | No | Autocomplete hint, e.g. `[file-or-symbol]`. |
| `disable-model-invocation` | No | `true` makes a skill manual (`/name`) only — use for side-effecting workflows. |
| `allowed-tools` | No | Tools Claude may use without a permission prompt while the skill is active. |

## Versioning

Bump the `version` in both `plugin.json` and the marketplace entry when you
change a skill's behaviour — Claude Code only pulls updates when the pinned
version changes.
