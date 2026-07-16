# Repository instructions

This repository is a cross-tool skills library. Keep each skill's canonical
instructions in `plugins/<name>/skills/<name>/SKILL.md`, and keep that file
portable between Claude Code and GitHub Copilot.

When changing or adding a skill:

- Update both marketplace manifests:
  `.claude-plugin/marketplace.json` and `.github/plugin/marketplace.json`.
- Update both plugin manifests for the skill:
  `plugins/<name>/.claude-plugin/plugin.json` and
  `plugins/<name>/.github/plugin/plugin.json`.
- Update `README.md`, `CONTRIBUTING.md`, and the skill's own `README.md` when
  installation, invocation, or packaging details change.
- Bump the version in both plugin manifests and both marketplace entries when
  the skill's behaviour changes.

Authoring rules:

- Prefer the shared frontmatter subset: `name`, `description`, and optional
  `license` or `allowed-tools`.
- Avoid client-specific placeholders or invocation syntax in `SKILL.md`.
  Reference the user prompt or referenced context instead of Claude-only
  variables such as `$ARGUMENTS`.
- Keep each skill narrow and explicit about when it should be used.

Repository layout:

- `.claude-plugin/marketplace.json` is the Claude marketplace manifest.
- `.github/plugin/marketplace.json` is the Copilot marketplace manifest.
- `plugins/<name>/skills/<name>/SKILL.md` is the canonical skill body.
- `plugins/<name>/README.md` is the user-facing documentation for that skill.
