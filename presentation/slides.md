---
marp: true
theme: default
paginate: true
header: "Microsoft Sentinel MCP with VS Code"
footer: "Security Operations with AI | 2026"
style: |
  section {
    font-family: 'Segoe UI', sans-serif;
  }
  section.lead h1 {
    font-size: 2.5em;
  }
  section.lead h2 {
    font-size: 1.4em;
    color: #666;
  }
  table {
    font-size: 0.85em;
  }
  blockquote {
    border-left: 4px solid #0078D4;
    padding-left: 1em;
    color: #333;
  }
---

<!-- _class: lead -->
<!-- _paginate: false -->

# Microsoft Sentinel MCP
# with VS Code

## Supercharging Security Operations with AI

---

# Agenda (30 min)

| # | Topic | Time |
|---|-------|------|
| 1 | VS Code — The Security Engineer's Workbench | 3 min |
| 2 | What is MCP? | 2 min |
| 3 | Sentinel MCP — Overview & Setup | 2 min |
| 4 | **Demo 1:** Data Exploration | 5 min |
| 5 | **Demo 2:** Triage & Incident Response | 5 min |
| 6 | **Demo 3:** Security Copilot Agent Creation | 5 min |
| 7 | Saved Prompts & Custom MCP Servers | 2 min |
| 8 | Agent Skills for Security | 3 min |
| 9 | Wrap-up & Q&A | 3 min |

---

# The Challenge

- Security teams are **overwhelmed** — alert fatigue, tool sprawl, talent gap
- Investigations require switching between **multiple portals and tools**
- Writing KQL queries and correlating data across sources takes **expertise and time**
- Incident reports and triage are **manual, repetitive, and error-prone**

> What if you could **ask questions in plain English** and get answers from your security data?

---

# VS Code — The Security Engineer's Workbench

**Not just for developers anymore.** VS Code is becoming the universal tool for security teams.

- **GitHub Copilot** — AI assistant for security workflows
- **Agent Mode** — multi-step, tool-calling AI conversations
- **MCP Support** — connect to external tools and data sources
- **Saved Prompts** — reusable, shareable investigation playbooks
- **Agent Skills** — 19+ security-specific skills from Microsoft

No code required — just natural language.

---

# Why VS Code for Security?

| Capability | Benefit for Security Teams |
|---|---|
| GitHub Copilot Agent Mode | Natural language queries over security data |
| MCP Integration | Direct connection to Sentinel, Defender, Purview |
| Saved Prompts (.prompt.md) | Standardized investigation playbooks |
| Agent Skills | Domain expertise for Azure Security, Sentinel, RBAC, etc. |
| Extensions Ecosystem | Sentinel notebooks, Azure tools, Git integration |

> **Key insight:** VS Code + Copilot + MCP = an AI-powered SOC analyst workstation

---

# What is MCP?

**Model Context Protocol** — an open standard for connecting AI models to external tools and data.

Think of it as **a universal adapter** between AI assistants and your security tools.

**How it works:**
1. AI model (Copilot) receives your question
2. It identifies which **MCP tools** to call
3. Tools execute against your **real security data**
4. AI synthesizes results into a **human-readable answer**

> You stay in control — every tool call requires your approval.

---

# Microsoft Sentinel MCP

**Fully hosted, zero deployment.** Microsoft provides the MCP server — you just connect.

### Three Server Collections

| Collection | What it Does |
|---|---|
| **Data Exploration** | Search tables, query the lake, analyze entities |
| **Triage** | Triage incidents, hunt threats across your org |
| **Security Copilot Agent Creation** | Build Copilot agents via natural language |

**Authentication:** Microsoft Entra ID
**Minimum role:** Security Reader

---

# Setup — It Takes 2 Minutes

### Step 1: Add the MCP Server
`Ctrl + Shift + P` → **MCP: Add Server** → HTTP → Paste server URL

### Step 2: Authenticate
Allow Microsoft Entra sign-in with Security Reader role

### Step 3: Verify
Open Chat (`Ctrl + Alt + I`) → Agent Mode → Configure Tools → Confirm tools listed

### Server URLs
- `https://sentinel.microsoft.com/mcp/data-exploration`
- `https://sentinel.microsoft.com/mcp/triage`
- `https://sentinel.microsoft.com/mcp/security-copilot-agent-creation`

---

<!-- _class: lead -->

# Demo 1
## Data Exploration Server

*Explore security data using natural language*

---

# Demo 1 — Data Exploration

### What we'll show

**Natural language queries** against your Sentinel data lake — no KQL required.

### Demo prompts

> "Find the top three users that are at risk and explain why they're at risk."

> "Find sign-in failures in the last 24 hours and give me a brief summary of key findings."

> "Identify devices that showed an outstanding number of outgoing network connections."

### What's happening behind the scenes
Copilot calls `search_tables`, `query_lake`, and `analyze_*` MCP tools, then synthesizes results.

---

# Demo 1 — Entity Analysis

### Investigating a specific user

> "Help me understand if the user `<user object ID>` is compromised."

### URL IOC Analysis

