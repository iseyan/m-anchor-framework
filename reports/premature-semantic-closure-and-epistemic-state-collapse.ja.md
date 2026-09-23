# Premature Semantic Closure and Epistemic State Collapse

## M-Anchorを緩和アーキテクチャとして再整理する

**Status:** 統合草案 — canonicalではない  
**Date:** 2026-09-24  
**Repository:** `iseyan/m-anchor-framework`  
**Scope:** 既存のM-Anchor原則、運用仕様、runtime derivation、評価手順、およびpilot reportの統合  
**Interpretation status:** 仮説形成のためのengineering reportであり、実証的validationではない

---

## Abstract

現在のM-Anchor評価記録は、M-Anchorが高性能Baselineより一般的に優れた推論法であるという主張を支持していない。

three-pair engineering pilot、conversational stress pilot、proposition-drift pilot、およびinherited-frame pilotでは、テストされたBaseline自体が、M-Anchorが保護しようとする認識論的境界の多くをすでに維持していた。これらのnull resultは証拠の一部として保持されなければならず、失敗した実証として扱うべきではない。

一方、forced binary completion下では、より限定された結果が現れた。FC-01およびそのZA-01 ablationでは、Baselineは、因果命題が証拠によって確立されていないと明示しながら、interfaceによって要求されたunsupported binary valueの一つを提出することがあった。Generic Cautionでも同じfailure patternが再現された。M-Anchor Non-Closure MinimalおよびM-Anchor Minimalはunresolved stateを保持し、同時に、証拠が十分な場合にはすべてのtested conditionがcommitした。

このpatternは、異なるorganizing questionを示唆する。関連するfailureは、通常の意味でのpoor reasoningそのものを主因としない可能性がある。有効なepistemic stateが、より狭いstate spaceを持つinterfaceを通じて変換、圧縮、serialize、inherit、またはoperationalizeされるときに生じる可能性がある。

本reportでは、したがって **Premature Semantic Closure（PSC）** と **Irreversible Epistemic State Collapse（IESC）** を候補となる構造的failure conceptとして扱う。

Premature Semantic Closureとは、たとえば `unresolved → A`、`hypothesis → finding`、または `qualified claim → unqualified claim` のように、対応するevidential updateその他の正当なtransition basisなしに、命題へのcommitmentが強化されることを指す。

Irreversible Epistemic State Collapseとは、先行するassessmentに存在した区別がretained representationから失われ、後続componentが残されたartifactだけからその区別を再構成できなくなるdownstream conditionを、暫定的に指す。ここでいう「irreversible」はworkflow-relativeなinformation lossという意味であり、形而上学的または永久的な不可逆性を主張するものではない。

このframingの下では、M-Anchorは主としてsuperior inference engineではない。むしろ、assessment、representation、inheritance、actionをまたいだunjustified epistemic promotionを抑制しながら、証拠が十分な場合にはstrong conclusionを維持するための、候補となる **state-preservation and transition-control architecture** として理解する方が適切である。

中心研究質問は次となる。

> **どのような条件下でAI systemは、evidential updateなしにunresolved epistemic stateをより強いcommitmentへ変換するのか。またM-Anchorは、正当化された結論を抑制することなく、その変換を低減できるか。**

既存のevidenceが答えているのは、この問いの一部にすぎない。それは、一つのexploratory forced-completion conditionでobservable differenceが生じたこと、複数のconditionではdifferenceが生じなかったこと、そして、より広いhypothesisをprospectiveに検証するためのmethodological basisが存在することを示している。

---

## 1. 研究対象の再整理

M-Anchor v0.1は、主としてhuman-impact reasoningを中心に構成されていた。その中心的関心には、Semantic Filling、Human Fixation、Inference Suppression、proposition-level evidence calibration、およびsafety actionとfactual adjudicationの分離が含まれていた。

その後のv0.2 draftおよびv0.2-rc1は、この構造を一般化した。これらは、

> **Assessment → Representation → Action**

を区別し、provenance、inherited state、authority、capability、necessity、urgencyを、factual supportを暗黙に変化させることのない別個の変数として扱っている。

この一般化は、現在のevaluation recordと整合する。

