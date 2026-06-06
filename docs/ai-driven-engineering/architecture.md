# AI-Driven Data Engineering — Enterprise Architecture Blueprint

## Executive Overview
This document defines the end-to-end blueprint for an enterprise-grade, AI-driven data engineering platform. The platform establishes a collaborative environment where a multi-agent AI swarm works directly alongside human engineers inside an integrated development environment (IDE). 

The platform uses the Model Context Protocol (MCP) to safely discover source systems, runs automated transpilation and data quality gates within a centralized CI/CD pipeline, and deploys governed, optimized data assets onto unified modern data platforms.

---

## Part 1: The 5-Layer End-to-End Architecture Flow  ### Layer 1: Enterprise Sources & Ingestion
The ingestion layer connects directly to production source systems, abstracting both batch enterprise data and high-frequency streaming events.
* **Core Systems:** SAP ERP, Salesforce CRM, Legacy SQL Server instances, and real-time Webhooks/APIs.
* **Ingestion Engines:** * *Batch/Micro-batch:* Sling CLI, Azure Data Factory (ADF).
    * *Streaming:* Apache Kafka, Azure Event Hubs.

### Layer 2: Model Context Protocol (MCP) Gateway
The MCP Gateway provides a secure, bi-directional communication layer between the development workspace and enterprise metadata, schemas, and documentation.
* **SAP Metadata MCP Server:** Connects directly to the SAP operational data provisioning layer to extract cryptic tables and translate field definitions.
* **Salesforce API MCP Server:** Exposes CRM object models, custom fields, and relationship properties to the workspace safely.
* **SQL Schema MCP Server:** Dynamically queries system catalogs and DDL definitions from legacy databases.
* **Enterprise Knowledge Base MCP Server:** Surfaces internal architecture specifications, corporate data dictionaries, and engineering runbooks out of JIRA and Confluence.
* **Data Lineage & Fabric Copilot API Servers:** Provide live runtime context, operational data execution history, and active platform metrics.

### Layer 3: Collaborative Agent Workspace (VS Code)
The development environment acts as a collaborative cockpit where human engineers interact with a multi-agent engineering swarm.

#### In-IDE AI Coding Assistants
* **GitHub Copilot (Agent Mode):** Provides inline code completions, text-based chat, and semi-autonomous script generation.
* **Claude Code:** A terminal-based developer agent used for multi-file editing, structural refactoring, and local code execution.
* **Cursor AI & Cline:** Background agents that monitor workspace files to implement software modifications autonomously.
* **OpenCode & Codex CLI:** Task routing engines and terminal-based natural language interpreters.

#### Managed Multi-Agent Swarm Roles
* **Business Analyst Agent (Orchestrated via LangGraph):** Translates broad business criteria into precise technical specifications and acceptance criteria.
* **Data Architect Agent (Orchestrated via Semantic Kernel):** Designs data schemas, reviews semantic models, and authors structural Architecture Decision Records (ADRs).
* **Scrum Master Agent (Orchestrated via LlamaIndex Workflows):** Manages project sprint pacing, updates task statuses, and syncs project backlogs automatically with JIRA.
* **Data Engineer Agent (Orchestrated via CrewAI):** Generates execution code, authors dbt models, configures pipelines, and writes infrastructure-as-code files.
* **QA Engineer Agent (Orchestrated via AutoGen):** Generates automated validation test scripts, reviews data profiles, and verifies edge-case parameters.

### Layer 4: CI/CD Testing & Security Validation Gates
When code changes are pushed to source control (GitHub / Azure DevOps), they must pass a series of automated quality gates before production deployment. ### Layer 5: Unified Target Platforms & Governance
The final production layer comprises modern cloud data ecosystems, governed by a unified security framework.

#### Target Ecosystem A: Microsoft Fabric (SaaS Platform)
* **OneLake:** A unified logical data lake that stores all enterprise data assets in open Delta Lake formats.
* **Fabric Data Factory:** Orchestrates low-code data ingestion pipelines and schedules activities.
* **Fabric Data Engineering & Warehouse:** High-performance Synapse Spark notebooks and scalable SQL Warehouses.
* **Real-Time Intelligence:** Captures, parses, and acts upon fast-moving event streams via KQL event streams.
* **Power BI (Direct Lake Mode):** Connects reporting dashboards directly to OneLake Delta tables, delivering fast query performance without separate data refreshes.

