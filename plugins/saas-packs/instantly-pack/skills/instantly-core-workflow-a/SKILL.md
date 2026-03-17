---
name: instantly-core-workflow-a
description: |
  Execute Instantly primary workflow: Core Workflow A.
  Use when implementing primary use case,
  building main features, or core integration tasks.
  Trigger with phrases like "instantly main workflow",
  "primary task with instantly".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Instantly Core Workflow A

## Overview
Primary money-path workflow for Instantly. This is the most common use case. Instantly is a cold email outreach automation platform that manages sending infrastructure, email warmup, campaign sequencing, and reply detection. It is designed for sales and lead generation teams that need to send personalized outreach at scale while maintaining high deliverability rates and avoiding spam filters.

## Prerequisites
- Completed `instantly-install-auth` setup
- Understanding of Instantly core concepts
- Valid API credentials configured

## Instructions

### Step 1: Initialize
Authenticate with the Instantly API and verify that your sending accounts are warmed up and ready. Confirm that your lead list is loaded and that contact fields match the personalization variables in your email templates. Set campaign sending schedule, daily volume limits, and reply-stop rules to avoid over-contacting prospects who have already responded.

```typescript
// Step 1 implementation
```

### Step 2: Execute
Launch the campaign via the API and monitor the initial send batch. Check open and reply rates against your expected baseline. Review the bounce and spam rates to detect deliverability issues early. If reply rates are below expectations, inspect the email sequence copy and subject lines for improvements.

```typescript
// Step 2 implementation
```

### Step 3: Finalize
Pull campaign analytics from the Instantly API and export interested replies to your CRM or sales pipeline. Mark bounced and unsubscribed contacts appropriately in your lead database. Archive the campaign results and document performance metrics to inform future outreach strategy.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow A execution
- Campaign launched with confirmed send activity across all enrolled leads
- Analytics report with open, reply, bounce, and unsubscribe rates
- Success confirmation or error details if the campaign could not be started

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
- [Instantly Documentation](https://docs.instantly.com)
- [Instantly API Reference](https://docs.instantly.com/api)

## Next Steps
For secondary workflow, see `instantly-core-workflow-b`.