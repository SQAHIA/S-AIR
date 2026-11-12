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

## 複数ページ

- `/index.html` — HOME
- `/listen.html` — LISTEN / プレイヤー案内
- `/schedule.html` — SCHEDULE / `schedule.json` 読込
- `/channels.html` — CHANNELS / 4チャンネル
- `/about.html` — ABOUT / プロジェクト記録

英語ページは `/en/` 配下にあります。

- `/en/index.html`
- `/en/listen.html`
- `/en/schedule.html`
- `/en/channels.html`
- `/en/about.html`

ページ右上の `EN` / `JP` から切り替えできます。

## 独立ドメインについて

S-AIRはSQAHIA Digital本体とは別リポジトリ・別Pagesプロジェクトとして運用します。現時点の確認用URLは `https://sqahia.github.io/S-AIR/` です。独自ドメインを割り当てる場合は、取得済みのドメイン名を決めた後、リポジトリルートにそのドメインを記載した `CNAME` ファイルを追加し、ドメイン側にGitHub PagesのDNSレコードを設定します。ドメイン名が未確定のため、CNAMEはまだ追加していません。

各ページに `noindex, nofollow` を設定しています。

## GitHub Pagesを有効化して公開URLを確認する手順

1. GitHubで [SQAHIA/S-AIR Settings](https://github.com/SQAHIA/S-AIR/settings) を開きます。
2. 左メニューの **Pages** を開きます。
3. **Build and deployment → Source** で **GitHub Actions** を選択します。
4. `main` へpush済みの `Deploy S-AIR to GitHub Pages` ワークフローを開き、**Run workflow** を押すか、次のpushで自動実行します。
5. Actionsが緑色で完了したら、Actionsのデプロイ結果、またはPages画面上部に表示される **Visit site** を開きます。
6. 通常のURLは `https://sqahia.github.io/S-AIR/` です。ページは `https://sqahia.github.io/S-AIR/listen.html` のように確認できます。

リポジトリがPrivateの場合、GitHubアカウントのプランによってPages公開が制限されます。Pages設定やActionsで `Resource not accessible by integration` が出る場合は、リポジトリをPublicにするか、Pagesを利用できるプランへ変更し、再度 **Source: GitHub Actions** を保存してください。

## 放送サーバー連携

現時点ではブラウザから設定したURLを直接再生します。AzuraCast APIの秘密トークンをフロントエンドへ置かないため、AzuraCast連携、管理画面、認証付きSchedule APIはバックエンド分離後に接続してください。未設定の音声や存在しないAPIを完成済みとは表示しません。
