# Lead Management System

Four modular n8n workflows for lead capture and AI qualification, human approval and verified sending, scheduled follow-up, and reply/status management.

## Workflows

1. `01-lead-capture-qualification-draft.json` — 33 nodes; accepts and normalizes leads, qualifies them, drafts email, and records the lead.
2. `02-human-approval-verified-send.json` — 12 nodes; validates an approval action and sends the approved message.
3. `03-automated-follow-up-engine.json` — 12 nodes; periodically selects eligible leads, generates follow-up content, sends, and updates status.
4. `04-reply-detection-status-management.json` — 12 nodes; detects replies and updates lead status.

## Requirements

- n8n with Google Sheets, Gmail, Webhook, Schedule Trigger, and HTTP Request nodes.
- Google Gemini API access for HTTP-based generation calls.
- A Google Sheet configured with the fields referenced by the workflows.

## Import and configure

1. Import each JSON file into n8n as a separate workflow.
2. Assign your own Google Sheets and Gmail credentials and configure Gemini HTTP authentication. Exported credential bindings were removed.
3. Set the same Google Sheet ID, sheet names, owner email, booking URL, n8n base URL, and approval path in the configuration code/parameters as applicable. Replace all setup placeholders.
4. Ensure the approval workflow is reachable at the path expected by the lead-capture workflow. Configure the Gmail reply trigger and schedule.
5. Test with a dedicated sheet and mailbox, then verify approval, follow-up timing, duplicate handling, and reply updates before enabling live sends.

## Notes

The modular exports are provided individually; they are not automatically linked in your n8n instance. Provider credentials, spreadsheet data, API keys, and deployed webhook URLs are not included. Review consent and opt-out handling before use.

