## Languages / 言语
[**🇺🇸 English**](README.md)  
[**🇷🇺 Russian / Русский**](README_RU.md)  
[**🇨🇳 Simplified / 简体中文**](README_ZH.md)  
[**🇹🇼 🇭🇰 🇲🇴 Traditional / 繁體中文**](README_HANT.md)

---

## FlClashX

[![Download](https://img.shields.io/github/downloads/pluralplay/FlClashX/total?style=flat-square&logo=github)](https://github.com/pluralplay/FlClashX/releases/)
[![Last Version](https://img.shields.io/github/release/pluralplay/FlClashX/all.svg?style=flat-square)](https://github.com/pluralplay/FlClashX/releases/)
[![License](https://img.shields.io/github/license/pluralplay/FlClashX?style=flat-square)](LICENSE)

[![Channel](https://img.shields.io/badge/Telegram-Chat-blue?style=flat-square&logo=telegram)](https://t.me/FlClashX)

ClashMeta をベースにしたマルチプロキシクライアント **FlClash** のブランチです。インターフェイスはシンプル、オープンソース、広告なしです。

### デスクトップ版

<p style="text-align: center;">
    <img alt="desktop" src="snapshots/desktop.gif">
</p>

### モバイル版

<p style="text-align: center;">
    <img alt="mobile" src="snapshots/mobile.gif">
</p>

## 新機能

- 🛠️ **デフォルト設定を修正しました**
  - プロセス検索モード：有効
  - TUN モード：有効
  - システムプロキシモード：無効
  - プロキシリスト表示方式：リスト
  - QR コードでのサブスクリプション時のカメラ動作を最適化

- 🇷🇺 **ローカライズの修正**
  インストーラにロシア語を追加し、アプリ内ローカライズを再設計しました。

- ✈️ **HWID 送信**
  パネルへ HWID を送信（Remnawave のみ対応）。

- 💻 **お知らせウィジェット**
  「お知らせ」ウィジェットを追加し、パネルのお知らせを自動同期（Remnawave のみ対応）。

- 📺 **TV 版の最適化**
  - 「貼り付け」ボタンでサブスクリプションリンクを素早く追加
  - 「設定切替」ボタンを追加
  - QR コードでモバイル設定をテレビへ直接転送可能

- 🪪 **設定カードのリファクタリング**
  - 使用量バーが流量に応じて色変化（無制限時は非表示）
  - サブスクリプションの有効期限を表示（年が 2099 の場合は「永久サブスクリプション」）
  - 「カスタマーサポート」ボタンを追加し、パネルの `supportUrl` を自動取得
  - パネルから配信される自動更新間隔が正しく適用されるようになりました

- 🪪 **新コンポーネント “Meta-Info” を追加**
  サブスクリプションパラメータをウィジェットに渡し、残量、終了日時、設定名、期限までの日数を表示。

## カスタムフィールドの解析

### 1. `flclashx-widgets`

ダッシュボードウィジェットの順序を制御します。カンマ区切りで指定します。

| 値                | ウィジェット |
| :----------------: | ------------ |
| `announce`         | お知らせ |
| `networkSpeed`     | ネットワーク速度 |
| `outboundModeV2`   | プロキシモード（新版） |
| `outboundMode`     | プロキシモード（旧版） |
| `trafficUsage`     | トラフィック使用量 |
| `networkDetection` | IP と地域の検出 |
| `tunButton`        | TUN ボタン（Desktop のみ） |
| `vpnButton`        | VPN ボタン（Android のみ） |
| `systemProxyButton`| システムプロキシボタン（Desktop のみ） |
| `intranetIp`       | ローカル IP |
| `memoryInfo`       | メモリ情報 |
| `metainfo`         | サブスクリプション情報 |
| `changeServerButton`| サーバー切替ボタン |
| `serviceInfo`      | サービス情報（`flclashx-servicename` と併用） |

**例**

```bash
flclashx-widgets: announce,metainfo,outboundModeV2,networkDetection
```

### 2. `flclashx-view`

「プロキシページ」の外観を制御します。セミコロン区切りで指定します。

| キー   | 説明               | 可能な値 |
| :----: | ------------------ | -------- |
| `type` | 表示モード         | `list`,`tab` |
| `sort` | ソート方式         | `none`,`delay`,`name` |
| `layout`| レイアウト密度   | `loose`,`standard`,`tight` |
| `icon` | ノードアイコンのスタイル | `none`,`standard`,`icon` |
| `card` | カードサイズ       | `expand`,`shrink`,`min`,`oneline` |

**例**

```bash
flclashx-view: type:list; sort:delay; layout:tight; icon:standard; card:shrink
```

### 3. `flclashx-custom`

スタイルが適用されるタイミングを制御します。

| 値      | 説明 |
| :-----: | ---- |
| `add`   | 初回サブスクリプション追加時のみ適用 |
| `update`| サブスクリプション更新時に毎回適用 |

**例**

```bash
flclashx-custom: update
```

### 4. `flclashx-denywidgets`

`true` に設定するとダッシュボードがロックされ、ユーザーが手動で編集できなくなります。

**例**

```bash
flclashx-denywidgets: true
```

### 5. `flclashx-servicename`

`serviceInfo` コンポーネントのサービス名をカスタマイズします。

**例**

```bash
flclashx-servicename: FlClashX
```

## 使用方法

### Linux

⚠️ 初回使用前に以下の依存関係がインストールされていることを確認してください：

```bash
sudo apt-get install libayatana-appindicator3-dev
sudo apt-get install libkeybinder-3.0-dev
```

### Android

以下のショートカットアクションが登録されています。サードパーティの自動化ツールと併用できます：

```bash
com.follow.clashx.action.START
com.follow.clashx.action.STOP
com.follow.clashx.action.CHANGE
```

## ダウンロード

<a href="https://github.com/pluralplay/FlClashX/releases"><img alt="Get it on GitHub" src="snapshots/get-it-on-github.svg" width="200px"/></a>

## プロジェクトを支援

<p style="text-align: center;">
もしこのプロジェクトが気に入ったら、右上の ⭐️ をクリックしてスターを付けてください！<br>
少額の寄付をご希望の方は、<a href="https://t.me/tribute/app?startapp=dtyh">こちら</a>からご支援いただけます。
</p>

**TON USDT:** `UQDSfrJ_k1BdsknhdR_zj4T3Is3OdMylD8PnDJ9mxO35i-TE`

---

## 翻訳者 / Translator
Japanese : [Heliumray](https://github.com/Heliumray)