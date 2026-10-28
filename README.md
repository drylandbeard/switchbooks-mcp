# Switchbooks

Connect Cursor, Grok Bot, and Grok Build to your Switchbooks accounting data. Ask about reports, search transactions, and inspect accounts, categories, payees, and rules.

Choose read-only access or authorize bookkeeping changes on the Switchbooks consent screen. Read-only access covers reports, transactions, accounts, categories, payees, and other accounting information. Selecting an active company changes only the connection's company selection.

## Connect

You need a Switchbooks account with access to at least one company. A company's accounting tools require an active trial or subscription; authorizing or disconnecting a connection does not.

1. After installing the plugin, open its connection settings. In Grok Bot, use **Marketplace → Your plugins** to find installed plugins.
2. Enable the Switchbooks connection and complete the browser sign-in when prompted.
3. Review the Switchbooks consent screen. To keep the connection read-only, clear **Let it make changes to the books** before choosing **Allow access**. Leave it selected only if you want to authorize bookkeeping changes, then choose **Allow access and changes**.
4. Ask the assistant to list your Switchbooks companies and select the company you want to work with.

The hosted server is `https://app.switchbooks.ai/api/mcp`. It uses Streamable HTTP with OAuth, dynamic client registration, and PKCE. No API key, shared secret, or local server is required.

Review the “Allow bookkeeping changes” checkbox each time you connect; uncheck it for read-only access. Read-only access uses `switchbooks.read`; allowing changes also grants `switchbooks.write`. Existing read-only connections stay read-only until you reconnect and authorize changes.

With write permission, ordinary MCP connections such as Cursor and Grok Bot can post or split transactions, match transfers, create or edit journal entries, change categories, payees or rules, and complete a previewed reconciliation. They can also connect a bank through the user's Plaid sign-in, sync connected banks, upload and import files, email the user or teammates, merge bank accounts, and delete files. Many bookkeeping changes can be undone, but some supported actions are irreversible and email reaches other people. Review the requested action before allowing it.

Read-only connections cannot perform these writes. No MCP connection can invite or remove teammates, change access roles, cancel invitations, or create shared report links. Those actions stay in the Switchbooks app.

ChatGPT and legacy OpenAI plugin connections use reviewed subsets of the full MCP catalog. On the ChatGPT-specific endpoint, bank sign-in and completion, file imports, owner-request writes, bank sync, email, bank-account merges and file deletion stay in the app.

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

See [Cursor MCP setup](https://cursor.com/docs/mcp) and [Grok Bot plugin settings](https://docs.x.ai/grok-bot/settings-and-notifications). In Grok Build, install from the marketplace with `grok plugin install switchbooks`; the `.mcp.json` at the plugin root points at the same hosted server.

## Support

Contact [ryland@switchbooks.ai](mailto:ryland@switchbooks.ai).

[Switchbooks](https://switchbooks.ai) · [Privacy policy](https://switchbooks.ai/privacy) · [Terms of service](https://switchbooks.ai/terms)
