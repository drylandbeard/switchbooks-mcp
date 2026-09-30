# Switchbooks

Connect Cursor and Grok Bot to your Switchbooks accounting data. Ask about reports, search transactions, and inspect accounts, categories, payees, and rules.

Choose read-only access or authorize undoable bookkeeping changes on the Switchbooks consent screen. Read-only access covers reports, transactions, accounts, categories, payees, and other accounting information. Selecting an active company changes only the connection's company selection.

## Connect

You need a Switchbooks account with access to at least one company. A company's accounting tools require an active trial or subscription; authorizing or disconnecting a connection does not.

1. After installing the plugin, open its connection settings. In Grok Bot, use **Marketplace → Your plugins** to find installed plugins.
2. Enable the Switchbooks connection and complete the browser sign-in when prompted.
3. Review the Switchbooks consent screen. To keep the connection read-only, clear **Let it make changes to the books** before choosing **Allow access**. Leave it selected only if you want to authorize bookkeeping changes, then choose **Allow access and changes**.
4. Ask the assistant to list your Switchbooks companies and select the company you want to work with.

The hosted server is `https://app.switchbooks.ai/api/mcp`. It uses Streamable HTTP with OAuth, dynamic client registration, and PKCE. No API key, shared secret, or local server is required.

The consent checkbox initially follows the scopes requested by your client, so review it each time you connect. Read-only access uses `switchbooks.read`; allowing changes also grants `switchbooks.write`. Existing read-only connections stay read-only until you reconnect and authorize changes.

With write permission, the connector can make changes that Switchbooks can undo, such as posting or splitting transactions, matching transfers, creating or editing journal entries, changing categories, payees or rules, and completing a previewed reconciliation. No connection can connect or sync banks, send email or invitations, share reports, import files, merge bank accounts, delete files, or remove teammates.

## Try it

- “List my Switchbooks companies.”
- “Use [company name] and show last month's profit and loss.”
- “Find transactions paid to [payee] last quarter.”
- “Show the accounts and categories for this company.”

The connector exposes `list_companies` and `set_company`. Other tools use the selected company. A single accessible company is selected automatically; accounts with multiple companies must choose one. Access is checked for every tool call.

## Disconnect

In Switchbooks, open **Settings → MCP → Connected apps**, find the connection, and choose **Disconnect**. This immediately revokes both its access and refresh tokens. You can reconnect later by authorizing access again.

## Local Cursor setup

To test the hosted connector before marketplace installation, merge the `mcpServers.switchbooks` entry from this package's `mcp.json` into your project's `.cursor/mcp.json` or your user's `~/.cursor/mcp.json`. Preserve any existing server entries, then enable Switchbooks and sign in through Cursor.

See [Cursor MCP setup](https://cursor.com/docs/mcp) and [Grok Bot plugin settings](https://docs.x.ai/grok-bot/settings-and-notifications).

## Support

Contact [ryland@switchbooks.ai](mailto:ryland@switchbooks.ai).

[Switchbooks](https://switchbooks.ai) · [Privacy policy](https://switchbooks.ai/privacy) · [Terms of service](https://switchbooks.ai/terms)
