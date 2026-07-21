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

## Cursor / Claude Code の情報共有アーキテクチャ（2026-07-21 明文化）

このリポジトリは Cursor と Claude Code の両方から同時に開発する前提で構成している。情報の置き場所は3層に分かれており、**Layer A の正本を増やさないこと**が全体の一貫性を保つ唯一の条件。

| Layer | 内容 | 正本 | 両ツールでの扱い |
|-------|------|------|------------------|
| A: プロジェクト共有知識 | 作業ルール・スキル | この `CLAUDE.md`（root）と `.claude/skills/` | Cursorは `CLAUDE.md` を `AGENTS.md` と同等に、`alwaysApply` 設定に関わらず全会話に適用する（[Cursor Docs: Rules](https://cursor.com/help/customization/rules)）。`.claude/skills/` もCursor/Claude Code双方が互換読み込みする（[Cursor Docs: Agent Skills](https://cursor.com/docs/skills)）。**つまりこの2つは既に単一の正本で完全に同一内容**。 |
| B: ツール運用設定 | `.claude/settings.local.json`（個人の許可設定） | Claude Code側のみ | 情報ではなく個人のツール設定なので非対称でよい。Gitでは常に除外する |
| C: 個人のUser Rules | Cursor Settings > Rules のグローバル項目 | （このリポジトリの範囲外） | 現状Claude Codeからは見えない。対応する場合は `~/.cursor/rules/` と `~/.claude/CLAUDE.md` 側で扱う、別タスク |

**やらないこと**: Layer A に `AGENTS.md` を新設しない。Cursorは既に `CLAUDE.md` を `AGENTS.md` と同格で読むため、追加すると「2ファイルの同期」という新たな非対称の火種を生むだけ（Claude Codeは `AGENTS.md` をnativeに読まない。[Claude Code Docs: Memory](https://code.claude.com/docs/en/memory) のAGENTS.md節を参照）。新しいプロジェクト知識を追記する場所に迷ったら、必ずこの `CLAUDE.md` か `.claude/skills/writing-proposals/references/` に置く。

**読み込みの確認方法**:
- Cursor: このリポジトリで新規チャットを開き、`writing-proposals` スキルと本ファイルの内容がルールとして認識されているか確認する
- Claude Code: このリポジトリで `claude` を起動し、`/context` コマンドで Memory files 一覧に `CLAUDE.md` と `.claude/skills/writing-proposals` が含まれているか確認する

## スキルの正本について（2026-07-12 明文化）

`writing-proposals` スキルの**実体は本リポジトリの `.claude/skills/writing-proposals/` の1つだけ**。`~/.claude/skills/writing-proposals` はここへの**シンボリックリンク**（2026-07-04 作成）であり、どちらのパスから見ても常に同一内容になる。

- チューニング期間中（課題提出まで）はこの構成のまま、本リポジトリ側で編集・コミットする
- **課題提出後の昇格手順**: `~/.claude/skills/writing-proposals` のシンボリックリンクを実体コピーに置き換えて `~/.claude` の Git 管理下に入れ、以後は `~/.claude` 側が正本。本リポジトリ側は提出物スナップショットとして凍結する（編集しない）
- **クライアント事実（`references/clients/`）の追記・更新は、昇格後は必ず `~/.claude` 側だけに行う**。事実が2箇所で食い違うと、古い決裁構造を前提にした提案文が生成される

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

図解は **このリポジトリの `output/` に** 作成する。`creating-visual-explainers` スキルはユーザーレベル（`~/.claude/skills/creating-visual-explainers/`）にあり、どのプロジェクトからでも同じスキル・テンプレート・公開スクリプトを使えるため、別リポジトリに移動する必要はない。

チャット欄で「チューニング前後の提案文を図解して」のように依頼する。

> **補足（2026-07-05訂正）**：以前は `personal-visual-explainers` で作る方針にしていたが、実際にはそのリポジトリは**別の月次課題（自分専用の図解スキルを作る課題）専用のワークスペース**であり、まだパーソナル版のスキルも作られていなかった（配布ままの汎用スキルしかない状態）。図解スキル自体がプロジェクトを問わず動く設計なので、今月の提出物一式（提案文・スキル・図解）はこのリポジトリにまとめる方針に変更した。

## 参照ドキュメント（作業開始前に読む）

| ファイル | 役割 |
|---------|------|
| [docs/assignment.md](docs/assignment.md) | 今月の課題の正本。ポータルのスクリーンショットを書き起こしたもの |
| [docs/references/ads-lectures.md](docs/references/ads-lectures.md) | 第9回講義など、関連する講義文字起こしへの索引 |

矛盾したら **docs/assignment.md がこのリポジトリ内では正**。講義は考え方の参照用。

## 講義参照

- 第9回講義文字起こし: `~/src/講義/第9回講義_文字起こし.md`
- ADS講義索引: `~/.claude/skills/ai-driven-school-lectures/references/index.md`
- 課題の詳細: ADS ポータルの「第5ヶ月目 自分専用の提案スキルを作る」

## やらないこと

- 出力した提案文をタイピング・音声で手直しする
- `output/before-tuning.md` を削除・上書きする（チューニング前後の比較が提出物に必要）

## 現在の最優先ワークストリーム（2026-07-22引き継ぎ）

コンサル料改定交渉の完遂支援と、writing-presentations スキルのチューニング課題。
状態の正本は docs/handoff/ の最新ファイル。毎セッション最初にそれを読む。

## 絶対ルール

- 提出用の提案文・プレゼン原稿は「AIによる一発出し」。出力後の手直し禁止。
  直す場合はスキルまたは docs/materials/ の材料を直して最初から再実行
- エピソードの創作禁止。docs/materials/ にある本人の実話のみ使う
- 公開物（図解・提出物）は実名・社名・院名を匿名化。本番原稿のみ実名可
- 数字は docs/materials/ の確定値のみ使用。未照合の数字（仮置きと明記された
  もの）は対外文書に使わない
- セッション終了時は docs/handoff/ に後継版の引き継ぎを必ず作成して commit

## 進め方

- Claude Code が段取りを主導する。ユーザーには「1問ずつ」確認し、
  まとめて質問攻めにしない。承認を得てから実行する
