---
name: ideogram-core-workflow-b
description: |
  Execute Ideogram secondary workflow: Core Workflow B.
  Use when implementing secondary use case,
  or complementing primary workflow.
  Trigger with phrases like "ideogram secondary workflow",
  "secondary task with ideogram".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Ideogram Core Workflow B

## Overview
Secondary workflow for Ideogram. Complements the primary generation workflow by focusing on image editing, remixing, and batch asset production. Use this skill when you need to modify an existing image (inpainting or style transfer), generate multiple variations of an approved concept, or produce an entire set of branded visual assets in a single automated batch.

## Prerequisites
- Completed `ideogram-install-auth` setup
- Familiarity with `ideogram-core-workflow-a`
- Valid API credentials configured

## Instructions

### Step 1: Setup
Determine the editing or batch generation mode to use. For image remixing, provide the source image and a description of the modifications you want. For inpainting, define the mask area that should be regenerated while preserving the rest of the composition. For batch production, prepare the list of prompts or template variations that define each asset in the set.

```typescript
// Step 1 implementation
```

### Step 2: Process
Submit the edit or batch requests to the Ideogram API. Use seed values to maintain stylistic consistency across a batch — setting the same seed with minor prompt variations produces visually coherent asset families. Review each generated image for brand alignment and quality. Reject and regenerate any images that do not meet the visual standard before proceeding.

```typescript
// Step 2 implementation
```

### Step 3: Complete
Organize the approved images into the appropriate directory structure for your project. Rename files according to your asset naming convention, convert to the required formats (PNG, WebP, JPEG), and commit to your design asset repository or upload to your CDN. Document the prompts and seeds used for each approved asset so the set can be extended or reproduced later.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow B execution
- Edited image or batch of generated assets from the Ideogram API
- Organized asset set named and formatted for delivery
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
- [Ideogram Documentation](https://docs.ideogram.com)
- [Ideogram API Reference](https://docs.ideogram.com/api)

## Next Steps
For common errors, see `ideogram-common-errors`.