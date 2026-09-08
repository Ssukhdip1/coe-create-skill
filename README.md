# coe-create-skill

Create the COE Google Doc from Cursor using **Slack + Google Drive**. No Slack admin and no pasting the incident thread.

After the COE is drafted, use **coe-admin-skill** for Section 9 Jira.

## What teammates say

New Agent chat:

```text
Create a COE for IPESRE-202565.
Use the coe-create-skill skill.
```

or

```text
Run coe-create-skill.
Channel: #ipesre-202565-walmart-iss
```

Dry run (no Doc, no Slack post):

```text
Dry run coe-create-skill for IPESRE-202565.
```

The agent reads Slack, shows a preview, creates the Doc in the FY quarter folder, and posts the announcement.

## One-time per person

See [setup.md](setup.md): Cursor Agent, this skill installed (`make install` or open this repo), Slack + Google Drive MCP connected, Drive access to the COE parent folder and template.
