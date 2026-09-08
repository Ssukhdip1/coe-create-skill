# COE create — team configuration

## Google Drive / Docs

| Setting | Value |
|---------|--------|
| Template Doc ID | `11E3IVlKKGlnUnN5bpVj1rCQlU1qiE_i6BPvMJw-ePms` |
| Parent folder (contains FY quarter folders) | `1dzOiwDETwQKJQBgEGIGm38EW76kYB4Lr` |
| New file name | `COE \| {yyyy-MM-dd} \| {JIRA} \| {ENV} \| {TITLE}` |
| Create quarter folder if missing | yes |
| Quarter folder name | `FY{YY} Q{Q} COE` (YY = fiscal year mod 100) |
| Fiscal year start month | **2** (February) |

Template placeholders (replace all):

| Token in doc | Source |
|--------------|--------|
| `{{TITLE}}` | Incident title |
| `{{JIRA_ID}}` | e.g. IPESRE-202565 |
| `{{ENVIRONMENTS}}` | e.g. WD504-PROD/WD504-NPRD |
| `{{OWNERS}}` | Full names |
| `{{IMSE_MANAGER}}` | IMSE Service Manager |
| `{{SLACK_CHANNEL}}` | `#ipesre-…` |
| `{{PRESENTATION_DATE}}` | `yyyy-MM-dd` of presentation |

Jira browse base: `https://jira2.workday.com/browse/`

## Dates (same as Apps Script)

- **Day 0** = COE initiation date (default today).
- **Draft due** = 5 **business** days after Day 0 (skip weekends + holidays).
- **Presentation date** = first **Tuesday** after 15 business days from Day 0. If that Tuesday is a holiday, add 7 days until it is not.

**Global Thank You Days (2026):** `2026-03-27`, `2026-05-22`, `2026-06-18`, `2026-09-04`.

Region holidays: none configured (blank region = these global days only).

## Fiscal quarter

Offset months from February: Q1 = Feb–Apr, Q2 = May–Jul, Q3 = Aug–Oct, Q4 = Nov–Jan. If calendar month ≥ February, fiscal year = calendar year + 1; else fiscal year = calendar year.

Example: 8 Sep 2026 → FY27 Q3.

Match an existing child folder of the parent whose name contains `FY27` (or `FY2027`) **and** `Q3`. Prefer existing folder over creating.

## Slack announcement (verbatim)

```
A COE Document has been created for this incident. Once your draft is complete, a Bar Raiser will join us to refine the document for the final presentation.

COE Link: {docUrl}
COE Owner: {owners or slack handles}

Please note the following deadlines:
• Draft Due: {weekday, Month D, YYYY}
• Presentation Date: {weekday, Month D, YYYY}
```

Post to the **incident Slack channel**. Set link unfurling off when the tool allows it.

## Parse hints (from Slack / Jira)

- `Incident Title: KEY | ENV | title`
- `Linked Jira issue: IPESRE-n`
- Channel name `ipesre-n-…` → Jira `IPESRE-n`
- `COE Owner(s):` or `COE Owners:` full names
- `IMSE Service Manager:`
- `cc @handle @handle`
