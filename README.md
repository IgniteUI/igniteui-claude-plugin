# Ignite UI MCP Tools for Claude Code

A [Claude Code](https://code.claude.com) plugin that connects Claude to the Ignite UI MCP servers, so it can look up component documentation and APIs and generate themes for **Angular**, **React**, **Blazor**, and **Web Components** without guessing from memory.

## What's included

| Component | Type | Description |
| --- | --- | --- |
| `igniteui-cli` | MCP server | Runs the [Ignite UI CLI](https://www.npmjs.com/package/igniteui-cli) MCP server (`ig mcp`): component lists, docs search, API reference, and project setup guides. |
| `igniteui-theming` | MCP server | Runs [`igniteui-theming`](https://www.npmjs.com/package/igniteui-theming): palettes, typography, elevations, component themes, and design tokens. |
| `igniteui-design-system` | Skill | Tells Claude to use both servers together, check APIs and tokens against the servers, and keep each framework's syntax separate. |

Both MCP servers run on your machine through `npx`. You don't need API keys or a hosted service.

## Requirements

- [Claude Code](https://code.claude.com/docs/en/quickstart), installed and signed in
- Node.js 20 or later (with `npx` on your `PATH`)
- Internet access the first time, so `npx` can download the server packages

## Installation

### From a marketplace

If the plugin is published in a marketplace you've added, install it from inside Claude Code:

```text
/plugin install igniteui-mcp-tools@<marketplace-name>
```

Or from your shell:

```bash
claude plugin install igniteui-mcp-tools@<marketplace-name>
```

### From source

Clone the repository and start Claude Code with the plugin loaded:

```bash
git clone https://github.com/IgniteUI/igniteui-claude-plugin.git
claude --plugin-dir ./igniteui-claude-plugin
```

## Usage

When the plugin is enabled, Claude can call the MCP tools directly. Ask questions the way you normally would, for example:

- "Add an Ignite UI grid with sorting and paging to this Angular component."
- "What events does `IgrCombo` expose in React?"
- "Create a dark theme for my Blazor app using our brand color `#0A5FFF`."
- "Which design tokens control the Web Components button's hover state?"

Claude detects the framework from your project: `Igx` prefixes for Angular, `Igr` for React, `Igb` for Blazor, and `Igc` for Web Components. If it can't tell, it asks.

### Skill

Claude loads the `igniteui-design-system` skill automatically when a request is about Ignite UI design or theming. You can also call it by name:

```text
/igniteui-mcp-tools:igniteui-design-system
```

### Checking the MCP servers

Run `/mcp` in Claude Code to see whether `igniteui-cli` and `igniteui-theming` are connected and which tools they provide.

## Plugin structure

```text
.
├── .claude-plugin/
│   └── plugin.json                 # Plugin manifest
├── .mcp.json                       # MCP server definitions
└── skills/
    └── igniteui-design-system/
        └── SKILL.md                # Design-system skill
```

## Development

Validate the manifest, skills, and MCP configuration:

```bash
claude plugin validate .
```

Use `--strict` to treat warnings as errors, for example in CI:

```bash
claude plugin validate . --strict
```

Load your local copy while you work on it:

```bash
claude --plugin-dir .
```

In the Claude Code session, run `/reload-plugins` to pick up changes you've made. Run `/help` to confirm the skill appears under the `igniteui-mcp-tools:` namespace.

## Troubleshooting

1. **Check your Node.js version.** It must be 20 or later:

   ```bash
   node -v
   ```

2. **Start each server by hand** to see any startup errors:

   ```bash
   npx -y igniteui-cli mcp
   npx -y igniteui-theming igniteui-theming-mcp
   ```

3. **Check the server status in Claude Code.** Run `/mcp` to see connection status and errors. Run `/plugin` to see whether the plugin loaded or failed.

4. **Clear a stale `npx` cache.** If a server won't start after an update, run `npx clear-npx-cache`, or delete `~/.npm/_npx`, and then restart Claude Code.

## Resources

- [Ignite UI AI-assisted app development](https://www.infragistics.com/ai-assisted-app-development)
- [Ignite UI on GitHub](https://github.com/IgniteUI)
- [Claude Code plugins documentation](https://code.claude.com/docs/en/plugins)

## License

[MIT](LICENSE)
