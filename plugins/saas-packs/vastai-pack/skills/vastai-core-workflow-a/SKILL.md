---
name: vastai-core-workflow-a
description: |
  Execute Vast.ai primary workflow: Core Workflow A.
  Use when implementing primary use case,
  building main features, or core integration tasks.
  Trigger with phrases like "vastai main workflow",
  "primary task with vastai".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Vast.ai Core Workflow A

## Overview
Primary money-path workflow for Vast.ai. This is the most common use case. Vast.ai is a marketplace for renting GPU compute from individual hosts and data centers at prices significantly lower than hyperscaler providers. It is commonly used for training machine learning models, running large-scale inference, and rendering workloads where cost efficiency matters more than guaranteed SLA uptime.

## Prerequisites
- Completed `vastai-install-auth` setup
- Understanding of Vast.ai core concepts
- Valid API credentials configured

## Instructions

### Step 1: Initialize
Authenticate with the Vast.ai API and search for available instances that match your requirements. Filter by GPU model, VRAM size, geographical region, reliability score, and price per hour. Sort offers by the metric most relevant to your workload — price for budget-conscious batch jobs, reliability score for long-running training runs, or interconnect bandwidth for distributed training setups.

```typescript
// Step 1 implementation
```

### Step 2: Execute
Rent the selected instance by creating an offer via the API. Specify the Docker image containing your workload environment, the startup command, and any environment variables or volume mounts needed. Monitor the instance status until it reaches the running state, then connect via SSH or the Jupyter interface to verify the environment is configured correctly before beginning your compute job.

```typescript
// Step 2 implementation
```

### Step 3: Finalize
When your job completes, copy all output artifacts (model checkpoints, logs, result files) to persistent storage before destroying the instance. Destroying the instance promptly stops billing. Review the actual cost against your budget estimate and note any performance characteristics that should influence future instance selection.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow A execution
- GPU instance provisioned and job executed successfully
- Output artifacts saved to persistent storage
- Success confirmation or error details if provisioning or execution failed

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
- [Vast.ai Documentation](https://docs.vastai.com)
- [Vast.ai API Reference](https://docs.vastai.com/api)

## Next Steps
For secondary workflow, see `vastai-core-workflow-b`.