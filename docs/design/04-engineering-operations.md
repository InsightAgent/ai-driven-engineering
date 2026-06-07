# Engineering Operations & Data Pipeline

**Status:** `Draft` | **Version:** `1.0.0` | **Domain:** `Delivery Layer`

## 1. The Autonomous CI/CD Pipeline
The delivery pipeline is not just a deployment script; it is a **Governed Gateway**. It ensures that AI-generated code is structurally sound and security-compliant before it ever touches a production environment.

### 1.1 Pipeline Topology
`[ Git Repo ]` $\rightarrow$ `[ Build/Lint/Unit ]` $\rightarrow$ `[ Integration/QA ]` $\rightarrow$ `[ IaC Deployment ]` $\rightarrow$ `[ Global Promotion ]`

### 1.2 The Security Agent Audit (PR Gate)
Every pull request is intercepted by the **Azure DevOps Security Agent**, which performs a six-dimensional audit:
* **SAST (Static Analysis):** Identifying structural security flaws and logic vulnerabilities.
* **SCA (Software Composition Analysis):** Scanning dependencies against Open CVE databases.
* **IaC Validation:** Vetting Terraform/Bicep for "over-privileged" resources or insecure networking.
* **Data Privacy Scan:** Detecting potential PII leakage or improper access patterns in SQL.
* **Compliance Guardrails:** Validating paths against GDPR, SOC2, and HIPAA.
* **AI Quality Review:** Ensuring code adheres to the enterprise "Clean Code" standard.

---

## 2. Data Architecture: The Medallion Framework
The platform implements a sequenced transformation pipeline to move data from raw chaos to curated business intelligence.

### 2.1 Bronze Layer (Raw Ingestion)
* **Objective:** Absolute fidelity. Data is landed in its original form.
* **Sources:** Relational DBs, Event Streams, PDFs, and Legacy APIs.
* **Standard:** Append-only, immutable history.

### 2.2 Silver Layer (Curated Transformation)
* **Objective:** Trust and Consistency.
* **Engineering Stack:** `Sling` $\rightarrow$ `dbt` $\rightarrow$ `Apache Spark` $\rightarrow$ `Great Expectations`.
* **Operations:** Schema normalization, cleansing, and metadata enrichment.

### 2.3 Gold Layer (Analytical Products)
* **Objective:** High-performance business consumption.
* **Storage:** Azure Synapse, Delta Lake, and Graph Databases.
* **Output:** Optimized feature sets for AI models and Power BI Direct Lake tables.

---

## 3. Technical Ecosystem Inventory

### 🤖 AI Agent Frameworks
* **Core Orchestration:** LangGraph (Cyclic/Stateful), CrewAI (Role-based), AutoGen (Conversational).
* **Enterprise SDKs:** Semantic Kernel (Microsoft), LlamaIndex Workflows.
* **Task Scheduling:** Hermes Agent.

### 🛠️ Engineering Toolkit
* **Orchestration:** Airflow, Dagster, Azure Data Factory (ADF).
* **Transformation:** dbt, Spark SQL, SQLGlot (Multi-dialect translation).
* **Quality:** Great Expectations, Soda Core.
* **Local Analytics:** DuckDB, MotherDuck, Evidence.md.

### ⚙️ Infrastructure & Ops
* **IaC:** Terraform, Bicep.
* **Runtime:** Docker, Kubernetes.
* **Provisioning:** Ansible.
* **CI/CD:** GitHub Actions, Azure DevOps.

---
**Navigation:**
- 🏛️ **Back to Blueprint:** [Solution Design](./01-solution-design.md)
- 🤖 **Agent Logic:** [Agent Orchestration](./agent-orchestration.md)
- 🔌 **Connector Map:** [MCP Catalog](./mcp-catalog.md)
