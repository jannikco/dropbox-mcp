# Dropbox MCP setup and connection checker

Generate Dropbox MCP client configuration, inspect available tools and validate hosted endpoint access through PipMCP.

Maintainer: jannikco · License: MIT · Verification: **mock-only**

## Quick start

Requires Node.js 22 or later.

```sh
npm ci
npm test
npm start
```

The default example runs locally without credentials and makes no external changes. Verification status describes recorded evidence; local configuration tests do not establish that provider authentication or execution works.

## Connect dropbox

[Create or sign in to PipMCP](https://pipmcp.com/register?app=dropbox&utm_source=github&utm_campaign=github-dropbox-mcp) and select the integration. Connect your authorized provider account and copy its hosted MCP endpoint. Set PIPMCP_ENDPOINT and, if required, PIPMCP_TOKEN in your environment. Run npm start to produce client configuration; run npm start -- --live for a read-only connection check. Provider app presence is catalog evidence, not live verification.

## Managed service

[Continue with PipMCP](https://pipmcp.com/register?app=dropbox&utm_source=github&utm_campaign=github-dropbox-mcp). This repository is maintained by the integration team and does not imply endorsement by LinkedIn or other providers.

## Provenance and support

Source revision: e54af4c3101090e778c85016b52e634c3ce5ae177b350e99e757b7d5815f2de9. The complete manifest is in integration.json; SHA256SUMS covers the reviewed artifact. Open a repository issue without credentials or personal data. See SECURITY.md for sensitive reports. No telemetry is sent by this code; signup links include explicit campaign parameters.

## Provider setup inventory

Run `npm start -- --setup` to inspect this app's recorded authentication requirements and setup links offline. Credentials are entered in PipMCP; this repository lists required field names only.

```json
{
  "type": "oauth2_authorization_code",
  "requiredCredentialFields": [
    "client_id",
    "client_secret",
    "owner_authorization"
  ],
  "requiredHeaderNames": [],
  "helpUrl": "https://developers.dropbox.com/oauth-guide",
  "tenantRequired": false,
  "accountParameterNames": []
}
```

Provider documentation: https://www.dropbox.com/developers/documentation/http/documentation
Provider website: https://www.dropbox.com/
