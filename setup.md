# Setup — COE create skill

One-time per teammate. Skill folder: `coe-create-skill/`. Install with `make install` — [INSTALL.md](../INSTALL.md).

## Prerequisites

| Requirement | Notes |
|-------------|-------|
| Cursor Agent | New chat when running the skill |
| Slack MCP | Connected in Settings → MCP (same Slack the team already uses in Cursor) |
| Google Drive / Docs MCP | Same Google account that can open the COE template and quarter folders |
| Shared Drive access | Template + parent folder `Correction of Error` (same as today’s COE process) |

No Slack workspace admin. No Apps Script deploy. No bot invite for a custom `/coe` app.

The Slack MCP user must be **in** the incident channel (private channels). If history fails, join the channel in Slack and retry.

## How to invoke

```text
Run coe-create-skill.
Incident: IPESRE-202565
```

or channel `#ipesre-…`. Add `dry run` to preview only.

## Troubleshooting

| Symptom | Fix |
|---------|-----|
| Skill not followed | Say: `Use the coe-create-skill skill` |
| Slack history empty | Join the incident channel; confirm Slack MCP auth |
| Drive 403 | Ask for access to the COE shared drive / template |
| Slack post fails | Agent still created the Doc — paste the message it prints |
| Wrong quarter folder | Check initiation date (default today) and FY start = February |
