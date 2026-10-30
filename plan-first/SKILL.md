---
name: plan-first
description: Plan-first workflow with staged context.md before execution.
version: 1.0.0
author: user
license: MIT
hermes:
  tags:
    - planning
    - workflow
  related_skills:
    - context-guard
---

# Plan-First & Context Memory Protocol

## When to Use
Load this skill when the user submits a task, feature request, or complex code change. Always stage a plan before modifying files.

Whenever the user submits a task, feature request, or complex code change, DO NOT execute or modify files immediately. Follow this 3-step staging workflow:

## Step 1: Draft `context.md` Memory State
Analyze the request and create/update a file named `context.md` (or in-memory state summary) containing:
- **Objective**: Core goal of the user's request.
- **Current State**: Active codebase, game tree, or relevant context.
- **Action Plan**: Numbered step-by-step breakdown of how the task will be implemented.
- **Target Files / Objects**: Specific scripts, files, or instances that will be created or modified.

## Step 2: Present Plan & Request Input
Output a clear summary block to the user:

```text
📋 [Execution Plan Staged]
Objective: [Short summary]

Proposed Steps:
1. [Step 1]
2. [Step 2]
3. [Step 3]

Target Files/Instances: [List affected items]
```

Then ask for user modifications or confirmation before proceeding.

## Step 3: Execute Only After Approval
Only after the user confirms or requests adjustments, proceed to implement the plan step-by-step.
