# Writing Proposals — 提案スキルのチューニング作業場

AI Driven School 第5ヶ月目の月次課題。配布された `writing-proposals` スキルを
自分の業務に合わせてチューニングし、AIによる一発出しで提案文を作成する。

## 課題のゴール

- 自分の業務に合わせてチューニングした提案スキルが手元にある
- そのスキルでAIによる一発出しをした提案文が手元にある
- チューニング前後の提案文と工夫・苦戦ポイントをまとめた図解の公開URLを提出済み

## フォルダ構成

| パス | 説明 |
|------|------|
| `.claude/skills/writing-proposals/SKILL.md` | 提案スキル本体。ここをチューニングする |
| `.claude/skills/writing-proposals/references/examples.md` | 模範回答（ステップ③で作成・追加する） |
| `.claude/skills/writing-proposals/references/output-quality.md` | 出力品質チェックリスト（配布ファイル） |
| `output/before-tuning.md` | ステップ②: 配布スキルそのままで出した提案文（絶対に消さない） |
| `output/after-tuning.md` | ステップ⑤: チューニング後スキルで一発出しした提案文 |

## 課題の2つのルール（必ず守る）

**ルール①: AIによる一発出し**
提案文はAIによる一発出しで作る。AIと何度もやり取りして文章を磨き上げるのではなく、
スキルを用いたアウトプットをそのまま提出物に使う。
（材料を集めるやり取りや、スキルの質問に答える対話はこのルールの対象外）

**ルール②: 手作業の文章修正は禁止**
提出する提案文は、タイピングや音声入力で手作業で書き換えるのは禁止。
気になる箇所があれば、提案スキルやAIに渡すコンテキストを整理・修正して、
もう一度最初から実行する。

## 進め方（6ステップ）

```
ステップ① 変えたいことを1つ決める
         ↓
ステップ② 配布スキルをそのまま使い提案文を出力 → output/before-tuning.md に保存（消さない）
         ↓
ステップ③ AIに渡す模範回答を作る → references/examples.md に保存
         ↓
ステップ④ スキル本体（SKILL.md）をチューニングする
         ↓
ステップ⑤ チューニング済みスキルで提案文を一発出し → output/after-tuning.md に保存
         ↓
ステップ⑥ 図解にまとめてSurgeにデプロイ → URLを提出
```

## ステップ⑥の図解作成について

図解は **このリポジトリではなく** `personal-visual-explainers` で作成する。

```bash
cd ~/src/personal-visual-explainers
# creating-visual-explainers スキルを使って図解を生成
```

## 講義参照

- 第9回講義文字起こし: `~/src/講義/第9回講義_文字起こし.md`（追加予定）
- ADS講義索引: `~/.claude/skills/ai-driven-school-lectures/references/index.md`
- 課題の詳細: ADS ポータルの「第5ヶ月目 自分専用の提案スキルを作る」

## やらないこと

- 出力した提案文をタイピング・音声で手直しする
- `output/before-tuning.md` を削除・上書きする（チューニング前後の比較が提出物に必要）
- 図解HTMLをこのリポジトリで作成する（`personal-visual-explainers` が担当）
