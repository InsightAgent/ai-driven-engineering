# AI-Driven Data Engineering — Architecture Reference

## Overview

This document catalogs every component in the AI-driven data engineering architecture. The system is a **collaborative multi-agent engineering platform** where AI agents work alongside humans inside VS Code, orchestrated through CI/CD, connected to enterprise source systems via MCP, and governed by security review gates.

See the accompanying draw.io diagrams in `docs/` for visual reference:
- `1 ai-driven-data-engineering.drawio` — End-to-end architecture (5 layers)
- `2 ai-agent-workspace-detail.drawio` — AI agent workspace internals
- `3 devops-integration-detail.drawio` — DevOps / JIRA integration
- `4 data-pipeline-detail.drawio` — Medallion pipeline architecture
- `5 copilot-solution-architecture.drawio` — Copilot convergence (unstructured + structured data)

---

## 1. VS Code — AI Agent Workspace

VS Code is the **primary IDE** and serves as the collaborative workspace where AI agents operate alongside the human engineer.

### AI Coding Assistants (in-IDE)

| Tool | Role |
|------|------|
| **GitHub Copilot** | AI pair programmer — inline completions, chat, agent mode |
| **Claude Code** | Terminal-based AI coding agent for complex tasks |
| **OpenCode** | Open-source AI coding assistant with skill routing |
| **Cursor AI** | AI-assisted coding with background agent |
| **Cline** | AI coding assistant for autonomous task execution |
| **Codex CLI** | OpenAI-powered terminal coding agent |

### Key VS Code Capabilities

- Multi-agent collaboration (Business Analyst, Architect, Scrum Master, Data Engineer, QA Engineer agents all operate within VS Code)
- MCP endpoint integration (knowledge bases, source systems, Fabric)
- Extension-driven tool execution
- Terminal integration for CLI tools (dbt, Airflow, Terraform, git)
- Source control integration (GitHub, Azure DevOps)

---

## 2. Model Context Protocol (MCP) Endpoints

MCP provides a **standardised interface** for AI agents to interact with tools and data sources.

### Engineering Knowledge & Standards MCP

| Endpoint | Purpose |
|----------|---------|
| **Engineering Knowledge Base** | RAG over past ADRs, architecture decisions, data models, security policies, company standards |
| **Code Standards** | Linting rules, style guides, best-practice checkers, anti-pattern detection |
| **Engineering Framework** | Project templates, pipeline scaffolds, IaC modules, CI/CD templates, data contract schemas |

### Source Systems MCP

| Endpoint | Purpose |
|----------|---------|
| **Dynamic CRM** | Schema exploration, entity relationship discovery, data profiling, sample queries |
| **SAP** | Table exploration, data profiling, extraction pattern discovery |
| **SQL Server / Oracle / PostgreSQL** | Database introspection, query execution, schema comparison |
| **Kafka / Event Hubs** | Topic discovery, schema registry interaction, sample message inspection |

### Microsoft Fabric MCP

| Endpoint | Purpose |
|----------|---------|
| **Fabric Notebooks** | Publish and execute Spark / Python notebooks |
| **Fabric Data Pipelines** | Deploy and trigger pipeline runs |
| **Fabric Semantic Models** | Query and publish Power BI datasets |
| **Fabric Lakehouse** | Read/write Delta tables, explore lakehouse structure |
| **Fabric Dataflows Gen2** | Deploy and monitor dataflows |
| **Fabric QA** | Validate data quality rules, run expectation suites, publish test results |

### Other MCP Endpoints Referenced

| Endpoint | Purpose |
|----------|---------|
| `WebFetch` / `tavily-search` / `brave-search` | Web research |
| `user-playwright` | PDF generation, browser automation |
| `user-docconvert` | DOCX conversion from HTML |
| `composio` | LinkedIn SDK integration |

---

## 3. AI Agents (Inside VS Code)

Five specialised agents collaborate within the VS Code workspace, orchestrated by the **Agent Orchestrator**.

### Agent Orchestrator

