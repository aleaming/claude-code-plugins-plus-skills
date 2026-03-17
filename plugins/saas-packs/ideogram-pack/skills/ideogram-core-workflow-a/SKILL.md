---
name: ideogram-core-workflow-a
description: |
  Execute Ideogram primary workflow: Core Workflow A.
  Use when implementing primary use case,
  building main features, or core integration tasks.
  Trigger with phrases like "ideogram main workflow",
  "primary task with ideogram".
allowed-tools: Read, Write, Edit, Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Ideogram Core Workflow A

## Overview
Primary money-path workflow for Ideogram. This is the most common use case. Ideogram is an AI image generation API that specializes in producing images with accurate, legible text rendering — a capability where most image models struggle. It is the preferred choice when your designs require readable typography embedded in the image, such as social media graphics, marketing banners, product mockups, or any visual that combines illustration with text labels.

## Prerequisites
- Completed `ideogram-install-auth` setup
- Understanding of Ideogram core concepts
- Valid API credentials configured

## Instructions

### Step 1: Initialize
Authenticate with the Ideogram API and select the appropriate model version and resolution for your target use case. Configure style presets (photorealistic, illustration, design) and aspect ratio to match the output dimensions required by your application or design system.

```typescript
// Step 1 implementation
```

### Step 2: Execute
Submit the generation request with your text prompt. When your prompt includes text that should appear in the image, enclose it in quotes within the prompt string so Ideogram renders it as visible typography. Monitor the response for the returned image URL or base64 data. Evaluate the generated image for visual quality and text legibility before accepting the result.

```typescript
// Step 2 implementation
```

### Step 3: Finalize
Download and store the generated image in your media storage layer. Apply any post-processing needed (resizing, format conversion, watermarking) before delivery to end users. Log generation metadata including prompt, model version, seed, and generation time for reproducibility and cost tracking.

```typescript
// Step 3 implementation
```

## Output
- Completed Core Workflow A execution
- Generated image URL or binary data from the Ideogram API
- Image meeting prompt specifications with accurate text rendering
- Success confirmation or error details if generation failed

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
- [Ideogram Documentation](https://docs.ideogram.com)
- [Ideogram API Reference](https://docs.ideogram.com/api)

## Next Steps
For secondary workflow, see `ideogram-core-workflow-b`.