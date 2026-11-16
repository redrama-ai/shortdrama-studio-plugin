# Security

Please report security vulnerabilities in this plugin or in the ShortDrama Studio service privately, by email to [support@shortdrama.studio](mailto:support@shortdrama.studio) with "Security" in the subject. Do not open a public issue for them.

Include what you found, the steps to reproduce it and its impact. We will reply, and keep you updated until the issue is fixed.

## How the plugin connects

- The plugin only points your agent at the hosted MCP server, `https://mcp.shortdrama.studio/mcp`. It contains no code that runs on your machine and no credentials.
- Sign-in is OAuth 2.1 with PKCE. Access tokens are bound to the MCP server, expire after an hour and refresh tokens rotate.
- Each connection gets only the permissions you approve, and a daily credit cap. You can disconnect it at any time in **Settings → MCP & Agents** on shortdrama.studio.
