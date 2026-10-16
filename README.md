# S-AIR サイト（GitHub Pages 配布用）

このフォルダの中身をそのままリポジトリのルートに置くことを想定しています。

```
/
├── index.html        ← トップページ（「準備中です」）。検索エンジンには noindex を設定済み
├── robots.txt         ← サイト全体のクロールを禁止
└── preview/
    └── index.html     ← S-AIRサイト本体（レビュー用。これも noindex 設定済み）
```

## なぜこの構成か

- ルート（`/`）に直接アクセスしても「準備中です」とだけ表示され、本サイトの内容は見えません。
- 本サイトは `/preview/` 以下に置いてあるので、URLを知っている人だけがレビューできます。
- `robots.txt` と各ページの `<meta name="robots" content="noindex, nofollow">` で、検索エンジンへの掲載（SEO）をまだ行わないようにしています。

## デプロイ手順（GitHub Pages）

1. GitHub で新しいリポジトリを作成します（例: `s-air-site`）。Public / Private どちらでも可（Privateの場合はGitHub Pro以上が必要な場合があります）。
2. このフォルダの中身（`index.html` / `robots.txt` / `preview/` フォルダ）をリポジトリのルートにそのままアップロードします。
   - GitHub上の「Add file → Upload files」からドラッグ＆ドロップでもアップロード可能です。
   - `preview` フォルダごとアップロードすれば、`preview/index.html` の構造が保たれます。
3. リポジトリの **Settings → Pages** を開きます。
4. **Source** を「Deploy from a branch」にし、ブランチは `main`（または `master`）、フォルダは `/ (root)` を選択して **Save**。
5. 数分待つと、`https://<ユーザー名>.github.io/<リポジトリ名>/` でサイトが公開されます。
   - トップページ（`/`）→「準備中です」
   - 本サイト（`/preview/`）→ 実際のS‑AIRサイト

## 本公開（SEOに乗せる）時にやること

- `index.html` を本サイトの内容に差し替える（`preview/index.html` の中身をそのままルートに移動するのが簡単です）。
- `robots.txt` の `Disallow: /` を削除、または必要なパスだけ許可する内容に変更する。
- 各ページの `<meta name="robots" content="noindex, nofollow">` タグを削除する。
