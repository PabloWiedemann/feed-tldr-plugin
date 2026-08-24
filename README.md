<p align="center">
  <img src="./plugins/feed-tldr/assets/feedTLDR_wordmark.svg" width="240" alt="FeedTLDR">
</p>

<br><br>

# FeedTLDR for AI agents

**Keep up with your social media feed without opening it.**

Turn the posts from accounts you follow into clear summaries. Explore any topic and see how each summary was made.

[Website](https://feedtldr.com) · [Privacy](https://feedtldr.com/privacy) · [Support](mailto:support@feedtldr.com)

[![Skills on skills.sh](https://skills.sh/b/pablowiedemann/feed-tldr-plugin)](https://skills.sh/pablowiedemann/feed-tldr-plugin)

FeedTLDR turns posts from the accounts you follow on X into a personal newsletter and clear summaries. These skills help your AI agent:

- Catch you up on the latest updates.
- Examine a topic across recent posts.
- Explain the sources and settings behind a summary.

The skills only read your FeedTLDR data. They cannot change your account, settings, or followed accounts.

## Install all skills

Run one command:

```bash
npx skills add PabloWiedemann/feed-tldr-plugin --skill '*' --global
```

This command installs all three skills for your AI agent. The skills stay available across your projects.

The [`skills` command](https://skills.sh) supports Claude Code, Codex, Cursor, and many other AI agents.

## Connect your FeedTLDR account

The skills need a connection to your FeedTLDR account. Add the connection once, then sign in.

### Claude Code

```bash
claude mcp add --transport http --scope user feed-tldr https://api.feedtldr.com/mcp
claude mcp login feed-tldr
```

### Codex

```bash
codex mcp add feed-tldr --url https://api.feedtldr.com/mcp
codex mcp login feed-tldr
```

For another agent, add this remote MCP server in its connector settings:

```text
https://api.feedtldr.com/mcp
```

FeedTLDR asks you to approve read-only access during sign-in.

## Install one skill

Install only the skills that you want.

### Daily brief

Create a short, organized brief from your latest FeedTLDR summary.

```bash
npx skills add PabloWiedemann/feed-tldr-plugin --skill daily-brief --global
```

### Deep dive

Examine a topic across recent posts and keep links to the original X posts.

```bash
npx skills add PabloWiedemann/feed-tldr-plugin --skill deep-dive --global
```

### Understand my feed

See which posts, accounts, prompt, model, and limits shaped your latest summary.

```bash
npx skills add PabloWiedemann/feed-tldr-plugin --skill understand-my-feed --global
```

## What each skill does

| Skill                          | Use it when you want to                | Example request                                                                   |
| ------------------------------ | -------------------------------------- | --------------------------------------------------------------------------------- |
| `feed-tldr:daily-brief`        | Catch up without opening social media  | “Give me a short brief from my latest FeedTLDR newsletter.”                       |
| `feed-tldr:deep-dive`          | Examine one topic across recent posts  | “What did the accounts I follow say about AI agents? Include the original posts.” |
| `feed-tldr:understand-my-feed` | Understand how FeedTLDR made a summary | “Explain how my latest summary was made and what it cannot include.”              |

Your agent can also find the right skill from a plain request. You do not need to remember the skill names.

## Install the full plugin

The full plugin includes the three skills and the FeedTLDR connector. Use this option for the native plugin experience.

### Claude Code

```bash
claude plugin marketplace add PabloWiedemann/feed-tldr-plugin
claude plugin install feed-tldr@feed-tldr
```

Start a new Claude Code session. Open `/mcp` and sign in when Claude asks you to connect.

### Claude web, Desktop, or Cowork

1. Open the [latest GitHub release](https://github.com/PabloWiedemann/feed-tldr-plugin/releases/latest).
2. Download the plugin ZIP file.
3. In Claude, open **Customize**, then **Plugins**.
4. Upload the ZIP file.
5. Start a new chat and choose a skill that starts with `feed-tldr:`.
6. Sign in to FeedTLDR when Claude asks you to connect.

Custom plugin uploads require a paid Claude plan. A workspace administrator can also restrict plugins or connectors.

### Codex

```bash
codex plugin marketplace add PabloWiedemann/feed-tldr-plugin
codex plugin add feed-tldr@feed-tldr
```

Restart Codex after installation. Sign in when the FeedTLDR connector asks for access.

## ChatGPT

ChatGPT users can add the FeedTLDR MCP server as a custom app:

```text
https://api.feedtldr.com/mcp
```

This connection provides the FeedTLDR tools. It does not install the three skills from this repository.

## Make sure that the installation works

Try these requests:

1. “Give me a brief from my latest FeedTLDR summary.”
2. “Examine a recent topic and include links to the original posts.”
3. “Explain how my latest FeedTLDR summary was made.”

The first request returns a short brief. The second request includes evidence from recent posts. The third request explains the source data and limits.

If summary details are unavailable, generate a new FeedTLDR summary and try again. Older summaries do not contain the same level of detail.

## Switch FeedTLDR accounts

You can keep the skills installed when you change accounts.

- Claude Code: Run `claude mcp logout feed-tldr`, then `claude mcp login feed-tldr`.
- Codex: Run `codex mcp logout feed-tldr`, then `codex mcp login feed-tldr`.
- Claude or ChatGPT: Disconnect FeedTLDR in the connector settings, then connect the account that you want.

## Data and privacy

FeedTLDR currently reads X posts only. Reddit and other sources are not included yet.

The connector requests only the `feed:read` permission. It cannot add accounts, remove accounts, or change FeedTLDR settings.

The deep-dive tool returns no more than 200 posts in one request. Private, deleted, or unavailable posts cannot appear in the results.

- [Privacy policy](https://feedtldr.com/privacy)
- [Terms of use](https://feedtldr.com/terms)
- [Contact support](mailto:support@feedtldr.com)

## Development

The distributable plugin is in [`plugins/feed-tldr`](./plugins/feed-tldr).

Make sure that the plugin is valid before you publish a release:

```bash
claude plugin validate --strict plugins/feed-tldr
uv run --with pyyaml python /path/to/plugin-creator/scripts/validate_plugin.py plugins/feed-tldr
```

## License

This project uses the [MIT License](./LICENSE).
