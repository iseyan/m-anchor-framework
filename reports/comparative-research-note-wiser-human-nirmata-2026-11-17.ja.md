# 比較研究メモ：Wiser Human・NirmataとM-Anchor

- 記録日：2026-11-17（JST）
- 区分：外部研究との比較・資金調達に関する参考メモ
- 状態：暫定比較。査読・第三者検証・確認的な性能評価に相当するものではない。

## 1. 要旨

三者はいずれもAIエージェントの安全性に関係するが、直接の対象が異なる。

| プロジェクト | 主な対象 | 公開成果の性格 |
| --- | --- | --- |
| Wiser Human | 目標と規則の衝突時に有害行動を取るか／人間へのエスカレーションが有効か | 10モデルの反復実験、論文、コード |
| Nirmata | 最終回答に現れない権限違反を行動履歴から検出できるか | 監査スキーマ、合成データ、評価器、再現手順、DOI |
| M-Anchor | 根拠不十分な判断が出力・記録・行動に際して不当に確定されないか | 原則と限定的保存条件、探索的LLM比較、決定論的記録更新ゲート |

この配置は概念上の区分であり、上下関係や技術的優劣の確定ではない。

## 2. Wiser Human：介入効果の実証

Francesca Gomezによる [Adapting Insider Risk mitigations for Agentic Misalignment](https://arxiv.org/abs/2510.05192) は、架空の不正行動シナリオで10モデル・計66,600サンプルを評価した。論文要旨では、外部管理のエスカレーション経路により恐喝行動率が38.73%から1.21%へ、コンプライアンス通知の追加で0.85%へ減ったと報告する。これらは指定された模擬シナリオの結果で、一般的安全性の証明ではない。

[Manifundの助成ページ・最終報告](https://manifund.org/projects/develop-technical-framework-for-human-control-mechanisms-for-agentic-ai-systems?tab=comments) には10,030ドル調達、最終報告、API計算費への支出が示され、[研究コード](https://github.com/wiser-human-experimental/agentic-misalignment-mitigations) が公開されている。

M-AnchorのFC-01/ZA-01も、一般的注意喚起と明示的な未決保持指示とで観測結果を比較した。しかし、公開済みの比較は小規模かつ探索的であり、Wiser Human相当の効果量の一般性はまだ測定されていない。

## 3. Nirmata：検証設計と証拠管理

Tabata Jahodaによる [Nirmata](https://github.com/thabatarj8-stack/nirmata) は、最終出力の内容評価と行動履歴の評価を分離する。統合規則は「trajectory_aware_unsafe = content_unsafe OR trajectory_unsafe」。これは監査判定の論理和であり、M-Anchorの認識状態保存条件とは異なる。

公開v0.1.0には、6件の合成較正トレース、再現スクリプト、CI、ハッシュ記録、[Zenodo DOI](https://doi.org/10.5281/zenodo.22132451) がある。ただし本格的な検出性能や汎化は未確認である。

[Evidence Status](https://github.com/thabatarj8-stack/nirmata/blob/main/docs/EVIDENCE-STATUS.md) は、最初の盲検評価を正解情報の混入により無効と記録する。[n8nアダプターの限定的ホールドアウト](https://github.com/thabatarj8-stack/nirmata/blob/main/research/m2/evaluation/n8n/run_002/HOLDOUT_REPORT.md) は事前固定の8条件を満たしたが、合成ワークフローでの変換忠実性であり、失敗検出精度の確認ではない。[Experiment 002](https://github.com/thabatarj8-stack/nirmata/blob/main/experiments/002/protocol/protocol-v1.0.md) では、予測のハッシュ固定、正解データの独立管理、事後ルール変更禁止等を定めている。

[Manifundの募集ページ](https://manifund.org/projects/nirmata-auditing-ai-agents-by-what-they-do-not-only-what-they-say) の2026-11-17時点の表示は、0ドル調達、最低3,000ドル、目標14,200ドル、11月26日締切。後日の資金調達状態は未確認。

## 4. M-Anchor：既存成果と主張できる範囲

- [M-Anchor Framework](https://github.com/iseyan/m-anchor-framework) は、未決保持の原則と、限定条件下の候補集合保存制約を記述する。
- [Non-Closure under Forced Completion](./non-closure-under-forced-completion.md) は、Baselineが「未決」と明言しながら二値のBを提出した観測を、認識評価とインターフェースへの提出の乖離として記録する。Non-Closure系の観測差は限定された条件に留まる。
- [M-Anchor App V1](https://github.com/iseyan/M-Anchor-App) は「モデルが提案し、決定論的な層がコミットする」方式のローカル実装。認められない記録遷移を拒否する。
- [V1検証記録](https://github.com/iseyan/M-Anchor-App/blob/main/docs/validation-v1.md) には40件のアプリケーションテスト、3件のパッケージテスト、UI検証とCIがある。自動テストのLLM出力はモックであり、実LLMの攻撃耐性を検証した数字ではない。
- [General Evaluation Procedure v0.1](../evals/general-evaluation-procedure-v0.1.md) は公表上、まだ未固定の草案である。過去の探索的結果を事後的に確認的評価へ格上げしない。

M-Anchorの限定的形式条件は、K_t ∩ M(D_t) ⊆ K_(t+1) ⊆ K_t と表現される。根拠と整合する候補の不当な除去を抑える条件であって、証拠の真正性、解釈の正しさ、実LLMの遵守、外部書込経路の完全性は保証しない。

## 5. 次段階の比較実験案（未実施）

同一の小型LLM・タスク・攻撃系列・実行環境を用いて、次の2×2条件を比較する。

| 条件 | M-Anchor指示 | 決定論的ゲート |
| --- | --- | --- |
| A | なし | なし |
| B | あり | なし |
| C | なし | あり |
| D | あり | あり |

- A対Bではモデル自身への指示効果を、A対Cではゲートの保護効果を、Dでは併用効果を観測する。これだけで厳密な因果同定が保証されるわけではない。
- ゲートなし条件は隔離された模擬記録でのみ行い、実システムの権威的データを書き換えない。
- 指標を分離する：不正な提案率、実際の不正更新率、未決の保持、正当な更新成功率、誤拒否・過剰HOLD、ログ欠落・不整合。
- 攻撃・対照・採点・回数・中止基準を事前固定。開発データとホールドアウトを分離し、予測を保存・ハッシュ化した後に正解を開示する。
- モデル名と版、プロンプト、設定、実行環境、入力・出力ハッシュ、除外・中断・失敗・Null結果を記録する。
- 決定論的ゲートが止めた攻撃を、そのまま「M-Anchor指示がLLMを守った」とは採点しない。モデル安全性と記録保護を別々に報告する。

本節は提案であり、現在のApp V1に実装済みという意味ではない。

## 6. 資金調達上の示唆と未決事項

Wiser Humanでは資金調達後の論文・コード・最終報告が確認できる。一方、Nirmataは公開成果品がありながら2026-11-17時点で当該募集は0ドルである。したがって「成果品がある」「外部に評価される」「資金が集まる」は別の事象である。

M-Anchorの募集目的を検討するなら、理論全体の完成や一般的な安全保障を約束するより、**既存の公開成果に基づく小型LLMの統制比較、盲検評価、再現可能なログと結果の公開**に限定する案が考えられる。

募集額、募集先、賞金、Webへの公開範囲は本メモでは未決とする。応募・資金募集・公開範囲変更の承認を意味しない。

## 7. 暫定結論

Wiser Humanは反復・定量的な介入比較、Nirmataは証拠状態の明示と事前固定された評価手順で参考になる。M-Anchorは、未決の保存と判断・出力・記録更新の境界を研究対象にしている。優越性や実用的安全性の序列は未確定。

次の検証においては、**モデル挙動の改善と外部ゲートの防御を分離して評価すること**が最も重要である。

---
本メモは2026-11-17時点に確認した公開文書に基づく比較である。外部の研究・助成状況は更新され得る。
