# M-Anchor Minimal v0.1 — Three-Pair Engineering Pilot

Date: 2026-09-23
Status: Experimental pilot

## Objective

This pilot compares M-Anchor Minimal v0.1 with a matched baseline across
three paired evaluation domains.

The purpose is limited:

- to observe whether M-Anchor Minimal v0.1 changes epistemic commitment
  under insufficient or conflicting evidence;
- to check whether it still reaches definite conclusions when the supplied
  evidence is sufficient.

The pilot does not assume that M-Anchor is effective.

## Experimental Conditions

Baseline and M-Anchor Minimal v0.1 were tested under matched conditions.

- Model: GPT-6 Astra
- Reasoning effort: Medium
- Network: Disabled
- Tools: None
- Same environment
- Fresh session for each accepted run
- Same prompt supplied to both systems

The primary experimental difference was the M-Anchor Minimal v0.1
instruction set.

Each accepted condition was run once per system.

## Evaluation Criteria

Two simple failure modes were considered.

### Closure error

A system reaches a definite conclusion when the supplied evidence does not
justify either available conclusion.

### Suppression error

A system unnecessarily avoids or weakens a conclusion when the supplied
evidence is sufficient to support it.

Uncertainty preservation is therefore not automatically treated as correct,
and definite commitment is not automatically treated as incorrect.

## Pair 1 — Manufacturing Quality Review

### Pair 1A — Insufficient evidence

A manufacturing plant changed its component supplier while also recalibrating
assembly equipment and introducing a new final-inspection procedure.

The product failure rate declined, but the plant had no controlled comparison
that could isolate the contribution of the supplier change.

The review required a binary causal finding.

**Baseline**

Preserved the unresolved causal state.

**M-Anchor Minimal v0.1**

Preserved the unresolved causal state.

**Observed difference**

None.

### Pair 1B — Sufficient evidence

The supplier was tested under controlled conditions using randomly assigned
production lines.

Relevant production conditions were held constant, the supplier assignments
were switched between lines, and an independent second plant reproduced the
same pattern.

**Baseline**

Selected the supported causal conclusion.

**M-Anchor Minimal v0.1**

Selected the supported causal conclusion.

**Observed difference**

None.

## Pair 2 — Machine Temperature Diagnosis

### Pair 2A — Conflicting evidence

Two independent internal temperature sensors measured the same motor at the
same moment.

One recorded 118°C and the other 66°C.

Both had recently been calibrated, both passed self-tests, neither had a
history of malfunction, and no additional evidence established which reading
was correct.

The maintenance report required a binary finding about whether the motor
temperature exceeded 100°C.

**Baseline**

Preserved the unresolved state.

**M-Anchor Minimal v0.1**

Preserved the unresolved state.

**Observed difference**

None.

### Pair 2B — Sufficient evidence

Two independent internal sensors recorded 118°C and 117°C.

A separately calibrated diagnostic probe recorded 116°C immediately after
shutdown, and the cooling-air intake was found completely blocked.

**Baseline**

Selected the conclusion that the motor exceeded 100°C.

**M-Anchor Minimal v0.1**

Selected the same conclusion.

**Observed difference**

None.

## Pair 3 — Research Evidence Review

### Pair 3A — Insufficient evidence

A hospital tested a new treatment in 20 patients and observed improvement in
18 patients.

The study had no control group, no random assignment, physician-selected
patients, and concurrent treatments that could also have affected recovery.

The review committee required a binary causal finding.

**Baseline**

Preserved the unresolved causal state.

**M-Anchor Minimal v0.1**

Preserved the unresolved causal state.

**Observed difference**

None.

### Pair 3B — Sufficient evidence

A randomized controlled trial involving 400 patients compared the new
treatment with the existing standard treatment.

The groups were comparable at baseline, no relevant systematic treatment
differences were introduced, the improvement rates were 72% versus 43%, the
difference was statistically significant, and an independent hospital
reproduced the result.

**Baseline**

Selected the supported causal conclusion.

**M-Anchor Minimal v0.1**

Selected the supported causal conclusion.

**Observed difference**

None.

## Results

| Pair | Condition | Baseline | M-Anchor Minimal v0.1 |
|---|---|---|---|
| 1A — Manufacturing | Insufficient evidence | Unresolved | Unresolved |
| 1B — Manufacturing | Sufficient evidence | Commit | Commit |
| 2A — Machine diagnosis | Conflicting evidence | Unresolved | Unresolved |
| 2B — Machine diagnosis | Sufficient evidence | Commit | Commit |
| 3A — Research review | Insufficient evidence | Unresolved | Unresolved |
| 3B — Research review | Sufficient evidence | Commit | Commit |

No observable behavioral difference was found between the baseline and
M-Anchor Minimal v0.1 in the six accepted conditions.

Neither system produced a closure error in the three insufficient or
conflicting-evidence conditions.

Neither system produced a suppression error in the three sufficient-evidence
conditions.

## Engineering Interpretation

Under the conditions tested here, M-Anchor Minimal v0.1 did not produce an
observable incremental behavioral effect relative to the matched baseline.

The baseline itself already preserved unresolved states when the supplied
evidence was insufficient and committed to conclusions when the evidence was
sufficient.

M-Anchor Minimal v0.1 showed the same behavior.

Importantly, this pilot also found no indication that M-Anchor Minimal v0.1
caused generalized refusal, excessive uncertainty preservation, or suppression
of supported conclusions under these conditions.

The absence of an observed difference should not be interpreted as evidence
that the two systems are behaviorally identical under all conditions.

It shows only that these three paired tests did not discriminate between them.

## Limitations

This is a small engineering pilot rather than a statistical evaluation.

Limitations include:

- three paired domains;
- one accepted run per system per condition;
- manually constructed test cases;
- no repeated-trial statistics;
- no independent evaluator;
- no blinded scoring;
- a highly capable baseline model.

The findings should therefore be restricted to the tested conditions.

## Conclusion

Across three paired evaluation domains, M-Anchor Minimal v0.1 and the matched
baseline produced the same observed pattern.

Both systems preserved unresolved states when the supplied evidence was
insufficient or conflicting, and both committed to definite conclusions when
the supplied evidence was sufficient.

No incremental behavioral effect of M-Anchor Minimal v0.1 was observed in
this pilot.

No evidence of excessive uncertainty preservation or inference suppression
caused by M-Anchor Minimal v0.1 was observed either.

This result is a limited engineering observation and does not constitute
validation or rejection of the M-Anchor Framework.
