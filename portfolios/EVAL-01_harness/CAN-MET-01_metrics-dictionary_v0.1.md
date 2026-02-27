# CAN-MET-01: Metrics Dictionary

## Overview
This dictionary formally defines the mathematical baseline for tracking "Teleological Drift" inside Neura-Lab systems. It defines Invariance and ROI Stability equations used across all transmutations.

### 1. Invariance ($\Omega/W$)
Invariance defines how effectively the original semantic intent is preserved across transmutations or Latent Semantic Mapping.

**Formula**: 
$\Omega = \frac{\Delta\text{Intent}}{\Delta\text{Transmutation}}$

Where:
- $\Delta\text{Intent}$ is the change in measurable alignment with the canonical policy.
- $\Delta\text{Transmutation}$ is the structural divergence introduced by an LLM-generation cycle.

A high invariance score ($\Omega \to 1$) indicates robust intent preservation relative to the generated structural changes.

### 2. ROI Stability
ROI (Representation of Intent) Stability evaluates the system-wide alignment to teleological objectives over successive multi-agent sprint cycles.
