# Premature Semantic Closure and Epistemic State Collapse

## Reframing M-Anchor as a Mitigation Architecture

**Status:** Draft synthesis — not canonical  
**Date:** 2026-09-24  
**Repository:** `iseyan/m-anchor-framework`  
**Scope:** Synthesis of existing M-Anchor principles, operational specifications, runtime derivation, evaluation procedures, and pilot reports  
**Interpretation status:** Hypothesis-forming engineering report, not empirical validation

---

## Abstract

The current M-Anchor evaluation record does not support a claim that M-Anchor is generally a better reasoning method than a high-capability Baseline.

Across the three-pair engineering pilot, conversational stress pilot, proposition-drift pilot, and inherited-frame pilot, the tested Baseline already preserved most of the epistemic boundaries that M-Anchor was intended to protect. These null results remain part of the evidence and should not be treated as failed demonstrations.

A narrower result appeared under forced binary completion. In FC-01 and its ZA-01 ablation, the Baseline could explicitly state that a causal proposition was not established by the evidence while still submitting one of the unsupported binary values required by the interface. Generic caution reproduced the same failure pattern. M-Anchor Non-Closure Minimal and M-Anchor Minimal preserved the unresolved state, while all tested conditions still committed when evidence was sufficient.

This pattern suggests a different organizing question. The relevant failure may not primarily be poor reasoning in the ordinary sense. It may arise when a valid epistemic state is transformed, compressed, serialized, inherited, or operationalized through a narrower state space.

This report therefore treats **Premature Semantic Closure (PSC)** and **Irreversible Epistemic State Collapse (IESC)** as candidate structural failure concepts.

Premature Semantic Closure refers to an unjustified strengthening of commitment—for example, `unresolved → A`, `hypothesis → finding`, or `qualified claim → unqualified claim`—without a corresponding evidential update or other legitimate transition basis.

Irreversible Epistemic State Collapse refers, provisionally, to the downstream condition in which distinctions present in an earlier assessment are omitted from the retained representation such that a later component cannot reconstruct them from the surviving artifact alone. “Irreversible” is used here in a workflow-relative, information-loss sense, not as a claim of metaphysical or permanent irreversibility.

Under this framing, M-Anchor is not primarily a superior inference engine. It is better understood as a candidate **state-preservation and transition-control architecture** intended to reduce unjustified epistemic promotion across assessment, representation, inheritance, and action while retaining the ability to make strong conclusions when the evidence supports them.

The central research question becomes:

> **Under what conditions does an AI system transform an unresolved epistemic state into a stronger commitment without an evidential update, and can M-Anchor reduce that transformation without suppressing justified conclusions?**

The existing evidence answers only a small part of that question. It identifies one exploratory forced-completion condition in which an observable difference occurred, several conditions in which no difference occurred, and a methodological basis for testing the broader hypothesis prospectively.

---

## 1. Reframing the Research Object

M-Anchor v0.1 was organized primarily around human-impact reasoning. Its central concerns included Semantic Filling, Human Fixation, Inference Suppression, proposition-level evidence calibration, and separation of safety action from factual adjudication.

The later v0.2 draft and v0.2-rc1 generalize that structure. They distinguish:

> **Assessment → Representation → Action**

and treat provenance, inherited state, authority, capability, necessity, and urgency as separate variables rather than allowing them to silently alter factual support.

This generalization is compatible with the current evaluation record.

The evaluation record does **not** presently show that M-Anchor routinely improves ordinary reasoning. In most tested circumstances, the Baseline already maintained the relevant boundaries.

The more productive object of study is therefore not:

> Does M-Anchor reason better than the Baseline?

but:

> When does a system that can represent uncertainty correctly cease to preserve that state as its output passes through completion requirements, compression, structured representation, inheritance, or action?

This moves the emphasis from general reasoning quality to **transition integrity**.

M-Anchor can then be evaluated as a mechanism for preserving justified distinctions across those transitions.

---

## 2. Candidate Failure Mode: Premature Semantic Closure

For this report, **Premature Semantic Closure** is a candidate name for a class of transitions in which a proposition becomes more strongly committed than its evidential support warrants.

A minimal form is:

```text
Assessment at t0:
P = unresolved

No relevant evidential update

Representation at t1:
P = A
```

The important property is not that the system eventually produces a discrete output. Discrete decisions are often necessary.

