# igniteui-mcp-tools

Claude Code plugin that enables local Ignite UI MCP servers for component documentation and theming workflows.

## Included MCP servers

- `igniteui` via `@igniteui/mcp-server`
- `igniteui-theming` via `igniteui-theming`

## Requirements

- Node.js 20+
- Claude Code installed and authenticated
- Internet access for first `npx` package resolution

## Plugin structure

- `.claude-plugin/plugin.json` plugin manifest
- `.mcp.json` MCP server definitions
- `skills/igniteui-design-system/SKILL.md` optional design-focused skill

## Validate

```bash
claude plugin validate .
```

Use strict validation if desired:

```bash
claude plugin validate . --strict
```

## Run locally

```bash
claude --plugin-dir .
```

In Claude Code, run:

- `/reload-plugins` after edits
- `/help` to verify namespaced skill availability

## Troubleshooting

1. Verify Node version:

```bash
node -v
```

2. Verify MCP server commands manually:

```bash
npx -y @igniteui/mcp-server
npx -y igniteui-theming igniteui-theming-mcp
```

3. If startup fails in Claude, inspect plugin errors and MCP logs from the plugin manager.

## License

MIT
