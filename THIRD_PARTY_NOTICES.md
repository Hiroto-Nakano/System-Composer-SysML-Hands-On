# 出典とライセンス表記

## JP-SysML-Connector-Simple-Workflow

- 参照元：[mathworks/JP-SysML-Connector-Simple-Workflow](https://github.com/mathworks/JP-SysML-Connector-Simple-Workflow)
- ライセンス：BSD-3-Clause
- 元の著作権表示：Copyright (c) 2024, The MathWorks, Inc.
- [元のライセンス全文](https://github.com/mathworks/JP-SysML-Connector-Simple-Workflow/blob/8ba839ff36f370a42da16ef35f8981e24e2354b0/license.txt)
- ファイル比較に用いたコミット：[`8ba839ff36f370a42da16ef35f8981e24e2354b0`](https://github.com/mathworks/JP-SysML-Connector-Simple-Workflow/commit/8ba839ff36f370a42da16ef35f8981e24e2354b0)
- 比較日：2026-10-24

上記コミットは公開準備時に比較した参照版です。過去に最初にコピーしたコミットを特定したものではありません。

## ファイルの対応

| 本リポジトリの配置 | 参照元の配置 | 利用内容 |
| --- | --- | --- |
| `SysMLImport/SystemModels/` | `SystemModels/` | インポート元のSysMLデータ（XML・MDZIP） |
| `SysMLImport/SysMLArchModel/` | `SysMLArchModel/` | アーキテクチャ、コンポーネント、入力、要求、テスト、プロジェクト定義 |
| `SimDrivenReqRefinement/` のプロジェクト | `SysMLArchModel/` | 要求具体化の演習用に変更したプロジェクト |
| `SimDrivenReqRefinement/SimDrivenReqRefinement_ans/` | `SysMLArchModel/` | 要求具体化の解答用に変更したプロジェクト |
| `SECURITY.md` | `SECURITY.md` | MathWorksの脆弱性報告先の案内 |

各プロジェクト内の `license.txt` は元のライセンス全文を保持しています。ルートの [LICENSE](LICENSE) の第1節には追加教材・独自変更部分の利用条件、第2節には参照元に適用されるBSD-3-Clauseの全文を記載しています。

## 演習での追加・変更

日本語・英語の演習資料（`SystemComposer_exercise*.pdf`、`SystemComposer_exercise*.pptx`）を追加し、シミュレーション結果から要求を具体化して再検証する演習と解答を用意しています。資料には `© 2026 by The MathWorks, Inc.` の表示があります。

日本語・英語のREADMEで使用する画像は、演習作成者から提供されたSimulink Testマネージャーのスクリーンショットです。改善前の元ファイルは `スクリーンショット 2026-10-24 020930.png`、改善後の元ファイルは `スクリーンショット 2026-10-24 021059.png` です。元画像はいずれも2884 × 1666のPNGです。

要求具体化の演習ストーリーは、鎌谷氏からいただいた「既存要求を満たした後も、シミュレーションで不足要求に気づき、要求・テスト・設計へ反映して再検証する」という助言を基にしています。

生成物を除く既存ファイルを上記参照版と比較した結果、`SysMLImport/` の123ファイルは一致しました。以下は参照元の同じ相対パスのファイルと内容が異なります。

| プロジェクト | 異なるファイル |
| --- | --- |
| `SimDrivenReqRefinement/` | `ElectricThrottleControl.slx` |
| 同上 | `Simulink Model/ThrottleValveController.slx` |
| 同上 | `TestFile/TestManagerFile.mldatx` |
| `SimDrivenReqRefinement/SimDrivenReqRefinement_ans/` | `ElectricThrottleControl.slx` |
| 同上 | `SysMLArchModel_REQ.slreqx` |
| 同上 | `Simulink Model/ThrottleValveController.slx` |
| 同上 | `TestFile/TestManagerFile.mldatx` |
| 同上 | `TestFile/TestManagerFile~mldatx.slmx` |

この表は公開準備時のバイト比較に基づくもので、モデルの意味的な差分や各変更の作成者を確定するものではありません。公開準備で追加したREADME、Git設定、空フォルダー維持用ファイルは比較対象に含めていません。

## 再配布時の表記

参照元由来の内容を再配布する場合は、元の著作権表示、BSD-3-Clauseの条件、免責条項を保持してください。ソース以外の形式で再配布する場合も、同梱文書などに必要な表記を含めてください。追加教材・独自変更部分の利用・再配布には、[LICENSE](LICENSE)の第1節が適用されます。許可された範囲でプロジェクトや資料を配布する際は、該当するライセンスと出典の説明も添付してください。

参照元・貢献者の名前を、許可なく派生製品の推奨・宣伝に使用することはできません。正確な条件は [LICENSE](LICENSE) および各プロジェクトの `license.txt` を参照してください。
