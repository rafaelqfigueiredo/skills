---
name: write-a-skill
description: Create new agent skills following repo conventions: correct directory structure, frontmatter, description triggers, and reference tiers. Use when user wants to create, write, or build a new skill for this plugin.
---

# Writing Skills

## Process

1. **Gather requirements** — ask about:
   - What task/domain does the skill cover?
   - What specific use cases should it handle?
   - Does it need executable scripts or just instructions?
   - Any reference materials to include?

2. **Draft the skill** — create files per the structure below.

3. **Lint before committing** — run `python3 scripts/lint-skills.py path/to/SKILL.md`.

4. **Review with user** — present draft, confirm coverage, then commit.

## Skill Structure

```
<plugin>/skills/<plugin>/<skill-name>/
├── SKILL.md               # Main instructions (required, ≤100 lines)
├── workflows/             # Tier 1 — step-by-step processes (optional)
│   └── <topic>.md
├── references/            # Tier 2 — detailed docs (optional)
│   └── <topic>.md
└── examples/              # Tier 2 — usage examples (optional)
    └── <topic>.md
```

Tier rules: `workflows/` files may link down to `references/` and `examples/`. Same-tier or upward links must go through `SKILL.md`. Every `.md` inside the skill dir must be linked from `SKILL.md` (no orphans).

## SKILL.md Template

```md
---
name: skill-name          # must match the skill directory name exactly
description: <what it does>. Use when <specific triggers>.
---

# Skill Name

## Quick start

[Minimal working example]

## Workflows

[Step-by-step processes — or link to workflows/ files]

## Reference

See [topic](references/\<topic\>.md)
```

## Description Requirements

The description is the only thing the agent sees when routing. Keep it ≤1024 chars, third person, two sentences:

1. What capability this provides.
2. "Use when [keywords / contexts / file types]."

Include both concept terms ("layered design") and concrete pattern names users actually type ("service object", "form object").

**Good:** `Extract text and tables from PDF files, fill forms, merge documents. Use when working with PDF files or when user mentions PDFs, forms, or document extraction.`

**Bad:** `Helps with documents.`

## When to Add Scripts

Add `scripts/` when the operation is deterministic (validation, formatting) or the same code would be generated repeatedly. Scripts save tokens and improve reliability.

Match specificity to fragility — pick the right degree of freedom:

| Freedom | Form | Use when |
|---|---|---|
| High | Plain text instructions | Flexible tasks, many valid outputs |
| Medium | Pseudocode / parameterised script | Some constraints, some flexibility |
| Low | Exact script, minimal parameters | Fragile operations (migrations, batch writes) |

If the skill bundles scripts, list required packages in SKILL.md — never assume they're installed.

## MCP Tool References

Always use fully qualified names: `ServerName:tool_name` (e.g. `BigQuery:bigquery_schema`, `GitHub:create_issue`). Bare tool names are ambiguous when multiple servers are connected.

## When to Split Files

Split when SKILL.md would exceed 100 lines or content has distinct domains. Put step-by-step flows in `workflows/`, detailed docs in `references/`, usage samples in `examples/`. Reference files >100 lines need a `## Contents` TOC near the top.

## Review Checklist

- [ ] `name:` matches the skill directory name
- [ ] Description ≥10 words, ≤1024 chars, includes "Use when..."
- [ ] SKILL.md ≤100 lines
- [ ] Every `.md` in the skill dir linked from `SKILL.md`
- [ ] All relative links resolve (no dead links)
- [ ] Scripts list required packages; MCP tools use `ServerName:tool_name` form
- [ ] Script degree of freedom matches operation fragility
- [ ] Lint passes: `python3 scripts/lint-skills.py`
