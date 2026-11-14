# Sendo への貢献ガイド

sendo-feed のリポジトリ（[sendo](https://github.com/sendo-feed/sendo)、[sendo-reader](https://github.com/sendo-feed/sendo-reader)）に共通の決まりごと。

いまは Hiroki と Yuichi の2人で開発している。外部の方からの Issue や PR は、公開の準備ができてから受け付ける。

## 進め方

試作を繰り返し、一度決めたことでも気軽に変える。詳しくはインセプションデッキの[「12. 私たちの進め方」](https://github.com/sendo-feed/sendo/blob/main/docs/inception-deck.md)を参照。

## 言語

- 2人で開発している間は、文書、コミットメッセージ、PR、Issue を**日本語**で書く。
- 一般に公開するときに、文書の英語版を作る。それ以降は**英語版を正**とし、新しいコミットメッセージや PR も英語で書く。
- 公開前の日本語のコミットは、そのまま残す（履歴は書き換えない）。
- 識別子（変数名・関数名・ファイル名など）は最初から英語にする。

## コミットメッセージ

[Conventional Commits 1.0.0](https://www.conventionalcommits.org/ja/v1.0.0/) を土台にする。

```text
<type>(<scope>): <件名>

<本文：なぜ変えたか>

<フッター>
```

### type

| type | 使う場面 |
|---|---|
| `feat` | 機能の追加 |
| `fix` | 不具合の修正 |
| `docs` | 文書だけの変更（`docs/decisions/` を除く） |
| `decision` | 決定ファイル（`docs/decisions/`）の変更。scope にテーマ名を書く |
| `refactor` | 振る舞いを変えないコードの整理 |
| `perf` | 性能の改善 |
| `test` | テストの追加・修正 |
| `build` | ビルドや依存関係 |
| `ci` | CI の設定 |
| `chore` | 上のどれにも当てはまらない雑務 |
| `revert` | 以前のコミットの取り消し |

### 書き方

- scope は任意。変更した場所（`api`、`fetcher`、`sync` など）を書く。
- 件名は、何をしたかを短く書く。末尾に句点を付けない。
- 本文には「なぜ」を書く。「何を」は差分を見れば分かる。
- 互換性を壊す変更は、type の後ろに `!` を付け、フッターに `BREAKING CHANGE:` を書く。
- AI と一緒に書いたコミットは、フッターに `Co-Authored-By:` を残してよい。

### 決定ファイルの変更

決定は `docs/decisions/<テーマ>.md` にテーマごとに置き、今の決定だけを書く。経緯は git の履歴が持つので、**コミットメッセージが「なぜ変えたか」の唯一の置き場**になる（[決定の残し方](https://github.com/sendo-feed/sendo/blob/main/docs/decisions/documentation.md)）。

- 件名は `decision(<テーマ>): <何を決めたか>` にする。
- 本文には、何をなぜ変えたか、何と比べて選んだかを書く。
- 決定ファイルの変更は、できるだけコードの変更と分けて単独のコミットにする。

例：

```text
decision(tech-stack): 第1版を Cloudflare 前提にし、緩衝層を挟む

TypeScript ／ Go ／ Rust で迷っていたが、無料枠で運用費ゼロにでき、
Phase 1 を早く終えられる Cloudflare 前提を選んだ。移植の余地は、
固有の機能を src/platform/ に閉じ込めることで残す。

Go の単一バイナリは VPS には載せやすいが、Workers で動かず、
reader と言語が分かれるので見送った。
```

## プルリクエスト

- `main` へは PR を通してマージする。マージはスカッシュマージにする。
- スカッシュマージでは、PR のタイトルと説明がそのままコミットメッセージになる。そのため、**PR のタイトルは上のコミットメッセージの形式**で書き、説明には何をなぜ変えたかを書く。
- リポジトリの設定で、スカッシュマージの既定のメッセージを「Pull request title and description」にしておく。
- `main` の履歴は書き換えない（force push しない）。履歴が決定の経緯そのものになるため。
