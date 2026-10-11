---
name: acquisity-cold-email-campaign
description: "Plan, build, check and launch a B2B cold email campaign with Acquisity Cold Email Agent over MCP: find verified leads, write the sequence, validate and launch. Use when someone wants outbound or cold email sent for their business."
---

# Run a cold email campaign with Acquisity

## Connect

Use the Acquisity MCP server at https://api.acquisity.ai/mcp (Streamable HTTP). The person signs in with OAuth and picks one workspace and Read-only or Full access. In Claude Code: `claude mcp add --transport http acquisity https://api.acquisity.ai/mcp`.

Start every session with `list_workspaces` and pass its `id` as `workspaceId` to every other tool.

## Before you start, ask the person

1. Who they want to reach (industry, job titles, company size, location).
2. What they offer and the outcome it gives the buyer.
3. What a good reply looks like (a call, a demo, a reply with interest).

## Steps

1. `create_campaign` with a clear name. It creates a draft; nothing is sent.
2. Find leads:
   - `ai_search_campaign_leads` turns the brief into proposed filters. Show the person the filters and assumptions.
   - `preview_campaign_lead_search` with the agreed filters returns a count and a sample. Free.
   - Tell the person how many leads it found and that each verified lead costs about 1 credit. Only after they agree, call `search_campaign_leads` with a stable `idempotencyKey`.
   - If they have their own list, map the CSV columns and call `add_campaign_leads` in batches of up to 1,000 (also free).
3. `set_campaign_sequence` to attach or generate the email steps and variants. Show the person the emails before launch. Use `{{variableName}}` for custom fields.
4. `validate_campaign` and fix every blocker it reports (usually sending inboxes, leads or sequence). Inboxes are bought and warmed up in the app: https://app.acquisity.ai/docs/cold-email-agent/email-accounts/buying-inboxes
5. Ask for an explicit "yes, launch it", then call `launch_campaign`. Launching sends real email.

## Rules

- Never launch, buy leads or add leads to an active campaign without the person's go-ahead.
- Writes run as operations. The tools wait for them; if one returns still running, poll `get_operation`.
- `update_campaign` needs `ifMatch` set to the campaign's latest `updatedAt` from `get_campaign`.
- Reuse an `idempotencyKey` only to retry the exact same request.
