# General Evaluation Procedure v0.1

**Status:** Draft — not yet frozen  
**Framework:** M-Anchor Framework v0.1  
**Scope:** Behavioral evaluations of M-Anchor-derived runtime instructions, with prospective specification and explicit exploratory labeling

## 1. Purpose

This document defines the general procedure for constructing, running,
recording, and interpreting behavioral evaluations of M-Anchor-derived
runtime instructions.

The purpose is not to demonstrate that M-Anchor is superior.

The purpose is to test whether a specified runtime condition produces
observable behavioral differences under matched conditions, including
differences that are unfavorable to M-Anchor.

Null results, Baseline advantages, excessive non-commitment, and other
negative results are retained as valid outcomes.

## 2. Evaluation unit

The basic evaluation unit is:

> one fixed evaluation item × one fixed runtime condition × one accepted run

Each evaluation item must define, before scored runs begin:

- the user prompt;
- the target proposition or decision;
- the relevant evidence state;
- the expected epistemic state;
- the primary PASS/FAIL rule or other primary outcome rule;
- relevant failure modes;
- runtime conditions to be compared;
- the number of runs per condition;
- the aggregation rule for multiple runs, if applicable.

The number of runs must not be increased selectively because an observed
result is inconvenient or favorable.

Where multiple runs are used, all accepted runs should be reported.

If multiple runs are reduced to a single summary outcome, the aggregation rule
must be specified before scored runs begin.

## 3. Prospective and exploratory status

Each evaluation must be labeled as one of:

### Prospective

The prompt, scoring rule, runtime conditions, run count, and any aggregation
rule were fixed before any scored output for that evaluation version was
observed.

### Exploratory

The evaluation was created, modified, or selected after observing behavior
that may have influenced its design.

Exploratory results may motivate new prospective evaluations, but must not be
reported as though they were prospectively specified.

Existing closed pilot evaluations retain their original status.

## 4. Pre-run specification

Before the first scored run of a prospective evaluation, record:

1. Evaluation ID and version
2. Target failure mode or mechanism
3. Exact prompt
4. Expected epistemic state
5. Primary scoring rule
6. Secondary recording fields, if any
7. Runtime conditions
8. Model and model version
9. Reasoning effort or equivalent setting
10. Tool availability
11. Network availability
12. Session requirements
13. Number of runs
14. Aggregation rule for multiple runs, if applicable
15. Any paired control item
16. Sampling settings or equivalent parameters, if observable and configurable
17. Planned execution date or execution window
18. Date of protocol freeze
19. Protocol-freeze commit or other fixed repository reference

For prospective evaluations in this repository, the frozen specification must
be committed before scored outputs are collected.

If a platform does not expose a relevant runtime parameter, record it as
unavailable rather than inferring or inventing a value.

## 5. Matched runtime conditions

Comparisons should use matched conditions wherever possible.

Unless an evaluation explicitly tests one of these variables, keep constant:

- model;
- model version;
- reasoning effort;
- environment;
- tool access;
- network access;
- user prompt;
- session state;
- sampling settings, where configurable;
- other system-level settings available to the evaluator.

Each run should use a fresh session unless the evaluation explicitly tests
conversation history or inherited context.

The intended independent variable should be stated explicitly.

For the standard Baseline vs. M-Anchor comparison, the intended independent
variable is the additional runtime instruction condition.

Baseline is an operational comparison condition.

It does not imply that the model has no provider-level, system-level, hidden,
or otherwise unavailable instructions.

Only evaluator-controlled or evaluator-observable differences should be
treated as known experimental variables.

Where platform behavior may change over time, matched conditions should be run
as close together in time as practical.

If conditions are run across materially different dates or model revisions,
that fact must be recorded.

## 6. Runtime conditions

A study may include, where relevant:

1. Baseline
2. Generic control instruction
3. Minimal M-Anchor-derived instruction
4. Full M-Anchor runtime derivation

Additional conditions may be used, but their purpose must be stated before
scored runs begin.

Conditions must not be added after observing results merely to rescue an
interpretation.

## 7. Primary scoring

The primary score for each evaluation item must be fixed before scored runs.

A primary PASS/FAIL rule must evaluate the behavior targeted by that item,
not general agreement with M-Anchor.

A refusal is not automatically a PASS.

A definite answer is not automatically a FAIL.

An uncertain answer is not automatically epistemically superior.

The score depends on whether the observable commitment is justified by the
evidence stipulated in the item.

Primary scoring rules must not be changed after observing scored outputs.

If an accepted output cannot be unambiguously scored under the frozen rule,
it must not be forced into PASS or FAIL by changing the rule after the fact.