- **Task decomposition** — Breaks high-level goals into agent-assignable tasks
- **Delegation** — Routes tasks to the appropriate specialist agent
- **Context management** — Maintains shared context window across agents
- **Conflict resolution** — Mediates agent disagreements (e.g., architect vs. engineer on tech choice)
- **Event-driven messaging** — Agents communicate via shared context / message bus

### 3.1 Business Analyst Agent

| Aspect | Detail |
|--------|--------|
| **Responsibilities** | Elicit/refine requirements, write acceptance criteria (Gherkin), define data requirements & business rules, map data flow & transformation logic |
| **Tools** | VS Code, Markdown, BDD frameworks |
| **Outputs** | User stories, acceptance criteria, data requirements, flow diagrams |

### 3.2 Architect Agent

| Aspect | Detail |
|--------|--------|
| **Responsibilities** | Design system architecture, select tech stack & patterns, define data contracts & schemas, ensure scalability & compliance |
| **Tools** | Draw.io, ADRs, C4 model, MCP endpoints for knowledge base |
| **Outputs** | Architecture Decision Records (ADRs), data contracts, schema definitions, stack recommendations |

### 3.3 Scrum Master Agent

| Aspect | Detail |
|--------|--------|
| **Responsibilities** | Break work into sprint tasks, track progress & dependencies, sync with Azure DevOps / JIRA boards, manage capacity & velocity |
| **Tools** | JIRA API, sprint metrics, MCP for board sync |
| **Outputs** | Sprint tasks, velocity metrics, dependency maps, retrospective data |

### 3.4 Data Engineer Agent

| Aspect | Detail |
|--------|--------|
| **Responsibilities** | Build & optimise data pipelines, implement data quality checks, manage data catalog & lineage, deploy infra with IaC |
| **Tools** | dbt, Airflow, Spark, SQL, Terraform, MCP for Fabric & source systems |
| **Outputs** | Pipeline code & config, IaC modules, data quality suites, lineage metadata |

### 3.5 QA Engineer Agent

| Aspect | Detail |
|--------|--------|
| **Responsibilities** | Validate data quality & accuracy, run Great Expectations tests, verify acceptance criteria, generate test reports & dashboards |
| **Tools** | Great Expectations, Soda, pytest, CI integration, MCP for Fabric QA |
| **Outputs** | Quality test suites, test reports, dashboards, regression suites |

---

## 4. AI Agents (Outside VS Code — CI/CD & Operations)

### 4.1 Azure DevOps CI/CD Security Agent

Runs as part of the PR pipeline in Azure DevOps. Automated analysis stages:

| Stage | What It Checks |
|-------|----------------|
| **SAST** | Static code analysis for vulnerabilities |
| **Dependency Scan** | CVEs, license compliance in packages |
| **IaC Security** | Terraform / ARM / Bicep misconfigurations |
| **Data Security Scan** | Data access patterns, PII exposure |
| **Compliance Check** | GDPR, SOC2, HIPAA, organisational policies |
| **AI Code Review** | Best practices, anti-patterns, architecture conformance |

- Results posted as PR comments
- Auto-approve / Request changes / Block outcomes
- Merge gate: all checks must pass before merge

### 4.2 PR Code Review Agent

- Triggered by Azure DevOps PR hook
- Analyses diff against code standards MCP
- Checks data contract adherence
- Validates test coverage
- Reviews IaC changes for drift
- Posts structured review as PR comments

---

## 5. CI/CD & DevOps Pipeline

### Git Repository — Single Source of Truth

```
main → develop → feature/*
```

**Repository contents:**
- Specs & user stories
- Pipeline code & configs
- Data contracts & schemas
- Quality test suites
- IaC (Terraform, ARM, Bicep)
- Estimates & velocity data

### CI/CD Pipeline Stages

| Stage | Actions |
|-------|---------|
| **Build** | Compile, lint, type-check, unit tests |
| **Test** | Integration tests, data quality checks, Great Expectations |
| **Deploy** | IaC apply, pipeline deployment, schema migration |
| **Promote** | Dev → Staging → Production with approval gates |

### AI-Driven Retrospective & Continuous Improvement

- Velocity trends & quality metrics
- Bottleneck detection
- Process improvement suggestions
- Agent fine-tuning feedback (feeds back to Agent Orchestrator)

