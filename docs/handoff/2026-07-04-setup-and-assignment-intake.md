# セッション引き継ぎ — セットアップ完了・課題資料の取り込み待ち

**日付:** 2026-07-04
**前トークルーム:** closing-prep-app のチャット（このリポジトリのセットアップ作業を行った）
**このファイルの使い方:** 新しいトークルームの最初のメッセージで `@このファイル` を添付する。

---

## 目的

AI Driven School 第5ヶ月目の月次課題「自分専用の提案スキルを作る」を進めるための
作業場（`writing-proposals` リポジトリ）をセットアップした。次のセッションでは、
課題資料（スクリーンショット・第9回講義文字起こし）を取り込み、テキスト化して
恒久的に参照できる状態にすることがゴール。

---

## 完了したこと

- `~/src/writing-proposals/` にリポジトリを新規作成
- GitHub リポジトリ作成・プッシュ済み（`https://github.com/anami-closing-prep/writing-proposals`）
- フォルダ構成を作成済み:
  - `.claude/skills/writing-proposals/SKILL.md`（配布ファイル待ちのプレースホルダー）
  - `.claude/skills/writing-proposals/references/examples.md`（模範回答テンプレート）
  - `.claude/skills/writing-proposals/references/output-quality.md`（配布ファイル待ちのプレースホルダー）
  - `output/before-tuning.md`（ステップ②の保存先テンプレート）
  - `output/after-tuning.md`（ステップ⑤の保存先テンプレート）
  - `docs/assignment.md`（課題詳細の書き起こし先。**まだ空の目次のみ**）
  - `docs/references/ads-lectures.md`（講義索引。closing-prep-app の同名ファイルと同じ設計パターン）
- `CLAUDE.md` / `README.md` を作成済み（課題のゴール・2つのルール・6ステップの進め方を記載）

---

## 未解決・バグ・ブロッカー

- **最初に送信された講義スクリーンショット（15〜20枚）の実ファイルが見つからなかった。**
  `~/.cursor/projects/Users-takahisaanami-src-closing-prep-app/assets/` を確認したが、
  該当ファイルが存在しなかった（別のチャット環境に紐づいていた可能性がある）。
  → **このセッションで再送してもらう必要がある。**
- 第9回講義の文字起こしも同様に未着手（テキストとして受け取り、`~/src/講義/第9回講義_文字起こし.md` に保存する）。
- ADS ポータルからの提案スキル本体（`SKILL.md` / `output-quality.md`）はまだダウンロード・配置されていない。

---

## 重要な決定

- **画像は「常に読み込まれる」形で保存できない**（Cursorが自動的に読み込むのはテキストファイルのみ）。
  そのため、スクリーンショットの内容は画像のまま置くのではなく、**テキストとして書き起こして
  `docs/assignment.md` に保存する**方針にした。
- 第9回講義の文字起こしは、このリポジトリの中ではなく `~/src/講義/第9回講義_文字起こし.md` に保存する。
  理由: 講義の正本フォルダは `~/src/講義/` に統一されており、`ai-driven-school-lectures` スキルが
  そこだけを参照する設計になっているため（closing-prep-app と同じ運用ルールに揃える）。
- 図解作成（ステップ⑥）はこのリポジトリでは行わず、`personal-visual-explainers` リポジトリで行う。

---

## 次にやること（優先順）

### 1. 今すぐやること
1. 講義スクリーンショット（15〜20枚）をこのチャットに再送してもらう
   → 受け取ったら `docs/assignment.md` に全文を書き起こして保存する
2. 第9回講義の文字起こしをテキストで受け取る
   → `~/src/講義/第9回講義_文字起こし.md` に保存する
3. ADS ポータルから提案スキルをダウンロードしてもらう
   → `SKILL.md` を `.claude/skills/writing-proposals/SKILL.md` に配置
   → `output-quality.md` を `.claude/skills/writing-proposals/references/output-quality.md` に配置

### 2. スキル配置後にやること
4. スキルの動作確認（チャット欄で「提案文を作って」と入力し、質問が返ってくるか確認）
5. ステップ①: 変えたいことを1つ決める
6. ステップ②: 配布スキルをそのまま使って提案文を出力 → `output/before-tuning.md` に貼り付ける（消さない）

### 3. やっておくと後で楽になること
7. `grill-me` スキル（`~/.claude/skills/grill-me/SKILL.md`）を使って、
   「利用目的・想定する相手・コンテキスト」の3点を整理する（第5回グループセッションの事前準備そのもの）
8. Surpriseルール（配布済みなら）を `references/` に置いておく

---

## 関連ファイル・コマンド

| 種別 | 内容 |
|------|------|
| ファイル | `CLAUDE.md`、`docs/assignment.md`、`docs/references/ads-lectures.md` |
| コマンド | なし（ダウンロード・貼り付け待ち） |
| 参照ドキュメント | `CLAUDE.md`（このリポジトリの正本） |
| GitHubリポジトリ | https://github.com/anami-closing-prep/writing-proposals |

---

## 新トークルーム用・最初の1メッセージ（コピペ用）

```text
@docs/handoff/2026-07-04-setup-and-assignment-intake.md を読んで、
前セッションの続きから作業してください。

まず「理解した続きの要点」を3行で返してから、以下を行ってください。

1. これから送る講義スクリーンショット（15〜20枚）を読み込んで、
   docs/assignment.md に全文を書き起こして保存する
2. これから送る第9回講義の文字起こしを ~/src/講義/第9回講義_文字起こし.md に保存する
3. 保存が終わったら、引き継ぎファイルの「次にやること」の2番以降に進む
```

---

## 意図的に捨てたもの（任意）

- 最初に貼られたスクリーンショットの実ファイルは見つからなかったため、
  「元のファイルパスから直接読み込む」というアプローチは断念した。再送を前提にする。
