---
name: deepgram-core-workflow-b
description: |
  Implement real-time streaming transcription with Deepgram.
  Use when building live transcription, voice interfaces,
  or real-time audio processing applications.
  Trigger with phrases like "deepgram streaming", "real-time transcription",
  "live transcription", "websocket transcription", "voice streaming".
allowed-tools: Read, Write, Edit, Bash(npm:*), Bash(pip:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Deepgram Core Workflow B: Streaming Transcription

## Overview
Build real-time streaming transcription with the Deepgram WebSocket API. Covers live audio capture, WebSocket connection management, interim/final result handling, and speaker diarization in streaming mode.

## Prerequisites
- Deepgram API key configured
- `@deepgram/sdk` npm package installed
- Microphone access (for live capture) or audio stream source
- WebSocket support in the runtime environment

## Instructions

### Step 1: Create WebSocket Connection
Initialize a live transcription connection with model, language, smart formatting, and interim results enabled. Register event handlers for Open, Transcript, UtteranceEnd, Error, and Close events.

### Step 2: Configure Audio Capture
Capture audio from the system microphone using Sox (`rec` command) at 16kHz, 16-bit, mono. Alternatively, pipe audio from any readable stream source.

### Step 3: Send Audio Chunks
Stream audio data to the Deepgram connection by calling `connection.send(chunk)` on each data event from the audio source.

### Step 4: Handle Interim and Final Results
Distinguish between interim (in-progress) and final (committed) transcription results. Accumulate final results while displaying interim results for real-time feedback.

### Step 5: Add Speaker Diarization
Enable `diarize: true` in connection options. Process word-level speaker assignments to group output by speaker segments.

### Step 6: Implement Connection Lifecycle
Close the connection gracefully with `connection.finish()` when audio capture ends. Implement auto-reconnect with exponential backoff for production resilience.

For complete TypeScript implementation including WebSocket setup, audio capture, result management, speaker diarization, and SSE endpoint, see [streaming implementation](references/streaming-implementation.md).

## Output
- Live transcription WebSocket connection
- Real-time transcript display with interim results
- Speaker-labeled conversation output
- Graceful connection lifecycle management

## Error Handling
| Issue | Cause | Solution |
|-------|-------|----------|
| WebSocket disconnects | Network instability | Implement auto-reconnect with backoff |
| No audio data | Microphone not captured | Check audio device permissions and format |
| High latency | Network congestion | Use `interim_results: true` for perceived speed |
| Missing speakers | Diarization not enabled | Set `diarize: true` in connection options |

## Examples

**Live microphone transcription**: Start a WebSocket connection with Nova-2, capture microphone audio via Sox at 16kHz mono, stream chunks to the connection, and print final results to stdout.

**SSE streaming endpoint**: Create an Express GET endpoint that opens a Deepgram WebSocket, streams transcript events as SSE `data:` messages, and closes the connection when the client disconnects.

## Resources
- [Deepgram Streaming API](https://developers.deepgram.com/docs/streaming)
- [Deepgram Node SDK](https://github.com/deepgram/deepgram-node-sdk)
- [Deepgram Models](https://developers.deepgram.com/docs/models-overview)

## Next Steps
Proceed to `deepgram-data-handling` for transcript processing and storage patterns.
