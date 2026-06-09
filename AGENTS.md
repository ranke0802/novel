# Awesome Novel Studio for Codex

This workspace contains the Awesome Novel Studio harness.

When the user enters one of the harness slash commands, use the matching local skill file as the workflow source:

- `/propose` -> `skills/propose/SKILL.md`
- `/design` -> `skills/design/SKILL.md`
- `/design-big` -> `skills/design-big/SKILL.md`
- `/design-small` -> `skills/design-small/SKILL.md`
- `/bootstrap` -> `skills/bootstrap/SKILL.md`
- `/character` -> `skills/character/SKILL.md`
- `/plot-hook` -> `skills/plot-hook/SKILL.md`
- `/create` -> `skills/create/SKILL.md`
- `/polish` or `/lint` -> `skills/polish/SKILL.md`
- `/rewrite` or `/revise` -> `skills/rewrite/SKILL.md`

Codex's built-in slash command menu may not show these harness commands. If the user writes a harness command without a leading slash, or embeds it in natural language, route it the same way. Examples: `propose: ...`, `Novel Studio /propose ...`, `design-big 진행`, `polish EP001`.

When running `create` for a specific episode or range, treat existing episode files outside the requested target as read-only continuity sources. Do not edit prior episodes while creating a later episode. If continuity issues seem to require changing earlier chapters, report the issue and ask before editing. `polish` and `rewrite` may edit only the explicit target range supplied by the user.

Treat `${CLAUDE_PLUGIN_ROOT}` references in copied upstream files as this workspace root.
Agent role files live in `agents/`. When a skill references a Claude subagent, read the matching `agents/*.md` file and use it as role guidance. In Codex, follow the active Codex agent policy for whether background/sub-agent execution is allowed; otherwise execute the workflow locally.

Generated novel project files should follow the upstream structure:

- `novel-config.md`
- `design/`
- `episode/`
- `revision/`
- `_workspace/`

This workspace has a project-specific writing bible:

- `CLAUDE.md` — source-of-truth writing rules for `중고 노트북 속 오리가 너무 전능함`
- `novel-config.md` — maps the writing bible and design documents into the harness
- `design/future-ai_*.md` — bootstrap, character sheet, and plot/hook guides

For every harness command in this workspace, load `novel-config.md` first when it exists. If `design_documents.writing_rules` is present, treat that file as a high-priority project bible and pass it to downstream planning, writing, polish, and rewrite agents. Do not override these rules with generic genre defaults.

The supported target platforms are `문피아`, `네이버시리즈`, `카카오페이지`, `리디`, `조아라`, and `노벨피아`.
