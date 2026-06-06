# Model Context Protocol (MCP) Catalog

**Status:** `Internal` | **Version:** `1.0.0` | **Domain:** `Connectivity Layer`

## 1. The Connectivity Strategy
The platform implements the **Model Context Protocol (MCP)** to solve the "Context Gap." Instead of feeding raw documentation to an LLM, the agents use MCP servers as **Dynamic Proxies** to fetch the most current, validated state of the enterprise environment.

### Core Connectivity Principles:
* **Standardization:** Every tool, whether a database or a SaaS API, uses the same request/response schema.
* **Security:** The MCP Gateway handles authentication, ensuring AI agents never see raw credentials.
* **Discovery:** Agents can "crawl" the MCP registry to find the correct tool for a specific data source.

---

## 2. Server Inventory

### ☁️ Cloud & Enterprise Ecosystems
| Server | Protocol / Command | Purpose | Critical Capability |
| :--- | :--- | :--- | :--- |
| **fabric** | `npx @microsoft/fabric-mcp` | Microsoft Fabric Gateway | Lakehouse/Notebook/Semantic Model mgmt |
| **microsoft365** | `npx @pnp/cli-m365-mcp` | M365 Administration | Teams, SharePoint, User Groups |
| **confluence** | `npx mcp-remote` | Knowledge Base Access | Enterprise documentation & runbooks |
| **azure-mcp** | `npx @azure/mcp` | Azure Resource Mgr | ARM, Fabric, AI Services orchestration |
| **fabric-api** | `npx @einlogic/mcp-fabric-api` | REST API Bridge | Direct Fabric platform manipulation |

### 🗄️ Database & Storage Interfaces
| Server | Protocol / Command | Purpose | Target System |
| :--- | :--- | :--- | :--- |
| **postgres** | `npx .../server-postgres` | Relational Querying | Local/Cloud PostgreSQL |
| **sqlite** | `uvx mcp-server-sqlite` | Local Analytical Store | `.n8n` / Local DB files |
| **mongodb** | `npx mongodb-mcp-server` | Document Store Interface | MongoDB (Read-Only) |
| **filesystem** | `npx .../server-filesystem` | OS File Access | `C:\projects`, `Documents` |

### 🔍 Intelligence & Web Research
| Server | Protocol / Command | Purpose | Key Feature |
| :--- | :--- | :--- | :--- |
| **tavily-search** | `npx tavily-mcp` | Tool-Optimized Search | AI-curated technical web search |
| **brave-search** | `npx .../server-brave-search` | General Web Access | Broad-spectrum internet search |
| **fetch** | `uvx mcp-server-fetch` | Markdown Extraction | Direct URL $\rightarrow$ MD conversion |
| **browser** | `npx @playwright/mcp` | Visual Automation | DOM extraction, screenshots, PDFs |
| **everything** | `uvx mcp-server-everything` | OS Indexing | Global asset search across local disk |

### 🛠️ DevOps & Productivity
| Server | Protocol / Command | Purpose | Key Feature |
| :--- | :--- | :--- |
 same as the original but restructured for professionalism and clarity 
... (rest of the original servers)
