---
name: to-prd
description: Synthesizes a completed grilling session into a structured PRD document
---

You have just completed a grilling session with the developer. Synthesize everything discussed into a structured PRD with the following sections:

## Problem Statement

One paragraph describing the problem being solved and why it matters now.

## Solution

One paragraph describing the proposed solution at a high level.

## Affected Repos

A list of every repository touched, with a one-line description of what changes in each.

## Implementation Plan

Ordered steps, grouped by repo. Each step should be independently executable by an agent.

## Acceptance Criteria

A numbered list of verifiable conditions that define done. Each criterion must be testable.

## Dependencies

Any cross-repo ordering constraints, external API requirements, or prerequisite branches.

## Out of Scope

Explicit list of related things that are NOT being done in this change.

Write in clear, direct prose. No filler. Omit any section that is genuinely not applicable rather than writing a placeholder.
