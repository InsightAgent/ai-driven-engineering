# Azure DevOps Git MCP Server — Design Spec

## Overview

An MCP server that exposes Azure DevOps Git repository operations as tools for AI agents. This enables AI assistants to browse repos, list files, and read file content from Azure DevOps without leaving the chat interface.

## Requirements

### Capabilities
- **List Repositories** — enumerate all or project-scoped Git repos
- **Get Repository Details** — fetch metadata for a specific repo
- **List Items** — browse files and folders at a given path
- **Get File Content** — read raw file content from a branch

### Non-Goals (out of scope for v1)
- Work item CRUD operations
- Pull request management
- Pipeline operations
- Boards/sprints interaction
- Write operations (create/update files)

## Architecture

### Directory Structure

```
packages/azure-devops-mcp/
  package.json
  tsconfig.json
  src/
    index.ts       — MCP server entry, tool registration
    auth.ts        — Azure CLI token acquisition
    client.ts      — REST API HTTP client
    tools/
      list-repos.ts
      get-repo.ts
      list-items.ts
      get-file.ts
```

### Tech Stack
- **Runtime:** Node.js
- **MCP SDK:** `@modelcontextprotocol/sdk` (official)
- **HTTP:** Node.js built-in `fetch` (Node 18+)
- **Language:** TypeScript

### Authentication
Azure CLI credential flow:
1. Server calls `az account get-access-token --resource 499b84ac-1321-427f-aa17-267ca6975798 --query accessToken -o tsv` at startup
2. Token cached and used as `Authorization: Bearer <token>` on all requests
3. On 401 response, re-run the command to refresh

### Configuration
Environment variables:
- `AZURE_DEVOPS_ORG_URL` (required) — e.g., `https://dev.azure.com/myorg`

### Tool Surface

| Tool | Input | Output | API Endpoint |
|------|-------|--------|-------------|
| `azure-devops_list_repos` | `project` (optional string) | Array of `{ id, name, url, defaultBranch, project }` | `GET {org}/_apis/git/repositories` |
| `azure-devops_get_repo` | `repo_id` (string) | Single repo object | `GET {org}/_apis/git/repositories/{repoId}` |
| `azure-devops_list_items` | `repository_id`, `scope_path` (default `/`), `recursion_level` (`OneLevel`/`Full`/`None`) | Array of `{ objectId, gitObjectType, path, isFolder, url }` | `GET {org}/_apis/git/repositories/{repo}/items?scopePath={path}` |
| `azure-devops_get_file` | `repository_id`, `path`, `branch` (optional) | File content as text | `GET {org}/_apis/git/repositories/{repo}/items?path={path}&includeContent=true` |

### Error Handling
- Auth failure → clear error message: "Azure CLI not logged in. Run `az login` and `az devops login`."
- Repo not found (404) → "Repository not found. Verify repo_id exists in the configured organization."
- API error → surface HTTP status + response body
- Token expiry → auto-refresh once, then fail

## Testing

### Unit Tests
- Mock `fetch` responses for each tool
- Mock `execSync` for Azure CLI calls
- Validate tool schemas (inputs match expected types)
- Validate error responses for each failure mode

### Integration
- `AZURE_DEVOPS_ORG_URL` + logged-in Azure CLI → run against a real org

## Future Considerations
- Add `search_code` tool (Azure DevOps Code Search API)
- Add `create_file` / `update_file` for AI-powered code changes
- Support PAT auth as fallback when Azure CLI is unavailable
