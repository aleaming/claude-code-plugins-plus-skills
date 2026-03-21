---
name: granola-debug-bundle
description: |
  Create diagnostic bundles for Granola troubleshooting.
  Use when preparing support requests, collecting system information,
  or diagnosing complex issues with Granola.
  Trigger with phrases like "granola debug", "granola diagnostics",
  "granola support bundle", "granola logs", "granola system info".
allowed-tools: Read, Write, Edit, Bash(system_profiler:*), Bash(log:*), Bash(sw_vers:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Granola Debug Bundle

## Current State
!`node --version 2>/dev/null || echo 'N/A'`
!`python3 --version 2>/dev/null || echo 'N/A'`
!`uname -a`

## Overview
Collect comprehensive diagnostic information for Granola troubleshooting and support requests. Produces a zip bundle containing system info, application logs, network diagnostics, and configuration state.

## Prerequisites
- Administrator access on the computer
- Granola installed (even if malfunctioning)
- Terminal or Command Prompt access

## Instructions

### Step 1: Create Debug Directory
```bash
mkdir -p ~/Desktop/granola-debug
cd ~/Desktop/granola-debug
```

### Step 2: Collect System and Audio Information
Run the platform-specific collection scripts to gather system info, audio configuration, and Granola logs. See [collection scripts](references/collection-scripts.md) for complete macOS and Windows commands.

### Step 3: Run Network Diagnostics
```bash
set -euo pipefail
curl -s -o /dev/null -w "%{http_code}" https://api.granola.ai/health > network-test.txt
nslookup api.granola.ai >> network-test.txt 2>&1
```

### Step 4: Package the Bundle
```bash
cd ~/Desktop
zip -r granola-debug-$(date +%Y%m%d-%H%M%S).zip granola-debug/
```

### Step 5: Run Self-Diagnosis Before Submitting
Verify these items before contacting support:
- [ ] Granola is updated to latest version
- [ ] Internet connection is stable
- [ ] Microphone permissions granted
- [ ] Calendar is connected
- [ ] Sufficient disk space (> 1GB)

## Output
- Comprehensive debug bundle zip file on the Desktop
- Ready for submission to Granola support at help@granola.ai
- Excludes sensitive data (transcripts, notes, API keys, audio recordings)

## Privacy Considerations
The debug bundle does NOT include meeting transcripts, personal calendar event details, API keys or tokens, or audio recordings.

## Error Handling

| Error | Cause | Resolution |
|-------|-------|------------|
| Permission denied on logs | Insufficient access | Run terminal as administrator |
| Network test fails | Firewall blocking | Check outbound HTTPS rules |
| Zip creation fails | Disk space full | Free up space before bundling |

## Examples

**Basic diagnostic bundle**: Create the debug directory, run `sw_vers` and `system_profiler SPAudioDataType` to collect system info, copy Granola logs from `~/Library/Logs/Granola`, test network connectivity to `api.granola.ai`, then zip the bundle.

**Targeted audio debugging**: Focus on audio configuration by running `system_profiler SPAudioDataType`, checking microphone permissions, and listing virtual audio software. Include the output in the debug bundle alongside the standard system info.

## Resources
- [Granola Support](https://granola.ai/help)
- [Status Page](https://status.granola.ai)

## Next Steps
Proceed to `granola-rate-limits` to understand usage limits.
