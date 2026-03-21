---
name: granola-cost-tuning
description: |
  Optimize Granola costs and select the right pricing plan.
  Use when evaluating plans, reducing costs,
  or maximizing value from Granola subscription.
  Trigger with phrases like "granola cost", "granola pricing",
  "granola plan", "save money granola", "granola subscription".
allowed-tools: Read, Write, Edit
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Granola Cost Tuning

## Overview
Optimize Granola costs by selecting the right plan, managing storage efficiently, and maximizing ROI from meeting capture. Covers individual and team cost analysis, negotiation strategies, and waste reduction.

## Prerequisites
- Current Granola plan details and usage metrics
- Team size and meeting frequency data
- Access to Granola Settings > Account for usage review

## Instructions

### Step 1: Calculate Individual ROI
```markdown
Time Saved per Meeting:
- Manual note-taking: 15-30 min/meeting
- With Granola: 0-5 min/meeting
- Time saved: ~20 min/meeting

Monthly Calculation:
Meetings per month: [20]
Time saved: 20 * 20 min = 400 min = 6.7 hours
Hourly rate: [$50]
Value of time saved: 6.7 * $50 = $333

Cost of Granola Pro: $10/month
Break-even: 0.6 meetings/month
```

### Step 2: Select the Right Plan
```markdown
< 10 meetings/month: Stay on Free
10-30 meetings/month (individual): Pro ($10/month)
Team of 2-10: Business ($25/user), or 2 Pro accounts if no admin needs
Team of 10+: Business or Enterprise (contact sales for volume discount)
```

### Step 3: Optimize Meeting Recording
Record selectively to stay within plan limits:
- **Record:** Client meetings, sprint planning, design reviews, important 1:1s
- **Skip:** Quick syncs (< 5 min), social calls, redundant status updates

### Step 4: Monitor Usage Monthly
Check in Settings > Account each month:
1. Review meetings recorded this month
2. Verify storage usage against plan limits
3. Audit integration usage and active seats
4. Downgrade unused accounts or reassign inactive seats

### Step 5: Negotiate Enterprise Pricing
Alternatively, contact sales for volume discounts when scaling beyond 10 users. Commit to annual billing for 10-15% savings, or negotiate multi-year agreements for 20-30% off.

For complete pricing tables, ROI calculators, storage management strategies, competitor comparisons, and negotiation tactics, see [pricing details](references/pricing-details.md).

## Output
- Plan recommendation with ROI justification
- Monthly cost optimization actions identified
- Storage management schedule established

## Error Handling

| Error | Cause | Resolution |
|-------|-------|------------|
| Unexpected billing increase | Seat count changed | Review active users in admin panel |
| Storage limit reached | Old notes not archived | Export and delete meetings older than 6 months |
| Integration cost spike | Zapier task overuse | Batch notifications and combine Zap actions |

## Examples

**Individual optimization**: Calculate ROI at $50/hour with 20 meetings/month. Time saved is 6.7 hours ($333 value) against $10 Pro cost. Verify break-even at 0.6 meetings/month.

**Team cost reduction**: Audit 10-person Business plan for inactive seats. Reassign 2 unused seats, export notes older than 6 months, and switch to annual billing to save $450/year.

## Resources
- [Granola Pricing](https://granola.ai/pricing)
- [Plan Comparison](https://granola.ai/compare)
- [Enterprise Contact](https://granola.ai/enterprise)

## Next Steps
Proceed to `granola-reference-architecture` for enterprise deployment patterns.
