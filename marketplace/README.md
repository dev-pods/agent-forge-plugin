# Agents Teams Catalog

This directory contains the local marketplace catalog for the `agents-teams` plugin. It makes the four bundled GitHub Copilot agents discoverable without referencing a remote marketplace.

## Structure

- `marketplace.json` is the machine-readable catalog.
- `../agents/` contains the source `.agent.md` definitions referenced by the catalog.
- `../../../plugin.json` is the plugin manifest and points to `marketplace.json` through its `com.github.copilot` extension metadata.

The catalog lists only these agents:

- `coder` — implementation, debugging, and code quality.
- `designer` — UI/UX and accessibility design.
- `planner` — implementation planning and research.
- `orchestrator` — task decomposition and agent coordination.

## Querying the Catalog

Read `marketplace.json` as JSON and select an entry from its `agents` array by stable `id`, `name`, `category`, `tags`, or `capabilities`. The `source` property is relative to this directory. Resolve it before loading the corresponding `.agent.md` file.

The `models` and `requiredTools` properties are copied from agent frontmatter when those fields are present. A missing `models` property means the source frontmatter does not declare one.

## Versioning and Publication

- Keep `catalogVersion` at `1.0.0` unless the catalog format changes incompatibly.
- Set every agent entry's `version` to the compatible plugin release version.
- Increment the plugin and agent versions together for a catalog change, agent metadata change, or source-definition change.
- Keep IDs stable after publication. Create a new ID rather than reusing an old one for a semantically different agent.
- Before publishing, confirm every `source` path resolves to an existing `.agent.md` file and that the catalog has no undeclared agents.

## Security Review

Review catalog changes together with their referenced agent definitions. Verify that tool names and model declarations exactly match source frontmatter, that relative paths do not leave the plugin directory, and that descriptions do not claim unavailable capabilities. Do not add external URLs, credentials, secrets, or unreviewed tool permissions to the catalog.