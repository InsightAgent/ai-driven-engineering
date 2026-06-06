# Agent Orchestration & Collaborative Workspace

## 1. The Collaborative Cockpit (VS Code)
The development environment serves as the primary interaction point where human engineers and the AI agent cluster operate in a tight feedback loop.

### AI Coding Assistants (In-IDE)
These tools provide the immediate interface for intent capture and code generation:
* **GitHub Copilot (Agent Mode):** Inline completions and semi-autonomous script generation.
* **Claude Code:** Terminal-based agent for structural refactoring and local execution.
* **Cursor AI & Cline:** Background agents for autonomous workspace modifications.
* **OpenCode & Codex CLI:** Natural language interpreters and task routing.

## 2. Agent Orchestration Framework

### The Orchestrator Core
The **Agent Orchestrator** acts as the brain of the swarm, managing the following critical functions:
* **Task Decomposition:** Breaking abstract business requests into decoupled, actionable tasks.
* **Delegation:** Routing workloads to the most appropriate specialized agent profile.
* **Context Preservation:** Managing shared token states and execution memory limits.
* **Event Brokerage:** Facilitating inter-agent communication via internal messaging loops.

### Specialized Agent Role Matrix

| Agent Role | Primary Responsibilities | Key Outputs |
| :--- | :--- | :--- |
| **Business Analyst** | Requirement gathering, BDD/Gherkin translation, constraint definition | User Stories, BDD Specs, Acceptance Criteria |
| **Architect** | System blueprints, tech stack alignment, schema boundary definition | ADRs, Data Contracts, Interface Schemas |
| **Scrum Master** | Agile sprint mapping, bottleneck resolution, JIRA synchronization | Task Break-outs, Velocity Indexes, Capacity Reports |
| **Data Engineer** | Pipeline programming, transformation logic, IaC design | dbt Models, Airflow DAGs, Terraform Scripts |
| **QA Engineer** | Quality profiling, compliance auditing, integration verification | Great Expectations Configs, Validation Reports |

## 3. Architecture Workflow Hierarchy
1. **Input:** User intent is captured by **AI Coding Assistants**.
2. **Routing:** Requests are parsed by the **Agent Orchestrator**.
3. **Execution:** Tasks are delegated to **Specialized Agents**.
4. **Action:** Agents interact with systems via **MCP** or push code to **CI/CD**.

---
**Related Documents:**
- [Solution Design](./solution-design.md)
- [MCP Catalog](./mcp-catalog.md)
- [Engineering Operations](./engineering-operations.md)
