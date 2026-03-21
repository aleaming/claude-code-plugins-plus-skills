# Security Validation Checklist (30% Weight)

Source: [Vertex AI Security Best Practices](https://cloud.google.com/vertex-ai/docs/security)

---

## IAM & Access Control

- Service accounts follow least privilege principle
- No overly permissive roles (Owner, Editor)
- Workload Identity configured for multi-cloud
- API keys rotated regularly (max 90 days)
- No hardcoded credentials in code or env vars
- Service account key rotation policy enforced

### Validation Commands

```bash
# List service account bindings
gcloud projects get-iam-policy PROJECT_ID \
  --flatten="bindings[].members" \
  --format="table(bindings.role, bindings.members)" \
  --filter="bindings.members:serviceAccount"

# Check for overly permissive roles
gcloud projects get-iam-policy PROJECT_ID \
  --flatten="bindings[].members" \
  --filter="bindings.role:(roles/owner OR roles/editor)"
```

---

## Network Security

- VPC Service Controls enabled for Agent Engine
- Private IP addressing configured
- Firewall rules follow allowlist approach
- TLS 1.3 enforced for all connections

### Validation Commands

```bash
# Check VPC-SC perimeters
gcloud access-context-manager perimeters list \
  --policy=POLICY_ID --format="table(name, status.resources)"

# Verify restricted services
gcloud access-context-manager perimeters describe PERIMETER_NAME \
  --policy=POLICY_ID --format="yaml(status.restrictedServices)"
```

Source: [VPC Service Controls](https://cloud.google.com/vpc-service-controls/docs)

---

## Data Protection

- Encryption at rest with CMEK keys (preferred) or Google-managed
- Encryption in transit (TLS)
- Model Armor enabled for ADK-based agents
- Sensitive data handling complies with policies

### Validation

```python
def validate_security(agent_config):
    checks = []
    service_account = agent_config.get('service_account')
    if has_overly_permissive_roles(service_account):
        checks.append({
            "category": "Security", "check": "IAM Least Privilege",
            "status": "FAIL",
            "message": f"Service account {service_account} has Owner role"
        })
    if not agent_config.get('encryption_config', {}).get('cmek_key'):
        checks.append({
            "category": "Security", "check": "Encryption at Rest",
            "status": "WARNING",
            "message": "No CMEK key configured, using Google-managed keys"
        })
    if agent_config.get('agent_framework') == 'google-adk':
        if not agent_config.get('model_armor_enabled'):
            checks.append({
                "category": "Security", "check": "Model Armor",
                "status": "FAIL",
                "message": "Model Armor not enabled for ADK agent"
            })
    return checks
```

Source: [Model Armor Documentation](https://cloud.google.com/vertex-ai/docs/generative-ai/model-armor)
