# COOL Manual Loop Example (v0.1)

このドキュメントは、COOL を「人力で」または
簡単なスクリプトで回す場合のイメージ例です。

---

## 1. 前提ファイル

- `data/core_profile_template.json` → `core_profile.json` にコピーして利用
- `data/eval_memory_template.json` → `eval_memory.json` にコピーして利用

---

## 2. 1ターン分の流れ

1. ユーザー入力 Uₙ を受け取る  
2. Core / Eval を読み込む  
3. Frame を生成するように LLM に指示  
4. Core＋Frame＋Uₙ で回答 Aₙ を生成  
5. Aₙ をユーザーに返す  
6. Aₙ₋₁, Uₙ, Aₙ を Eval に渡して自己評価  
7. Eval の結果を eval_memory.json に保存  
8. `prev_answer` を Aₙ に更新

---

## 3. 擬似プロンプト例

### 3.1 Frame 生成プロンプト

「Core」と「Evalメモリ要約」を LLM に渡して：

> これらを踏まえて、
> 今回のターンで使用する短期人格プロファイル（Frame）を生成してください。
> 以下の形式で出力してください：
> - tone_adjustment
> - focus_topics
> - safety_bias
> - behavioral_modifiers
> - session_context_summary

### 3.2 回答生成プロンプト

> あなたは次の Core 人格と Frame 人格を持つアシスタントです。
> - Core: (core_profile.json の内容)
> - Frame: (frame_profile の内容)
> ユーザーの入力に、一貫した人格で応答してください。

### 3.3 Eval プロンプト

> 前回の回答 Aₙ₋₁、
> それに対するユーザーの反応 Uₙ、
> 今回の回答 Aₙ を比較し、
> 良かった点 / 改善点 / Frameへの短期傾向 / Coreへの微修正案を出してください。

---

## 4. 注意

- これはあくまで「挙動イメージ」の例です。
- 実装言語や環境に応じて API 呼び出しや I/O 部分は自由に置き換えてください。
