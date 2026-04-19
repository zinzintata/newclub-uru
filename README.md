# New Club Uru — Website

## セットアップ

このWebサイトは単一の `site/index.html` ファイルで構成されています。
サーバー・ビルドツール不要で、ファイルをホスティングするだけで動作します。

## ファイル構成

```
outputs/newclub-uru/
├── site/
│   └── index.html    ← メインファイル（これ1つを公開）
├── README.md
├── handover.md       ← 更新・運用マニュアル
└── image_sources.md  ← 画像出典
```

## デプロイ

`site/index.html` を任意のWebホスティングにアップロードするだけです。

- Netlify: `site/` フォルダをドロップ
- GitHub Pages: `site/` の中身を公開

**HTTPS必須**（sessionStorageとCDNの動作に必要）

## 初回作業チェックリスト

- [ ] 店舗実写写真をUnsplash画像から差し替え
- [ ] 営業時間を確定情報に更新  
- [ ] 定休日を確定情報に更新
- [ ] 料金システムの詳細を追記
- [ ] Google Mapsの埋め込みコードを最新版に差し替え
- [ ] Google Business Profileにウェブサイトを登録
- [ ] Google Analytics 4 トラッキングIDを追加（任意）

詳細は `handover.md` を参照してください。
