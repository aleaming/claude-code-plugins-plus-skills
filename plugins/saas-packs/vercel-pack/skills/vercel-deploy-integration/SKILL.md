---
name: vercel-deploy-integration
description: |
  Deploy Vercel integrations to Vercel, Fly.io, and Cloud Run platforms.
  Use when deploying Vercel-powered applications to production,
  configuring platform-specific secrets, or setting up deployment pipelines.
  Trigger with phrases like "deploy vercel", "vercel Vercel",
  "vercel production deploy", "vercel Cloud Run", "vercel Fly.io".
allowed-tools: Read, Write, Edit, Bash(vercel:*), Bash(fly:*), Bash(gcloud:*)
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Vercel Deploy Integration

## Overview
Deploy Vercel-powered applications to production across Vercel, Fly.io, or Google Cloud Run. Covers platform-specific secret management, deployment workflows, health verification, and environment isolation for staging and production.

## Prerequisites
- Vercel API keys for the production environment
- Platform CLI installed (vercel, fly, or gcloud)
- Application code ready for deployment
- Environment variables documented

## Instructions

### Step 1: Choose Deployment Platform
Select the target platform based on infrastructure requirements. Alternatively, deploy to multiple platforms for redundancy or multi-region availability.

### Step 2: Configure Production Secrets
1. Store `VERCEL_TOKEN` and environment-specific API keys using the platform's secrets management
2. Add database connection strings and third-party service credentials
3. Verify secrets are scoped to the correct environment (preview, development, or production)

### Step 3: Deploy the Application
1. Run the platform deploy command (e.g., `vercel deploy --prod`, `fly deploy`, `gcloud run deploy`)
2. Verify the build completes without errors
3. Check deployment logs for configuration issues

### Step 4: Verify Health
1. Test the health check endpoint to confirm application connectivity
2. Verify API routes return expected responses
3. Check serverless function cold start times and edge function latency

### Step 5: Configure Environment Isolation
Set up separate environments for staging and production. Use environment-specific variables and deployment branches to isolate data and configuration.

For platform-specific guides, troubleshooting, and deployment examples, see:
- [Vercel deployment guide](references/vercel-deployment.md)
- [Cloud Run deployment guide](references/google-cloud-run.md)
- [Deployment examples](references/examples.md)
- [Error reference](references/errors.md)

## Output
- Application deployed to production
- Secrets securely configured per platform
- Health check endpoint functional and verified
- Environment-specific configuration in place

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| Build failure | Missing environment variables | Verify all required vars are set in the platform |
| Function timeout | Cold start too slow | Optimize bundle size or use edge functions |
| Secret not found | Wrong environment scope | Check secret is scoped to production |
| Deploy rejected | Branch protection rule | Merge to the production branch first |

## Examples

**Vercel production deploy**: Run `vercel env add` for each secret scoped to production, then run `vercel deploy --prod`. Verify with `curl https://your-app.vercel.app/api/health`. Alternatively, configure automatic deployments from the main branch in the Vercel dashboard.

**Cloud Run deploy**: Create secrets with `gcloud secrets create`, reference them in the service YAML, deploy with `gcloud run deploy`, and verify the health endpoint returns a 200 status.

## Resources
- [Vercel Documentation](https://vercel.com/docs)
- [Fly.io Documentation](https://fly.io/docs)
- [Cloud Run Documentation](https://cloud.google.com/run/docs)
- [Vercel Deploy Guide](https://vercel.com/docs/deploy)

## Next Steps
Proceed to `vercel-observability` for monitoring and logging configuration.
