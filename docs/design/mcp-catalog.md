# Model Context Protocol (MCP) Catalog

## 1. Overview
The platform utilizes a standardized interface of 38+ MCP servers, allowing AI agents to safely query tools, explore enterprise ecosystems, and manipulate local/remote filesystems.

## 2. Server Inventory

### Azure & Microsoft Cloud MCP
| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **fabric** | `npx @microsoft/fabric-mcp server start --mode all` | Microsoft Fabric — Lakehouses, Notebooks, Pipelines, Semantic Models |
| **microsoft365** | `npx @pnp/cli-microsoft365-mcp-server` | Microsoft 365 administration — users, groups, SharePoint, Teams |
| **confluence** | `npx mcp-remote https://mcp.atlassian.com/v1/mcp/authv2` | Atlassian Confluence enterprise knowledge base access |
| **git** | `uvx mcp-server-git` | Native Git repository metadata and structural operations |
| **azure-mcp** | `npx @azure/mcp server start` | Azure Resource Manager, Fabric, AI services |
| **fabric-api** | `npx @einlogic/mcp-fabric-api` | Fabric REST API integration |

### Database & Storage MCP
| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **postgres** | `npx @modelcontextprotocol/server-postgres` | PostgreSQL database connection (localhost:5432) |
| **sqlite** | `uvx mcp-server-sqlite --db-path ...` | Local SQLite analytical database instances |
| **mongodb** | `npx mongodb-mcp-server --readOnly` | MongoDB document storage interface |
| **filesystem** | `npx @modelcontextprotocol/server-filesystem` | Local system storage file access |

### Search & Web Research MCP
| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **tavily-search** | `npx tavily-mcp` | AI-powered technical web search optimization |
| **brave-search** | `npx @modelcontextprotocol/server-brave-search` | Brave search engine integration |
| **fetch** | `uvx mcp-server-fetch` | Inline web URL fetching and markdown extraction |
| **browser/playwright** | `npx @playwright/mcp` | Browser automation, screenshots, DOM extraction |
| **puppeteer** | `npx @modelcontextprotocol/server-puppeteer` | Headless Chrome automation scripts |
| **everything-search** | `uvx mcp-server-everything-search` | Universal desktop indexing and global asset search |

### DevOps & Productivity MCP
| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **github** | `npx @modelcontextprotocol/server-github` | GitHub API interaction — repos, PRs, issues |
| **docker** | `npx docker-mcp-server` | Container ecosystem and image orchestration |
| **n8n** | `npx n8n-mcp` | Multi-app workflow automation |
| **memory** | `npx @modelcontextprotocol/server-memory` | Persistent local agent core graph memory |
| **supermemory** | `https://mcp.supermemory.ai/mcp` | Cloud-scale AI memory and knowledge storage |
| **context7** | `npx @upstash/context7-mcp` | Web operational context and content analysis |
| **sequential-thinking**| `npx @modelcontextprotocol/server-sequential-thinking` | Advanced chain-of-thought reasoning automation |

### Document Processing MCP
| Server | Command | Purpose |
| :--- | :--- | :--- |
| **docconvert** | `pdf2odt_mcp_server.py` | Specialized PDF to ODT document conversion |
| **docling** | `uvx --from=docling-mcp docling-mcp-server` | High-fidelity document structural parsing |
| **markitdown** | `npx markitdown-mcp-npx` | Multi-format legacy file to Markdown conversion |
| **pdf2docx** | `npx @youhaozhao/pdf2docx-mcp` | PDF structural conversion to Word |
| **md-pdf** | `npx md-pdf-mcp` | Markdown rendering into production PDFs |

### Automation & Remote SaaS MCPs
| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **composio** | `https://connect.composio.dev/mcp` | Agent tool platform and third-party SDKs |
| **make** | `npx @makehq/mcp-server` | Make integration scenarios and automation |
| **taskade** | `npx @taskade/mcp-server` | Taskade unified project management sync |
| **shadcn** | `npx shadcn mcp` | UI presentation layer component scaffolding |
| **time** | `uvx mcp-server-time` | Timezone-aware context management |
| **adeu** | `adeu-server.exe` | Local machine binary level utility execution |
| **keboola** | `https://mcp.keboola.com/mcp` | Keboola cloud data platform management |
| **zernio** | `https://mcp.zernio.com/mcp` | Zernio internal system automation |
| **postiz** | `https://api.postiz.com/mcp/{key}` | Distributed social media scheduling |
| **indeed** | `https://mcp.indeed.com/claude/mcp` | Candidate posting and job board search |
| **theirstack** | `https://api.theirstack.com/mcp` | Market signal and lead identification |

## 3. Extended Registry (Available / Non-Active)
* **Asana:** Task management (`https://mcp.asana.com/sse`)
* **Linear:** Agile tracking (`https://mcp.linear.app/mcp`)
* **GitLab:** Repository control (`https://gitlab.com/api/v4/mcp`)
* **Terraform:** IaC management (`hashicorp/terraform-mcp-server`)
* **Firebase:** Server management (`npx firebase-tools mcp`)
* **Greptile:** Code graph understanding (`https://api.greptile.com/mcp`)

---
**Related Documents:**
- [Solution Design](./solution-design.md)
- [Agent Orchestration](./agent-orchestration.md)
- [Engineering Operations](./engineering-operations.md)
