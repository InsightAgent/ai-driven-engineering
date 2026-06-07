Code-to-Canvas: Automating Architectural Diagrams via Claude Code and OpenCode
==============================================================================

Modern AI coding agents like Claude Code and OpenCode have fundamentally changed how engineers maintain system documentation. Instead of manually updating static images or wrestling with clunky drag-and-drop design tools, development teams can now generate, render, and continuously update complex architecture diagrams directly from Markdown files.

Because OpenCode natively supports importing Claude Code plugins, terminal commands, and Model Context Protocol (MCP) configurations, engineering teams can build seamless text-to-diagram pipelines that work interchangeably across both ecosystems.

The Core Tool Stack: Dedicated AI Plugins and Visual Editors
------------------------------------------------------------

Native plugins bridge the gap between terminal-based AI agents and visual layout engines, providing real-time rendering as backend configurations change. Three primary tools lead this category:

*   **Cartograph (Native OpenCode Plugin):** Specifically engineered for OpenCode terminal agents, Cartograph acts as a background file watcher. It scans your directory structures or Markdown design documents and continuously updates architectural maps in the background while you or your AI agent code. It outputs code-first diagrams automatically inside a dedicated .architecture/ folder in your repository.
    
*   **claude-diagrams (Kroki-backed Plugin):** This open-source, zero-API-key plugin translates plain-text system descriptions or file paths into more than 20 types of code-first diagramming types. Compilation is handled automatically via Kroki.io, outputting visual maps using popular formats like Mermaid, PlantUML, D2, C4 models, and Graphviz.
    
*   **Nimbalyst (Visual Editor Plugin):** Available via the Nimbalyst Marketplace, this open-architecture extension allows the AI agent to parse Markdown design docs and render interactive Excalidraw files, live Mermaid scripts, and data models side-by-side with your code. The resulting canvas can be modified either via raw text or manually with a mouse.
    

Extending Ecosystems with Model Context Protocol (MCP)
------------------------------------------------------

Model Context Protocol (MCP) connectors allow your terminal-based AI agent to interface securely with cloud-synced canvas platforms and specialized local rendering engines. Rather than relying on simple text output, these servers give the AI direct visual capabilities:

1.  **Eraser Model Context Protocol (MCP)** server or the Eraser Agent Skills CLI. Both solutions integrate directly with OpenCode or other AI coding assistants (like Claude Code and Cursor) to convert code strings, notes, or prompts into structured Eraser Diagrams-as-Code.
    
2.  **Excalidraw MCP:** The most reliable setup for interactive, editable diagrams. The agent parses your Markdown text, renders it into component nodes, and generates an interlocking canvas JSON file that you can immediately tweak in your web browser.
    
3.  **AWS Diagram MCP:** Ideal for teams building cloud infrastructure. This server utilizes the Python diagrams package alongside the official, comprehensive AWS icon set to create professional infrastructure layouts directly from your text specifications.
    
4.  **Microsoft MarkItDown:** A helpful file standardization utility that pre-processes diverse local assets (such as PDFs, Word documents, or images) into clean, token-efficient Markdown that your AI agent can easily ingest before generating a diagram.
    
5.  [**veelenga/claude-mermaid**](https://github.com/veelenga/claude-mermaid): An excellent option for text-to-diagram workflows. When you feed Claude your markdown structure, it generates Mermaid.js code, opens a local live-preview browser tab, and auto-saves the diagram as an SVG or PNG in your workspace. \[[1](https://github.com/veelenga/claude-mermaid), [2](https://www.reddit.com/r/ClaudeAI/comments/1qu3lin/built_an_mcp_server_for_live_mermaid_diagrams/)\]
    
6.  [**angrysky56/mcp-diagram-server**](https://github.com/angrysky56/mcp-diagram-server): This server is explicitly optimized to **map markdown text directly into mind maps** and structural flowcharts. It includes built-in indentation detection and auto-saves artifacts into a dedicated library directory. \[[1](https://github.com/angrysky56/mcp-diagram-server)\]
    
7.  **drawio-diagramming Plugin**: Allows Claude to parse your technical specifications and output editable .drawio XML files or structural SVGs natively embedded into your repository
    

"Skills" for Lightweight, No-Script Automations
-----------------------------------------------

In OpenCode and Claude Code, "Skills" are manifest-first Markdown configuration files that train your terminal agent to adopt specific execution behaviors without needing to spin up local web servers.

*   **Architecture Documentation Skill:** This skill analyzes the deep structure of your codebase and dynamically injects C4 component or deployment maps straight into your system files. It can be initialized via:npx skills add \[https://github.com/melodic-software/claude-code-plugins\](https://github.com/melodic-software/claude-code-plugins) --skill architecture-documentation
    
*   **Oh-My-Mermaid (omm-scan):** A lightweight, syntax-focused skill tailored to parse textual layouts and recursively compile native Markdown .mmd blocks into instant previews. It can be installed globally via:npm install -g oh-my-mermaid && omm setup
    
*   [**Cocoon-AI Architecture Diagram Generator**](https://github.com/Cocoon-AI/architecture-diagram-generator): The leading tool in this space. It directs the AI agent to turn plain text or Markdown into beautiful, modern, dark-themed architecture diagrams saved as standalone HTML/SVG files. No extra visual software is required.
    
*   **Agents365 Draw.io Skill**: A zero-config skill that auto-positions and aligns diagrams. It boasts an inventory of over 10,000 official shapes (AWS, GCP, Kubernetes) and includes an automated self-check loops to fix overlapping text or misaligned lines.
    
*   [**Markdown Viewer Agent Skills**](https://github.com/markdown-viewer/skills): A massive ecosystem featuring 14 distinct visual skills spanning across 5 rendering engines. It includes enterprise architecture mapping rules natively optimized for standard arkdown text code blocks.
    
*   [**Coleam00 Excalidraw Skill**](https://github.com/coleam00/excalidraw-diagram-skill): Teaches your OpenCode agent how to generate structured JSON data that instantly compiles into a sketch-style Excalidraw map. \[[1](https://www.youtube.com/watch?v=m3fqyXZ4k4I&vl=en), [2](https://github.com/coleam00/excalidraw-diagram-skill)\]
    

Implementation Guide: Getting Started on OpenCode
-------------------------------------------------

Setting up a text-to-diagram automation pipeline inside your local workspace requires a quick, three-step configuration.

### 1\. Local Plugin Installation

Begin by dropping your preferred JavaScript or TypeScript diagramming plugin file into your root workspace hidden directory:your-project/.opencode/plugins/diagram-generator.js

### 2\. Global Integration Setup

If you are utilizing community-managed npm packages or explicit MCP tools, declare them inside your project configuration sheet (.opencode/opencode.json or ~/.config/opencode/opencode.json):

JSON

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   {    "plugin": [      "cartograph-plugin",       "opencode-with-claude"    ]  }   `

### 3\. Workflow Execution

Once your environment is reloaded, you can trigger diagram creation directly inside the terminal loop. For targeted design sheets, use the prompt:/diagrams: Create a system context map parsing the service definitions located in @architecture.md

Alternatively, if you are utilizing an active MCP canvas setup, you can give your agent a broader instructional prompt:_"Analyze this Markdown document and generate an Excalidraw architecture diagram."_