> "Find and analyze URL IOCs from this threat analytics report."

### Key takeaway

- **No KQL expertise required** — AI writes and executes queries for you
- **Entity context** — user risk, device posture, URL reputation in one place
- **Time savings** — minutes instead of hours for initial triage

---

<!-- _class: lead -->

# Demo 2
## Triage Server

*Incident triage and threat hunting with AI*

---

# Demo 2 — Incident Triage

### What we'll show

AI-assisted **incident prioritization and investigation**.

### Demo prompts

> "List recent incidents and assess urgency for triage."

> "Analyze alert evidence for incident #12345."

> "Investigate users with a password spray alert in the last seven days and tell me if any of them are compromised."

### What's happening behind the scenes
Copilot calls incident listing, alert correlation, and entity enrichment tools — orchestrating a multi-step investigation automatically.

---

# Demo 2 — Threat Hunting

### Proactive hunting scenarios

> "Hunt for users that interacted with entity X."

> "Identify devices that showed an outstanding number of outgoing network connections."

### Value for security teams

- **Automated multi-step investigations** — one question triggers dozens of API calls
- **Correlation across sources** — Defender + Sentinel + Purview in one view
- **Consistent triage quality** — AI follows the same thorough process every time

---

<!-- _class: lead -->

# Demo 3
## Security Copilot Agent Creation

*Build automated security agents with natural language*

---

# Demo 3 — Agent Creation

### What we'll show

Creating a **Security Copilot agent** that automates post-incident reporting.

### Demo prompt

> "Create a Security Copilot agent that generates comprehensive post-incident reports by aggregating data from Defender, Sentinel, and Purview."

### What the agent does

1. **Retrieves incidents** from Defender and Sentinel
2. **Deep dives** — guided response, user/device risk, identity summaries
3. **Correlates** Sentinel incidents with Defender data
4. **Generates a structured report** — executive summary, affected entities, remediation

---

# Demo 3 — Post-Incident Report

### Agent output structure

| Section | Content |
|---|---|
| Executive Summary | High-level overview of all incidents |
| Incident Details | ID, title, severity, status, timeline |
| Affected Entities | Users (with risk), devices (with posture), files |
| Triggered Alerts | Defender, Sentinel, Purview alerts |
| Data Risk Assessment | DLP/IRM findings, sensitive data exposure |
| Remediation | Immediate, short-term, and long-term actions |

> **One prompt → a complete incident report** that used to take hours to compile.

---

# Saved Prompts — Your Investigation Playbooks

Reusable `.prompt.md` files in `.github/prompts/` — one-click investigation workflows.

| Prompt | Use Case |
|---|---|
| `assess-urgent-incidents` | Morning triage — prioritize the queue |
| `password-spray-investigation` | Respond to credential attacks |
| `users-at-risk` | Review risky users and risk factors |
| `sign-in-failures` | Daily sign-in health check |
| `user-compromise-check` | Investigate a specific user for compromise |
| `url-ioc-analysis` | Analyze URLs from threat intel |
| `outgoing-connections` | Detect data exfiltration patterns |

Each prompt declares the exact MCP tools needed — **no manual configuration**.

---

# How Saved Prompts Work

### Using a saved prompt

1. Open Chat → Agent Mode
2. Click **Attach Context** (📎) → **Prompt...**
3. Select a prompt → it fills the chat input
4. Fill in variables (if any) → Send

### Sharing across your team

- Store prompts in `.github/prompts/` in your repo
- Version-controlled investigation playbooks
- **Standardize** how your team investigates incidents
- New analysts get **instant access** to expert-level workflows

---

# Custom MCP Servers

### Extend beyond built-in tools

You can **build custom MCP tools** tailored to your organization's specific needs.

**Example: SigninDemo MCP Server** — custom sign-in analytics for investigating authentication patterns, risky locations, and brute-force attacks.

---

# Custom MCP Server — Demo Prompts

### SigninDemo: Sign-in Analytics

> "Which locations have the most failed and risky sign-ins?"

> "Are there any sign-in attempts from sanctioned countries like North Korea or Iran?"

> "Which user accounts are being targeted with invalid password attempts?"

> "Show me the most suspicious IP addresses based on failure volume and risk signals."

> "Is the admin account under a brute-force attack? Summarize the sign-in failures."

> "Which applications are being targeted from high-risk locations?"

Each prompt maps to a real security investigation scenario — **no KQL, no portal switching**.

---

# What Are Agent Skills?

**Agent skills** = domain-specific knowledge packs that make Copilot an expert in a topic.

### How they work
- Install a skill → Copilot **automatically gains expertise** in that domain
- No code, no plugins — just a knowledge file added to your workspace
- Skills provide **best practices, troubleshooting guides, and architectural patterns**

### Three official registries

