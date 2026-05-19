# STEM BIO-AI Local Audit Report

**Target:** `yorkeccak/bio`
**Execution Mode:** `LOCAL_ANALYSIS`
**Calibration Profile:** `default` (`ca-policy-1.0`, `mirror_only`, `authoritative_release`)
**Calibration Effect:** mirror-only in 1.7.8 — selected profile metadata is surfaced in artifacts, but authoritative scan scoring still follows deterministic runtime constants. Preview-only posture changes, including Stage 4 replication emphasis, do not change the formal score until a future read-through phase. Use `stem policy simulate` to preview governed score deltas and posture changes.
**Final Score:** **48 / 100**
**Formal Tier:** **T1 Quarantine**
**Use Scope:** Exploratory review only; no patient-adjacent use.

## Score Matrix

| Stage | Weight | Score |
| --- | ---: | ---: |
| Stage 1 README Evidence Signal | 0.40 | 75 |
| Stage 2R Repo-Local Consistency | 0.20 | 40 |
| Stage 3 Code/Bio Responsibility | 0.40 | 25 |
| Risk Penalty | -- | 0 |

## Replication Evidence Lane

**Stage 4 Replication Score:** **30 / 100**
**Replication Tier:** **R1**

## Audit Freshness

**Review After:** **45 days**
**Expires On:** `2026-07-02`
**Change-triggered re-audit recommended now:** `False`
**Current re-audit reasons:** `none`
**Trigger examples:** `git_commit_changed, readme_or_docs_claim_surface_changed, dependency_manifest_changed, dataset_or_model_reference_changed`

## Reasoning Diagnostics

Diagnostic-only heuristic `stem-bio-ai-reasoning-v1.3.2` (uncalibrated_initial_priors_pending_benchmark_calibration); lane consistency `heuristic_mixed` (0.725), uncertainty band `review_advised` (0.2789), risk heuristic `within_heuristic_gate` (0.4825), confidence envelope 0.431-0.529. This heuristic layer does not override the final score.

## Regulatory Traceability Assistant

> **Regulatory basis note**
> Aligned to current official source classes as of May 2026: EU AI Act (Regulation (EU) 2024/1689), FDA QMSR, FDA AI-enabled device guidance themes, and IMDRF SaMD/GMLP frameworks.
> This is a traceability aid, not a compliance or clearance determination.

### Stage 1
- **EU_AI_ACT_ARTICLE_13** — signal_only (mapping confidence: weak, evidence strength: weak)
  - Boundary, intended-use, and limitation language is relevant to transparency scaffolding only.
- **COMPLIANCE_CLAIM_GROUNDING_SIGNAL** — signal_only (mapping confidence: weak_moderate, evidence strength: weak)
  - Legal or compliance claims without supporting governance evidence are relevant to transparency and quality-system review, not compliance proof.

### Stage 2R
- **IMDRF_CLINICAL_CONTEXT_BOUNDARY_SIGNAL** — signal_only (mapping confidence: weak_moderate, evidence strength: moderate)
  - Repository-local contradiction and boundary signals are relevant to clinical-context traceability, not clinical validation.

### Stage 3
- **EU_AI_ACT_ARTICLE_10** — signal_only (mapping confidence: weak, evidence strength: weak)
  - Provenance and bias signals are relevant to data-governance review, but do not verify execution quality.

### Stage 4
- **EU_AI_ACT_ARTICLE_12** — partially_aligned (mapping confidence: moderate, evidence strength: moderate)
  - Reproducibility and trace manifests support record-keeping scaffolding, not operational logging completeness.

**Summary:** Structural signals partially align with traceability scaffolding. This remains a pre-audit traceability aid, not a compliance determination.

## AIRI Coverage

**Covered Risks:** **7 / 32**
**Coverage Rate:** `0.219`
**Bundle Scope:** `curated_medical_clinical_subset`
**Upstream Snapshot:** `2026-04-23`

**Examples of Covered AIRI Risks**
- `24.01.03` — Safe exploration problem with widely deployed AI assistants (covered by: C5_compliance_boundary_integrity; why: C5_compliance_boundary_integrity: Unsupported legal/compliance claim surfaced in boundary-integrity lane.)
- `24.04.01` — Physical and Psychological Harms (covered by: C2_dependency_pinning; why: C2_dependency_pinning: External operational dependency signal surfaced in code-integrity lane.)
- `33.01.05` — Privacy and security (covered by: C2_dependency_pinning; why: C2_dependency_pinning: External operational dependency signal surfaced in code-integrity lane.)

**Known Gaps In Bundle**
- `65.03.03` — Reidentification
- `70.02.02` — Misinformation — hallucination of clinical knowledge
## Code Integrity
- **C1_hardcoded_credentials:** PASS — No direct credential patterns detected by local CLI scan.
- **C2_dependency_pinning:** WARN — External operational dependency signal surfaced in code-integrity lane.
- **C3_dead_or_deprecated_patient_adjacent_paths:** PASS — No deprecated patient-adjacent metadata patterns detected.
- **C4_exception_handling_clinical_adjacent_paths:** PASS — No executable fail-open exception handler detected.
- **C5_compliance_boundary_integrity:** WARN — Unsupported legal/compliance claim surfaced in boundary-integrity lane.
- **C6_mock_auth_or_fail_open_boundary:** WARN — Mock-auth or auto-login boundary surfaced in code-integrity lane.

## Bio Deterministic Diagnostics

- **SMILES Surface Integrity:** not_detected=1 — No malformed or suspicious SMILES-like strings detected by conservative surface checks.
- **SMILES RDKit Validation:** not_detected=1 — RDKit optional validation lane not exercised because no SMILES-like candidates were detected.
- **SMILES Parser Guard:** not_detected=1 — No missing None/invalid guards detected after SMILES parser calls.
- **Silent Mock Fallback:** not_detected=1 — No silent mock or simulated-data fallback patterns detected in production code paths.
- **Traceability Manifest Surface:** not_detected=1 — No traceability manifest or runtime audit-log schema surface detected.
- **Bio Subprocess Run Trace:** not_detected=1 — No risky subprocess or os.system bio-tool execution patterns detected.

## Top Risks
- Clinical-adjacent surfaces exist without an explicit non-diagnostic/non-clinical boundary.
- Self-asserted compliance or privacy-governance claim requires independent verification.
- Legal, privacy, or compliance claim appears without supporting governance or security-grounding evidence in reviewed repository sources.
- Core workflow appears materially dependent on named external service providers; local or self-host claims may overstate operational independence.
- C2_dependency_pinning: WARN

## Disclaimer
This is an evidence-surface pre-screen, not clinical certification, regulatory clearance, or medical advice.
