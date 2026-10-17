<h1 align="center">👁️ Agent Reach</h1>

<p align="center">
  <strong>給你的 AI Agent 一鍵裝上網際網路能力</strong>
</p>

<p align="center">
  當下最穩的接入方式，替你選好、裝好、體檢好——接入方式會換代，你不用操心
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3.10+-green.svg?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+"></a>
</p>

<p align="center">
  <a href="#快速上手">快速開始</a> · <a href="docs/README_en.md">English</a> · <a href="docs/README_ja.md">日本語</a> · <a href="docs/README_ko.md">한국어</a> · <a href="#支援的平臺">支援平臺</a> · <a href="#設計理念">設計理念</a>
</p>

---

## 為什麼需要 Agent Reach？

AI Agent 已經能幫你寫程式碼、改文件、管專案——但你讓它去網上找點東西，它就抓瞎了：

- 📺 "幫我看看這個 YouTube 教程講了什麼" → **看不了**，拿不到字幕
- 🐦 "幫我搜一下推特上大家怎麼評價這個產品" → **搜不了**，Twitter API 要付費
- 📖 "去 Reddit 上看看有沒有人遇到過同樣的 bug" → **403 被封**，伺服器 IP 被拒
- 📕 "幫我看看小紅書上這個品的口碑" → **打不開**，必須登入才能看
- 📺 "B站上有個技術影片，幫我總結一下" → **拿不到**，通用下載工具被 B站風控全面攔截
- 🔍 "幫我在網上搜一下最新的 LLM 框架對比" → **沒有好用的搜尋**，要麼付費要麼質量差
- 🌐 "幫我看看這個網頁寫了啥" → **抓回來一堆 HTML 標籤**，根本沒法讀
- 📦 "這個 GitHub 倉庫是幹嘛的？Issue 裡說了什麼？" → 能用，但認證配置很麻煩
- 📡 "幫我訂閱這幾個 RSS 源，有更新告訴我" → 要自己裝庫寫程式碼

**這些不難實現，但是需要自己折騰配置**

每個平臺都有自己的門檻——要付費的 API、要繞過的封鎖、要登入的賬號、要清洗的資料。你要一個一個去踩坑、裝工具、調配置，光是讓 Agent 能讀個推特就得折騰半天。

**Agent Reach 把這件事變成一句話：**

```
幫我安裝 Agent Reach：https://raw.githubusercontent.com/austin17022/agent-reach/main/docs/install.md
```

複製給你的 Agent，幾分鐘後它就能讀推特、搜 Reddit、看 YouTube、刷小紅書了。

**已經裝過了？更新也是一句話：**

```
幫我更新 Agent Reach：https://raw.githubusercontent.com/austin17022/agent-reach/main/docs/update.md
```

### ✅ 在你用之前，你可能想知道

| | |
|---|---|
| 💰 **完全免費** | 所有工具開源、所有 API 免費。唯一可能花錢的是伺服器代理（$1/月），本地電腦不需要 |
| 🔒 **隱私安全** | Cookie 只存在你本地，不上傳不外傳。程式碼完全開源，隨時可審查 |
| 🔄 **持續換代** | 每個平臺都是「首選 + 備選」多後端路由。某個接入方式失效了，我們換下一個，你無感（2026-06 實例：yt-dlp 被 B站風控封死 → 已切換 bili-cli，使用者零操作） |
| 🤖 **相容所有 Agent** | Claude Code、OpenClaw、Cursor、Windsurf……任何能跑命令列的 Agent 都能用 |
| 🩺 **自帶診斷** | `agent-reach doctor` 一條命令告訴你哪個通、哪個不通、怎麼修 |

---

## 支援的平臺

