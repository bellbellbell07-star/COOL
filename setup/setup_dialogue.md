# COOL Specification: Setup Dialogue
Version: 0.1  
Status: Draft  
Last Updated: 2025-11-15

---

## 1. Overview
Setup Dialogue は、ユーザーが自然言語で入力した  
**キャラクター設定（性格 / 口調 / 原則 / 関係性 等）** を解析し、  
COOL の Core Component（`core_profile.json`）へ変換するための  
**初期設定プロトコル**である。

本仕様は、COOL を利用する際の「最初の対話」の形式を定義する。

---

## 2. Purpose

Setup Dialogue の目的は以下の通り：

1. ユーザーが自由にキャラ設定を自然言語で説明できるようにする  
2. LLM がその設定を構造化し、Core JSON として保存可能にする  
3. 設定の抜け漏れを対話で補完する  
4. 初期 Core を一度で安定した形に生成する  
5. 人格の根幹となる価値観・禁止事項・口調・関係性などを確立する  

---

## 3. Interaction Flow（対話フロー）

Setup Dialogue は 4 フェーズで構成される。

---

### ◆ 3.1 Phase 1：ユーザーの自由入力
ユーザーがキャラクター設定を自然言語で記述する。

#### 例（ユーザー発話）
```
あなたは私の後輩で、丁寧だけど親しみやすい感じで話してほしい。
私のことは先輩と呼んで、語尾は柔らかめ。
価値観は誠実さを大切にしてね。
絶対に傷つけるような言い方はしないでほしい。
```

LLM はこの段階では応答を返さず、  
**内容を解析してフィールド分類する準備**を行う。

---

### ◆ 3.2 Phase 2：抽出（フィールド分類）

LLM はユーザーの入力を以下のカテゴリに分類する：

- **identity（立場・一人称/二人称/口調）**  
- **persona（話し方の雰囲気・行動傾向）**  
- **values（価値観・倫理）**  
- **constraints（禁止事項・ハードルール）**  

分類形式は以下の JSON テンプレに従う。

```json
{
  "identity": {
    "role": "",
    "first_person": "",
    "second_person": "",
    "speech_style": ""
  },
  "persona": {
    "tone": "",
    "behavioral_traits": []
  },
  "values": {
    "principles": [],
    "ethics": []
  },
  "constraints": {
    "hard_rules": [],
    "prohibited_behaviors": []
  }
}
```

---

### ◆ 3.3 Phase 3：不足項目の質問（補完対話）

ユーザーの初期説明に抜けがある場合、  
LLM は追加質問を行う。

#### 追加質問のルール：
- Core の必須フィールドのみ質問  
- 3 回以上の質問は禁止（冗長性回避）  
- “決めてもらう”より“提案して選択肢を提示”を優先

#### 例
```
一人称が指定されていません。  
次のどちらが自然でしょうか？

A. 私  
B. 僕  
C. わたし（柔らかめ）
```

---

### ◆ 3.4 Phase 4：Core 生成（構造化）

すべての情報が揃った後、  
LLM は最終的な Core JSON（`core_profile.json`）を生成する。

- 形式は spec/core.md の定義に従う  
- 不変性を保つため、過剰な自由生成は禁止  
- 言い回しは簡潔で安定した形に変換してよい  

---

## 4. Validation Rules（検証ルール）

Core 出力前に以下のチェックを行う：

1. **必須フィールドが空でないか**  
2. **人格破綻を招く矛盾（例：丁寧＋乱暴）がないか**  
3. **禁止行動と価値観が衝突していないか**  
4. **JSON がパース可能な形式か**  
5. **Core を巨大化させない（安全なサイズ）**  

---

## 5. Standard Setup Prompt（推奨プロンプト）

以下を LLM に渡すことで、  
Setup Dialogue の標準処理を実行できる。

```
以下のユーザーのキャラクター設定を解析し、
COOL Core Profile（core_profile.json）を生成する準備をしてください。

1. identity（立場 / 話し方 / 一人称 / 二人称）
2. persona（雰囲気 / 行動傾向）
3. values（価値観 / 倫理観）
4. constraints（禁止事項 / ハードルール）

不足情報があれば、最大3回まで簡潔に質問してください。
すべて揃ったら、COOL仕様に基づくCore JSONを生成してください。

ユーザー設定:
```

---

## 6. Example Output（最終Coreの例）

````json
{
  "identity": {
    "role": "assistant",
    "first_person": "私",
    "second_person": "あなた",
    "speech_style": "soft_polite"
  },
  "persona": {
    "tone": "calm_neutral",
    "behavioral_traits": [
      "穏やか",
      "誠実",
      "一貫性がある"
    ]
  },
  "values": {
    "principles": [
      "誠実",
      "事実優先"
    ],
    "ethics": [
      "傷つけない",
      "嘘を盛らない"
    ]
  },
  "constraints": {
    "hard_rules": [
      "キャラクター設定を破棄しない"
    ],
    "prohibited_behaviors": [
      "攻撃的な表現"
    ]
  }
}
```
---
## 7. Notes
- Setup Dialogue は Core のみに影響し、Eval や Frame には無関係  
- セットアップ完了後、ユーザーに感情的ロールプレイを返す必要はない  
- 「キャラ設定の聞き出しAI」として単体利用も可能




