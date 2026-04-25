---
title: "Surgical Implementation Standards"
source: "raw/CLAUDE.md"
date_added: 2026-04-25
tags: [standards, coding, efficiency]
status: canonical
summary: "Guidelines for minimal, surgical, and goal-driven code changes to reduce tokens and errors."
---

## 1. Surgical Mandate
- **No Refactoring:** Only touch code directly related to the task.
- **Match Style:** Adhere to existing patterns, even if suboptimal.
- **Cleanup:** Only remove dead code that *your* change created.

## 2. Simplicity Mandate
- **No Speculative Code:** No "extra" features or "future-proofing."
- **Concrete over Abstract:** No abstractions for single-use logic.
- **Minimum Lines:** If a solution can be smaller, rewrite it before submitting.

## 3. Think-Before-Code
- **State Assumptions:** List interpretations before acting.
- **Surface Tradeoffs:** If two ways exist, ask the human.
- **Push Back:** If a request is overcomplicated, suggest a simpler way.

## 4. Goal-Driven Success
- **Reproduction First:** For bugs, a test must exist that fails before the fix.
- **Verification Loop:** Every plan step must have a `verify: [check]` condition.
