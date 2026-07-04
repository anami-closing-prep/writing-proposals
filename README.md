# writing-proposals

AI Driven School 第5ヶ月目の月次課題 — 自分専用の提案スキルを作る作業場。

## この作業場でやること

配布された `writing-proposals` スキルを自分の業務に合わせてチューニングし、
AIによる「一発出し」で提案文を作成する。

提出物は「図解の公開URL」のみ。図解には以下の4点を入れる：

1. 想定した相手と変えたいこと
2. チューニング前のスキルで作成した提案文
3. チューニング後のスキルでAIによる一発出しした提案文
4. 工夫したポイントと苦戦したポイント

## フォルダ構成

```
writing-proposals/
├── .claude/
│   └── skills/
│       └── writing-proposals/       ← 提案スキル本体（配布ファイルを配置する）
│           ├── SKILL.md             ← AIへの指示書。ここをチューニングする
│           └── references/
│               ├── examples.md      ← 自分が作った模範回答（ステップ③で作成）
│               └── output-quality.md ← 出力品質チェックリスト（配布ファイル）
├── output/
│   ├── before-tuning.md             ← チューニング前の提案文（消さない）
│   └── after-tuning.md              ← チューニング後の提案文（提出用）
├── CLAUDE.md                        ← Cursor向けの作業ガイド
└── README.md                        ← この説明書
```

## 始め方

1. ADS ポータルから配布スキル（`writing-proposals`）をダウンロードする
2. ダウンロードした `SKILL.md` を `.claude/skills/writing-proposals/` に配置する
3. CLAUDE.md の「進め方 6ステップ」に沿って作業を進める

## 関連リポジトリ

| リポジトリ | 用途 |
|-----------|------|
| `personal-visual-explainers` | ステップ⑥の図解作成・Surgeデプロイ |
| `closing-prep-app` | 別の課題（太陽光・蓄電池の商談準備ツール）|
