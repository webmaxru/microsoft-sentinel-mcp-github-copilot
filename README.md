# Microsoft Sentinel MCP with VS Code

This repository demonstrates how to use [Microsoft Sentinel's Model Context Protocol (MCP)](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-overview) server with Visual Studio Code to interact with security data using natural language.

## Overview

Microsoft Sentinel's MCP support provides scenario-focused collections of security tools through a unified, hosted server interface. It enables security teams to:

- **Explore security data** in Microsoft Sentinel data lake using natural language
- **Analyze entities** such as URLs, users, and devices across security data
- **Triage incidents** and hunt for threats with AI-powered assistance
- **Build Security Copilot agents** through natural language descriptions

No infrastructure deployment is required — the MCP server is fully hosted and uses Microsoft Entra for identity.

## Repository Contents

| File | Description |
|------|-------------|
| `post-incident-report-agent.yaml` | A Security Copilot agent definition that generates comprehensive post-incident reports by aggregating data from Microsoft Defender, Sentinel, and Purview. |

## Prerequisites

- [Visual Studio Code](https://code.visualstudio.com/) with [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot) extension
- An Azure account with access to Microsoft Sentinel
- Onboarded to the [Microsoft Sentinel data lake](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-lake-onboarding)
- **Security reader** role (minimum) to list and invoke Sentinel MCP tools
- Depending on tools used, you may also need access to:
  - Microsoft Sentinel in the Microsoft Defender portal
  - Microsoft Defender XDR or Microsoft Defender for Endpoint
  - Microsoft Security Copilot

## Available MCP Tool Collections

| Collection | Description | Server URL |
|------------|-------------|------------|
| Data Exploration | Explore security data by searching tables, querying the lake, and analyzing entities | `https://sentinel.microsoft.com/mcp/data-exploration` |
| Security Copilot Agent Creation | Create Microsoft Security Copilot agents for complex workflows | `https://sentinel.microsoft.com/mcp/security-copilot-agent-creation` |
| Triage | Triage incidents and hunt over your organization's data | `https://sentinel.microsoft.com/mcp/triage` |

## Getting Started

### 1. Add the MCP Server in VS Code

1. Press `Ctrl + Shift + P` and select **MCP: Add Server**
2. Choose **HTTP (HTTP or Server-Sent Events)**
3. Enter the URL of the tool collection you want to use (see table above)
4. Assign a friendly **Server ID** (e.g., `Microsoft Sentinel MCP server`)
5. Choose whether to make the server available in all workspaces or just the current one

### 2. Authenticate

When prompted, select **Allow** to authenticate using an account with at least the **Security reader** role.

### 3. Verify the Connection

1. Open VS Code chat via **View > Chat** or `Ctrl + Alt + I`
2. Set the chat to **Agent mode**
3. Select the **Configure Tools** icon to verify the MCP tools are listed under the server

### 4. Start Querying

Use natural language prompts in Agent mode to interact with your security data. For example:

- *"Find the top three users that are at risk and explain why they're at risk."*
- *"Find sign-in failures in the last 24 hours and give me a brief summary of key findings."*
- *"Identify devices that showed an outstanding number of outgoing network connections."*
- *"Help me understand if the user \<user object ID\> is compromised."*
- *"Investigate users with a password spray alert in the last seven days and tell me if any of them are compromised."*

## Post-Incident Report Agent

The `post-incident-report-agent.yaml` file defines a Security Copilot agent that automates post-incident reporting. It orchestrates data retrieval from multiple sources:

1. **Retrieve Incidents** — Lists incidents from both Defender and Sentinel
2. **Deep Dive Analysis** — For each incident, retrieves guided response recommendations, user/device risk summaries, identity summaries, and Purview alerts
3. **Correlation** — Correlates Sentinel incidents with Defender data and enriches entity information
4. **Report Generation** — Compiles a structured report with:
   - Executive Summary
   - Incident Details (ID, title, severity, status, timeline)
   - Affected Entities (users, devices, files)
   - Triggered Alerts (Defender, Sentinel, Purview)
   - Data Risk Assessment (DLP/IRM findings)
   - Remediation Recommendations (Immediate, Short-term, Long-term)

## Resources

- [Microsoft Sentinel MCP Overview](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-overview)
- [Get Started with Microsoft Sentinel MCP Server](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-get-started)
- [Use MCP Tools in Visual Studio Code](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-use-tool-visual-studio-code)
- [Tool Collections Overview](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-tools-overview)
- [Create Custom MCP Tools](https://learn.microsoft.com/en-us/azure/sentinel/datalake/sentinel-mcp-create-custom-tool)
- [Model Context Protocol Specification](https://modelcontextprotocol.io/)
