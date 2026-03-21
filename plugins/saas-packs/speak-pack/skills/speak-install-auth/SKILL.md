---
name: speak-install-auth
description: |
  Install and configure Speak language learning SDK/API authentication.
  Use when setting up a new Speak integration, configuring API keys,
  or initializing Speak services in your language learning application.
  Trigger with phrases like "install speak", "setup speak",
  "speak auth", "configure speak API key", "speak language learning setup".
allowed-tools: Read, Write, Edit, Bash(npm:*), Bash(pip:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Speak Install & Auth

## Overview
Set up the Speak language learning SDK and configure authentication credentials for AI-powered language tutoring integration. Supports pronunciation assessment, conversation practice, and proficiency evaluation across 10+ languages.

## Prerequisites
- Node.js 18+ or Python 3.10+
- Package manager (npm, pnpm, or pip)
- Speak developer account with API access
- API key from Speak developer dashboard

## Instructions

### Step 1: Install the SDK
```bash
set -euo pipefail
# Node.js
npm install @speak/language-sdk

# Python
pip install speak-language-sdk
```

### Step 2: Configure Authentication
```bash
# Set environment variables
export SPEAK_API_KEY="your-api-key"
export SPEAK_APP_ID="your-app-id"

# Or create .env file
echo 'SPEAK_API_KEY=your-api-key' >> .env
echo 'SPEAK_APP_ID=your-app-id' >> .env
```

### Step 3: Initialize the Client
```typescript
// src/speak/client.ts
import { SpeakClient } from '@speak/language-sdk';

const client = new SpeakClient({
  apiKey: process.env.SPEAK_API_KEY!,
  appId: process.env.SPEAK_APP_ID!,
  language: 'ko', // Target language: Korean, Spanish (es), Japanese (ja), etc.
});
```

### Step 4: Verify the Connection
```typescript
async function verifyConnection() {
  const status = await client.health.check();
  console.log('Speak connection verified:', status);
  return status;
}
```

### Step 5: Select Target Language
Configure the `language` parameter for the target language. Alternatively, switch languages dynamically per session to support multi-language applications.

For TypeScript setup with speech recognition, Python configuration, supported language codes, and alternative API approaches, see [setup examples](references/setup-examples.md).

## Output
- Installed SDK package in node_modules or site-packages
- Environment variable or .env file with API credentials
- Successful connection verification output

## Error Handling
| Error | Cause | Solution |
|-------|-------|----------|
| Invalid API Key | Incorrect or expired key | Verify key in Speak developer dashboard |
| App ID Mismatch | Wrong application identifier | Check app ID in project settings |
| Rate Limited | Exceeded quota | Check usage at developer.speak.com |
| Network Error | Firewall blocking | Ensure outbound HTTPS is allowed |
| Module Not Found | Installation failed | Run `npm install` or `pip install` again |

## Examples

**TypeScript quickstart**: Install `@speak/language-sdk`, set `SPEAK_API_KEY` and `SPEAK_APP_ID` environment variables, initialize `SpeakClient` with target language `ko`, and call `client.health.check()` to verify the connection.

**Python quickstart**: Install `speak-language-sdk` via pip, initialize `SpeakClient` with `api_key` and `app_id` from environment variables, set language to `ja` for Japanese, and verify with `client.health.check()`.

## Resources
- [Speak Developer Documentation](https://developer.speak.com/docs)
- [Speak API Reference](https://developer.speak.com/api)
- [Speak Status Page](https://status.speak.com)
- [OpenAI Real-time API (used by Speak)](https://platform.openai.com/docs/guides/realtime)

## Next Steps
After successful auth, proceed to `speak-hello-world` for the first lesson session.
