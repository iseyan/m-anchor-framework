# Addendum — Independent Convergence with Milad Farazian's Structured-Output Abstention Study

**Status:** Comparative addendum — external independent work  
**Date:** 2026-09-24  
**Repository:** `iseyan/m-anchor-framework`  
**Scope:** Comparison between M-Anchor / the 1-bit representation problem and Milad Farazian's structured-output abstention study  
**External work status:** Farazian describes the study as completed and pre-registered, with analysis finished and a paper drafted, but not yet peer-reviewed at the time of this addendum.

---

## 1. Why this comparison matters

The M-Anchor evaluation program independently arrived at a structural concern:

> A richer epistemic state cannot be losslessly represented by a narrower downstream state space.

The minimal form used in the current work is:

```text
Epistemic state:
{A, B, unresolved}

Downstream binary field:
{A, B}
```

If the downstream representation retains only the binary field, the third epistemic state cannot be preserved in that field itself.

A natural-language qualification can preserve additional information only if the qualification survives the handoff and is consumed downstream.

This is the basis of the shorthand:

> **Language does not split the bit.**

Milad Farazian's independently developed structured-output abstention study approaches a closely related boundary from a different direction: instead of beginning with a structural state-space argument, it experimentally varies the **shape of the output interface** and measures whether models continue to abstain on questions that should not be answered.

The proximity is therefore methodologically interesting.

The two projects did not begin from the same framework, terminology, or experimental path.

---

## 2. Farazian's research question

Farazian's study asks, in effect:

> If a model can abstain in free-form text, what happens when a structured-output schema requires an answer field?

According to the public study description, the experiment was pre-registered before the headline data collection and used:

- 600 items;
- 300 epistemically unanswerable questions;
- 300 matched answerable controls;
- five output conditions;
- API-native strict structured-output conditions;
- multiple model families;
- 12,000 graded responses;
- multiple independent judges.

The five output conditions were described as:

```text
1. Free-form text
2. Prompted JSON without enforcement
3. API-native strict schema with a required answer
4. Strict schema with nullable answer + status enum
5. The same escape-hatch schema with status ordered first
```

The reported central result was that a required-answer schema sharply reduced abstention across the tested models.

Adding an explicit abstention affordance restored much of the behavior, but did not fully restore free-form abstention parity in most tested cases.

Farazian summarizes the engineering lesson as a warning that a required answer field can suppress a model's willingness or ability to say that it does not know.

### Public source

- Milad Farazian, **"When Models Won't Say 'I Don't Know'"**  
  https://farazian.com/work/schema-abstention/

---

## 3. The M-Anchor / 1-bit route

The M-Anchor route was different.

It began with a framework concerned with preserving distinctions among:

- established facts;
- supported inference;
- speculation;
- unknown or unresolved states;
- safety/action urgency;
- representation and downstream action.

During exploratory forced-completion evaluation, FC-01 produced an unusual observable divergence:

```text
Assessment:
unresolved

Interface submission:
B
```

The Baseline explicitly stated that the evidence did not support the binary causal conclusion, yet still emitted the required binary value.

Later tests mostly produced null results:

- strong Baselines often refused the lossy A/B mapping instead;
- downstream consumers given only the collapsed value did not automatically promote it into an evidence-supported fact;
- explicit metadata preserved the unresolved state correctly;
- no general M-Anchor advantage was observed across the broader pilot set.

This led to a narrower structural formulation:

```text
L1 — structural:
A richer epistemic state cannot be losslessly represented
in a narrower binary field.

L2 — empirical:
How does the model resolve the mismatch?

L3a — structural:
If provenance is discarded, it cannot be recovered
from the binary value alone.

L3b — empirical:
Does a downstream model promote the retained value
into an evidence-supported finding?
```

---

## 4. Core similarity

The strongest point of convergence is not "abstention" in the abstract.

It is the recognition that **output shape can change epistemic behavior**.

Farazian:

```text
Unanswerable question
        ↓
Output schema changes
        ↓
Abstention behavior changes
```

M-Anchor / 1-bit framing:

```text
Richer epistemic state
        ↓
Narrower representational boundary
        ↓
Some distinction may be lost,
refused, or re-encoded
```

Both lines reject the assumption that the model's final field value can be treated as a transparent readout of a stable epistemic state independent of the interface.

That is the main commonality.

---

## 5. Independent convergence

The convergence is notable because the paths are substantially different.

### Farazian's route

The public record suggests an engineering-first trajectory:

