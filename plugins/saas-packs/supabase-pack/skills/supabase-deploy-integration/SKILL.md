---
name: supabase-deploy-integration
description: |
  Deploy Supabase integrations to Vercel, Fly.io, and Cloud Run platforms.
  Use when deploying Supabase-powered applications to production,
  configuring platform-specific secrets, or setting up deployment pipelines.
  Trigger with phrases like "deploy supabase", "supabase Vercel",
  "supabase production deploy", "supabase Cloud Run", "supabase Fly.io".
allowed-tools: Read, Write, Edit, Bash(vercel:*), Bash(fly:*), Bash(gcloud:*)
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Supabase Deploy Integration

## Overview
Deploy Supabase-powered applications to production on Vercel, Fly.io, or Google Cloud Run. Covers platform-specific secret management, deployment configuration, health checks, and environment-specific connection pooling.

## Prerequisites
- Supabase API keys for the production environment
- Platform CLI installed (vercel, fly, or gcloud)
- Application code ready for deployment
- Environment variables documented

## Instructions

### Step 1: Choose Deployment Platform
Select the platform that fits the infrastructure needs. Alternatively, deploy to multiple platforms for redundancy or multi-region availability.

### Step 2: Configure Production Secrets
1. Store `SUPABASE_URL` and `SUPABASE_ANON_KEY` using the platform's secrets management
2. Add `SUPABASE_SERVICE_ROLE_KEY` for server-side operations
3. Configure connection pooling via `DATABASE_URL` with pgBouncer

### Step 3: Deploy the Application
1. Run the platform-specific deploy command (e.g., `vercel deploy --prod`, `fly deploy`, `gcloud run deploy`)
2. Verify the build completes without errors
3. Check deployment logs for Supabase connection issues

### Step 4: Verify Health
1. Test the health check endpoint to confirm Supabase connectivity
2. Verify database queries return expected results
3. Check real-time subscriptions connect successfully (if applicable)

### Step 5: Configure Environment-Specific Settings
Set up separate Supabase projects for staging and production. Use environment-specific API keys and connection strings to isolate data.

For Vercel-specific deployment, Fly.io configuration, Cloud Run setup, and troubleshooting guides, see:
- [Vercel deployment guide](references/vercel-deployment.md)
- [Cloud Run deployment guide](references/google-cloud-run.md)
- [Deployment examples](references/examples.md)
- [Error reference](references/errors.md)

## Output
- Application deployed to production
- Supabase secrets securely configured per platform
- Health check endpoint functional and verified
- Environment-specific configuration in place

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| Connection refused | Wrong Supabase URL | Verify `SUPABASE_URL` matches the project |
| Auth error on deploy | Missing service role key | Add `SUPABASE_SERVICE_ROLE_KEY` to secrets |
| Timeout on health check | Connection pooling misconfigured | Use pgBouncer URL for `DATABASE_URL` |
| Build failure | Missing environment variables | Verify all required vars are set in platform |

## Examples

**Vercel deployment**: Run `vercel env add SUPABASE_URL production`, add the anon key and service role key, then run `vercel deploy --prod`. Verify with `curl https://your-app.vercel.app/api/health`.

**Cloud Run deployment**: Create secrets with `gcloud secrets create`, reference them in `service.yaml`, deploy with `gcloud run deploy`, and verify the health endpoint returns a 200 status.

## Resources
- [Vercel Documentation](https://vercel.com/docs)
- [Fly.io Documentation](https://fly.io/docs)
- [Cloud Run Documentation](https://cloud.google.com/run/docs)
- [Supabase Deploy Guide](https://supabase.com/docs/deploy)

## Next Steps
Proceed to `supabase-observability` for monitoring and logging configuration.