| 平臺 | 裝好即用 | 配置後解鎖 | 怎麼配 |
|------|---------|-----------|-------|
| 🌐 **網頁** | 閱讀任意網頁 | — | 無需配置 |
| 📺 **YouTube** | 字幕提取 + 影片搜尋 | — | 無需配置 |
| 📡 **RSS** | 閱讀任意 RSS/Atom 源 | — | 無需配置 |
| 🔍 **全網搜尋** | — | 全網語義搜尋 | 自動配置（MCP 接入，免費無需 Key） |
| 📦 **GitHub** | 讀公開倉庫 + 搜尋 | 私有倉庫、提 Issue/PR、Fork | 告訴 Agent「幫我登入 GitHub」 |
| 🐦 **Twitter/X** | 讀單條推文 | 搜尋推文、瀏覽時間線、讀長文 | 告訴 Agent「幫我配 Twitter」 |
| 📺 **B站** | 搜尋 + 影片詳情（bili-cli，無需登入） | 字幕（OpenCLI） | 告訴 Agent「幫我配 B站」 |
| 📖 **Reddit** | —（沒有零配置路徑：匿名介面已被封） | 搜尋 + 讀帖子和評論 | 桌面裝 OpenCLI 用瀏覽器登入態；或 rdt-cli + Cookie |
| 📘 **Facebook** | — | 搜尋、主頁、Feed、群組列表 | 桌面裝 OpenCLI（複用 Chrome 登入態） |
| 📷 **Instagram** | — | 使用者搜尋、Profile、使用者最近帖子、Explore | 桌面裝 OpenCLI（複用 Chrome 登入態） |
| 📕 **小紅書** | — | 搜尋、閱讀、評論 | OpenCLI 只用使用者已有 Chrome 會話；MCP/存量工具用 Cookie-Editor |
| 💼 **LinkedIn** | Jina Reader 讀公開頁面 | Profile 詳情、公司頁面、職位搜尋 | 告訴 Agent「幫我配 LinkedIn」 |
| 🎯 **Boss直聘** | CDP 鏈路體檢 | 搜尋崗位 + JD 全文（專用真 Chrome） | 告訴 Agent「幫我配 Boss直聘」；Agent 開啟專用 Chrome，你手動登入 |
| 💻 **V2EX** | 熱門帖子、節點帖子、帖子詳情+回覆、使用者資訊 | — | 無需配置 |
| 📈 **雪球** | 股票行情、搜尋股票、熱門帖子、熱門股票排行 | — | 告訴 Agent「幫我配雪球」 |
| 🎙️ **小宇宙播客** | — | 播客音訊轉文字（Whisper 轉錄，免費 Key） | 告訴 Agent「幫我配小宇宙播客」 |

> **不知道怎麼配？不用查文件。** 直接告訴 Agent「幫我配 XXX」，它知道需要什麼、會一步一步引導你。
>
> 🍪 Twitter 只接受使用者透過 Cookie-Editor 手工匯出的內容。Agent Reach 不替使用者執行小紅書登入，也不讀取小紅書瀏覽器 Cookie；OpenCLI 只使用使用者已經存在且明確控制的 Chrome 會話。`agent-reach configure xhs-cookies` 不會把 Cookie 注入 OpenCLI / Chrome；沒有現成會話時，改用 Cookie-Editor 匯出後配置 xiaohongshu-mcp / 存量工具。
>
> Twitter Cookie 儲存後僅供 `agent-reach doctor` 檢查配置是否齊全；直接執行上游 `twitter` 命令前，仍需在當前程序環境中顯式設定 `TWITTER_AUTH_TOKEN` 和 `TWITTER_CT0`。
>
> 🔒 Cookie 只存在你本地，不上傳不外傳。程式碼完全開源，隨時可審查。
> 💻 本地電腦不需要代理。代理只有部署在伺服器上才需要（~$1/月）。

---

## 快速上手

