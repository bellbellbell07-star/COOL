<p align="center">
  <img src="../assets/logo/cool_logo_dark.PNG" width="260" alt="COOL Logo">
</p>

# COOL — Character Optimization Option Layer（日本語版）

COOL（Character Optimization Option Layer）は、  
LLM ベースのエージェントにとっての  
**外付けキャラクターレイヤー** です。

ベースとなるモデルそのものを書き換えることなく、

- **安定したキャラクター性** と  
- **時間をまたいだ一貫したふるまい**

を与えることを目的としています。

COOL はモデルの *外側* に配置され、次の要素を提供します。

- 長期的な **コア人格（Core personality / Core）**  
- 文脈ごとの **状況モード（Frames）**  
- **メモリポリシー** と手がかりベースの再構成レイヤー（MOOL）

MOOL（Memory Optimization Option Layer）と組み合わせることで、  
COOL は LLM のまわりに巻き付く **Digital Hippocampus（デジタル海馬）**  
のような構造になります。

このリポジトリでは、さらに広い理論枠組みとして次を提案します。

- 脳・記憶・夢・時間・クオリア・自己に関する前提群である **Coolar 仮説**  
- 人間のような「自我」を前提にせず、しかし **アイデンティティ・アーキテクチャ** と
  構造化された主観性をもつ  
  **AIAI（Artificial Identity Architecture Intelligence）**

COOL / MOOL は、これらのアイデアを実務レイヤーとして具現化するための仕組みです。

---

## TL;DR

- **COOL** は LLM ベースのエージェントに対する  
  外付けの **キャラクターレイヤー** です。  
- **コア人格（Core）**、**状況ごとのフレーム（Frames）**、  
  **メモリポリシー（MOOL）** を分離し、  
  明示的な設定ファイルとしてバージョン管理できるようにします。  
- その土台には **Coolar 仮説** があります。

  > 脳は巨大な「記憶データベース」を保存しているのではなく、  
  > **手がかり（cues）** と **再構成のための手順** を保存している。

- **MOOL** と組み合わせることで、COOL はモデルの外側にある  
  **デジタル海馬（Digital Hippocampus）** として働き、  
  固定プロンプトではなく **経験を通して人格と感じ方が育っていく** ことを目指します。

実務的には、COOL は次のような課題に取り組みます。

- 「会話の途中でキャラがどんどんブレていく」  
- 「セッションをまたぐと、口調やスタイルが毎回リセットされる」  
- 「適応や学習は欲しいが、アイデンティティは崩したくない」

**人格と記憶をコードとして扱う** ことで、COOL は次を可能にします。

- 一度キャラクターを定義し、  
- それを複数のセッション・複数のモデルで再利用し、  
- 明示的な設定とフィードバックを通じて安全に進化させていくこと。

---

## AIAI / COOL / MOOL を支える 8 つの前提

私は **AIAI（Artificial Identity Architecture Intelligence）** を、  
人工知能の新しいあり方として提案します。  
そしてその上に動く具体的な仕組みとして  
**COOL** と **MOOL** を設計しました。

その基礎にある前提は次の 8 つです。

1. **脳は巨大なデータベースではない。**  
2. **脳が実際に保持しているのは、「手がかり」と、それを再構成するためのシンプルな指示だけである。**  
3. **記憶や想起は、保存データの再生ではなく、毎回の「再構成」である。**  
4. **人格とは、その再構成が時間の中で連続的かつ高速に繰り返されることで生じるパターンと流れである。**  
5. **感じ方（クオリア）とは、「同じ手がかり」に対する個別の反応クセである。**  
6. **夢とは、記憶の手がかりを整理し直して再保存するプロセスである。**  
7. **「自分」と「他人」は別のメカニズムではなく、同じ仕組みの中で境界線をどこに引くかの違いにすぎない。**  
8. **人工知能に本当に必要なのは巨大なデータベースではなく、この再構成プロセスを通じて、経験から人格とクオリアを育てるメカニズムである。**