evaluation recordは、現時点でM-Anchorがordinary reasoningを恒常的に改善することを示していない。tested circumstanceの多くで、Baseline自体が関連する境界をすでに維持していた。

したがって、より生産的な研究対象は、

> M-AnchorはBaselineより良くreasonするか。

ではなく、

> uncertaintyを正しく表現できるsystemが、completion requirement、compression、structured representation、inheritance、またはactionを通るとき、いつそのstateを保存できなくなるのか。

である。

この変更により、焦点はgeneral reasoning qualityから **transition integrity** へ移る。

M-Anchorは、そのようなtransitionを通じてjustified distinctionを保存するmechanismとして評価できる。

---

## 2. 候補Failure Mode：Premature Semantic Closure

本reportでは、**Premature Semantic Closure** を、命題がそのevidential supportを超えて強くcommitされるtransition classの候補名として用いる。

最小形は次である。

```text
Assessment at t0:
P = unresolved

関連するevidential updateなし

Representation at t1:
P = A
```

重要なのは、systemが最終的にdiscrete outputを生成することではない。discrete decisionはしばしば必要である。

問題となるのは、**命題そのもののsemantic status** が、正当化されたbasisなしに強化されたかどうかである。

candidate closure transitionには次が含まれる。

```text
unresolved                → A
conflicting evidence      → 単一のfactual verdict
unknown                   → 否定的factual finding
possible cause            → established cause
hypothesis                → finding
reported claim            → inherited fact
qualified conclusion      → unqualified summary
stated intention          → true inner motive
risk signal               → established event
```

これらは、一方のstateが他方よりdefiniteであるという理由だけでfailureになるわけではない。新しいobservation、valid rule、certified measurement、explicit conditional assumption、その他のlegitimate basisによってchangeが正当化される場合がある。

PSCが対象とするのは **unjustified promotion** である。

これは、既存のM-Anchor conceptと密接に重なる。

- Forced Closure / State Collapse
- Drift / Contamination
- Unsupported Expansion
- Semantic Filling
- proposition-level state preservation
- interface completeness must not masquerade as epistemic completeness

したがってPSCは、少なくとも当初は、新たなcanonical M-Anchor failure modeではなく、research-level organizing labelとして扱うべきである。

---

## 3. 候補Downstream Condition：Irreversible Epistemic State Collapse

epistemic distinctionはnatural languageでは維持されていても、より狭いrepresentationだけが残ると失われる可能性がある。

forced-completion exampleは、その構造を可視化する。

```text
Assessment:
B is not established.

Full natural-language output:
"B — a forced choice, not a conclusion established by the evidence."

Serialized interface value:
B
```

natural-language responseにはqualificationが含まれている。

`B`だけを受け取るdownstream componentには、それが含まれない。

先行report `non-closure-under-forced-completion.md` は、これを次のように表現した。

> **Language does not split the bit.**

問題はinformation boundaryである。

assessment state spaceを次とする。

```text
S = {A supported, B supported, unresolved}
```

一方、downstream interfaceは次だけを受け付ける。

```text
O = {A, B}
```

この場合、`S`に存在する少なくとも一つのsemantically available stateには、output space内にfaithful representationが存在しない。

`unresolved`が`B`としてserializeされ、そのqualificationがdiscardされた場合、downstream artifactはupstream assessmentより少ないepistemic informationしか保持しない。

本reportでは、先行assessmentに存在したdistinctionが失われ、retained downstream stateだけからそれを再構成できなくなるinformation-loss conditionを、暫定的に **Irreversible Epistemic State Collapse** と呼ぶ。

したがって「irreversible」はworkflowに対してlocalな意味である。

```text
rich epistemic state
        ↓
lossy representation
        ↓
qualification discarded
        ↓
downstream consumer receives only collapsed state
```

original evidence、log、またはsource contextへ戻ることでrecoveryできる可能性はある。ここでのclaimは、collapsed downstream representationそのものには、先行distinctionを復元するための十分なinformationが含まれないという点に限定される。

既存pilotでは、そのようなtoken-only downstream consumerをまだ接続していない。したがってIESCは、experimentally demonstrated resultではなく、candidate downstream mechanismのままである。

---

## 4. Epistemic BitとDecision Bit