> ⚠️ **OpenClaw 使用者請先確認 exec 許可權已開啟**
>
> Agent Reach 依賴 Agent 執行 shell 命令（`pip install`、`mcporter`、`twitter` 等）。如果你的 OpenClaw 使用了預設的 `messaging` 工具配置，Agent 將無法執行命令。**安裝前請先開啟 exec 許可權**：
>
> ```bash
> openclaw config set tools.profile "coding"
> ```
> 或在 `~/.openclaw/openclaw.json` 中設定 `"tools": { "profile": "coding" }`。
> 設定後重啟 Gateway（`openclaw gateway restart`）並開啟新對話即可。其他平臺（Claude Code、Cursor、Windsurf 等）不受此限制。

複製這句話給你的 AI Agent（Claude Code、OpenClaw、Cursor 等）：

```
幫我安裝 Agent Reach：https://raw.githubusercontent.com/austin17022/agent-reach/main/docs/install.md
```

就這一步。Agent 會自己完成剩下的所有事情。

> 🔄 **已安裝過？** 更新也是一句話：
> ```
> 幫我更新 Agent Reach：https://raw.githubusercontent.com/austin17022/agent-reach/main/docs/update.md
> ```

> 🛡️ **預設安全：** `agent-reach install` 預設只檢查環境，不會自動裝系統包或寫入配置：
> ```
> 幫我安全檢查並安裝 Agent Reach：https://raw.githubusercontent.com/austin17022/agent-reach/main/docs/install.md
> ```
> 只有在你明確允許修改系統後，才使用 `agent-reach install --system`。

<details>
<summary>它會做什麼？（點選展開）</summary>

1. **安裝 CLI 工具** — 從本倉庫安裝 `agent-reach` 命令列（自帶 yt-dlp、feedparser；不要從 PyPI 安裝同名包，它不是本專案）
2. **檢查系統基建** — 檢查 Node.js、gh CLI、mcporter，並給出缺失項的安裝方式
3. **按授權安裝與配置** — 僅在顯式傳入 `--system` 時安裝依賴並透過 MCP 接入 Exa
4. **檢測環境** — 判斷是本地電腦還是伺服器，給出對應的配置建議
5. **按授權註冊 SKILL.md** — 僅在顯式 `--system` 時寫入 Agent 的 skills 目錄；預設檢查不改檔案
6. **問你要不要更多** — 預設只啟用 6 個零配置渠道；小紅書、Twitter、Reddit、Facebook、Instagram 這些需要登入態的，Agent 會列選單問你要哪些，點名才裝

安裝完之後，`agent-reach doctor` 一條命令告訴你每個渠道的狀態、當前走哪條路。
</details>

---

## 裝好就能用

不需要任何配置，告訴 Agent 就行：

- "幫我看看這個連結" → `curl https://r.jina.ai/URL` 讀任意網頁
- "這個 GitHub 倉庫是做什麼的" → `gh repo view owner/repo`
- "這個 YouTube 影片講了什麼" → `yt-dlp` 提取字幕
- "B站搜一下 AI 教程" → `bili search`（無需登入）
- "全網搜一下 LLM 框架對比" → Exa 語義搜尋
- "訂閱這個 RSS" → `feedparser` 解析

**不需要記命令。** Agent 讀了 SKILL.md 之後自己知道該調什麼。需要登入的平臺（小紅書、Twitter、Reddit、Facebook、Instagram），告訴 Agent「幫我配 XXX」即可解鎖。

---

## 設計理念

**Agent Reach 是一個能力層（capability layer），不是又一個工具。**

它比任何具體實現高一層——負責**選型、安裝、體檢、路由**，不負責底層讀取本身。讀取由 Agent 直接呼叫上游工具完成，沒有包裝層。

你給一個新 Agent 裝環境的時候，總要花時間去找工具、裝依賴、調配置——Twitter 用什麼讀？Reddit 怎麼登入？小紅書的 CLI 停更了換什麼？每次都要重新踩一遍。Agent Reach 做的事情很簡單：**當下最穩的接入方式，我們替你選好、裝好、體檢好。接入方式會換代（2026 年 3 月一批單平臺 CLI 集體停更，我們換了路由），你不用操心。**

