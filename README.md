# nabitan-web — NABItan Web UI（Cloudflare Pages）

NABItan のチャットWeb UI（`public/index.html`）。GitHub連携でCloudflare Pagesに自動デプロイする。

## 構成

```
public/
  index.html   ← 1枚で完結（CSS/JS内蔵）。GASを直接GETで呼ぶ（GAS_URL）。LIFF対応（liff.getProfile()でUID取得・URL方式もフォールバック）
```

## Cloudflare Pages 設定（Git連携）

| 項目 | 値 |
|---|---|
| Framework preset | None |
| Build command | （空欄） |
| Build output directory | `public` |

## LIFF

- LINE Login チャネル（bot と同一プロバイダー・Channel 2009693555）に LIFF を作成。
- エンドポイントURL＝この Pages のURL。`public/index.html` の `LIFF_ID` に liffId を設定。
- userId は `liff.getProfile()` で取得。URL の `?uid=` は後方互換フォールバック。
