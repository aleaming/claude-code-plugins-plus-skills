---
name: granola-upgrade-migration
description: |
  Upgrade Granola versions and migrate between plans.
  Use when upgrading app versions, changing subscription plans,
  or migrating data between Granola accounts.
  Trigger with phrases like "upgrade granola", "granola migration",
  "granola new version", "change granola plan", "granola update".
allowed-tools: Read, Write, Edit, Bash(brew:*), Bash(curl:*)
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Granola Upgrade & Migration

## Current State
!`npm list 2>/dev/null | head -20`
!`pip freeze 2>/dev/null | head -20`

## Overview
Guide for upgrading Granola app versions and migrating between subscription plans. Covers auto-update configuration, plan upgrades and downgrades, data export/import, and enterprise migrations from competing tools.

## Prerequisites
- Current Granola version information (Menu > About Granola)
- Admin access for organization-level changes
- Data backup before major upgrades

## Instructions

### Step 1: Check Current Version
```bash
# macOS - Check installed version
defaults read /Applications/Granola.app/Contents/Info.plist CFBundleShortVersionString
```

### Step 2: Configure Auto-Updates
Navigate to Granola > Preferences > General. Enable "Check for updates automatically" and "Download updates in background."

### Step 3: Upgrade App Version
```bash
# macOS via Homebrew
brew update
brew upgrade --cask granola
```
Alternatively, download the latest version directly from granola.ai/download.

### Step 4: Upgrade Subscription Plan
Navigate to Settings > Account > Subscription. Select the target plan (Pro, Business, or Enterprise) and complete the upgrade flow. Plan features activate immediately with prorated billing.

```
Upgrade Path: Free → Pro → Business → Enterprise
- Immediate access to new features
- No data loss during upgrade
- Prorated billing applied
```

### Step 5: Export Data Before Downgrades
Before downgrading, export all data via Settings > Data > Export in Markdown or JSON format. Verify the export contains all notes, transcripts, and action items.

For complete update troubleshooting, plan upgrade details, data import/export procedures, rollback steps, and enterprise migration checklists, see [migration procedures](references/migration-procedures.md).

## Output
- Granola updated to latest version
- Subscription plan changed with features activated
- Data exported and verified before any downgrades

## Error Handling

| Error | Cause | Resolution |
|-------|-------|------------|
| Update fails to install | Cached data conflict | Delete ~/Library/Caches/Granola and retry |
| App crashes after update | Corrupted preferences | Clear preferences and re-authenticate |
| Billing error on upgrade | Payment method expired | Update payment method in Account settings |

## Examples

**Version upgrade**: Run `brew update && brew upgrade --cask granola` to update. Verify with `defaults read /Applications/Granola.app/Contents/Info.plist CFBundleShortVersionString`. Clear caches if the update fails.

**Plan migration with data preservation**: Export all data as JSON before downgrading from Business to Pro. Document active integrations (they disconnect on downgrade), notify team members, and re-import critical notes after the downgrade completes.

## Resources
- [Granola Updates](https://granola.ai/updates)
- [Pricing & Plans](https://granola.ai/pricing)
- [Migration Support](https://granola.ai/help/migration)

## Next Steps
Proceed to `granola-ci-integration` for CI/CD workflow integration.
