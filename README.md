# ai-thinking-archive

AI との会話から蒸留された **思考資産** のアーカイブ。

## このリポジトリに含まれるもの

- 設計判断（Design Decisions）
- 原則・哲学（Principles）
- アーキテクチャ（Architectures）
- 思考フレームワーク（Frameworks）
- 学びの記録（Learnings）

## このリポジトリに含まれないもの

- 生の会話ログ
- 個人情報
- API キー・機密情報
- 未整理のドラフト

## 構成

```
ai-thinking-archive/
├── design-decisions/     # 設計判断・アーキテクチャ決定
├── principles/           # 原則・哲学・考え方
├── frameworks/           # 思考フレームワーク・手法
├── architectures/        # システム構成・設計パターン
└── learnings/            # 学びの記録・振り返り
```

## Philosophy

**Clarity over completeness.**

結論と再利用可能な洞察のみを保存する。

## 関連リポジトリ

```
[D] ai-conversation-client (Private)
    - 会話の入口
    - raw 保存
        ↓
[B] ai-conversation-vault (Private)
    - マスキング
    - 要約
    - Gate 判定
        ↓ (human review)
[C] ai-thinking-archive (Public) ← このリポジトリ
    - 公開資産
```
