---
name: clay-core-workflow-a
description: |
  Execute Clay primary workflow: Core Workflow A.
  Use when implementing primary use case,
  building main features, or core integration tasks.
  Trigger with phrases like "clay main workflow",
  "primary task with clay".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Clay Core Workflow A

## Overview
Primary money-path workflow for Clay. This is the most common use case. Clay is a data enrichment and lead research platform that aggregates contact and company information from dozens of data providers into a single spreadsheet-like interface. It is designed for go-to-market teams that need to build highly enriched prospect lists without manually querying multiple data sources, making it ideal for personalized outbound campaigns and account research at scale.

## Prerequisites
- Completed `clay-install-auth` setup
- Understanding of Clay core concepts
- Valid API credentials configured

## Instructions

### Step 1: Initialize
Authenticate with the Clay API and identify the table or workflow you want to work with. Confirm that your data source integrations (LinkedIn, Clearbit, Apollo, or other enrichment providers) are connected and that your Clay credit balance is sufficient for the enrichment volume you need. Review the column schema of your target table to understand which fields are already populated and which require enrichment.

```typescript
// Step 1 implementation
```

### Step 2: Execute
Trigger the enrichment workflow by submitting records through the Clay API or by uploading a CSV of contacts or companies to a table. Clay will automatically query the configured data providers to fill in missing fields — job titles, email addresses, company headcount, tech stack, funding data, and more. Monitor the enrichment job progress and check the match rate to identify records where data could not be found.

```typescript
// Step 2 implementation
```

### Step 3: Finalize
Export the enriched table from Clay via the API once enrichment is complete. Review the quality of the enriched data before passing it to your CRM or outreach tool. Deduplicate records and flag any rows with low-confidence matches for manual review. Archive the enrichment run metadata including credit cost and match rate for budget tracking.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow A execution
- Enriched contact or company records with populated data fields
- Match rate report identifying records that could not be enriched
- Success confirmation or error details if the enrichment job failed

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
- [Clay Documentation](https://docs.clay.com)
- [Clay API Reference](https://docs.clay.com/api)

## Next Steps
For secondary workflow, see `clay-core-workflow-b`.