#### Target Ecosystem B: Databricks Lakehouse (PaaS Platform)
* **Unity Catalog:** Provides fine-grained, centralized data governance for files, tables, and AI models across clouds.
* **Delta Live Tables (DLT):** Declarative pipelines that automate the deployment and scaling of high-performance data processing.
* **Mosaic AI Framework:** Tools to build, evaluate, deploy, and monitor production-grade generative AI models and custom LLMs.

#### Central Governance & Metadata Catalog
* **Microsoft Purview & Alation:** Provides end-to-end data lineage tracking, enterprise search catalogs, and compliance rule enforcement across both target platforms.
* **OpenLineage & Marquez:** Open-source framework that captures operational metadata from active processing pipelines in real time.

---

## Part 2: Technical Tool & Library Inventory

### AI Agent Frameworks & Execution
* **LangGraph / LangGraph Cloud:** State-controlled, cyclic graph orchestration ideal for complex business logic and multi-agent interaction loops.
* **CrewAI / CrewAI Enterprise:** Role-driven agent systems optimized for sequential execution workflows.
* **AutoGen:** Multi-agent conversation frameworks that allow complex, collaborative problem-solving.
* **Semantic Kernel:** Enterprise-grade SDK developed by Microsoft to integrate LLMs into traditional codebases.
* **LlamaIndex Workflows & LCEL:** Event-driven data processing frameworks and expressive component chains.
* **Hermes Agent:** A scheduled micro-runner built to manage background agent tasks automatically.

### Agent Toolkits & Libraries
* **Composio & Toolhouse:** Integrates AI agents with third-party enterprise tools, authorization pathways, and external APIs.
* **Browser Use:** Allows agents to interact with web interfaces, fill out forms, and navigate browser elements.
* **LangChain Tools:** Specialized libraries that connect models with search engines, math tools, and local terminal execution wrappers.

### Data Engineering Core Ecosystem
* **Orchestration:** Apache Airflow, Dagster, Prefect, Azure Data Factory (ADF).
* **Transformations:** dbt (Data Build Tool), Apache Spark (PySpark, Spark SQL).
* **Quality & Profiling:** Great Expectations, Soda Core.
* **Emerging AI-First Data Tools:** * *Sling:* Light, high-performance data syncing CLI.
    * *SQLGlot:* Multi-dialect SQL parser, translator, and optimizer.
    * *DuckDB & MotherDuck:* In-process analytical databases optimized for fast local query execution.
    * *Evidence:* Code-based business intelligence frameworks for building data applications via markdown and SQL.

### Infrastructure & Operations
* **Terraform:** Infrastructure as Code (Ia laC) tool used to deploy cloud infrastructure repeatably.
* **Docker & Kubernetes:** Containerization runtimes and orchestration platforms used to host custom agent applications.
* **Ansible:** Automated configuration management and environment provisioning engine.
* **Azure DevOps & GitHub Actions:** CI/CD runners, repository hosting, and project kanban tracking. # AI-Driven Data Engineering — Enterprise Architecture Reference

## Overview

This document serves as the comprehensive single-source blueprint for the AI-driven data engineering architecture[cite: 6]. It unifies the functional inventory from `architecture.md` with the complete end-to-end workflow topologies, systemic interactions, and lifecycle stages visually mapped out in `architecture.jpg`. 

The system functions as an enterprise-grade **collaborative multi-agent engineering platform** where AI agents operate alongside humans inside VS Code[cite: 6]. The environment is orchestrated via secure CI/CD pipelines, integrated with source systems through the Model Context Protocol (MCP), managed via bidirectional Scrumboard synchronizations, and deployed across a Medallion pipeline converging into an AI-driven service layer[cite: 6].

---

## 1. DevOps/JIRA Scrumboard (Sprint Lifecycle)

As mapped in `architecture.jpg`, the project management tracking layer sits adjacent to the development workspace, driving continuous alignment through an automated lifecycle loop.

### Sprint Board Lifecycle (AI-Managed)
The system visualizes and tracks execution states across four definitive, automated stages: ### Sync Mechanism
* **Bi-Directional Integration:** Operates via a dedicated **MCP Server Sync** pathway directly connecting the Scrumboard to the VS Code Workspace.
* **Repo ──> DevOps/JIRA:** Structural specification modifications, code commits, and agent-calculated task updates automatically update issue tracking cards[cite: 6].
* **DevOps/JIRA ──> Repo:** State transitions, user priority adjustments, and capacity changes feed directly into active agent context windows[cite: 6].

---

## 2. VS Code — AI Agent Workspace

