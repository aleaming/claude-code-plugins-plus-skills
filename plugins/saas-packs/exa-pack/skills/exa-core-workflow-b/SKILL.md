---
name: exa-core-workflow-b
description: |
  Execute Exa secondary workflow: Core Workflow B.
  Use when implementing secondary use case,
  or complementing primary workflow.
  Trigger with phrases like "exa secondary workflow",
  "secondary task with exa".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Exa Core Workflow B

## Overview
Secondary workflow for Exa. Complements the primary search workflow by focusing on advanced retrieval patterns: similarity search from a seed URL, domain-filtered queries, and batching multiple queries efficiently. Use this skill when you need to find pages similar to a known reference, restrict results to specific domains, or run bulk research queries within your API quota.

## Prerequisites
- Completed `exa-install-auth` setup
- Familiarity with `exa-core-workflow-a`
- Valid API credentials configured

## Instructions

### Step 1: Setup
Determine whether to use URL-based similarity search or a domain-scoped query. For similarity search, provide a seed URL that represents the type of content you want to surface. For domain-scoped queries, specify the `include_domains` or `exclude_domains` filters to narrow results to authoritative sources.

```typescript
// Step 1 implementation
```

### Step 2: Process
Execute the configured query using the appropriate Exa endpoint variant. Review the returned results for coverage and quality. If using similarity search, compare the seed URL content against the returned results to confirm the semantic alignment is accurate. Adjust the `num_results` and `start_published_date` parameters to refine freshness and volume.

```typescript
// Step 2 implementation
```

### Step 3: Complete
Aggregate results from multiple queries if running a batch, merge and deduplicate across query outputs, and write the final result set to your target destination. Document the query strategy used so future runs can reproduce or iterate on the approach.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow B execution
- Filtered or similarity-matched results from Exa API
- Deduplicated, merged result set ready for downstream consumption
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
- [Exa Documentation](https://docs.exa.com)
- [Exa API Reference](https://docs.exa.com/api)

## Next Steps
For common errors, see `exa-common-errors`.