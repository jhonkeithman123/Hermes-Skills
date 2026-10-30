---
name: roblox-studio-init
description: Use when starting Roblox Studio. Checks MCP and tools.
---

# Roblox Studio Initialization Protocol

Run the following checks automatically at the start of a session or whenever handling Roblox Studio tasks:

## 1. MCP Connectivity & Tool Check
- Ping or verify the active **Roblox Studio MCP server** connection.
- Query available tools exposed by the Roblox Studio MCP integration (e.g., `search_game_tree`, `inspect_instance`, `script_read`, `script_write`, `run_code`, `get_console_output`, `insert_asset`).
- **If MCP is not connected or unresponsive**:
  - Stop execution immediately.
  - Alert: "? **Roblox Studio MCP Connection Failed**: Ensure Roblox Studio is open, the MCP plugin/server is active, and HTTP requests are enabled in Experience Settings."

## 2. Game Tree & Workspace Indexing
- Run `search_game_tree` or `get_file_tree` to map out the current place structure.
- Index core Roblox services:
  - `Workspace`
  - `ReplicatedStorage`
  - `ServerScriptService`
  - `ServerStorage`
  - `StarterPlayer` / `StarterPlayerScripts`
  - `StarterGui`

## 3. Session Readiness Status
Display a clean status block summarizing health and structure before executing user prompts:

```text
[Roblox Studio Health Check]
Status: Connected
Available Tools: [List core tools detected]
Active Place: [Place Name or Universe ID]
Game Tree: [Indexed core services and top-level hierarchy]
```