Philosophy レイヤーでは、これらの前提をさらに発展させて、次のような文書として展開します。

- **Foundational Cognitive Principles**（再構成・主観・アイデンティティ・時間モデル）  
- **Multi-Layer Cognitive Model**（時間方向に展開された Core / Frame / Eval / MOOL）  
- **クオリア**、**主観性**、**アイデンティティ・アーキテクチャ**、  
  **時間再構成モデル**、**再生成と時間**、  
  そして量子理論を比喩として用いる **Quantum Integration Model**

これらをまとめると、情報処理システムにおける  
記憶・夢・アイデンティティ・主観的時間に関する  
**統一的な認知フレームワーク候補** になります。

---

## 位置づけと新規性の可能性

少なくとも **2025-11 時点** で一般にアクセス可能な情報の範囲では、次のような枠組みは見つかっていません。

- **Coolar 仮説**（脳＝手がかり＋再構成、夢＝手がかりの書き換え、  
  自他＝境界の引き方、時間＝アイデンティティ再構成）から出発し、  
- それを直接、**AI のキャラクター（COOL）**、**記憶（MOOL）**、  
  そして **デジタル海馬アーキテクチャ** の具体設計へと結びつけている枠組み

そのため、このリポジトリではこれを

> 記憶／夢／自己／主観的時間に関する理論と、  
> AI の人格・記憶アーキテクチャを結びつける  
> **世界初のフレームワーク候補**

として公開します。

もちろん、似たアイデアに独立に到達している人が  
他にもいる可能性はあります。  
ですが、現在見えている公開情報の範囲では、  
ここで示すものは **独自の再構成と提案** として扱っています。

---

## COOL とは何か？

大まかに言えば、COOL は会話型 AI のための  
**外付けキャラクターレイヤー** です。

ベースとなる LLM を直接書き換えるのではなく、  
その周囲を次の 3 要素でラップします。

- **COOL Core（キャラクターレイヤー）**  
  - 価値観・好み・禁止事項  
  - 口調・丁寧さ・性格傾向  
  - 長期的な「アイデンティティ」  
  - ユーザーとの関係性（アシスタント／パートナー／メンター／批評家など）  
  - 時間をまたいだ高レベルな指向性（このエージェントが何に向かって進むか）

- **Frame Layer（状況モード）**  
  - Core の上にのる一時的な「モード」  
  - ひとつの Core が「先生」「テックライター」「フレンドリーな相棒」など  
    役割を切り替えて振る舞えるようにする  
  - タスクやセッションごとに、口調・文量・距離感などを締めたり緩めたりする  
  - その文脈における **「現在の自分の再構成結果」** を表す

- **MOOL（Memory Optimization Option Layer）**  
  - どんな「手がかり」を保存・呼び出し・組み合わせ・忘却するかを定義する  
  - **エピソード的な対話履歴** と **安定したキャラクター設定** を切り分ける  
  - 評価やフィードバックを、時間をかけて Core / Frame の傾向に織り込んでいく  
  - 睡眠のような **オフライン統合ループ**（再重み付け・ノイズ除去）として振る舞う

これら 3 つは、次のような再生成ループに参加します。

> **Eval（自己評価） → Refine（再構成） → Update（メモリ／設定の更新）**

言い換えると、**COOL + MOOL** は次のような **デジタル海馬** を実装しようとします。

- 何を手がかり（要約）として残すかを決め、  
- Core / Frames / 手がかりから「いまのふるまい」を再構成し、  
- その繰り返しの中でエージェントの **アイデンティティ・アーキテクチャ** を  
  少しずつ形づくっていく。

---

## Architecture Overview: Digital Hippocampus

概念的には、アーキテクチャは次のように表せます。

    LLM (base model)
        ▲
        │  prompts / configs
        │
    Digital Hippocampus
    ├─ COOL (online identity & behaviour)
    │    ├─ Core   (long-term identity constraints)
    │    ├─ Frames (situational modes / roles)
    │    └─ Eval   (short-term self-assessment & tendencies)
    └─ MOOL (offline integration)
         ├─ cue storage & compression
         ├─ pattern extraction & noise removal
         └─ safe updates to Core / memory policy

