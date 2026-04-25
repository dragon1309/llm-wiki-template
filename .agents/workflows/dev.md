---
description: Knowledge-driven development workflow to implement features using the wiki as primary context.
---

# /dev — Wiki-First Implementation

This workflow uses existing knowledge (Patterns, Standards, Tools) to implement features or fix bugs, ensuring that implementation is consistent with project history and best practices.

## Activation
- `/dev [task description]`
- "Implement [feature]"
- "Fix bug in [module]"

## Implementation Steps

### 1. Knowledge Retrieval (The "Wiki-First" Step)
- Scan `wiki/repos/` for the relevant codebase map.
- Search `wiki/patterns/` for logic already established in the project.
- Search `wiki/standards/` for coding rules.
- **Goal:** Minimize reading raw source files by trusting the wiki's "compressed" context.

### 2. Strategic Planning
- Create a plan in `outputs/plans/[task-name].md`.
- **Surgical Constraint:** Ensure the plan only touches files strictly necessary for the goal.
- **Verification Loop:** Each step must follow the format: `[Step] → verify: [check]`.
- **Tradeoff Check:** If the task is ambiguous, stop and ask the user before writing the plan.

### 3. Execution (Act -> Validate)
- **Simplicity First:** Write the minimum code that solves the problem. No speculative abstractions.
- **Style Matching:** Strictly follow the coding style found in the [[repo]] or [[standards]] articles.
- **Reproduction:** For bugs, write a failing test/script first. Verify the fix by making it pass.
- If a new pattern is created, note it for the feedback step.

### 4. Knowledge Feedback (Crucial)
- **Update Wiki:** If the implementation introduced a new pattern or solved a non-trivial problem, update/create the relevant [[patterns]] or [[concepts]] article.
- **Log Operation:** Append to `wiki/_ops_log.md`.

## Quality Rules
- **Referential Integrity:** Code must follow the [[standards]] found in the wiki.
- **Context Conservation:** Only read files explicitly identified as "Entry Points" or "Critical Logic" in the wiki. Avoid blind scanning.
- **Feedback Loop:** No implementation is complete until the wiki is updated with any new "lessons learned."

## Output
1. The implemented code.
2. An updated Wiki article (or new one) reflecting the current state of the architecture.