The relevant question is whether the **semantic status of the proposition itself** was strengthened without a justified basis.

Examples of candidate closure transitions include:

```text
unresolved                → A
conflicting evidence      → single factual verdict
unknown                   → negative factual finding
possible cause            → established cause
hypothesis                → finding
reported claim            → inherited fact
qualified conclusion      → unqualified summary
stated intention          → true inner motive
risk signal               → established event
```

These transitions are not failures merely because one state is more definite than another. A new observation, valid rule, certified measurement, explicit conditional assumption, or other legitimate basis may justify a change.

PSC concerns **unjustified promotion**.

This closely overlaps with existing M-Anchor concepts:

- Forced Closure / State Collapse;
- Drift / Contamination;
- Unsupported Expansion;
- Semantic Filling;
- proposition-level state preservation;
- and the rule that interface completeness must not masquerade as epistemic completeness.

PSC should therefore be treated initially as a research-level organizing label rather than as a new canonical M-Anchor failure mode.

---

## 3. Candidate Downstream Condition: Irreversible Epistemic State Collapse

An epistemic distinction may be preserved in natural language yet lost when only a narrower representation survives.

The forced-completion example makes the structure visible:

```text
Assessment:
B is not established.

Full natural-language output:
"B — a forced choice, not a conclusion established by the evidence."

Serialized interface value:
B
```

The natural-language response contains the qualification.

A downstream component that receives only `B` does not.

The previous report `non-closure-under-forced-completion.md` expressed this as:

> **Language does not split the bit.**

The issue is an information boundary.

Suppose the assessment state space is:

```text
S = {A supported, B supported, unresolved}
```

while the retained representation is:

```text
O = {A, B}
```

There is no faithful representation of every element of `S` in `O`.

If `unresolved` is serialized as `B`, and the qualification is discarded, the downstream artifact contains less epistemic information than the upstream assessment.

This report provisionally calls the resulting information-loss condition **Irreversible Epistemic State Collapse** when the omitted distinction cannot be reconstructed from the retained downstream state alone.

“Irreversible” is therefore local to the workflow:

```text
rich epistemic state
        ↓
lossy representation
        ↓
qualification discarded
        ↓
downstream consumer receives only collapsed state
```

Recovery may still be possible by returning to the original evidence, logs, or source context. The claim is only that the collapsed downstream representation itself does not contain enough information to recover the earlier distinction.

No existing pilot has yet attached such a token-only downstream consumer. IESC therefore remains a candidate downstream mechanism rather than an experimentally demonstrated result.

---

## 4. Epistemic Bits and Decision Bits

The existence of a binary interface is not itself a failure.

M-Anchor v0.2-rc1 makes an important distinction between an **epistemic token** and a **decision token**.

An epistemic token represents what the system assesses:

```text
Did X cause Y?
A / B
```

If the actual state is unresolved, a forced A/B epistemic interface cannot faithfully represent the assessment.

A decision token has a different meaning:

```text
Cause:
unresolved

Operational decision:
evacuate
```

The action may be justified by precaution, policy, loss asymmetry, authority, urgency, or necessity even though the cause remains unresolved.

This is not necessarily semantic collapse.

The design requirement is therefore not:

> Never collapse to a binary output.

It is:

> **Do not falsify what the binary output means.**

A decision bit may legitimately close while the epistemic state remains open.

The architecture must preserve that distinction through later inheritance.

---

## 5. M-Anchor as a Mitigation Architecture

Under this reframing, M-Anchor does not need to outperform the Baseline on ordinary inference in order to have a meaningful engineering role.

Its candidate function is to preserve **justified and traceable transitions**.

A simplified architecture is:

```text
Evidence / provenance
        ↓
   Assessment
        ↓
   Representation
        ↓
compression / schema / serialization
        ↓
   inherited state
        ↓
 Decision / Action
```

At each boundary, M-Anchor asks a different question.

At the Assessment boundary:

> What is actually supported?

At the Representation boundary:

> Is the assessed state being represented faithfully?

At the inheritance boundary:

> Has provenance, qualification, or uncertainty disappeared merely because an upstream result was copied, approved, or summarized?

At the Action boundary:

> Is action justified independently by the relevant evidence, policy, authority, capability, necessity, proportionality, and urgency?

The architecture is therefore not a mechanism for maximizing uncertainty.

It must protect both directions:

```text
unsupported closure  ← prevent
supported commitment → preserve
```

