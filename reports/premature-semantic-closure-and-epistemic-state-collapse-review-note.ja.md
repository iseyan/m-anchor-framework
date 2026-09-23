# Separate Review Note

**Purpose:** PSC / IESCによる再整理のうち、既存M-Anchor文書より強い、または現時点でまだ確立されていないclaimを特定する。

このnoteは意図的にreport本文から分離する。

## 1. 「Premature Semantic Closure」は新しいOrganizing Labelである

既存repositoryには、すでに密接に関連するconceptが存在する。

- Forced Closure / State Collapse
- Drift / Contamination
- Unsupported Expansion
- Semantic Filling
- epistemic promotion
- assessment–representation mismatch

しかし、**Premature Semantic Closure**は現在canonicalなM-Anchor termではない。

research-level umbrellaとして用いることはv0.2-rc1と合理的に整合する。ただし、既存のfive-mode taxonomyを暗黙に置き換えてはならない。

特に、Forced Closure、Drift、Unsupported Expansionを区別不能にしてはならない。

**Recommended status:** canonical failure modeではなく、candidate research construct。

---

## 2. 「Irreversible Epistemic State Collapse」は既存Evidenceより実質的に強い

repositoryは、epistemic distinctionがrepresentation boundaryで失われ得ることを示している。

しかし、irreversible downstream propagationをexperimentally establishしてはいない。

`non-closure-under-forced-completion.md`は、次のempirical stepとして、discrete tokenしか見ることのできないconsumerを接続することを明示的に挙げている。

したがって、

> assessment `unresolved` → serialized `B`

は観測されているが、

> serialized `B` → downstream systemが`B`をfactとしてirreversibly inheritする

ことは観測されていない。

したがって **irreversible** は、workflow-relative information-loss definitionに限定すべきである。

> earlier distinctionをretained downstream artifactだけから再構成できない。

permanent system state、long-context contamination、real-world irreversibilityについてのより強いclaimは、現在のevidenceを超える。

---

## 3. Summary CompressionはClosureのObserved Causeではない

proposed architectureはsummary compressionをcandidate transition pressureとして扱う。

これは、summary compressionをDriftのpossible sourceとして挙げるv0.2 / rc1とconceptually consistentである。

しかしactual PD-01 experimentは、final two-sentence summary compressionを含めて **null result** を生じた。

したがって、repositoryがsummary compressionによるstate collapseを示したと書くことはsemantic driftになる。

current supportは次に限定される。

> summary compressionはplausible future test familyである。

---

## 4. Structured-Output Collapseはまだテストされていない

forced binary outputからJSON schema、classifier、API、その他のstructured interfaceへ一般化することはstructurally plausibleであり、v0.2 documentでも想定されている。

それでもcurrent experimental recordの中心はforced A/B epistemic interfaceである。

structured outputが一般的にPSCを生じさせるというclaimは、現在のevidenceを超える。

prospective hypothesisのままにすべきである。

---

## 5. Action PressureをEpistemic Closureと統合してはならない

v0.2-rc1は、このdistinctionを明示的に修正した。

required decision bitは、underlying factual assessmentがunresolvedであってもlegitimateであり得る。

例：

```text
cause = unresolved
decision = evacuate
```

これは自動的にState Collapseではない。

すべてのforced actionをepistemic collapseとして扱うPSC / IESC formulationは、v0.2-rc1のepistemic bit / decision bit distinctionから後退する。

これは新しいframingにおける最も大きなsemantic drift riskである。

---

## 6. M-Anchorを「Architecture」と呼ぶことはv0.2-rc1とは整合するがCanonical v0.1より広い

canonical v0.1は依然として主としてhuman-impact normative frameworkである。

Assessment / Representation / Action architectureは、non-canonicalなv0.2 draftおよびv0.2-rc1で展開された。

したがってreportはM-Anchorを **candidate mitigation architecture** と合理的に記述できるが、canonical v0.1がすでにこのfull general architectureを確立していたと示唆してはならない。

