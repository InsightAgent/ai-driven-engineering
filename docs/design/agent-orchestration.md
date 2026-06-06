# Agent Orchestration & Collaborative Workspace

**Status:** `Draft` | **Version:** `1.0.0` | **Domain:** `Intelligence Layer`

## 1. The "Human-in-the-Loop" IDE Cockpit
The platform transforms the IDE (VS Code) from a text editor into a **Collaborative Execution Cockpit**. The human engineer transitions from a "coder" to an "orchestrator," managing a swarm of specialized AI agents.

### 1.1 Interface Tier: The Gateway to Intent
User intents are captured via three primary channels, depending on the task granularity:
* **Inline Flow (GitHub Copilot):** For atomic changes, immediate completions, and localized refactoring.
* **Agentic Flow (Claude Code / Cline):** For multi-file structural changes and autonomous task execution.
* **Command Flow (OpenCode / Codex CLI):** For system-level operations, tool routing, and natural language terminal control.

---

## 2. Swarm Architecture & Orchestration

### 2.1 The Orchestrator Engine
The **Agent Orchestrator** is the central nervous system. It prevents "context drift" by acting as the single source of truth for task state.

**Core Operational Logic:**
1. **Decomposition:** Large goals (e.g., "Build a Salesforce to Fabric pipeline") are split into a directed acyclic graph (DAG) of sub-tasks.
2. **Dynamic Delegation:** Tasks are routed based on the **Responsibility Matrix**.
3. **Memory Synchronization:** The orchestrator ensures that a decision made by the *Architect Agent* is immediately injected into the *Data Engineer Agent's* context.
4. **Verification Loop:** Before any "Outbound Action" (Commit/Deploy), a verification request is sent to the *QA Agent*.

### 2.2 Specialized Agent Responsibility Matrix

| Role | Archetype | Core Responsibility | Primary Output | Critical Tooling |
| :--- | :--- | :--- | :--- | :--- |
| **Business Analyst** | `Translator` | Convert business ambiguity $\rightarrow$ technical precision | Gherkin Specs, BDD Assertions | Confluence MCP, JIRA MCP |
| **Architect** | `Governor` | Define structural boundaries & technical compliance | ADRs, Data Contracts, Schema | Schema MCP, Architecture Templates |
| **Scrum Master** | `Synchronizer` | Manage delivery velocity & backlog health | Sprint Maps, Task Break-outs | JIRA Sync, Velocity Metrics |
| **Data Engineer** | `Implementer` | Translate design $\rightarrow$ executable code | Spark SQL, dbt, Terraform | Fabric API, Git MCP, SQL MCP |
| **QA Engineer** | `Validator` | Verify correctness & performance compliance | Great Expectations, Validation Reports | Soda Core, Data Profilers |

---

## 3. The Operational Flow (End-to-End)

### 3.1 The Implementation Cycle
The interaction follows a recursive a-synchronous loop:

`User Intent` $\rightarrow$ `Orchestrator` $\rightarrow$ `Specialist Agent (Analysis/Design)` $\rightarrow$ `MCP Query` $\rightarrow$ `Proposal` $\rightarrow$ `Human Approval` $\rightarrow$ `Specialist Agent (Code)` $\rightarrow$ `Git Commit`

### 3.2 Context Management Strategy
To avoid token exhaustion and "forgetting," the orchestrator implements:
* **Surgical Context Injection:** Only providing the agent with the specific files and MCP-fetched schemas needed for the current sub-task.
* **Persistent Memory Graph:** Using a graph-based memory system to track cross-agent dependencies.

---
**Navigation:**
- 🏛️ **Back to Blueprint:** [Solution Design](./01-solution-design.md)
- 🔌 **Connectivity Details:** [MCP Catalog](./mcp-catalog.md)
- ⚙️ **Delivery Pipeline:** [Engineering Operations](./engineering-operations.md)
