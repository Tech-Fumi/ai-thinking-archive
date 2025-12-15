# ai-thinking-archive 開発ルール

## プロジェクト概要

AI との会話から蒸留された **思考資産** を公開するリポジトリ。

**このリポジトリは Public**

### システム全体での立ち位置

```
[D] ai-conversation-client
    - 会話の入口
    - raw 保存
        ↓
[B] ai-conversation-vault (Private)
    - マスキング
    - 要約
    - Gate 判定
        ↓ (human review)
[C] ai-thinking-archive ← このリポジトリ (Public)
    - 公開資産
```

## 責務

### やること（Must）

| 機能 | 説明 |
|------|------|
| 思考資産の公開 | vault からレビュー済みコンテンツを受け入れ |
| カテゴリ整理 | 設計決定、原則、アーキテクチャ等に分類 |
| 検索性確保 | タグ、front matter で整理 |

### やらないこと（Must NOT）

| 機能 | 理由 |
|------|------|
| raw ログの格納 | Private データは vault に留まる |
| 自動コミット | 必ず human review を経る |
| 機密情報の格納 | Public リポジトリのため |

## 構成

```
ai-thinking-archive/
├── design-decisions/     # 設計判断・アーキテクチャ決定
├── principles/           # 原則・哲学・考え方
├── frameworks/           # 思考フレームワーク・手法
├── architectures/        # システム構成・設計パターン
├── learnings/            # 学びの記録・振り返り
└── README.md
```

## 開発ルール

### コンテンツ受け入れ基準

vault から転送されるコンテンツは以下を満たすこと：

1. **マスキング済み** - 機密情報が除去されている
2. **要約/蒸留済み** - 生の会話ではなく、エッセンスが抽出されている
3. **human review 済み** - 人間が公開を承認している
4. **front matter 付き** - メタデータが整備されている

### Front Matter 形式

```yaml
---
title: "タイトル"
date: 2025-12-15
source: chatgpt | claude
topics:
  - topic1
  - topic2
publish_score: 0.8
reviewed: true
---
```

### 禁止事項

- raw/ からの直接コピー
- マスキングなしのコンテンツ
- 機密情報（API キー、個人情報、内部 URL 等）

## 命名規則

### ファイル名

```
{topic}_{YYYYMMDD}.md
例: fastapi-auth-design_20251215.md
```

### カテゴリ

- 英語小文字、ハイフン区切り
- 具体的で検索しやすい名前

## 運用

### コンテンツ追加フロー

1. vault の `ready-to-publish/` にファイルが移動される
2. human review で承認
3. vault の publisher.py が archive に転送
4. archive で commit & push

### メンテナンス

- 定期的な README 更新（コンテンツ一覧）
- タグの整理・統合
- 古いコンテンツの整理（必要に応じて）

## 注意事項

- **Public リポジトリ** - 全世界から閲覧可能
- コミット前に機密情報がないか必ず確認
- 疑わしい場合は公開しない
