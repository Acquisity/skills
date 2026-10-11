# Acquisity skills and plugin for AI agents

Let your AI agent run B2B cold email for you with [Acquisity](https://www.acquisity.ai): find verified leads, write and launch campaigns, see who replied and keep the CRM up to date.

This repo is an [Agent Plugins](https://agent-plugins.org) plugin and a Claude Code plugin marketplace. It bundles:

- The Acquisity MCP server (https://api.acquisity.ai/mcp). You sign in with OAuth and choose one workspace and Read-only or Full access.
- The `acquisity-cold-email-campaign` skill: Plan, build, check and launch a B2B cold email campaign with Acquisity Cold Email Agent over MCP: find verified leads, write the sequence, validate and launch. Use when someone wants outbound or cold email sent for their business.
- The `acquisity-campaign-results` skill: Check how Acquisity cold email campaigns are doing: sends, opens, replies, which leads replied, and what to change next. Use when someone asks how their outreach is going or who replied.

## Install

Claude Code:

```
/plugin marketplace add Acquisity/skills
/plugin install acquisity@acquisity
```

Any agent that supports Agent Skills:

```bash
npx skills add Acquisity/skills
```

Just the MCP server:

```bash
claude mcp add --transport http acquisity https://api.acquisity.ai/mcp
```

## Learn more

- [Developers and AI agents](https://www.acquisity.ai/developers.md)
- [How agents sign in](https://www.acquisity.ai/auth.md)
- [Pricing](https://www.acquisity.ai/pricing.md)
- [Developer docs](https://developer.acquisity.ai)

This repo is generated from the Acquisity website source. Open an issue or email support@acquisity.ai with changes.
