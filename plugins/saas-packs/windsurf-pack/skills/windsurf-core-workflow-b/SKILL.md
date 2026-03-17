---
name: windsurf-core-workflow-b
description: |
  Execute Windsurf secondary workflow: Core Workflow B.
  Use when implementing secondary use case,
  or complementing primary workflow.
  Trigger with phrases like "windsurf secondary workflow",
  "secondary task with windsurf".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Windsurf Core Workflow B

## Overview
Secondary workflow for Windsurf. Complements the primary Cascade agent workflow by focusing on configuration management, team settings, and context-sharing for large codebases. Use this skill when you need to configure Windsurf rules to enforce project conventions, set up team-wide AI behavior standards, or troubleshoot degraded AI context quality caused by stale indexes or misconfigured ignore patterns.

## Prerequisites
- Completed `windsurf-install-auth` setup
- Familiarity with `windsurf-core-workflow-a`
- Valid API credentials configured

## Instructions

### Step 1: Setup
Review the current Windsurf configuration files in your project, including `.windsurfrules` and any workspace-level settings. Determine which conventions need to be encoded as rules — for example, preferred code style, which directories to exclude from AI context, or specific patterns that should always be followed when generating code in this project.

```typescript
// Step 1 implementation
```

### Step 2: Process
Update the configuration files with your rule definitions and re-index the project to apply the changes. Test the updated rules by running representative tasks through Cascade and verifying that the AI output respects the new conventions. Adjust rule phrasing if the model is not consistently following a rule — more specific, example-driven rules tend to produce more reliable behavior than abstract directives.

```typescript
// Step 2 implementation
```

### Step 3: Complete
Commit the updated Windsurf configuration files to version control so all team members share the same AI behavior settings. Document the rationale for each rule in a comment or team wiki so future contributors understand why the constraints exist. Share the configuration with team members and confirm that their Windsurf instances pick up the shared rules correctly.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow B execution
- Updated Windsurf configuration with project-specific rules committed to repository
- Verified AI behavior aligned with defined conventions
- Success confirmation or error details

## Error Handling
| Aspect | Workflow A | Workflow B |
|--------|------------|------------|
| Use Case | Primary | Secondary |
| Complexity | Medium | Lower |
| Performance | Standard | Optimized |

## Examples

### Complete Workflow
```typescript
// Complete workflow example
```

### Error Recovery
```typescript
// Error handling code
```

## Resources
- [Windsurf Documentation](https://docs.windsurf.com)
- [Windsurf API Reference](https://docs.windsurf.com/api)

## Next Steps
For common errors, see `windsurf-common-errors`.