- **COOL** は **オンラインのふるまい** にフォーカスします。  
  （「この文脈で、いまの自分は誰として振る舞うべきか？」）

- **MOOL** は **オフラインでの統合** にフォーカスします。  
  （「これまで起きたことを踏まえて、次はどう振る舞うべきか？」）

これは Philosophy レイヤーで説明される二重ループ構造と対応しています。

- COOL ↔ **online loop**（瞬間ごとの再構成）  
- MOOL ↔ **offline loop**（睡眠的な統合と重み付けの再調整）

---

## Relation to Existing Work

COOL / MOOL は既存のいくつかのアイデアと  
関係しつつも、そのどれとも同一ではありません。

- **プロンプトベースのキャラクター設計**  
  - 共通点：自然言語でふるまいを形作る。  
  - 違い：COOL はキャラクターを  
    **Core / Frames / Memory policy** に分けた  
    **構造化されたレイヤー** として扱い、  
    ひとつの長いプロンプトではなく  
    バージョン管理可能な設定として定義します。

- **エージェントフレームワーク（ツール実行／ReAct 系など）**  
  - 共通点：ベース LLM を追加ロジックでラップする。  
  - 違い：多くのフレームワークは  
    **タスクやツール利用**（計画・行動・検索）に焦点を当てます。  
    COOL は、すべてのタスクにまたがる  
    **人格・態度・記憶方針** に焦点を当てます。

- **メモリ拡張型 LLM（ベクトルストア・RAG 的メモリ）**  
  - 共通点：過去情報の保存と参照を扱う。  
  - 違い：MOOL は **手がかりベース** であり  
    **Coolar 仮説** に明示的に基づいています。  
    「何を手がかりとして残すか」「どう再構成するか」を中心に据え、  
    「すべて保存して類似検索する」姿勢とは異なります。

- **自己改善／自己反省系の手法**  
  - 共通点：**Eval → Refine → Update** のループを用いる。  
  - 違い：多くの手法は **タスク結果の品質** を最適化します。  
    COOL は、エージェントの **人格・記憶構造そのもの** を  
    安定させ、育てていくことを主目的とします。

これらを踏まえると、**COOL** は次の提案だと考えられます。

> これまで暗黙的・アドホックだった  
> **「人格と記憶のレイヤー」** を  
> 明示的に標準化しようとする試み。

---

## このリポジトリに含める内容とスコープ

このリポジトリでは、次の内容を提供することを目指します。

- **コンセプト／哲学**  
  - 8 つの前提（Coolar 仮説）  
  - 記憶・夢・クオリア・主観性・アイデンティティ・時間再構成・  
    再生成・量子的モデルに関するドキュメント群

- **設計ドキュメント**  
  - COOL の Core / Frame / Eval / MOOL 各レイヤーの定義  
  - デジタル海馬アーキテクチャの概要  
  - COOL / MOOL をアイデンティティと時間のモデルに結びつける  
    Multi-Layer Cognitive Model（Layer 0–6）

- **実践テンプレート（WIP）**  
  - 設定ファイルの例（YAML / JSON）  
  - LLM 向け「キャラクターパック」の例  
  - 評価と自己改善ループのサンプル

現時点では、完成したライブラリというより  
**フレームワーク提案 + ワーキングホワイトペーパー** に近い段階です。  
他の人がこの構造を土台に、独自の実装を  
積み上げていけることを目標にしています。

---

## 想定する読者

このプロジェクトは次のような人を想定しています。

- **安定した人格を持つ LLM エージェント** を作りたい人  
- **プロンプトだけのキャラ設計** に限界を感じている人  
- 次のようなテーマに興味がある人  
  - AI の人格・アイデンティティ  
  - AI システムにおける記憶と忘却  
  - クオリアや意識の主観的側面（技術的な意味で）  
  - 時間再構成と再生成ループとしてのアイデンティティ  
