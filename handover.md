# 引き渡し書 — New Club Uru Website
制作: AI Web制作カンパニー / 2026-04-19

---

## 納品物一覧

```
outputs/newclub-uru/
├── site/
│   └── index.html          ← 本番投入可能なWebサイト（単一HTMLファイル）
├── handover.md             ← 本ファイル
├── README.md               ← セットアップ・デプロイ手順
└── image_sources.md        ← 画像出典一覧
```

---

## 更新方法

### 1. 店舗写真の差し替え（推奨: 最初にやること）

現在はUnsplash（フリー素材）を使用しています。
実際の店舗写真に差し替えることで、リアリティが大幅に向上します。

**手順**:
1. Instagram @new_club_uru の投稿から写真を保存（または直接撮影）
2. `index.html` 内の以下のURLを差し替えます:

```html
<!-- ヒーロー背景 (section#hero > .hero-bg の background-image) -->
#hero の CSS内: url('https://images.unsplash.com/photo-1566737236500-...')
→ url('assets/images/hero_bg.jpg') に変更し、同フォルダに画像を配置

<!-- インテリアギャラリー (4枚) -->
<img src="https://images.unsplash.com/photo-1574180045827-..." alt="...">
→ <img src="assets/images/interior_01.jpg" alt="...">
```

**推奨画像仕様**:
- ヒーロー: 横長 1920×1080px 以上、JPEG/WebP
- インテリア: 900×675px 以上、JPEG/WebP

---

### 2. 営業時間の変更

`index.html` 内 `<!-- 05 INFORMATION -->` セクションを編集:

```html
<span class="info-value">20:00 〜 LAST</span>
↓
<span class="info-value">XX:00 〜 LAST（または具体的な時間）</span>
```

---

### 3. 定休日の更新

同じく `<!-- 05 INFORMATION -->` セクション:

```html
<span class="info-value">不定休<br><small ...>最新情報はInstagramにて</small></span>
↓
<span class="info-value">毎週〇曜日</span>  ← 確定したら更新
```

---

### 4. 料金表の充実

`<!-- 04 SYSTEM -->` セクションの `.card-body` を編集:

```html
<!-- 現在 -->
詳細はご来店時またはInstagramにてご確認ください。

<!-- 料金確定後 -->
セット料金 ¥X,XXX〜（税込）
ドリンクX杯含む
```

---

### 5. 年齢確認リダイレクト先の変更

```javascript
// index.html 内 JavaScript セクション
function leaveSite() {
  window.location.href = 'https://www.yahoo.co.jp/';  ← ここを変更
}
```

---

### 6. Google Maps 更新

`<!-- 06 ACCESS -->` セクションの iframe src を変更:

```html
<iframe src="https://maps.google.com/maps?q=770-0934+徳島県...&output=embed&z=16&hl=ja"
```

Google マップで店舗を開き、「共有」→「地図を埋め込む」から取得したコードに差し替えると精度が上がります。

**Googleマップのダークフィルターについて**:
マップに `filter: grayscale(100%) invert(90%)...` を適用しています。
ブラウザによっては地名が読みにくい場合は、以下の行を削除してください:

```css
.access-map-wrap iframe {
  filter: grayscale(100%) invert(90%) brightness(80%) contrast(90%);  ← この行を削除
}
```

---

## 将来のキャスト紹介ページ拡張ポイント

`<!-- 07 RECRUIT -->` セクションの後、以下のセクションを追加することで対応可能:

```html
<!-- キャスト紹介セクション（将来追加） -->
<section id="cast">
  <div class="section-inner">
    <p class="section-eyebrow">Cast</p>
    <h2 class="section-h2-ja">キャスト紹介</h2>
    <!-- 各キャストカードをここに追加 -->
  </div>
</section>
```

**注意事項**:
- キャストの顔写真・本名・個人SNSの掲載は本人の同意を必ず取得
- ニックネーム・イメージ写真（後ろ姿・シルエット等）の使用を推奨

---

## Google Business Profile 連携推奨手順

1. Google ビジネスプロフィール (https://business.google.com) にアクセス
2. 「New Club Uru」で検索またはオーナー申請
3. 以下の情報を入力:
   - 住所: 徳島県徳島市秋田町1丁目-50 アクティ異人館2F
   - カテゴリ: ナイトクラブ
   - 営業時間: 20:00〜LAST
   - ウェブサイト URL: （本サイトのURL）
   - Instagram リンク
4. 写真をアップロード（店内・外観）
5. 定期的にGoogle投稿で営業情報を更新

---

## 技術情報

| 項目 | 内容 |
|---|---|
| ファイル構成 | 単一HTMLファイル（index.html） |
| 外部依存 | GSAP v3.13.0, Lenis v1.1.14 (CDN), Google Fonts |
| 画像ホスト | Unsplash CDN（本番では自サーバー推奨） |
| ブラウザ対応 | Chrome 90+, Safari 14+, Firefox 88+, Edge 90+ |
| モバイル対応 | iOS 14+, Android 10+ |
| HTTPS | 必須（sessionStorage / 外部CDNのため） |

---

## デプロイ手順

Netlify (推奨):
1. https://netlify.com にアクセス
2. `outputs/newclub-uru/site/` フォルダをドラッグ&ドロップ
3. カスタムドメインを設定（例: newclub-uru.jp）
4. SSL証明書は自動発行

GitHub Pages:
1. GitHubリポジトリに `site/` の中身をpush
2. Settings → Pages → Source を `main` ブランチに設定
3. カスタムドメイン設定

---

## サポート・問い合わせ

サイトに関する技術的な質問や修正依頼は、制作担当者までご連絡ください。
