---
name: handoff
description: Compact the current conversation into a handoff document so a fresh agent can continue the work. Use when the user wants to hand off, summarize for a new session, continue in another window, or pass context to another agent.
argument-hint: "What will the next session be used for?"
---

# Handoff

Write a handoff document summarising the current conversation so a fresh agent can pick up where this one left off. Save it to the OS temp directory (not the current workspace).

## What to include

- Current state of the work: what was done, what's in progress, what's blocked
- Key decisions made and their rationale
- Immediate next steps
- A **Suggested skills** section listing skills the next agent should invoke

## What to skip

Do not duplicate content already captured in other artifacts (PRDs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact sensitive information: API keys, passwords, PII.

## Tailoring

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the document accordingly — emphasise relevant context, de-emphasise the rest.
