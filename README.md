# hitohako-site

ひとはこさん（VTuber / 変身ヒロイン）のポートフォリオサイト。<https://hitohako.b0xp.io>

和風（桜・鳥居・和柄）× 90 年代レトロゲーム（ドット絵・DotGothic16・RPG/ADV 風ウィンドウ・CRT 風演出）。
配色は変身衣装に合わせた紫 × 金 × 桜ピンク。

## Stack

- [Astro](https://astro.build) 7 + [Tailwind CSS](https://tailwindcss.com) 4
- Node 22
- Cloudflare Pages（プロジェクト名 `boxp-hitohako`、`hitohako.b0xp.io`）

## Commands

| Command           | Action                               |
| :---------------- | :----------------------------------- |
| `npm install`     | 依存関係をインストール               |
| `npm run dev`     | 開発サーバー起動 `localhost:4321`    |
| `npm run build`   | `./dist/` に本番ビルド               |
| `npm run preview` | ビルド結果をローカルでプレビュー     |

## Deploy

`.github/workflows/deploy.yml` が `main` への push で `npm run build` → `wrangler pages deploy dist --project-name=boxp-hitohako` を実行する。
PR では build のみ実行し、wrangler は走らない（secrets 未参照による失敗を避けるため）。

事前に必要なもの:

- Cloudflare Pages プロジェクト `boxp-hitohako` と DNS: boxp/arch `terraform/cloudflare/b0xp.io/portfolio`（`cloudflare_pages_project.hitohako`）で管理。
- GitHub Actions secrets: `CLOUDFLARE_API_TOKEN`（Pages 編集権限）、`CLOUDFLARE_ACCOUNT_ID`。
- `--project-name` は Terraform 側の `boxp-hitohako` と必ず一致させる。

## Content

- `src/data/profile.json` … プロフィール（RPG ステータス画面）
- `src/data/allies.json` … 仲間（コハコ.exe / 鳴瀬理央 / 天城紗那）
- `src/data/stg.json` … STG 1CC 記録・挑戦中
- `src/data/links.json` … リンク
- `public/pixel/` … ドット絵（`scripts/make-tiles.py` で和柄タイルを生成、キャラクターは generate-pixelart で制作）

掲載内容は「ひとはこさんバース」設定の公開可能範囲のみ。正体に関わる情報や NSFW 要素は掲載しない。

## Credits

- アイコン・ヒーローイメージ（YouTube）: nagaren さん
- フォント: [DotGothic16](https://fonts.google.com/specimen/DotGothic16)（SIL OFL 1.1）
