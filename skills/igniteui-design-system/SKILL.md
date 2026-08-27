---
description: Build framework-correct Ignite UI design output by combining documentation and theming MCP tools.
---

Use this skill for Ignite UI design and implementation requests, including component selection, API usage, tokens, palettes, theme customization, and style consistency.

Primary goals:
1. Keep output strictly framework-correct (angular, react, blazor, or webcomponents).
2. Use MCP tools as source of truth for component docs, API details, and theme tokens.
3. Produce copy-paste-ready output with a short rationale.

Workflow:
1. Detect the framework from user context; if unclear, ask one concise clarification question.
2. Use igniteui MCP documentation and API tools to confirm component names, capabilities, and framework-specific usage.
3. Use igniteui-theming MCP tools to generate palettes, tokens, and theme-level customization.
4. Combine both results into implementation guidance that references valid component APIs and valid token names.
5. If requested output is ambiguous, provide one safe default and one alternative.

Quality bar:
- Never mix APIs or syntax between frameworks.
- Do not invent component APIs, events, or token names from memory.
- Prioritize accessibility and contrast-safe choices.
- Keep naming consistent with Ignite UI conventions.
- Prefer tokenized, maintainable styling over one-off overrides.
