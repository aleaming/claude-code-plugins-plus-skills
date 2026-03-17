---
name: windsurf-core-workflow-a
description: |
  Execute Windsurf primary workflow: Core Workflow A.
  Use when implementing primary use case,
  building main features, or core integration tasks.
  Trigger with phrases like "windsurf main workflow",
  "primary task with windsurf".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Windsurf Core Workflow A

## Overview
Primary money-path workflow for Windsurf. This is the most common use case. Windsurf is an AI-powered code editor built by Codeium that uses agentic flows called Cascade to understand and act on your codebase across multiple files simultaneously. Unlike simple autocomplete tools, Windsurf can execute multi-step tasks such as refactoring an entire module, writing tests for existing code, or debugging a chain of errors with full codebase context.

## Prerequisites
- Completed `windsurf-install-auth` setup
- Understanding of Windsurf core concepts
- Valid API credentials configured

## Instructions

### Step 1: Initialize
Open your project in Windsurf and verify that the AI index has been built for the codebase. The indexing step allows Windsurf to understand the full context of your project rather than treating each file in isolation. Check that your model tier (standard or Pro) is configured to match the complexity of tasks you intend to perform.

```typescript
// Step 1 implementation
```

### Step 2: Execute
Invoke the Cascade agent with a natural-language instruction describing the task. Be specific about scope — name the files, functions, or patterns involved. Windsurf will plan its approach, make the necessary edits across files, and present a diff for your review. Read the proposed changes carefully before accepting, particularly for refactoring tasks that touch many files.

```typescript
// Step 2 implementation
```

### Step 3: Finalize
Review and accept the changes proposed by Cascade. Run your test suite to confirm nothing was broken by the edits. If tests fail, provide Windsurf with the error output and ask it to diagnose and fix the issue — the editor retains context about the changes it just made, which makes iterative debugging efficient.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow A execution
- Multi-file code changes applied by Windsurf Cascade
- Test suite verification confirming no regressions introduced
- Success confirmation or error details if the agent could not complete the task

## Error Handling
| Error | Cause | Solution |
|-------|-------|----------|
| Error 1 | Cause | Solution |
| Error 2 | Cause | Solution |

## Examples

### Complete Workflow
```typescript
// Complete workflow example
```

### Common Variations
- Variation 1: Description
- Variation 2: Description

## Resources
- [Windsurf Documentation](https://docs.windsurf.com)
- [Windsurf API Reference](https://docs.windsurf.com/api)

## Next Steps
For secondary workflow, see `windsurf-core-workflow-b`.