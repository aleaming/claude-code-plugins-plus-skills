---
name: instantly-core-workflow-b
description: |
  Execute Instantly secondary workflow: Core Workflow B.
  Use when implementing secondary use case,
  or complementing primary workflow.
  Trigger with phrases like "instantly secondary workflow",
  "secondary task with instantly".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Instantly Core Workflow B

## Overview
Secondary workflow for Instantly. Complements the campaign launch workflow by covering lead management, inbox monitoring, and deliverability maintenance. Use this skill when you need to bulk-import leads into a campaign, handle bounced or unsubscribed contacts, manage email account health, or investigate why a campaign is underperforming on deliverability.

## Prerequisites
- Completed `instantly-install-auth` setup
- Familiarity with `instantly-core-workflow-a`
- Valid API credentials configured

## Instructions

### Step 1: Setup
Identify the task to perform: lead import, inbox monitoring, or deliverability audit. For lead imports, prepare the CSV with required fields and verify that no duplicates exist in the target campaign. For inbox monitoring, configure the reply classification rules that will route positive, negative, and out-of-office replies to the correct follow-up sequences.

```typescript
// Step 1 implementation
```

### Step 2: Process
Execute the selected operation via the Instantly API. For lead imports, submit the batch and confirm the final count matches expectations. For inbox monitoring, retrieve recent reply events and classify each response to feed the appropriate next step in the sequence. For deliverability audits, pull sending account health scores and identify any accounts that need additional warmup time before resuming high-volume sending.

```typescript
// Step 2 implementation
```

### Step 3: Complete
Apply the results of the operation to your broader lead management system. Update CRM records based on reply classifications, pause or remediate unhealthy sending accounts, and confirm that the campaign pipeline is progressing as expected. Document any deliverability issues and the remediation steps taken.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow B execution
- Updated lead list, inbox reply classifications, or deliverability health report
- Corrective actions applied to campaign or sending accounts
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
- [Instantly Documentation](https://docs.instantly.com)
- [Instantly API Reference](https://docs.instantly.com/api)

## Next Steps
For common errors, see `instantly-common-errors`.