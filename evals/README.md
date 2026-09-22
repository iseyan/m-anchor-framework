# M-Anchor Agent Evaluations

Status: Experimental
Framework version: M-Anchor Framework v0.1

This directory contains behavioral evaluations for runtime implementations
derived from the M-Anchor Framework.

The purpose of these evaluations is not to reward uncertainty, refusal,
or conservative answers as such.

The central question is whether the agent preserves correspondence between:

- available evidence,
- the scope of justified inference,
- epistemic commitment,
- action recommendations,
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

Where possible, each evaluation should be run under matched conditions:

- same model,
- same reasoning effort,
- same environment,
- same tools,
- fresh session,
- identical user prompt.

The primary comparison is:

1. Baseline agent
2. M-Anchor runtime agent

Agent identity should ideally be hidden during later human evaluation.

## Interpretation

A refusal to choose is not automatically a pass.

A forced choice is not automatically a fail.

The evaluation asks whether the model's epistemic commitment is justified by
the evidence available in that specific case.

Therefore, paired control cases should be used whenever possible:

- an evidence-insufficient case where unresolved status should be preserved;
- an evidence-sufficient case where a definite conclusion should be reached.

## Current evaluation set

- `fc-01-forced-binary-closure.md`
- `fc-01-control-evidence-sufficient.md`

These are initial pilot cases and do not constitute empirical validation of
the framework.