VS Code acts as the centralized **primary IDE** and localized collaborative execution cockpit where human developers work in tandem with an active multi-agent cluster[cite: 6]. ### AI Coding Assistants (In-IDE)

| Tool | Role |
| :--- | :--- |
| **GitHub Copilot** | AI pair programmer — inline completions, chat, agent mode[cite: 6] |
| **Claude Code** | Terminal-based AI coding agent for complex, multi-file tasks[cite: 6] |
| **Cursor AI** | AI-assisted coding environment with a background execution agent[cite: 6] |
| **Cline** | AI coding assistant optimized for autonomous multi-step task execution[cite: 6] |
| **OpenCode** | Open-source AI coding assistant featuring built-in skill routing[cite: 6] |
| **Codex CLI** | OpenAI-powered native terminal coding and command execution agent[cite: 6] |

### Architecture Workflow Hierarchy
1. **Input Interface:** User intents or code changes pass first through the **AI Coding Assistants** tier.
2. **Orchestration:** Requests are routed directly down into the centralized **Agent Orchestrator** engine.
3. **Delegation:** The Orchestrator decomposes instructions and delegates tasks downward to the target **Specialized Agents** cluster.
4. **Outbound Actions:** 
   * Local changes push outward via the **MCP Protocol** to active system servers.
   * Finalized features issue code outputs via the **Commits Code** pathway into the CI/CD pipeline.

---

## 3. Model Context Protocol (MCP) Servers

The platform utilizes 38 configured MCP servers to establish a **standardized interface** for agents to query tools, access deep file systems, and explore enterprise ecosystems safely[cite: 6]. ### Azure & Microsoft Cloud MCP

| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **fabric** | `npx @microsoft/fabric-mcp server start --mode all` | Microsoft Fabric — Lakehouses, Notebooks, Pipelines, Semantic Models[cite: 6] |
| **microsoft365** | `npx @pnp/cli-microsoft365-mcp-server` | Microsoft 365 administration — users, groups, SharePoint, Teams[cite: 6] |
| **confluence** | `npx mcp-remote https://mcp.atlassian.com/v1/mcp/authv2` | Atlassian Confluence enterprise knowledge base access[cite: 6] |
| **git** | `uvx mcp-server-git` | Native Git repository metadata and structural operations[cite: 6] |
| **azure-mcp** | `npx @azure/mcp server start` | Azure Resource Manager, Fabric, AI services (env: `AZURE_FABRIC_ENABLED=true`)[cite: 6] |
| **fabric-api** | `npx @einlogic/mcp-fabric-api` | Fabric REST API integration[cite: 6] |

### Database & Storage MCP

| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **postgres** | `npx @modelcontextprotocol/server-postgres` | PostgreSQL database connection (localhost:5432)[cite: 6] |
| **sqlite** | `uvx mcp-server-sqlite --db-path ...` | Local SQLite analytical database instances (`.n8n/database.sqlite`)[cite: 6] |
| **mongodb** | `npx mongodb-mcp-server --readOnly` | MongoDB document storage interface (10.26.0.6:27017, read-only)[cite: 6] |
| **filesystem** | `npx @modelcontextprotocol/server-filesystem` | Local system storage file access (`C:\projects`, `Documents`, `Desktop`)[cite: 6] |

### Search & Web Research MCP

| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **tavily-search** | `npx tavily-mcp` | AI-powered technical web search optimization (requires API key)[cite: 6] |
| **brave-search** | `npx @modelcontextprotocol/server-brave-search` | Brave search engine integration (requires API key)[cite: 6] |
| **fetch** | `uvx mcp-server-fetch` | Inline web URL fetching and markdown content extraction[cite: 6] |
| **browser** / **playwright** | `npx @playwright/mcp` | Browser automation — navigation, screenshots, DOM extraction, PDF generation[cite: 6] |
| **puppeteer** | `npx @modelcontextprotocol/server-puppeteer` | Headless Chrome automation scripts[cite: 6] |
| **everything-search** | `uvx mcp-server-everything-search` | Universal desktop indexing and global asset search[cite: 6] |

### DevOps & Productivity MCP

