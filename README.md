# 自転車タイヤ・チューブ サイズ換算＆適合診断ツール 公開パッケージ

GitHub Pages にそのままアップロードして公開するための一式です。すべて単独で動作する静的ファイルで、外部リソース（CDN・外部フォント等）は使っていません。

## ファイル構成

| ファイル | 内容 |
|---|---|
| `index.html` | ツール本体（表記／ETRTOから換算・適合チューブ・買い間違い警告） |
| `guide.html` | 解説ページ（表記の読み方・買い間違いパターン・チューブとバルブの選び方） |
| `sitemap.xml` | 検索エンジン向けサイトマップ |
| `robots.txt` | クローラー向け設定（sitemap の場所を通知） |
| `README.md` | このファイル |
| `BUILD_NOTES.md` | 制作メモ（データ出典・テスト結果・残課題）※公開しなくてもよい |

## 公開手順（GitHub Pages）

1. GitHub にログインし、新しいリポジトリを作成する（名前は `bicycle-tire` を推奨。Public にする）
2. このフォルダのファイルをすべてリポジトリ直下にアップロードする（`Add file` → `Upload files`）
3. リポジトリの `Settings` → `Pages` を開く
4. `Build and deployment` の Source で `Deploy from a branch` を選び、Branch は `main` / `(root)` にして `Save`
5. 数分待つと `https://mini-tools-lab.github.io/bicycle-tire/` で公開される（`mini-tools-lab` は自分の GitHub ユーザー名）

### URL について

ファイル内の URL は `https://mini-tools-lab.github.io/bicycle-tire/` で書いてあります。自分のユーザー名が異なる場合は、次のファイル内の `mini-tools-lab` を置き換えてください。

- `index.html` の canonical / og:url
- `guide.html` の canonical / og:url
- `sitemap.xml` と `robots.txt` の URL

### 公開後にやること（別途対応）

- GA4 測定タグの埋め込み（割り勘ツールと同じ測定IDを使うかは公開時に判断）
- Google Search Console へのプロパティ追加と sitemap 送信

## 後から独自ドメインを設定するときの注意

- GitHub 側： `Settings` → `Pages` → `Custom domain` にドメインを入力すると、リポジトリに `CNAME` ファイルが自動で作られる（このファイルは消さないこと）
- DNS 側： サブドメイン（例 `tire.example.com`）なら `CNAME` レコードで `mini-tools-lab.github.io` を向ける。ルートドメインの場合は GitHub 公式ドキュメントの A / ALIAS レコード設定に従う
- HTTPS： DNS が反映されると Let's Encrypt の証明書が自動発行される。`Enforce HTTPS` にチェックが入るようになってから有効化する（反映まで最大で1日程度かかることがある）
- URL の差し替え： ドメインを付けたら、上記ファイル内の URL（canonical・og:url・sitemap・robots）を **新しいドメインの URL にすべて差し替える**。古い `github.io` の URL が残っていると、検索エンジンが旧URLを正として扱うことがある
- Search Console 等に旧 URL で登録していた場合は、新ドメインで登録し直す
