---
name: granola-deploy-integration
description: |
  Deploy Granola integrations to Slack, Notion, HubSpot, and other apps.
  Use when connecting Granola to productivity tools,
  setting up native integrations, or configuring auto-sync.
  Trigger with phrases like "granola slack", "granola notion",
  "granola hubspot", "granola integration", "connect granola".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Granola Deploy Integration

## Overview
Configure and deploy native Granola integrations with Slack, Notion, HubSpot, and Zapier-based workflows. Supports single-integration setup or multi-platform automation chains for complete meeting follow-up.

## Prerequisites
- Granola Pro or Business plan
- Admin access to target apps (Slack workspace, Notion workspace, HubSpot portal)
- Integration requirements defined per team

## Instructions

### Step 1: Select Target Integrations
Identify which platforms to connect based on team workflow. Alternatively, deploy a single integration first and expand later.

### Step 2: Connect Native Integration
1. Navigate to Granola Settings > Integrations
2. Select the target platform (Slack, Notion, or HubSpot)
3. Authorize permissions in the platform's OAuth flow
4. Configure default settings (channel, database, or contact matching)

### Step 3: Configure Automation Rules
Set auto-posting behavior, attendee mentions, and content filtering per integration. Customize the output format for each connected platform.

### Step 4: Test with a Sample Meeting
1. Record a short test meeting
2. Verify notes appear in the connected platform
3. Check data mapping, formatting, and permissions
4. Adjust configuration based on test results

### Step 5: Deploy Multi-Integration Workflows (Optional)
Use Zapier to chain multiple platforms: meeting ends in Granola, summary posts to Slack, full notes sync to Notion, action items create tasks in Linear or Asana.

For complete setup guides, configuration tables, Zapier recipes, and deployment checklists per platform, see [integration guides](references/integration-guides.md).

## Output
- Native integrations connected and authorized
- Auto-sync configured per platform preferences
- Multi-platform workflow chains validated with test data

## Error Handling

| Integration | Common Error | Solution |
|-------------|--------------|----------|
| Slack | Channel not found | Verify channel exists and bot is invited |
| Notion | Database missing | Recreate target database with required schema |
| HubSpot | Contact mismatch | Update matching rules for email domain |
| Zapier | Rate limited | Add delays between Zap steps |

## Examples

**Single Slack integration**: Connect Slack via Settings > Integrations, select the #meeting-notes channel, enable auto-post with summary and action items. Test with a sample meeting to verify formatting.

**Full automation chain**: Configure Zapier with path-based routing: internal meetings go to Slack + Notion + Linear; client meetings additionally update HubSpot contacts and draft follow-up emails in Gmail.

## Resources
- [Granola Integrations](https://granola.ai/integrations)
- [Zapier Granola App](https://zapier.com/apps/granola)
- [Integration FAQ](https://granola.ai/help/integrations)

## Next Steps
Proceed to `granola-webhooks-events` for event-driven automation.
