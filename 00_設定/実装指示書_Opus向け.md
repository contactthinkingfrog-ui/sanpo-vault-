---
title: 実装指示書（Opus向け）｜The Strolling Husband 立ち上げ
type: implementation-spec
created: 2026-07-03
last_updated: 2026-07-03
status: 確定（2026-07-03。実装の起点として書いてあった）
purpose: サイト立ち上げの仕様。当時は Opus 向けに、この保管庫だけ見て実装できるように書いてあった。
related:
  - "[[00_設定/英語圏版_上流設計]]"
  - "[[wiki/design/英語圏版_デザイン調整]]"
  - "[[wiki/content-architecture-en]]"
  - "[[00_設定/収益化方針_英語圏版]]"
---

# 実装指示書｜The Strolling Husband（Opus向け）

> 英語圏向けサイト The Strolling Husband の立ち上げ仕様（2026-07-03）。当時、設計は確定済みとして書いてあり、疑問は実装を止めて本人に確認する、作業は `logs/activity.md` に残す、としてあった。

## 0. 実装前に見ていたもの

1. [[00_設定/wiki-schema]]（構成メモ）→ [[wiki/index]]
2. [[00_設定/英語圏版_上流設計]]（事業の全体像・5本の柱・収益）
3. [[00_設定/MVV_英語圏版]]（判断のふるい）
4. [[wiki/content-architecture-en]]（サイト構造・カテゴリ・初期記事25本）
5. [[wiki/design/英語圏版_デザイン調整]]（デザイン差分）＋その親である日本語版設計群（カラー設計／トップページ設計／カテゴリページ設計／個別記事ページ設計／ロゴ設計／アイキャッチ・OGP設計）と `wiki/design/cocoon/共通土台.css`
6. [[wiki/voice-guide-en]]（文体）／[[wiki/persona/英語圏版_3ペルソナ]]（読者）
7. [[00_設定/収益化方針_英語圏版]]・[[00_設定/マーケティング・運用設計_英語圏版]]

## 1. 技術スタック（確定・再検討しない）

| 項目 | 決定 | 理由 |
|---|---|---|
| CMS | **WordPress ＋ Cocoon親テーマ＋専用子テーマ（新規）** | 既存2サイトと同一サーバー・構築ノウハウ流用・現金コストほぼゼロ。Cocoonの自動目次・吹き出し部品を継承 |
| インストール | **新規WordPress**（shafu-life / shufu-sanpo とは別インスタンス） | ブランド・言語・解析の分離 |
| サイト言語 | `en_US`（WP設定）。管理画面は日本語のままで可 | 読者向け出力が英語であること |
| ドメイン | **strollinghusband.com 推奨**（2026-07-03 whois確認：.com/the付き.com/.jp すべて空き） | 短い・タグラインと一致 |
| EC | **WooCommerceは入れない**。ShopページはEtsyストアへの導線＋ギャラリー | 保守負荷回避（収益化方針） |
| 解析 | GA4＋Search Console | KPI（マーケ・運用設計）準拠 |

## 2. フェーズ0：ユーザー作業（手順を出して誘導していた）

- [ ] ドメイン取得（strollinghusband.com。**購入・契約はユーザー本人が行う**）
- [ ] サーバーにドメイン追加・SSL設定・WordPress新規インストール
- [ ] Cocoon親テーマ導入・空の子テーマ作成
- [ ] Etsyショップ開設・アフィリエイト各社への登録申請（**2026/12以降**）

## 3. フェーズ1：子テーマ土台（Opus）

1. `wiki/design/cocoon/共通土台.css` を子テーマ style.css に移植。
2. [[wiki/design/英語圏版_デザイン調整]] §2のフォント差し替え（Lora読み込み・Noto Serif JP削除・line-height 1.7・本文72ch）。
3. 同 §4 の攻略本UI部品を追加実装：`.ss-cheat` `.ss-diff` `.ss-check` `.ss-stamp` `.ss-quest-nav` `.ss-chapter-card`（既存ボックス部品のパターンを流用）。
4. ファビコン：assets/favicon_足あと.svg から 16/32/180/512px を書き出して設定。

