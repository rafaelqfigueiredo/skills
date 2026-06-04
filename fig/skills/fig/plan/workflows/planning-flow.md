---
name: planning-flow
description: Full planning workflow — grills the goal, produces a PRD, generates a framework-aware implementation plan, and decomposes it into a backlog stored in .plans/.
---

# Planning Flow

## Step 1 — Grill the goal

Run the `grill-me` skill on the stated goal. Ask probing questions until every ambiguity is resolved:

- What exactly will be built? What is out of scope?
- Which services or repos are affected?
- Are there existing patterns in this codebase that apply?
- What could go wrong? What are the hardest parts?
- What does success look like — how will it be tested?

Do not proceed until all answers are clear.

## Step 2 — Detect the stack

Follow the stack detection section of `skills/fig/plan/SKILL.md` to identify the framework(s) in the repo. Load the matching convention references now — they inform the PRD, backlog, and plan.

## Step 3 — Determine the plan directory

Find the next available sequential slot under `.plans/`:

- List existing directories matching `.plans/NNN-*`
- Increment the highest number by 1, zero-padded to 3 digits
- Slugify the feature name from the goal (lowercase, hyphens, no special chars)
- Create the directory: `.plans/NNN-slug/`

Example: if `001-user-auth/` exists, the next is `.plans/002-my-feature/`.

## Step 4 — PRD

Synthesize the grilling session into a structured PRD following the `to-prd` skill. Read and follow `skills/fig/to-prd/SKILL.md`. Apply framework conventions from step 2 when describing the solution and implementation approach.

Save the PRD to `.plans/NNN-slug/prd.md`. Present it to the user and wait for confirmation before proceeding.

## Step 5 — Plan

Follow the plan output format in `skills/fig/plan/SKILL.md`. Work from the confirmed PRD and the loaded conventions as the source of truth.

## Step 6 — Backlog

Decompose the plan into backlog tickets following the `to-backlog` skill. Read and follow `skills/fig/to-backlog/SKILL.md`. Work from the PRD and the implementation plan together. Use framework-specific terminology and patterns from step 2 when naming and describing tickets.

Save each ticket as a sequentially numbered file inside the plan directory:

```
.plans/NNN-slug/
├── prd.md
├── 001-ticket-slug.md
├── 002-ticket-slug.md
└── 003-ticket-slug.md
```

Ticket filenames are zero-padded and slugified from the ticket title.

The backlog is the handoff artifact for the implementer — every ticket must be independently executable without further planning decisions.

## Storage rules

- All files live under `.plans/` in the project root
- `.plans/` must be in `.gitignore` — add it if missing, never stage these files
- Never include `.plans/` files in git commits or suggest staging them