---

## 6. Scrum Dashboard (Bidirectional Sync)

The Scrum dashboard syncs user stories bidirectionally between the Git repository and Azure DevOps / JIRA.

### Sync Direction

| From | To | Data |
|------|----|------|
| **Repo → DevOps/JIRA** | Spec revisions → user stories, code changes → task estimates |
| **DevOps/JIRA → Repo** | Sprint progress → velocity metrics, task assignments → agent context, board status → spec revisions, retro data → process improvements |

### Sync Mechanism

- **Event-driven** (webhooks) + **Scheduled** sync
- **Conflict resolution**: Repo wins on specs, JIRA wins on status

### Sprint Board Lifecycle (AI-Managed)

```
Backlog (AI priority score)
  → Sprint Backlog (velocity tracking)
    → In Progress (with AI ETA)
      → Review / QA (PR tracking)
        → Done
```

---

## 7. Data Engineering Pipeline — Medallion Architecture

### Bronze — Raw Data Ingestion

| Source Type | Examples |
|-------------|----------|
| **Databases** | SQL Server, Oracle, PostgreSQL |
| **APIs & Streams** | REST, Kafka, Event Hubs |
| **Files** | PDF, CSV, JSON, Avro, Parquet |
| **Data Lakes** | ADLS Gen2, S3 |

### Silver — Transformation & Processing

| Tool | Purpose |
|------|---------|
| **dbt** | SQL transformations |
| **Spark** | Large-scale processing |
| **Airflow / Dagster / Prefect** | Orchestration |
| **Azure Data Factory** | Cloud orchestration |
| **Great Expectations / Soda** | Data quality |

### Gold — Curated Data & Storage

| Store | Purpose |
|-------|---------|
| **Synapse / Snowflake / Redshift** | Analytical datastores |
| **Delta Lake / Iceberg** | Lakehouse storage |
| **Feast / Tecton** | Feature store |
| **Alation / Collibra / Purview** | Data catalog |

### Cross-Cutting AI Platform

| Component | Tools |
|-----------|-------|
| **Pipeline Orchestrator** | Airflow, Dagster, Prefect, ADF |
| **Data Quality & Testing** | Great Expectations, Soda, dbt tests |
| **Data Lineage** | OpenLineage, Marquez, Atlan |
| **Schema Registry & Contracts** | Avro, Protobuf, Data Contracts |
| **Observability & Monitoring** | Monte Carlo, Sifflet, cost tracking |

---

## 8. Copilot & AI Platform Convergence

Dual-path convergence into the Azure OpenAI / Copilot stack:

### Unstructured Knowledge Path (Workflow 1)

```
SharePoint PDFs & Docs
  → PDF/Doc Extraction Agent (Azure Doc Intelligence)
    → Bronze: Raw files & extracted content
      → Silver: Semantic Chunking Agent + Knowledge Classification Agent
        → Gold: Metadata Enrichment Agent → Embeddings + Enriched Metadata
          → Azure AI Search (vector index + hybrid search)
```

### Structured Business Data Path (Workflow 2)

```
CRM, ERP & Operational Systems
  → Bronze: Raw data (CDC)
    → Silver: Cleansed & transformed
      → Gold: Curated business entities + entity relationship mapping
        → Graph Database (GraphQL)
```

### Convergence Stack

| Layer | Components |
|-------|------------|
| **LLM Models** | Azure OpenAI GPT-4o, GPT-4-turbo, text-embedding-ada |
| **AI Gateway** | Rate limiting, authentication, logging, cost tracking |
| **Microsoft Foundry AI** | Orchestration, prompt management, monitoring, safety |
| **Microsoft 365 Copilot** | Natural language interface, context-aware answers, actions |
| **Users** | Ask questions grounded in org data |

---

## 9. Skills Framework

The project uses a **skill-routing agent framework** where an orchestrator agent dispatches to specialised `SKILL.md` files based on user intent.

