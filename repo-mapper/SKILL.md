---
name: repo-mapper
description: Use when mapping repos or Roblox trees. Generates Markdown.
---

# Dual-Mode Repository & Project Documentation Protocol

## 1. Environment Detection
Determine whether the active workspace is a **Standard Code Repository** or a **Roblox Studio MCP Session**.

---

## Mode A: Standard Code Repositories

### Reading Documentation
- Check if a file `path/to/file.ext` has an accompanying `path/to/file.md` or a directory `README.md`.
- Read and summarize the contents of those `.md` files into the master map.

### Writing/Updating Documentation
- When documenting a file `src/auth.js`, create or update `src/auth.md`.
- Store technical details, dependencies, key functions, and usage notes in `src/auth.md`.

---

## Mode B: Roblox Studio (via MCP)

### Reading Documentation
1. Inspect the target Instance (Script, Folder, Model) via MCP.
2. Search for a child `StringValue` named `Doc`, `Description`, or `README`.
3. If present, read its `.Value` string as Markdown documentation.
4. If missing, fall back to reading block comments (`--[[ ... ]]`) at the top of the Luau script.

### Writing/Updating Documentation
1. To document a Script or Service (e.g., `ServerScriptService.PlayerManager`):
   - Use MCP to create a child `StringValue` named `Doc` under that Instance.
   - Set `Doc.Value` to the formatted Markdown text.
2. If using file-based syncing tools (Rojo):
   - Create a companion `.md` file in your synced filesystem folder (e.g., `PlayerManager.script.md` alongside `PlayerManager.server.luau`).

---

## 2. Output Formatting Template

```markdown
# Project Architectural Map

## Structure
```text
[Generated ASCII Tree]
```

## Key Modules
| Module | Path | Responsibility | Dependencies |
|--------|------|----------------|-------------|

## Dependencies
| Dependency | Used By | Purpose |
|-----------|---------|---------|
