# ShortDrama Studio plugin

<img src="assets/logo.png" alt="ShortDrama Studio" width="96" height="96" align="right">

Write and produce vertical AI short dramas from your AI agent. This plugin connects your agent to the [ShortDrama Studio](https://shortdrama.studio) MCP server, so it can create a drama, write its story bible, characters, episode outlines and scene-by-scene scripts, check them, and, if you allow it, generate the pictures, video, voices and music and render finished episodes. Everything lands in your own ShortDrama Studio account, where you can keep editing it yourself.

**MCP server:** `https://mcp.shortdrama.studio/mcp` (Streamable HTTP, OAuth 2.1)

This repository holds only the plugin manifests and docs. The server is hosted by ShortDrama Studio; nothing runs on your machine and no secrets are stored here.

## What it costs

| | |
|---|---|
| **Free** | Connecting, and all the writing: dramas, story bibles, characters, locations, episode outlines, scene-by-scene scripts, the script checker, skills, import and export. Your agent does the thinking with its own model, so writing never spends ShortDrama Studio credits. |
| **Credits** | Only production: character portraits, location and prop images, keyframes, scene videos, music, subtitle timing and episode renders. New accounts get free welcome credits; more are on the [pricing page](https://shortdrama.studio/pricing). |

Your agent can call `estimate_cost` before it spends anything, and every connection has a daily credit cap that you choose.

## Install

### Cursor

Install **ShortDrama Studio** from the Cursor Marketplace. To add it by hand instead, put this in `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "shortdrama": { "url": "https://mcp.shortdrama.studio/mcp" } } }
```

### Grok

Add **ShortDrama Studio** from the Grok Bot marketplace.

### Claude Code

```
/plugin marketplace add redrama-ai/shortdrama-studio-plugin
/plugin install shortdrama-studio@shortdrama-studio
```

Then run `/mcp`, choose **shortdrama** and sign in.

### Any other MCP client

Add `https://mcp.shortdrama.studio/mcp` as a remote MCP server (Streamable HTTP). Clients that support OAuth sign in through the browser. Clients that can only send a header can use an access token instead: see the [setup guide](https://shortdrama.studio/mcp).

## Sign in and permissions

The first time your agent uses a tool, your browser opens shortdrama.studio. Sign in (or create a free account) and approve the connection. You choose what the agent may do:

| Permission | What it allows |
|---|---|
| Read your dramas | Stories, characters, episodes, scripts, catalogs and your credit balance. Always on. |
| Write and edit your dramas | Create dramas and change stories, characters, episodes and scripts. Every change is kept in history and can be undone. |
| Read skills / Save skills and presets | Use the official skills and your own; save new skills and custom presets. |
| Spend credits on generation | Generate images, voice and video and render episodes, within your daily cap. Granted only when you approve it. |
| See credit usage | Your credit history and usage by connection. |

You set a daily credit cap for the connection on the same screen, and you can disconnect it any time in **Settings → MCP & Agents**; access ends at once. The agent only ever sees your own workspace.

## Try it

Ask your agent, for example:

- "Create a 10-episode CEO romance on ShortDrama Studio, write its story bible and cast it."
- "Write episode 1 scene by scene, then lint the drama and fix what it finds."
- "Estimate what producing episode 1 would cost." Then, if you allowed generation: "Generate the lead's portrait and the first scene's video."
- "Export the script as Fountain."

## What your agent gets

- **The whole story in one call** (`get_drama_context`), so episode 7 is written knowing episodes 1–6.
- **Every valid option** (`get_drama_spec`, `get_catalog`): formats, genres, tropes, visual styles, shots and languages, so it never guesses.
- **Skills**: official playbooks for the workflow, vertical-drama storycraft, genres, visual prompting and character consistency, served by the server itself, so there is nothing to install.
- **A script checker** (`lint_drama`) for hooks, cliffhangers, pacing and dialogue, with a fix for each finding.
- **Production**: portraits, location plates, keyframes and lip-synced scene videos, a fixed voice per character, episode music and the rendered MP4 with subtitles.
- **Import and export** as JSON ([`shortdrama.script.v1`](https://shortdrama.studio/shortdrama-script-format)) or Fountain.
- **Undo**: every change an agent makes is kept in the drama's history with the agent's name on it.

Agents that choose tools better from a shorter list can use `https://mcp.shortdrama.studio/mcp/writer` (story only) or `https://mcp.shortdrama.studio/mcp/producer` (story reading and production). The full tool reference, with each tool's permission and input schema, is at [api.shortdrama.studio/v2/schemas/tools.json](https://api.shortdrama.studio/v2/schemas/tools.json).

## Privacy, content and terms

- **Your data:** what the agent writes and generates belongs to your account. We do not sell your personal data, and we do not use your content to train our own AI models. To generate images, voices and video, the relevant parts of your content are sent to the AI model providers that power each feature. Details: [Privacy Policy](https://shortdrama.studio/privacy).
- **What you can make:** original stories rated up to 16+. No NSFW content, no deepfakes or face swaps, and no voice cloning without consent. Details: [Content Policy](https://shortdrama.studio/content-policy).
- **Ownership and use:** [Creative License](https://shortdrama.studio/creative-license) and [Terms of Service](https://shortdrama.studio/terms).

## Support

- Setup guide: [shortdrama.studio/mcp](https://shortdrama.studio/mcp)
- Email: [support@shortdrama.studio](mailto:support@shortdrama.studio)
- Plugin issues: [GitHub issues](https://github.com/redrama-ai/shortdrama-studio-plugin/issues)
- Security reports: see [SECURITY.md](SECURITY.md)

ShortDrama Studio is built by PT Redrama Inovasi Global, Jakarta, Indonesia.

## License

The files in this repository are released under the [MIT License](LICENSE). Use of the ShortDrama Studio service is governed by its [Terms of Service](https://shortdrama.studio/terms).
