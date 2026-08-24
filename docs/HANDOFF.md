# Arionaut ブランド立ち上げ — ハンドオフドキュメント

> 作成: 2026-08-24 / Cowork セッションからの引き継ぎ用
> 対象: Claude Code（またはこの続きを担当するセッション）
> オーナー: 松崎 雄太（Yuta Matsuzaki / ymatsuza.tech@gmail.com）

---

## 1. プロジェクト概要と経緯

新設法人の商号を **PATHFINDER LABS合同会社 → Arionaut合同会社（ARIONAUT LLC）** に変更する
リブランドプロジェクト。定款・印鑑・名刺は旧名で作成済みだが、**法務局への設立登記は未提出**の
段階で切り替えを決断した。

### 改名の決定的理由（J-PlatPat 称呼検索の結果 / 2026-08-24 実施）

| 称呼 | ヒット | 42類 | 備考 |
|---|---|---|---|
| パスファインダー | 64件 | **16件** | **日揮グローバル「PATHFINDER」登録6467514**（標準文字、2021登録、存続期間満了 2031-11-08）が42類で「CAD/CAMコンピュータプログラムの開発」「AIを活用したプログラムの設計」「電子計算機のプログラムの設計・作成・保守」等を指定（類似群 42N01/42N03/**42P02**/42X11）。他に1インチ社「PATHFINDER」登録6733359等も存続 |
| アリオノート／アリオナウト | 完全一致 **0件** | 類似3件のみ | 類似称呼はアローネット（東証 arrownet）、アルムノート（Alumnote）等で音的に遠い |

- 「PATHFINDER LABS」の LABS は識別力の弱い付加語 → 要部「パスファインダー」で類似判断されるリスクが高く、受託ソフト開発（42P02）は指定役務に正面衝突。
- Arionaut は Web 上の企業・ブランド競合もゼロ。**arionaut.com は取得済み**（DNS: GMO系で解決確認済み）。arionaut.jp / arionaut.co.jp / arionaut.io は 2026-08-24 時点で空き。
- 最終的な商標の類否判断は弁理士確認を推奨（本ドキュメントは非専門家による一次調査）。

### 名前の由来（ブランドストーリー）

BUMP OF CHICKEN 関連の造語。**Arion（アリオン: 神話の駿馬・名曲「アリア」のルーツ）+ Astronaut/Aeronaut**。
アルバム『COSMONAUT』の系譜。「宇宙の深淵を旅し、全く新しい航路を拓く探検家」。
旧名 PATHFINDER（BUMP TOUR 2017-2018 の名前でもある）の「開拓者の志」を継承。

---

## 2. 確定済みの決定事項

- **商号**: Arionaut合同会社 / 英文 ARIONAUT LLC（法人形態は合同会社のまま）
- **ロゴ**: 「Glider」案で決定（『beautiful glider』由来のファセット・グライダー＋オレンジ四芒星）。
  旧 PATHFINDER LABS ロゴのテイスト（青グラデ角張りマーク＋オレンジ星＋ネイビー太字ワードマーク）を踏襲
- **代表社員**: 松崎 雄太（Yuta Matsuzaki）
- **所在地**: 〒300-2635 茨城県つくば市東光台3-21-7
- **TEL**: 090-9778-7388
- **事業3本柱**: 業務改善 / AI活用 / 受託開発（現行 pf-labs.org と同一）
- **設立予定日**: 2027年1月4日（現行サイト記載を引き継ぎ）

## 3. 仮置き（ユーザー確認が必要）

1. **メールアドレス** `matsuzaki@arionaut.com` — 仮。ドメイン側のメール設定は未実施
2. **スローガン** 「新しい“航路”を拓く」 — 旧「新しい“道”を拓く」からの変更提案（未承認）。
   名刺裏面とサイト hero の2箇所に使用中。戻す場合は両方を修正
3. **サブテキスト** ロゴロックアップの「GENERATIVE DESIGN」および
   タグライン「NAVIGATE. DESIGN. DISCOVER.」はドラフト
   （※事業内容は現行サイトでは業務改善/AI活用/受託開発。「GENERATIVE DESIGN」表記は
   ロゴ検討初期の事業構想由来なので、そのまま使うかユーザーに要確認）

---

## 4. ブランド仕様（デザイントークン）

### カラーパレット

```css
--navy:   #0c3a86;  /* ロゴグラデ始点・見出し */
--mid:    #1b62c0;
--cyan:   #48a3ec;
--orange: #ef8f27;  /* 星・アクセントルール */
--ink:    #1f2933;  /* 本文 */
--muted:  #616e7c;
--bg:     #f7f9fb;  /* 淡背景 */
--line:   #dfe5ec;  /* 罫線 */
/* ダーク背景: radial #12315f → #0a1f42 → #071734 / footer #071734 */
/* 星グラデ: #ef8117 → #f8b64d */
```

### フォント

- 欧文: **Montserrat** 600–900（Google Fonts）/ fallback: Helvetica Neue, Arial
- 和文: **Noto Sans JP** / Hiragino Kaku Gothic ProN 系
- ワードマーク「ARIONAUT」: Montserrat 900, letter-spacing .06em,
  テキストグラデ `linear-gradient(90deg, #0d3c85, #1e74d8)`

### ロゴマーク（マスターSVG / viewBox="0 0 300 230"）

