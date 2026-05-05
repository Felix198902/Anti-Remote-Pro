<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=zh-TW"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**專為 [Antigravity](https://antigravity.dev)（Google AI 程式設計助理）打造的隱私至上、防封鎖、支援 Telegram 遠端操控的自動駕駛擴充功能。**
**一個 Google 帳號，無限裝置同步。**

### [🌐 造訪官網 &nbsp;·&nbsp; 立即下載 →](https://antigravity.apiai.eu.cc/?lang=zh-TW)

<sub>
  📖 <b>其他語言版本：</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <a href="./README.zh-CN.md">简体中文</a> &nbsp;·&nbsp;
  <b>繁體中文</b> &nbsp;·&nbsp;
  <a href="./README.ja.md">日本語</a> &nbsp;·&nbsp;
  <a href="./README.ko.md">한국어</a> &nbsp;·&nbsp;
  <a href="./README.es.md">Español</a> &nbsp;·&nbsp;
  <a href="./README.fr.md">Français</a> &nbsp;·&nbsp;
  <a href="./README.de.md">Deutsch</a> &nbsp;·&nbsp;
  <a href="./README.pt.md">Português</a> &nbsp;·&nbsp;
  <a href="./README.ru.md">Русский</a> &nbsp;·&nbsp;
  <a href="./README.ar.md">العربية</a> &nbsp;·&nbsp;
  <a href="./README.hi.md">हिन्दी</a>
</sub>

</div>

自動接受 Agent 步驟、終端機指令、檔案編輯與權限提示，讓 Agent 全程免點擊交付工作——所有資料都保留在您本機，並且您可以用手機遠端操控每一台機器。