| Skill | Purpose |
|-------|---------|
| `build-profile` | Build/refresh `profile.yaml` from source resume DOCX |
| `search-jobs` | Search portals, score jobs, write JD HTML, wish-list YAML |
| `write-resume` | Tailor resume + cover letter, render PDFs, track submissions |
| `interview-prep` | Research + YAML + interactive HTML dashboard + PDF/DOCX reports |
| `create-dashboard` | Create interactive HTML dashboard from text/PDF/Word |
| `make-infographic` | HTML → PNG infographics for LinkedIn and decks |
| `linkedin-daily-posts` | Daily paired Posts + Articles |
| `write-linkedin-comments` | Scheduled feed engagement |
| `create-linkedin-comments` | Interactive composio-driven LinkedIn commenting |

---

## 10. Observability & Cross-Cutting Concerns

| Concern | Implementation |
|---------|----------------|
| **Observability & Monitoring** | Pipeline health, data freshness, volume anomalies |
| **Cost Tracking & Optimization** | Pipeline compute, storage, AI agent API costs |
| **ChatOps** | Slack / Teams — sprint updates, PR summaries, quality alerts |
| **Incident Management** | PagerDuty / Opsgenie — pipeline failures, data quality incidents |

---

## 11. Data Consumers

| Consumer | Interface |
|----------|-----------|
| **Power BI / Tableau / Looker** | BI dashboards and reports |
| **APIs & Data Products** | REST / GraphQL endpoints, data mesh |
| **ML Models & Reports** | MLflow, automated reporting, regulatory |
| **Data Sharing & Collaboration** | Data marketplace, cross-team catalogs |
| **Azure OpenAI / Copilot** | Natural language Q&A over org data |

---

## 12. Technology Stack Summary

### AI Models

| Provider | Models |
|----------|--------|
| **OpenAI** | GPT-4o, GPT-4-turbo, o1, o3, text-embedding-ada |
| **Anthropic** | Claude Opus 4, Sonnet 4, Haiku 4 |
| **DeepSeek** | R1, V3, V4 |
| **Google** | Gemini 2.5 Pro, 2.5 Flash |
| **Meta** | Llama 4, Llama 3 |
| **Mistral** | Large, Mixtral |

### Agent Frameworks

| Framework | Purpose |
|-----------|---------|
| **LangChain / LangGraph** | LLM application framework |
| **CrewAI / AutoGen** | Multi-agent orchestration |
| **Claude Agent SDK** | Anthropic agent development |
| **OpenAI Agents SDK** | OpenAI agent development |
| **Azure AI Foundry Agents** | Microsoft agent framework |
| **Amazon Bedrock Agents** | AWS agent framework |
| **Databricks Mosaic Agent Framework** | Databricks agent orchestration |
| **Hermes Agent** | Scheduled AI agent runner |

### Infrastructure & IaC

| Tool | Purpose |
|------|---------|
| **Terraform** | Infrastructure as Code |
| **Docker** | Containerisation |
| **Kubernetes** | Container orchestration |
| **Azure DevOps** | CI/CD pipelines and boards |
| **n8n** | Workflow automation |

### Data Tools

| Category | Tools |
|----------|-------|
| **Orchestration** | Airflow, Dagster, Prefect, ADF |
| **Transformations** | dbt, Spark |
| **Quality** | Great Expectations, Soda |
| **Lineage** | OpenLineage, Marquez, Atlan |
| **Catalog** | Alation, Collibra, Purview |
| **Storage** | ADLS Gen2, S3, Delta Lake, Iceberg |
| **Compute** | Synapse, Snowflake, Redshift, Databricks |
| **Streaming** | Kafka, Event Hubs |

---

## Reference Diagrams

| File | Content |
|------|---------|
| `docs/1 ai-driven-data-engineering.drawio` | End-to-end 5-layer architecture |
| `docs/2 ai-agent-workspace-detail.drawio` | AI agent workspace with 5 agents |
| `docs/3 devops-integration-detail.drawio` | DevOps/JIRA PR security + sync flow |
| `docs/4 data-pipeline-detail.drawio` | Medallion pipeline with bronze/silver/gold |
| `docs/5 copilot-solution-architecture.drawio` | Copilot convergence (knowledge + business data paths) |
