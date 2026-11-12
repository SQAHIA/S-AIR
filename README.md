# S-AIR Official Website

SQAHIA DIGITAL Across-the-border Internet Radio のGitHub Pages向け静的サイトです。

## 現在の実装

- ダークネイビー／シアン／パープルのレスポンシブUI
- Legends / Rookies / BGM / Indaily の4チャンネル切替
- 実ストリームURLをチャンネル別・PCM/FLAC別にブラウザへ保存
- HTML5 Audioによる実音声再生、音量、ミュート、接続状態・エラー表示
- `schedule.json` を外部データソースとして読み込むJST番組表
- 現在実装・準備中・将来計画を分離した表示

## GitHub Pages

`.github/workflows/pages.yml` が `main` へのpush時にPagesへデプロイします。リポジトリの Settings → Pages で Source を **GitHub Actions** にしてください。初回のみ、リポジトリ権限の都合でPages有効化が必要な場合があります。

## 検索エンジン非表示

公開時点ではSEOを開始しない方針です。以下を意図的に設定しています。

- `index.html`: `noindex, nofollow, noarchive, nosnippet`
- `googlebot`: `noindex, nofollow, noarchive, nosnippet`
- `robots.txt`: 全クローラーに対して `Disallow: /`
- sitemap.xml は配置していません

GitHub PagesはHTTPの `X-Robots-Tag` ヘッダーを自由に設定できないため、メタタグとrobots.txtによる非表示です。将来SEOを開始するときは、メタタグ、robots.txt、sitemapの方針を同時に変更してください。

## 放送サーバー連携

現時点ではブラウザから設定したURLを直接再生します。AzuraCast APIの秘密トークンをフロントエンドへ置かないため、AzuraCast連携、管理画面、認証付きSchedule APIはバックエンド分離後に接続してください。未設定の音声や存在しないAPIを完成済みとは表示しません。
