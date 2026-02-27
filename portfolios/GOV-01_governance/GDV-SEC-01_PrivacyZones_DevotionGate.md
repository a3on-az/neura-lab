# GDV-SEC-01: Privacy Zones & Devotion Gate Enforcement

## Policy Scope
This file enforces strict boundary rules for data retention, ingestion consent gating, and cross-agent sharing to maintain compliance with HIPAA, specifically tailored for the `AMP-01` clinical applications.

### Red-Zone Data Retention
1. **PHI Boundary**: Any interaction or log containing identifying characteristics corresponding to a patient or entity within the clinical domain is explicitly restricted to a secure processing tier. Agent inference traces or token histories must be immediately scrubbed or retained exclusively in encrypted `/tmp` volumes.
2. **LLM Submission Constraints**: The Pi Harness is strictly prohibited from sending PHI outside local instances or managed, dedicated VPC endpoints (e.g., Nimbus GCP nodes). Absolutely NO red-zone data may be passed to open API endpoints like OpenAI or general Anthropic models without local scrubbing/anonymization logic.

### Devotion Gate Policies
1. **Consent Requisites**: Projects flagged as requiring participant-aligned ingestion must ensure that the "Devotion Gate" (GDV-DG-01) status evaluates to TRUE.
2. If `consent_state == false` or evaluation remains undetermined, the Pi Agent is instructed to halt task execution and output a `[TELEOLOGICAL HALT]` flag to require human-in-the-loop validation.

### Agentic Sub-Routine Execution
If a sub-agent is spawned in `E2B-sandbox` or a similar environment to process telemetry or telemetry metadata for an associated clinical target, the sandbox manifest **must not** have networking capabilities to public CDNs or untrusted remote hosts pending an explicit override in the canonical config.
