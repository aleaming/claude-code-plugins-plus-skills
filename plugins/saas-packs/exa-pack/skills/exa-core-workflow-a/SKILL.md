---
name: exa-core-workflow-a
description: |
  Execute Exa primary workflow: Core Workflow A.
  Use when implementing primary use case,
  building main features, or core integration tasks.
  Trigger with phrases like "exa main workflow",
  "primary task with exa".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Exa Core Workflow A

## Overview
Primary money-path workflow for Exa. This is the most common use case. Exa is a neural search API that retrieves web content using semantic similarity rather than keyword frequency. Unlike traditional search engines, Exa understands the meaning of your query and returns contextually related results, making it ideal for research, competitive intelligence, and building retrieval-augmented generation pipelines.

## Prerequisites
- Completed `exa-install-auth` setup
- Understanding of Exa core concepts
- Valid API credentials configured

## Instructions

### Step 1: Initialize
Authenticate with the Exa API using your stored API key and verify connectivity. Configure default parameters such as the number of results per query, whether to include text highlights, and whether to use auto-prompt mode which rewrites your input for better retrieval accuracy.

```typescript
// Step 1 implementation
```

### Step 2: Execute
Submit your natural-language query to the Exa search endpoint. Exa returns ranked results with similarity scores, source URLs, and optional content snippets. Examine the scores to gauge how well the results match your intent. If relevance is low, try rephrasing the query as a statement rather than a question.

```typescript
// Step 2 implementation
```

### Step 3: Finalize
Extract and format the returned results for your downstream use case. Deduplicate overlapping sources, cite URLs when presenting information externally, and cache result sets to avoid redundant API calls. Log query metadata including token count and latency for cost monitoring.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow A execution
- Ranked list of semantically matched results with URLs and relevance scores
- Optional highlights or full-page content per result
- Success confirmation or error details if the query could not be resolved

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
- [Exa Documentation](https://docs.exa.com)
- [Exa API Reference](https://docs.exa.com/api)

## Next Steps
For secondary workflow, see `exa-core-workflow-b`.