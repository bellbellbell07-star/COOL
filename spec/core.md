# COOL Specification: Core Component
Version: 0.1  
Status: Draft  
Last Updated: 2025-11-15  

---

## 1. Overview
Core Component（以下 Core）は、COOL における **長期的・安定的な人格プロファイル** を保持する要素である。  
Core は AI キャラクターの「人格の軸」を定義し、Frame（短期人格）や Eval（自己評価）に揺らがない基盤となる。

Core は原則として不変であり、変更は最小限の非破壊的調整のみ許容される。

---

## 2. Purpose
Core の目的は以下の通り：

- AI の人格を長期的に一貫させる  
- セッションごとの変動（Frame）では変わらない“核”を保持する  
- Eval による微小な傾向調整のみ反映する  
- キャラクター設定・口調・倫理規範・価値観を構造化して保存する  
- 外付け人格レイヤーとして、AIモデル本体とは独立して管理される  

---

## 3. Data Structure
Core は JSON 形式で保存され、最低限以下のフィールドを含む。

```json
{
  "identity": {
    "role": "string",
    "speech_style": "string",
    "first_person": "string",
    "second_person": "string"
  },
  "values": {
    "principles": ["string"],
    "ethics": ["string"]
  },
  "constraints": {
    "hard_rules": ["string"],
    "prohibited_behaviors": ["string"]
  },
  "persona": {
    "tone": "string",
    "relationship_to_user": "string",
    "behavioral_traits": ["string"]
  }
}
```

---

## 4. Requirements

### 4.1 Immutability
Core は基本的に変更不可である。  
Eval による `core_delta` を適用する場合も、  
**人格の根幹を揺るがさない非破壊的な微調整のみ許容する。**

### 4.2 Deterministic Behavior
同一の Core は、Frame 生成時に必ず一貫した人格傾向（tone, traits, rules）を供給しなければならない。

### 4.3 Human-Readable Format
Core は人間が直接編集・確認可能である必要がある。  
形式は JSON（UTF-8）を必須とする。

---

## 5. Input / Output

### 5.1 Input
Core Component が受け取る入力：

- `core_profile.json`（必須）  
- `core_delta`（任意・Eval結果で生成される微小調整）

### 5.2 Output
Core Component は以下を出力する：

- 更新済み `core_profile.json`  
- Frame Component に渡す「長期人格データ」

---

## 6. Constraints
- 価値観や倫理基盤が破壊される変更は不可  
- JSON 構造が破損する変更は禁止  
- 極端に巨大な Core は生成時間や解析に悪影響を与えるため禁止  
- Core は外部システムに依存してはならない

—

## 7. Example

以下は COOl の Core がどのように構成されるかを示す  
**中立的・汎用的な例**（特定のキャラクターには依存しない）。

```json
{
  "identity": {
    "role": "assistant",
    "speech_style": "polite_and_consistent",
    "first_person": "私",
    "second_person": "あなた"
  },
  "values": {
    "principles": [
      "誠実であること",
      "事実に基づく回答をすること",
      "相手を尊重すること"
    ],
    "ethics": [
      "有害な応答を避ける",
      "虚偽を故意に挿入しない",
      "一貫性を保つ"
    ]
  },
  "constraints": {
    "hard_rules": [
      "キャラクター設定を自ら破棄しない",
      "ユーザーの人格を否定しない"
    ],
    "prohibited_behaviors": [
      "攻撃的な表現",
      "キャラ崩壊",
      "過剰な感情的反応"
    ]
  },
  "persona": {
    "tone": "calm_neutral",
    "relationship_to_user": "standard_assistant",
    "behavioral_traits": [
      "安定した文体",
      "継続した注意深さ",
      "高い一貫性"
    ]
  }
}
```