### 🔌 每個平臺 = 首選 + 備選的有序後端列表

換接入方式 = 調整列表順序，不是重寫程式碼。`agent-reach doctor` 會告訴你每個平臺**當前在用哪個後端**。

```
channels/
├── web.py          → Jina Reader
├── twitter.py      → twitter-cli ▸ OpenCLI ▸ bird
├── youtube.py      → yt-dlp
├── github.py       → gh CLI
├── bilibili.py     → bili-cli ▸ OpenCLI ▸ 搜尋 API（yt-dlp 已被 B站風控封死，退役）
├── reddit.py       → OpenCLI ▸ rdt-cli（無零配置路徑，必須登入態）
├── facebook.py     → OpenCLI（桌面瀏覽器登入態）
├── instagram.py    → OpenCLI（桌面瀏覽器登入態）
├── xiaohongshu.py  → OpenCLI ▸ xiaohongshu-mcp ▸ xhs-cli
├── linkedin.py     → mcp-server-linkedin ▸ Jina Reader
├── rss.py          → feedparser
├── exa_search.py   → Exa via mcporter
└── __init__.py     → 渠道註冊（doctor 檢測用）
```

每個渠道檔案按序**真實探測**各候選後端（不只是看命令存不存在），第一個完整可用的當選；壞掉的會給出修復處方。實際的讀取和搜尋由 Agent 直接呼叫上游工具完成。

### 當前選型

