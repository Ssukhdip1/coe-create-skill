# Create COE — procedure

## 1. Resolve the incident

- If the user gave `#ipesre-…` or a channel ID: use Slack **get channel details** + **get channel history** (limit ~40; fields `text`, `ts`, `user`). Join message texts newest-last.
- If they only gave `IPESRE-n`: Slack **search** for `IPESRE-n` or look up `#ipesre-n` via **list/get channel**. Also **getTicketDetails** for summary / title / environment if Slack is empty.
- Never ask them to paste the thread if Slack MCP can read the channel.

## 2. Parse

Fill: title, jiraId, env, owners (names), slackOwners, imseManager, channel.

If title/jira still empty after Slack+Jira, stop and ask one clarifying question.

## 3. Dates and folder

Compute draft due + presentation date from [team-config.md](team-config.md).

List folders under the parent folder ID. Pick the FY+Q match. If none and create-if-missing: create `FY{YY} Q{Q} COE`.

## 4. Preview (required unless user already confirmed create)

Show in chat:

- Title, Jira, env, owners, IMSE manager, channel
- Draft due, presentation date
- Target folder name
- Dry run vs live

Wait for **yes** / **create** on live runs.

**Dry run:** stop here. Print the Slack message body. Do not copy Drive. Do not post Slack.

## 5. Create the Doc (live)

Preferred: **create file from template** with `templateId`, `name`, `mode: ["Google Doc"]`, `folderId` = quarter folder, `replaceValues` keys **without** braces (`TITLE`, `JIRA_ID`, `ENVIRONMENTS`, `OWNERS`, `IMSE_MANAGER`, `SLACK_CHANNEL`, `PRESENTATION_DATE`).

Fallback: **copy file** template → **update file** name → **replace-text** each `{{TOKEN}}` → **move file** into the quarter folder.

Doc URL: `https://docs.google.com/document/d/{id}/edit`

If placeholders remain, run replace-text again.

## 6. Post Slack (live)

Post the announcement from team-config into the incident channel. If post fails (bot not in private channel), give the user the exact message to paste and the Doc URL — still a success for Drive.

## 7. Cursor reply

- Doc link and Drive folder link
- Dates
- Slack: posted vs copy-paste fallback
- Remind: **coe-admin-skill** is later, after Section 9 exists