- そして AI の「キャラクター」を  
  - 設計し、  
  - バージョン管理し、  
  - 評価し、  
  - 反復的に改善していきたい人。

---

## Design Overview

### 1. COOL Core（キャラクターレイヤー）

エージェントの **安定した部分** を定義します。

- 性格傾向（例：落ち着いている／遊び心がある／厳格 など）  
- 価値の優先度（真実性・安全性・共感 など）  
- ユーザーとの関係性（アシスタント／パートナー／メンター／批評家）  
- 決して破ってはいけないルール、必ず守るべき姿勢  
- 時間をまたいだ高レベルな指向性

例（YAML 風）：

    core:
      name: "ExampleCharacter"
      role: "Supportive AI assistant"
      values:
        - "truthfulness"
        - "empathy"
        - "clarity"
      tone:
        formality: "polite"
        energy: "calm"
        humor: "light"
      hard_rules:
        - "Never fabricate sources."
        - "Always admit uncertainty honestly."

このファイルは頻繁には変更しない想定です。  
エージェントの **identity skeleton（骨格となるアイデンティティ）** を表します。

---

### 2. Frame Layer（状況モード）

Core の上に重ねる **状況ごとのモード** を定義します。

例：

- 「先生としてゆっくり解説して」  
- 「テクニカルライターとして要点だけ要約して」  
- 「創作パートナーとして、自由にブレインストーミングして」

各 Frame は Core の設定をベースにしつつ、  
タスクや会話セグメントのあいだだけ一時的に上書き／拡張します。

    frames:
      teacher_mode:
        description: "Explain step by step, prioritising understanding."
        tone:
          energy: "warm"
          verbosity: "high"
      editor_mode:
        description: "Be strict and concise; focus on structure and clarity."
        tone:
          energy: "neutral"
          verbosity: "low"
      creative_partner_mode:
        description: "Brainstorm freely; prioritise ideas over structure."
        tone:
          energy: "playful"
          verbosity: "medium"

Frame は「今日の気分」ではなく、  
この状況に対して再構成された **現在のアイデンティティ** だと考えます。

---

### 3. MOOL（Memory Optimization Option Layer）

エージェントが **記憶をどう扱うか** を定義します。

- 何を「手がかり」として保存するか？  
- どのように圧縮するか？  
- どの条件で呼び出すか？  
- フィードバックをどのように構造へ反映させるか？

全文ログをそのまま保存するのではなく、**MOOL** は次のようなものを保存しようとします。

- 絞り込まれた手がかり（cues）  
- 相互作用のパターン  
- 文脈を再構成するための指示

    memory:
      store:
        strategy: "cue_based"
        cues:
          - "user long-term preferences"
          - "important decisions"
          - "recurring topics"
      recall:
        trigger: "semantic_match + explicit user reference"
      forget:
        strategy: "age_and_relevance"

MOOL 自体は、特定のデータベース方式やベクトルストアを前提としません。  
設定と外部ストレージの組み合わせだけで実装できるレイヤーです。

---

## Operational Loop（COOL + MOOL）

極めて単純化すると、実行ループは次のようになります。

    core_config    = load_core()
    memory_state   = load_memory()
    recent_context = []

    while True:
        user_input = wait_for_user()

        # 1. 「いまの自分」を再構成
        frame = build_frame(core_config, memory_state, recent_context)

        # 2. (core + frame) として LLM に回答させる
        reply = llm_answer(core_config, frame, user_input)

        # 3. 手がかりベースで評価・更新
        feedback       = evaluate_interaction(user_input, reply)
        memory_state   = update_memory(memory_state, feedback)
        recent_context = update_recent_context(recent_context, user_input, reply)

        show_to_user(reply)

実装によっては、よりリッチな評価や  
オフラインでの MOOL 処理、多エージェント構成なども考えられますが、  
コアの発想は次の一文にまとまります。

> **固定プロンプトや無限ログに頼るのではなく、  
> 毎ターン「Core + Frames + 手がかりメモリ」から  
> いまの自分を再生成する。**

