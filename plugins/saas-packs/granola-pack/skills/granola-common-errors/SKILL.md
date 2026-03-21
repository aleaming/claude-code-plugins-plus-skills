---
name: granola-common-errors
description: |
  Troubleshoot common Granola errors and issues.
  Use when experiencing recording problems, sync issues,
  transcription errors, or integration failures.
  Trigger with phrases like "granola error", "granola not working",
  "granola problem", "fix granola", "granola troubleshoot".
allowed-tools: Read, Write, Edit, Bash(pgrep:*), Bash(ps:*)
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Granola Common Errors

## Overview
Diagnose and resolve common Granola issues covering audio capture, calendar sync, processing failures, and integration errors. Each error includes symptoms, root causes, and step-by-step remediation.

## Prerequisites
- Granola installed (even if malfunctioning)
- Terminal access for diagnostic commands
- Admin access on macOS or Windows

## Instructions

### Step 1: Run Quick Diagnostics
```bash
# macOS - Check if Granola is running
pgrep -l Granola

# Check audio devices
system_profiler SPAudioDataType | grep "Default Input"
```

### Step 2: Identify the Error Category
Match symptoms to the appropriate section below, then apply the corresponding fix.

### Step 3: Apply the Fix
Follow the resolution steps for the matched error. Verify the fix resolved the issue before closing.

## Audio Issues

### Error: "No Audio Captured"
**Symptoms:** Meeting recorded but transcript is empty

| Cause | Solution |
|-------|----------|
| Wrong audio input | System Preferences > Sound > Input > Select correct device |
| Microphone muted | Check physical mute button on device |
| Permission denied | Grant microphone access in System Preferences |
| Virtual audio conflict | Disable conflicting audio software |

```bash
set -euo pipefail
# Reset audio on macOS
sudo killall coreaudiod
```

### Error: "Poor Transcription Quality"
1. Use a quality microphone or headset
2. Reduce background noise
3. Speak clearly at a moderate pace
4. Position microphone closer to the speaker

## Calendar Sync Issues

### Error: "Meeting Not Detected"
1. **Check calendar connection:** Settings > Integrations > Calendar; disconnect and reconnect
2. **Verify event visibility:** Event must be on a synced calendar with a video link
3. **Force sync:** Click the sync button in Granola and wait 30 seconds

### Error: "Calendar Authentication Failed"
1. Clear browser cache
2. Log out of Google/Microsoft account
3. Log back in and reconnect Granola
4. Alternatively, use a private/incognito browser window

For processing errors, integration errors, app issues, and error codes, see [detailed error reference](references/detailed-errors.md).

## Output
- Identified root cause of the Granola issue
- Applied resolution steps with verified fix
- Documented the error and solution for team reference

## Error Handling

| Error | Cause | Resolution |
|-------|-------|------------|
| Authentication failure | Invalid or expired credentials | Re-authenticate with Granola account |
| Configuration conflict | Incompatible settings detected | Review and resolve conflicting parameters |
| Resource not found | Referenced resource missing | Verify resource exists and permissions are correct |

## Examples

**Audio troubleshooting**: Run `pgrep -l Granola` to confirm the app is running, then check `system_profiler SPAudioDataType` to verify the correct input device. Reset Core Audio with `sudo killall coreaudiod` if the device is correct but audio is not captured.

**Calendar sync fix**: Navigate to Settings > Integrations > Calendar, disconnect the calendar, wait 10 seconds, reconnect, and verify the next scheduled meeting appears in Granola.

## Resources
- [Granola Status](https://status.granola.ai)
- [Granola Help Center](https://granola.ai/help)
- [Known Issues](https://granola.ai/updates)

## Next Steps
Proceed to `granola-debug-bundle` for creating diagnostic reports.
