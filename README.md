# Betting Tips AI MCP

Read-only football and cricket tips for Claude, Cursor, VS Code, Grok, and other MCP clients.

This public repository holds documentation, a logo, and the official MCP registry manifest for the remote Betting Tips AI MCP server. The server itself is hosted at [bettingtipsai.com](https://bettingtipsai.com). There is no local package to install.

- MCP URL: `https://bettingtipsai.com/api/mcp`
- Transport: Streamable HTTP
- Registry name: `com.collatiomedia/bettingtipsai` (version 1.0.2)
- Docs: https://bettingtipsai.com/docs

## Authentication and limits

OAuth 2.1 sign-in with a free [Betting Tips AI](https://bettingtipsai.com) account is required. Use the same account as the website: email code, Google, or Apple. There is no password. Clients that support OAuth and dynamic client registration will open a browser so you can sign in and approve the `tips:read` scope.

Unauthenticated requests to the MCP endpoint return HTTP 401.

Each account can make 30 requests per minute and 500 requests per day. Going over the limit returns HTTP 429.

## Tools

All tools are read-only. They return tips already published on bettingtipsai.com.

| Tool | What it returns |
| --- | --- |
| `list_today_tips` | Upcoming published picks, with confidence, kickoff time, and a link to the tip page. Some clients can render these as in-chat cards. |
| `get_match_tip` | The tip and a short analysis for one fixture, looked up by match slug. |
| `list_leagues` | Leagues that have tip pages, with hub URLs on bettingtipsai.com only. |
| `list_recent_results` | Recently settled hit or miss outcomes, for track-record questions. Past results do not guarantee future performance. |

The server does not place bets, open bookmaker accounts, take payments, show ads, or return affiliate or visit links. It is not a sportsbook.

## Install

Add the remote URL in your client, then sign in when the browser opens.

### Claude

In Claude, open Settings, then Connectors, and add a custom connector with this URL:

```
https://bettingtipsai.com/api/mcp
```

Approve access in the browser when prompted.

### Cursor

Add a project or user MCP config. A project example lives in this repo at [`.cursor/mcp.json`](.cursor/mcp.json):

```json
{
  "mcpServers": {
    "bettingtipsai": {
      "url": "https://bettingtipsai.com/api/mcp"
    }
  }
}
```

You can also put the same entry in `~/.cursor/mcp.json` to use it in every project. After saving, connect the server in Cursor Settings, MCP, and sign in.

### VS Code

Run **MCP: Add Server** from the Command Palette and choose an HTTP server, or add this to `.vscode/mcp.json`:

```json
{
  "servers": {
    "bettingtipsai": {
      "type": "http",
      "url": "https://bettingtipsai.com/api/mcp"
    }
  }
}
```

Sign in when VS Code opens the Betting Tips AI authorization page.

### Gemini CLI

Install the extension from this repository:

```
gemini extensions install https://github.com/collatiomedia/bettingtipsai-mcp
```

A free [bettingtipsai.com](https://bettingtipsai.com) account and OAuth sign-in are required. Sign in when the CLI opens a browser. Content is for users aged 18 or over. Please gamble responsibly.

The manifest is [`gemini-extension.json`](gemini-extension.json). Context for the model is in [`GEMINI.md`](GEMINI.md).

### Grok

In Grok or Grok Bot, add a custom MCP server with this URL:

```
https://bettingtipsai.com/api/mcp
```

The browser opens the Betting Tips AI sign-in page. Approve the `tips:read` scope, then try questions such as "What football tips are upcoming today?" or "Which leagues have tips?"

## Responsible gambling

Content is for users aged 18 or over. Predictions are informational only. They are not guarantees, financial advice, or an instruction to place a bet. Gambling can be addictive. Please play responsibly.

- Responsible gambling: https://bettingtipsai.com/responsible-gambling
- Privacy: https://bettingtipsai.com/privacy-policy
- Terms: https://bettingtipsai.com/terms
- Support: https://bettingtipsai.com/support

## Manifest and logo

- [`server.json`](server.json) is the Official MCP Registry manifest (remote Streamable HTTP) for `com.collatiomedia/bettingtipsai` version 1.0.2.
- [`gemini-extension.json`](gemini-extension.json) is the Gemini CLI extension manifest for the same remote server.
- [`GEMINI.md`](GEMINI.md) is the extension context file (account, OAuth, and 18+ / responsible gambling note).
- [`logo-512.png`](logo-512.png) is a 512x512 PNG copy of the live logo at https://bettingtipsai.com/brand/logo-512.png

## License

The contents of this repository are licensed under the [MIT License](LICENSE).
