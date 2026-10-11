---
name: acquisity-campaign-results
description: "Check how Acquisity cold email campaigns are doing: sends, opens, replies, which leads replied, and what to change next. Use when someone asks how their outreach is going or who replied."
---

# Report on Acquisity cold email results

## Connect

Use the Acquisity MCP server at https://api.acquisity.ai/mcp (Streamable HTTP). The person signs in with OAuth and picks one workspace and Read-only or Full access. In Claude Code: `claude mcp add --transport http acquisity https://api.acquisity.ai/mcp`.

Start every session with `list_workspaces` and pass its `id` as `workspaceId` to every other tool.

## Steps

1. `list_campaigns` (active campaigns by default) and pick the ones the person cares about.
2. `get_campaign_metrics` for each: sent, opened, replied. Report reply rate, not just counts.
3. `list_campaign_leads` filtered by status to find who replied, then `get_campaign_lead` for details.
4. For a full list, `export_campaign_leads` returns CSV pages.
5. To hear about new positive replies as they happen, `create_webhook` with an HTTPS endpoint (needs `webhooks:write`; store the secret it returns once).

## Reading the numbers

- Cold Email Agent tests message variants and judges them after about 100 sends each. Don't call a variant a winner before that.
- Typical healthy reply rates by method: Podcast 2%+, Interview 1.5%+, AI Business Audit 1%+, Direct 0.8%+.
- AI SDR answers replies and books calls automatically, so check the CRM before following up by hand.

## Changing a campaign

- `pause_campaign` stops sending. Ask first.
- To try a new angle, `duplicate_campaign` into a draft, change it, then follow the launch steps in the acquisity-cold-email-campaign skill.
