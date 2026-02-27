# DAT-EVAL-01: Triplet Dataset Contracts for NeuraMem LSM

## Specification Purpose
This document establishes the 'ground truth' structure for evaluating Latent Semantic Mapping (LSM) transmutation quality in Neura-Lab. It dictates the triplet format used to define inputs, expected outputs, and constraints.

## Triplet Structure 
Every Dataset Contract will consist of instances formalized as a Triplet: `[Episode, Context, Shadow]`.

1. **Episode (E):** The raw ingestion event. This can represent text, telemetry, or a multi-modal artifact prior to transformation.
2. **Context (C):** The active policy, intent weighting, or system state under which the Episode occurred or must be interpreted.
3. **Shadow (S):** The canonical "Target" or "After Transmutation" representation.

### Shadow Transmutation Pair Logic
Shadow Transmutation pairs define the relationship between the `Episode` and `Shadow`.

*   **Before Transmutation (Episode+Context):** Evaluating if the agent successfully parsed the raw input subject to the given Context parameters. 
*   **After Transmutation (Shadow):** The required representation in the LSM registry format. This output must pass verification to ensure it did not undergo 'Teleological Drift' (meaning loss).

## Triplet JSON Schema Draft
```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Triplet Dataset Contract",
  "type": "object",
  "properties": {
    "contract_id": { "type": "string" },
    "triplets": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "episode": { "type": "string", "description": "Raw ingestion text or artifact." },
          "context": { "type": "string", "description": "Active policy constraints or state." },
          "shadow": { "type": "string", "description": "Canonical expected output in LSM." }
        },
        "required": ["episode", "context", "shadow"]
      }
    }
  },
  "required": ["contract_id", "triplets"]
}
```
