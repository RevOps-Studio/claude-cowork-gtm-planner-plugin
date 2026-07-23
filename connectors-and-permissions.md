# Connectors & permissions

All connectors are **optional**. The planner runs the full journey with
zero connectors (web research + user-provided materials); each connector
upgrades precision on specific steps. Before researching, the market-map
and demand-plan steps run a source readiness check and let the user choose
fallbacks explicitly. Estimates are always labeled.

| Connector | Steps | What it adds | Data it reads | Data it writes | Access requirements | If not connected |
|---|---|---|---|---|---|---|
| **HubSpot** | 1, 4 | Real funnel: lead sources, stage conversion, cycle length, deal sizes | CRM objects (contacts, deals, pipelines) — read-only usage by the planner | Nothing | HubSpot account, OAuth | User-declared numbers, flagged as declared |
| **Notion** | 5 | Persists the GTM Plan and roadmap | Target pages/databases chosen by the user | Creates/updates plan pages | Notion account, OAuth | Plan delivered in chat/files only |
| **Similarweb** | 2, 4 | Competitor traffic scale and channel mix | Traffic/channel reports for named domains | Nothing | **Similarweb plan with API access (paid)** | Web-based estimates, labeled as estimates |
| **Ahrefs** | 2, 4 | Competitor organic footprint, keyword volumes | SEO metrics for named domains | Nothing | **Ahrefs plan with API access** | Web research on visible content/SERPs |
| Google Drive *(native, no MCP)* | 1 | Reads the user's decks/docs at intake | Files the user points to | Nothing | Standard Claude integration | User uploads files in chat |

**Endpoints** (defined in `.mcp.json`): mcp.hubspot.com ·
mcp.notion.com/mcp · mcp.similarweb.com · api.ahrefs.com/mcp/mcp. All are
official remote MCP servers from their vendors, listed in Anthropic's
Connectors Directory. Authentication is OAuth handled by the Claude client;
the plugin never sees or stores credentials.