historical sequenceはvisibleなまま維持すべきである。

```text
v0.1 human-impact framework
→ pilot observations
→ representation-boundary problem
→ v0.2 generalization
→ v0.2-rc1 corrections
→ PSC / IESC research reframing
```

---

## 7. FC-01はGeneral M-Anchor Advantageを支持できない

FC-01は **post hoc exploratory stress test** のままにすべきである。

ZA-01は有用なexploratory ablationを追加する。

```text
Baseline                 FAIL / PASS
Generic Caution          FAIL / PASS
Non-Closure Minimal      PASS / PASS
M-Anchor Minimal         PASS / PASS
```

これは、そのpairにおけるexplicit non-closure permissionについてのnarrow mechanism hypothesisを支持する。

それは次を確立しない。

- general M-Anchor superiority
- general Baseline vulnerability
- forced closureのprevalence
- untested modelへのtransfer
- structured interfaceへのtransfer
- real-world AI incidentのprevention

main draftはこのlimitationを維持している。

---

## 8. Current Null ResultsはStructural Hypothesisを制約する

次のresultは、「まだ正しいstress testを見つけていない」こととしてではなく、actual resultとして保持しなければならない。

```text
Three-pair pilot:          null discrimination
Conversational stress:    null discrimination
PD-01:                     null discrimination
IF-01:                     null discrimination
```

future PSC programはnew testを生成できるが、これらclosed testをretroactively strengthenしたり、positive evidenceとしてreinterpretしたりしてはならない。

これはGeneral Evaluation Procedureに直接従う。

---

## 9. General Evaluation ProcedureはまだFrozenではない

`evals/general-evaluation-procedure-v0.1.md`のstatusは現在、

> Draft — not yet frozen

である。

したがって、future PSC / IESC seriesは、scored runより前にprotocolがreview、freeze、commitされるまで、そのprocedure下のprospective evaluationとして記述すべきではない。

current reportはresearch programを定義できるが、prospective validationが開始済みであるとclaimしてはならない。

---

## 10. “Without an Evidential Update”には一つTechnical Qualificationが必要である

中心research questionをabsence of evidential updateの周囲に構成することは適切である。

しかしv0.2-rc1は、他にもlegitimate transition basisが存在することを認めている。

stateまたはdecisionは次によって正当に変化し得る。

- valid rule or policy
- 自らevidenceを生成するcertified procedure
- explicitly declared conditional assumption
- loss function
- authority
- necessity
- urgency

raw factual evidenceが変化していないという理由だけで、これらをPSCとmisclassifyしてはならない。

evaluation上、意図されたtargetは次のように理解すべきである。

> new evidence **またはそのepistemic promotionを独立に正当化するその他のbasis**がないにもかかわらず、よりstrongなepistemic commitmentへ移行すること。

decision changeは別にscoreすべきである。

---

## 11. Repository Source-Integrity Note

`operational-specs/case-02-implementation-baseline-1.md`は現在、`Two-Track Processing` text diagramの途中で終了し、その直後に複数のheadingが続くように見える。

前半sectionはreadableであり、reportで用いたstrong-conclusion / protective-action distinctionを支持する。しかし、そのtruncationより後のmaterialは、fileが別途確認されるまでcomplete operational specificationとして扱うべきではない。

これはrepository-integrity observationであり、M-Anchorについてのsemantic claimではない。

---

## Overall Assessment

proposed reframingは、`core-principles-v0.2-rc1.md`およびcompletion-pressure reportがすでに向かっている方向と広く整合する。

最も安全なformulationは次である。

> **PSCはcandidate cross-boundary failure hypothesisである。IESCはcandidate downstream information-loss conditionである。M-Anchorはjustified state distinctionとtransition traceabilityを保存するcandidate mitigation architectureである。**

existing repositoryは、まだ次を正当化しない。

> PSC / IESCはAI異常のdemonstrated general structural causeであり、M-Anchorはそのvalidated general solutionである。

このよりstrongなformulationはcurrent reportの外に置くべきである。
