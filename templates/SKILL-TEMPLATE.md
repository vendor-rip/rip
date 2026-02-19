---
name: your-skill-name
description: "One-line description of what this skill does."
---

# Skill Name

> Brief tagline describing the skill's purpose.

## Version & Prerequisites

- Skill version: 0.1.0
- Requires: file system access, code search, code generation, command execution
- Optional: tool profiles in `profiles/{tool}/` for enriched analysis

## Quick Start

Entry points for this skill:

- **Scan**: `your-skill scan` — assess the current state
- **Plan**: `your-skill plan` — generate a migration/implementation plan

## Phase 1: Scan

### Goal

What does the scan produce? What does it analyze?

### Methodology

1. **Step 1** — What to look for
2. **Step 2** — How to assess it
3. **Step 3** — How to produce the report

### Output

Save to `./your-skill-report.json`:

```json
{
  "example": "schema"
}
```

---

## Phase 2: Plan

### Goal

Generate an actionable plan based on the scan.

### Methodology

1. **Select approach** — How to choose between strategies
2. **Generate phases** — Break down into steps with validation criteria

---

## Phase 3: Execute

### Goal

Perform the actual work. Developer reviews at each phase boundary.

### Guidelines

- Follow the plan phase by phase
- Run validation criteria before proceeding
- Ask before making decisions (library choices, architecture, scope)

---

## Phase 4: Validate

### Goal

Verify the work is correct and complete.

### Checklist

1. Run existing tests
2. Check for leftover references
3. Verify configuration cleanup
4. Prompt for manual verification

---

## Phase 5: Complete

### Goal

Produce the completion report.

### Output

Save to `./your-skill-completion.json` with timing, outcomes, and gotchas.

---

## Error Handling

| Situation | What to do |
|---|---|
| **Scan fails** | Report what happened. Don't save partial results. |
| **Execution fails** | Show the error. Offer: fix, revert, or abort. |
| **Validation fails** | Show specific failures. Offer: fix, accept partial, or abandon. |
