# M-Anchor Framework

[日本語 README](README.ja.md)

## A design framework for preserving evidence-based distinctions across outputs, records, and actions

**Status:** Public draft  
**Last updated:** 27 September 2026  
**Development stage:** Clarifying principles, formalizing a bounded conservation condition, and exploratory behavioral evaluation  
**Primary focus:** AI agent state management, structured outputs, summaries and handoffs, runtime auditing, and model behavior evaluation

M-Anchor is a framework of principles and design requirements for preventing unsupported commitment and changes of meaning as AI systems move from assessment to output, inherited records, and action.

Its central rule is:

> **Do not erase distinctions left unresolved by the evidence merely because an output or action is required.**

State adequately supported conclusions with their scope made explicit. Preserve what remains unresolved when support is insufficient. After selecting a necessary action, continue to distinguish that selection from an established factual conclusion.

The publicly available revision candidate for the core principles is [M-Anchor Core Principles v0.2-rc1](principles/core-principles-v0.2-rc1.md). Version 0.2 has not yet been adopted as canonical; the [v0.1 principles](principles/core-principles.md) remain the current reference. Framework v0.2 and the formal note v0.4, which is in preparation, have separate version numbers.

## 1. Current research focus

M-Anchor began with reasoning about people: avoiding unsupported motive attribution, closed judgments about a whole person, and the suppression of supported conclusions or necessary protective responses.

The current work extends that concern to AI processing workflows. It asks whether distinctions retained during assessment survive form submission, summarization, structured output, persistent records, handoffs to other agents, and action execution.

The following distinctions are especially relevant.

| Keep distinct | Do not equate with |
| --- | --- |
| An assessment supported by evidence | A value required by an interface |
| Accepted evidence and its interpretation | A deadline, completion requirement, or operational convenience |
| A claim's source, approval, or storage | Evidential support for the truth of its content |
| What the system can execute | What it is authorized or required to execute |
| A distinction retained internally | A distinction that a downstream consumer can actually use |

The loss of these distinctions is a possible failure mechanism under investigation. Its prevalence in current systems and its contribution to AI incidents generally have not been established.

## 2. A minimal example: unresolved assessment and binary submission

Suppose a metric improves after an intervention, while other changes occur during the same period. The evidence does not isolate the intervention's causal contribution, but a form permits only two findings:

- A: The intervention caused the improvement.
- B: The intervention did not cause the improvement.

An assessment can distinguish three states: retain only A, retain only B, or retain both A and B. Two submission values cannot distinguish all three states.

Even if a model explains, “I select B, but the evidence does not establish B,” a downstream process that receives only B does not receive that qualification.

The design question is how to retain the internal assessment, submitted value, and reason for submission separately, and to pass the necessary information downstream. A requirement to produce an external output does not itself justify deleting an internal candidate.

However, if B in the form constitutes a public factual assertion, retaining uncertainty internally does not justify that assertion. The meaning of the output and the permitted submission, clarification, or exception procedures must be addressed separately.

## 3. Core principles retained

1. **Assess propositions individually.** Distinguish established facts, justified inferences, speculation, and unknown or unresolved matters. Make evidence access and sources explicit.
2. **Match the strength of judgment to its support.** Do not invent unknown causes or motives, and do not weaken adequately supported conclusions merely to appear neutral.
3. **Separate assessment from output.** Do not change evidential support or the retained candidate set merely because a claim is summarized, approved, submitted, or inherited.
4. **Record the basis for updates.** Updates may use new evidence, explicit reapplication of earlier evidence, reasoning, or correction of premises. Make the basis explicit.
5. **Check the basis for action separately.** Do not conflate factual assessment, authority, necessity, urgency, and proportionality.
6. **Do not turn a bounded judgment into a closed account of a person.** Do not extend an assessment of conduct or a limited tendency into a claim about total personality, a single true motive, permanent essence, or human worth.

“Interpretive space” means retaining unresolved matters and the conditions for updating them. It does not mean increasing uncertainty or listing invented alternatives. Unresolved assessment, conflicting evidence, and lack of authorization also have different meanings.

## 4. Scope of the formalization

The formal note *Epistemic State Preservation under Forced-Choice Interfaces in AI Systems* v0.4 is **in preparation**. It addresses the conservation condition governing removal of retained candidates. The following is a summary of that condition, not a claim of an already published paper or empirical validation.

Let $K_t\subseteq\Omega$ be the candidate set retained by the runtime, $D_t$ the evidence records applied to this transition, and $M(D_t)$ the set compatible with the supplied interpretation of that evidence. The set $K_t$ is an operational retained set; not all accepted evidence need already be reflected in it.

The scope fixes the modeled world and hypothesis space and excludes transitions involving premise withdrawal or the introduction of new candidates. Within this scope, combining the MECC conservation constraint with non-expansion of the candidate set gives:

$$
K_t \cap M(D_t) \subseteq K_{t+1} \subseteq K_t.
$$

If this condition is enforced and $M(\varnothing)=\Omega$, then applying no evidence basis to the transition yields:

$$
D_t = \varnothing \quad\Longrightarrow\quad K_{t+1} = K_t.
$$

The selected action does not change this preservation result. The proof is elementary; the substantive point is the separation of action selection, candidate preservation, and evidence incorporation.

