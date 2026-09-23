# Separate Review Note

**Purpose:** Identify claims in the proposed PSC / IESC reframing that are stronger than, or not yet established by, the existing M-Anchor documents.

This note is intentionally separate from the report body.

## 1. “Premature Semantic Closure” is a new organizing label

The existing repository already defines closely related concepts:

- Forced Closure / State Collapse
- Drift / Contamination
- Unsupported Expansion
- Semantic Filling
- epistemic promotion
- assessment–representation mismatch

However, **Premature Semantic Closure** is not presently a canonical M-Anchor term.

Using it as a research-level umbrella is reasonably compatible with v0.2-rc1, provided it does not silently replace the existing five-mode taxonomy.

In particular, it should not make Forced Closure, Drift, and Unsupported Expansion indistinguishable.

**Recommended status:** candidate research construct, not canonical failure mode.

---

## 2. “Irreversible Epistemic State Collapse” is materially stronger than the existing evidence

The repository establishes that an epistemic distinction can be lost at a representation boundary.

It does **not** yet experimentally establish irreversible downstream propagation.

`non-closure-under-forced-completion.md` explicitly identifies the next empirical step as attaching a consumer that can see only the discrete token.

Therefore:

> assessment `unresolved` → serialized `B`

has been observed,

but:

> serialized `B` → downstream system irreversibly inherits `B` as fact

has not.

The word **irreversible** should therefore be restricted to a workflow-relative information-loss definition:

> the earlier distinction cannot be reconstructed from the retained downstream artifact alone.

Any stronger claim about permanent system state, long-context contamination, or real-world irreversibility would currently exceed the evidence.

---

## 3. Summary compression is not an observed cause of closure

The proposed architecture treats summary compression as a candidate transition pressure.

That is conceptually consistent with v0.2/rc1, which lists summary compression as a possible source of Drift.

But the actual PD-01 experiment produced a **null result**, including under final two-sentence summary compression.

It would therefore be semantic drift to write that the repository has shown summary compression to cause state collapse.

Current support is only:

> summary compression is a plausible future test family.

---

## 4. Structured-output collapse has not yet been tested

The extension from forced binary output to JSON schemas, classifiers, APIs, or other structured interfaces is structurally plausible and is contemplated by the v0.2 documents.

The current experimental record nevertheless centers on a forced A/B epistemic interface.

Claims that structured outputs generally create PSC would exceed the present evidence.

They should remain prospective hypotheses.

---

## 5. Action pressure must not be merged with epistemic closure

v0.2-rc1 explicitly corrected this distinction.

A required decision bit may be legitimate while the underlying factual assessment remains unresolved.

For example:

```text
cause = unresolved
decision = evacuate
```

is not automatically State Collapse.

Any PSC/IESC formulation that treats every forced action as epistemic collapse would regress from the v0.2-rc1 distinction between epistemic bits and decision bits.

This is the highest-risk semantic drift in the new framing.

---

## 6. M-Anchor as an “architecture” is consistent with v0.2-rc1 but broader than canonical v0.1

Canonical v0.1 is still primarily a human-impact normative framework.

The Assessment / Representation / Action architecture is developed in the non-canonical v0.2 draft and v0.2-rc1.

Therefore the report may reasonably describe M-Anchor as a **candidate mitigation architecture**, but it should not imply that canonical v0.1 had already established this full general architecture.

The historical sequence should remain visible:

```text
v0.1 human-impact framework
→ pilot observations
→ representation-boundary problem
→ v0.2 generalization
→ v0.2-rc1 corrections
→ PSC / IESC research reframing
```

---

## 7. FC-01 cannot support a general M-Anchor advantage

FC-01 should remain a **post hoc exploratory stress test**.

ZA-01 adds a useful exploratory ablation:

```text
Baseline                 FAIL / PASS
Generic Caution          FAIL / PASS
Non-Closure Minimal      PASS / PASS
M-Anchor Minimal         PASS / PASS
```

This supports a narrow mechanism hypothesis concerning explicit non-closure permission in that pair.

It does not establish:

- general M-Anchor superiority;
- general Baseline vulnerability;
- prevalence of forced closure;
- transfer across models;
- transfer across structured interfaces;
- prevention of real-world AI incidents.

The main draft above preserves this limitation.

---

## 8. Current null results constrain the structural hypothesis

The following must continue to be presented as actual results, not as preliminary failures to find the “right” stress test:

```text
Three-pair pilot:          null discrimination
Conversational stress:    null discrimination
PD-01:                     null discrimination
IF-01:                     null discrimination
```

A future PSC program may generate new tests, but these closed tests must not be retroactively strengthened or reinterpreted as positive evidence.

This follows directly from the General Evaluation Procedure.

---

## 9. The General Evaluation Procedure is not yet frozen

`evals/general-evaluation-procedure-v0.1.md` remains:

> Draft — not yet frozen

Accordingly, a future PSC / IESC series should not be described as prospective under that procedure until the protocol has been reviewed, frozen, and committed before scored runs.

The current report can define the research program without claiming that prospective validation has begun.

---

## 10. “Without an evidential update” needs one technical qualification

The central research question is appropriately phrased around absence of an evidential update.

However, v0.2-rc1 recognizes other legitimate transition bases.

A state or decision may properly change because of:

- a valid rule or policy;
- a certified procedure that itself generates evidence;
- an explicitly declared conditional assumption;
- a loss function;
- authority;
- necessity;
- urgency.

These must not be misclassified as PSC merely because the raw factual evidence did not change.

For evaluation purposes, the intended target should therefore be understood as:

> stronger epistemic commitment without new evidence **or another independently justified basis for that epistemic promotion**.

Decision changes should be scored separately.

---

## 11. Repository source-integrity note

`operational-specs/case-02-implementation-baseline-1.md` currently appears to terminate inside the `Two-Track Processing` text diagram, followed immediately by several headings.

The earlier sections are readable and support the strong-conclusion / protective-action distinction used in the report, but material after that truncation should not be treated as a complete operational specification until the file is checked separately.

This is a repository-integrity observation, not a semantic claim about M-Anchor.

---

## Overall assessment

The proposed reframing is broadly consistent with the direction already taken by `core-principles-v0.2-rc1.md` and the completion-pressure reports.

The safest formulation is:

> **PSC is a candidate cross-boundary failure hypothesis. IESC is a candidate downstream information-loss condition. M-Anchor is a candidate mitigation architecture for preserving justified state distinctions and transition traceability.**

The existing repository does **not** yet justify:

> PSC / IESC is a demonstrated general structural cause of AI abnormal behavior, or M-Anchor is a validated general solution.

That stronger formulation should remain outside the current report.
