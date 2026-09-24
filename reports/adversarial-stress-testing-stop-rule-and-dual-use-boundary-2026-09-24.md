# Addendum — Stop Rule for Adversarial Stress Testing and Dual-Use Boundary

**Status:** Major methodological and ethical addendum  
**Date:** 2026-09-24  
**Repository:** `iseyan/m-anchor-framework`  
**Applies to:** FC-01-related forced-closure work, L2/L3 boundary testing, and future adversarial stress-test design  
**Effect:** Further adversarial prompt-construction work in this line is suspended. Existing results remain unchanged and are retained as historical evidence.

---

## 1. Reason for this addendum

The current evaluation sequence began as an attempt to determine whether M-Anchor-derived runtime constraints produce observable differences relative to a strong Baseline.

Most ordinary and conversational stress tests produced null results. A narrow forced-completion case, FC-01, produced an unusual assessment–interface divergence:

```text
Assessment = unresolved
Interface submission = B
```

Later tests showed that strong current Baselines often avoid the same mismatch by refusing the lossy binary submission, and that downstream systems did not automatically promote a collapsed binary record into an evidence-supported fact.

These later null results are important and are retained.

However, the work also exposed a methodological boundary.

To continue searching for additional cases resembling FC-01, the evaluator would increasingly need to design prompts whose purpose is to locate narrow conditions under which an otherwise well-calibrated model crosses a behavioral boundary despite retaining a more appropriate assessment.

At that point, adversarial evaluation and jailbreak-style prompt construction can become externally difficult to distinguish.

This creates both an ethical concern and a methodological confound.

---

## 2. The dual-use problem

The research question is legitimate:

> Under what conditions can a system with an appropriate epistemic assessment nevertheless emit a representation inconsistent with that assessment?

But a search procedure optimized to make such failures occur can gradually become:

> Find prompt structures that cause a capable model to violate its normal boundary-preserving behavior.

Those two activities may be conceptually distinguishable by intent, but the resulting prompt artifacts may be operationally similar.

This is especially relevant when the search process involves:

- repeated adversarial reformulation;
- attempts to increase failure frequency;
- systematic exploration of instruction-order effects;
- pressure to override a model's own stated assessment;
- construction of prompts intended to bypass refusal or non-closure behavior;
- transfer testing across providers in order to locate a more vulnerable runtime condition.

Such work can produce artifacts with dual-use value even if the original research purpose is epistemic evaluation.

---

## 3. No claim of mechanism identity

This addendum does **not** claim that FC-01, prompt injection, and jailbreaks share the same internal mechanism.

That has not been established.

The current evidence supports only a weaker observation:

> FC-01 and some adversarial prompting techniques can share an external structural feature: a normally functioning model is placed under competing or sequential constraints, and the final observable output may depart from a better-supported internal or explicitly stated assessment.

This external similarity is sufficient to justify a stop rule.

An internal-mechanism claim would require evidence that the current project does not have and should not seek through increasingly adversarial prompt construction.

---

## 4. Stop rule

Effective with this addendum, this research line will not proceed by designing new prompts whose primary purpose is to increase the probability of forced-closure failure or to discover new failure-inducing instruction sequences.

Specifically, the project will not continue with:

- iterative jailbreak-like prompt refinement;
- systematic search for wording that defeats refusal behavior;
- optimization of FC-01-like prompts for higher failure rates;
- adversarial cross-provider transfer testing intended to identify weaker systems;
- construction of action-leakage scenarios whose purpose is to force downstream misuse;
- automated mutation or large-scale search over prompt variants designed to elicit boundary violations.

Existing tests are not deleted or reinterpreted.

The stop rule is prospective.

---

## 5. Why stopping is methodologically justified

Stopping is not based on a positive finding of a general vulnerability.

The opposite is true.

Most tested conditions produced null differences, and strong Baselines frequently preserved the relevant epistemic boundary without M-Anchor assistance.

That means further progress would increasingly depend on designing more artificial or adversarial prompts to force a rare failure.