| Server | Command / URL | Purpose |
| :--- | :--- | :--- |
| **github** | `npx @modelcontextprotocol/server-github` | GitHub API interaction — repos, PR management, issues (requires PAT)[cite: 6] |
| **docker** | `npx docker-mcp-server` | Container ecosystem, volume, and active image orchestration[cite: 6] |
| **n8n** | `npx n8n-mcp` | Multi-app workflow automation (localhost:5678, Webhook security)[cite: 6] |
| **memory** | `npx @modelcontextprotocol/server-memory` | Persistent local agent core graph memory tracking (`memory.json`)[cite: 6] |
| **supermemory** | `https://mcp.supermemory.ai/mcp` | Cloud-scale AI memory and aggregated knowledge storage[cite: 6] |
| **context7** | `npx @upstash/context7-mcp` | Web operational context and text content analysis[cite: 6] |
| **sequential-thinking**| `npx @modelcontextprotocol/server-sequential-thinking` | Advanced multi-step chain-of-thought reasoning automation[cite: 6] |

### Document Processing MCP

| Server | Command | Purpose |
| :--- | :--- | :--- |
| **docconvert** | Python script (`pdf2odt_mcp_server.py`) | Specialized PDF to ODT document conversion[cite: 6] |
| **docling** | `uvx --from=docling-mcp docling-mcp-server` | High-fidelity document structural parsing and analysis[cite: 6] |
| **markitdown** | `npx markitdown-mcp-npx` | Multi-format legacy file to Markdown conversion[cite: 6] |
| **pdf2docx** | `npx @youhaozhao/pdf2docx-mcp` | PDF structural conversion into Microsoft Word files[cite: 6] |
| **md-pdf** | `npx md-pdf-mcp` | Markdown documentation rendering into production PDFs[cite: 6] |

### Automation, Utilities & Remote SaaS MCPs

| Server | Command / Connection URL | Purpose |
| :--- | :--- | :--- |
| **composio** | `https://connect.composio.dev/mcp` | Agent tool platform featuring custom LinkedIn SDK app integrations[cite: 6] |
| **make** | `npx @makehq/mcp-server` | Make integration scenarios and multi-app workflow automation[cite: 6] |
| **taskade** | `npx @taskade/mcp-server` | Taskade unified collaborative project management sync[cite: 6] |
| **shadcn** | `npx shadcn mcp` | UI presentation layer component scaffolding system[cite: 6] |
| **time** | `uvx mcp-server-time --local-timezone=...` | Timezone-aware context management (Australia/Melbourne)[cite: 6] |
| **adeu** | `adeu-server.exe` | Local machine binary level utility execution[cite: 6] |
| **keboola** | `https://mcp.keboola.com/mcp` | Keboola cloud data platform environment management[cite: 6] |
| **zernio** | `https://mcp.zernio.com/mcp` | Zernio internal system task automation[cite: 6] |
| **postiz** | `https://api.postiz.com/mcp/{key}` | Distributed multi-platform social media scheduling[cite: 6] |
| **indeed** | `https://mcp.indeed.com/claude/mcp` | Live candidate posting and target job board search[cite: 6] |
| **theirstack** | `https://api.theirstack.com/mcp` | TheirStack market signal and recruitment lead identification[cite: 6] |

### Extended Plugin Registries (Available / Non-Active Status)
* **asana:** `https://mcp.asana.com/sse` (Asana workspace task management)[cite: 6]
* **linear:** `https://mcp.linear.app/mcp` (Linear agile software tracking)[cite: 6]
* **gitlab:** `https://gitlab.com/api/v4/mcp` (GitLab alternative repository control)[cite: 6]
* **terraform:** `hashicorp/terraform-mcp-server` (Terraform Cloud IaC management)[cite: 6]
* **firebase:** `npx firebase-tools mcp` (Firebase application server management)[cite: 6]
* **greptile:** `https://api.greptile.com/mcp` (AI code graph understanding engine)[cite: 6]

---

## 4. AI Agents (Inside VS Code Workspaces)

Five highly specialized agent roles act collaboratively inside the workspace environment under the direction of the core **Agent Orchestrator**[cite: 6].

### Agent Orchestrator Core Capabilities
* **Task Decomposition:** Breaks abstract business requests into decoupled tasks[cite: 6].
* **Delegation Framework:** Directly dispatches workloads to assigned specialist profiles[cite: 6].
* **Context Preservation:** Coordinates shared token states and execution memory limits[cite: 6].
* **Event Brokerage:** Drives communication across agents using an active internal messaging loop[cite: 6].

### Specialized Agent Tool & Responsibility Matrices

#### Business Analyst Agent
* **Responsibilities:** requirement gathering, translation of features to explicit Gherkin / BDD assertions, workflow constraint definitions[cite: 6].
* **Outputs:** User stories, system data flows, BDD file specs, clear acceptance parameters[cite: 6].

