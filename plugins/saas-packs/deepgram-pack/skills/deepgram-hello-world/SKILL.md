---
name: deepgram-hello-world
description: |
  Create a minimal working Deepgram transcription example.
  Use when starting a new Deepgram integration, testing your setup,
  or learning basic Deepgram API patterns.
  Trigger with phrases like "deepgram hello world", "deepgram example",
  "deepgram quick start", "simple transcription", "transcribe audio".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Deepgram Hello World

## Overview
Minimal working example demonstrating core Deepgram speech-to-text functionality. Produces a transcribed text output from an audio URL or local file in under 10 lines of code.

## Prerequisites
- Completed `deepgram-install-auth` setup
- Valid API credentials configured via `DEEPGRAM_API_KEY` environment variable
- Audio file for transcription (or use the Deepgram sample URL)

## Instructions

### Step 1: Create Entry File
Create a new TypeScript or Python file for the hello world example.

### Step 2: Initialize the Deepgram Client
```typescript
import { createClient } from '@deepgram/sdk';

const deepgram = createClient(process.env.DEEPGRAM_API_KEY);
```

### Step 3: Transcribe Audio from URL
```typescript
async function transcribe() {
  const { result, error } = await deepgram.listen.prerecorded.transcribeUrl(
    { url: 'https://static.deepgram.com/examples/nasa-podcast.wav' },
    { model: 'nova-2', smart_format: true }
  );

  if (error) throw error;
  console.log(result.results.channels[0].alternatives[0].transcript);
}

transcribe();
```

### Step 4: Verify Transcription Output
Run the file and confirm a text transcript appears in the console. Alternatively, transcribe a local file by reading it into a buffer and passing it to `transcribeFile`.

### Step 5: Customize Options (Optional)
Change `model` to `nova`, `enhanced`, or `base` for different accuracy/speed trade-offs. Set `language` for non-English audio. Enable `diarize: true` for speaker identification.

For additional language examples (Python, local file transcription) and customization options, see [extended examples](references/extended-examples.md).

## Output
- Working code file with Deepgram client initialization
- Successful transcription response from the API
- Console output showing transcribed text

## Error Handling
| Error | Cause | Solution |
|-------|-------|----------|
| Import Error | SDK not installed | Verify with `npm list @deepgram/sdk` |
| Auth Error | Invalid credentials | Check `DEEPGRAM_API_KEY` environment variable |
| Audio Format Error | Unsupported format | Use WAV, MP3, FLAC, or OGG files |
| URL Not Accessible | Cannot fetch audio | Ensure URL is publicly accessible |

## Examples

**URL transcription**: Initialize the client with `createClient(process.env.DEEPGRAM_API_KEY)`, call `transcribeUrl` with the NASA podcast sample URL and Nova-2 model, then print the transcript from `result.results.channels[0].alternatives[0].transcript`.

**Local file transcription**: Read the audio file with `readFileSync`, pass the buffer to `transcribeFile` with the appropriate MIME type, and extract the transcript from the response.

## Resources
- [Deepgram Getting Started](https://developers.deepgram.com/docs/getting-started)
- [Deepgram API Reference](https://developers.deepgram.com/reference)
- [Deepgram Models](https://developers.deepgram.com/docs/models)

## Next Steps
Proceed to `deepgram-local-dev-loop` for development workflow setup.