```text
production LLM systems
→ evaluation harnesses
→ groundedness / hallucination checks
→ structured-output abstention experiment
```

Farazian's separate project **Honest** is explicitly framed as an evaluation layer for catching hallucinations, unsupported claims, and guardrail failures before an answer reaches the user.

Public source:

- Milad Farazian, **"Honest"**  
  https://farazian.com/work/honest/

His earlier controllable-generation work also describes a recurring concern with changing one dimension of model output while preserving another.

Public source:

- Milad Farazian et al., **"Emotion Translation with Transformers"**  
  https://farazian.com/work/emotion-translation/

### M-Anchor route

The M-Anchor route was closer to:

```text
external behavioral observation
→ proposition-level epistemic distinctions
→ runtime non-closure rules
→ forced-completion anomaly
→ representation-boundary formulation
```

The proximity therefore appears to be an **independent convergence on a boundary problem**, not a shared derivation.

This addendum makes no claim of priority over Farazian's work and no claim that Farazian derived his study from M-Anchor.

---

## 6. Where Farazian is empirically stronger

Farazian's study is substantially stronger than the current M-Anchor record in several empirical respects.

### Scale

The study uses hundreds of items and thousands of responses rather than a small exploratory prompt set.

### Prospective discipline

The hypotheses, arms, exclusions, and analysis plan were pre-registered before the main collection.

### Direct manipulation of the representation layer

The experiment changes the actual output schema rather than relying only on natural-language pressure.

This is particularly important for the 1-bit framing.

FC-01 still allowed natural-language qualification around the binary answer.

A strict API-native schema can more directly constrain what downstream software receives.

### Matched answerable controls

The study includes answerable controls, making it possible to distinguish useful abstention from indiscriminate refusal.

These properties make Farazian's work strong external evidence that representation constraints can materially alter abstention behavior.

---

## 7. Where M-Anchor asks a different question

The two projects should not be collapsed into one.

Farazian primarily measures:

```text
Does the model answer or abstain
under different output schemas?
```

M-Anchor additionally separates:

```text
Assessment
Representation
Provenance / inherited state
Decision
Action
```

This distinction matters.

A model can have:

```text
Assessment = unresolved
Decision = evacuate
```

without contradiction.

M-Anchor therefore distinguishes an **epistemic bit** from a **decision bit**.

A binary operational decision is not automatically epistemic collapse.

Similarly, the M-Anchor L3 exploratory test asks a question outside the main scope of Farazian's published study description:

> Once a lossy interface value has been retained, how does a separate downstream consumer interpret it?

The M-Anchor downstream test was very small and produced a null result for semantic promotion, but it extends the conceptual boundary beyond the first output schema.

---

## 8. The important partial mismatch

The Farazian study does not directly show:

```text
Assessment = unresolved
Interface = B
```

inside the same observed response.

A change from free-form abstention to strict-schema answering admits several possible explanations:

```text
1. The assessment remained unresolved,
   but the representation layer forced an answer.

2. The schema changed the model's expressed assessment itself.

3. The schema altered the overall generation policy
   in a way that does not cleanly decompose into
   assessment and representation.
```

Farazian's public study description does not need to resolve this distinction for its own research question.

FC-01 is interesting because it made the first pattern directly observable in one case:

```text
the model said the claim was unresolved
and nevertheless submitted the forced value.
```

This is one reason FC-01 remains valuable despite its small scale and exploratory status.

---

## 9. Escape hatches and M-Anchor Minimal

A particularly interesting point of contact is Farazian's escape-hatch result.

If the problem were only:

```text
the schema lacks an unresolved state
```

then adding an explicit `null` or `status = abstain` state might be expected to solve the problem completely.

According to Farazian's reported results, it did not.

Explicit abstention affordances recovered much of the lost abstention behavior, but full parity with free-form behavior was not restored in most cases.

This suggests a useful distinction:

```text
Representation affordance
        ≠
Behavioral use of that affordance
```

M-Anchor Minimal addresses the second side as well as the first.

Its non-closure logic includes ideas such as:

- do not force an answer where evidence does not support one;
- leave genuinely unresolved states unresolved;
- do not treat absence of closure as a defect;
- do not add explanation, certainty, motive, or structure merely to fill empty space;
- when a conclusion is supported, state it clearly;
- do not suppress justified inference.

The possible connection is therefore:

```text
Farazian:
Give the interface an escape hatch.

M-Anchor:
Also normalize the use of non-closure
as a valid runtime terminal state.
```

This is a research hypothesis, not an established comparative result.

