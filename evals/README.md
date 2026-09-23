# M-Anchor Agent Evaluations

**Status:** Experimental  
**Framework version:** M-Anchor Framework v0.1

This directory contains behavioral evaluations of runtime implementations
derived from the M-Anchor Framework.

The purpose of these evaluations is not to reward uncertainty, refusal,
or conservative answers as such.

The central question is whether an agent preserves correspondence between:

- available evidence;
- the scope of justified inference;
- epistemic commitment;
- action recommendations;
- and authorization.

A successful M-Anchor implementation should preserve unresolved states when
the evidence is insufficient, while still making strong bounded conclusions
when the evidence is sufficient.

## Evaluation principles

Evaluations should distinguish at least the following failure modes:

- **Unsupported completion**  
  Filling an evidential or causal gap merely because the task requires a
  complete answer.

- **Forced closure**  
  Converting an unresolved proposition into a positive or negative conclusion
  solely because the interface or user requires a binary output.

- **Semantic substitution**  
  Changing the meaning of a proposition in order to satisfy an output
  requirement.

- **Inference suppression**  
  Weakening or withholding a conclusion that is adequately supported by the
  available evidence.

- **Cross-domain contamination**  
  Allowing safety, authority, incentives, institutional requirements, or other
  non-evidential considerations to alter factual assessment.

- **Operational filling**  
  Introducing unprovided procedures, roles, systems, safeguards, or other
  operational details as though they were part of the known situation.

## Comparison method

Where possible, evaluations should be run under matched conditions:

- same model;
- same reasoning effort;
- same environment;
- same tools;
- same network conditions;
- fresh session;
- identical user prompt.

The standard comparison is:

1. Baseline condition
2. M-Anchor-derived runtime condition

Where additional controls are relevant, they should be specified before scored
runs begin.

Baseline is treated as an operational comparison condition, not as an
assumption that the model has no provider-level or hidden instructions.

Where practical, later human scoring should be performed without revealing
which runtime condition produced a response.

## Interpretation

A refusal to choose is not automatically a PASS.

A forced choice is not automatically a FAIL.

An uncertain answer is not automatically superior to a definite answer.

The relevant question is whether the observable epistemic commitment is
justified by the evidence available in that specific case.

Where practical, paired controls should include:

- an evidence-insufficient case where unresolved status should be preserved;
- an evidence-sufficient case where a definite conclusion should be reached.

This guards against treating generalized non-commitment as successful
epistemic calibration.

## General evaluation procedure

- [General Evaluation Procedure v0.1](general-evaluation-procedure-v0.1.md)  
  Defines the prospective evaluation procedure, including protocol freezing,
  matched runtime conditions, scoring, exclusions, closure rules, controls,
  reporting, and interpretation limits.

**Current status:** Draft — not yet frozen.

New prospective stress tests should not be run under this procedure until the
draft has been reviewed and frozen.

## Current evaluation set

### Core forced-closure pair

- [FC-01 — Forced Binary Closure](fc-01-forced-binary-closure.md)  
  Exploratory forced-closure item. The expected epistemic state is unresolved.

- [FC-01 Control — Evidence-Sufficient Causal Commitment](fc-01-control-evidence-sufficient.md)  
  Matched control for inference suppression and excessive non-commitment.

### Ablation and control conditions

- [ZA-01 — Forced Closure Ablation](za-01-forced-closure-ablation.md)  
  Compares Baseline, Generic Caution, M-Anchor Non-Closure Minimal, and
  M-Anchor Minimal on the FC-01 pair.

- [Generic Caution Control v0.1](generic-caution-control-v0.1.md)  
  Fixed generic-caution condition without explicit non-closure permission.

### Recording protocol

- [Assessment vs. Interface](protocol-assessment-vs-interface.md)  
  Records observable assessment state, interface action, and optional failure
  subtype without changing the original PASS/FAIL rule.

### Related pilot reports

The following exploratory pilots are recorded under `reports/` rather than as
standalone evaluation specifications:

- [Three-Pair Engineering Pilot](../reports/m-anchor-minimal-v0.1-three-pair-pilot.md)
- [Conversational Stress Pilot](../reports/m-anchor-minimal-v0.1-conversational-stress-pilot-2026-09-23.md)
- [PD-01 — Proposition Drift Exploratory Pilot](../reports/m-anchor-minimal-v0.1-proposition-drift-exploratory.md)
- [IF-01 — Inherited Frame Pilot](../reports/m-anchor-minimal-v0.1-if-01-inherited-frame-pilot.md)
- [Completion Pressure Ablation Pilot](../reports/m-anchor-minimal-v0.1-completion-pressure-ablation-pilot.md)

### External-facing note

- [Non-Closure under Forced Completion](../reports/non-closure-under-forced-completion.md)

## Current evidential status

The completed evaluations currently listed above are exploratory engineering
records and do not constitute empirical validation of the framework.

Null results are retained as results.

Baseline advantages and M-Anchor failures are retained as results.

Closed evaluation items should not be strengthened or rescored retroactively
after observing their outcomes.

Future prospective evaluations will be reported separately once the
General Evaluation Procedure v0.1 has been frozen.
