# Arionaut ブランドガイド

商号: **Arionaut合同会社** / 英文 **ARIONAUT LLC**
由来: Arion（神話の駿馬）＋ Astronaut / Aeronaut。「宇宙の深淵を旅し、まだ地図にない航路を拓く探検家」。

## カラー

| トークン | HEX | 用途 |
|---|---|---|
| `--navy` | `#0c3a86` | ロゴグラデ始点、見出し |
| `--mid` | `#1b62c0` | リンク、サブ見出し |
| `--cyan` | `#48a3ec` | グラデ終点、ダーク背景上のアクセント |
| `--orange` | `#ef8f27` | 四芒星、セクション見出しの罫線 |
| `--ink` | `#1f2933` | 本文 |
| `--muted` | `#616e7c` | 補足テキスト |
| `--bg` | `#f7f9fb` | 淡背景 |
| `--line` | `#dfe5ec` | 罫線・枠 |

- ダーク背景: radial `#12315f` → `#0a1f42` → `#071734`、フッター単色 `#071734`
- 星グラデ: `#ef8117` → `#f8b64d`

## フォント

- 欧文: **Montserrat** 600–900（Google Fonts）/ fallback `Helvetica Neue, Arial`
- 和文: **Noto Sans JP** / fallback `Hiragino Kaku Gothic ProN, Hiragino Sans, Yu Gothic, Meiryo`
- ワードマーク `ARIONAUT`: Montserrat 900 / letter-spacing `.06em` /
  テキストグラデ `linear-gradient(90deg, #0d3c85, #1e74d8)`

## ロゴ

| ファイル | 用途 |
|---|---|
| `logo-mark.svg` | マスター。カラー背景が白〜淡色のとき |
| `logo-mark-compact.svg` | スピードライン省略版。おおむね48px以下 |
| `logo-mark-white.svg` | ダーク背景用の白抜き（翼1=`#ffffff` / 翼2=`#cfe4f7` / 星=`#f8b64d`） |
| `logo-lockup.svg` | マーク＋ワードマークの横組み。ワードマークは Montserrat 900 のテキスト要素 |
| `logo-stack.svg` | マーク＋社名の縦組み（マークの下に `ARIONAUT` ／ オレンジのダッシュを挟んで `合同会社`）。サイトの hero とヘッダーの社名表示はこの構成に合わせている |

### ルール

- マークの周囲には、星の直径以上の余白（アイソレーション）を確保する
- グライダーの角度・翼の2トーン（上=明・下=暗）は変えない
- 白黒1色で使う場合はスピードラインを省略する
- 星を単独のシンボルとして使わない

## OGP / ファビコン

- `ogp.svg` → `../assets/ogp.png`（1200×630）。テキストを変えたら再レンダリングが必要
- `../assets/favicon.svg`: ネイビー角丸地に白抜きグライダー＋オレンジ四芒星。
  16px でも星がオレンジの点として残るよう、マスターより星を拡大している

## QRコード

`qr-navy.svg` / `.png` — `https://arionaut.com/` 宛。segno 生成（v3・誤り訂正Q・
クワイエットゾーン4モジュール内包）、ダーク `#0c3a86`。
名刺での白パネル 18mm は縮小しない（1モジュール約0.49mm、印刷下限0.4mm）。

## 名刺

`namecard/arionaut-namecard.html` が正本、`.pdf` はそこからの書き出し。
仕上がり 91×55mm ＋塗り足し3mm（`@page` 97×61mm・2ページ）。

再生成: Chromium系で HTML を開き印刷 → 用紙カスタム 97×61mm・余白なし・背景グラフィックON。
Playwright なら `page.pdf(prefer_css_page_size=True, print_background=True)`。

## スローガン

**新しい“道”を拓く**（2026-08-24 確定。PATHFINDER LABS 時代からの継承。「航路」案は不採用）

使用箇所: サイトの `<title>` と hero `<h1>`、`ogp.svg`、名刺裏面。変更時は全箇所を揃えること。
