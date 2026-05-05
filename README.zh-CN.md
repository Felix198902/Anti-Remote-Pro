<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=zh-CN"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**专为 [Antigravity](https://antigravity.dev)（Google AI 编码助手）打造的隐私至上、防封号、支持 Telegram 远程操控的自动驾驶扩展。**
**一个 Google 账号，无限设备同步。**

### [🌐 访问官网 &nbsp;·&nbsp; 立即下载 →](https://antigravity.apiai.eu.cc/?lang=zh-CN)

<sub>
  📖 <b>其他语言版本：</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <b>简体中文</b> &nbsp;·&nbsp;
  <a href="./README.zh-TW.md">繁體中文</a> &nbsp;·&nbsp;
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

自动接受 Agent 步骤、终端命令、文件编辑和权限提示，让 Agent 全程免点击交付工作——所有数据都保留在你本地，并且你可以用手机远程操控每一台机器。

> 💡 **想要快速开始？** [官网](https://antigravity.apiai.eu.cc/?lang=zh-CN) 提供完整指南、产品截图、Pro 定价和最新版 `.vsix` 下载——全部 12 种语言。

---

## 🔥 为什么选择 Anti-Remote-Pro

### 🔒 1. 绝对隐私 —— 你的代码永远不离开本机

- **100% 本地运行。** 所有按钮识别、DOM 扫描、命令过滤都在你的 VS Code / Antigravity 进程内部完成。任何 prompt、截图、diff 都不会离开这台机器。
- **仅限 localhost 的调试端口。** CDP 严格绑定在 `127.0.0.1:9333`。局域网、咖啡馆 Wi-Fi、联合办公网络里的任何外部主机都无法连接——不是靠承诺，是靠 socket 绑定直接保证。
- **零遥测。** 自动接受核心不发送任何分析请求、崩溃报告、"匿名使用统计"。唯一的外部流量是：（a）你主动配对的 Telegram；（b）验证密钥的授权服务器。
- **目标白名单绑定。** CDP 层**只**会附加到匹配 Agent 面板的 `vscode-webview://` 目标。它拒绝附加到你的其他标签页、浏览器子 Agent 或任何非 Antigravity 的 Chromium 目标。
- **核心载荷签名校验。** Pro 核心引擎以 Ed25519 签名包的形式获取，在 Node worker 内完成验签后**内存中**编译——从不落盘、不可被中间人篡改。
- **不修改 Antigravity 任何文件。** 我们不打补丁、不重打包、不 hook Antigravity 的二进制文件。纯外部 CDP——卸载即零痕迹。

### 📱 2. Telegram 远程操控 —— 随时随地驾驭 Antigravity

将你的 IDE 与 Telegram 机器人一次配对，你的手机就变成了 Agent 的完整遥控器：

- **`/prompt <文本>`** —— 从地球上任何角落向当前对话发送新 prompt。自动拼接 Telegram 4096 字符分片消息。
- **`/peek [N]`** —— 直接在 Telegram 里阅读 Agent 最新回复，不必唤醒笔记本。
- **带说明发送图片** —— 将截图附加到 prompt，随时随地做可视化调试。
- **`/pause` & `/resume`** —— 从手机切换全局开关。跨窗口文件锁确保每个 Antigravity 窗口即时响应。
- **`/stop`** —— 停止当前正在生成的响应。
- **HMAC 签名命令。** 每条 Telegram 命令都通过设备级 HMAC 密钥校验。即使 Telegram 聊天泄露，也**无法**控制你的 IDE。
- **单主控选举。** 当你同时开了 5 个 Antigravity 窗口时，只有一个会赢得主控锁处理命令——不会重复发送，不会有竞态。

### 🛡️ 3. 业界首创的防封号策略

大多数自动点击器之所以触发账号标记，是因为它们用固定节奏打接口，并在用户还在打字时就抢着点击。Anti-Remote-Pro 的工程思路恰恰相反：

- **拟人化节奏。** 主动轮询间隔 500 ms，加 **±20% 随机抖动** + 连续错误时指数退避（上限 30 s）。没有机械般完美的节拍可以被指纹识别。
- **空闲智能休眠。** 没有活跃 CDP 会话时，引擎降到 5 秒心跳——离开时几乎零 IPC 开销。
- **20 秒用户活跃宽限窗口。** 如果用户正在聊天框打字、滚动 webview 或移动光标，**所有自动点击都会延后**。机器人真的会等你停下来再点，从不在你阅读时抢点。
- **不做二进制修补。** Antigravity 的文件、settings.json、用户数据目录对本扩展都是只读的。官方自动更新和完整性校验可以完整通过，因为我们什么都没改。
- **CDP 仅 loopback。** 没有 TCP 监听，没有远程转发。`--remote-debugging-port=9333` 这个 flag 就是标准 Electron 调试参数——微软、Google、JetBrains 内部用的是同一个。
- **硬性命令防火墙。** 内置黑名单 + 可选严格白名单 + 50+ 精选的**安全预设**（rm -rf、强制 push、drop database、fork 炸弹、磁盘擦除、注册表删除等）。即使 Agent 坚持要执行，机器人也会**拒绝**跑这些破坏性命令。
- **展开类按钮一次一会话。** 消除"无限重开"循环，避免触发反滥用启发。
- **即时让位给官方浏览器子 Agent。** 当 AG 自身的浏览器工具激活 9222 端口时，我们的 worker 立即脱离并让出——不会有端口冲突，不会有双重附加的指纹。

> 综合效果：从 Agent 后台的视角看，你就是一个手速略快但彬彬有礼的普通人类用户。

### 🌍 4. 多语言支持 —— 12 种语言，覆盖数十亿用户

Anti-Remote-Pro 提供完整的 UI 本地化（命令、设置、仪表盘、通知、Telegram 回复）。可以在仪表盘的下拉菜单手动选择，也可以让插件自动检测你的 IDE 语言。

| # | 语言 | 本地名称 | 主要地区 |
|---|---|---|---|
| 1 | 英语 | English | 🇺🇸 美国 · 🇬🇧 英国 · 🇨🇦 加拿大 · 🇦🇺 澳大利亚 · 🇮🇪 爱尔兰 · 🇳🇿 新西兰 · 🇿🇦 南非 · 🇸🇬 新加坡 · 🇮🇳 印度（IT） |
| 2 | 简体中文 | 简体中文 | 🇨🇳 中国大陆 · 🇸🇬 新加坡 · 🇲🇾 马来西亚 |
| 3 | 繁体中文 | 繁體中文 | 🇹🇼 台湾 · 🇭🇰 香港 · 🇲🇴 澳门 |
| 4 | 西班牙语 | Español | 🇪🇸 西班牙 · 🇲🇽 墨西哥 · 🇦🇷 阿根廷 · 🇨🇴 哥伦比亚 · 🇨🇱 智利 · 🇵🇪 秘鲁 · 🇻🇪 委内瑞拉 · +14 个 |
| 5 | 法语 | Français | 🇫🇷 法国 · 🇨🇦 加拿大（魁北克） · 🇧🇪 比利时 · 🇨🇭 瑞士 · 🇱🇺 卢森堡 · 🇲🇨 摩纳哥 · 大部分西非与中非国家 |
| 6 | 印地语 | हिन्दी | 🇮🇳 印度 · 🇫🇯 斐济 |
| 7 | 葡萄牙语（巴西） | Português | 🇧🇷 巴西 · 🇵🇹 葡萄牙 · 🇦🇴 安哥拉 · 🇲🇿 莫桑比克 |
| 8 | 俄语 | Русский | 🇷🇺 俄罗斯 · 🇧🇾 白俄罗斯 · 🇰🇿 哈萨克斯坦 · 🇰🇬 吉尔吉斯斯坦 · 🇺🇿 乌兹别克斯坦 · 🇺🇦 乌克兰 |
| 9 | 阿拉伯语 | العربية（从右向左） | 🇸🇦 沙特 · 🇦🇪 阿联酋 · 🇪🇬 埃及 · 🇶🇦 卡塔尔 · 🇰🇼 科威特 · 🇧🇭 巴林 · 🇴🇲 阿曼 · 🇯🇴 约旦 · 🇲🇦 摩洛哥 · 🇩🇿 阿尔及利亚 · 🇹🇳 突尼斯 · 🇮🇶 伊拉克 · +10 个 |
| 10 | 日语 | 日本語 | 🇯🇵 日本 |
| 11 | 德语 | Deutsch | 🇩🇪 德国 · 🇦🇹 奥地利 · 🇨🇭 瑞士 · 🇱🇮 列支敦士登 · 🇱🇺 卢森堡 |
| 12 | 韩语 | 한국어 | 🇰🇷 韩国 |

- **自动检测** 跟随 `vscode.env.language`——插件首次启动时即刻使用你的 locale。
- **手动切换** 通过仪表盘语言下拉（切换后持久保存，重载仍生效）。
- **RTL 感知** —— 阿拉伯语 UI 会自动翻转布局方向（`dir="rtl"`）。
- **自定义关键词覆盖** —— `autoAcceptV2.customButtonTexts` 允许你为尚未翻译的 UI 字符串追加本地化按钮文案（例如 `["toujours autoriser", "siempre permitir"]`）。

### 🔗 5. Google 登录多设备同步 —— 一个账号，所有机器

**一次 Google 登录**，Anti-Remote-Pro 跟随你到任何设备——台式、笔记本、家用 PC、公司工作站，Windows、macOS、Linux 都支持。

- **一键 Google OAuth。** `Anti-Remote-Pro: Login with Google` 会打开浏览器完成标准 Google OAuth 流程，然后通过安全的 `vscode://Pro.antigravity-autoaccept/auth` URI 回调返回 IDE。无需复制粘贴许可证密钥，无需邮件流程。
- **Pro 许可跨设备自动同步。** 你的订阅绑定的是 Google 账号，不是单台机器。在第 2 台、第 3 台、第 10 台设备上安装——登录即刻解锁 Pro。许可证服务器每次刷新都会针对你的账号校验每台 `machineId`。
- **无限设备并行运行。** 工作笔记本、家用台式、远程开发机、为每个客户准备的虚拟机——都可以在同一账号下并行跑 Anti-Remote-Pro。
- **并行舰队。** 每台设备独立运作，拥有自己的 CDP / Swarm / 命令防火墙。你的笔记本可以处理对话 A，台式机处理对话 B，互不抢焦点。
- **每设备独立 Telegram 配对。** 每台机器单独与 Telegram 机器人配对，得到自己的 HMAC 密钥。配对流程中可以为它们命名（如 "MacBook"、"WorkPC"），然后在同一个 Telegram 聊天里分别寻址。
- **同机跨窗口协同。** 当同一台机器上开了多个 Antigravity 窗口时，一个文件锁协议在 1 秒内同步所有窗口的暂停/恢复状态——不重复点击、不互相争抢。
- **即时吊销。** `Anti-Remote-Pro: Logout` 清除本地令牌并通知服务器作废该设备。丢了笔记本？在另一台机器登出 + `Refresh Pro Status`，老机器立刻失效。
- **Refresh Pro Status。** 改了套餐或续费了订阅？一条命令重新拉取最新权益——无需重装、无需重启。

> 实际用法：在 3 台电脑上各登录一次，每台配对同一个 Telegram 机器人，你的手机就是整个编码舰队的中央遥控器。

---

## ⚡ 核心能力一览

- **自动点击** Run / Accept / Always Allow / Allow this conversation / Continue / Retry 这些 Agent 面板按钮——基于优先级，`Run` 永远胜过 `Accept`。
- **自动接受文件编辑**，一键切换——随时关闭以手动 review diff。
- **命令防火墙** —— 阻止模式或严格白名单模式，两者都用词边界匹配。
- **安全预设** —— 一键导入 50+ 破坏性命令模式（文件系统擦除、磁盘格式化、强制 push、DB drop、fork 炸弹）。
- **Swarm 模式（Pro）** —— 自动在 Agent Manager 的待处理对话间轮换，后台无人值守运行。
- **Telegram Remote（Pro）** —— 完整 IDE 远程：`/prompt`、`/peek`、图片 prompt、`/pause`、`/resume`、`/stop`，带 HMAC 鉴权。
- **Google 登录 + 多设备同步（Pro）** —— 一个 Google 账号、无限设备；`vscode://` URI handler OAuth 回调；设备级许可证校验。
- **跨窗口暂停** —— 在一个 Antigravity 窗口按下暂停，通过文件锁在 <1 秒内广播到其他所有窗口。
- **活动日志 + 仪表盘** —— 实时查看每次点击、每个 CDP 会话、每条 Telegram 命令。
- **诊断转储** —— 一键把结构化调试信息复制到剪贴板，方便一条消息走完支持流程。
- **快捷方式自动修复** —— Windows `.lnk` 补丁器（桌面 / 开始菜单 / 任务栏），补上 `--remote-debugging-port` flag。
- **心跳自愈** —— 被 webview 导航 / 热重载清除的 MutationObserver 会在 10 秒内检测并自动重新注入。

---

## 它做什么

当 Antigravity 的 Agent 提议文件编辑、终端命令或请求工具权限时，本扩展会自动接受这些操作，让你不用一个个按钮去点。

**两种策略，零干扰：**

| 策略 | 处理内容 | 实现方式 |
|---|---|---|
| **VS Code 命令** (500 ms + 抖动) | Agent 步骤、终端命令 | 调用 Antigravity 原生的 accept 命令 |
| **CDP + MutationObserver** (事件驱动) | Run、Accept、Always Allow、Continue、Retry | 每个目标注入一次脚本，DOM 变化即时响应 |

---

## 安装设置

### 1. 启用调试模式（必需）

本扩展需要 Chrome DevTools Protocol 来点击权限按钮。启动 Antigravity 时加上：

```
--remote-debugging-port=9333
```

> **为什么用 9333？** Antigravity 内置的 Browser Control（工具栏里的 Chrome 按钮）默认用 9222。用相同端口会在 macOS/Linux 上触发 `EADDRINUSE` 冲突。用 9333 彻底回避这个问题。

<details>
<summary><b>🪟 Windows</b></summary>

**自动方式：** 首次启动时，扩展会检测端口是否打开，如果没打开会提示 **"Auto-Fix Shortcut"**——点一下就会自动给你的 `.lnk` 快捷方式打补丁。

**手动方式：** 右键 Antigravity 快捷方式 → 属性 → 在 Target 后追加：
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**方案 1 —— Automator 应用（推荐）：**
1. 打开 **Automator** → 新建文稿 → **应用程序**
2. 在库里搜索 **"运行 Shell 脚本"**
3. 粘贴：`open -a "Antigravity" --args --remote-debugging-port=9333`
4. 另存为 "AntiGravity Launcher" 放到桌面或应用程序文件夹

**方案 2 —— 终端别名**（添加到 `~/.zshrc`）：
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **注意：** App 名字必须完全一致。用 `ls /Applications/ | grep -i anti` 检查。

**方案 3 —— 直接 Electron 二进制**（如果 `open -a` 不能正确传参）：
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**方案 1 —— 编辑 `.desktop` 文件：**
```bash
# 找到它：
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# 编辑 Exec 行：
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**方案 2 —— Shell 别名**（添加到 `~/.bashrc` 或 `~/.zshrc`）：
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**方案 3 —— Wrapper 脚本：**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. 安装扩展

**通过 VSIX（推荐）：**
1. 获取最新的 `.vsix` 包
2. 在 Antigravity 里：`Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. 选中下载的文件
4. Reload Window

**手动安装：**
1. 把 `src/` 目录、`package.json`、`package-lock.json` 拷到：
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. 在该目录里跑 `npm install`（安装 `ws` 依赖）
3. Reload Window

---

## 使用方法

### 基础命令

- **切换开关：** 点击状态栏的 `⚡ Auto: ON` / `✕ Auto: OFF`
- **或者：** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **仪表盘：** 点击状态栏的仪表盘图标，查看 CDP 状态、活跃会话、活动日志和语言选择器
- **日志：** Output 面板 → `Anti-Remote-Pro`

### Pro 命令

所有 Pro 功能都可以通过命令面板（`Ctrl+Shift+P`）触发：

| 命令 | 作用 |
|---|---|
| `Anti-Remote-Pro: Login with Google` | 登录以跨设备同步 Pro 许可证 |
| `Anti-Remote-Pro: Logout` | 清除本地许可证 + 已登录账号 |
| `Anti-Remote-Pro: Refresh Pro Status` | 强制向服务器重新校验许可证 |
| `Anti-Remote-Pro: Connect Telegram Bot` | 启动配对流程——打开 Telegram 里的机器人，点 **Start** 即可绑定本机 |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | 吊销本机的 HMAC 密钥 |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | 强制重新下载签名的核心载荷 |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | 全局开关（同时绑定 `Ctrl+Shift+S`） |
| `Anti-Remote-Pro: Fix Missing Conversations` | 当侧边栏对话索引不同步时，重新播种 Swarm 索引 |

> **提示：** `Ctrl+Shift+S` 是队友突然加入你会话时，暂停/恢复 Swarm + 自动接受的最快方式。

---

## 多 Agent 工作流

### ⚠️ Agent Manager 限制（未启用 Swarm 模式时）

Antigravity 的 Agent Manager 使用**单个共享 webview**——只有当前对话的 DOM 会被渲染，背景对话完全 unmount。没有 Swarm 模式时，VS Code Commands API 和 CDP 都只能触及当前可见的对话。

### ✅ 解决方案：Swarm 模式（Pro）

Swarm 模式通过在所有待处理对话间轮换焦点来解决这个问题，让数十个后台 Agent 无人值守运行：

- 扫描侧边栏每一个对话，挑出有待处理工作的那一个。
- 遵守你的空闲秒数设置，绝不在你打字时抢焦点。
- 跨窗口感知：任一窗口暂停会通过文件锁广播暂停所有窗口。
- 默认安全：签名的核心载荷、命令防火墙仍然生效。

### 备选方案：复制工作区（免费）

如果你没有 Pro 许可证，仍然可以并行跑 2–3 个 Agent：

1. 点 **File → Duplicate Workspace**
2. 这会打开连接到同一项目的第二个 Antigravity 窗口
3. 在窗口 1 开一个聊天，在窗口 2 再开一个
4. 每个窗口有自己独立的 webview——扩展会在**两个窗口同时**自动点击按钮

---

## 设置项

| 设置 | 默认值 | 作用域 | 说明 |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | 基础轮询间隔（毫秒，自动附加 ±20% 抖动） |
| `autoAcceptV2.customButtonTexts` | `[]` | application | 额外的按钮文案，用于 i18n 或自定义 prompt（例如 `["toujours autoriser"]`） |
| `autoAcceptV2.cdpPort` | `9333` | machine | CDP 端口（默认避开 AG Browser Control 的 9222） |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | 自动接受文件编辑（关闭后需手动 review diff） |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Agent 遇到错误或调用限制时自动点 Retry / Continue |
| `autoAcceptV2.blockedCommands` | `[]` | application | 绝不自动执行的命令（例如 `rm`、`git push`、`npm publish`） |
| `autoAcceptV2.allowedCommands` | `[]` | application | 如设置，**仅**这些命令会被自动执行（白名单模式） |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Pro 许可证密钥——解锁 Swarm 模式 + Telegram Remote |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Swarm 跳转到待处理对话前，要求用户的无操作秒数（3–60） |

> **提示：** 设置支持热重载，改完立即生效，无需重启。

---

## 工作原理

### 持久化 CDP + MutationObserver

扩展保持一个**浏览器级别的持久化 WebSocket** 连接到 Chromium 的 DevTools Protocol。它不是每 1.5 秒轮询一次，而是给每个目标注入一次 **MutationObserver** 载荷。当 React 挂载新的按钮元素时，observer 即时反应，并带 100ms 前沿节流以避免流式输出时的 CPU 峰值。扩展使用**严格白名单目标过滤器**——只附加到 `vscode-webview://` 目标，检测到 AG 浏览器子 Agent 时自动让出 CDP 端口，防止 ArrayBuffer 冲突。

### 单趟 DOM 扫描

按钮扫描器每个周期只走一次 DOM 树，对每个节点同时检查所有关键词。时间复杂度是 O(D) 而不是 O(N×D)，避免了关键词多时 UI 卡顿。基于优先级的匹配确保 `Run` 总是优先于 `Accept`，`Accept` 总是优先于 `Allow`，与 DOM 顺序无关。

### Webview 守卫

Antigravity 的 Agent 面板运行在隔离的 Chromium 进程（OOPIF）里。注入的脚本在 `scanAndClick()` 内部使用延迟的 `isAgentPanel()` 检查——每次扫描时动态验证 `.react-app-container` 是否存在，而不是注入时就校验。这避免了 `targetCreated` 时 DOM 尚未 hydrate 的竞态。

### 心跳自愈

CDP 连接每个心跳周期（10 秒）会校验现有会话。如果某个会话的 MutationObserver 已死（执行上下文被 webview 导航或 React 热重载清除），它会自动重新注入 observer——无需重新连接。连续 3 次不可达的会话会被干净地分离并清理。

### 展开按钮循环预防

展开类按钮（例如 browser preview 的 "Expand"）采用**每个会话点一次**规则：一旦被点击，在该 CDP 会话中永久被抑制（通过一个 `expandedOnce` Set）。这防止了关闭展开面板又触发重新点击的无限重开循环。新的 Agent 对话开始时状态自然重置。

### 按钮识别

在 Agent 面板内，一个 `TreeWalker` 通过 `startsWith` + **词边界检查**来按文本内容搜索按钮（防止误匹配，例如 `accept-test.js` 不会匹配 `accept`）：

| 优先级 | 文本 | 匹配对象 |
|---|---|---|
| 1 | `run` | "Run Alt+d" 按钮（不是 "Always run ^" 下拉） |
| 2 | `accept` | Accept 按钮 |
| 3 | `always allow` | 权限提示 |
| 4 | `allow this conversation` | 对话级权限 |
| 5 | `allow` | 权限提示 |
| 6 | `retry` | Retry 提示 |
| 7 | `continue` | Agent 调用次数限制后的继续 |

### 命令过滤

黑名单和白名单都用**词边界匹配**对 Run 按钮上方的代码块做匹配。例如，屏蔽 `rm` 会阻止 `rm -rf /tmp`，但**不会**阻止 `yarn format` 或 `npm run build`。

---

## 推荐的阻止命令

仪表盘里有一个 **Load Safety Presets** 按钮，会批量导入 50+ 破坏性命令模式，涵盖文件系统擦除、磁盘格式化、数据库删除、强制 push、fork 炸弹等。

**一键操作：** 打开仪表盘 → 点 **Load Recommended Safety Presets**。

**批量粘贴：** 黑/白名单输入框支持**逗号分隔**值——粘一串按回车即可。

<details>
<summary><b>📋 手动：复制到 settings.json</b></summary>

把下面这段加到你的 `settings.json`（`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`）：

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

### CDP 自动修复

激活时扩展会检测 9333 端口是否开启（备用 9222）。如果未开启，会弹出通知：
- **Auto-Fix Shortcut（Windows）** —— 给桌面、开始菜单、**任务栏**上的 `.lnk` 快捷方式全部打补丁

---

## 故障排查

### 机器人工作几小时后停了

**原因：** 要么 (a) Antigravity 静默重启了 Electron 进程（自动更新、内存压力、或扩展宿主崩溃），新进程没带 `--remote-debugging-port=9333`；要么 (b) webview 的执行上下文被一次导航 / 热重载清除了。

**修复：** 心跳自愈逻辑会自动检测并重新注入死掉的 observer。如果仍然不工作，**完全关闭所有** Antigravity 窗口，然后用你打过补丁的快捷方式重新打开。

### 机器人已 ON 但什么都不点

1. **切 OFF → ON** —— 点两下状态栏图标，重启轮询
2. **检查调试端口** —— 浏览器访问 `http://127.0.0.1:9333/json/list`。如果拒绝连接，说明调试端口已死（见上一节）
3. **检查输出日志** —— `Ctrl+Shift+U` → 下拉选 `Anti-Remote-Pro`。找 `[CDP] ✓ Thread` 这样的行。如果一条都没有，说明 CDP 找不到 Agent 面板

### 安装后状态栏图标不显示

1. `Ctrl+Shift+P` → `Reload Window`
2. 确认 VSIX 打包时**包含了依赖**（`ws` 包必须在包里）

---

## 安全策略

下面这些命令**故意排除**以防止伤害：
- `notification.acceptPrimaryAction` —— 会自动点击破坏性对话框
- `chatEditing.acceptAllFiles` —— 会导致侧边栏 Outline 抖动
- 所有 merge / git 冲突命令 —— 可能静默地选错一边
- 所有自动补全 / 建议命令 —— 会污染你的输入

---

## 安全 FAQ

**为什么需要 `--remote-debugging-port`？**

Antigravity 的 Agent 面板运行在隔离的 Chromium 进程里。VS Code 扩展 API 无法看到或操作里面的 Run / Accept / Allow 按钮——它们是 React UI 元素，没有注册任何命令。通过 localhost 端口（默认 9333）的 Chrome DevTools Protocol 是触达它们的唯一途径。

**安全吗？**

- **仅 localhost** —— 端口绑定到 `127.0.0.1`，不是 `0.0.0.0`。任何外部机器都连不上。
- **自动接受核心零遥测** —— DOM 扫描、按钮匹配、命令过滤从不发网络请求。
- **唯一的对外流量**是 (a) 许可证校验、(b) Telegram Bot API（仅在你配对后）、(c) Swarm 模式签名核心载荷获取。三者默认都是关闭的。
- **签名 Pro 载荷。** Swarm 核心引擎通过 Ed25519 签名，在 Node worker 内验签后才在 RAM 里编译——中间人无法塞入流氓扫描器。
- **标准开发工作流** —— `--remote-debugging-port` 就是 VS Code 扩展开发者和 Electron 应用调试用的同一个 flag。
- **快捷方式补丁器仅作用于目标路径包含 "Antigravity" 的 `.lnk` 文件** —— 不会误伤其他快捷方式。
- **不改动 Antigravity 任何文件** —— 本扩展完全作为外部 VS Code 扩展运行。卸载后零痕迹。

**我的 Telegram 聊天会读我的代码吗？**

只会读取你**明确要求**的内容。`/peek` 返回当前 Agent 面板的可见文本；`/prompt` 把你的消息发进去。扩展从不主动把代码、diff、截图或遥测推给 Telegram。

---

## 许可证

MIT
