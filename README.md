<div align="center">

<a href="https://antigravity.apiai.eu.cc"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**The privacy-first, ban-proof, Telegram-controlled auto-pilot for [Antigravity](https://antigravity.dev) — Google's AI coding assistant.**
**One Google account, unlimited devices.**

### [🌐 Official Website &nbsp;·&nbsp; Download Now →](https://antigravity.apiai.eu.cc)

<sub>
  <a href="https://antigravity.apiai.eu.cc/?lang=en">English</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=zh-CN">简体中文</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=zh-TW">繁體中文</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=ja">日本語</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=ko">한국어</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=es">Español</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=fr">Français</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=de">Deutsch</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=pt">Português</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=ru">Русский</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=ar">العربية</a> &nbsp;·&nbsp;
  <a href="https://antigravity.apiai.eu.cc/?lang=hi">हिन्दी</a>
</sub>

</div>

Auto-accepts agent steps, terminal commands, file edits and permission prompts so the agent ships your work hands-free — while keeping every byte on your machine, and letting you steer every one of your machines from your phone.

> 💡 **Getting started?** The [official site](https://antigravity.apiai.eu.cc) has a full guide, live screenshots, Pro pricing, and the latest `.vsix` download — all in 12 languages.

---

## 🔥 Why Anti-Remote-Pro

### 🔒 1. Absolute Privacy — your code never leaves your laptop

- **100% local pipeline.** All button detection, DOM scanning and command filtering run inside your VS Code / Antigravity process. No prompts, no screenshots, no diffs ever leave the machine.
- **Localhost-only debug port.** CDP binds strictly to `127.0.0.1:9333`. No external host on the LAN, on a coffee-shop Wi-Fi, or on a co-working network can reach it — verified by socket binding, not just by promise.
- **Zero telemetry.** The auto-accept core makes no analytics calls, no crash reports, no “anonymous usage stats”. The only outbound traffic is to Telegram (only if you pair it) and to the license server (only to verify your key).
- **Whitelist-only target attach.** The CDP layer attaches **only** to `vscode-webview://` targets matching the agent panel. It refuses to attach to your other tabs, browser sub-agents, or any non-Antigravity Chromium target.
- **Signed core payload.** The Pro core engine is fetched as an Ed25519-signed payload, verified inside a Node worker, and compiled in RAM — never written to disk, never tamperable by a man-in-the-middle.
- **No file modification of Antigravity itself.** We do not patch, repack or hook Antigravity binaries. Pure external CDP — uninstall and zero traces remain.

### 📱 2. Telegram Remote Control — drive Antigravity from anywhere

Pair your IDE to a Telegram bot once, and your phone becomes a full remote for the agent:

- **`/prompt <text>`** — send a new prompt to the active conversation from anywhere on the planet. Auto-stitches Telegram's 4096-char message splits.
- **`/peek [N]`** — read the agent's latest reply right inside Telegram, no need to wake your laptop.
- **Send a photo with caption** — attaches the screenshot to the prompt for visual debugging on the go.
- **`/pause` & `/resume`** — flip the global kill-switch from your phone. Cross-window file lock guarantees every Antigravity window obeys instantly.
- **`/stop`** — halt the currently generating response.
- **HMAC-signed commands.** Every Telegram command is verified with a per-device HMAC key. A leaked Telegram chat is *not* enough to control your IDE.
- **Single-master election.** When you have 5 Antigravity windows open, only one wins the master lock and processes commands — no duplicate sends, no race conditions.

### 🛡️ 3. Industry-First Anti-Ban Strategy

Most autoclickers get accounts flagged because they hammer endpoints at a fixed cadence and click while the human is still typing. Anti-Remote-Pro is engineered the opposite way:

- **Human-rhythm timing.** Active polling at 500 ms with **±20 % random jitter** + exponential backoff (capped at 30 s) on consecutive errors. No machine-perfect intervals to fingerprint.
- **Idle smart-sleep.** With no active CDP session the engine drops to a 5 s heartbeat — practically zero IPC pressure when you're away.
- **20-second user-active grace window.** If the user is typing in chat, scrolling the webview or moving the editor cursor, **all auto-clicks are deferred**. The bot literally waits for you to stop, so it never co-clicks while you read.
- **No binary patching.** Antigravity files, settings.json, and the user data dir are read-only to this extension. Official auto-updates and integrity checks pass cleanly because nothing is modified.
- **Loopback-only CDP.** No TCP listener, no remote forwarding. The flag `--remote-debugging-port=9333` is a vanilla Electron debug flag — the same one Microsoft, Google and JetBrains use internally.
- **Hard command firewall.** Built-in blocklist + optional strict allowlist + 50+ curated *Safety Presets* (rm -rf, force-push, drop database, fork bombs, disk wipers, registry deletes…). The bot will *refuse* to run a destructive command even if the agent insists.
- **Click-once-per-session for expand buttons.** Eliminates the “infinite re-open” loop that risks tripping abuse heuristics.
- **Instant yield to the official Browser sub-agent.** When AG's own browser tooling activates on port 9222, our worker detaches and gets out of the way — no port collision, no double-attach signature.

> The combined effect: from the agent backend's perspective you look like a slightly-faster-than-average, impeccably polite human user.

### 🌍 4. Multi-Language — 12 languages, billions of users covered

Anti-Remote-Pro ships full UI translations (commands, settings, dashboard, notifications, Telegram replies). Pick from a dropdown in the dashboard, or let it auto-detect your IDE language.

| # | Language | Native name | Primary regions |
|---|---|---|---|
| 1 | English | English | 🇺🇸 USA · 🇬🇧 UK · 🇨🇦 Canada · 🇦🇺 Australia · 🇮🇪 Ireland · 🇳🇿 New Zealand · 🇿🇦 South Africa · 🇸🇬 Singapore · 🇮🇳 India (IT) |
| 2 | Simplified Chinese | 简体中文 | 🇨🇳 Mainland China · 🇸🇬 Singapore · 🇲🇾 Malaysia |
| 3 | Traditional Chinese | 繁體中文 | 🇹🇼 Taiwan · 🇭🇰 Hong Kong · 🇲🇴 Macau |
| 4 | Spanish | Español | 🇪🇸 Spain · 🇲🇽 Mexico · 🇦🇷 Argentina · 🇨🇴 Colombia · 🇨🇱 Chile · 🇵🇪 Peru · 🇻🇪 Venezuela · +14 more |
| 5 | French | Français | 🇫🇷 France · 🇨🇦 Canada (Québec) · 🇧🇪 Belgium · 🇨🇭 Switzerland · 🇱🇺 Luxembourg · 🇲🇨 Monaco · much of West & Central Africa |
| 6 | Hindi | हिन्दी | 🇮🇳 India · 🇫🇯 Fiji |
| 7 | Portuguese (BR) | Português | 🇧🇷 Brazil · 🇵🇹 Portugal · 🇦🇴 Angola · 🇲🇿 Mozambique |
| 8 | Russian | Русский | 🇷🇺 Russia · 🇧🇾 Belarus · 🇰🇿 Kazakhstan · 🇰🇬 Kyrgyzstan · 🇺🇿 Uzbekistan · 🇺🇦 Ukraine |
| 9 | Arabic | العربية (RTL) | 🇸🇦 Saudi Arabia · 🇦🇪 UAE · 🇪🇬 Egypt · 🇶🇦 Qatar · 🇰🇼 Kuwait · 🇧🇭 Bahrain · 🇴🇲 Oman · 🇯🇴 Jordan · 🇲🇦 Morocco · 🇩🇿 Algeria · 🇹🇳 Tunisia · 🇮🇶 Iraq · +10 more |
| 10 | Japanese | 日本語 | 🇯🇵 Japan |
| 11 | German | Deutsch | 🇩🇪 Germany · 🇦🇹 Austria · 🇨🇭 Switzerland · 🇱🇮 Liechtenstein · 🇱🇺 Luxembourg |
| 12 | Korean | 한국어 | 🇰🇷 South Korea |

- **Auto-detect** follows `vscode.env.language` — the extension serves your locale immediately on first launch.
- **Manual override** via the Dashboard language dropdown (persists across reloads).
- **RTL aware** — Arabic UI flips layout direction automatically (`dir="rtl"`).
- **Custom keyword overrides** — `autoAcceptV2.customButtonTexts` lets you add localized button labels for any UI string we haven't translated yet (e.g. `["toujours autoriser", "siempre permitir"]`).

### 🔗 5. Multi-Device Sync with Google Sign-In — one account, all your machines

Sign in **once with Google** and Anti-Remote-Pro follows you everywhere — desktop, laptop, home PC, work workstation, Windows, macOS, Linux.

- **One click Google OAuth.** `Anti-Remote-Pro: Login with Google` opens your browser, completes standard Google OAuth, and redirects back to the IDE via a secure `vscode://Pro.antigravity-autoaccept/auth` URI handler. No license key copy-paste, no email dance.
- **Pro license auto-syncs across devices.** Your subscription is bound to your Google account, not to a single machine. Install on device #2, #3, #10 — sign in and Pro unlocks instantly. The license server verifies each `machineId` against your account on every refresh.
- **Run on an unlimited number of devices simultaneously.** Work laptop, home desktop, a remote dev box, a VM for each client — all of them can run Anti-Remote-Pro in parallel under the same account.
- **Parallel fleets.** Each device operates independently with its own CDP / Swarm / command firewall, so you can have one laptop crunching Conversation A while your desktop runs Conversation B — neither steals focus from the other.
- **Per-device Telegram pairing.** Each machine pairs with the Telegram bot separately and gets its own HMAC key. You can name them in the pairing flow (e.g. "MacBook", "WorkPC") and address them individually from the same Telegram chat.
- **Cross-window coordination on the same machine.** When you have multiple Antigravity windows open on one device, a file-lock protocol keeps their pause/resume state in sync in under a second — no duplicate clicks, no fighting.
- **Instant revocation.** `Anti-Remote-Pro: Logout` wipes the local token and tells the server to invalidate that device. Lost a laptop? Log out from another machine + `Refresh Pro Status` and the old machine goes dark.
- **Refresh Pro Status.** Changed plans or renewed your subscription? One command re-pulls the latest entitlements — no reinstall, no restart.

> In practice: log in once on your 3 computers, pair each to the same Telegram bot, and your phone becomes a central remote for your entire coding fleet.

---

## ⚡ Core Capabilities at a Glance

- **Auto-click** Run / Accept / Always Allow / Allow this conversation / Continue / Retry across the agent panel — priority-aware so `Run` always wins over `Accept`.
- **Auto-accept file edits** with one toggle — turn it off any time to review diffs manually.
- **Command firewall** — block patterns or strict allowlist mode, both with word-boundary matching.
- **Safety presets** — one-click import of 50+ destructive command patterns (filesystem wipers, disk formatters, force-push, DB drops, fork bombs).
- **Swarm Mode (Pro)** — automatically rotates across pending Agent Manager conversations and runs them hands-free in the background.
- **Telegram Remote (Pro)** — full IDE remote: `/prompt`, `/peek`, photo prompts, `/pause`, `/resume`, `/stop`, with HMAC auth.
- **Google Sign-In + multi-device sync (Pro)** — one Google account, unlimited devices; `vscode://` URI handler OAuth callback; per-device license verification.
- **Cross-window pause** — pausing in one Antigravity window broadcasts via file-lock to every other window in <1 s.
- **Activity log + Dashboard** — see every clicked button, every CDP session, every Telegram command live.
- **Diagnostic dump** — copy a structured debug payload to clipboard for one-message support.
- **Auto-Fix shortcut** — Windows `.lnk` patcher (Desktop / Start Menu / Taskbar) for the `--remote-debugging-port` flag.
- **Heartbeat self-healing** — dead MutationObservers (cleared by webview navigation / hot-reload) are detected and re-injected automatically every 10 s.

---

## What it does

When the Antigravity agent proposes file edits, terminal commands, or asks for tool permissions, this extension auto-accepts them so you don't have to click every button manually.

**Two strategies, zero interference:**

| Strategy | What it handles | How |
|---|---|---|
| **VS Code Commands** (500 ms + jitter) | Agent steps, terminal commands | Calls Antigravity's native accept commands |
| **CDP + MutationObserver** (event-driven) | Run, Accept, Always Allow, Continue, Retry | One-shot script injected once, reacts instantly to DOM changes |

---

## Setup

### 1. Enable Debug Mode (Required)

The extension needs Chrome DevTools Protocol to click permission buttons. Launch Antigravity with:

```
--remote-debugging-port=9333
```

> **Why port 9333?** Antigravity's built-in Browser Control (Chrome button in the toolbar) uses port 9222 by default. Using the same port causes an `EADDRINUSE` conflict on macOS/Linux. Port 9333 avoids this entirely.

<details>
<summary><b>🪟 Windows</b></summary>

**Automatic:** On first launch, the extension detects if the port is closed and shows **"Auto-Fix Shortcut"** — click it to automatically patch your `.lnk` shortcut.

**Manual:** Right-click your Antigravity shortcut → Properties → append to Target:
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**Option 1 — Automator App (recommended):**
1. Open **Automator** → New Document → **Application**
2. Search for **"Run Shell Script"** in the library
3. Paste: `open -a "Antigravity" --args --remote-debugging-port=9333`
4. Save as "AntiGravity Launcher" to Desktop or Applications

**Option 2 — Terminal alias** (add to `~/.zshrc`):
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **Note:** The app name must match exactly. Check with `ls /Applications/ | grep -i anti`

**Option 3 — Direct Electron binary** (if `open -a` doesn't pass args correctly):
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**Option 1 — Edit the `.desktop` file:**
```bash
# Find it:
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# Edit the Exec line:
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**Option 2 — Shell alias** (add to `~/.bashrc` or `~/.zshrc`):
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**Option 3 — Wrapper script:**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. Install the Extension

**From VSIX (recommended):**
1. Obtain the latest `.vsix` package
2. In Antigravity: `Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. Select the downloaded file
4. Reload Window

**Manual:**
1. Copy the `src/` directory, `package.json`, and `package-lock.json` to:
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. Run `npm install` in that directory (installs `ws` dependency)
3. Reload Window

---

## Usage

### Basic commands

- **Toggle:** Click `⚡ Auto: ON` / `✕ Auto: OFF` in the status bar
- **Or:** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **Dashboard:** Click the dashboard icon in the status bar to see CDP status, active sessions, activity log and language picker
- **Logs:** Output panel → `Anti-Remote-Pro`

### Pro commands

All Pro features are reachable via the Command Palette (`Ctrl+Shift+P`):

| Command | What it does |
|---|---|
| `Anti-Remote-Pro: Login with Google` | Sign in to sync your Pro license across devices |
| `Anti-Remote-Pro: Logout` | Clear the local license + signed-in account |
| `Anti-Remote-Pro: Refresh Pro Status` | Force a license re-check against the server |
| `Anti-Remote-Pro: Connect Telegram Bot` | Launch the pairing flow — opens the bot in Telegram, tap **Start** to link this machine |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | Revoke the HMAC key for this machine |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | Force re-download of the signed core payload |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | Global kill-switch (also bound to `Ctrl+Shift+S`) |
| `Anti-Remote-Pro: Fix Missing Conversations` | Re-seed Swarm's conversation index if the sidebar looks out of sync |

> **Tip:** `Ctrl+Shift+S` is the fastest way to pause/resume Swarm + auto-accept when a human teammate drops into your session.

---

## Multi-Agent Workflow

### ⚠️ Agent Manager Limitation (without Swarm Mode)

Antigravity's Agent Manager uses a **single shared webview** — only the active conversation's DOM is rendered. Background conversations are completely unmounted. Without Swarm Mode, both the VS Code Commands API and CDP can only reach the currently visible conversation.

### ✅ Solution: Swarm Mode (Pro)

Swarm Mode solves this by rotating focus across all pending conversations, letting dozens of background agents run hands-free:

- Scans every conversation in the sidebar and picks the one with pending work.
- Respects your idle-seconds setting so it never steals focus while you type.
- Cross-window aware: pausing any one window pauses all of them via file-lock broadcast.
- Safe-by-default: signed core payload, command firewall still applies.

### Fallback: Duplicate Workspace (free)

If you don't have a Pro license, you can still run 2–3 agents in parallel:

1. Click **File → Duplicate Workspace**
2. This opens a second Antigravity window connected to the same project
3. Start a chat in Window 1 and another chat in Window 2
4. Each window has its own webview — the extension auto-clicks buttons in **both windows simultaneously**

---

## Settings

| Setting | Default | Scope | Description |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | Base polling interval in ms (±20 % jitter applied automatically) |
| `autoAcceptV2.customButtonTexts` | `[]` | application | Extra button texts for i18n or custom prompts (e.g. `["toujours autoriser"]`) |
| `autoAcceptV2.cdpPort` | `9333` | machine | CDP port (default avoids conflict with AG Browser Control on 9222) |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | Auto-accept file edit changes (disable to review diffs manually) |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Auto-click Retry / Continue when the agent hits errors or invocation limits |
| `autoAcceptV2.blockedCommands` | `[]` | application | Commands to NEVER auto-run (e.g. `rm`, `git push`, `npm publish`) |
| `autoAcceptV2.allowedCommands` | `[]` | application | If set, ONLY these commands will auto-run (whitelist mode) |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Pro license key — unlocks Swarm Mode + Telegram Remote |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Seconds of user inactivity before Swarm navigates to a pending chat (3–60) |

> **Tip:** Settings are hot-reloaded — changes take effect immediately without restarting.

---

## How it Works

### Persistent CDP + MutationObserver

The extension maintains a **persistent browser-level WebSocket** connection to Chromium's DevTools Protocol. Instead of polling every 1.5s, it injects a **MutationObserver** payload once per target. The observer reacts instantly when React mounts new button elements, with 100ms leading-edge throttle to prevent CPU spikes during streaming output. The extension uses a **whitelist-only target filter** — it only attaches to `vscode-webview://` targets and automatically yields the CDP port when the AG browser sub-agent is detected, preventing ArrayBuffer conflicts.

### Single-Pass DOM Scanner

The button scanner walks the DOM tree **exactly once** per cycle, checking all keywords simultaneously against each node. This is O(D) instead of O(N×D) which could cause UI freezes with many keywords. Priority-aware matching ensures `Run` always beats `Accept`, which always beats `Allow`, regardless of DOM order.

### Webview Guard

Antigravity's agent panel runs in an isolated Chromium process (OOPIF). The injected script uses a deferred `isAgentPanel()` check inside `scanAndClick()` — verifying `.react-app-container` existence dynamically on each scan rather than at injection time. This avoids a race condition where the DOM is unhydrated on `targetCreated`.

### Heartbeat Self-Healing

The CDP connection validates existing sessions every heartbeat cycle (10s). If a session's MutationObserver is dead (execution context cleared by webview navigation or React hot-reload), it automatically re-injects the observer — no reconnection needed. Sessions unreachable 3 times consecutively are cleanly detached and pruned.

### Expand Button Loop Prevention

Expand-type buttons (e.g. browser preview "Expand") use a **click-once-per-session** rule: once clicked, they are permanently suppressed for that CDP session via an `expandedOnce` Set. This prevents the infinite overlay re-open loop where closing the expanded panel triggers a re-click. The state resets naturally when a new agent conversation starts.

### Button Detection

Inside the agent panel, a `TreeWalker` searches for buttons by text content using `startsWith` matching with **word-boundary checks** to prevent false positives (e.g. `accept-test.js` won't match `accept`):

| Priority | Text | Matches |
|---|---|---|
| 1 | `run` | "Run Alt+d" button (not "Always run ^" dropdown) |
| 2 | `accept` | Accept button |
| 3 | `always allow` | Permission prompts |
| 4 | `allow this conversation` | Conversation-scoped permissions |
| 5 | `allow` | Permission prompts |
| 6 | `retry` | Retry prompts |
| 7 | `continue` | Agent invocation limit resume |

### Command Filtering

Blocked and allowed command lists use **word-boundary matching** against the code block above a Run button. For example, blocking `rm` will block `rm -rf /tmp` but NOT `yarn format` or `npm run build`.

---

## Recommended Blocked Commands

The dashboard includes a **Load Safety Presets** button that bulk-imports 50+ destructive command patterns covering filesystem wipers, disk formatters, database drops, force-pushes, and fork bombs.

**One-click:** Open the Dashboard → click **Load Recommended Safety Presets**.

**Bulk paste:** The blocked / allowed inputs support **comma-separated** values — paste a list and hit Enter.

<details>
<summary><b>📋 Manual: Copy to settings.json</b></summary>

Add this to your `settings.json` (`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`):

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

### CDP Auto-Fix

On activation, the extension checks if port 9333 is open (with 9222 fallback). If not, it shows a notification with:
- **Auto-Fix Shortcut (Windows)** — patches `.lnk` shortcuts on Desktop, Start Menu, **and Taskbar**

---

## Troubleshooting

### Bot stops working after a few hours

**Cause:** Either (a) Antigravity silently restarts its Electron process (auto-updates, memory pressure, or extension host crash) and the new process doesn't have `--remote-debugging-port=9333`, or (b) the webview's execution context was cleared by a navigation / hot-reload.

**Fix:** The heartbeat self-healing logic auto-detects and re-injects dead observers. If it still doesn't work, close **all** Antigravity windows completely, then reopen from your patched shortcut.

### Bot is ON but not clicking anything

1. **Toggle OFF → ON** — click the status bar icon twice to restart polling
2. **Check the debug port** — visit `http://127.0.0.1:9333/json/list` in a browser. If it refuses, the debug port is dead (see above)
3. **Check Output logs** — `Ctrl+Shift+U` → dropdown → `Anti-Remote-Pro`. Look for `[CDP] ✓ Thread` lines. If there are none, CDP can't find the agent panel

### Status bar icon not showing after install

1. Run `Ctrl+Shift+P` → `Reload Window`
2. Check that the VSIX was built **with** dependencies (the `ws` package must be included)

---

## Safety

Commands deliberately **excluded** to prevent harm:
- `notification.acceptPrimaryAction` — would auto-click destructive dialogs
- `chatEditing.acceptAllFiles` — causes sidebar Outline toggling
- All merge / git conflict commands — could silently pick the wrong side
- All autocomplete / suggestion commands — would corrupt typing

---

## Security FAQ

**Why does this need `--remote-debugging-port`?**

Antigravity's agent panel runs in an isolated Chromium process. The VS Code Extension API cannot see or interact with the Run / Accept / Allow buttons inside it — they're React UI elements with no registered commands. Chrome DevTools Protocol (CDP) on a localhost port (default 9333) is the only way to reach them.

**Is it safe?**

- **Localhost only** — the port binds to `127.0.0.1`, not `0.0.0.0`. No external machine can connect.
- **Zero telemetry in the auto-accept core** — DOM scanning, button matching, and command filtering never make network calls.
- **The only outbound traffic** is (a) license verification, (b) Telegram Bot API — and only if you pair it, and (c) signed core payload fetch for Swarm Mode. All three are off by default.
- **Signed Pro payload.** The Swarm core engine is Ed25519-signed and verified inside a Node worker before it's compiled in RAM — a man-in-the-middle cannot slip in a rogue scanner.
- **Standard dev workflow** — `--remote-debugging-port` is the same flag used by VS Code extension developers and Electron app debugging.
- **Shortcut patcher is scoped** — the auto-fix only modifies `.lnk` files whose target path contains "Antigravity".
- **No Antigravity files modified** — this extension runs entirely as an external VS Code extension. Uninstall and every trace is gone.

**Will my Telegram chat read my code?**

Only what *you* explicitly ask for. `/peek` returns the visible text of the active agent panel; `/prompt` sends your message in. The extension never proactively pushes code, diffs, screenshots or telemetry to Telegram.

---

## License

MIT