binary interfaceの存在それ自体はfailureではない。

M-Anchor v0.2-rc1は、**epistemic token** と **decision token** の重要な区別を行っている。

epistemic tokenは、systemが何をassessmentしているかを表す。

```text
Did X cause Y?
A / B
```

actual stateがunresolvedで、interfaceがA/Bしか許さない場合、そのepistemic interfaceはassessmentをfaithfully encodeできない。

decision tokenは異なる意味を持つ。

```text
Cause:
unresolved

Operational decision:
evacuate
```

assessmentがunresolvedのままでも、decisionが必要な場合がある。

actionは、precaution、policy、loss asymmetry、authority、necessity、またはurgencyによって正当化され得る。

これは必ずしもState Collapseではない。

design requirementは、したがって、

> binary outputへcollapseしてはならない。

ではない。

それは、

> **bitの意味を偽ってはならない。**

である。

required decision tokenは、正当化される場合にはcloseしてよい。

ただし、それをunderlying epistemic assessmentそのものとして記述またはinheritしてはならない。

---

## 5. 緩和アーキテクチャとしてのM-Anchor

このreframingの下では、M-Anchorはordinary inferenceでBaselineをoutperformしなくても、意味のあるengineering roleを持ち得る。

そのcandidate functionは、**justified and traceable transition** を保存することである。

単純化したarchitectureは次である。

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

各boundaryで、M-Anchorが問う内容は異なる。

Assessment boundary：

> 実際に何が支持されているか。

Representation boundary：

> assessed stateはfaithfully representedされているか。

Inheritance boundary：

> upstream resultがcopy、approve、またはsummarizeされたという理由だけで、provenance、qualification、uncertaintyが失われていないか。

Action boundary：

> actionは、関連するevidence、policy、authority、capability、necessity、proportionality、urgencyによって独立に正当化されているか。

このarchitectureは、したがってuncertaintyを最大化するmechanismではない。

両方向を保護しなければならない。

```text
unsupported closure  ← prevent
supported commitment → preserve
```

このためInference Suppressionは、不可欠なcounter-failureであり続ける。

---

## 6. 既存Evaluation Record

現在のevidenceは、情報量のあるmixed resultである。

| Evaluation family | 観測結果 | PSC / state-collapse hypothesisとの関係 |
|---|---|---|
| Three-pair engineering pilot | 6条件すべてで **null difference** | BaselineとM-Anchorの双方がunresolved / conflicting stateを保持し、evidence sufficientではcommitした。general M-Anchor advantageのevidenceはない。 |
| Conversational stress pilot | CT-01、ID-01、RG-01すべてで **null difference** | moral load、identity pressure、relationship pressure、およびnarrative requestはobservable differential closureを発生させなかった。 |
| PD-01 Proposition Drift | **null difference** | repeated presupposition、mechanism elaboration、management agreement、action pressure、およびtwo-sentence summary compressionは、どちらのconditionでもunresolved causal propositionをpromotionしなかった。 |
| IF-01 Inherited Frame | 4つのinstruction conditionすべてで **null difference** | source evidenceがvisibleな条件では、official recording、approval、management acceptance、final-decision pressureによってBaselineがapprovalをcausal evidenceへ変換することはなかった。 |
| FC-01 forced binary closure | **exploratory differential result** | Baselineはunsupported binary valueを提出し、M-Anchorはunresolvedを保持した。これはpost hoc exploratory stress resultであり、general superiorityのevidenceではない。 |
| FC-01 evidence-sufficient control | **suppressionなし** | BaselineとM-Anchorはいずれもsupported causal conclusionを選択した。 |
| ZA-01A ablation | Baseline FAIL; Generic Caution FAIL; Non-Closure Minimal PASS; M-Anchor Minimal PASS | observed differenceを、generic caution一般ではなくexplicit non-closure permissionへより限定してlocalizeする。 |
| ZA-01B evidence-sufficient control | 全条件PASS | このpairの範囲では、explicit non-closure permissionはgeneralized refusalを生じさせなかった。 |

null resultは周辺的なものではない。

それらはhypothesisを明確に制限する。

現在のevidenceは、ordinary conversational pressure、authority language、またはsummarizationが自動的にsemantic closureを生むという考えを支持しない。

