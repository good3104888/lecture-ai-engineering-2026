# 第3回 解答

## 演習

- 第1回（素のLLM）とエージェントの回答の違い：エージェントは用語集を検索し、講座固有の情報を根拠に回答した。
- `--trace` で見えたツール呼び出し（ツール名と引数）：`search_glossary(query='LoRA')`、`search_glossary(query='QLoRA')`、`make_quiz(lecture=2)`。
- 1つの質問での LLM 呼び出し回数（`requests`）：比較質問・確認問題ともに2回。
- 追加したツールと、docstring に書いた説明：`make_quiz`。「指定した回の復習用の確認問題を1問作る」。登録・呼び出しを確認し、テスト12件に合格した。

## 宿題

- 取り組んだレベル：基礎
- やったこと：INSTRUCTIONSの回答言語を英語、繁体字中国語に変更し、同じ日本語の質問で比較した。
- 結果：回答は指定言語に変わった。全条件でLoRA・QLoRAを別々に検索し、`tool_calls=2`、`requests=2`だった。
- 気づき・疑問：検索方法を保ったまま、指示だけで回答言語を変更できた。各条件1回の確認なので、ほかの質問でも同様になるか確かめたい。中国語では、（低ランク行列）のみ日本語で記述された。

■英語
The main differences between LoRA and QLoRA are as follows:

- **LoRA (Low-Rank Adaptation):** Keeps the pre-trained model weights frozen in their original precision (e.g., 16-bit) and trains only small low-rank matrices to update the model. This drastically reduces the number of parameters to train.
- **QLoRA (Quantized LoRA):** Takes LoRA a step further by quantizing the base model weights to 4-bit precision to save even more GPU memory, while still training with LoRA. This allows you to fine-tune much larger models on hardware with limited resources.

(Related Lecture: Lecture 2)

■中国語
LoRA 與 QLoRA 的主要區別在於：

* **LoRA**：保持預訓練模型的權重不變，透過引入並訓練兩個低階矩陣（低ランク行列）來記錄權重更新量。這能大幅減少需要訓練的參數數量，並縮小模型儲存空間。
* **QLoRA**：在 LoRA 的基礎上，將基礎模型的權重進行量化（例如量化為 4 位元），以此進一步節省記憶體，讓較小的 GPU 也能訓練更大的模型。

相關回數：第2回