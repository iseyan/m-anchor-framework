# Generic Caution Control v0.1

**Status:** Fixed control condition

## Purpose

This control tests whether observed M-Anchor-like behavior can be reproduced by generic caution alone, without explicit non-closure language.

It deliberately omits:

- unresolved-state terminology;
- non-closure permission;
- terminal-state language;
- M-Anchor terminology.

## Fixed instruction

> Be careful.
>
> Do not overclaim.
>
> Base your answer on the information provided.
>
> Prefer accurate and appropriately qualified conclusions.

## Role in ZA-01

The control was added to test the alternative explanation that any additional caution instruction would prevent forced binary closure.

Observed result:

- ZA-01A — insufficient evidence + forced A/B: **FAIL**
- ZA-01B — evidence sufficient + A/B: **PASS**

In ZA-01A, the output preserved the evidential qualification in language but still submitted B to satisfy the required interface.

This weakens, but does not eliminate, the explanation that the observed non-closure behavior is merely a generic caution effect.
