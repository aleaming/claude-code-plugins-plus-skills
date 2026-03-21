---
name: speak-rate-limits
description: |
  Implement Speak rate limiting, backoff, and idempotency patterns for language learning APIs.
  Use when handling rate limit errors, implementing retry logic,
  or optimizing API request throughput for Speak integrations.
  Trigger with phrases like "speak rate limit", "speak throttling",
  "speak 429", "speak retry", "speak backoff".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Speak Rate Limits

## Overview
Rate limit management for Speak's language learning API. Audio processing endpoints are computationally expensive, with stricter limits on pronunciation assessment than text-based endpoints. Covers per-endpoint tracking, batch queuing, and retry logic.

## Prerequisites
- Speak API access configured
- Understanding of audio processing latency
- Queue infrastructure for batch assessments (optional)

## Speak API Rate Limits

| Endpoint | Limit | Notes |
|----------|-------|-------|
| Pronunciation Assessment | 30/min | Audio processing intensive |
| Conversation Start | 20/min | Creates session state |
| Conversation Turn | 60/min | Within active sessions |
| Translation | 120/min | Text-only, faster |

## Instructions

### Step 1: Identify Endpoint Limits
Review the rate limits table above. Map each API call in the application to its endpoint category. Alternatively, check the `X-RateLimit-Remaining` response header for real-time tracking.

### Step 2: Implement Per-Endpoint Rate Limiter
Create a thread-safe rate limiter that tracks sliding windows per endpoint. Block requests that would exceed the limit until capacity is available.

### Step 3: Add Retry Logic for 429 Responses
Parse the `Retry-After` header from 429 responses. Sleep for the specified duration before retrying. Limit retries to 3 attempts with exponential backoff.

### Step 4: Queue Batch Assessments
Submit multiple pronunciation assessments to a priority queue. Process them sequentially within rate limits, recording results per student.

### Step 5: Monitor Rate Limit Usage
Track used vs. available capacity per endpoint. Log warnings when approaching 80% of any endpoint limit. Adjust batch processing speed based on remaining capacity.

For complete Python rate limiter class, batch assessment queue, retry handler, and rate status monitor, see [limiter implementation](references/limiter-implementation.md).

## Output
- Rate limiter implementation configured per endpoint
- Retry logic with backoff for 429 responses
- Batch assessment queue with priority ordering
- Monitoring output showing rate limit usage

## Error Handling
| Issue | Cause | Solution |
|-------|-------|----------|
| 429 on assessment | Exceeded 30/min pronunciation limit | Queue assessments and spread over time |
| Slow batch processing | Sequential audio processing | Respect rate limits; avoid excessive parallelism |
| Session timeout | Conversation idle too long | Send turns within the session timeout window |
| Audio upload rejected | File exceeds 25MB | Compress audio before uploading |

## Examples

**Basic rate limiting**: Instantiate `SpeakRateLimiter()`, call `limiter.wait_if_needed("pronunciation")` before each assessment request, and let the limiter automatically sleep when the 30/min limit is reached.

**Batch student assessments**: Submit 50 student recordings to `AssessmentQueue` with priority levels, call `process_all()` to process within rate limits, and review the results dictionary for scores and failures.

## Resources
- [Speak API Docs](https://docs.speak.com)

## Next Steps
Proceed to `speak-sdk-patterns` for production-ready SDK patterns.
