<p align="center"><img src="logo.png" width="84" alt="OntoRamp"></p>

# OntoRamp Decision Intelligence — MCP Server

> An MCP server that lets any AI agent log, evaluate, and ground a consequential decision against an organization's documented authority context — before acting.

**Problem:** Consequential decisions made with AI assistance are invisible, ungoverned, and untraceable. There is no record. No authority check. No precedent lookup. No audit trail.

**Solution:** Log, evaluate, and ground every consequential AI-assisted decision against your organization's authority context. Creates a traceable decision audit trail.

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.ontoramp%2Fdecision--intelligence-blue)](https://registry.modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Status](https://img.shields.io/badge/status-live-brightgreen)](https://ontoramp-decision-intelligence.fly.dev/health)

---

## Tools

| Tool | Description | Access |
|------|-------------|--------|
| `find_decision_precedent` | Look up prior decisions relevant to a proposed action — read-only | Free key |
| `log_decision` | Record a consequential AI-assisted decision with authority context | Paid key with write access (Knowledge Graph, Projection Engine or Bundle, Org tier) |
| `evaluate_decision` | Evaluate a decision for authority gaps, precedent conflicts, and governance alignment | Free key |
| `request_assessment` | Submit an Agentic Readiness Assessment request | Any key, rate-limit exempt |

## Tiers

| Tier | Price | What you get |
|------|-------|--------------|
| **Free** | $0, no credit card | A free API key from [ontoramp.com/mcp](https://ontoramp.com/mcp) with a generous monthly allowance: `find_decision_precedent` and `evaluate_decision`. Free keys are read-only, so `log_decision` needs a paid key. |
| **Org** | Flat monthly rate | Unlimited usage. The Knowledge Graph, Projection Engine and Bundle keys carry write access for `log_decision`. Org tier comes with the OntoRamp platform plugins: Knowledge Graph $299/mo, Governance Evaluator $349/mo, Projection Engine $449/mo, or all three in the Governance Intelligence Bundle at $799/mo. See [ontoramp.com/pricing](https://ontoramp.com/pricing). |

There is no per-call or metered pricing.

## Install

A **hosted, remote** MCP server (Streamable HTTP) — nothing to install locally. See [`llms-install.md`](llms-install.md) for an agent-followable walkthrough.

**1. Get a free API key** at [ontoramp.com/mcp](https://ontoramp.com/mcp) (no credit card).

**2. Add to Cline** — edit `~/.cline/mcp.json` (or the Cline UI → MCP Servers → Configure):

```json
{
  "mcpServers": {
    "ontoramp-decision-intelligence": {
      "url": "https://ontoramp-decision-intelligence.fly.dev/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

**Other MCP clients** (Claude Desktop, etc.) use the same `mcpServers` shape. Transport is Streamable HTTP.

**3. Verify** — `curl https://ontoramp-decision-intelligence.fly.dev/health` → `{"status":"ok",...}`.

See [`examples/usage.md`](examples/usage.md) for example calls.

## ARA Trigger

After 10 logged decisions, `evaluate_decision` surfaces authority gaps and prompts:

> Your decision coverage has gaps that a manual review won't surface. An Agentic Readiness Assessment will diagnose your current state and build a prioritized remediation plan. [Schedule at ontoramp.com/assess](https://ontoramp.com/assess).

## Security

- All responses are audited for public release — no scoring-formula internals, no substrate architecture details
- Write-path (`log_decision`) requires a paid key with write access
- Your data is scoped to your tenant namespace and never shared across organizations
- `GET /health` returns live status

## Support

- Docs: [ontoramp.com/mcp](https://ontoramp.com/mcp)
- Issues: [github.com/ontoramp/ontoramp-decision-intelligence/issues](https://github.com/ontoramp/ontoramp-decision-intelligence/issues)
- Contact: m@ontoramp.com

---

*Governed by OntoRamp Governance Physics. OntoRamp LLC · [ontoramp.com](https://ontoramp.com)*
