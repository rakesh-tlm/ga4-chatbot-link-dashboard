ga4-chatbot-link-dashboard

A Claude skill that builds and refreshes the WhatsApp chatbot link dashboard for an online store. It pulls chatbot traffic from Google Analytics 4 and click counts from short.io, then publishes (or republishes) the result as a Claude artifact.

The dashboard shows, for every chatbot link: its name (product, collection or page), short link, link clicks, sessions, add to cart, purchases, plus the click path, funnel, scroll depth, video and products viewed after the click.

How to use

In any Claude chat where the skill is installed, type:

/ga4-chatbot-link-dashboard

or say:

Use the ga4-chatbot-link-dashboard skill to refresh the chatbot dashboard now. Pull fresh GA4 and short.io data up to today (today is partial) and republish to the same artifact link.

Every call refreshes the data and republishes the artifact.

What you need before it works

Installing the skill is not enough. The person using it needs all of these in their own Claude:

Requirement	Why
Google Analytics MCP (analytics-mcp) connected, with access to GA4 property 459087595	Source of sessions, events, scroll, video, products
short.io MCP connected with your own short.io API key	Source of short link click counts, link checks
Claude desktop app linked to your computer	The GA4 and short.io tools run through it
Artifact tool enabled	The dashboard is published as an artifact

The sample artifact link inside the skill belongs to the original author and is private. If it cannot be opened, the skill builds a new dashboard and gives you your own link on the first run.

To use this for a different store, edit SKILL.md and replace the GA4 property ID, the short.io domain and the artifact URL.

Never put API keys in SKILL.md or in this repo.

Install
Claude.ai / Cowork (upload)
Download dist/ga4-chatbot-link-dashboard.zip.
Go to Settings, Capabilities, Skills, then Upload.
Claude Code (plugin marketplace)
/plugin marketplace add rakesh-tlm/ga4-chatbot-link-dashboard
/plugin install ga4-chatbot-link-dashboard@ga4-chatbot-link-dashboard
Manual

Copy plugins/ga4-chatbot-link-dashboard/skills/ga4-chatbot-link-dashboard into ~/.claude/skills/.

Connect short.io MCP (example config)

Add to your Claude desktop config, using your own key (store it as an environment variable, do not commit it):

json
"shortio": {
  "command": "cmd",
  "args": ["/c", "npx", "mcp-remote", "https://ai-assistant.short.io/mcp", "--header", "Authorization:${SHORTIO_API_KEY}"],
  "env": { "SHORTIO_API_KEY": "<your short.io private API key>" }
}
Known limits
OTP logins from chatbot users do not show in GA4 chatbot sessions, and individual customers cannot be identified.
short.io clicks and GA4 sessions will not match exactly.
License

MIT
