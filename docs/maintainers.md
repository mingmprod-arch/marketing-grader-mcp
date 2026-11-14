# Maintainer compatibility notes

## Portable manifests and OpenAI OAuth

The root `plugin.json` and `mcp.json` use the Agent Plugins 1.0.0 format. `mcp.json` declares the Streamable HTTP URL only; the hosted service still requires OAuth. No fixed credential or private client is packaged.

The current [OpenAI packaging documentation](https://developers.openai.com/plugins/build/plugins) describes per-server `extensions.com.openai.auth` with `type: oauth` and `client.mode: dcr`. The public [Agent Plugins 1.0.0 MCP schema](https://agent-plugins.org/schemas/1.0.0/mcp.schema.json) currently disallows per-server `extensions`. To avoid a known portable-schema mismatch, this package relies on OAuth discovery and keeps that optional declaration out of `mcp.json`. Confirm discovery and the OAuth selection in the host's connection/submission workflow. Do not change the server to unauthenticated access.

## Gemini CLI

`gemini-extension.json` lives at the repository root and declares a remote MCP server using `httpUrl`. It does not install a local server or request API-key settings, hooks or trust bypasses. The [official extension reference](https://geminicli.com/docs/extensions/reference/) permits MCP settings except `trust`; the [MCP configuration reference](https://geminicli.com/docs/tools/mcp-server/) defines `httpUrl` as Streamable HTTP.

## Service scope

The hosted service and its data are separate from this public connection package. Do not add backend source, deployment notes, account identifiers, private evidence, support transcripts, environment files or credentials to this repository. No open-source backend license is implied.

## Release checks

Validate JSON/TOML, the portable manifests and Gemini MCP shape, then inspect every public file for private material. Live host OAuth, selected-brand access, property grants and revocation are separate acceptance checks. Avoid labeling configuration validation as successful marketplace review.
