# HubSpot CRM MCP Starter Kit — Manage HubSpot with AI

[![MCP Compatible](https://img.shields.io/badge/MCP-compatible-blue)](https://modelcontextprotocol.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform: HubSpot](https://img.shields.io/badge/Platform-HubSpot-FF7A59)](https://www.hubspot.com)

**Bridge your CRM and ad campaigns with AI.** Open this repo in Amp, Cursor, or VS Code and manage HubSpot contacts, deals, and lists with AI — then sync your best customers to ad platforms for lookalike targeting.

---

## Why HubSpot + AI?

HubSpot is the CRM of choice for 228,000+ businesses — especially SMBs and inbound marketing teams. It holds your most valuable marketing asset: first-party customer data. Email addresses, lifecycle stages, deal values, engagement history, and customer LTV.

This data is gold for advertising. Your best customers aren't just a CRM record — they're the seed for Meta Lookalike audiences, Google Customer Match campaigns, and LinkedIn Matched Audiences. But manually exporting HubSpot lists, formatting them, and uploading to each ad platform is tedious enough that most teams never do it.

An AI agent automates this pipeline. It queries HubSpot for high-value segments, formats the data for each platform's requirements, and syncs audiences — turning your CRM into an always-fresh ad targeting engine.

**Best for:** Inbound marketing teams, SMBs using HubSpot CRM, B2B companies wanting to sync deals/contacts to ad audiences, teams who need to suppress existing customers from acquisition campaigns.

---

## Quick Start (30 Seconds)

### Amp / Cursor / VS Code (Copilot)

1. **Get a free API key** at [syntermedia.ai/developer](https://syntermedia.ai/developer)
2. **Set the key:**
   ```bash
   export SYNTER_API_KEY=syn_your_key_here
   ```
3. **Open this repo** in your editor
4. **Start chatting** — MCP tools are pre-configured in `.mcp.json`

### Claude Desktop

Copy `claude_desktop_config.json` to your Claude config directory and replace the API key:

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

---

## What You Can Do

| Capability | Example |
|-----------|---------|
| **Contact Lookup** | "Find all contacts at Acme Corp with a deal in pipeline" |
| **Deal Pipeline** | "Show me all deals closing this month by stage" |
| **List Building** | "Create a list of customers who spent over $10,000 lifetime" |
| **Audience Sync** | "Sync my high-LTV customers to Meta for Lookalike audiences" |
| **Suppression Lists** | "Exclude all existing customers from my Google Ads campaigns" |
| **Lifecycle Analysis** | "What's the average time from MQL to Customer?" |
| **Engagement Scoring** | "Which contacts have opened emails but never requested a demo?" |
| **Deal Attribution** | "Which marketing channel brought in the most closed-won deals?" |
| **Contact Enrichment** | "Show me contacts with missing company size or industry data" |
| **Bulk Updates** | "Mark all contacts who attended the webinar as MQLs" |

---

## Example Conversations

### 1. Building a High-LTV Lookalike Audience

> **You:** I want to find more customers like my best ones. Can you help?
>
> **Agent:** Absolutely. Let me analyze your HubSpot deals to find your highest-value customers...
>
> **Top 10% customers by lifetime value:**
> - 127 customers with average LTV of $48,200
> - Common traits: Company size 50-200 employees, SaaS/Technology industry, Director+ contacts, entered pipeline through content marketing
>
> **What I'll do:**
> 1. Export these 127 customer email addresses from HubSpot
> 2. Hash them (SHA-256) for privacy compliance
> 3. Upload to Meta as a Custom Audience → Create 1% Lookalike (~2.3M people)
> 4. Upload to Google Ads as Customer Match → Use for Similar Audiences
> 5. Upload to LinkedIn as Matched Audience → Target similar professionals
>
> **Expected impact:** Lookalike audiences based on high-LTV customers typically deliver 30-50% lower CPA than interest-based targeting because the ad platform finds people with similar purchase behaviors.
>
> **You:** Do it. And set up a monthly refresh so the audience stays current.
>
> **Agent:** Audiences created on all 3 platforms. I've also set a reminder to refresh monthly — new high-LTV customers get added, churned customers get removed.

### 2. Suppressing Customers from Acquisition Campaigns

> **You:** I'm spending money showing ads to people who are already customers. How do I stop that?
>
> **Agent:** This is one of the most common budget leaks. Let me build a suppression audience from your HubSpot data.
>
> **I'll create suppression lists for:**
> 1. All contacts with lifecycle stage = "Customer" (892 contacts)
> 2. All contacts with at least one closed-won deal (847 contacts)
> 3. All contacts who are currently in a free trial (203 contacts)
>
> **Combined unique contacts for suppression: 1,142**
>
> **Syncing to:**
> - Google Ads → Customer Match exclusion list
> - Meta → Custom Audience exclusion
> - LinkedIn → Matched Audience exclusion
>
> **Budget impact estimate:** If 8% of your ad impressions currently reach existing customers (industry average), and your monthly ad spend is $15,000, you're wasting ~$1,200/month. This suppression list recovers that budget for actual acquisition.
>
> **Bonus insight:** I also found 203 trial users in your HubSpot. Instead of suppressing them, should I create a separate retargeting campaign to convert them to paid? They're warm leads who already know your product.

### 3. Deal Pipeline Analysis for Ad Targeting

> **You:** Which marketing channels are bringing in deals that actually close?
>
> **Agent:** Let me cross-reference your HubSpot deal pipeline with original source data...
>
> **Closed-Won Deals (Last 6 Months):**
>
> | Original Source | Deals | Revenue | Avg Deal Size | Win Rate |
> |---|---|---|---|---|
> | Organic Search | 34 | $612,000 | $18,000 | 28% |
> | Paid Search (Google) | 22 | $484,000 | $22,000 | 31% |
> | Paid Social (LinkedIn) | 18 | $540,000 | $30,000 | 24% |
> | Content Download | 28 | $336,000 | $12,000 | 19% |
> | Referral | 12 | $396,000 | $33,000 | 42% |
> | Event/Webinar | 8 | $144,000 | $18,000 | 15% |
>
> **Key insights:**
> - **LinkedIn deals are the biggest** ($30K avg) — worth the expensive CPCs
> - **Referrals have the highest win rate** (42%) and largest deals ($33K)
> - **Content downloads generate volume** but smaller deals and lower win rates
> - **Google Ads has the best balance** — good volume, large deals, strong win rate
>
> **Recommendation:** Increase LinkedIn budget (highest deal size), create a referral incentive program (highest win rate), and reduce content download budget (lowest quality leads).

### 4. Lifecycle Stage Progression Monitoring

> **You:** How long does it take leads to move through our pipeline?
>
> **Agent:** Pulling lifecycle stage timestamps from HubSpot...
>
> **Average progression (last 6 months):**
>
> | Stage Transition | Avg Days | Median Days |
> |---|---|---|
> | Subscriber → Lead | 3.2 | 1 |
> | Lead → MQL | 12.4 | 8 |
> | MQL → SQL | 18.7 | 14 |
> | SQL → Opportunity | 7.3 | 5 |
> | Opportunity → Customer | 31.2 | 24 |
> | **Total: Subscriber → Customer** | **72.8** | **52** |
>
> **Your bottleneck is MQL → SQL (18.7 days).** This is where marketing hands off to sales. Possible causes:
> - Sales team slow to follow up on MQLs
> - MQL criteria too loose (unqualified leads getting tagged as MQL)
> - Not enough sales capacity to work all MQLs
>
> **Ad strategy implication:** Your 73-day sales cycle means attribution windows matter. Google Ads defaults to 30-day attribution — you're missing 40% of conversions. Extend to 90-day attribution. For LinkedIn, use offline conversion import to report closed-won deals back to the campaign that generated the lead.

### 5. Webinar Attendee Retargeting

> **You:** We had 300 people register for a webinar. 180 attended. What should I do with them?
>
> **Agent:** Webinar attendees are some of your warmest leads. Here's a tiered approach:
>
> **Tier 1: Attended but no demo booked (estimate: ~150)**
> - Create a HubSpot list: webinar attendees + lifecycle stage NOT "Opportunity" or "Customer"
> - Sync to Meta/Google/LinkedIn as Custom Audience
> - Ad messaging: "Loved the webinar? See [Product] in action — book a personalized demo"
> - Budget: $20/day for 2 weeks
>
> **Tier 2: Registered but didn't attend (120 people)**
> - Create a separate HubSpot list
> - Ad messaging: "Missed our webinar? Watch the recording + get exclusive bonus content"
> - Link to an ungated recording with a CTA to book a demo
> - Budget: $10/day for 1 week
>
> **Tier 3: Already in pipeline (30 attendees)**
> - Don't waste ad spend — these are already sales-engaged
> - Instead, add a note in HubSpot: "Attended [webinar name]" so sales can reference it in follow-ups
>
> Want me to create these lists and sync the audiences?

---

## HubSpot Tips for Ad Targeting

1. **Sync high-LTV customers to all ad platforms.** Your top 10-25% of customers by revenue are the perfect seed for Lookalike/Similar audiences on Meta, Google, and LinkedIn.
2. **Suppress existing customers from acquisition campaigns.** This is the easiest way to save 5-10% of your ad budget immediately. Create a HubSpot list of customers → sync as exclusion audience.
3. **Use lifecycle stages for ad messaging.** MQLs get awareness content, SQLs get product demos, Opportunities get case studies. Match your ad creative to where the contact is in their journey.
4. **Import offline conversions from HubSpot.** When a deal closes in HubSpot, send that conversion back to Google Ads and LinkedIn. This teaches the ad algorithm which leads become customers — dramatically improving lead quality over time.
5. **Refresh audiences monthly.** Customer lists change as new people buy and others churn. Stale audiences mean you're targeting the wrong people.
6. **Track original source religiously.** HubSpot's "Original Source" field tells you which marketing channel brought each contact. This is your ground truth for channel attribution.
7. **Don't advertise to your email list.** If you can reach someone via email for free, don't pay to reach them via ads. Suppress your entire HubSpot contact database from cold prospecting campaigns.

---

## FAQ

### Is there an MCP for HubSpot?
Yes — this repo. It pre-configures the Synter MCP server for HubSpot CRM management. Works with Amp, Cursor, VS Code, and Claude Desktop.

### Can AI sync HubSpot contacts to ad platforms?
Yes. The agent can export HubSpot lists, hash PII for privacy compliance, and upload as Custom Audiences to Google, Meta, LinkedIn, and other platforms.

### Do I need HubSpot Marketing Hub or just CRM?
The free HubSpot CRM works for basic contact queries and list building. Marketing Hub adds lifecycle stages, lead scoring, and email engagement data that are valuable for audience segmentation.

### Can the agent create HubSpot workflows?
The agent focuses on contacts, deals, lists, and audience sync. For HubSpot workflow automation, use the HubSpot UI directly.

### How does this help my ad campaigns?
First-party CRM data is the highest-quality targeting signal. Lookalike audiences built from your best HubSpot customers consistently outperform interest-based targeting by 30-50%.

---

## Related Repos

- [salesforce-agent](https://github.com/Synter-Media-AI/salesforce-agent) — Enterprise CRM alternative
- [audience-sync-agent](https://github.com/Synter-Media-AI/audience-sync-agent) — Multi-platform audience sync
- [google-ads-agent](https://github.com/Synter-Media-AI/google-ads-agent) — Google Ads Customer Match
- [meta-ads-agent](https://github.com/Synter-Media-AI/meta-ads-agent) — Meta Custom Audiences
- [linkedin-ads-agent](https://github.com/Synter-Media-AI/linkedin-ads-agent) — LinkedIn Matched Audiences
- [klaviyo-agent](https://github.com/Synter-Media-AI/klaviyo-agent) — Email/SMS marketing sync

---

## License

MIT — see [LICENSE](LICENSE) for details.

Built by [Synter](https://syntermedia.ai) · [Get API Key](https://syntermedia.ai/developer) · [Documentation](https://syntermedia.ai/docs)
