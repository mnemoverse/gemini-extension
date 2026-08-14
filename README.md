# Mnemoverse Memory for Gemini CLI

Persistent memory for AI agents, shared across tools. One account gives Gemini CLI the same long-term memory it has in Claude Code, Cursor, VS Code, and any other MCP client: write a memory in one tool, recall it in another.

## Install

```
gemini extensions install https://github.com/mnemoverse/gemini-extension
```

## First run: sign in once, no API key

The server at `https://mcp.mnemoverse.com/mcp` uses OAuth 2.1 with PKCE. On first use Gemini CLI opens a browser sign-in on a localhost callback; sign in to your Mnemoverse account (free tier at [console.mnemoverse.com](https://console.mnemoverse.com?utm_source=github&utm_medium=readme&utm_campaign=gemini-extension), no credit card) and grant the requested scopes, which include `memory:read` and `memory:write`. There is no API key to paste, and access can be revoked at any time from the console.

## What you get

Ten tools from the remote server: `memory_read`, `memory_write`, `memory_list_recent`, `memory_stats`, `memory_feedback`, four shared-room tools, and `vault_list` (aliases only, values are never returned). The two delete tools available in the [local package](https://mnemoverse.com/docs/api/mcp-server) are deliberately not exposed over the remote connector, so a one-time sign-in can never wipe memory.

The bundled `GEMINI.md` adds the discipline that makes connected memory actually get used: recall before acting, save durable decisions and corrections, close superseded facts instead of overwriting them. These rules are backend-neutral and are also published standalone as the CC0 [agent-memory-discipline](https://github.com/mnemoverse/agent-memory-discipline) skill.

## What gets stored, and what does not

Only what you or the agent explicitly save through the memory tools: single facts, decisions, corrections. It does not record conversations and does not read your chat history. Privacy policy: [mnemoverse.com/privacy](https://mnemoverse.com/privacy).

## Troubleshooting

- No browser window on first use: check the server status with `/mcp` inside Gemini CLI, then retry a memory call.
- `401` after it used to work: the token expired; the next call normally refreshes it. If not, remove and re-install the extension to re-run sign-in.
- More: [docs](https://mnemoverse.com/docs/api/remote-mcp-server).

## Support

Issues in this repository, or [helloworld@uinside.org](mailto:helloworld@uinside.org).

## License

MIT.