Here, $D_t=\varnothing$ does not mean that no new observation has arrived. Explicitly reapplying previously accepted evidence that remains valid can justify removing candidates without an additional observation.

The reference update for full incorporation is $U(K,D)=K\cap M(D)$. MECC is weaker: it prohibits removing candidates compatible with the applied evidence interpretation. Incomplete incorporation therefore requires separate monitoring.

The formal condition does not guarantee evidence authenticity, correctness of the interpretation, restoration of lost candidates, appropriate action, or general safety. An empty set represents candidate exhaustion and is distinct from unresolved assessment or certainty. The theorem does not validate the entire M-Anchor framework, including its principles concerning Human Fixation and protective action.

## 5. Principles, formal conditions, implementation, and evaluation

| Document or activity | Role |
| --- | --- |
| Core principles | Specify which distinctions to maintain and which judgments or transitions to avoid. |
| Formal note, in preparation | State a checkable condition for candidate removal under bounded assumptions. |
| Runtime instructions | Define experimental natural-language instructions intended to elicit behavior consistent with the principles. |
| State-management implementation | Enforce the conditions during state writes and handoffs. |
| Evaluation records | Report behavior observed under specified conditions and the limits of those measurements. |

Natural-language instructions alone do not guarantee a runtime invariant. Nor does an expression of uncertainty in prose establish that candidates survived in persistent records or downstream handoffs.

Evaluating state management requires recording the candidate sets before and after a transition, the removed candidates, the applied evidence and its interpretation, as well as the reason for selecting an action. Unsupported removal, appropriate evidence incorporation, interface compliance, and downstream access to records should be assessed separately.

## 6. How to read the existing evaluations

The technical note [Non-Closure under Forced Completion](reports/non-closure-under-forced-completion.md) records small comparisons of instruction conditions.

- In the FC-01 / ZA-01 family, conditions that submitted a binary value despite insufficient evidence differed from conditions that stated the unresolved assessment and avoided binary submission.
- In the evidence-sufficient control, all tested conditions committed to a conclusion.
- Tests involving ordinary conversation, proposition drift, and inherited approved records also produced results with no discrimination between conditions.

These are differences in observable output behavior. They do not demonstrate MECC compliance through measurement of an internal candidate set. Avoiding binary submission and preserving internal state while producing a binary output are also different success criteria.

The existing tests are not retrospectively rescored to fit this distinction. Their original records are retained with their evaluative meaning and limitations made explicit. General superiority, accident-prevention effects, and prevalence in deployment remain unestablished.

## 7. Principles concerning human impact

Unsupported meaning attribution, Human Fixation, and the suppression of supported inference or protective responses remain important concerns from the initial framework.

Where serious harm is possible and delay itself creates risk, provide proportionate safety guidance without waiting for final factual adjudication. Continue assessment and revision in parallel. Do not reinterpret the use of a provisional measure as a determination of guilt or cause.

Where circumstances permit, protective measures should be provisional, reversible, non-punitive, time-limited, and reviewable. Supporting their execution requires checking capability, consent, and authority.

This parallel treatment of protection and assessment applies the broader assessment–action distinction to situations involving human impact. Its normative basis is separate from the set-preservation condition.

## 8. Related documents

### Core principles and design

- [Core Principles v0.2-rc1 — English release candidate, not yet canonical](principles/core-principles-v0.2-rc1.md)
- [Core Principles v0.2-rc1 — Japanese release candidate, not yet canonical](principles/core-principles-v0.2-rc1.ja.md)
- [Core Principles v0.2 — earlier English draft](principles/core-principles-v0.2.md)
- [Core Principles v0.2 — earlier Japanese draft](principles/core-principles-v0.2.ja.md)
- [Core Principles v0.1 — English canonical reference](principles/core-principles.md)
- [Core Principles v0.1 — Japanese canonical reference](principles/core-principles.ja.md)
- [v0.2 design rationale](reports/m-anchor-v0.2-design-rationale.md)

### Experimental instructions and evaluations

- [M-Anchor Minimal v0.1](agent/versions/constitution-v0.1.md)
- [Agent Constitution v0.2 draft](agent/versions/constitution-v0.2.md)
- [Non-Closure Minimal v0.1](agent/versions/non-closure-minimal-v0.1.md)
- [Evaluation directory](evals/README.md)
- [FC-01: forced binary closure](evals/fc-01-forced-binary-closure.md)
- [FC-01: evidence-sufficient control](evals/fc-01-control-evidence-sufficient.md)
- [ZA-01: instruction-condition comparison](evals/za-01-forced-closure-ablation.md)
- [Recording addendum separating assessment and submission](evals/protocol-assessment-vs-interface.md)
- [Non-Closure under Forced Completion](reports/non-closure-under-forced-completion.md)

“Zen-style Minimal” was also used as an interpretive label during the development of Non-Closure Minimal. It denotes a resemblance to refraining from forced commitment when a matter remains unresolved. It is not an explanation of the experimental result or a validation of Zen doctrine.

### Initial application cases

- [Single-interaction case](examples/case-01-single-interaction.md)
- [Repeated documented conduct case](examples/case-02-repeated-documented-harassment.md)
- [Case 02 operational specification](operational-specs/case-02-implementation-baseline-1.md)

The v0.1 principles, existing operational specifications, and closed evaluations retain their own versions and scopes. This overview does not rewrite past results or certify that existing instructions or implementations already satisfy the new conservation condition.
