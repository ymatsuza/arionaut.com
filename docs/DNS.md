# arionaut.com を GitHub Pages に向ける（DNS設定手順）

> レジストラ: お名前.com（2026-08-24 時点で権威DNSは `01.dnsv.jp` 〜 `04.dnsv.jp`＝お名前.comのDNSサービス）
> 公開方針: **apex（arionaut.com）を正**、`www` は GitHub 側で apex に自動リダイレクト

## 0. 現状（2026-08-24 実測）

```
$ dig +short arionaut.com A        → 150.95.255.38   （お名前.com の初期ページ）
$ dig +short www.arionaut.com      → 150.95.255.38
$ dig +short arionaut.com NS       → 01.dnsv.jp. 〜 04.dnsv.jp.
```

既存の A レコード（`150.95.255.38`）は **削除または置き換えが必要**。
特に `www` は、A レコードが残っていると CNAME を併存させられない。

## 1. お名前.com Navi でレコードを設定する

お名前.com Navi にログイン →「ドメイン」→「DNS」→ 対象ドメイン `arionaut.com` の
「DNSレコード設定を利用する」から編集する。
（メニュー名は変更されることがあるので、実画面の表示で読み替えてください）

### 削除するレコード

| ホスト名 | TYPE | VALUE |
|---|---|---|
| （空欄） | A | 150.95.255.38 |
| www | A | 150.95.255.38 |

### 追加するレコード

**apex（ホスト名は空欄）— A レコード 4本**

| ホスト名 | TYPE | TTL | VALUE |
|---|---|---|---|
| （空欄） | A | 3600 | 185.199.108.153 |
| （空欄） | A | 3600 | 185.199.109.153 |
| （空欄） | A | 3600 | 185.199.110.153 |
| （空欄） | A | 3600 | 185.199.111.153 |

**apex — AAAA レコード 4本（IPv6。任意だが推奨）**

| ホスト名 | TYPE | TTL | VALUE |
|---|---|---|---|
| （空欄） | AAAA | 3600 | 2606:50c0:8000::153 |
| （空欄） | AAAA | 3600 | 2606:50c0:8001::153 |
| （空欄） | AAAA | 3600 | 2606:50c0:8002::153 |
| （空欄） | AAAA | 3600 | 2606:50c0:8003::153 |

**www — CNAME 1本**

| ホスト名 | TYPE | TTL | VALUE |
|---|---|---|---|
| www | CNAME | 3600 | ymatsuza.github.io. |

> IPアドレスは GitHub Pages の Apex ドメイン用アドレス。
> 上記は `dig +short ymatsuza.github.io A` / `AAAA` の実測値と一致することを確認済み（2026-08-24）。
> 将来変更される可能性があるため、設定前に GitHub の公式ドキュメント
> （Pages / Managing a custom domain）で再確認するのが安全。

## 2. 反映の確認

TTL 経過後（数分〜数時間）に以下を確認する。

```bash
dig +short arionaut.com A          # → 185.199.108-111.153 の4本
dig +short arionaut.com AAAA       # → 2606:50c0:800{0,1,2,3}::153
dig +short www.arionaut.com CNAME  # → ymatsuza.github.io.
curl -sI https://arionaut.com/ | head -3
```

## 3. HTTPS を有効にする

DNS が反映されると GitHub がドメイン検証を行い、Let's Encrypt 証明書を自動発行する。

リポジトリ → Settings → Pages で
- Custom domain が `arionaut.com`（緑チェック）
- **Enforce HTTPS** にチェックを入れる

証明書発行まで最大24時間かかることがある。それまでは `Enforce HTTPS` が
グレーアウトしたままになる（異常ではない）。

## 4. メール（MX）について

問い合わせ先は `info@arionaut.com`（2026-08-25 確定）。
**MXレコード未設定のため現時点では受信できない**。
Google Workspace を契約したうえで、MX レコードを別途追加すること。
MX は上記の A/AAAA/CNAME とは独立なので、Pages の設定と競合しない。

## 5. 独自ドメイン乗っ取り（dangling DNS）の注意

将来この GitHub Pages サイトを閉じる場合は、**先に DNS レコードを削除してから**
リポジトリ／Pages 設定を消すこと。逆順にすると、第三者が同名のリポジトリで
`arionaut.com` を乗っ取れる状態が一時的に生じる。

---

## 6. 切替結果（2026-08-24 実測）

権威DNS `01.dnsv.jp` 直問い合わせ・Google Public DNS ともに反映を確認。

```
$ dig +short @01.dnsv.jp arionaut.com A      → 185.199.108-111.153
$ dig +short @01.dnsv.jp arionaut.com AAAA   → 2606:50c0:8000-8003::153
$ dig +short @01.dnsv.jp www.arionaut.com CNAME → ymatsuza.github.io.
```

Let's Encrypt 証明書は DNS 反映から約 1 分で発行された（想定の最大24hより大幅に早い）。

```
subject=CN=arionaut.com
issuer=C=US, O=Let's Encrypt, CN=YR1
notBefore=Aug 24 07:45:29 2026 GMT / notAfter=Nov 22 07:45:28 2026 GMT
SAN: DNS:arionaut.com, DNS:www.arionaut.com
```

Enforce HTTPS は API で有効化済み（`PUT /repos/ymatsuza/arionaut.com/pages` の `https_enforced=true`）。
`https://www.arionaut.com/` → `https://arionaut.com/` へ 301。

> 注: 有効化直後、`http://arionaut.com/`（ルートのみ）が Fastly エッジのキャッシュに残った
> 200 を返し続けることがある（`x-proxy-cache: MISS` / `X-Cache: HIT`）。
> `http://arionaut.com/privacy.html` は 301 を返すので設定自体は効いている。キャッシュ失効待ち。
