# OPS-EVAL-01: Experimental Evaluation Harness

## Outline
This specification covers the repeatable experiment runner required for Neura-Lab's Pillar 5 operations. The scope involves evaluating "transmutation" quality using triplet datasets and stability scoring.

### Methodology
1. **Triplet Datasets**: Each test scenario is evaluated across three primary dimensions: Initial input representation, output generation, and counterfactual constraint checking (Adversarial falsification via `FCog`).
2. **Shadow Transmutation**: Agents output artifacts to a temporary directory for parallel processing and invariance checks before updating canonical registries.
3. **Metrics Tracking**: Each run is timestamped and quantified on ROI stability criteria (as defined conceptually in metric engineering guidelines).
4. **Agent Integration**: The Pi telemetry extension must wrap these steps and transmit a final measurement vector to the Orchestrator dashboard for HITL review.

### Usage Protocol
Run the testing harness via:
`pi eval --target <slug> --mode triplet`

The output is aggregated into `audit_logs/` ensuring that a high telos alignment score implies safe assimilation into the NM directory.
