---
title: コンテンツ設計（英語圏版）｜The Japan Walkthrough
type: content-architecture
created: 2026-07-03
last_updated: 2026-07-03
status: ⚠️**旧（2026-07-03）＝そのまま実装に使わない。** ①**POD前提が残っている**（サイト構造の`Shop`・記事#7#8の収益・第4陣の見出し）＝**2026-07-31に本人が除外決定済み** ②**サイト名「The Japan Walkthrough」・章名・攻略本メタファーは未決定**（STEP 2.5 のB5/B7で決める。本人評価＝章タイトル案は「微妙」） ③記事リストの改廃案＝[[wiki/keyword-map-en]] §6/§13。／旧status＝「確定（初期記事リスト25本つき。KW実数はA6以降にSearch Consoleの実データで補正）」
purpose: サイトの章構造（攻略本）と初期記事リスト。Opusのカテゴリ実装・執筆順の根拠。
related:
  - "[[00_設定/英語圏版_上流設計]]"
  - "[[wiki/persona/英語圏版_3ペルソナ]]"
  - "[[wiki/design/英語圏版_デザイン調整]]"
---

# コンテンツ設計｜The Japan Walkthrough（日本の攻略本）

> **組織原理（ユーザー発案・採用）**：サイトの主要コンテンツを「ゲームの攻略本」として章立てする。
> 根拠：(1) 著者の実践思想「日本＝ルールが特殊なゲーム。台本で攻略する」（Hole/日本攻略）がそのままUXになる (2) MVV Value③「台本を渡す」の体現 (3) 攻略本メタファーは英語圏ゲーマー文化（walkthrough/guide/quest）に自然に通じ、Sam層にシェアされやすい (4) 競合（Tofugu=語学・深掘り／GaijinPot=求人・生活DB／japan-guide=網羅観光／Tokyo Cheapo=節約）に**「攻略本UX」は不在**（確認日2026-07-03・[競合比較](http://easynihon.com/blog/best-japan-resources-for-foreigners-2026/)）。

## サイト構造

```
Home
├── The Japan Walkthrough（攻略本ハブ＝旗艦固定ページ。全章への目次）
│   ├── Ch.0 Before You Land（出発前：eSIM・IC・現金・アプリ）
│   ├── Ch.1 Day One（到着初日：空港→電車→コンビニ→低接触メシ）
│   ├── Ch.2 Eating Like a Local（食：チェーン攻略・券売機・注文台本・マナー）
│   ├── Ch.3 The Rules（マナー・暗黙のルール：箸・ゴミ・銭湯・電車）
│   ├── Ch.4 The Hidden OS（日本のOS：世間・うちそと・建前・同調圧力）
│   └── Ch.5 Making Friends（日本人との繋がり方＝バズ投稿の本丸）
├── Strolls（散歩・ローカル：おまけ2〜3割。手賀沼・北総・東京東側・店紹介）
├── Shop（PODグッズ）
└── About / Contact / Privacy & Disclosure
```

- WordPressカテゴリ＝ **Walkthrough各章（6）＋ Strolls** の7つ。攻略本ハブは固定ページ（全章の目次＋進行表UI）。
- 記事は「クエスト」単位＝1記事1タスク完結（読んだらその日できる）。
- 攻略本UI部品（[[wiki/design/英語圏版_デザイン調整]]で定義）：**Cheat Sheetボックス**（結論の台本）／**難易度バッジ**（Language needed: None/Basic）／**チェックリスト**／**「実際にやった」著者スタンプ**（Value①の体験/調査の区別表示）。

## 執筆ルール（全記事共通）

1. 冒頭に「このクエストで出来るようになること」1文＋Cheat Sheet（結論先出し）。
2. 台本は**そのまま音読できる形**（ローマ字＋日本語＋意味）で渡す。例：*"Sumimasen" (すみません — excuse me)*。
3. 体験と調査を区別（MVV Value①）：体験→"I did this"、調査→出典リンク。制度・ビザ・医療は一次情報リンク＋「専門家/公式に確認を」を必ず添える（YMYL・日本語版ルール継承）。
4. 写真は著者の一次写真優先。キャラ吹き出しは1記事2〜4回（英語セリフ）。
5. Weird Japan禁止・説教禁止・「日本人は皆〜」の一般化禁止（Value②⑤）。

## 初期記事リスト（25本・執筆順）

> 凡例：主対象＝[[wiki/persona/英語圏版_3ペルソナ]]（J=Jake/C=Claire/S=Sam）、収益＝広告以外の導線。★＝旗艦。

### 第1陣：旗艦＋Survival（公開時に最低限これを揃える）
| # | 章 | タイトル（仮） | 対象 | 収益 |
|---|---|---|---|---|
| 1★ | ハブ | The Japan Walkthrough — A Local Househusband's Guide to Actually Surviving Japan | 全 | — |
| 2★ | Ch.1 | Restaurants You Can Use on Day One in Japan (No Japanese Needed) — 松屋/すき家/マック/日高屋等、券売機・タッチパネル・接触量で格付け | C/J | eSIM・アフィ内部導線 |
| 3 | Ch.1 | The Konbini Walkthrough: Everything You Can Do at a Japanese Convenience Store | C/J | — |
| 4 | Ch.0 | Before You Land: eSIM, IC Cards, and Cash — The 30-Minute Setup | C | **eSIM/交通アフィ** |
| 5 | Ch.2 | How to Use a Ticket Machine Restaurant (Step-by-Step, with Photos) | C/J | — |
| 6★ | Ch.5 | How to Actually Make Japanese Friends — From the Japanese Guy Who Asked Reddit the Reverse Question | J | — ※バズ投稿の続編。Reddit再投稿の目玉 |

### 第2陣：The Hidden OS（差別化の核・Sam獲得）
| # | 章 | タイトル（仮） | 対象 | 収益 |
|---|---|---|---|---|
| 7★ | Ch.4 | Why Japanese People Seem Distant: Uchi and Soto, Explained by an Insider | J/S | POD（概念グッズ） |
| 8 | Ch.4 | "Seken": The Invisible Crowd That Rules Japan (and Me) | S/J | POD |
| 9 | Ch.4 | Honne and Tatemae Are Not Lying — Here's the Actual Manual | J/S | — |
| 10 | Ch.4 | Japan Is a "Tight" Culture — The Research That Explains Your Exhaustion | J | — |
| 11 | Ch.5 | The "Regular" Strategy: How Repetition (Not Talking) Makes You Belong in Japan | J | — |

### 第3陣：Rules & Eating（検索の裾野）
| # | 章 | タイトル（仮） | 対象 | 収益 |
|---|---|---|---|---|
| 12 | Ch.3 | Chopstick Rules That Actually Matter (and the Ones Nobody Cares About) | C | — |
| 13 | Ch.3 | The Onsen Walkthrough: Tattoos, Towels, and the Exact Order of Things | C | 体験予約アフィ |
| 14 | Ch.3 | Garbage Rules in Japan: The Real Difficulty Level | J | — |
| 15 | Ch.3 | Train Etiquette: What's Actually Rude vs. Tourist Myth | C | 交通アフィ |
| 16 | Ch.2 | Ordering at an Izakaya: The Complete Script | C/J | — |
| 17 | Ch.2 | Solo Dining in Japan Is Normal: Where to Sit, What to Say | J/C | — |
| 18 | Ch.2 | Japanese Chain Restaurant Tier List (by a Guy Who Eats There Weekly) | C/J/S | — |

### 第4陣：Strolls＋文化（世界観・POD・E-E-A-T）
| # | 章 | タイトル（仮） | 対象 | 収益 |
|---|---|---|---|---|
| 19 | Strolls | Teganuma: The Lake Walk 40 Minutes from Tokyo That Nobody Told You About | C/S | — |
| 20 | Strolls | A Househusband's Tokyo: The East Side, on Foot | C/S | — |
| 21 | Strolls | My Local Shopping Street (Shotengai) — What to Buy, How to Behave | C/S | — |
| 22 | Ch.5 | Foreigner-Friendly Places in Japan: How to Spot Them | J/C | — |
| 23 | Ch.0 | First Week in Japan: The Complete Checklist | C/J | eSIM・宿アフィ |
| 24 | Ch.4 | Why I Became a Househusband in Japan (and What It Taught Me About This Country) | S/J | — ※About兼旗艦・人格ブランドの核 |
| 25 | Strolls | Traditional Culture Without the Tour Bus: 5 Things I Actually Do | C/S | 体験アフィ |

### 以降のネタ供給源（切らさない仕組み）
- **r/japanresidents・r/JapanTravel・r/movingtojapanの質問**を月次で収集→クエスト化（運用設計参照）。バズ投稿のコメント176件が最初の鉱脈。
- Hole/日本攻略の攻略エントリが増えるたび、英語記事化を検討（本人の実生活＝コンテンツ工場）。

## 競合との住み分け（確認日2026-07-03）

| 競合 | 強み | 本サイトとの差 |
|---|---|---|
| [GaijinPot](https://gaijinpot.com) | 求人・住居・生活DBの最大手 | DB型。一人称の攻略本ではない |
| [Tofugu](https://www.tofugu.com) | 日本語学習・深掘り記事 | 外国人視点。語学が主戦場 |
| [japan-guide.com](https://www.japan-guide.com) | 観光網羅・1996年から | 百科事典型。台本・接触量の視点なし |
| [Tokyo Cheapo](https://tokyocheapo.com) | 節約×東京 | 節約軸。文化のOS解説なし |
| 本サイト | **日本人主夫本人の一人称×攻略本UX×低接触の台本** | 「なぜそうなのか（OS）」と「どう動くか（台本）」を同一人物が書く |
