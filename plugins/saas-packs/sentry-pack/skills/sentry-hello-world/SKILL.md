---
name: sentry-hello-world
description: |
  Execute capture your first error with Sentry and verify it appears in the dashboard.
  Use when testing Sentry integration or verifying error capture works.
  Trigger with phrases like "test sentry", "sentry hello world",
  "verify sentry", "first sentry error".
allowed-tools: Read, Write, Edit, Bash(node:*), Bash(python:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Sentry Hello World

## Prerequisites
- Sentry SDK installed and initialized
- Valid DSN configured
- Network access to Sentry servers

## Instructions

Sentry error capture verification is the first test you should run after installing and configuring the Sentry SDK. Sending a controlled test event confirms that your DSN is correctly configured, that network requests to Sentry's ingestion endpoint are not being blocked by a firewall or proxy, and that the SDK is capturing the metadata you expect (release version, environment tag, user context). Catching misconfiguration at this stage prevents silent monitoring gaps in production.

1. Open https://sentry.io
2. Navigate to your project
3. Check Issues tab for the test error
4. Verify event details are correct — confirm the environment is labeled correctly (not accidentally tagged as `production` when testing), check that the release version appears in the event, and verify that any user context you attached is visible in the event detail view.

See `${CLAUDE_SKILL_DIR}/references/implementation.md` for a detailed implementation guide covering SDK initialization, environment tagging, and user context attachment.

## Output
- Test error visible in Sentry dashboard within seconds of being captured
- Event contains a full stack trace pointing to the correct line in your source
- User context, release tag, and environment label attached to the event
- Confirmation that the integration is working correctly before deploying to production

## Error Handling

See `${CLAUDE_SKILL_DIR}/references/errors.md` for comprehensive error handling.

## Examples

See `${CLAUDE_SKILL_DIR}/references/examples.md` for detailed examples.

## Resources
- [Sentry Error Capture](https://docs.sentry.io/platforms/javascript/usage/)
- [Sentry Context](https://docs.sentry.io/platforms/javascript/enriching-events/context/)

## Overview

Execute capture your first error with Sentry and verify it appears in the dashboard.