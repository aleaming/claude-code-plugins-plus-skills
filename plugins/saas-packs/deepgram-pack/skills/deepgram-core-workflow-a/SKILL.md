---
name: deepgram-core-workflow-a
description: |
  Implement speech-to-text transcription workflow with Deepgram.
  Use when building pre-recorded audio transcription, batch processing,
  or implementing core transcription features.
  Trigger with phrases like "deepgram transcription", "speech to text",
  "transcribe audio", "audio transcription workflow", "batch transcription".
allowed-tools: Read, Write, Edit, Bash(npm:*), Bash(pip:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Deepgram Core Workflow A: Pre-recorded Transcription

## Overview
Implement a complete pre-recorded audio transcription workflow using Deepgram's Nova-2 model. Covers file and URL transcription, configurable feature options, batch processing, and speaker diarization.

## Prerequisites
- Completed `deepgram-install-auth` setup
- Understanding of async patterns
- Audio files or URLs to transcribe

## Instructions

### Step 1: Create Transcription Service
Create a service class to handle transcription operations with configurable options for model, language, punctuation, and diarization.

### Step 2: Implement URL Transcription
```typescript
import { createClient } from '@deepgram/sdk';

const deepgram = createClient(process.env.DEEPGRAM_API_KEY!);
const { result, error } = await deepgram.listen.prerecorded.transcribeUrl(
  { url: 'https://example.com/audio.wav' },
  { model: 'nova-2', smart_format: true, punctuate: true, diarize: false }
);
```

### Step 3: Add File Transcription
Read the audio file into a buffer, detect the MIME type from the file extension, and pass both to `transcribeFile`. Alternatively, use `transcribeUrl` for remote audio files to avoid local I/O.

### Step 4: Configure Feature Options
Enable optional features per transcription request: `diarize` for speaker identification, `utterances` for turn-based segments, `paragraphs` for structured output.

### Step 5: Process Results
Extract transcript text, confidence scores, and word-level timing from the response. Format diarized output with speaker labels.

```typescript
// Speaker diarization output
result.utterances?.forEach(utterance => {
  console.log(`Speaker ${utterance.speaker}: ${utterance.transcript}`);
});
```

### Step 6: Implement Batch Processing (Optional)
Process multiple audio files concurrently with configurable concurrency limits using `Promise.allSettled`.

For complete TypeScript service class, batch transcription implementation, and Python SDK equivalent, see [implementation reference](references/implementation.md).

## Output
- Transcription service class with file and URL support
- Configurable transcription options (model, language, diarization)
- Batch processing capability with concurrency control
- Formatted transcript with word-level timing and speaker labels

## Error Handling
| Error | Cause | Solution |
|-------|-------|----------|
| Audio Too Long | Exceeds limits | Split into chunks or use async callback |
| Unsupported Format | Invalid audio type | Convert to WAV/MP3/FLAC |
| Empty Response | No speech detected | Check audio quality and volume |
| Timeout | Large file processing | Use callback URL pattern |

## Examples

**Single file transcription**: Create the service with an API key, call `transcribeFile('./meeting.wav', { diarize: true })`, and format the result with speaker labels and timestamps.

**Batch processing**: Pass an array of file paths to `batchTranscribe` with concurrency set to 5. Iterate over results, logging successful transcripts and retrying failures.

## Resources
- [Deepgram Pre-recorded API](https://developers.deepgram.com/docs/getting-started-with-pre-recorded-audio)
- [Deepgram Models](https://developers.deepgram.com/docs/models)
- [Speaker Diarization](https://developers.deepgram.com/docs/diarization)

## Next Steps
Proceed to `deepgram-core-workflow-b` for real-time streaming transcription.
