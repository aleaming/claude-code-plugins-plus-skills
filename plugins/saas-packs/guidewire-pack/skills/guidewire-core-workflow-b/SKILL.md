---
name: guidewire-core-workflow-b
description: |
  Execute Guidewire secondary workflow: Claims processing in ClaimCenter.
  Use when implementing FNOL, claim investigation, reserves, payments, and settlement.
  Trigger with phrases like "claimcenter workflow", "create claim", "file fnol",
  "process claim", "claim settlement", "claim payment".
allowed-tools: Read, Write, Edit, Bash(curl:*), Bash(npm:*), Grep
version: 1.0.0
license: MIT
author: Jeremy Longshore <jeremy@intentsolutions.io>
compatible-with: claude-code, codex, openclaw
---
# Guidewire Core Workflow B: Claims Processing

## Overview
Master the complete claims lifecycle in ClaimCenter: First Notice of Loss (FNOL), claim investigation, reserve setting, payments, and settlement. Supports auto, property, and general liability claim types.

## Prerequisites
- Completed `guidewire-install-auth` and `guidewire-core-workflow-a`
- Understanding of claims handling processes
- Valid API credentials with claims admin permissions

## Claims Lifecycle States

```
FNOL -> Open -> Investigation -> Evaluation -> Negotiation -> Settlement -> Closed
[Draft] [Open]   [Reserve]      [Exposure]    [Payment]     [Settle]    [Closed]
```

## Instructions

### Step 1: Create FNOL
1. POST to `/fnol/v1/fnol` with loss date, loss type/cause, description, policy number, loss location, and reporter details
2. Verify the claim number is returned in the response

### Step 2: Add Exposures
1. POST exposures to `/claim/v1/claims/<claimId>/exposures`
2. Specify exposure type (`VehicleDamage`, `BodilyInjury`, or `PropertyDamage`)
3. Set loss party (`insured` or `claimant`) and primary coverage
4. Alternatively, create multiple exposure types on a single claim for complex losses

### Step 3: Add Incidents
1. POST vehicle or property incidents with severity, damage description, and details
2. Link incidents to the corresponding exposures

### Step 4: Set Reserves
1. POST reserves to each exposure specifying reserve line (`indemnity` or `expenses`)
2. Configure cost type, category, and initial reserve amount
3. Adjust reserves as the claim investigation progresses

### Step 5: Create Payments
1. POST payments with payment type (`partial` or `final`)
2. Specify exposure reference, payee, reserve line, amount, and payment method
3. Alternatively, use direct deposit instead of check for faster processing

### Step 6: Close Exposures
1. POST to each exposure's `/close` endpoint with the closed outcome
2. Select outcome: `completed`, `denied`, or `duplicate`

### Step 7: Close Claim
1. Verify all exposures are closed before attempting claim closure
2. POST to `/claim/v1/claims/<claimId>/close` with the final outcome

For complete TypeScript API calls and Gosu server-side implementations, see [implementation guide](references/implementation-guide.md).

## Output
- FNOL claim with assigned claim number
- Exposures linked to applicable coverages
- Reserves set and tracked on exposures
- Payments processed to payees
- Claim closed with documented outcome

## Error Handling

| Error | Cause | Solution |
|-------|-------|----------|
| Policy not found | Invalid policy number | Verify policy number and active status |
| Coverage not applicable | Wrong coverage type | Check policy coverages before adding exposure |
| Reserve exceeds limit | Over policy limit | Adjust reserve amount to policy limits |
| Payment validation | Missing required fields | Check payee, amount, and reserve line |
| Cannot close | Open activities or exposures | Complete all pending items before closure |

## Examples

**Auto collision claim**: File an FNOL for a two-vehicle accident. Create `VehicleDamage` and `BodilyInjury` exposures. Set reserves of $5,000 for vehicle repair and $2,000 for medical expenses. Issue a partial payment to the body shop, then close exposures and the claim after settlement.

**Property damage with subrogation**: File an FNOL for water damage at a commercial property. Create a `PropertyDamage` exposure, set indemnity reserves, process payments to the restoration contractor. Alternatively, pursue subrogation against the responsible party and close the claim with recovered amounts.

## Resources
- [ClaimCenter Cloud API](https://docs.guidewire.com/cloud/cc/202503/apiref/)
- [Claims Workflow Guide](https://docs.guidewire.com/cloud/cc/202503/cloudapica/)
- [Exposure Types Reference](https://docs.guidewire.com/education/)

## Next Steps
For error handling patterns, see `guidewire-common-errors`.
