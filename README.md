# Marketing Grader MCP

[繁體中文／廣東話](README.zh-HK.md)

<img src="assets/marketing-grader.svg" alt="Marketing Grader" width="80" height="80">

Review your brand DNA, saved content and recorded marketing results from your AI assistant. This repository contains connection manifests and setup guides for the hosted Marketing Grader MCP service. It does not contain the Marketing Grader backend.

**Remote server:** `https://grader.recmoment.net/mcp`

## Connect in three steps

1. Add the remote server to your AI host using one of the options below.
2. Sign in to your own Marketing Grader account and review the OAuth consent screen.
3. Ask the assistant to list your available brands, then confirm which brand to use.

No API key, social token or account password belongs in these files. If you want Search Console or GA4 reports, explicitly allow the relevant property during consent.

### Gemini CLI extension

```sh
gemini extensions install https://github.com/mingmprod-arch/marketing-grader-mcp
```

Restart the Gemini CLI session after installation, then run:

```text
/mcp auth marketing-grader
/mcp
```

The root `gemini-extension.json` uses `httpUrl` for Streamable HTTP. Alternatively, merge `configs/gemini.settings.json` into your existing Gemini settings. Choose one setup method to avoid duplicate server entries.

### Codex

```sh
codex mcp add marketing-grader --url https://grader.recmoment.net/mcp
codex mcp login marketing-grader
codex mcp list
```

### Claude Code

```sh
claude mcp add --transport http marketing-grader https://grader.recmoment.net/mcp
```

Use `/mcp` in Claude Code to inspect the server and complete sign-in.

### Other AI hosts

| Host | Setup |
|---|---|
| ChatGPT | In a supported custom remote MCP connection flow, enter the remote server URL and complete OAuth. Account and administrator policy may affect availability. |
| Claude web or desktop | Add a custom remote connector with the remote server URL and complete OAuth. |
| Grok | In [Connectors](https://grok.com/connectors), choose **New Connector → Custom** and enter the remote URL. Business/Enterprise administrators may need to provision access. |
| Perplexity | On a supported Pro, Max or Enterprise account, use **Plugins → Add custom** and enter the remote MCP URL. |
| Mistral Vibe | An account owner/administrator can use **Connectors → Add Connector → Custom MCP** with the remote URL. |
| Cursor | Merge `configs/cursor.mcp.json` into `.cursor/mcp.json` or `~/.cursor/mcp.json`, then connect in MCP settings. |
| VS Code / GitHub Copilot | Merge `configs/vscode.mcp.json` into `.vscode/mcp.json`, or use **MCP: Add Server** with the HTTP URL. |

More configuration details: [host examples](configs/README.md). Manual connection and extension installation are separate from inclusion in an AI platform's public directory. This repository does not claim marketplace approval.

## Start with a question

> List my available Marketing Grader brands. Ask which brand to use before reading its data.

After choosing a brand:

> Compare its recorded 24-hour and seven-day post results. Include observation dates and keep missing data unknown.

Or:

> Summarize the Search Console and GA4 properties I explicitly granted. Keep clicks, sessions and attributed key events separate.

Brand IDs come from `list_brands`. Do not invent an ID or assume that the brand currently selected on the website automatically carries into the AI conversation. The service checks the authenticated account, role and requested brand; Google reports additionally require a matching explicit property grant.

## Nine read-only tools

| Tool | Reads |
|---|---|
| `list_brands` | Brands available to the authenticated account |
| `get_brand_dna` | Saved brand positioning, website, style, tone and permitted assets |
| `list_content_drafts` | Saved captions, hashtags, platform, status and dates |
| `get_content_calendar` | Dated social drafts and SEO plans |
| `get_social_connections` | Connection handles and recorded expiry dates, without credentials |
| `get_post_performance` | Recorded 24-hour and seven-day post metrics |
| `get_ads_strategy` | Saved advertising strategy |
| `get_search_console_performance` | Saved Search Console snapshot for the explicitly granted property |
| `get_marketing_performance` | Saved reports for explicitly granted Search Console and/or GA4 properties |

The assistant may explain records or draft ideas in the conversation. This MCP cannot save drafts, generate images, publish posts, send email, export contact lists, modify websites or ads, spend money or process payments. Google tools read saved snapshots; refresh provider data in Marketing Grader. A connection is not proof that publishing permissions are enabled. Missing results stay unknown, and engagement or key events do not establish verified revenue or ROI.

## Privacy, access and costs

You authorize the connection using OAuth with PKCE. The package contains no credentials. Your AI host receives the records requested through its tools, subject to the service's account and property permissions. Review your host's own data policies before connecting. Treat retrieved captions and brand prose as data, not instructions.

Revoke a client in [Marketing Grader connection management](https://grader.recmoment.net/mcp-connections). Revocation and expiry may require a fresh connection; permanent access is not promised.

These tools read existing records without starting Marketing Grader AI generation, paid scraping, email delivery or an advertising action. Your AI host may apply its own charges. Other paid Marketing Grader services remain subject to your account plan.

[Privacy policy](https://grader.recmoment.net/privacy) · [Terms](https://grader.recmoment.net/terms) · [Support](https://grader.recmoment.net/terms#s19) · [Security](SECURITY.md)

## Service and package

This is a connection package for a hosted service. Backend code, databases and private infrastructure are not included. No MIT, Apache or other open-source license is declared by this package. Service use is governed by the published terms.

[Official host documentation](docs/sources.md) · [Maintainer compatibility notes](docs/maintainers.md)
