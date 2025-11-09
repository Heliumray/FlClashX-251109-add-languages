## Languages / 语言
[**🇺🇸 English**](README.md)  
[**🇷🇺 Russian / Русский**](README_RU.md)  
[**🇯🇵 Japanese / 日本語**](README_JP.md)  
[**🇹🇼 🇭🇰 🇲🇴 Traditional / 繁體中文**](README_HANT.md)

---

## FlClashX

[![Downlaod](https://img.shields.io/github/downloads/pluralplay/FlClashX/total?style=flat-square&logo=github)](https://github.com/pluralplay/FlClashX/releases/)
[![Last Version](https://img.shields.io/github/release/pluralplay/FlClashX/all.svg?style=flat-square)](https://github.com/pluralplay/FlClashX/releases/)
[![License](https://img.shields.io/github/license/pluralplay/FlClashX?style=flat-square)](LICENSE)

[![Channel](https://img.shields.io/badge/Telegram-Chat-blue?style=flat-square&logo=telegram)](https://t.me/FlClashX)

基于 ClashMeta 的多平台代理客户端 FlClash 分支，界面简洁、开源且无广告。

### 桌面端

<p style="text-align: center;">
    <img alt="desktop" src="snapshots/desktop.gif">
</p>

### 移动端

<p style="text-align: center;">
    <img alt="mobile" src="snapshots/mobile.gif">
</p>

## 新增能

- 🛠️ **修复了默认配置**
  - 进程搜索模式：开启
  - TUN 模式：开启
  - 系统代理模式：关闭
  - 代理列表显示方式：列表
  - 优化扫码订阅时的相机行为

- 🇷🇺 **本地化修改**
  安装程序已添加俄语，并重新设计应用内本地化。

- ✈️ **HWID 回传**
  向面板回传 HWID（仅支持 [Remnawave](https://github.com/remnawave/panel)）。

- 💻 **公告组件**
  新增「公告」小部件，自动同步面板公告（仅支持 Remnawave）。

- 📺 **TV 版优化**
  - 支持通过「粘贴」按钮快速添加订阅链接
  - 新增「配置切换」按钮
  - 可通过二维码把移动端配置直接传到电视端

- 🪪 **配置卡片重构**
  - 用量条随流量变化颜色（不限速时隐藏）
  - 显示订阅到期时间（年份为 2099 时显示“永久订阅”）
  - 新增「联系客服」按钮，自动读取面板中的 `supportUrl`
  - 面板下发的自动更新间隔现在能正确生效

- 🪪 **新增组件 “Meta-Info”**
  传递订阅参数到小部件，显示剩余流量、订阅结束时间、配置名称以及距离到期的天数。

## 解析自定义字段

### 1. `flclashx-widgets`

控制仪表盘小部件顺序，用逗号分隔。

|       值       | 小部件 |
| :------------: | ------ |
| `announce`     | 公告 |
| `networkSpeed` | 网络速度 |
| `outboundModeV2` | 代理模式（新版） |
| `outboundMode` | 代理模式（旧版） |
| `trafficUsage` | 流量使用 |
| `networkDetection` | IP 与地区检测 |
| `tunButton`    | TUN 按钮（仅 Desktop） |
| `vpnButton`    | VPN 按钮（仅 Android） |
| `systemProxyButton` | 系统代理按钮（仅 Desktop） |
| `intranetIp`   | 本地 IP |
| `memoryInfo`   | 内存信息 |
| `metainfo`     | 订阅信息 |
| `changeServerButton` | 换服务器按钮 |
| `serviceInfo`  | 服务信息（需配合 `flclashx-servicename`） |

**举个栗子**

```bash
flclashx-widgets: announce,metainfo,outboundModeV2,networkDetection
```

### 2. `flclashx-view`

控制「代理页」外观，分号分隔。

| 键      | 说明               | 可选值 |
| :-----: | ------------------ | ------ |
| `type`  | 显示模式           | `list`,`tab` |
| `sort`  | 排序方式           | `none`,`delay`,`name` |
| `layout`| 布局密度           | `loose`,`standard`,`tight` |
| `icon`  | 节点图标风格       | `none`,`standard`,`icon` |
| `card`  | 卡片尺寸           | `expand`,`shrink`,`min`,`oneline` |

**举个栗子**

```bash
flclashx-view: type:list; sort:delay; layout:tight; icon:standard; card:shrink
```

### 3. `flclashx-custom`

控制样式何时生效。

| 值      | 说明 |
| :-----: | ---- |
| `add`   | 仅在首次添加订阅时应用 |
| `update`| 每次更新订阅时重新应用 |

**举个栗子**

```bash
flclashx-custom: update
```

### 4. `flclashx-denywidgets`

设为 `true` 即锁定仪表盘，禁止用户手动编辑。

**举个栗子**

```bash
flclashx-denywidgets: true
```

### 5. `flclashx-servicename`

自定义 `serviceInfo` 组件的服务名称。

**举个栗子**

```bash
flclashx-servicename: FlClashX
```

## 使用说明

### Linux

⚠️ 首次使用前请确保已安装以下依赖：

```bash
sudo apt-get install libayatana-appindicator3-dev
sudo apt-get install libkeybinder-3.0-dev
```

### Android

已注册以下快捷指令，可配合第三方自动化工具使用：

```bash
com.follow.clashx.action.START
com.follow.clashx.action.STOP
com.follow.clashx.action.CHANGE
```

## 下载

<a href="https://github.com/pluralplay/FlClashX/releases"><img alt="Get it on GitHub" src="snapshots/get-it-on-github.svg" width="200px"/></a>

## 支持项目

<p style="text-align: center;">
如果觉得项目不错，可以在右上角为咱点亮一颗Star⭐️！<br>
如果想要小额赞助，可以 <a href="https://t.me/tribute/app?startapp=dtyh">在这里</a> 进行打赏。
</p>

**TON USDT:** `UQDSfrJ_k1BdsknhdR_zj4T3Is3OdMylD8PnDJ9mxO35i-TE`

---

## 译者 / Translator
Simplified Chinese : [Heliumray](https://github.com/Heliumray)