## 4. フェーズ2：サイト構造（Opus）

1. カテゴリ作成（スラッグ）：`before-you-land` / `day-one` / `eating` / `the-rules` / `hidden-os` / `making-friends` / `strolls`
2. 固定ページ：Home（トップ）／The Japan Walkthrough（ハブ）／About／Contact／Privacy & Disclosure／Shop
3. トップページHTML：[[wiki/design/トップページ設計]]＋[[wiki/design/英語圏版_デザイン調整]]§6。`wiki/design/トップページ_モック.html` をビジュアル参照（文言は英語版に）。ヒーロー＝一次写真＋「The real Japan, one stroll at a time.」＋Start the Walkthroughボタン。
4. Walkthroughハブ：章カード6枚（`.ss-chapter-card`）＋各章のクエスト一覧。
5. ナビ・フッター：デザイン調整§3のラベル。

## 5. フェーズ3：記事テンプレート（Opus）

`templates/記事テンプレ_EN.html` を新規作成。必須部品（上から順）：

```
[難易度バッジ .ss-diff] → [リード2〜3文] → [Cheat Sheet .ss-cheat]
→ [アフィ開示文（該当記事のみ・1行）] → [広告(リード後・2026/12以降)]
→ 本文（h2セリフ装飾・吹き出し2〜4・.ss-check/.ss-stamp適宜）
→ [出典ボックス（調査記事は必須）] → [著者ボックス] → [.ss-quest-nav]
```

- h1は入れない（投稿タイトル）・目次ブロックは入れない（Cocoon自動目次）＝日本語版ルール継承。
- 広告位置・密度は [[wiki/design/個別記事ページ設計]] の「品を守る」規定に従う。

## 6. フェーズ4：固定ページ本文（Opus＋ユーザー確認）

- **About**：記事#24（Why I Became a Househusband in Japan）を兼ねる。voice-guide-en準拠でドラフト→ユーザー承認。ハンドルネーム運用（日本語版・固定ページ設計の方針継承）。
- **Contact**：フォームプラグイン（Contact Form 7 等）。メール直書きしない。
- **Privacy & Disclosure**：`templates/法務ページ_雛形` を下敷きに英語で新規作成。必須要素＝プライバシーポリシー／Cookie・解析／AdSense第三者配信／**アフィリエイト開示（FTC要件：関係の明示・目立つ位置）**／免責（制度・旅行情報は変わる・公式を確認）。公開前にユーザー最終確認。

## 7. フェーズ5：アイキャッチ・OGP（Opus）

- `templates/アイキャッチ_テンプレ` をLora＋英語版に改修（デザイン調整§5）。運用＝書き換え→スクショ（日本語版と同じ）。

## 8. フェーズ6：公開前チェックリスト（受け入れ基準）

- [ ] トップ・ハブ・カテゴリ7・固定ページ5がデザイン通り表示される（モバイル含む）
- [ ] 記事テンプレで1本入稿し、全部品（cheat/diff/check/stamp/quest-nav/吹き出し/出典/著者）が正しく描画される
- [ ] Lighthouse：Performance/SEO 90以上目安（CWV重視＝広告なし時点）
- [ ] GA4・Search Console 接続
- [ ] **収益コードが一切入っていないこと（2026/12まで）**：AdSenseコードなし・アフィリンクはプレースホルダ（`href="#" data-aff="airalo"`形式）で実装し、解禁時に一括差し替え
- [ ] activity.md に実装記録

## 9. 実装時にやらなかったこと

- `raw/` は原文のまま。日本語版の棚上げドキュメント（MVV・ペルソナ・keyword-map等）も触っていない。
- 2026/12前に報酬が発生しうる状態は作っていない（§8）。
- 配色・柱・カテゴリ・収益方針の独自変更はしていない。疑問は本人へ。
- 記事の一人称・体験部分は捏造していない（voice-guide-en の執筆体制）。

## 10. 実装後の運用へ

公開後は [[00_設定/マーケティング・運用設計_英語圏版]] のサイクル（週次執筆・Reddit・月次メンテ・四半期レビュー）に接続。performance-log を開始する。