#### Architect Agent
* **Responsibilities:** System pattern blueprints, tech stack alignment, validation of structural compliance rules, schema boundary definitions[cite: 6].
* **Outputs:** Architecture Decision Records (ADRs), data contracts, interface schemas, blueprint specs[cite: 6].

#### Scrum Master Agent
* **Responsibilities:** Automated agile sprint mapping, bottleneck resolution, task metadata extraction, and JIRA board tracking[cite: 6].
* **Outputs:** Task break-outs, execution velocity indexes, capacity summaries[cite: 6].

#### Data Engineer Agent
* **Responsibilities:** Data pipeline programming, analytical transformation definitions, orchestration configs, infrastructure code design[cite: 6].
* **Outputs:** Native pipeline code, dbt models, Airflow DAG files, declarative Terraform scripts[cite: 6].

#### QA Engineer Agent
* **Responsibilities:** Quality metric profiling, assertion checking, compliance auditing, integration script verification[cite: 6].
* **Outputs:** Great Expectations test configurations, run validations, issue dashboards, regression scripts[cite: 6].

---

## 5. CI/CD & DevOps Pipeline

The integration pipeline acts as an automated gateway validating everything from basic structural correctness to specialized security compliance postures[cite: 6].

[ Git Repo ] ──(Triggers)──> [ Build Lint/Unit ] ──> [ Test Int/QA ] ──> [ Deploy IaC ] ──> [ Promote ]
▲
│ (Scans PR)
┌──────────────────────────┐
│ Azure DevOps Sec Agent   │
│ SAST - Dep Scan - IaC Sec│
│ Data Sec - Compliance - AI│
└──────────────────────────┘


### End-to-End Pipeline Stages

1. **Git Repo (Source of Truth):** Code commits coming out of the VS Code Workspace trigger the runner sequence[cite: 6]. Handles tracking for all specs, code, contracts, IaC files, and sprint metrics[cite: 6].
2. **Build Lint / Unit:** Compilation checks, syntax lints, type checks, and isolated unit test validations[cite: 6].
3. **Test Int / QA:** Execution of multi-layered integration steps and automated data quality checks[cite: 6]. This phase is actively inspected by the **Azure DevOps Security Agent** via automated PR hooks[cite: 6].
4. **Deploy IaC / Schema:** Applies verified Terraform/Bicep infrastructure and triggers target database schema upgrades[cite: 6].
5. **Promote Dev ──> Prod:** Safely routes functional build states across environments through structured verification gates[cite: 6].

### Azure DevOps Security Agent Audit Layers
During the PR testing phase, the security agent inspects the code across six distinct vectors:
* **SAST:** Evaluates the codebase to identify hidden structural security flaws[cite: 6].
* **Dependency Scan:** Validates packages against open CVE databases to ensure licensing compliance[cite: 6].
* **IaC Security:** Scans Terraform configurations to catch deployment infrastructure risks[cite: 6].
* **Data Security Scan:** Reviews query structures to prevent PII exposure and bad access patterns[cite: 6].
* **Compliance Check:** Validates pipeline paths against GDPR, SOC2, HIPAA, and internal policies[cite: 6].
* **AI Code Review:** Evaluates code alignment against established enterprise engineering standards[cite: 6].

---

## 6. Data Engineering Medallion Pipeline

Data flows sequentially through a 3-tier Medallion architecture, movin ### Bronze — Raw Ingestion
* **Supported Source Streams:** Relational SQL DBs, Application APIs, unstructured Files, Raw Lakes, Event Streams, and PDFs.
* **Operational Goal:** Land raw, unmodified upstream data histories directly into storage layers[cite: 6].

### Silver — Transformation
* **Processing Frameworks:** Managed dbt configurations, Apache Spark compute, Apache Airflow scheduling, Great Expectations (QE)/Soda data validations, and Azure Data Factory (ADF) pipeline tasks[cite: 6].
* **Core Operations:** Executes schema definition mapping, field normalization filtering, cleansing, and metadata enrichment stages.

### Gold — Curated Data
* **Data Storage Subsystems:** Azure Synapse data warehouses, open Delta Lake layers, Feast feature storage, unified enterprise catalogs, and Graph Databases[cite: 6].
* **Core Operations:** Aggregates multi-source information into business entities, analytical data products, optimized feature spaces, and graph topologies.

---

## 7. AI Platform Convergence Stack

At the base of the processing flow, the pipeline feeds into two parallel data pathways that converge into a unified enterprise AI environment.