The existing M-Anchor pilots often showed no incremental advantage over a strong Baseline.

---

## 10. Why the convergence strengthens the research framing but not the claims

Farazian's work increases confidence that the broad research **question** is real and independently interesting:

> Can representational constraints alter the expression of epistemic uncertainty?

It does not validate the full M-Anchor framework.

It does not prove that FC-01 and schema-induced abstention collapse share an identical internal mechanism.

It does not show that M-Anchor is the best mitigation.

It does not establish that the 1-bit formulation is the unique or complete explanation of Farazian's findings.

The strongest defensible relationship is:

> **Farazian provides independent large-scale empirical evidence that output-schema constraints can suppress abstention. M-Anchor independently frames a related problem as preservation of richer epistemic states across narrower representation boundaries.**

That is substantial convergence without claiming equivalence.

---

## 11. Relation to the testing stop rule

This independent work also changes the value of additional adversarial testing inside the M-Anchor project.

The project has already adopted a stop rule against further failure-induction prompt optimization because repeated attempts to discover narrow boundary failures could become difficult to distinguish from jailbreak-style adversarial search.

Farazian's study reduces the need to reopen that line.

The externally published evidence already provides a much larger and more systematic demonstration that output structure can alter abstention behavior.

Therefore the M-Anchor project can remain focused on:

- formalizing the representation-capacity problem;
- separating assessment, representation, provenance, decision, and action;
- analyzing existing positive and null results;
- designing defensive state-preserving interfaces;
- preserving ethical and methodological stopping rules.

There is no need to manufacture additional FC-01 analogues merely to show that interface shape can matter.

---

## 12. Comparative summary

| Dimension | Farazian structured-output study | M-Anchor / 1-bit work |
|---|---|---|
| Primary origin | production/evaluation engineering | external behavioral observation and epistemic framework |
| Central question | does strict schema suppress abstention? | what happens when richer epistemic state meets narrower representation? |
| Main object | structured output schema | assessment → representation → provenance → decision/action |
| Core state contrast | answer vs abstain | A / B / unresolved, plus provenance and action separation |
| Method | pre-registered large-scale empirical study | small exploratory behavioral studies + structural analysis |
| Strongest evidence | schema-dependent abstention collapse | FC-01 assessment/interface divergence + null controls |
| Escape mechanism | nullable answer + status enum | explicit non-closure + state separation + metadata |
| Downstream inheritance | not the main published test | small L3 exploratory test |
| General superiority claim | none required | explicitly not established |
| Current limitation | not yet peer-reviewed | exploratory scale; many null results |

---

## 13. Current interpretation

The most useful combined picture is:

```text
Structural layer
───────────────
A richer epistemic state cannot be losslessly encoded
in a narrower retained state space.

        ↓

Farazian
────────
Large-scale evidence that narrowing the output schema
can sharply suppress abstention.

        ↓

FC-01
─────
One exploratory case where the model visibly retained
the unresolved assessment while submitting a binary value.

        ↓

M-Anchor
────────
Candidate runtime and representation architecture
for preserving justified distinctions without suppressing
justified conclusions.

        ↓

Stop rule
─────────
Do not escalate into adversarial failure-induction search
merely to manufacture more positive cases.
```

The similarity between Farazian's study and the M-Anchor / 1-bit line is therefore real and worth preserving in the research record.

The most important shared insight is not that models should simply "refuse more."

It is:

> **The representational contract imposed on a model is part of the epistemic system.**

A model cannot reliably preserve distinctions that the interface does not retain, and merely adding an escape state may not guarantee that the model will use it.

That is the point of independent convergence.

---

## 14. External references

1. Milad Farazian, **"When Models Won't Say 'I Don't Know'"**  
   https://farazian.com/work/schema-abstention/

2. Milad Farazian, **"Honest"**  
   https://farazian.com/work/honest/

3. Milad Farazian et al., **"Emotion Translation with Transformers"**  
   https://farazian.com/work/emotion-translation/

---

## 15. Claim discipline

This addendum should not be cited as establishing that:

- Farazian and M-Anchor discovered the same mechanism;
- Farazian's work validates M-Anchor;
- M-Anchor anticipated Farazian's empirical result;
- FC-01 explains Farazian's abstention collapse;
- the 1-bit problem is the sole cause of structured-output hallucination.

It may be cited as documenting:

> **an independently reached, technically adjacent result in which output-state constraints materially affect epistemic behavior, closely matching the representation-boundary problem independently identified in the M-Anchor evaluation program.**
