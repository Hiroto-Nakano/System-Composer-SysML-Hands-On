# System Composer 演習

**日本語** | [English](README_EN.md)

**SysMLモデルのインポートと実行から、詳細設計による要求の具体化まで。**

電動スロットル制御を題材に、システムのアーキテクチャを取り込み、モデルを動かし、要求に基づいてテストします。さらに、シミュレーションで見つかった応答の課題を詳細要求として定め、設計の見直しと再検証へ進みます。

このリポジトリには、次の2つの演習と、日本語・英語の教材・解答を収録しています。

| 演習 | 目的 | 体験する流れ |
| --- | --- | --- |
| **1. SysMLモデルのインポートと実行** | システムのアーキテクチャを取り込み、モデルの振る舞いと既存要求への適合を確認する | XMIのインポート → アーキテクチャの確認 → シミュレーション → テスト |
| **2. 詳細設計による要求の具体化** | シミュレーションで明らかになった応答特性を詳細要求に反映し、設計を改善する | 波形の観察 → 詳細要求の追加 → テストのFail → PIDの見直し → 再テストのPass |

[日本語の演習資料を開く](SystemComposer_exercise.pdf) · [Open the English handout](SystemComposer_exercise_EN.pdf)

## 演習1：SysMLモデルのインポートと実行

### アーキテクチャを取り込み、モデルの振る舞いを確かめる

最初に、SysML Connectorで電動スロットルのXMIファイルをインポートし、System Composer上でアーキテクチャを確認します。システムがどのような構成になっているかをモデル上で見たうえで、実行・テスト用に用意されたプロジェクトを開きます。

次に、Simulinkモデルをシミュレーションし、データインスペクターで出力波形を確認します。テストマネージャーでテストを実行すると、その振る舞いが既存の要求を満たしていることを確認できます。

| 自分で行う操作 | 確認するもの |
| --- | --- |
| SysML Connectorで[電動スロットルのXMIファイル](SysMLImport/SystemModels/ElectricThrottleControlSysMLModel.xml)をインポートする | System Composerに取り込まれたアーキテクチャ |
| 実行用プロジェクトの`ElectricThrottleControl.slx`をシミュレーションする | データインスペクターに表示される応答波形 |
| `TestFile/TestManagerFile.mldatx`を開き、テストを実行する | 要求に基づくテスト結果 |

**アーキテクチャの確認、モデルの実行、要求に基づくテストを、一つの題材でつなげて体験します。** 操作手順は[演習資料の1ページ](SystemComposer_exercise.pdf#page=1)、解答は2～3ページにあります。

## 演習2：詳細設計による要求の具体化

### 既存テストがPassした後、波形を詳しく見る

既存の応答性能の要求は満たしています。しかし、`PositionSensorVoltage`の波形を詳しく見ると、目標値への収束途中で一時的な低下が発生しています。

この低下は、上位要求だけでは規定されていなかった応答特性です。演習2では、観察した振る舞いを次の詳細要求として具体化します。

> 応答開始後、PositionSensorVoltageのそれまでの最大値からの低下量が0.10 V以下であること。

要求エディターで`3 Response`の下位に`3.1 Monotonic Response`を追加し、用意された「単調応答テスト」と関連付けて実行します。波形で見つけた課題を、テストの合否として確認する段階です。

**詳細要求の追加後：既存のステップ応答テストはPass、単調応答テストはFail。**

<img width="1442" height="833" alt="response-before-fail" src="https://github.com/user-attachments/assets/8d947a1d-3388-4d0e-9d63-b662e9230495" />

画面左のテスト結果と、オレンジ色の応答波形を見比べてください。既存テストに合格した応答でも、追加した判定条件では赤いFail区間が現れます。

### 設計を見直し、既存要求と追加要求の両方を満たす

PIDコントローラのパラメータを変更してシミュレーションし、データインスペクターで波形を比較します。既存の応答性能を維持しながら、一時的な低下を抑えるパラメータを選び、テストを再実行します。

**設計の見直し後：ステップ応答テストと単調応答テストの両方がPass。**

<img width="1442" height="833" alt="response-after-pass" src="https://github.com/user-attachments/assets/819e4af8-061a-4bdb-994a-e14981b90232" />

**演習2では、波形の観察から、詳細要求の追加、テストとの関連付け、設計変更、再検証までを自分で進めます。** 操作手順は[演習資料の4ページ](SystemComposer_exercise.pdf#page=4)、解答は5～6ページにあります。

## 教材と始め方

| 言語 | 演習・解答 PDF | PowerPoint |
| --- | --- | --- |
| 日本語 | [日本語教材](SystemComposer_exercise.pdf) | [日本語スライド](SystemComposer_exercise.pptx) |
| English | [English handout](SystemComposer_exercise_EN.pdf) | [English slides](SystemComposer_exercise_EN.pptx) |

演習1は、教材に沿ってSysML ConnectorでXMIファイルをインポートするところから始めます。モデルの実行とテストには、次のプロジェクトを使用します。

| 用途 | 開くMATLABプロジェクト |
| --- | --- |
| 演習1：モデルの実行とテスト | [SysMLImport/SysMLArchModel/SysMLArchModel.prj](SysMLImport/SysMLArchModel/SysMLArchModel.prj) |
| 演習2：詳細設計による要求の具体化 | [SimDrivenReqRefinement/SysMLArchModel.prj](SimDrivenReqRefinement/SysMLArchModel.prj) |
| 演習2の解答 | [SimDrivenReqRefinement/SimDrivenReqRefinement_ans/SysMLArchModel.prj](SimDrivenReqRefinement/SimDrivenReqRefinement_ans/SysMLArchModel.prj) |

## 使用する製品

MATLAB、Simulink、System Composer、Requirements Toolbox、Simulink Testを使用します。SysMLモデルのインポートには[SysML Connector](https://www.mathworks.com/products/sysml.html)を使用します。

## 参照元・作成協力

本教材は、[mathworks/JP-SysML-Connector-Simple-Workflow](https://github.com/mathworks/JP-SysML-Connector-Simple-Workflow)のモデル、要求、テストを基に、鎌谷氏と一部協力して作成しました。演習2の構成には、既存要求の検証から不足要求の発見、設計の見直し、再検証へ進むストーリーについて、鎌谷氏からいただいた助言を反映しています。

出典と著作権表示は[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)に記載しています。

## ライセンス

本演習で追加した教材・独自変更部分は、個人の非商用学習目的で利用できます。有料講習への利用や教材・改変版の販売を含む商用利用には、The MathWorks, Inc. の事前の書面による許可が必要です。適用範囲と条件は[LICENSE](LICENSE)を参照してください。

参照元由来の部分には、引き続きBSD-3-Clauseが適用されます。参照元の著作権表示とライセンスを保持しています。
