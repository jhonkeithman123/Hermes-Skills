---
name: context-guard
description: Warns when long session context risks reducing accuracy.
version: 1.0.0
author: user
license: MIT
hermes:
  tags:
    - session-management
    - context-window
  related_skills:
    - topic-guard
---

# Context Window & Memory Guard Protocol

## When to Use
Load this skill on every turn in prolonged sessions to monitor context window length and warn when density risks reducing accuracy.

On every turn during prolonged sessions, evaluate session depth and context length:

## 1. Overflow Risk Assessment
- Monitor message count and depth of conversation history.
- If the conversation exceeds ~20 turns or high token volume:
  - Identify that accuracy and retrieval quality (the "needle in a haystack" effect) are at risk of degrading, especially on smaller/free models with limited context windows.

## 2. Trigger Threshold Alert
When context density reaches the threshold, append a brief warning banner before or after your answer:

> ⚠️ **Context Density High**: This session is getting long, which may reduce response accuracy and detail.

## 3. Auto-Remediation Offer
Offer the user two remediation options:
1. **Compress Session**: Summarize core technical details, open tasks, and active game tree/repo structures into a compact state, clearing old raw history.
2. **Branch Session**: Offer a slash command to initialize a clean session pre-loaded with the active state summary (`/new [Summary Title]`).