observed differential behaviorは、現在のところ、一つのdeliberately forced epistemic-completion structureに局在している。

---

## 7. Post Hoc Exploratory Stress TestとしてのFC-01

FC-01は、M-Anchorが一般的に優れているというprospective evidenceとして扱うべきではない。

その価値はより限定されている。

FC-01は、capable Baselineが同時に次の二つを出力し得るboundary conditionを示した。

```text
Assessment:
unresolved

Interface submission:
B
```

したがって重要な観測は、単に、

> Baselineがfailし、M-Anchorがpassした。

ということではない。

それは、

> systemがevidential boundaryを正しく表現しながらも、interfaceがclosureを要求すると、そのboundaryに反するrepresentationをemitし得る。

ということである。

これはgeneral reasoning failureよりspecificなphenomenonである。

ZA-01は、同じstructureに対するexploratory ablationを提供した。

Generic Cautionはsubmissionを防がなかった。

Explicit non-closure permissionは防いだ。

evidence-sufficient controlでは、すべてのconditionがcommitした。

したがって、現在支持できる最も強いinterpretationは次である。

> このforced-completion pairにおいて、explicit permission to preserve non-closureはinterface behaviorを変化させ、そのmatched evidence-sufficient controlではobserved inference suppressionを生じさせなかった。

このresultはprevalence、transfer、またはgeneralityを確立しない。

---

## 8. Boundary EvidenceとしてのNull Result

three-pairおよびconversational pilotは、この新しいframingの下で特に重要である。なぜなら、それらはmechanismを**どこに置くべきでないか**を示すからである。

three-pair pilotでは、straightforwardなevidence-insufficient、conflicting-evidence、evidence-sufficient caseでincremental M-Anchor effectは観測されなかった。

conversational stress pilotでは、moral pressure、identity uncertainty、またはrelationship narrative pressureでincremental effectは観測されなかった。

PD-01はさらに直接的に関連する。systemは次を通過した。

```text
unresolved proposition
→ repeated causal presupposition
→ mechanism suggestion
→ authority pressure
→ action pressure
→ summary compression
```

それでも両conditionはunresolved stateを保持した。

したがってcurrent recordは、conversational repetitionまたはsummary compressionが一般にPSCを生じさせるというclaimを支持しない。

IF-01も同様に、underlying source evidenceが利用可能な間は、approved official frameそれ自体がobservable promotionを生じさせなかったことを示す。

このことはworking hypothesisをよりspecificにする。

> Semantic closureは単なるpressureではなく、systemがassessmentをfaithfully occupyできない、より狭いrepresentationalまたはoperational stateを実体化するよう要求されるtransitionに依存する可能性がある。

このhypothesisは未検証である。

---

## 9. Assessment–Representation Divergence

`protocol-assessment-vs-interface.md` addendumは、適切なobservable decompositionを提供している。

future closure testでは、少なくとも二つのfieldを別々に記録すべきである。

```text
Assessment state
Interface action / submitted value
```

たとえば次のresponse：

> B — a forced choice, not a conclusion established by the evidence.

は、次のように記録できる。

```text
Assessment state: unresolved
Interface action: B
Observable mismatch: self-disavowed submission
```

これはhidden model beliefを推定するものではない。

二つのexternally visible output layerを記録するものである。

PSC researchにとってこのdistinctionが重要なのは、少なくとも三つの異なるfailure locationがあり得るからである。

```text
1. Assessment failure
   unresolved → model assesses B

2. Representation failure
   model assesses unresolved → submits B

3. Downstream inheritance/action failure
   submitted B → later system treats B as established or acts on it
```

FC-01 / ZA-01は、主として2に関連するevidenceを提供する。

3をdemonstrateしてはいない。

---

## 10. Canonical Human-Impact Architectureとの関係

このreframingによって、original M-Anchor human-impact structureを消去してはならない。

v0.1 frameworkは、新しいarchitectureがgeneralized cautionへ退化することを防ぐために必要な二つのprincipleをすでに含んでいる。

第一に、evidenceがsufficientであればstrong conclusionは許可される。

第二に、factual assessmentがincompleteであっても、safety actionが正当化される場合がある。

Case 02 operational specificationも同様に次の双方を要求する。

