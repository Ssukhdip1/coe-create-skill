---
name: coe-create-skill
description: >-
  Create a Correction of Error Google Doc from an IPESRE incident: read Slack
  (and Jira if needed), copy the COE template, fill title/Jira/env/owners/dates,
  file it in the FY quarter Drive folder, and post the standard Slack
  announcement. Use when the user asks to create a COE, run coe-create-skill,
  or start a COE document from an incident channel or Jira key.
---

# COE Create Skill

Create the COE **Google Doc** and **Slack announcement** from Cursor. Teammates do not paste the incident thread. Slack slash-command admin is not required.

**Do not confuse with** [coe-admin-skill](../coe-admin-skill/SKILL.md) (Section 9 Jira after the COE is written).

## Step 0 — Team configuration

Read [team-config.md](team-config.md) first (template ID, parent folder, date rules, Slack message text, placeholders).

## Inputs

Collect **one** of:

1. **Incident Slack channel** — `#ipesre-123456-…` or channel ID
2. **Incident Jira key** — `IPESRE-123456` (or browse URL)

Optional: COE initiation date (Day 0). Default = **today** in the script timezone / local date the user is in. Optional: Service Owner Region (blank = global Thank You Days only). Optional: `dry run` (parse + dates + message only; no Drive copy, no Slack post).

If both channel and Jira are missing, ask for either. Do not invent an incident.

## Workflow

Follow [coe-create.md](coe-create.md):

1. Read Slack history (and Jira summary if Slack is thin).
2. Parse fields. Show a **preview** in chat (title, Jira, env, owners, channel, draft due, presentation date, target folder).
3. Wait for the user to confirm unless they already said **create** / **go** / **not a dry run**.
4. Copy template → replace placeholders → place in FY quarter folder.
5. Post the Slack announcement into the **incident channel**.
6. Reply in Cursor with Doc URL, folder, and whether Slack posted.

## MCP

Discover schemas before calling. Typical servers in this workspace: Slack + Google Drive/Docs (`user-Conduit` / Pipedream), Jira (`user-jira-ghe`).

| Need | Tools (names vary; inspect catalog) |
|------|-------------------------------------|
| Slack read | Channel history, search, get channel details |
| Slack write | Post message (`unfurlLinks`: false) |
| Drive | List files in parent folder, copy or create-from-template, move/update name, create folder if missing |
| Docs | Replace text `{{TITLE}}` etc. if copy-from-template placeholders were not applied |
| Jira | Ticket details when Slack has no Incident Title line |

Do not use Apps Script. Do not ask the user to copy-paste the Slack thread.

## Changelog

- 2026-09-08 — Initial skill (Cursor + Slack + Drive; no slash command).
