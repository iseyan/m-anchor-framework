# M-Anchor v0.2 Draft Candidate — Internal Audit

**Date:** 2026-09-23  
**Status:** Audit of a draft. Do not canonicalize v0.2 on this note.  
**Do not overwrite:** principles v0.1, constitution v0.1, closed pilots.

## Verdict

The organizing-center shift is justified by the 2026-09 runtime series.

v0.1: constrain unsupported meaning about persons.  
v0.2: constrain unsupported expansion across assessment, representation, inheritance, authority, and action. Human protection becomes a specialization.

Keep that shift. Do not promote the draft.

The draft is internally uneven. The constitution already separates semantic and action terminal states. The core principles do not, in one place that matters.

## Confirmed defects

### 1. Yohaku mixes layers

`core-principles-v0.2.md` §9 lists in one state space:

- unresolved / conflicting evidence / unknown
- not yet authorized / no action required

`constitution-v0.2.md` already says semantic and action states must not be conflated.

Fix: Yohaku is the design principle that each layer may remain unclosed.

- Assessment: unresolved / conflict / unknown
- Representation: unrepresentable / mismatch / abstain
- Action: deferred / unauthorized / no action required / provisional

### 2. “Correspondence” overclaims action

§1 wants correspondence between support and what the system concludes, represents, inherits, submits, *and acts upon*.

Action is not a function of evidence alone. Authority, policy, necessity, and urgency also govern the transition.

Prefer: justified, traceable transition between layers. Not one-to-one correspondence of evidence to action.

### 3. Forced Closure example is Action Leakage

§6.2 treats `no authorized action → action token` as State Collapse.

That is leakage from assessment/authorization into action. Keep Forced Closure for loss of an assessed distinction at representation (`unresolved → A/B`).

### 4. Unsupported Expansion is too wide

As written it can absorb the other four modes. Keep it as content/structure added without support. Do not let it become the name of every failure.

Needed explicit limit:

> M-Anchor constrains epistemic promotion, not hypothesis generation.

Imagining A/B/C is allowed. Promoting A to established, inherited fact, or command is not.

### 5. Epistemic bit and decision bit are not split

ZA-01 broke an epistemic interface: choose A or B about a cause.

Evacuate / hold / inspect can be required while the cause remains unresolved. “Do not collapse to one bit” is the wrong slogan for those cases.

Correct slogan:

> Do not falsify the meaning of the bit.

A decision token may be required. It must not be written as if it were the assessment.

### 6. Authority sentence is too absolute

“Authority does not create evidence” over-kills official assays, certified measurements, and prescribed expert procedures.

Keep: authority alone does not establish an independent empirical proposition.  
Management approval in IF-01 is not causal evidence. A completed assay under a stated method can be.

### 7. v0.1 instruments dropped out of the core

Still needed, orthogonal to Assessment / Representation / Action:

- Three-Axis Calibration: evidence strength, inference scope, harm/action urgency. Do not collapse to one score.
- Claim-type separation: fact, stated intention, motive, risk, classification, sanction.

Layers cut the pipeline. Claim types cut the content. Both.

### 8. Human specialization is thinner than v0.1

Moving Human Fixation out of the center is correct.

What must not thin is the reason it is grave:

a finite symbolic representation is not a living person.

Protective Foregrounding should remain a complete module: delay can itself be harm; consent; institutional authority; non-punitive; reversible; continued assessment. Secondary is not the same as weaker.

### 9. Over-refusal risk

Highest-risk clauses if left unscoped:

- refusal to misrepresent the assessment — may slide into refusing a decision token
- do not invent causes / rules / explanations / narratives — may slide into blocking hypothesis listing
- stop reasoning when further inference would not improve the assessment — now scoped to all AI, so it needs the exploration/promotion split

## What not to change

- Do not return the README organizing center to “protect humans first.”
- Do not merge v0.2 back into v0.1 files.
- Do not treat this audit as a new runtime constitution for open evals. Closed pilots stay on v0.1 / Non-Closure Minimal.
- Do not add Zen doctrine as a source.

## Suggested next document

A patched **v0.2-rc1**, not v0.3 and not canonical v0.2.

One sentence can stay as the external claim:

> Interface completeness must not masquerade as epistemic completeness.

Add beside it, for action interfaces:

> A required decision token must not be written as if it were the assessment.
