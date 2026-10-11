# Using Acquisity from a coding agent

- Connect the MCP server at https://api.acquisity.ai/mcp and call `list_workspaces` first; every other tool needs its `workspaceId`.
- Never launch a campaign, buy leads or add leads to an active campaign without the person's explicit go-ahead. Launching sends real email and lead search spends credits.
- Run `validate_campaign` and fix every blocker before `launch_campaign`.
- Reuse an `idempotencyKey` only to retry the exact same write.
- Read the skills in `skills/` for the full step-by-step flows.