```svg
<svg viewBox="0 0 300 230" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="w1" gradientUnits="userSpaceOnUse" x1="40" y1="190" x2="220" y2="40">
      <stop offset="0" stop-color="#1b62c0"/><stop offset="1" stop-color="#48a3ec"/>
    </linearGradient>
    <linearGradient id="w2" gradientUnits="userSpaceOnUse" x1="120" y1="200" x2="230" y2="40">
      <stop offset="0" stop-color="#0c3a86"/><stop offset="1" stop-color="#1b62c0"/>
    </linearGradient>
    <linearGradient id="sp" gradientUnits="userSpaceOnUse" x1="20" y1="200" x2="150" y2="120">
      <stop offset="0" stop-color="#8ec4ef"/><stop offset="1" stop-color="#2f74c4"/>
    </linearGradient>
    <linearGradient id="st" gradientUnits="userSpaceOnUse" x1="250" y1="34" x2="284" y2="0">
      <stop offset="0" stop-color="#ef8117"/><stop offset="1" stop-color="#f8b64d"/>
    </linearGradient>
  </defs>
  <!-- スピードライン（省略可。小サイズでは省く） -->
  <polyline points="24,196 74,148 108,168" stroke="url(#sp)" stroke-width="13" fill="none"
            stroke-linejoin="miter" stroke-miterlimit="12" opacity="0.85"/>
  <!-- グライダー翼（上=明・下=暗） -->
  <polygon points="52,182 226,38 132,148" fill="url(#w1)"/>
  <polygon points="132,148 226,38 168,186 140,158" fill="url(#w2)"/>
  <!-- 四芒星 -->
  <polygon points="267,2 271.5,14.5 284,19 271.5,23.5 267,36 262.5,23.5 250,19 262.5,14.5" fill="url(#st)"/>
</svg>
```

白抜き版（ダーク背景用）: 翼1=#ffffff, 翼2=#cfe4f7, 星=#f8b64d, スピードライン=#ffffff opacity .75

---

## 5. 成果物の所在

### Google Drive `マイドライブ/Arionaut/`（全て 2026-08-24 アップロード済み）

| ファイル | 内容 |
|---|---|
| `arionaut-namecard.html` | 名刺入稿データ（表・裏）。仕上がり91×55mm＋塗り足し3mm、@page 97×61mm・2ページ。画面表示時はトンボガイドと入稿メモ付き（印刷時は自動非表示） |
| `arionaut-namecard.pdf` | 上記をChromium印刷で書き出した2ページPDF（97×61mm） |
| `index.html` | ホームページ完成品（自己完結・レスポンシブ確認済み）。構成: sticky nav / hero / 事業内容3カード / 会社概要表 / お問い合わせ / footer |
| `qr-navy.svg` / `qr-navy.png` | QRコード（https://arionaut.com/ 宛、segno生成、v3・誤り訂正Q・クワイエットゾーン4モジュール内包、OpenCVでデコード検証済み。ネイビー #0c3a86） |

### その他

- **ロゴのデザインカンバス**（編集可能）: https://claude.ai/code/artifact/ac8d81b4-c339-4c78-a018-87f68eea3ca0
  （1ページ目=決定版 Glider ライト/ダーク、2ページ目=ボツ案アーカイブ A: Ascent / B: Orbit）
- **旧ブランド資料**: Drive `マイドライブ/PATHFINDER_LABS/`（旧ロゴjpeg、旧名刺一式 `namecard/`、
  定款PDF `定款_PATHFINDER LABS_*.pdf`、プロフィール写真 512×512 ほか）
- **現行サイト**: https://pf-labs.org （新サイトの構成・文言のベース）

---

## 6. 残タスク（優先度順の提案）

1. **仮置き3点の確定**（§3）— メール実アドレス、スローガン、サブテキスト
2. **定款の商号修正 → 設立登記**
   - 合同会社なので公証役場の認証は不要（作り直しはほぼ印刷代のみ）
   - 会社実印の彫り直し、freee会社設立で書類再生成（Drive旧フォルダに freee のスクショあり）
3. **ドメイン整備**
   - arionaut.jp の取得推奨（先取りリスク回避）。co.jp は登記完了後に取得可
   - arionaut.com の DNS / メール（MX）設定
4. **サイトのデプロイ** — index.html は静的1ファイル。Cloudflare Pages / GitHub Pages 等で
   arionaut.com に公開。favicon・OGP画像・プライバシーポリシーページ（footerリンクが `#` のまま）が未作成
5. **商標出願** — 「Arionaut」を42類（＋できれば9類）で出願（特許庁へ直接なら出願料12,000円＋区分加算）。
   今回の教訓（日揮のPATHFINDER）を踏まえ、押さえる側に回る
6. **名刺の入稿** — PDFをIllustrator等でアウトライン化して印刷所へ。
   QRの白パネル18mmは縮小しない（1モジュール約0.49mm、下限0.4mm）
7. **pf-labs.org の扱い** — 移行後のリダイレクト or 併存の方針決め

---

## 7. 技術メモ（再現用）

- QR再生成: `python3 -c "import segno; segno.make('https://arionaut.com/', error='q').save('qr.svg', border=4, dark='#0c3a86', light='#ffffff', omitsize=True)"`
- 名刺PDF再生成: Chromium系で `arionaut-namecard.html` を開き印刷 → 用紙カスタム97×61mm・余白なし・背景グラフィックON（Playwrightなら `page.pdf(prefer_css_page_size=True, print_background=True)`）
- 名刺・サイトとも外部依存は Google Fonts のみ（サイトのみ使用。名刺はシステムフォント）
- 旧名刺 `PATHFINDER_LABS/namecard/namecard.html` が構造の原型。同じCSS変数名・クラス設計を踏襲している
