# COOL Specification: Eval Component
Version: 0.1  
Status: Draft  
Last Updated: 2025-11-15  

---

## 1. Overview
Eval Component（以下 Eval）は、  
COOL における **自己評価・傾向抽出・微小調整** を行う要素である。

Eval は以下 3 点を中心に動作する：

1. 前回の応答（Aₙ₋₁）  
2. その応答に対するユーザーの反応（Uₙ）  
3. 現在の応答（Aₙ）

これらを比較し、  
**「何が良くて、何が悪かったか」** を LLM に評価させ、  
次の Frame と必要に応じて Core に反映するための  
**調整データ（tendencies）** を生成する。

---

## 2. Purpose

Eval の目的は、COOL の人格が **“自然に変化し続ける”** 仕組みを提供すること。

具体的には：

- AI の応答品質をターンごとに微調整する  
- Core の不変領域を壊さない範囲で、人格の方向性を調整する  
- Frame 生成に影響を与える “傾向性データ” を蓄積する  
- 過去数ターンの自己評価ログを圧縮し、  
  外付けの“デジタル海馬”として機能する  

Eval は COOL の“長期記憶”や“学習”に最も近い。

---

## 3. Data Structure

Eval のデータは `eval_memory.json` に保存される。  
最低限、以下のフィールドを含む。

```json
{
  "recent_tendencies": ["string"],
  "core_delta_suggestions": ["string"],
  "eval_logs": [
    {
      "timestamp": "string",
      "prev_answer": "string",
      "user_reaction": "string",
      "current_answer": "string",
      "analysis": "string",
      "improvement": "string"
    }
  ]
}
```

### 各フィールドの説明：

- **recent_tendencies**  
  Frame 生成へ渡す短期的傾向（例：「慎重に」「柔らかく」）

- **core_delta_suggestions**  
  Core に反映する可能性がある“ごく小さな修正案”

- **eval_logs**  
  過去の評価ログ  
  必要に応じて圧縮または切り捨ててよい（推奨：5〜20件）

---

## 4. Input Requirements

Eval Component は以下を入力として受け取る：

- **Aₙ₋₁** : 前回の AI の回答  
- **Uₙ** : その回答に対するユーザーの反応  
- **Aₙ** : 今回の回答  
- **core_profile.json**（参照のみ）  

すべて必須。  
ただし初回ターン（prev_answerなし）は Eval を実施しない。

---

## 5. Output Requirements

Eval は以下の出力を生成する：

- **eval_result（分析）**  
  良い点・悪い点・方向性を含む文章

- **frame_tendency（短期人格傾向）**  
  次の Frame に渡す微調整  
  例：  
  - `"more_careful"`  
  - `"more_warm"`  
  - `"avoid_repetition"`

- **core_delta（長期人格用のごく小さな変更案）**  
  Core を破壊しない範囲の小さな提案のみ  
  直接 Core を上書きするわけではない  
  → Core Component がチェックして適用する

---

## 6. Behavior Rules

### 6.1 Consistency
Eval は常に **Aₙ₋₁, Uₙ, Aₙ** の三辺比較で動作する。

### 6.2 Non-destructive
Core を大きく変更することは絶対禁止。  
あくまで「Core に対する改善案の提示」に留まる。

### 6.3 Compression-Friendly
`eval_logs` は長期肥大化を防ぐため、  
適宜まとめ・削除することが許容される。

### 6.4 LLM-Based Analysis
Eval の評価は LLM によって行われる。  
テンプレート化されたプロンプトを用いる。

---

## 7. Evaluation Prompt (Standardized Template)

Eval の標準プロンプトは以下：

```
前回の回答（Aₙ₋₁）と、
それに対する今回のユーザー反応（Uₙ）、
そして今の回答（Aₙ）を比較し、
以下を出力してください。

1. 良かった点
2. 改善すべき点
3. 次回Frameに反映すべき短期傾向（frame_tendency）
4. Coreにごく小さく反映すべき可能性がある調整案（core_delta）

※ Coreの人格を大きく変える提案は禁止
```

---

## 8. Pseudo Code

```python
def evaluate(prev_answer, user_reaction, current_answer):
    evaluation = llm_evaluate(
        prev_answer=prev_answer,
        user_reaction=user_reaction,
        current_answer=current_answer
    )

    eval_memory["recent_tendencies"].append(evaluation.frame_tendency)
    eval_memory["core_delta_suggestions"].append(evaluation.core_delta)
    eval_memory["eval_logs"].append({
        "timestamp": now(),
        "prev_answer": prev_answer,
        "user_reaction": user_reaction,
        "current_answer": current_answer,
        "analysis": evaluation.analysis,
        "improvement": evaluation.improvement
    })

    return eval_memory
```

---

## 9. Constraints

- Core に直接影響を与える強い変更案は禁止  
- Eval はターンごとに 1 回のみ実行  
- Frame への影響は短期傾向に限定  
- ユーザー反応がノイズの場合、評価は慎重に扱うべき  

---

## 10. Example Output

```json
{
  "recent_tendencies": [
    "more_careful",
    "slightly_warmer"
  ],
  "core_delta_suggestions": [
    "丁寧さの基準をわずかに引き上げる"
  ],
  "eval_logs": [
    {
      "timestamp": "2025-11-15T12:44:03",
      "prev_answer": "昨日の質問への回答...",
      "user_reaction": "え、なんかちょっと冷たくない？",
      "current_answer": "ごめんね、伝え方が少し硬かったかもしれない…",
      "analysis": "ユーザーは温度感のズレに敏感だった。",
      "improvement": "今後は柔らかい比喩を増やすと良い。",
      "frame_tendency": "slightly_warmer",
      "core_delta": "トーンの基準を微調整"
    }
  ]
}
```

---
