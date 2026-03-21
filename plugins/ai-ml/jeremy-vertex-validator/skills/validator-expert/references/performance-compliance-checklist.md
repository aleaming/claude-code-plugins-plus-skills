# Performance (25% Weight) & Compliance (15% Weight) Checklists

---

## Performance Validation

### Auto-Scaling
- Auto-scaling enabled for Agent Engine
- Min/max replicas configured appropriately
- CPU/memory targets set
- Scale-up/scale-down thresholds tuned

### Caching
- Memory Bank caching enabled
- Cache hit rate >60%
- Cache TTL configured
- Response caching for frequent queries

### Resource Limits
- Memory limits appropriate for workload
- CPU allocation sufficient
- Timeout values configured
- Concurrent request limits set

### Code Execution Sandbox
- Sandbox state persistence TTL configured (1-14 days)
- Execution timeout appropriate
- Artifact storage configured
- Resource isolation enabled

### Validation

```python
def validate_performance(agent_config):
    checks = []
    runtime_config = agent_config.get('runtime_config', {})
    auto_scaling = runtime_config.get('auto_scaling', {})
    if not auto_scaling.get('enabled'):
        checks.append({
            "category": "Performance", "check": "Auto-Scaling",
            "status": "WARNING", "message": "Auto-scaling not enabled"
        })
    code_exec = runtime_config.get('code_execution_config', {})
    ttl_days = code_exec.get('state_persistence_ttl_days', 0)
    if ttl_days < 1 or ttl_days > 14:
        checks.append({
            "category": "Performance", "check": "Code Execution TTL",
            "status": "FAIL", "message": f"TTL must be 1-14 days, got {ttl_days}"
        })
    return checks
```

---

## Compliance Validation

### Audit Logging
- Cloud Audit Logs enabled
- Admin activity logged
- Data access logs enabled for sensitive operations
- Log retention >1 year for compliance

### Data Residency
- Agent deployed in compliant region
- Data storage in approved locations
- Cross-border data transfer documented
- Regional data processing requirements met

### Privacy
- PII handling policies implemented
- User consent mechanisms in place
- Data anonymization for non-prod environments
- Right to deletion implemented

### Backup & DR
- Memory Bank backup configured
- Disaster recovery plan documented
- RTO/RPO objectives defined
- Backup restoration tested

### Validation

```python
def validate_compliance(agent_config, project_id):
    from google.cloud import logging_v2
    client = logging_v2.ConfigServiceV2Client()
    parent = f"projects/{project_id}"
    sinks = client.list_sinks(parent=parent)
    audit_sink_exists = any('audit' in sink.name.lower() for sink in sinks)
    if not audit_sink_exists:
        return {
            "category": "Compliance", "check": "Audit Logging",
            "status": "FAIL", "message": "No audit log sink configured"
        }
    return {
        "category": "Compliance", "check": "Audit Logging",
        "status": "PASS", "message": "Audit logging configured"
    }
```

Source: [Cloud Audit Logs](https://cloud.google.com/logging/docs/audit)
