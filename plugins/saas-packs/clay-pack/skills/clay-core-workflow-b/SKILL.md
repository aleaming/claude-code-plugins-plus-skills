---
name: clay-core-workflow-b
description: |
  Execute Clay secondary workflow: Core Workflow B.
  Use when implementing secondary use case,
  or complementing primary workflow.
  Trigger with phrases like "clay secondary workflow",
  "secondary task with clay".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Clay Core Workflow B

## Overview
Secondary workflow for Clay. Complements the enrichment workflow by focusing on AI-powered personalization, waterfall enrichment strategies, and CRM synchronization. Use this skill when you need to generate personalized outreach snippets for each prospect using their enriched profile data, configure waterfall logic to try cheaper data sources before falling back to premium ones, or sync enriched records back to Salesforce or HubSpot automatically.

## Prerequisites
- Completed `clay-install-auth` setup
- Familiarity with `clay-core-workflow-a`
- Valid API credentials configured

## Instructions

### Step 1: Setup
Define the personalization or sync task. For AI personalization, configure the Clay AI column with a prompt template that references the prospect's enriched fields — company, role, recent news, or tech stack — to generate unique first-line copy for each outreach email. For waterfall enrichment, order your data provider sequence from lowest cost to highest so expensive lookups are only triggered when cheaper sources return no data.

```typescript
// Step 1 implementation
```

### Step 2: Process
Run the configured columns across your table. For AI personalization, review a random sample of generated snippets to verify quality and relevance before using them in campaigns. For waterfall enrichment, inspect the provider column to see which source filled each record and calculate the average cost per enriched contact. For CRM sync, trigger the export and verify that records map to the correct object types and field names in your CRM.

```typescript
// Step 2 implementation
```

### Step 3: Complete
Export or push the finalized records to your outreach tool or CRM. For personalized campaigns, attach the generated snippets as a field in your email sequence tool's contact import. Document the waterfall configuration and credit cost breakdown so the approach can be reproduced or refined for future campaigns.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow B execution
- Personalized outreach snippets or waterfall-enriched records
- CRM sync confirmation with mapped field values
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
- [Clay Documentation](https://docs.clay.com)
- [Clay API Reference](https://docs.clay.com/api)

## Next Steps
For common errors, see `clay-common-errors`.