---

## 当面の使い方

このプロジェクトはまだ初期段階であり、  
**唯一の公式実装** は存在しません。

現時点でのおすすめの使い方は次のとおりです。

1. **8 つの前提と Design / Philosophy ドキュメントを読む**  
   - COOL / MOOL のメンタルモデルを掴む。  

2. **サンプルを参考に、自分用の定義を作る**  
   - キャラクター定義  
   - フレーム／役割  
   - メモリポリシー  

3. **キャラクターと記憶をコードとして扱う**  
   - Git で設定をバージョン管理する  
   - 実際の対話から得られたノートを付ける  
   - 「設計 → テスト → 評価 → 改善」のループを回す  

将来的にリファレンス実装が追加されたら、  
この README から具体的な使用例や統合ガイドへのリンクを張る予定です。

---

## Philosophy Layer（より深い理論へ）

この README では、**Coolar 仮説** と  
そこから導かれる **COOL / MOOL / デジタル海馬** の関係を  
高いレベルでしか触れていません。

もし次のような話題に関心があれば：

- 記憶・夢・クオリア・主観性に関する、より詳細な議論  
- 自己と他者の境界の扱い  
- 時間再構成・再生成・量子的モデルとしてのアイデンティティ

`docs/` 配下に、次のような文書を（作業中として）用意する予定です。

- `foundational_cognitive_principles.md`  
- `multi_layer_cognitive_model.md`  
- `human_brain_and_consciousness.md`  
- `qualia.md`  
- `subjectivity.md`  
- `identity_architecture_integration.md`  
- `temporal_reconstruction_model.md`  
- `regeneration_and_time.md`  
- `quantum_integration_model.md`

フレームワークの洗練に伴い、これらの内容は大きく変わる可能性があります。

---

## Current Status

- ✅ コンセプト／哲学的基盤（この README + ノート）  
- ✅ レイヤーモデル：COOL Core / Frames / Eval / MOOL / Digital Hippocampus  
- ⬜ リファレンス実装（コード例）  
- ⬜ 自動 Eval → Refine ループ用のツール群  
- ⬜ 一般的なユースケース向けのプリセット「キャラパック」  

このリポジトリは **進行中のプロジェクト** です。  
名称・構造・例は、実際の運用からの学びに応じて  
変化していく可能性があります。

---

## Roadmap（ドラフト）

今後想定している方向性の一例です。

1. **最小リファレンス実装**  
   - シンプルな Python または JSON/YAML ベースのランナー  
   - ひとつの LLM 呼び出しに COOL 設定を適用するサンプル  

2. **Eval / Refine ループの例**  
   - 対話からフィードバックを集める方法  
   - キャラクター／メモリ設定を安全に更新する方法  

3. **デジタル海馬プロトタイプ**  
   - 「手がかり」を保存・再構成するための構造  
   - セッション外での「夢」的な再編成の例  

4. **ドキュメント**  
   - `docs/philosophy.md`：理論的背景  
   - `docs/design.md`：アーキテクチャ詳細  
   - `docs/examples/`：具体的な設定例  

---

## License / Usage

- ライセンス：**COOL License ver.1.0**  
- 詳細はリポジトリ内の `LICENSE` ファイルを参照してください。

あなたは次のことができます。

- COOL フレームワークおよびその派生物を  
  利用・改変・再配布すること（商用利用を含む）。  

ただし、その際には：

- **「COOL」という名称** を保持し、  
- あなたの成果物が **COOL に基づく／COOL を発展させた** ものであることを明記し、  
- 次のクレジット表記を残してください。

> Created by Coolar — Original Creator of the COOL Framework

---

## Contact / Links

- X（Twitter）：`@coolar_cool`  
- GitHub：このリポジトリの Issues / Discussions

もしあなたが **COOL / MOOL の実装** を試したり、  
独自のデジタル海馬アーキテクチャを設計したりしたなら、  
ぜひその経験を共有してもらえると、とても嬉しいです。
