## Languages / 語言
[**🇺🇸 English**](README.md)  
[**🇷🇺 Russian / Русский**](README_RU.md)  
[**🇯🇵 Japanese / 日本語**](README_JP.md)  
[**🇨🇳 Simplified / 简体中文**](README_ZH.md)  

---

## FlClashX

[![下載](https://img.shields.io/github/downloads/pluralplay/FlClashX/total?style=flat-square&logo=github)](https://github.com/pluralplay/FlClashX/releases/)
[![最新版本](https://img.shields.io/github/release/pluralplay/FlClashX/all.svg?style=flat-square)](https://github.com/pluralplay/FlClashX/releases/)
[![開源許可證](https://img.shields.io/github/license/pluralplay/FlClashX?style=flat-square)](LICENSE)

[![加入頻道](https://img.shields.io/badge/Telegram-Chat-blue?style=flat-square&logo=telegram)](https://t.me/FlClashX)

基於 **ClashMeta** 的多代理客戶端 **FlClash** 分支，介面簡潔、開源且無廣告。

### 桌面端

<p style="text-align: center;">
    <img alt="desktop" src="snapshots/desktop.gif">
</p>

### 行動端

<p style="text-align: center;">
    <img alt="mobile" src="snapshots/mobile.gif">
</p>

## 新增功能

- 🛠️ **修復了預設設定**
  - 進程搜尋模式：開啟
  - TUN 模式：開啟
  - 系統代理模式：關閉
  - 代理列表顯示方式：列表
  - 優化掃描訂閱時的相機行為

- 🇷🇺 **本地化修改**
  安裝程式已加入俄語，並重新設計應用內本地化。

- ✈️ **HWID 回傳**
  向面板回傳 HWID（僅支援 [Remnawave](https://github.com/remnawave/panel)）。

- 💻 **公告元件**
  新增「公告」小部件，會自動同步面板公告（僅支援 Remnawave）。

- 📺 **TV 版優化**
  - 支援透過「貼上」按鈕快速新增訂閱連結
  - 新增「配置切換」按鈕
  - 可透過 QR Code 把行動端配置直接傳到電視端

- 🪪 **配置卡片重構**
  - 用量條隨流量變化顏色（不限速時隱藏）
  - 顯示訂閱到期時間（年份為 2099 時顯示「永久訂閱」）
  - 新增「聯絡客服」按鈕，會自動讀取面板中的 `supportUrl`
  - 面板下發的自動更新間隔現在能正確生效

- 🪪 **新增元件 “Meta-Info”**
  傳遞訂閱參數到小部件，顯示剩餘流量、訂閱結束時間、配置名稱以及距離到期的天數。

## 解析自訂欄位

### 1. `flclashx-widgets`

控制儀表板小工具順序，用逗號分隔。

|       值       | 小工具 |
| :------------: | ------ |
| `announce`     | 公告 |
| `networkSpeed` | 網路速度 |
| `outboundModeV2` | 代理模式（新版） |
| `outboundMode` | 代理模式（舊版） |
| `trafficUsage` | 流量使用 |
| `networkDetection` | IP 與地區偵測 |
| `tunButton`    | TUN 按鈕（僅 Desktop） |
| `vpnButton`    | VPN 按鈕（僅 Android） |
| `systemProxyButton` | 系統代理按鈕（僅 Desktop） |
| `intranetIp`   | 本地 IP |
| `memoryInfo`   | 記憶體資訊 |
| `metainfo`     | 訂閱資訊 |
| `changeServerButton` | 換伺服器按鈕 |
| `serviceInfo`  | 服務資訊（需配合 `flclashx-servicename`） |

**舉個例子**

```bash
flclashx-widgets: announce,metainfo,outboundModeV2,networkDetection
```

### 2. `flclashx-view`

控制「代理頁」外觀，分號分隔。

| 鍵      | 說明               | 可選值 |
| :-----: | ------------------ | ------ |
| `type`  | 顯示模式           | `list`,`tab` |
| `sort`  | 排序方式           | `none`,`delay`,`name` |
| `layout`| 版面密度           | `loose`,`standard`,`tight` |
| `icon`  | 節點圖示風格       | `none`,`standard`,`icon` |
| `card`  | 卡片尺寸           | `expand`,`shrink`,`min`,`oneline` |

**舉個例子**

```bash
flclashx-view: type:list; sort:delay; layout:tight; icon:standard; card:shrink
```

### 3. `flclashx-custom`

控制樣式何時生效。

| 值      | 說明 |
| :-----: | ---- |
| `add`   | 僅在首次新增訂閱時套用 |
| `update`| 每次更新訂閱時重新套用 |

**舉個例子**

```bash
flclashx-custom: update
```

### 4. `flclashx-denywidgets`

設為 `true` 即鎖定儀表板，禁止使用者手動編輯。

**舉個例子**

```bash
flclashx-denywidgets: true
```

### 5. `flclashx-servicename`

自訂 `serviceInfo` 元件的服務名稱。

**舉個例子**

```bash
flclashx-servicename: FlClashX
```

## 使用說明

### Linux

⚠️ 首次使用前請確保已安裝以下相依套件：

```bash
sudo apt-get install libayatana-appindicator3-dev
sudo apt-get install libkeybinder-3.0-dev
```

### Android

已註冊以下快捷指令，可配合第三方自動化工具使用：

```bash
com.follow.clashx.action.START
com.follow.clashx.action.STOP
com.follow.clashx.action.CHANGE
```

## 下載

<a href="https://github.com/pluralplay/FlClashX/releases"><img alt="Get it on GitHub" src="snapshots/get-it-on-github.svg" width="200px"/></a>

## 支援

<p style="text-align: center;">
如果您支持我們所做，可以在右上角為咱點亮一顆 Star⭐️！<br>
如果想要小額贊助，可以 <a href="https://t.me/tribute/app?startapp=dtyh">在這裡</a> 進行打賞。
</p>

**TON USDT:** `UQDSfrJ_k1BdsknhdR_zj4T3Is3OdMylD8PnDJ9mxO35i-TE`

---

## 譯者 / Translator
Traditional Chinese : [Heliumray](https://github.com/Heliumray)