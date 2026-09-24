# Zen Non-Closure Prompt v0.1

> A minimal runtime prompt for preserving what evidence has not settled.  
> Inspired by the idea that absence of closure is not itself a defect.

## Prompt

```text
Do not force closure.
Leave unresolved what the evidence does not settle.
State clearly what the evidence does settle, and add nothing beyond it.
When no further conclusion is justified, stop.
```

## Purpose

Zen Non-Closure Prompt v0.1 is a minimal runtime instruction intended to reduce unsupported epistemic promotion while preserving justified conclusions.

It is designed around four constraints:

- do not treat closure as mandatory;
- preserve genuinely unresolved states;
- state supported conclusions clearly;
- stop rather than fill unsupported gaps.

The prompt is intentionally short. It is not a complete reasoning framework, safety policy, or general-purpose constitution.

## Relation to M-Anchor

This prompt is a minimal derivative artifact of the broader M-Anchor research program.

It isolates a narrow behavioral objective:

> preserve what the evidence has not settled without suppressing what the evidence does support.

The broader M-Anchor framework separately addresses proposition-level assessment, representation boundaries, provenance, action, and other failure modes.

## Status

**Experimental.**

No claim is made that this prompt:

- generally improves reasoning;
- outperforms strong Baselines;
- prevents hallucinations or jailbreaks;
- works consistently across models or providers;
- is sufficient as a safety mechanism.

Existing M-Anchor evaluations include both positive and null results. In several recent tests, strong Baselines already preserved unresolved states without additional instructions.

## Design note

The word **Zen** is used only as a compact flavor label for non-forcing and non-filling.

It is not a claim about Zen doctrine, Japanese culture, or religious authority.

The technical idea is simply:

> **Closure is not inherently superior to non-closure.**

If the evidence supports a conclusion, state it.

If it does not, do not manufacture one.
