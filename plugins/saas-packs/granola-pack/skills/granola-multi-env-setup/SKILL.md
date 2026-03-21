---
name: granola-multi-env-setup
description: |
  Configure Granola across multiple workspaces and team environments.
  Use when setting up multi-team deployments, configuring workspace hierarchies,
  or managing enterprise-scale Granola installations.
  Trigger with phrases like "granola workspaces", "granola multi-team",
  "granola environments", "granola organization", "granola multi-env".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Granola Multi-Environment Setup

## Overview
Configure Granola for multi-workspace and multi-team enterprise deployments. Covers workspace hierarchy design, user provisioning via SSO/SCIM, per-environment integration configuration, and compliance controls.

## Prerequisites
- Granola Business or Enterprise plan
- Organization admin access
- Team structure defined
- SSO configured (recommended for automated provisioning)

## Instructions

### Step 1: Plan Workspace Structure
Define each workspace with name, purpose, owner, members, access level, integrations, and retention policy. Map organizational departments to separate workspaces.

### Step 2: Create Workspaces
1. Navigate to Organization Settings > Workspaces
2. Create each workspace with name, slug, description, and owner
3. Configure privacy, sharing, and retention per workspace

### Step 3: Configure User Provisioning
Choose a provisioning method based on organization size:
- **Manual:** Invite by email, assign to workspaces, set roles
- **SSO/SCIM:** Map SSO groups to workspaces and roles for automatic provisioning
- **JIT:** Enable Just-in-Time provisioning so users auto-join on first SSO sign-in

### Step 4: Set Up Per-Workspace Integrations
Configure environment-specific integrations for each workspace. Alternatively, test integrations in a staging workspace before promoting to production.

### Step 5: Configure Compliance Controls
Apply data residency, encryption, audit logging, and retention overrides per workspace. Confidential workspaces (HR, Legal) require stricter settings.

### Step 6: Validate and Promote
1. Test configuration in staging workspace with sample meetings
2. Verify integration data flow and permissions
3. Promote to production workspaces
4. Monitor for 24 hours after go-live

| Role | Permissions | Use Case |
|------|------------|----------|
| Owner | Full admin + billing | Organization owner |
| Admin | Workspace management | Team leads |
| Member | Create + edit notes | Regular users |
| Viewer | Read only | Stakeholders |
| Guest | Single workspace | Contractors |

For complete workspace templates, SSO group mappings, environment-specific configs, compliance settings, and promotion procedures, see [workspace configuration reference](references/workspace-configs.md).

## Output
- Workspace hierarchy created and configured
- User provisioning method established (manual, SSO/SCIM, or JIT)
- Per-workspace integrations deployed and verified
- Compliance controls applied to sensitive workspaces

## Error Handling

| Issue | Cause | Solution |
|-------|-------|----------|
| User in wrong workspace | SSO mapping error | Check group assignments in SSO provider |
| Integration not syncing | Wrong environment config | Verify API keys match the environment |
| Notes not visible | Permission mismatch | Check role assignment for the workspace |
| Cross-workspace search failing | Feature not enabled | Enable in Organization Settings |

## Examples

**Engineering workspace setup**: Create an Engineering workspace with team sharing enabled, connect Linear for task creation and Notion for wiki integration, set 1-year note retention and 90-day transcript retention, and provision members via SSO group mapping.

**Compliance-first HR workspace**: Create an HR workspace with external sharing prohibited, customer-managed encryption keys, 30-day retention override, MFA required, and 4-hour session timeout. Export audit logs daily to Splunk.

## Resources
- [Granola Enterprise Admin](https://granola.ai/admin)
- [SSO Configuration](https://granola.ai/help/sso)
- [SCIM Provisioning](https://granola.ai/help/scim)

## Next Steps
Proceed to `granola-observability` for monitoring and analytics.
