# Switchbooks

Connect Cursor and Grok Bot to your Switchbooks accounting data. Ask about reports, search transactions, and inspect accounts, categories, payees, and rules.

This connection is read-only for your books. It cannot post transactions, edit or delete accounting records, or send invitations. Selecting an active company changes only the connection's company selection.

## Connect

You need a Switchbooks account with access to at least one company.

1. After installing the plugin, open its connection settings. In Grok Bot, use **Marketplace → Your plugins** to find installed plugins.
2. Enable the Switchbooks connection and complete the browser sign-in when prompted.
3. Review and approve the Switchbooks consent screen. The requested scope is `switchbooks.read`.
4. Ask the assistant to list your Switchbooks companies and select the company you want to work with.

The hosted server is `https://app.switchbooks.ai/api/mcp`. It uses Streamable HTTP with OAuth, dynamic client registration, and PKCE. No API key, shared secret, or local server is required.

## Try it

- “List my Switchbooks companies.”
- “Use [company name] and show last month's profit and loss.”
- “Find transactions paid to [payee] last quarter.”
- “Show the accounts and categories for this company.”

The connector exposes `list_companies` and `set_company`. Other tools use the selected company. A single accessible company is selected automatically; accounts with multiple companies must choose one. Access is checked for every tool call.

## Local Cursor setup

To test the hosted connector before marketplace installation, merge the `mcpServers.switchbooks` entry from this package's `mcp.json` into your project's `.cursor/mcp.json` or your user's `~/.cursor/mcp.json`. Preserve any existing server entries, then enable Switchbooks and sign in through Cursor.

See [Cursor MCP setup](https://cursor.com/docs/mcp) and [Grok Bot plugin settings](https://docs.x.ai/grok-bot/settings-and-notifications).

## Support

Contact [ryland@switchbooks.ai](mailto:ryland@switchbooks.ai).

[Switchbooks](https://switchbooks.ai) · [Privacy policy](https://switchbooks.ai/privacy) · [Terms of service](https://switchbooks.ai/terms)
