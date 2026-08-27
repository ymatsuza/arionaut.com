# arionaut.com

アリオノート合同会社（ARIONAUT LLC）のコーポレートサイトとブランド資産。

- 本番: https://arionaut.com/ （GitHub Pages、`main` ブランチのルートを配信）
- ビルド工程なし。静的HTML/CSSのみ。

## 構成

```
index.html            トップページ
privacy.html          プライバシーポリシー
404.html              404ページ
CNAME                 GitHub Pages 独自ドメイン設定（arionaut.com）
.nojekyll             Jekyll 処理を無効化
robots.txt / sitemap.xml / site.webmanifest
assets/
  style.css           サイト共通CSS（index / privacy / 404 で共有）
  favicon.svg .ico    ファビコン
  apple-touch-icon.png / icon-192.png / icon-512.png
  ogp.png             OGP画像 1200×630
brand/
  logo-mark.svg           ロゴマーク（マスター・カラー）
  logo-mark-compact.svg   同上・スピードライン省略版（小サイズ用）
  logo-mark-white.svg     白抜き版（ダーク背景用）
  logo-lockup.svg         マーク＋ワードマークのロックアップ
  ogp.svg                 OGP画像のソース
  qr-navy.svg / .png      QRコード（https://arionaut.com/ 宛）
  png/                    ロゴ各種のPNG書き出し（SVGの4倍解像度・背景透過）
  namecard/               名刺入稿データ（HTML / PDF）
  BRAND.md                デザイントークン・使用ルール
docs/
  DNS.md                  独自ドメイン（お名前.com）の設定手順
  HANDOFF.md              ブランド立ち上げ時のハンドオフ資料（経緯・商標調査）
```

## ローカルでの確認

```bash
python3 -m http.server 8000
# http://localhost:8000/
```

`index.html` を直接ブラウザで開いても表示できるが、`site.webmanifest` などルート相対の
参照があるためローカルサーバー経由での確認を推奨する。

## デプロイ

`main` に push すると GitHub Pages が自動で反映する（数十秒〜数分）。

## 素材の再生成

```bash
# QRコード
python3 -c "import segno; segno.make('https://arionaut.com/', error='q').save('brand/qr-navy.svg', border=4, dark='#0c3a86', light='#ffffff', omitsize=True)"

# OGP画像（Montserrat が必要）
rsvg-convert -w 1200 -h 630 brand/ogp.svg -o assets/ogp.png

# ファビコン
for s in 180 192 512; do rsvg-convert -w $s -h $s assets/favicon.svg -o assets/icon-$s.png; done

# ロゴのPNG書き出し（Montserrat が必要。brew install --cask font-montserrat）
rsvg-convert -w 1200 -h 920  brand/logo-mark.svg         -o brand/png/logo-mark.png
rsvg-convert -w 1200 -h 920  brand/logo-mark-compact.svg -o brand/png/logo-mark-compact.png
rsvg-convert -w 1200 -h 920  brand/logo-mark-white.svg   -o brand/png/logo-mark-white.png
rsvg-convert -w 2224 -h 560  brand/logo-lockup.svg       -o brand/png/logo-lockup.png
rsvg-convert -w 2240 -h 1720 brand/logo-stack.svg        -o brand/png/logo-stack.png
```

## 確定事項（2026-08-24）

- **商号**: 「**アリオノート合同会社**」— カタカナ表記で登記する方針（英文 ARIONAUT LLC、ドメインと
  ロゴのワードマーク `ARIONAUT` は変更なし）
- **タグライン**: `EXPLORE, INNOVATE, DISCOVER`。ロゴからは商号表記を外し、タグラインに差し替えた
- **メール**: 問い合わせ先 `info@arionaut.com` / 名刺記載 `matsuzaki@arionaut.com`（2026-08-25 確定。Google Workspace で開設予定）
- **スローガン**: 「新しい“道”を拓く」で確定。PATHFINDER LABS 時代からの継承で、「航路」案は不採用
- **設立**: 2027年1月4日（予定）のまま据え置き
- **pf-labs.org**: 廃止する方針

## 未確定・TODO

- arionaut.com の **MXレコードが未設定**のため、`info@` / `matsuzaki@` とも現時点では受信できない。
  Google Workspace 側の設定後に MX を追加すること（→ `docs/DNS.md` §4）
- pf-labs.org の停止手順。**DNS レコードを先に削除してから** Pages / リポジトリを畳むこと
  （逆順だと dangling DNS で乗っ取られる。→ `docs/DNS.md` §5）
- 商標の**称呼検索は「アリオナウト」で実施済み**。読みを「アリオノート」に確定したため、
  J-PlatPat の称呼検索をこの読みで再実施すること
