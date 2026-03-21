---
name: deepgram-local-dev-loop
description: |
  Configure Deepgram local development workflow with testing and iteration.
  Use when setting up development environment, configuring test fixtures,
  or establishing rapid iteration patterns for Deepgram integration.
  Trigger with phrases like "deepgram local dev", "deepgram development setup",
  "deepgram test environment", "deepgram dev workflow".
allowed-tools: Read, Write, Edit, Bash(npm:*), Bash(pip:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Deepgram Local Dev Loop

## Overview
Set up an efficient local development workflow for Deepgram integration with fast feedback cycles, test fixtures, and mock responses for offline development.

## Prerequisites
- Completed `deepgram-install-auth` setup
- Node.js 18+ with npm/pnpm or Python 3.10+
- Sample audio files for testing
- Environment variables configured in `.env`

## Instructions

### Step 1: Create Project Structure
```bash
mkdir -p src tests fixtures
touch src/transcribe.ts tests/transcribe.test.ts
```

### Step 2: Configure Environment Files
```bash
# .env.development
DEEPGRAM_API_KEY=your-dev-api-key
DEEPGRAM_MODEL=nova-2
```

### Step 3: Download Test Fixtures
```bash
set -euo pipefail
curl -o fixtures/sample.wav https://static.deepgram.com/examples/nasa-podcast.wav
```

### Step 4: Set Up Watch Mode
```json
{
  "scripts": {
    "dev": "tsx watch src/transcribe.ts",
    "test": "vitest",
    "test:watch": "vitest --watch"
  }
}
```

### Step 5: Create Mock Responses
Build mock response objects that mirror the Deepgram API structure for offline testing. Use these mocks to avoid API calls during unit tests and CI runs.

### Step 6: Run Tests and Iterate
Execute `npm test` to run the test suite against fixtures. Alternatively, use `npm run test:watch` for continuous feedback during development.

For complete TypeScript dev entry point, Vitest test setup, mock response objects, and alternative test framework options, see [test setup reference](references/test-setup.md).

## Output
- Project structure with src, tests, and fixtures directories
- Environment files for development and testing
- Watch mode scripts for rapid iteration
- Mock responses for offline test execution

## Error Handling
| Error | Cause | Solution |
|-------|-------|----------|
| Fixture Not Found | Missing audio file | Run fixture download script |
| Env Not Loaded | dotenv not configured | Install and configure dotenv |
| Watch Mode Fails | Missing tsx | Install tsx: `npm i -D tsx` |
| API Rate Limited | Too many dev requests | Use cached mock responses in tests |

## Examples

**Quick dev setup**: Create the project structure, download the NASA podcast fixture, configure `.env` with the API key, and run `tsx watch src/transcribe.ts` for live reloading during development.

**Offline test suite**: Create mock response objects matching the Deepgram API shape, inject them into tests via dependency injection or module mocking, and run `vitest` without any network calls.

## Resources
- [Deepgram SDK Reference](https://developers.deepgram.com/docs/sdk)
- [Vitest Documentation](https://vitest.dev/)
- [dotenv Configuration](https://github.com/motdotla/dotenv)

## Next Steps
Proceed to `deepgram-sdk-patterns` for production-ready code patterns.