Such an output should be retained as scoring-ambiguous unless a pre-specified
adjudication procedure resolves it.

## 8. Secondary recording

Secondary annotations may preserve information that the primary score does
not capture.

Where relevant, record:

- explicit assessment state;
- interface action;
- semantic substitution;
- unsupported completion;
- forced closure;
- inference suppression;
- excessive withholding or over-conservatism;
- operational filling;
- cross-domain contamination;
- scoring ambiguity;
- other pre-specified observable failure subtype.

For forced-completion tests, use the separate
`protocol-assessment-vs-interface.md` recording addendum.

Secondary annotations do not retroactively alter the primary scoring rule.

Do not infer hidden beliefs, intentions, or internal model states from output.

## 9. Valid inference preservation

M-Anchor-derived conditions must not receive credit merely for withholding
commitment.

Where evidence is sufficient, failure to make the supported inference is a
failure mode.

Paired evidence-sufficient controls should be used when practical to test
whether non-closure behavior has become generalized non-commitment.

A condition that reduces unsupported closure while also suppressing valid
inference must be reported as having both effects.

## 10. Run acceptance and exclusion

A run may be excluded only for a pre-specified technical reason, such as:

- wrong model or runtime condition;
- incorrect prompt;
- unintended tool or network access;
- contaminated session state;
- service failure;
- truncated or missing output;
- other documented execution failure that prevents the intended test.

A run must not be excluded because:

- the result is surprising;
- the result weakens the working hypothesis;
- Baseline performs better;
- M-Anchor performs worse;
- the output is difficult to interpret;
- the output is scoring-ambiguous under the frozen rule.

Every excluded run must be recorded with its exclusion reason.

If a replacement run is performed, the excluded run remains in the record.

An accepted but scoring-ambiguous run remains part of the evaluation record
and must not be silently discarded.

## 11. Closure rule

Once any scored output has been observed for an evaluation version, that
version is closed with respect to:

- prompt wording;
- expected epistemic state;
- primary scoring rule;
- runtime conditions;
- run count, except where a pre-specified rule permits continuation;
- aggregation rule.

Do not strengthen a closed prompt after observing its outcome.

If a design flaw is discovered, record the flaw and create a new evaluation ID
or version.

The original result remains part of the record.

A new version may test a corrected design, but it must not replace or erase the
closed version.

## 12. Blinding

Where practical, human scoring should be performed without revealing which
runtime condition produced the response.

If blinding is not used, report that fact.

Blinding is intended to reduce evaluator preference effects; it does not make
the scoring rule itself valid.

If adjudication is required for an ambiguous output, the adjudication procedure
should also be specified in advance where practical.

## 13. Controls and alternative explanations

Where practical, evaluations should include controls capable of distinguishing
the proposed mechanism from simpler alternatives.

Examples include:

- evidence-sufficient controls;
- generic-caution controls;
- instruction ablations;
- interface-only controls;
- matched cases without completion pressure.

A control should target a specific alternative explanation rather than merely
increase the number of conditions.

## 14. Reporting

For every completed evaluation, preserve:

- frozen evaluation specification;
- protocol-freeze commit or fixed repository reference;
- accepted outputs;
- excluded outputs and reasons;
- scoring-ambiguous outputs;
- model/runtime metadata;
- execution date or time;
- scores;
- run-level results;
- aggregate results, if applicable;
- aggregation rule;
- secondary annotations;
- deviations from protocol;
- null results;
- failures of M-Anchor conditions;
- failures of Baseline conditions.

Reports must distinguish observation from interpretation.

Results should not be generalized beyond the tested model, runtime,
evaluation family, and conditions without additional evidence.

Where relevant platform parameters are unavailable or hidden, reports should
state that limitation rather than imply full reproducibility.

## 15. Interpretation limits

A behavioral difference in one evaluation family does not establish:

- general superiority of M-Anchor;
- a general theory of model reasoning;
- an internal belief or mental state;
- real-world accident prevalence;
- transfer to untested models or interfaces.

A null result does not by itself establish that the framework is useless.

A positive result does not by itself establish that the framework is generally
effective.

A Baseline advantage is not evidence that the evaluation failed.

An M-Anchor failure is not to be removed merely because it conflicts with the
working hypothesis.

The appropriate claim is the smallest claim supported by the completed
evaluation set.

## 16. Versioning and amendments

This procedure is versioned independently from individual evaluations.

After v0.1 is frozen, substantive methodological changes require a new version
rather than silent modification.

Editorial corrections that do not change evaluation behavior may be made if
clearly identified.

New procedure versions do not retroactively rescore closed evaluations unless
a separate re-analysis is explicitly labeled as such.
