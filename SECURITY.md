# セキュリティポリシー

> **English:** Please report security vulnerabilities privately via **Security → Report a vulnerability** on the affected repository. Do not open public issues, pull requests, or discussions for them. Reports in English are welcome.

## 脆弱性の報告

脆弱性を見つけたら、**公開の Issue、PR、Discussions には書かずに**、GitHub の非公開の脆弱性報告を使ってください。

1. 対象のリポジトリ（[sendo](https://github.com/sendo-feed/sendo/security/advisories/new)、[sendo-reader](https://github.com/sendo-feed/sendo-reader/security/advisories/new)）の **Security** タブを開く
2. **Report a vulnerability** から報告する

報告には、次のことを書いてください。

- 対象のリポジトリと、コミットまたはバージョン
- 再現の手順（できれば最小の例）
- 想定される影響（何ができてしまうか）
- 修正の案があれば、その内容

## 対応

いまは2人で開発しているので、対応はできる範囲で行います。

- 受け取ったことを、7 日以内を目安に返信する
- 修正したら、GitHub Security Advisory で公開する。報告してくれた方の名前を載せてよいかは、事前に確かめる
- 修正が公開されるまでは、内容を公にしないようお願いします

## 対象

- sendo と sendo-reader の `main` ブランチ。まだリリースはないので、サポートするのは `main` だけ
- 依存しているパッケージそのものの脆弱性は、そのパッケージの提供元に報告してください。Sendo に影響する場合は、こちらにも知らせてもらえると助かります
- 各自がホストしている環境の設定の誤りは対象外です

Sendo は外部の URL を取得し、外部から来た記事の本文を扱います。特に、SSRF、記事本文を経由した XSS やプロンプトインジェクション、API トークンや認証まわりの問題の報告を歓迎します。
