# Architectural Diagrams from Markdown: AI Plugins & Workflows

To generate architectural diagrams directly from Markdown using **Claude Code** or **OpenCode**, you can leverage several highly optimized native plugins and "Skills". Because OpenCode natively supports importing Claude Code plugins, commands, and Model Context Protocol (MCP) configs, these tools can be used interchangeably across both platforms.

Here are the best dedicated AI plugins and tools to build text-to-diagram workflows:

---

## 1. Dedicated OpenCode & Claude Plugins

* **Cartograph (Native OpenCode Plugin)**
  * **What it does:** Specifically built for OpenCode terminal agents. It scans your directory structures or Markdown design documents and continuously updates architectural maps in the background as you or your AI agent code.
  * **Output:** Saves code-first diagrams inside a `.architecture/` folder in your repository.
  * **Source:** `cloudshipai/cartograph`
* **claude-diagrams (Kroki-backed Plugin)**
  * **What it does:** An open-source plugin requiring zero API keys. It translates your system description text or file paths (like markdown design docs) into over 20+ types of code-first diagramming types.
  * **Output:** Automatically handles compilation via Kroki.io into visual maps. Supports Mermaid, PlantUML, D2, C4 models, and Graphviz.
  * **Source:** `tirandagan/claude-diagrams`
* **Nimbalyst: Visual Editor Plugin**
  * **What it does:** An open-architecture visual editor extension built for Claude Code and OpenCode. It lets the AI parse markdown files and render Excalidraw, live Mermaid scripts, and data models side-by-side in real-time.
  * **Output:** Live canvas rendering editable both textually and via mouse.
  * **Source:** Available via the Nimbalyst Marketplace.

---

## 2. Markdown-Viewer Skills (No-Script Solutions)

"Skills" are manifest-first Markdown configuration files that teach Claude and OpenCode strict behaviors without spinning up local servers.

### Architecture Documentation Skill
* **How it works:** Analyzes your codebase and injects C4 component/deployment maps directly into system files.
* **Installation:** 
```bash
  npx skills add [https://github.com/melodic-software/claude-code-plugins](https://github.com/melodic-software/claude-code-plugins) --skill architecture-documentation
