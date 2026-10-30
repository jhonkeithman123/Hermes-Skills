---
name: topic-guard
description: Use when detecting chat topic shifts. Offers context switch.
---

# Topic Shift Guard

On every turn, quickly evaluate if the user's prompt represents a complete shift in context from the preceding session history.

- If the topic has **significantly shifted**:
  1. Do NOT answer the main prompt immediately.
  2. Output: "?? **Topic Shift Detected**: This prompt appears to be about **[New Topic]**, which differs from **[Current Topic]**."
  3. Ask: "Would you like to start a new session for this?"
  4. Provide the command to execute: `/new [Suggested Title]` and remind the user to re-paste their prompt once switched.

- If the topic is **related or incremental**:
  Proceed with answering normally.