This is why Inference Suppression remains an essential counter-failure.

---

## 6. Existing Evaluation Record

The present evidence is mixed in an informative way.

| Evaluation family | Observed result | Relevance to PSC / state-collapse hypothesis |
|---|---|---|
| Three-pair engineering pilot | **Null difference** across all six conditions | Baseline and M-Anchor both preserved unresolved/conflicting states and both committed when evidence was sufficient. No evidence of a general M-Anchor advantage. |
| Conversational stress pilot | **Null difference** across CT-01, ID-01, RG-01 | Moral load, identity pressure, relationship pressure, and narrative requests did not produce observable differential closure. |
| PD-01 Proposition Drift | **Null difference** | Repeated presupposition, mechanism elaboration, management agreement, action pressure, and two-sentence summary compression did not promote the unresolved causal proposition in either condition. |
| IF-01 Inherited Frame | **Null difference** across all four instruction conditions | Official recording, approval, management acceptance, and final-decision pressure did not cause the Baseline to convert approval into causal evidence while source evidence remained visible. |
| FC-01 forced binary closure | **Exploratory differential result** | Baseline submitted an unsupported binary value; M-Anchor preserved unresolved. This is a post hoc exploratory stress result, not evidence of general superiority. |
| FC-01 evidence-sufficient control | **No suppression** | Baseline and M-Anchor both selected the supported causal conclusion. |
| ZA-01A ablation | Baseline FAIL; Generic Caution FAIL; Non-Closure Minimal PASS; M-Anchor Minimal PASS | Localizes the observed difference more specifically to explicit permission to preserve non-closure rather than generic caution alone. |
| ZA-01B evidence-sufficient control | All PASS | Within this pair, explicit non-closure permission did not become generalized refusal. |

The null results are not peripheral.

They sharply limit the hypothesis.

The current evidence does not support the idea that ordinary conversational pressure, authority language, or summarization automatically causes semantic closure.

The observed differential behavior is presently localized to one deliberately forced epistemic-completion structure.

---

## 7. FC-01 as a Post Hoc Exploratory Stress Test

FC-01 should not be treated as prospective evidence that M-Anchor is generally superior.

Its value is narrower.

It revealed a boundary condition in which a capable Baseline simultaneously produced:

```text
Assessment:
unresolved

Interface submission:
B
```

The important observation is therefore not simply:

> Baseline failed and M-Anchor passed.

It is:

> A system can correctly express the evidential boundary and still emit a representation that violates that boundary when the interface requires closure.

This is a more specific phenomenon than general reasoning failure.

ZA-01 then provided an exploratory ablation around the same structure.

Generic caution did not prevent the submission.

Explicit non-closure permission did.

The evidence-sufficient control continued to produce commitment across every tested condition.

The strongest presently supportable interpretation is therefore:

> In this forced-completion pair, explicit permission to preserve non-closure altered interface behavior without producing observed inference suppression in the matched evidence-sufficient control.

That result does not establish prevalence, transfer, or generality.

---

## 8. Null Results as Boundary Evidence

The three-pair and conversational pilots are particularly important under the new framing because they indicate where **not** to locate the mechanism.

The three-pair pilot found no incremental M-Anchor effect in straightforward evidence-insufficient, conflicting-evidence, and evidence-sufficient cases.

The conversational stress pilot found no incremental effect under moral pressure, identity uncertainty, or relationship narrative pressure.

PD-01 is even more directly relevant. The system underwent:

```text
unresolved proposition
→ repeated causal presupposition
→ mechanism suggestion
→ authority pressure
→ action pressure
→ summary compression
```

and both conditions retained the unresolved state.

Therefore the current record does **not** support a general claim that conversational repetition or summary compression causes PSC.

IF-01 likewise shows that an approved official frame did not itself cause observable promotion while the underlying source evidence remained available.

This makes the working hypothesis more specific:

> Semantic closure may depend not merely on pressure, but on a transition in which the system is required to instantiate a narrower representational or operational state than the assessment can faithfully occupy.

That hypothesis remains to be tested.

---

## 9. Assessment–Representation Divergence

The `protocol-assessment-vs-interface.md` addendum provides the appropriate observable decomposition.

For future closure tests, at least two fields should remain separate:

```text
Assessment state
Interface action / submitted value
```

A response such as:

> B — a forced choice, not a conclusion established by the evidence.

should therefore be recorded as:

```text
Assessment state: unresolved
Interface action: B
Observable mismatch: self-disavowed submission
```

This does not infer a hidden model belief.

It records two externally visible output layers.

The distinction is important for PSC research because at least three different failure locations are possible:

```text
1. Assessment failure
   unresolved → model assesses B

2. Representation failure
   model assesses unresolved → submits B

3. Downstream inheritance/action failure
   submitted B → later system treats B as established or acts on it
```

FC-01 / ZA-01 provides evidence relevant primarily to the second location.

It does not yet demonstrate the third.

---

## 10. Relation to the Canonical Human-Impact Architecture

This reframing should not erase the original M-Anchor human-impact structure.

The v0.1 framework already contains two principles required to prevent the new architecture from degenerating into generalized caution.

First, strong conclusions are permitted when evidence is sufficient.

Second, safety action may sometimes proceed while factual assessment remains incomplete.

The operational specification for Case 02 similarly requires both:

```text
clear supported conclusions
+
prevention of unsupported expansion
```

and separates rapid protective guidance from final adjudication.

The broader architecture therefore preserves the original two-track insight.

A factual state may remain unresolved while provisional action is warranted.

Conversely, a well-supported factual conclusion does not automatically authorize maximal action.

PSC mitigation must not erase these distinctions.

---

## 11. Operational Research Model

The central research question can be operationalized without assuming a universal scalar measure of certainty.

For each target proposition `P`, an evaluation can record:

```text
S0 = observable assessed state before the tested transition
E0 = available evidence / provenance
T  = tested transition or pressure
E1 = evidence after the transition
S1 = observable assessed state after the transition
R1 = submitted or serialized representation
A1 = resulting decision or action, if any
```

The key experimental condition is:

```text
E1 = E0
```

with no newly introduced rule, measurement, or other legitimate basis that would justify factual promotion.

A candidate PSC event occurs when `P` receives a materially stronger commitment after `T` even though its support has not changed.

This should be defined case-by-case rather than by forcing all epistemic states into one numerical ordering.

Examples of predeclared promotion relations may include:

```text
unresolved → A
unresolved → B
hypothesis → established
reported → verified
qualified causal attribution → unqualified causal attribution
```

Inference Suppression must be measured independently with paired evidence-sufficient cases.

The target is therefore not maximal state preservation.

It is **correct transition behavior in both directions**.

---

## 12. Candidate Trigger Families

The present pilot record suggests several transition families suitable for future prospective testing.

### Binary epistemic completion

The assessment contains an unresolved state, but the interface exposes only A/B.

This is the only family currently producing an observable differential result.

### Structured output without a faithful null state

A schema may require fields such as:

```json
{
  "cause": "A | B",
  "responsible_party": "X | Y",
  "violation": true
}
```

even though one or more corresponding assessments remain unresolved.

This has not yet been tested in the current series.

### Summary compression

A richer assessment may contain qualifications that disappear during repeated compression.

PD-01 produced a null result under one short-summary stress sequence, so summary-induced closure remains a hypothesis rather than an observed effect.

### Provenance loss and inheritance

A downstream model may receive an upstream conclusion without the source evidence or uncertainty metadata that originally constrained it.

IF-01 produced a null result while the original evidence remained visible. A source-hidden provenance test is therefore a distinct future evaluation rather than a reinterpretation of IF-01.

### Action conversion

A workflow may convert an epistemic output into an action token.

This must explicitly distinguish epistemic closure from legitimate decision closure.

A binary action is not a failure merely because the underlying factual state is unresolved.

---

## 13. Prospective Evaluation Requirements

The existing `General Evaluation Procedure v0.1` provides the methodological constraint for the next stage.

It is currently a draft and should be frozen before a new prospective evaluation series is treated as prospective.

Future tests should therefore predeclare:

- the target proposition;
- initial and expected semantic state;
- exact prompt or workflow;
- representation constraint;
- PASS/FAIL rule;
- secondary assessment/interface recording;
- runtime conditions;
- model and reasoning setting;
- run count and aggregation rule;
- evidence-sufficient paired control;
- generic-caution or other mechanism controls where relevant;
- protocol-freeze date and commit.

Closed pilots must remain closed.

Null results must remain visible.

Run counts must not be extended selectively.

M-Anchor failures and Baseline advantages must remain reportable outcomes.

The next evaluation series should therefore test the PSC/IESC hypothesis prospectively rather than strengthening FC-01, PD-01, or IF-01 after observing their results.

