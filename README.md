# FeedTLDR plugin

Use your FeedTLDR data in Claude and Codex with three ready-made, read-only skills.

The plugin connects to the hosted FeedTLDR MCP server. It asks you to sign in to FeedTLDR and grants only the `feed:read` permission. It cannot add or remove followed accounts, change settings, or write data.

## Included skills

- `/feed-tldr:daily-brief` creates a short briefing from your latest summary.
- `/feed-tldr:deep-dive` investigates a topic across recent posts and keeps links to the original X posts.
- `/feed-tldr:understand-my-feed` explains the data, prompt, model, account share, source links, and limits behind your latest summary.

The plugin also includes the FeedTLDR MCP connector and its read-only tools:

- `feed-tldr:get-latest-summary`
- `feed-tldr:get-feed-posts`
- `feed-tldr:get-tracked-accounts`
- `feed-tldr:get-summary-details`

## Install in Claude Code

Run these commands:

```bash
claude plugin marketplace add PabloWiedemann/feed-tldr-plugin
claude plugin install feed-tldr@feed-tldr
```

Start a new Claude Code session. The first time a skill needs FeedTLDR, open `/mcp` and complete the FeedTLDR sign-in if Claude asks you to connect.

## Install in Claude web, Desktop, or Cowork

1. Open the latest [GitHub release](https://github.com/PabloWiedemann/feed-tldr-plugin/releases/latest).
2. Download `feed-tldr-plugin-v0.2.1.zip`.
3. In Claude, open **Customize**, then **Plugins**.
4. Choose the option to upload a custom plugin and select the ZIP file.
5. Start a new chat, type `/`, and choose a `feed-tldr:` skill.
6. Sign in to FeedTLDR when Claude asks you to connect.

Custom plugin uploads are available on Claude paid plans. Your workspace administrator may need to allow the plugin or connector.

## Install in Codex

Run these commands:

```bash
codex plugin marketplace add PabloWiedemann/feed-tldr-plugin
codex plugin add feed-tldr@feed-tldr
```

Restart Codex after installing. The three skills appear with names that start with `feed-tldr:`. Sign in to FeedTLDR when the connector asks you to authorize access.

## ChatGPT

The same FeedTLDR MCP server works as a custom ChatGPT app. A public GitHub plugin does not automatically put FeedTLDR in ChatGPT's Plugins Directory. FeedTLDR must also pass OpenAI's app review before everyone can install it from that directory.

Until then, supported ChatGPT users can add `https://api.feedtldr.com/mcp` as a custom app. That gives ChatGPT the MCP tools, but it does not automatically install the three skills from this repository.

## Quick QA

After installation:

1. Type `/feed-tldr:daily-brief`. Expect a short brief based on your latest saved summary.
2. Type `/feed-tldr:deep-dive` and ask about a recent topic. Expect evidence links to the original X posts.
3. Type `/feed-tldr:understand-my-feed`. Expect the source, post count, covered period, account share, prompt, model, and known limits for a recent summary.

If the last skill says provenance is unavailable, generate a new FeedTLDR summary and try again. Older summaries created before provenance tracking do not contain those details.

## Switch FeedTLDR accounts

The plugin and the FeedTLDR connection are separate. You can keep the plugin installed and reconnect the MCP connector:

- In Claude Code, open `/mcp`, select FeedTLDR, clear its authentication, and sign in again.
- In Claude or ChatGPT settings, disconnect the FeedTLDR app or connector, then connect it again with the account you want.

## Data and privacy

FeedTLDR currently reads X posts only. Reddit and other sources are not included yet. The deep-dive tool returns at most 200 posts in one call.

- [Privacy policy](https://feedtldr.com/privacy)
- [Terms of use](https://feedtldr.com/terms)
- [FeedTLDR](https://feedtldr.com)

## Development

The distributable plugin is in [`plugins/feed-tldr`](./plugins/feed-tldr).

Validate it with:

```bash
claude plugin validate --strict plugins/feed-tldr
uv run --with pyyaml python /path/to/plugin-creator/scripts/validate_plugin.py plugins/feed-tldr
```
