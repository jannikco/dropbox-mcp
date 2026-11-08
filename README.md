# Dropbox MCP server

Confirm the account, list a chosen folder, and continue using returned cursors to create a document inventory.

A direct-provider MCP server with useful local execution. No PipMCP account is required for local use. Provider API access and any provider charges are your responsibility.

## Quick start

Requires Node.js22+. Clone this repository, then run:

```sh
npm ci --ignore-scripts
npm test
npm start
```

The default command inspects the tools offline. Configure your own credentials in your environment:

- `DROPBOX_ACCESS_TOKEN`

For local OAuth, use node local-auth/cli.mjs login ./connector.json with your own provider app; see AUTH.md. Your tokens remain in the native OS credential store.

Credential help: https://www.dropbox.com/developers/documentation/http/documentation

## Execute a real read

Replace example record IDs with records you are authorized to access.

```sh
npm start -- --call get_current_account '{}'
```

## Use with an MCP client

Launch `node /absolute/path/dropbox-mcp/server.mjs` using stdio transport; pass credentials through the client environment. Stdout is reserved for JSON-RPC.

## Tools

| Tool | Effect | Purpose |
| --- | --- | --- |
| get_current_account | Read | Read the authorized Dropbox account. |
| list_folder | Read | Read folder entries using a user-authorized path. Empty path lists the root. |
| continue_folder_listing | Read | Read the next folder page using a cursor returned by list_folder. |

## Concrete workflow

Confirm the account, list a chosen folder, and continue using returned cursors to create a document inventory.

1. get_current_account
2. list_folder
3. continue_folder_listing

## Optional writes

Writes are disabled by default. Set CONNECTOR_ALLOW_WRITES=true and supply `_approval: {approved:true,idempotencyKey:"unique-request-id"}` on the specific call. Do not reuse a key for a different request. Uncertain outcomes are never automatically replayed; inspect the provider before another attempt.

## Capability evidence

Local: **Tested — HTTP fixtures and real stdio tools/call**. Managed: **Documented**. Provider authentication and live operations have not been established by these fixture tests. Evidence applies per operation and execution mode; setup discovery does not imply provider execution.

## Managed production

[Activate with PipMCP](https://pipmcp.com/github/start?app=dropbox&integration=dropbox-mcp&utm_source=github&utm_campaign=github-dropbox-mcp&utm_content=readme) when you want the hosted service.  Local credentials are not uploaded by this code. Review provider permissions in the managed onboarding. [Directory and related projects](https://jannikco.github.io/pipmcp-connectors/integrations/dropbox/).

## Provenance and maintenance

- https://www.dropbox.com/developers/documentation/http/documentation
- https://developers.dropbox.com/oauth-guide
- https://www.dropbox.com/developers/documentation/http/documentation#files-list_folder

Maintainer:jannikco. MIT license for this code. See connector.json for selected operations and integration.json for evidence. Runtime dependencies retain their own licenses. Report sensitive issues through https://pipmcp.com/contact; do not post credentials or customer data in public issues.
