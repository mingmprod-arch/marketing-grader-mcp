# Host configuration examples

Merge only the `marketing-grader` server entry into existing settings. Do not overwrite your other servers. No file in this directory contains a credential.

| File | Destination | Important difference |
|---|---|---|
| `cursor.mcp.json` | `.cursor/mcp.json` or `~/.cursor/mcp.json` | `mcpServers` with `url` |
| `claude-code.mcp.json` | Project `.mcp.json` | `mcpServers` with `type: http` and `url` |
| `vscode.mcp.json` | `.vscode/mcp.json` | Top-level `servers` with `type: http` and `url` |
| `copilot-portable.mcp.json` | Portable workspace `.mcp.json` | Top-level `mcpServers`; distinct from the editor format |
| `gemini.settings.json` | `.gemini/settings.json` or `~/.gemini/settings.json` | `mcpServers` with `httpUrl` for Streamable HTTP |
| `codex.config.toml` | Relevant Codex `config.toml` | `[mcp_servers.marketing-grader]` with `url` |

The repository root also has a Gemini extension manifest. Choose extension installation or manual Gemini settings, not both.

Complete OAuth through your AI host. If the host cannot complete discovery, check the [official host documentation](../docs/sources.md) and report a sanitized error. Do not replace OAuth with a pasted token.