| Registry | Focus | Skills Count |
|---|---|---|
| [Microsoft Agent Skills](https://github.com/MicrosoftDocs/Agent-Skills) | Azure services & security | 19 security skills |
| [Awesome Copilot Skills](https://github.com/github/awesome-copilot) | Community-contributed | Governance, safety, SQL review |
| [Microsoft Skills Gallery](https://microsoft.github.io/skills/) | SDK-level guidance | Identity, Key Vault, Content Safety |

---

# Microsoft Agent Skills — Security & Identity (1/2)

### 19 security-focused skills from Microsoft

**SIEM / SOAR / Threat Protection**
- `azure-sentinel` — Sentinel SIEM/SOAR development and optimization
- `azure-defender-for-cloud` — Defender for Cloud threat protection
- `azure-defender-for-iot` — IoT/OT device security
- `azure-security` — Azure Security best practices and configuration

**Identity & Access**
- `azure-rbac` — Role-based access control guidance
- `azure-active-directory-b2c` — Customer identity and access management

**Network Security**
- `azure-firewall` — Network traffic filtering and threat intelligence
- `azure-web-application-firewall` — WAF protection for web apps

---

# Microsoft Agent Skills — Security & Identity (2/2)

**Cryptography & Key Management**
- `azure-key-vault` — Secrets, keys, and certificates management
- `azure-cloud-hsm` — Cloud-based Hardware Security Modules
- `azure-dedicated-hsm` — Dedicated HSM key management
- `azure-payment-hsm` — Payment HSM for financial crypto operations

**Data Protection & Compliance**
- `azure-information-protection` — Data classification and protection
- `azure-confidential-computing` — Secure enclaves for sensitive workloads
- `azure-confidential-ledger` — Tamper-proof ledger for auditing
- `azure-attestation` — Platform integrity verification

**Attack Surface & Firmware**
- `azure-external-attack-surface-management` — External attack surface discovery
- `azure-firmware-analysis` — IoT/OT firmware vulnerability analysis
- `azure-artifact-signing` — Code and artifact signing

---

# Community & SDK Security Skills

### Awesome Copilot — Community Skills

| Skill | What It Does |
|---|---|
| `agent-governance` | Policy-based access controls, trust scoring, audit trails for AI agents |
| `ai-prompt-engineering-safety-review` | Detect bias, security vulnerabilities, and prompt injection risks |
| `sql-code-review` | SQL injection prevention, access control, anti-pattern detection |

### Microsoft Skills Gallery — SDK Security Skills

| Skill | What It Does |
|---|---|
| `azure-identity-*` (.NET, Java, Python, Rust, TS) | Authentication with Microsoft Entra ID |
| `azure-keyvault-*` (secrets, keys, certificates) | Cryptographic key & secret management |
| `azure-ai-contentsafety-*` (Java, Python, TS) | Detect hate, violence, self-harm in content |
| `azure-webjobs-auth-events` | Custom Entra ID auth extensions |

---

# Agent Skills in Action — Security Scenarios

### Example: You ask Copilot about Key Vault

**Without** `azure-key-vault` skill:
> Generic guidance, possibly outdated

**With** `azure-key-vault` skill:
> Best practices for secret rotation, HSM-backed keys, RBAC vs. access policies, diagnostic logging, network restrictions — current and accurate

### How to install a skill
1. Go to the skill registry (e.g., [Microsoft Agent Skills](https://github.com/MicrosoftDocs/Agent-Skills))
2. Copy the skill file to `.github/skills/` in your repo
3. Copilot automatically picks it up — **done**

> Skills turn Copilot from a generalist into a **security domain expert**.

---

# What This Means for Your SOC

### Before (traditional workflow)
- Switch between Sentinel portal, Defender portal, Purview
- Write KQL queries manually
- Copy-paste data between tools
- Manually compile incident reports

### After (Sentinel MCP + VS Code)
- **One interface** — ask in natural language, get correlated answers
- **Automated investigations** — AI orchestrates multi-source queries
- **Standardized playbooks** — saved prompts ensure consistent quality
- **Automated reporting** — agents compile reports from multiple sources

---

# Key Takeaways

1. **VS Code + Copilot** is a powerful platform for security operations — not just coding

2. **Sentinel MCP** connects AI directly to your security data — no deployment needed

3. **Three server collections** cover exploration, triage, and agent creation

4. **Saved prompts** turn expert knowledge into shareable, version-controlled playbooks

5. **Custom MCP servers** let you extend to organization-specific tools

> **The future of SOC is conversational** — ask questions, get answers, take action.

---

# Getting Started

### Today
- Install VS Code + GitHub Copilot extension
- Connect to Sentinel MCP servers (2 min setup)
- Try the saved prompts from this repo

### This Week
- Share saved prompts with your team
- Explore the Security Skills ecosystem
- Identify custom MCP server opportunities

### Resources
- [Sentinel MCP Overview](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-overview)
- [Get Started Guide](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-get-started)
- [Create Custom MCP Tools](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-create-custom-tool)

---

<!-- _class: lead -->
<!-- _paginate: false -->

# Thank You

## Questions?

**Repository:** github.com/webmaxru/microsoft-sentinel-mcp-github-copilot

**Resources:**
[Sentinel MCP Overview](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-overview) |
[MCP Specification](https://modelcontextprotocol.io/)
