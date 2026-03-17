---
name: vastai-core-workflow-b
description: |
  Execute Vast.ai secondary workflow: Core Workflow B.
  Use when implementing secondary use case,
  or complementing primary workflow.
  Trigger with phrases like "vastai secondary workflow",
  "secondary task with vastai".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Vast.ai Core Workflow B

## Overview
Secondary workflow for Vast.ai. Complements the instance provisioning workflow by focusing on cost optimization, multi-instance orchestration, and spot interruption handling. Use this skill when you need to run a distributed training job across multiple rented GPUs, implement automatic spot interruption recovery to avoid losing training progress, or analyze your spending history to identify opportunities to reduce per-job cost.

## Prerequisites
- Completed `vastai-install-auth` setup
- Familiarity with `vastai-core-workflow-a`
- Valid API credentials configured

## Instructions

### Step 1: Setup
Plan the multi-instance configuration or cost optimization strategy. For distributed workloads, identify how many nodes are needed and which interconnect topology (NVLink, high-bandwidth network) is required for your framework. For cost optimization, pull your billing history from the API and calculate cost-per-compute-hour across past jobs to establish a baseline you can compare against improved configurations.

```typescript
// Step 1 implementation
```

### Step 2: Process
Provision the required instances using your optimized search criteria. For distributed jobs, start all nodes, verify connectivity between them, and coordinate the start of your distributed training script. Implement checkpoint saving at regular intervals so that if a spot instance is reclaimed, the job can resume from the last checkpoint on a replacement node rather than starting over from scratch.

```typescript
// Step 2 implementation
```

### Step 3: Complete
After the job finishes or if interrupted, destroy all rented instances to stop billing. Collect all saved checkpoints and output artifacts from the distributed nodes before teardown. Generate a cost report comparing actual spend against the estimate, and record the instance configuration and job parameters that achieved the best cost-efficiency ratio for future reference.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow B execution
- Distributed job completed with checkpoints and output artifacts collected
- Cost analysis report comparing estimated versus actual spend
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
- [Vast.ai Documentation](https://docs.vastai.com)
- [Vast.ai API Reference](https://docs.vastai.com/api)

## Next Steps
For common errors, see `vastai-common-errors`.