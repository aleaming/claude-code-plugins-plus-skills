---
name: speak-sdk-patterns
description: |
  Apply production-ready Speak SDK patterns for TypeScript and Python.
  Use when implementing Speak integrations, refactoring SDK usage,
  or establishing team coding standards for language learning features.
  Trigger with phrases like "speak SDK patterns", "speak best practices",
  "speak code patterns", "idiomatic speak".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Speak SDK Patterns

## Overview
Production patterns for the Speak language learning REST API. Covers pronunciation assessment, conversation practice, audio preprocessing, and batch assessment with rate-limit-aware scheduling.

## Prerequisites
- Speak API key configured via `SPEAK_API_KEY` environment variable
- Audio recording capability (WAV/MP3 format)
- Understanding of language learning assessment concepts

## Instructions

### Step 1: Initialize the Client
Create a `SpeakClient` class wrapping the REST API with session-based authentication and a reusable `_post` helper method.

### Step 2: Implement Pronunciation Assessment
Send audio files to the `/pronunciation/assess` endpoint with target text and language. Parse word-level and phoneme-level scores from the response.

### Step 3: Add Conversation Practice
Start a conversation session with a scenario, language, and proficiency level. Send audio turns to the session endpoint and receive AI-generated responses.

### Step 4: Preprocess Audio Files
Convert input audio to WAV 16kHz mono using ffmpeg before sending to the API. This ensures consistent format and reduces upload size. Alternatively, accept pre-formatted WAV files directly.

### Step 5: Implement Batch Assessment
Process multiple student recordings sequentially with a configurable delay between requests. Handle 429 rate limit errors by reading the `Retry-After` header and sleeping before retrying.

For the complete client class, batch assessment runner, audio preprocessing utility, and usage examples, see [code patterns](references/code-patterns.md).

## Output
- Production-ready `SpeakClient` class with typed methods
- Audio preprocessing pipeline (format conversion, quality validation)
- Batch assessment runner with rate-limit-aware scheduling
- Pronunciation scoring at word and phoneme granularity

## Error Handling
| Error | Cause | Solution |
|-------|-------|----------|
| `400 Bad audio format` | Unsupported codec | Convert to WAV 16kHz mono with ffmpeg |
| `413 Payload too large` | Audio file exceeds 25MB | Trim or compress audio before upload |
| `429 Rate limited` | Too many assessments | Add delay between requests or use batch queue |
| Low confidence score | Background noise | Record in a quiet environment |

## Examples

**Single pronunciation assessment**: Initialize `SpeakClient()`, call `assess_pronunciation("recording.wav", "Hello, how are you?")`, and print the overall score and per-word scores from the response.

**Conversation practice session**: Start a session with `start_conversation("ordering at a restaurant", language="es")`, send student audio via `send_turn(session_id, "reply.wav")`, and display the AI tutor response.

## Resources
- [Speak API Docs](https://docs.speak.com)

## Next Steps
Proceed to `speak-data-handling` for transcript storage and analysis patterns.
