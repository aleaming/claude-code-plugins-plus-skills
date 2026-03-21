# Monitoring Validation Checklist (20% Weight)

Source: [Cloud Monitoring Alerting](https://cloud.google.com/monitoring/alerts)

---

## Observability Dashboard

- Agent Engine observability dashboard configured
- Token usage tracking enabled with per-model granularity
- Error rate monitoring active
- Latency metrics tracked (p50, p90, p95, p99)

## Alerting

- Alert policies configured for critical errors
- Notification channels set up (email, Slack, PagerDuty)
- Alert thresholds appropriate for workload
- Alert escalation policies defined

## SLOs & SLIs

- Service Level Objectives defined
- Error budget configured
- SLI metrics tracked
- SLO compliance reporting enabled

## Logging

- Cloud Logging enabled for Agent Engine
- Log retention policies configured (>90 days for ops, >365 for compliance)
- Structured logging format with severity levels and correlation IDs
- PII data properly redacted in logs

### Validation

```python
def validate_monitoring(agent_id, project_id):
    from google.cloud import monitoring_v3
    client = monitoring_v3.AlertPolicyServiceClient()
    project_name = f"projects/{project_id}"
    alert_policies = client.list_alert_policies(name=project_name)
    agent_alerts = [
        policy for policy in alert_policies
        if agent_id in policy.display_name.lower()
    ]
    if not agent_alerts:
        return {
            "category": "Monitoring", "check": "Alert Policies",
            "status": "FAIL",
            "message": f"No alert policies configured for agent {agent_id}"
        }
    return {
        "category": "Monitoring", "check": "Alert Policies",
        "status": "PASS",
        "message": f"Found {len(agent_alerts)} alert policies"
    }
```
