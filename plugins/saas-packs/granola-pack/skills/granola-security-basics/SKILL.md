---
name: granola-security-basics
description: |
  Security best practices for Granola meeting data.
  Use when implementing security controls, reviewing data handling,
  or ensuring compliance with security policies.
  Trigger with phrases like "granola security", "granola privacy",
  "granola data protection", "secure granola", "granola compliance".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Granola Security Basics

## Overview
Implement security best practices for protecting meeting data in Granola. Covers access controls, data retention, sensitive meeting handling, compliance requirements, and incident response procedures.

## Prerequisites
- Granola account with admin access (Business plan recommended)
- Understanding of organizational security policies
- Compliance requirements identified (GDPR, HIPAA, SOC 2)

## Instructions

### Step 1: Secure Personal Account
1. Set a strong unique password for the Granola account
2. Enable two-factor authentication (2FA)
3. Review connected apps and revoke unused integrations
4. Use SSO if available on Business or Enterprise plan

### Step 2: Configure Sharing Defaults
```
Settings > Privacy > Default Sharing
- New meetings: Private (recommended)
- Auto-share with attendees: Off (for sensitive meetings)
- External sharing: Disabled (for compliance)
```

### Step 3: Set Data Retention Policy
Configure retention in Settings > Privacy > Data Retention. Delete audio after processing to retain notes while removing raw recordings. Alternatively, set 7-day or 30-day audio retention for audit trail needs.

### Step 4: Apply Compliance Controls
Review GDPR, HIPAA, and SOC 2 requirements against Granola's certifications. Enable audit logging and configure data residency for regulated workspaces.

### Step 5: Establish Sensitive Meeting Protocol
1. Disable auto-recording before sensitive meetings
2. Announce recording to all participants
3. Review and redact notes before sharing
4. Set expiration on shared links

For complete security architecture, compliance matrices, admin checklists, audit logging details, and incident response procedures, see [security controls reference](references/security-controls.md).

## Output
- Personal account secured with 2FA and strong password
- Sharing defaults configured for organizational policy
- Data retention policy applied
- Compliance controls verified against requirements

## Error Handling

| Error | Cause | Resolution |
|-------|-------|------------|
| 2FA setup fails | Authenticator app misconfigured | Resync time on device or use backup codes |
| Sharing override blocked | Organization policy restriction | Contact admin to modify workspace policy |
| Data export fails | Insufficient permissions | Request export access from workspace admin |

## Examples

**Individual security setup**: Enable 2FA, set default sharing to Private, configure audio deletion after processing, and review connected apps quarterly.

**Team security rollout**: Enforce SSO login for all team members, enable audit logging, set external sharing to disabled, configure IP allowlisting, and establish a quarterly access review cadence.

## Resources
- [Granola Security](https://granola.ai/security)
- [Privacy Policy](https://granola.ai/privacy)
- [Trust Center](https://granola.ai/trust)

## Next Steps
Proceed to `granola-prod-checklist` for production deployment preparation.