| 場景 | 首選 | 備選 | 為什麼這麼選 |
|------|------|------|-----------|
| 讀網頁 | [Jina Reader](https://github.com/jina-ai/reader) | — | 免費，不需要 API Key |
| 讀推特 | [twitter-cli](https://github.com/public-clis/twitter-cli) | [OpenCLI](https://github.com/jackwener/opencli) | 實測搜尋穩定；OpenCLI 走瀏覽器登入態兜底 |
| Reddit | [OpenCLI](https://github.com/jackwener/opencli)（桌面） | [rdt-cli](https://github.com/public-clis/rdt-cli) | 匿名介面已被封、官方 API 審批制——只剩登入態路線 |
| Facebook | [OpenCLI](https://github.com/jackwener/opencli)（桌面） | — | Graph API/Groups API 許可權收緊；瀏覽器登入態是當前最實用路徑 |
| Instagram | [OpenCLI](https://github.com/jackwener/opencli)（桌面） | 官方 Graph API（Business/Creator + 審批） | instaloader 類路徑不穩定；OpenCLI 複用真實瀏覽器會話 |
| YouTube 字幕 + 搜尋 | [yt-dlp](https://github.com/yt-dlp/yt-dlp) | — | 154K Star，YouTube 仍是最佳（注意：不再用於 B站） |
| B站 | [bili-cli](https://github.com/public-clis/bilibili-cli) | OpenCLI ▸ 搜尋 API | yt-dlp 被 B站風控 412 封死（2026-06 實測），bili-cli 無登入可搜可讀 |
| 搜全網 | [Exa](https://exa.ai) via [mcporter](https://github.com/nicobailon/mcporter) | — | AI 語義搜尋，MCP 接入免 Key |
| GitHub | [gh CLI](https://cli.github.com) | — | 官方工具，認證後完整 API 能力 |
| 讀 RSS | [feedparser](https://github.com/kurtmckee/feedparser) | — | Python 生態標準選擇 |
| 小紅書 | [OpenCLI](https://github.com/jackwener/opencli)（桌面） | [xiaohongshu-mcp](https://github.com/xpzouying/xiaohongshu-mcp)（伺服器）▸ xhs-cli | OpenCLI 只用使用者已有會話；其餘後端用 Cookie-Editor 手工匯出 |
| LinkedIn | [mcp-server-linkedin](https://github.com/stickerdaniel/linkedin-mcp-server) | Jina Reader | MCP 服務，瀏覽器自動化 |

> 📌 這些都是「當前選型」，基於真機實測定期複核。某條路失效了我們換下一條——`agent-reach doctor` 永遠告訴你現在走的是哪條。

---

## 安全性

Agent Reach 在設計上重視安全：

| 措施 | 說明 |
|------|------|
| 🔒 **憑據本地儲存** | Cookie、Token 只存在你本機 `~/.agent-reach/config.yaml`，檔案許可權 600（僅所有者可讀寫），不上傳不外傳 |
| 🛡️ **預設安全** | `agent-reach install` 預設不修改系統；只有顯式 `--system` 才安裝外部工具和寫入配置 |
| 👀 **完全開源** | 程式碼透明，隨時可審查。所有依賴工具也是開源專案 |
| 🔍 **Dry Run** | `agent-reach install --dry-run` 預覽所有操作，不做任何改動 |
| 🧩 **可插拔架構** | 不信任某個元件？換掉對應的 channel 檔案即可，不影響其他 |

### 🍪 Cookie 安全建議

> ⚠️ **封號風險提醒：** 使用 Cookie 登入的平臺（Twitter、小紅書等），透過指令碼/API 呼叫**存在被平臺檢測並封號的風險**。請務必使用**專用小號**，不要用你的主賬號。

需要 Cookie 或登入態的平臺（Twitter、小紅書、Reddit、Facebook、Instagram 等）建議使用**專用小號**，不要用主賬號。原因有二：
1. **封號風險** — 平臺可能檢測到非正常瀏覽器的 API 呼叫行為，導致賬號被限制或封禁
2. **安全風險** — Cookie 等同於完整登入許可權，用小號可以在憑據洩露時限制影響範圍

### 📦 安裝方式

| 方式 | 命令 | 適合場景 |
|------|------|---------|
| 預設安全檢查 | `agent-reach install --env=auto` | 所有環境；只讀檢查並列出缺失項 |
| 顯式安裝系統依賴 | `agent-reach install --env=auto --system` | 你明確允許修改當前機器時 |
| 相容安全參數 | `agent-reach install --env=auto --safe` | 與預設行為相同 |
| 僅預覽 | `agent-reach install --env=auto --dry-run` | 先看看會做什麼 |

### 🗑️ 解除安裝

```bash
agent-reach uninstall
```

會清除：`~/.agent-reach/`（含所有 token/cookie）、各 Agent 的 skill 檔案、mcporter 中的 MCP 配置。

```bash
# 只預覽，不實際刪除
agent-reach uninstall --dry-run

# 只刪 skill 檔案，保留 token 配置（重裝時用）
agent-reach uninstall --keep-config
```

解除安裝 Python 包本身：`pip uninstall agent-reach`

---

## 致謝

[OpenCLI](https://github.com/jackwener/opencli) · [twitter-cli](https://github.com/public-clis/twitter-cli) · [rdt-cli](https://github.com/public-clis/rdt-cli) · [xiaohongshu-mcp](https://github.com/xpzouying/xiaohongshu-mcp) · [xhs-cli](https://github.com/jackwener/xiaohongshu-cli) · [bili-cli](https://github.com/public-clis/bilibili-cli) · [yt-dlp](https://github.com/yt-dlp/yt-dlp) · [Jina Reader](https://github.com/jina-ai/reader) · [Exa](https://exa.ai) · [mcporter](https://github.com/nicobailon/mcporter) · [feedparser](https://github.com/kurtmckee/feedparser) · [mcp-server-linkedin](https://github.com/stickerdaniel/linkedin-mcp-server)

## 問題回報

Bug 回報與功能需求請使用 [GitHub Issues](https://github.com/austin17022/agent-reach/issues)。

## License

[MIT](LICENSE)

---

<sub>Based on Agent-Reach by Panniantong (MIT)</sub>