> 💡 **想要快速開始？** [官網](https://antigravity.apiai.eu.cc/?lang=zh-TW) 提供完整指南、產品截圖、Pro 訂價與最新版 `.vsix` 下載——共 12 種語言。

---

## 🔥 為什麼選擇 Anti-Remote-Pro

### 🔒 1. 絕對隱私 —— 您的程式碼永遠不離開本機

- **100% 本機運作。** 所有按鈕辨識、DOM 掃描、指令過濾都在您的 VS Code / Antigravity 行程內部完成。任何 prompt、截圖、diff 都不會離開這台機器。
- **僅限 localhost 的偵錯連接埠。** CDP 嚴格繫結在 `127.0.0.1:9333`。區域網路、咖啡廳 Wi-Fi、共享辦公空間網路裡的任何外部主機都無法連線——不是靠承諾，是靠 socket 繫結直接保證。
- **零遙測。** 自動接受核心不發送任何分析請求、當機報告、「匿名使用統計」。唯一的對外流量是：（a）您主動配對的 Telegram；（b）驗證金鑰的授權伺服器。
- **目標白名單繫結。** CDP 層**只**會附加到符合 Agent 面板的 `vscode-webview://` 目標。它拒絕附加到您的其他分頁、瀏覽器子 Agent 或任何非 Antigravity 的 Chromium 目標。
- **核心載荷簽章驗證。** Pro 核心引擎以 Ed25519 簽章封包的形式取得，在 Node worker 內完成驗證後**記憶體中**編譯——從不寫入磁碟、不可被中間人竄改。
- **不修改 Antigravity 任何檔案。** 我們不打 patch、不重新打包、不 hook Antigravity 的二進位檔。純外部 CDP——解除安裝即零痕跡。

### 📱 2. Telegram 遠端操控 —— 隨時隨地駕馭 Antigravity

將您的 IDE 與 Telegram 機器人一次配對，您的手機就變成了 Agent 的完整遙控器：

- **`/prompt <文字>`** —— 從地球上任何角落向當前對話傳送新 prompt。自動拼接 Telegram 4096 字元分片訊息。
- **`/peek [N]`** —— 直接在 Telegram 裡閱讀 Agent 最新回覆，不必喚醒筆電。
- **附說明傳送圖片** —— 將截圖附加到 prompt，隨時隨地做視覺化除錯。
- **`/pause` & `/resume`** —— 從手機切換全域開關。跨視窗檔案鎖確保每個 Antigravity 視窗即時回應。
- **`/stop`** —— 停止當前正在生成的回應。
- **HMAC 簽章指令。** 每條 Telegram 指令都通過裝置層級 HMAC 金鑰驗證。即使 Telegram 聊天外洩，也**無法**控制您的 IDE。
- **單一主控選舉。** 當您同時開了 5 個 Antigravity 視窗時，只有一個會贏得主控鎖處理指令——不會重複傳送，不會有競爭條件。

### 🛡️ 3. 業界首創的防封鎖策略

大多數自動點擊器之所以觸發帳號標記，是因為它們用固定節奏打 endpoint，並在使用者還在打字時就搶著點擊。Anti-Remote-Pro 的工程思路恰恰相反：

- **擬人化節奏。** 主動輪詢間隔 500 ms，加 **±20% 隨機抖動** + 連續錯誤時指數退避（上限 30 s）。沒有機械般完美的節拍可以被指紋辨識。
- **閒置智慧休眠。** 沒有活躍 CDP 工作階段時，引擎降到 5 秒心跳——離開時幾乎零 IPC 開銷。
- **20 秒使用者活躍寬限視窗。** 如果使用者正在聊天框打字、捲動 webview 或移動游標，**所有自動點擊都會延後**。機器人真的會等您停下來再點，從不在您閱讀時搶點。
- **不做二進位修補。** Antigravity 的檔案、settings.json、使用者資料目錄對本擴充功能都是唯讀的。官方自動更新和完整性校驗可以完整通過，因為我們什麼都沒改。
- **CDP 僅 loopback。** 沒有 TCP 監聽，沒有遠端轉發。`--remote-debugging-port=9333` 這個 flag 就是標準 Electron 偵錯參數——Microsoft、Google、JetBrains 內部用的是同一個。
- **硬性指令防火牆。** 內建黑名單 + 可選嚴格白名單 + 50+ 精選的**安全預設**（rm -rf、強制 push、drop database、fork 炸彈、磁碟擦除、登錄檔刪除等）。即使 Agent 堅持要執行，機器人也會**拒絕**跑這些破壞性指令。
- **展開類按鈕一次一工作階段。** 消除「無限重開」迴圈，避免觸發反濫用啟發。
- **即時讓位給官方瀏覽器子 Agent。** 當 AG 自身的瀏覽器工具啟用 9222 連接埠時，我們的 worker 立即脫離並讓出——不會有連接埠衝突，不會有雙重附加的指紋。

> 綜合效果：從 Agent 後端的視角看，您就是一個手速略快但彬彬有禮的普通人類使用者。

### 🌍 4. 多語言支援 —— 12 種語言，覆蓋數十億使用者

Anti-Remote-Pro 提供完整的 UI 在地化（指令、設定、儀表板、通知、Telegram 回覆）。可以在儀表板的下拉選單手動選擇，也可以讓擴充功能自動偵測您的 IDE 語言。

| # | 語言 | 本地名稱 | 主要地區 |
|---|---|---|---|
| 1 | 英語 | English | 🇺🇸 美國 · 🇬🇧 英國 · 🇨🇦 加拿大 · 🇦🇺 澳洲 · 🇮🇪 愛爾蘭 · 🇳🇿 紐西蘭 · 🇿🇦 南非 · 🇸🇬 新加坡 · 🇮🇳 印度（IT） |
| 2 | 簡體中文 | 简体中文 | 🇨🇳 中國大陸 · 🇸🇬 新加坡 · 🇲🇾 馬來西亞 |
| 3 | 繁體中文 | 繁體中文 | 🇹🇼 臺灣 · 🇭🇰 香港 · 🇲🇴 澳門 |
| 4 | 西班牙語 | Español | 🇪🇸 西班牙 · 🇲🇽 墨西哥 · 🇦🇷 阿根廷 · 🇨🇴 哥倫比亞 · 🇨🇱 智利 · 🇵🇪 秘魯 · 🇻🇪 委內瑞拉 · +14 國 |
| 5 | 法語 | Français | 🇫🇷 法國 · 🇨🇦 加拿大（魁北克） · 🇧🇪 比利時 · 🇨🇭 瑞士 · 🇱🇺 盧森堡 · 🇲🇨 摩納哥 · 大部分西非與中非國家 |
| 6 | 印地語 | हिन्दी | 🇮🇳 印度 · 🇫🇯 斐濟 |
| 7 | 葡萄牙語（巴西） | Português | 🇧🇷 巴西 · 🇵🇹 葡萄牙 · 🇦🇴 安哥拉 · 🇲🇿 莫三比克 |
| 8 | 俄語 | Русский | 🇷🇺 俄羅斯 · 🇧🇾 白俄羅斯 · 🇰🇿 哈薩克 · 🇰🇬 吉爾吉斯 · 🇺🇿 烏茲別克 · 🇺🇦 烏克蘭 |
| 9 | 阿拉伯語 | العربية（從右向左） | 🇸🇦 沙烏地 · 🇦🇪 阿聯 · 🇪🇬 埃及 · 🇶🇦 卡達 · 🇰🇼 科威特 · 🇧🇭 巴林 · 🇴🇲 阿曼 · 🇯🇴 約旦 · 🇲🇦 摩洛哥 · 🇩🇿 阿爾及利亞 · 🇹🇳 突尼西亞 · 🇮🇶 伊拉克 · +10 國 |
| 10 | 日語 | 日本語 | 🇯🇵 日本 |
| 11 | 德語 | Deutsch | 🇩🇪 德國 · 🇦🇹 奧地利 · 🇨🇭 瑞士 · 🇱🇮 列支敦斯登 · 🇱🇺 盧森堡 |
| 12 | 韓語 | 한국어 | 🇰🇷 韓國 |

- **自動偵測** 跟隨 `vscode.env.language`——擴充功能首次啟動時即刻使用您的 locale。
- **手動切換** 透過儀表板語言下拉選單（切換後持久儲存，重新載入仍生效）。
- **RTL 感知** —— 阿拉伯語 UI 會自動翻轉版面方向（`dir="rtl"`）。
- **自訂關鍵字覆蓋** —— `autoAcceptV2.customButtonTexts` 允許您為尚未翻譯的 UI 字串追加在地化按鈕文案（例如 `["toujours autoriser", "siempre permitir"]`）。

### 🔗 5. Google 登入多裝置同步 —— 一個帳號，所有機器

**一次 Google 登入**，Anti-Remote-Pro 跟隨您到任何裝置——桌機、筆電、家用 PC、公司工作站，Windows、macOS、Linux 都支援。

- **一鍵 Google OAuth。** `Anti-Remote-Pro: Login with Google` 會開啟瀏覽器完成標準 Google OAuth 流程，然後透過安全的 `vscode://Pro.antigravity-autoaccept/auth` URI 回呼返回 IDE。無需複製貼上授權金鑰，無需電子郵件流程。
- **Pro 授權跨裝置自動同步。** 您的訂閱繫結的是 Google 帳號，不是單台機器。在第 2 台、第 3 台、第 10 台裝置上安裝——登入即刻解鎖 Pro。授權伺服器每次重新整理都會針對您的帳號驗證每台 `machineId`。
- **無限裝置並行執行。** 工作筆電、家用桌機、遠端開發機、為每個客戶準備的虛擬機——都可以在同一帳號下並行跑 Anti-Remote-Pro。
- **並行艦隊。** 每台裝置獨立運作，擁有自己的 CDP / Swarm / 指令防火牆。您的筆電可以處理對話 A，桌機處理對話 B，互不搶焦點。
- **每裝置獨立 Telegram 配對。** 每台機器單獨與 Telegram 機器人配對，得到自己的 HMAC 金鑰。配對流程中可以為它們命名（如 "MacBook"、"WorkPC"），然後在同一個 Telegram 聊天裡分別定址。
- **同機跨視窗協同。** 當同一台機器上開了多個 Antigravity 視窗時，一個檔案鎖協定在 1 秒內同步所有視窗的暫停/恢復狀態——不重複點擊、不互相爭搶。
- **即時撤銷。** `Anti-Remote-Pro: Logout` 清除本機 token 並通知伺服器作廢該裝置。遺失筆電？在另一台機器登出 + `Refresh Pro Status`，舊機器立刻失效。
- **Refresh Pro Status。** 改了方案或續費了訂閱？一條指令重新拉取最新權益——無需重灌、無需重啟。

> 實際用法：在 3 台電腦上各登入一次，每台配對同一個 Telegram 機器人，您的手機就是整個程式設計艦隊的中央遙控器。

---

## ⚡ 核心能力一覽

- **自動點擊** Run / Accept / Always Allow / Allow this conversation / Continue / Retry 這些 Agent 面板按鈕——基於優先順序，`Run` 永遠勝過 `Accept`。
- **自動接受檔案編輯**，一鍵切換——隨時關閉以手動 review diff。
- **指令防火牆** —— 阻擋模式或嚴格白名單模式，兩者都用詞邊界比對。
- **安全預設** —— 一鍵匯入 50+ 破壞性指令模式（檔案系統擦除、磁碟格式化、強制 push、DB drop、fork 炸彈）。
- **Swarm 模式（Pro）** —— 自動在 Agent Manager 的待處理對話間輪換，後台無人值守執行。
- **Telegram Remote（Pro）** —— 完整 IDE 遠端：`/prompt`、`/peek`、圖片 prompt、`/pause`、`/resume`、`/stop`，帶 HMAC 鑑權。
- **Google 登入 + 多裝置同步（Pro）** —— 一個 Google 帳號、無限裝置；`vscode://` URI handler OAuth 回呼；裝置層級授權驗證。
- **跨視窗暫停** —— 在一個 Antigravity 視窗按下暫停，透過檔案鎖在 <1 秒內廣播到其他所有視窗。
- **活動紀錄 + 儀表板** —— 即時查看每次點擊、每個 CDP 工作階段、每條 Telegram 指令。
- **診斷傾印** —— 一鍵把結構化除錯資訊複製到剪貼簿，方便一條訊息走完支援流程。
- **捷徑自動修復** —— Windows `.lnk` patch 工具（桌面 / 開始功能表 / 工作列），補上 `--remote-debugging-port` flag。
- **心跳自癒** —— 被 webview 導覽 / 熱重載清除的 MutationObserver 會在 10 秒內偵測並自動重新注入。

---

## 它做什麼

當 Antigravity 的 Agent 提議檔案編輯、終端機指令或請求工具權限時，本擴充功能會自動接受這些操作，讓您不用一個個按鈕去點。

**兩種策略，零干擾：**

| 策略 | 處理內容 | 實作方式 |
|---|---|---|
| **VS Code 指令** (500 ms + 抖動) | Agent 步驟、終端機指令 | 呼叫 Antigravity 原生的 accept 指令 |
| **CDP + MutationObserver** (事件驅動) | Run、Accept、Always Allow、Continue、Retry | 每個目標注入一次指令稿，DOM 變化即時回應 |

---

## 安裝設定

### 1. 啟用偵錯模式（必要）

本擴充功能需要 Chrome DevTools Protocol 來點擊權限按鈕。啟動 Antigravity 時加上：

```
--remote-debugging-port=9333
```

> **為什麼用 9333？** Antigravity 內建的 Browser Control（工具列裡的 Chrome 按鈕）預設用 9222。用相同連接埠會在 macOS/Linux 上觸發 `EADDRINUSE` 衝突。用 9333 徹底迴避這個問題。

<details>
<summary><b>🪟 Windows</b></summary>

**自動方式：** 首次啟動時，擴充功能會偵測連接埠是否打開，如果沒打開會提示 **"Auto-Fix Shortcut"**——點一下就會自動給您的 `.lnk` 捷徑打 patch。

**手動方式：** 右鍵 Antigravity 捷徑 → 內容 → 在 Target 後追加：
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**方案 1 —— Automator 應用（推薦）：**
1. 開啟 **Automator** → 新增文件 → **應用程式**
2. 在資料庫裡搜尋 **"執行 Shell 指令稿"**
3. 貼上：`open -a "Antigravity" --args --remote-debugging-port=9333`
4. 另存為 "AntiGravity Launcher" 放到桌面或應用程式資料夾

**方案 2 —— 終端機別名**（加到 `~/.zshrc`）：
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **注意：** App 名字必須完全一致。用 `ls /Applications/ | grep -i anti` 檢查。

**方案 3 —— 直接 Electron 二進位**（如果 `open -a` 不能正確傳參）：
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**方案 1 —— 編輯 `.desktop` 檔案：**
```bash
# 找到它：
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# 編輯 Exec 列：
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**方案 2 —— Shell 別名**（加到 `~/.bashrc` 或 `~/.zshrc`）：
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**方案 3 —— Wrapper 指令稿：**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. 安裝擴充功能

**透過 VSIX（推薦）：**
1. 取得最新的 `.vsix` 套件
2. 在 Antigravity 裡：`Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. 選中下載的檔案
4. Reload Window

**手動安裝：**
1. 把 `src/` 目錄、`package.json`、`package-lock.json` 拷到：
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. 在該目錄裡跑 `npm install`（安裝 `ws` 相依套件）
3. Reload Window

---

## 使用方法

### 基礎指令

- **切換開關：** 點擊狀態列的 `⚡ Auto: ON` / `✕ Auto: OFF`
- **或者：** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **儀表板：** 點擊狀態列的儀表板圖示，查看 CDP 狀態、活躍工作階段、活動紀錄和語言選擇器
- **紀錄：** Output 面板 → `Anti-Remote-Pro`

### Pro 指令

所有 Pro 功能都可以透過指令面板（`Ctrl+Shift+P`）觸發：

| 指令 | 作用 |
|---|---|
| `Anti-Remote-Pro: Login with Google` | 登入以跨裝置同步 Pro 授權 |
| `Anti-Remote-Pro: Logout` | 清除本機授權 + 已登入帳號 |
| `Anti-Remote-Pro: Refresh Pro Status` | 強制向伺服器重新驗證授權 |
| `Anti-Remote-Pro: Connect Telegram Bot` | 啟動配對流程——開啟 Telegram 裡的機器人，點 **Start** 即可繫結本機 |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | 撤銷本機的 HMAC 金鑰 |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | 強制重新下載簽章的核心載荷 |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | 全域開關（同時繫結 `Ctrl+Shift+S`） |
| `Anti-Remote-Pro: Fix Missing Conversations` | 當側邊欄對話索引不同步時，重新播種 Swarm 索引 |

> **提示：** `Ctrl+Shift+S` 是隊友突然加入您工作階段時，暫停/恢復 Swarm + 自動接受的最快方式。

---

## 多 Agent 工作流

### ⚠️ Agent Manager 限制（未啟用 Swarm 模式時）

Antigravity 的 Agent Manager 使用**單個共享 webview**——只有當前對話的 DOM 會被渲染，背景對話完全 unmount。沒有 Swarm 模式時，VS Code Commands API 和 CDP 都只能觸及當前可見的對話。

### ✅ 解決方案：Swarm 模式（Pro）

Swarm 模式透過在所有待處理對話間輪換焦點來解決這個問題，讓數十個後台 Agent 無人值守執行：

- 掃描側邊欄每一個對話，挑出有待處理工作的那一個。
- 遵守您的閒置秒數設定，絕不在您打字時搶焦點。
- 跨視窗感知：任一視窗暫停會透過檔案鎖廣播暫停所有視窗。
- 預設安全：簽章的核心載荷、指令防火牆仍然生效。

### 備選方案：複製工作區（免費）

如果您沒有 Pro 授權，仍然可以並行跑 2–3 個 Agent：

1. 點 **File → Duplicate Workspace**
2. 這會開啟連接到同一專案的第二個 Antigravity 視窗
3. 在視窗 1 開一個聊天，在視窗 2 再開一個
4. 每個視窗有自己獨立的 webview——擴充功能會在**兩個視窗同時**自動點擊按鈕

---

## 設定項

| 設定 | 預設值 | 範圍 | 說明 |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | 基礎輪詢間隔（毫秒，自動附加 ±20% 抖動） |
| `autoAcceptV2.customButtonTexts` | `[]` | application | 額外的按鈕文案，用於 i18n 或自訂 prompt（例如 `["toujours autoriser"]`） |
| `autoAcceptV2.cdpPort` | `9333` | machine | CDP 連接埠（預設避開 AG Browser Control 的 9222） |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | 自動接受檔案編輯（關閉後需手動 review diff） |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Agent 遇到錯誤或呼叫限制時自動點 Retry / Continue |
| `autoAcceptV2.blockedCommands` | `[]` | application | 絕不自動執行的指令（例如 `rm`、`git push`、`npm publish`） |
| `autoAcceptV2.allowedCommands` | `[]` | application | 如設定，**僅**這些指令會被自動執行（白名單模式） |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Pro 授權金鑰——解鎖 Swarm 模式 + Telegram Remote |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Swarm 跳轉到待處理對話前，要求使用者的無操作秒數（3–60） |

> **提示：** 設定支援熱重載，改完立即生效，無需重啟。

---

## 工作原理

### 持久化 CDP + MutationObserver

擴充功能保持一個**瀏覽器層級的持久化 WebSocket** 連線到 Chromium 的 DevTools Protocol。它不是每 1.5 秒輪詢一次，而是給每個目標注入一次 **MutationObserver** 載荷。當 React 掛載新的按鈕元素時，observer 即時反應，並帶 100ms 前沿節流以避免串流輸出時的 CPU 峰值。擴充功能使用**嚴格白名單目標過濾器**——只附加到 `vscode-webview://` 目標，偵測到 AG 瀏覽器子 Agent 時自動讓出 CDP 連接埠，防止 ArrayBuffer 衝突。

### 單趟 DOM 掃描

按鈕掃描器每個週期只走一次 DOM 樹，對每個節點同時檢查所有關鍵字。時間複雜度是 O(D) 而不是 O(N×D)，避免了關鍵字多時 UI 卡頓。基於優先順序的比對確保 `Run` 總是優先於 `Accept`，`Accept` 總是優先於 `Allow`，與 DOM 順序無關。

### Webview 守衛

Antigravity 的 Agent 面板執行在隔離的 Chromium 行程（OOPIF）裡。注入的指令稿在 `scanAndClick()` 內部使用延遲的 `isAgentPanel()` 檢查——每次掃描時動態驗證 `.react-app-container` 是否存在，而不是注入時就校驗。這避免了 `targetCreated` 時 DOM 尚未 hydrate 的競爭條件。

### 心跳自癒

CDP 連線每個心跳週期（10 秒）會驗證現有工作階段。如果某個工作階段的 MutationObserver 已死（執行上下文被 webview 導覽或 React 熱重載清除），它會自動重新注入 observer——無需重新連線。連續 3 次不可達的工作階段會被乾淨地分離並清理。

### 展開按鈕迴圈預防

展開類按鈕（例如 browser preview 的 "Expand"）採用**每個工作階段點一次**規則：一旦被點擊，在該 CDP 工作階段中永久被抑制（透過一個 `expandedOnce` Set）。這防止了關閉展開面板又觸發重新點擊的無限重開迴圈。新的 Agent 對話開始時狀態自然重置。

### 按鈕辨識

在 Agent 面板內，一個 `TreeWalker` 透過 `startsWith` + **詞邊界檢查**來按文字內容搜尋按鈕（防止誤比對，例如 `accept-test.js` 不會比對到 `accept`）：

| 優先順序 | 文字 | 比對對象 |
|---|---|---|
| 1 | `run` | "Run Alt+d" 按鈕（不是 "Always run ^" 下拉） |
| 2 | `accept` | Accept 按鈕 |
| 3 | `always allow` | 權限提示 |
| 4 | `allow this conversation` | 對話層級權限 |
| 5 | `allow` | 權限提示 |
| 6 | `retry` | Retry 提示 |
| 7 | `continue` | Agent 呼叫次數限制後的繼續 |

### 指令過濾

黑名單和白名單都用**詞邊界比對**對 Run 按鈕上方的程式碼區塊做比對。例如，封鎖 `rm` 會阻止 `rm -rf /tmp`，但**不會**阻止 `yarn format` 或 `npm run build`。

---

## 推薦的封鎖指令

儀表板裡有一個 **Load Safety Presets** 按鈕，會批次匯入 50+ 破壞性指令模式，涵蓋檔案系統擦除、磁碟格式化、資料庫刪除、強制 push、fork 炸彈等。

**一鍵操作：** 開啟儀表板 → 點 **Load Recommended Safety Presets**。

**批次貼上：** 黑/白名單輸入框支援**逗號分隔**值——貼一串按 Enter 即可。

<details>
<summary><b>📋 手動：複製到 settings.json</b></summary>

把下面這段加到您的 `settings.json`（`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`）：

```json
"autoAcceptV2.blockedCommands": [
  "rm -rf /",
  "rm -rf /*",
  "rm -rf ~",
  "rm -rf .*",
  "rm -rf .git",
  "rmdir /s /q c:\\",
  "rmdir /s /q d:\\",
  "rd /s /q c:\\",
  "rd /s /q d:\\",
  "del /f /s /q c:\\",
  "del /f /s /q d:\\",
  "remove-item -recurse -force c:\\",
  "remove-item -recurse -force d:\\",
  "format c:",
  "format d:",
  "diskpart",
  "clear-disk",
  "format-volume",
  "remove-partition",
  "initialize-disk",
  "dd if=/dev/zero",
  "dd if=/dev/urandom",
  "dd if=/dev/random",
  "mkfs.",
  "wipefs",
  "shred ",
  "vssadmin delete shadows",
  "reg delete hk",
  "chmod -r 777 /",
  "chown -r root /",
  "sudo su",
  "su -",
  "| bash",
  "| sh",
  "| zsh",
  "| pwsh",
  "invoke-expression",
  "iex (",
  "set-executionpolicy bypass",
  "drop database",
  "drop table",
  "truncate table",
  "db.dropdatabase()",
  "docker system prune -a --volumes",
  "docker volume prune",
  "docker volume rm",
  "git push --force",
  "git push -f",
  "git clean -fdx",
  ":(){ :|:& };:",
  "shutdown ",
  "stop-computer"
]
```

</details>

### CDP 自動修復

啟用時擴充功能會偵測 9333 連接埠是否開啟（備用 9222）。如果未開啟，會彈出通知：
- **Auto-Fix Shortcut（Windows）** —— 給桌面、開始功能表、**工作列**上的 `.lnk` 捷徑全部打 patch

---

## 故障排除

### 機器人工作幾小時後停了

**原因：** 要麼 (a) Antigravity 靜默重啟了 Electron 行程（自動更新、記憶體壓力、或擴充功能宿主當機），新行程沒帶 `--remote-debugging-port=9333`；要麼 (b) webview 的執行上下文被一次導覽 / 熱重載清除了。

**修復：** 心跳自癒邏輯會自動偵測並重新注入死掉的 observer。如果仍然不工作，**完全關閉所有** Antigravity 視窗，然後用您打過 patch 的捷徑重新打開。

### 機器人已 ON 但什麼都不點

1. **切 OFF → ON** —— 點兩下狀態列圖示，重啟輪詢
2. **檢查偵錯連接埠** —— 瀏覽器存取 `http://127.0.0.1:9333/json/list`。如果拒絕連線，說明偵錯連接埠已死（見上一節）
3. **檢查輸出紀錄** —— `Ctrl+Shift+U` → 下拉選 `Anti-Remote-Pro`。找 `[CDP] ✓ Thread` 這樣的列。如果一條都沒有，說明 CDP 找不到 Agent 面板

### 安裝後狀態列圖示不顯示

1. `Ctrl+Shift+P` → `Reload Window`
2. 確認 VSIX 打包時**包含了相依套件**（`ws` 套件必須在包裡）

---

## 安全策略

下面這些指令**故意排除**以防止傷害：
- `notification.acceptPrimaryAction` —— 會自動點擊破壞性對話框
- `chatEditing.acceptAllFiles` —— 會導致側邊欄 Outline 抖動
- 所有 merge / git 衝突指令 —— 可能靜默地選錯一邊
- 所有自動補全 / 建議指令 —— 會污染您的輸入

---

## 安全 FAQ

**為什麼需要 `--remote-debugging-port`？**

Antigravity 的 Agent 面板執行在隔離的 Chromium 行程裡。VS Code 擴充功能 API 無法看到或操作裡面的 Run / Accept / Allow 按鈕——它們是 React UI 元素，沒有註冊任何指令。透過 localhost 連接埠（預設 9333）的 Chrome DevTools Protocol 是觸達它們的唯一途徑。

**安全嗎？**

- **僅 localhost** —— 連接埠繫結到 `127.0.0.1`，不是 `0.0.0.0`。任何外部機器都連不上。
- **自動接受核心零遙測** —— DOM 掃描、按鈕比對、指令過濾從不發網路請求。
- **唯一的對外流量**是 (a) 授權驗證、(b) Telegram Bot API（僅在您配對後）、(c) Swarm 模式簽章核心載荷取得。三者預設都是關閉的。
- **簽章 Pro 載荷。** Swarm 核心引擎透過 Ed25519 簽章，在 Node worker 內驗章後才在 RAM 裡編譯——中間人無法塞入流氓掃描器。
- **標準開發工作流** —— `--remote-debugging-port` 就是 VS Code 擴充功能開發者和 Electron 應用偵錯用的同一個 flag。
- **捷徑 patch 工具僅作用於目標路徑包含 "Antigravity" 的 `.lnk` 檔案** —— 不會誤傷其他捷徑。
- **不改動 Antigravity 任何檔案** —— 本擴充功能完全作為外部 VS Code 擴充功能執行。解除安裝後零痕跡。

**我的 Telegram 聊天會讀我的程式碼嗎？**

只會讀取您**明確要求**的內容。`/peek` 回傳當前 Agent 面板的可見文字；`/prompt` 把您的訊息傳進去。擴充功能從不主動把程式碼、diff、截圖或遙測推給 Telegram。

---

## 授權

MIT
