---
description: Deep repository analysis to extract architecture, patterns, and standards into the wiki.
---

# /map — Repository Analysis & Indexing

This workflow scans a codebase to create high-level "Concept" and "Pattern" maps in the wiki, reducing the need for the AI to re-read the entire repo in future sessions.

## Activation
- `/map [path or repo name]`
- "Analyze this repository"
- "Create a technical map for [project]"

## Implementation Steps

### 1. Structural Scan
- Use `ls -R` or `glob` to map the file tree.
- Identify entry points (e.g., `main.py`, `index.ts`, `App.tsx`).
- Identify configuration files (e.g., `package.json`, `tsconfig.json`, `Dockerfile`).

### 2. Logic Extraction
- Find core directories (e.g., `src/services/`, `src/components/`, `src/utils/`).
- **Pattern Identification:** Look for recurring logic (e.g., Redux slices, API wrappers, Middleware).
- **Standard Identification:** Look for naming conventions, linting rules, and testing patterns.

### 3. Wiki Entry Creation
For each repository, create/update:
- **Repo Article** (`wiki/repos/[name].md`): High-level overview, tech stack, and entry points.
- **Pattern Articles** (`wiki/patterns/[pattern-name].md`): Detailed logic flows extracted from the code.
- **Standard Articles** (`wiki/standards/[name].md`): Coding rules identified in the repo.

### 4. Backlink Rebuild
- Link the new [[repo]] article to existing [[tools]] and [[concepts]].
- Update `wiki/_index.md`.

## Quality Rules
- **Anti-Bloat:** Do NOT summarize every file. Only summarize the *Architecture* and *Patterns*.
- **Code Snippets:** Include 1-2 idiomatic snippets in the Pattern article.
- **Dependency Mapping:** List internal and external dependencies.

## Output
A "Technical Map" that the AI will use as its primary context for the next task.
