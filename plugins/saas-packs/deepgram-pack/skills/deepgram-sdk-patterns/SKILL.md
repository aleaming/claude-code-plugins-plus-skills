---
name: deepgram-sdk-patterns
description: |
  Apply production-ready Deepgram SDK patterns for TypeScript and Python.
  Use when implementing Deepgram integrations, refactoring SDK usage,
  or establishing team coding standards for Deepgram.
  Trigger with phrases like "deepgram SDK patterns", "deepgram best practices",
  "deepgram code patterns", "idiomatic deepgram", "deepgram typescript".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Deepgram SDK Patterns

## Overview
Production patterns for the Deepgram speech-to-text SDK. Covers client initialization, pre-recorded transcription, live streaming, speaker diarization, and batch processing with proper error handling and concurrency control.

## Prerequisites
- `pip install deepgram-sdk` or `npm install @deepgram/sdk`
- `DEEPGRAM_API_KEY` environment variable configured
- Audio files or microphone access for testing

## Instructions

### Step 1: Initialize Client

```python
from deepgram import DeepgramClient, PrerecordedOptions, LiveOptions
import os

def get_deepgram_client() -> DeepgramClient:
    return DeepgramClient(os.environ["DEEPGRAM_API_KEY"])
```

```typescript
import { createClient, DeepgramClient } from '@deepgram/sdk';
const deepgram = createClient(process.env.DEEPGRAM_API_KEY!);
```

### Step 2: Configure Transcription Options
Set model (`nova-2` for best accuracy), enable `smart_format` for clean output, and add `diarize` for multi-speaker scenarios. Alternatively, use `enhanced` or `base` models for faster processing at lower cost.

### Step 3: Implement Pre-Recorded Transcription
Open the audio file, detect MIME type, and call the REST transcription endpoint. Extract transcript text, confidence score, and word-level timing from the response.

### Step 4: Add Live Streaming (Optional)
Create an async WebSocket connection with `LiveOptions`. Register event handlers to process interim and final results in real time.

### Step 5: Implement Batch Processing
Process multiple files concurrently using an asyncio semaphore to respect rate limits. Gather results with `asyncio.gather` and handle exceptions per-file.

For complete Python and TypeScript implementations including pre-recorded transcription, streaming, batch processing, and speaker-labeled formatting, see [code patterns](references/code-patterns.md).

## Output
- Production-ready client initialization with environment-based configuration
- Pre-recorded transcription with word-level timing and speaker labels
- Batch processing pipeline with configurable concurrency
- Live streaming connection with interim result handling

## Error Handling
| Error | Cause | Solution |
|-------|-------|----------|
| `401 Unauthorized` | Invalid API key | Check `DEEPGRAM_API_KEY` value |
| `400 Unsupported format` | Bad audio codec | Convert to WAV/MP3/FLAC |
| Empty transcript | No speech in audio | Check audio quality and volume |
| WebSocket disconnect | Network instability | Implement reconnection logic |

## Examples

**Pre-recorded with diarization**: Call `transcribe_file("meeting.wav")` with `diarize=True`, then iterate over words grouping by `speaker` field to produce speaker-labeled output like `Speaker 0: Hello everyone...`.

**Batch processing**: Pass a list of 50 audio file paths to `batch_transcribe` with `max_concurrent=5`. Review results for errors and retry failed files individually.

## Resources
- [Deepgram SDK Python](https://github.com/deepgram/deepgram-python-sdk)
- [Deepgram API Docs](https://developers.deepgram.com/docs)

## Next Steps
Proceed to `deepgram-data-handling` for transcript storage and processing patterns.
