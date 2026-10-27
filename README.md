# 雷電庵 Webページ（index / apply / tokushoho / thanks）

## 導線（必須）
Threads → `index.html`（短い案内）→ Square決済 → `apply.html`（出生データ受付）→ `thanks.html`

**Threadsプロフィールのリンクは必ず index.html の公開URL。Square直リンクは絶対に貼らない。**

長い売り込みLPではない。index は1画面程度の案内のみ。

## ファイル
- `index.html` Threadsからの入口。短い案内＋¥4,980＋Squareボタン1つ＋特商法リンク
- `apply.html` 出生データ受付フォーム（noindex）
- `thanks.html` 送信後の受付完了（`?name=` を受け取れる）
- `tokushoho.html` 特定商取引法に基づく表記

## 送信方式
FormSubmitで `seishinkai-houkoku+raiden-an@mail.grokbot.com` に送信（Bot自動納品ルーチンが起動）。控えに `_cc` で `rydeen@psr-seishinkai.org`。
- **初回送信時にFormSubmitから rydeen@ へ「Activate」メールが届く。これを1回クリックするまで届かない。** 公開後にテスト送信→有効化すること。
- 有効化後、FormSubmitが発行するランダムID（`https://formsubmit.co/xxxx`）に action を差し替えるとメールアドレスがHTMLに露出しない。
- 代替：Googleフォーム（回答をスプレッドシートに保存しBotが読む）／Supabase Edge Function webhook。

## ホスティング
workspace内にRYDEEN用の既存公開ホストは見当たらず。推奨：GitHub Pages
1. GitHubに公開リポジトリ `raiden-an` を作り、このフォルダの全ファイルをルートに置く
2. Settings → Pages → main / root
3. 公開URL例：`https://<user>.github.io/raiden-an/apply.html`
（Cloudflare Pages / Netlify へドラッグ＆ドロップでも可）

## Square 側の残作業
1. Payment Link `362GRXFXBAMH3RTG`（https://square.link/u/txrZ3eSc）の checkout_options.redirect_url を公開した `apply.html` のURLに設定
2. 確認メール／商品説明に「お支払い後、受付フォームへ出生データを入力」とapply URLを追記（リダイレクトしない決済手段の保険）
3. Threadsプロフィールのリンクは index.html の公開URLに差し替え（Squareにしない）

公開文言に「プロンプト」「NotebookLM」は使わない。