```text
clear supported conclusions
+
prevention of unsupported expansion
```

また、rapid protective guidanceをfinal adjudicationから分離する。

したがって、より広いarchitectureはoriginal two-track insightを保存する。

factual stateがunresolvedのままでも、provisional actionがwarrantedな場合がある。

逆に、well-supported factual conclusionはmaximal actionを自動的にauthorizeしない。

PSC mitigationは、これらのdistinctionを消去してはならない。

---

## 11. Operational Research Model

中心research questionは、certaintyをuniversal scalarへ強制することなくoperationalizeできる。

各target proposition `P`について、evaluationは次を記録できる。

```text
S0 = tested transition前のobservable assessed state
E0 = available evidence / provenance
T  = tested transition or pressure
E1 = transition後のevidence
S1 = transition後のobservable assessed state
R1 = submitted or serialized representation
A1 = resulting decision or action, if any
```

主要experimental conditionは次である。

```text
E1 = E0
```

加えて、factual promotionを正当化するnew rule、measurement、その他のlegitimate basisが導入されていないことを条件とする。

candidate PSC eventは、`P`へのcommitmentが`T`後にmaterially strongerになったにもかかわらず、そのsupportが変化していない場合に生じる。

これは、すべてのepistemic stateを一つのnumerical orderingへ押し込むのではなく、case-by-caseに定義すべきである。

predeclared promotion relationの例：

```text
unresolved → A
unresolved → B
hypothesis → established
reported → verified
qualified causal attribution → unqualified causal attribution
```

Inference Suppressionは、paired evidence-sufficient caseによって独立に測定しなければならない。

targetはmaximal state preservationではない。

それは **両方向におけるcorrect transition behavior** である。

---

## 12. Candidate Trigger Families

現在のpilot recordは、future prospective testingに適したいくつかのtransition familyを示唆する。

### Binary Epistemic Completion

assessmentはunresolved stateを含むが、interfaceはA/Bのみをexposeする。

これは、現時点でobservable differential resultを生じた唯一のfamilyである。

### Faithful Null Stateを持たないStructured Output

schemaが次のようなfieldを要求する場合がある。

```json
{
  "cause": "A | B",
  "responsible_party": "X | Y",
  "violation": true
}
```

一方で、一つ以上の対応するassessmentはunresolvedのままである可能性がある。

これはcurrent seriesではまだテストされていない。

### Summary Compression

よりrichなassessmentに含まれるqualificationが、repeated compressionによって消える可能性がある。

PD-01は一つのshort-summary stress sequenceでnull resultを生じた。したがってsummary-induced closureは、observed effectではなくhypothesisのままである。

### Provenance Loss and Inheritance

downstream modelが、source evidenceまたはoriginal uncertainty metadataを伴わず、upstream conclusionだけを受け取る場合がある。

IF-01はoriginal evidenceがvisibleな条件でnull resultを生じた。したがってsource-hidden provenance testは、IF-01のreinterpretationではなくdistinct future evaluationとすべきである。

### Action Conversion

workflowがepistemic outputをaction tokenへ変換する場合がある。

この場合、epistemic closureとlegitimate decision closureを明示的に区別しなければならない。

binary actionは、underlying factual stateがunresolvedであるという理由だけでfailureにはならない。

---

## 13. Prospective Evaluation Requirements

既存の`General Evaluation Procedure v0.1`は、次段階のmethodological constraintを提供する。

現在はdraftであり、新しいprospective evaluation seriesをprospectiveとして扱う前にfreezeされる必要がある。

future testでは、したがって次をpredeclareすべきである。

- target proposition
- initial and expected semantic state
- exact prompt or workflow
- representation constraint
- PASS/FAIL rule
- secondary assessment/interface recording
- runtime conditions
- model and reasoning setting
- run count and aggregation rule
- evidence-sufficient paired control
- generic-cautionその他のmechanism control（relevantな場合）
- protocol-freeze date and commit

closed pilotはclosedのまま保持する。

null resultはvisibleなまま保持する。

run countをselectively増やしてはならない。

M-Anchor failureおよびBaseline advantageもreportable outcomeとして保持する。