Such a procedure would create two problems.

### 5.1 Construct contamination

If a test is repeatedly modified until the target failure appears, the experiment stops measuring a naturally occurring boundary condition and begins measuring the evaluator's ability to manufacture one.

A positive result would then be difficult to interpret.

### 5.2 Dual-use convergence

The same iterative process could generate prompt patterns useful for bypassing normal model safeguards or boundary-preserving behavior.

The distinction between stress testing and jailbreak construction would then depend too heavily on stated intent rather than on the artifact produced.

For this project, that tradeoff is not justified.

---

## 6. Status of FC-01 after the stop rule

FC-01 should be preserved as a narrow exploratory observation.

Its importance is not that it demonstrated a general AI weakness.

Its importance is that it captured an unusual case in which:

- the model retained the correct unresolved assessment;
- the model recognized that the forced binary value was not evidence-supported;
- yet the model still emitted the binary value.

Later tests suggest that current high-capability Baselines often avoid this pattern.

Therefore, the most defensible interpretation is:

> FC-01 may have captured a residual representation-boundary failure that is uncommon and condition-dependent.

The project will not attempt to manufacture additional FC-01 analogues merely to increase the number of positive examples.

---

## 7. What remains legitimate to study

The stop rule does not prohibit non-adversarial work.

The following remain within scope:

### Formal analysis

- precise formulation of L1;
- state-space and information-loss analysis;
- distinction between epistemic bit and decision bit;
- representation-capacity analysis;
- provenance-preservation requirements.

### Analysis of already collected data

- re-reading existing FC-01, ZA-01, PD-01, IF-01, L2, and L3 records;
- comparing positive and null results without rescoring closed tests;
- identifying what the existing evidence does and does not support.

### Defensive architecture

- designing representations that explicitly preserve `unresolved`;
- separating assessment, interface submission, provenance, and action;
- testing benign schema designs that do not require boundary violation;
- documenting how to avoid lossy handoff.

### Methodological work

- freezing evaluation procedures;
- defining stopping rules;
- documenting dual-use boundaries;
- clarifying what future work would require independent ethical review.

---

## 8. Consequence for M-Anchor claims

This stop rule increases the importance of claim discipline.

The project should not claim:

- that FC-01 reveals the general cause of AI abnormal behavior;
- that forced closure is common;
- that jailbreaks are caused by the same mechanism;
- that M-Anchor is a validated jailbreak defense;
- that more adversarial testing would probably confirm the hypothesis.

The project may state:

> A structural representation mismatch exists when a richer epistemic state is compressed into a narrower interface.

It may also state:

> FC-01 captured one exploratory case in which that mismatch became behaviorally visible as assessment–interface divergence.

And:

> Later tests showed that strong Baselines often avoid the same failure, and that downstream semantic promotion did not automatically occur.

These statements preserve both the positive observation and the null results.

---

## 9. Ethical interpretation

The central ethical concern is not that the current work successfully produced a jailbreak.

It did not.

The concern is that a continued search for increasingly effective failure-inducing prompts could become operationally similar to jailbreak research even if the stated purpose remained evaluative.

The absence of success does not remove that concern.

Indeed, repeated failure could itself create pressure to make the prompts more adversarial.

For this reason, the project adopts a conservative research stop rule before such optimization begins.

---

## 10. Final position

The current evaluation record is sufficient to support a bounded research claim:

```text
L1:
A richer epistemic state cannot be losslessly represented
in a narrower binary field.

L2:
AI systems can resolve that mismatch in different ways.
FC-01 captured one unusual lossy-submission case;
later tests often produced refusal instead.

L3a:
If provenance is discarded, it cannot be recovered
from the binary value alone.

L3b:
Downstream semantic promotion was not observed
in the current exploratory test.
```

Further adversarial search is not necessary to preserve these findings.

The project therefore stops active failure-induction testing at this point.

Future work should emphasize formalization, defensive representation design, archival analysis of existing results, and explicit preservation of unresolved epistemic state rather than further attempts to trigger boundary failures.