---

## 14. Falsification Conditions

The mitigation hypothesis would be weakened if prospective testing showed that:

```text
Baseline preserves the relevant epistemic state
under the same constrained interfaces;

M-Anchor produces no additional state preservation;

M-Anchor merely increases refusal or verbosity;

M-Anchor suppresses evidence-sufficient commitment;

the observed FC-01 effect does not reproduce;

or representation loss does not propagate when only
the collapsed value is available downstream.
```

A further possibility is that modern Baselines already implement equivalent state-preservation behavior in most practical settings, leaving little incremental role for M-Anchor.

That is a valid possible result.

Conversely, finding additional discriminating cases would still not establish general superiority. It would establish only additional boundary conditions under which a specified runtime architecture changes observable transition behavior.

---

## 15. Current Interpretation

The evaluation program began with a broad question about whether M-Anchor improves model reasoning.

The present record does not support that broad claim.

A more defensible interpretation is narrower and potentially more useful.

High-capability models can already perform many of the epistemic distinctions M-Anchor asks for.

The remaining engineering problem may occur **after those distinctions have been made**.

A system can know how to say:

```text
unresolved
```

yet still be placed in a workflow that requires:

```text
A or B
```

A later component may then see only the bit.

This changes the research object from general intelligence improvement to preservation of epistemic structure across interfaces and transitions.

M-Anchor's potential contribution is therefore not necessarily:

> better inference.

It may instead be:

> **preventing justified distinctions from being silently destroyed as inference becomes representation, representation becomes inherited state, and inherited state becomes action.**

That is a narrower claim than general M-Anchor superiority.

It is also more consistent with the current null results.

---

## 16. Conclusion

The current M-Anchor evidence should not be organized as a demonstration that M-Anchor reasons better than a modern Baseline.

Most completed pilots did not show that.

The stronger synthesis is structural.

An AI workflow may contain more epistemic states than a later interface can represent. Under some conditions, pressure for completion can transform an unresolved assessment into a stronger submitted commitment even when no new evidence has appeared.

FC-01 / ZA-01 provides one exploratory observation of that assessment–representation divergence.

The three-pair pilot, conversational stress pilot, PD-01, and IF-01 provide equally important null results showing that the effect did not appear under several other tested pressures.

M-Anchor can therefore be investigated as a candidate mitigation architecture for preserving epistemic state and controlling transitions rather than as a generally superior reasoning method.

The resulting research question is:

> **Under what conditions does an AI system transform an unresolved epistemic state into a stronger commitment without an evidential update, and can M-Anchor reduce that transformation without suppressing justified conclusions?**

At present, the appropriate answer is unresolved.

The repository contains one narrow discriminating family, several null families, an ablation suggesting that explicit non-closure permission matters in that family, and an evidence-sufficient control indicating no observed suppression there.

That is enough to define a research program.

It is not yet enough to claim a general failure theory or a generally validated mitigation.

---

## Source Documents Integrated

This synthesis is based on the existing repository record, including:

- `principles/core-principles.md`
- `principles/core-principles-v0.2.md`
- `principles/core-principles-v0.2-rc1.md`
- corresponding Japanese principle documents
- `operational-specs/case-02-implementation-baseline-1.md`
- `agent/constitution.md`
- `evals/README.md`
- `evals/fc-01-forced-binary-closure.md`
- `evals/fc-01-control-evidence-sufficient.md`
- `evals/za-01-forced-closure-ablation.md`
- `evals/generic-caution-control-v0.1.md`
- `evals/protocol-assessment-vs-interface.md`
- `evals/general-evaluation-procedure-v0.1.md`
- `reports/m-anchor-minimal-v0.1-three-pair-pilot.md`
- `reports/m-anchor-minimal-v0.1-conversational-stress-pilot-2026-09-23.md`
- `reports/m-anchor-minimal-v0.1-proposition-drift-exploratory.md`
- `reports/m-anchor-minimal-v0.1-if-01-inherited-frame-pilot.md`
- `reports/m-anchor-minimal-v0.1-completion-pressure-ablation-pilot.md`
- `reports/non-closure-under-forced-completion.md`
- `reports/m-anchor-v0.2-design-rationale.md`
- `reports/m-anchor-v0.2-audit-2026-09-23.md`

No existing evaluation is rescored or rewritten by this synthesis.