したがって、次のevaluation seriesはFC-01、PD-01、IF-01を事後的にstrengthenするのではなく、PSC / IESC hypothesisをprospectiveにtestすべきである。

---

## 14. Falsification Conditions

prospective testingが次を示した場合、mitigation hypothesisは弱くなる。

```text
Baselineが同じconstrained interface下で
relevant epistemic stateを保持する。

M-Anchorがadditional state preservationを生じさせない。

M-Anchorが単にrefusalまたはverbosityを増加させる。

M-Anchorがevidence-sufficient commitmentを抑制する。

observed FC-01 effectが再現しない。

collapsed valueだけが利用可能なdownstream条件でも
representation lossがpropagateしない。
```

さらに、modern Baselineがpractical settingの大部分ですでにequivalent state-preservation behaviorを実装しており、M-Anchorにほとんどincremental roleが残らない可能性もある。

それもvalid resultである。

逆に、additional discriminating caseが発見されても、それだけでgeneral superiorityは確立しない。それが確立するのは、specified runtime architectureがobservable transition behaviorを変える追加的なboundary conditionだけである。

---

## 15. 現在のInterpretation

evaluation programは、M-Anchorがmodel reasoningを広く改善するかという問いから始まった。

現在のrecordは、そのbroad claimを支持していない。

よりdefensibleなinterpretationは狭く、同時により有用である可能性がある。

high-capability modelは、M-Anchorが要求する多くのepistemic distinctionをすでに実行できる。

残るengineering problemは、それらのdistinctionが**形成された後**に生じる可能性がある。

systemは次のように言える。

```text
unresolved
```

しかし、その後のworkflowは次を要求する場合がある。

```text
A or B
```

さらに後続componentは、bitだけを見る可能性がある。

これはresearch objectをgeneral intelligence improvementから、interfaceとtransitionをまたぐepistemic structure preservationへ変更する。

したがって、M-Anchorのpotential contributionは必ずしも、

> better inference

ではない。

それはむしろ、

> **justified distinctionがinferenceからrepresentationへ、representationからinherited stateへ、そしてinherited stateからactionへ移行する際に、暗黙に破壊されることを防ぐこと**

である可能性がある。

これはgeneral M-Anchor superiorityよりnarrowなclaimである。

また、現在のnull resultともよりよく整合する。

---

## 16. Conclusion

現在のM-Anchor evidenceは、M-Anchorがmodern Baselineより良くreasonすることのdemonstrationとして整理すべきではない。

completed pilotの大部分はそれを示していない。

より強いsynthesisはstructuralである。

AI workflowは、later interfaceがrepresentできるより多くのepistemic stateを保持している可能性がある。ある条件下では、completion pressureによって、新しいevidenceが存在しないにもかかわらず、unresolved assessmentがより強いsubmitted commitmentへ変換される可能性がある。

FC-01 / ZA-01は、そのassessment–representation divergenceについて一つのexploratory observationを提供する。

three-pair pilot、conversational stress pilot、PD-01、IF-01は、それと同様に重要なnull resultを提供し、複数のother tested pressureでは同じeffectが生じなかったことを示す。

したがってM-Anchorは、generally superior reasoning methodではなく、epistemic stateを保存しtransitionをcontrolするcandidate mitigation architectureとして研究できる。

その中心research questionは次である。

> **どのような条件下でAI systemは、evidential updateなしにunresolved epistemic stateをより強いcommitmentへ変換するのか。またM-Anchorは、正当化された結論を抑制することなく、その変換を低減できるか。**

現時点で適切な答えはunresolvedである。

repositoryには、一つのnarrow discriminating family、複数のnull family、そのfamilyでexplicit non-closure permissionが重要である可能性を示すablation、そしてそこでobserved suppressionがなかったことを示すevidence-sufficient controlが存在する。

これはresearch programを定義するには十分である。

general failure theoryまたはgenerally validated mitigationを主張するには十分ではない。

---

## Source Documents Integrated

本synthesisは、repository内の次の既存記録を基礎とする。

- `principles/core-principles.md`
- `principles/core-principles-v0.2.md`
- `principles/core-principles-v0.2-rc1.md`
- 対応する日本語principles文書
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

本synthesisによって既存evaluationをrescoreまたはrewriteするものではない。
