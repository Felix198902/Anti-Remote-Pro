<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=ja"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**[Antigravity](https://antigravity.dev)（Google の AI コーディングアシスタント）向け、プライバシー最優先・BAN 耐性・Telegram リモート操作対応の自動操縦拡張機能。**
**Google アカウント 1 つで、デバイス数無制限。**

### [🌐 公式サイト &nbsp;·&nbsp; 今すぐダウンロード →](https://antigravity.apiai.eu.cc/?lang=ja)

<sub>
  📖 <b>他の言語で読む:</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <a href="./README.zh-CN.md">简体中文</a> &nbsp;·&nbsp;
  <a href="./README.zh-TW.md">繁體中文</a> &nbsp;·&nbsp;
  <b>日本語</b> &nbsp;·&nbsp;
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

Agent のステップ、ターミナルコマンド、ファイル編集、権限プロンプトを自動承認することで、Agent があなたの作業を完全ハンズフリーで完遂します。すべてのデータはローカルに留まり、スマートフォンから全マシンを遠隔操作できます。

> 💡 **今すぐ始めたい？** [公式サイト](https://antigravity.apiai.eu.cc/?lang=ja) には完全ガイド、スクリーンショット、Pro 料金、最新の `.vsix` ダウンロードが揃っています——すべて 12 言語対応です。

---

## 🔥 なぜ Anti-Remote-Pro なのか

### 🔒 1. 絶対的なプライバシー — コードは本体から一歩も出ない

- **100% ローカル完結。** ボタン検出、DOM スキャン、コマンドフィルタはすべて VS Code / Antigravity のプロセス内で実行されます。プロンプト、スクリーンショット、diff が端末から外に出ることは一切ありません。
- **localhost 限定のデバッグポート。** CDP は `127.0.0.1:9333` に厳密にバインドされます。LAN、カフェ Wi-Fi、コワーキングの同一ネットワーク上にある外部ホストから接続できません——約束ではなく、socket バインドで保証しています。
- **ゼロテレメトリ。** 自動承認コアは、分析リクエスト、クラッシュレポート、「匿名利用統計」の類を一切送信しません。外向き通信は、ペアリングした場合の Telegram と、ライセンスサーバーへの鍵検証のみです。
- **ホワイトリスト限定のターゲットアタッチ。** CDP レイヤーは Agent パネルにマッチする `vscode-webview://` ターゲット**にのみ**アタッチします。他のタブ、ブラウザ sub-agent、Antigravity 以外の Chromium ターゲットへのアタッチは拒否します。
- **署名済みコアペイロード。** Pro コアエンジンは Ed25519 で署名されたペイロードとして取得され、Node worker 内で検証後、RAM 上でコンパイルされます——ディスクには一切書き込まれず、中間者攻撃による改ざんも不可能です。
- **Antigravity 本体には一切手を加えない。** Antigravity のバイナリにパッチを当てたり、リパックしたり、フックすることはありません。純粋な外部 CDP 通信のみ——アンインストール後は痕跡ゼロです。

### 📱 2. Telegram リモート操作 — どこからでも Antigravity を操縦

IDE と Telegram ボットを一度ペアリングするだけで、スマートフォンが Agent のフルリモコンになります：

- **`/prompt <テキスト>`** — 地球のどこからでも現在の会話に新しいプロンプトを送信。Telegram の 4096 文字分割メッセージを自動で結合します。
- **`/peek [N]`** — Telegram 内で Agent の最新返信を確認、ノート PC を起こす必要なし。
- **キャプション付き写真** — スクリーンショットをプロンプトに添付、外出先でも視覚的デバッグ可能。
- **`/pause` と `/resume`** — スマホからグローバルキルスイッチを切り替え。クロスウィンドウのファイルロックが、すべての Antigravity ウィンドウの即時反映を保証します。
- **`/stop`** — 生成中のレスポンスを停止。
- **HMAC 署名コマンド。** すべての Telegram コマンドはデバイス別 HMAC キーで検証されます。Telegram チャットが漏洩しても、それだけで IDE は制御できません。
- **シングルマスター選出。** Antigravity ウィンドウを 5 枚開いていても、マスターロックを取った 1 つだけがコマンドを処理します——重複送信なし、競合状態なし。

### 🛡️ 3. 業界初の BAN 耐性戦略

多くの自動クリッカーがアカウント BAN されるのは、固定周期でエンドポイントを叩き、ユーザーが入力中でもクリックしてしまうからです。Anti-Remote-Pro は真逆の設計です：

- **人間リズムのタイミング。** 500 ms のアクティブポーリング + **±20% のランダムジッター** + 連続エラー時の指数バックオフ（上限 30 s）。フィンガープリントされる機械的な完璧な間隔は存在しません。
- **アイドル時のスマートスリープ。** アクティブな CDP セッションがないとき、エンジンは 5 秒ハートビートに落ちます——離席中の IPC 負荷は実質ゼロ。
- **20 秒のユーザーアクティブ猶予ウィンドウ。** ユーザーがチャット入力中、webview スクロール中、エディタカーソル移動中の場合、**すべての自動クリックが保留されます**。ボットは文字通りあなたが手を止めるのを待つので、読んでいる最中に横から押すことがありません。
- **バイナリパッチなし。** Antigravity のファイル、settings.json、ユーザーデータディレクトリは、この拡張機能にとって読み取り専用です。何も変更しないため、公式の自動アップデートと完整性チェックは問題なく通過します。
- **ループバック限定 CDP。** TCP リスナーなし、リモートフォワーディングなし。`--remote-debugging-port=9333` フラグは、Microsoft、Google、JetBrains が内部で使っているのと同じ、素の Electron デバッグフラグです。
- **ハードなコマンドファイアウォール。** 内蔵ブロックリスト + 任意の厳格ホワイトリスト + 50 以上の厳選 **Safety Presets**（rm -rf、force-push、drop database、fork 爆弾、ディスク消去、レジストリ削除など）。Agent がどれほど主張しても、ボットは破壊的コマンドの実行を**拒否**します。
- **展開ボタンはセッション 1 回限定。** 「無限リオープン」ループを排除し、不正利用ヒューリスティックに引っかかるリスクを回避。
- **公式 Browser sub-agent への即時譲歩。** AG 自身のブラウザツールがポート 9222 を起動したら、我々の worker は即座にデタッチして道を空けます——ポート競合なし、二重アタッチの痕跡なし。

> 総合効果：Agent バックエンドから見ると、あなたは「平均よりやや速いが、礼儀正しい人間ユーザー」に見えます。

### 🌍 4. 多言語対応 — 12 言語、数十億ユーザーをカバー

Anti-Remote-Pro は完全な UI 翻訳を搭載（コマンド、設定、ダッシュボード、通知、Telegram 返信）。ダッシュボードのドロップダウンから選ぶか、IDE の言語を自動検出させることができます。

| # | 言語 | 現地名 | 主な地域 |
|---|---|---|---|
| 1 | 英語 | English | 🇺🇸 アメリカ · 🇬🇧 イギリス · 🇨🇦 カナダ · 🇦🇺 オーストラリア · 🇮🇪 アイルランド · 🇳🇿 ニュージーランド · 🇿🇦 南アフリカ · 🇸🇬 シンガポール · 🇮🇳 インド（IT） |
| 2 | 簡体中国語 | 简体中文 | 🇨🇳 中国本土 · 🇸🇬 シンガポール · 🇲🇾 マレーシア |
| 3 | 繁体中国語 | 繁體中文 | 🇹🇼 台湾 · 🇭🇰 香港 · 🇲🇴 マカオ |
| 4 | スペイン語 | Español | 🇪🇸 スペイン · 🇲🇽 メキシコ · 🇦🇷 アルゼンチン · 🇨🇴 コロンビア · 🇨🇱 チリ · 🇵🇪 ペルー · 🇻🇪 ベネズエラ · +14 カ国 |
| 5 | フランス語 | Français | 🇫🇷 フランス · 🇨🇦 カナダ（ケベック） · 🇧🇪 ベルギー · 🇨🇭 スイス · 🇱🇺 ルクセンブルク · 🇲🇨 モナコ · 西・中央アフリカの大部分 |
| 6 | ヒンディー語 | हिन्दी | 🇮🇳 インド · 🇫🇯 フィジー |
| 7 | ポルトガル語（BR） | Português | 🇧🇷 ブラジル · 🇵🇹 ポルトガル · 🇦🇴 アンゴラ · 🇲🇿 モザンビーク |
| 8 | ロシア語 | Русский | 🇷🇺 ロシア · 🇧🇾 ベラルーシ · 🇰🇿 カザフスタン · 🇰🇬 キルギス · 🇺🇿 ウズベキスタン · 🇺🇦 ウクライナ |
| 9 | アラビア語 | العربية（RTL） | 🇸🇦 サウジアラビア · 🇦🇪 UAE · 🇪🇬 エジプト · 🇶🇦 カタール · 🇰🇼 クウェート · 🇧🇭 バーレーン · 🇴🇲 オマーン · 🇯🇴 ヨルダン · 🇲🇦 モロッコ · 🇩🇿 アルジェリア · 🇹🇳 チュニジア · 🇮🇶 イラク · +10 カ国 |
| 10 | 日本語 | 日本語 | 🇯🇵 日本 |
| 11 | ドイツ語 | Deutsch | 🇩🇪 ドイツ · 🇦🇹 オーストリア · 🇨🇭 スイス · 🇱🇮 リヒテンシュタイン · 🇱🇺 ルクセンブルク |
| 12 | 韓国語 | 한국어 | 🇰🇷 韓国 |

- **自動検出** は `vscode.env.language` に従います——拡張機能は初回起動時にあなたのロケールで動作します。
- **手動切替** はダッシュボードの言語ドロップダウンから（リロード後も保持されます）。
- **RTL 対応** — アラビア語 UI はレイアウト方向を自動で反転します（`dir="rtl"`）。
- **カスタムキーワード上書き** — `autoAcceptV2.customButtonTexts` で、未翻訳の UI 文字列に対応するローカライズボタンラベルを追加できます（例：`["toujours autoriser", "siempre permitir"]`）。

### 🔗 5. Google サインインによるマルチデバイス同期 — 1 アカウント、すべてのマシン

**Google で一度サインイン**するだけで、Anti-Remote-Pro はどこへでもついてきます——デスクトップ、ノート、自宅 PC、仕事用ワークステーション、Windows、macOS、Linux。

- **ワンクリック Google OAuth。** `Anti-Remote-Pro: Login with Google` でブラウザが開き、標準の Google OAuth を完了した後、安全な `vscode://Pro.antigravity-autoaccept/auth` URI ハンドラ経由で IDE に戻ります。ライセンスキーのコピペ不要、メールの手間も不要。
- **Pro ライセンスはデバイス間で自動同期。** サブスクリプションは Google アカウントに紐づいており、個別のマシンではありません。2 台目、3 台目、10 台目のデバイスにインストール——サインインすれば即座に Pro が解放されます。ライセンスサーバーは更新のたびに `machineId` をアカウント単位で検証します。
- **無制限台数で同時実行可能。** 仕事用ノート、自宅デスクトップ、リモート開発ボックス、クライアント別の VM——すべて同一アカウントで Anti-Remote-Pro を並行稼働できます。
- **並列艦隊。** 各デバイスは独立して動作し、自分の CDP / Swarm / コマンドファイアウォールを持ちます。ノート PC で会話 A、デスクトップで会話 B を回しても、互いにフォーカスを奪い合いません。
- **デバイス別の Telegram ペアリング。** 各マシンは個別に Telegram ボットとペアリングし、独自の HMAC キーを受け取ります。ペアリングフローで名前（例 "MacBook"、"WorkPC"）を付けられ、同じ Telegram チャット内で個別にアドレッシングできます。
- **同一マシン内でのウィンドウ間協調。** 同じ PC で複数の Antigravity ウィンドウが開いている場合、ファイルロックプロトコルが 1 秒未満でポーズ/レジューム状態を同期します——重複クリックなし、競合なし。
- **即時失効。** `Anti-Remote-Pro: Logout` はローカルトークンを消し、サーバーに該当デバイスの無効化を通知します。ノート PC を紛失したら、別のマシンからログアウト + `Refresh Pro Status` で古いマシンが即座にダーク化します。
- **Refresh Pro Status。** プラン変更やサブスク更新後は、1 コマンドで最新の権限を再取得——再インストールも再起動も不要。

> 実用例：3 台の PC に一度ずつサインインし、それぞれを同一 Telegram ボットにペアリングすれば、スマホがコーディング艦隊全体の中央リモコンになります。

---

## ⚡ コア機能一覧

- **自動クリック** Agent パネル上の Run / Accept / Always Allow / Allow this conversation / Continue / Retry——優先順位付きで、`Run` は常に `Accept` より優先されます。
- **ファイル編集の自動承認**、トグル 1 つで切替——いつでもオフにして diff を手動レビューできます。
- **コマンドファイアウォール** — パターンブロックまたは厳格ホワイトリストモード、いずれも語境界マッチングを使用。
- **Safety Presets** — 50 以上の破壊的コマンドパターン（ファイルシステム消去、ディスクフォーマット、force-push、DB drop、fork 爆弾）をワンクリックでインポート。
- **Swarm モード（Pro）** — Agent Manager の未処理会話を自動でローテーションし、バックグラウンドでハンズフリーに実行。
- **Telegram Remote（Pro）** — フル IDE リモート：`/prompt`、`/peek`、写真プロンプト、`/pause`、`/resume`、`/stop`、HMAC 認証付き。
- **Google サインイン + マルチデバイス同期（Pro）** — 1 つの Google アカウントで無制限のデバイス、`vscode://` URI ハンドラによる OAuth コールバック、デバイス単位のライセンス検証。
- **クロスウィンドウポーズ** — 1 つの Antigravity ウィンドウでポーズすると、ファイルロック経由で他の全ウィンドウに 1 秒以内にブロードキャスト。
- **アクティビティログ + ダッシュボード** — クリックしたボタン、CDP セッション、Telegram コマンドをライブで確認。
- **診断ダンプ** — 構造化されたデバッグペイロードをクリップボードにコピーし、1 メッセージでサポートへ。
- **自動修復ショートカット** — Windows の `.lnk` パッチャー（デスクトップ / スタートメニュー / タスクバー）で `--remote-debugging-port` フラグを適用。
- **ハートビート自己修復** — webview のナビゲーション / ホットリロードで消えた MutationObserver を 10 秒ごとに検出し、自動で再注入。

---

## 何をするものか

Antigravity Agent がファイル編集、ターミナルコマンド、ツール権限を求めてきたとき、この拡張機能が自動承認することで、いちいちボタンを押す必要がなくなります。

**2 つの戦略、ゼロ干渉：**

| 戦略 | 扱う対象 | 実装方法 |
|---|---|---|
| **VS Code コマンド**（500 ms + ジッター） | Agent ステップ、ターミナルコマンド | Antigravity ネイティブの accept コマンドを呼び出す |
| **CDP + MutationObserver**（イベント駆動） | Run、Accept、Always Allow、Continue、Retry | ターゲットごとに 1 回だけスクリプト注入、DOM 変化に即時反応 |

---

## セットアップ

### 1. デバッグモードの有効化（必須）

この拡張機能は権限ボタンのクリックに Chrome DevTools Protocol を使います。Antigravity を以下のフラグ付きで起動してください：

```
--remote-debugging-port=9333
```

> **なぜポート 9333？** Antigravity に組み込まれた Browser Control（ツールバーの Chrome ボタン）がデフォルトで 9222 を使います。同じポートだと macOS/Linux で `EADDRINUSE` 競合が発生します。9333 を使えばこれを完全に回避できます。

<details>
<summary><b>🪟 Windows</b></summary>

**自動：** 初回起動時、拡張機能はポートが閉じていることを検出し **"Auto-Fix Shortcut"** を表示します——クリックするだけで `.lnk` ショートカットに自動パッチを適用します。

**手動：** Antigravity のショートカットを右クリック → プロパティ → Target の末尾に追加：
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**オプション 1 — Automator アプリ（推奨）：**
1. **Automator** を開く → 新規書類 → **アプリケーション**
2. ライブラリから **「シェルスクリプトを実行」** を検索
3. 貼り付け：`open -a "Antigravity" --args --remote-debugging-port=9333`
4. "AntiGravity Launcher" という名前でデスクトップまたはアプリケーションに保存

**オプション 2 — ターミナルのエイリアス**（`~/.zshrc` に追加）：
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **注意：** アプリ名は完全一致でなければなりません。`ls /Applications/ | grep -i anti` で確認してください。

**オプション 3 — Electron バイナリを直接実行**（`open -a` で引数が正しく渡らない場合）：
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**オプション 1 — `.desktop` ファイルを編集：**
```bash
# 場所を探す：
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# Exec 行を編集：
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**オプション 2 — シェルエイリアス**（`~/.bashrc` または `~/.zshrc` に追加）：
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**オプション 3 — ラッパースクリプト：**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. 拡張機能のインストール

**VSIX から（推奨）：**
1. 最新の `.vsix` パッケージを入手
2. Antigravity で：`Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. ダウンロードしたファイルを選択
4. Reload Window

**手動：**
1. `src/` ディレクトリ、`package.json`、`package-lock.json` を以下にコピー：
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. そのディレクトリで `npm install` を実行（`ws` 依存関係をインストール）
3. Reload Window

---

## 使い方

### 基本コマンド

- **トグル：** ステータスバーの `⚡ Auto: ON` / `✕ Auto: OFF` をクリック
- **または：** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **ダッシュボード：** ステータスバーのダッシュボードアイコンをクリックして、CDP 状態、アクティブセッション、アクティビティログ、言語選択を確認
- **ログ：** Output パネル → `Anti-Remote-Pro`

### Pro コマンド

すべての Pro 機能はコマンドパレット（`Ctrl+Shift+P`）から実行可能：

| コマンド | 機能 |
|---|---|
| `Anti-Remote-Pro: Login with Google` | サインインして Pro ライセンスをデバイス間で同期 |
| `Anti-Remote-Pro: Logout` | ローカルライセンスとサインイン済みアカウントをクリア |
| `Anti-Remote-Pro: Refresh Pro Status` | サーバーへのライセンス再検証を強制 |
| `Anti-Remote-Pro: Connect Telegram Bot` | ペアリングフロー起動——Telegram でボットを開き **Start** をタップして本マシンをリンク |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | 本マシンの HMAC キーを失効 |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | 署名済みコアペイロードの強制再ダウンロード |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | グローバルキルスイッチ（`Ctrl+Shift+S` にもバインド） |
| `Anti-Remote-Pro: Fix Missing Conversations` | サイドバーが同期ずれしているときに Swarm の会話インデックスを再構築 |

> **ヒント：** 人間の同僚があなたのセッションに入ってきたとき、Swarm + 自動承認を一瞬でポーズ/レジュームする最速の方法は `Ctrl+Shift+S` です。

---

## マルチ Agent ワークフロー

### ⚠️ Agent Manager の制限（Swarm モードなし）

Antigravity の Agent Manager は**単一の共有 webview** を使います——アクティブな会話の DOM だけがレンダリングされ、バックグラウンド会話は完全に unmount されます。Swarm モードなしでは、VS Code Commands API も CDP も、現在表示中の会話にしか届きません。

### ✅ 解決策：Swarm モード（Pro）

Swarm モードは、待機中の全会話をローテーションでフォーカス移動させることで、数十個のバックグラウンド Agent をハンズフリー実行できるようにします：

- サイドバーの全会話をスキャンし、未処理作業のあるものを選びます。
- あなたの idle-seconds 設定を守り、入力中は絶対にフォーカスを奪いません。
- クロスウィンドウ対応：1 つのウィンドウをポーズすると、ファイルロック経由で全ウィンドウがポーズします。
- デフォルトで安全：署名済みコアペイロード、コマンドファイアウォールは引き続き適用。

### フォールバック：Duplicate Workspace（無料）

Pro ライセンスがなくても、2–3 個の Agent を並列実行できます：

1. **File → Duplicate Workspace** をクリック
2. 同じプロジェクトに接続された 2 つ目の Antigravity ウィンドウが開きます
3. ウィンドウ 1 でチャットを開始し、ウィンドウ 2 で別のチャットを開始
4. 各ウィンドウは独自の webview を持ちます——拡張機能は**両方のウィンドウで同時に**ボタンを自動クリックします

---

## 設定

| 設定 | デフォルト | スコープ | 説明 |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | 基本ポーリング間隔（ms、自動で ±20% ジッターが加わる） |
| `autoAcceptV2.customButtonTexts` | `[]` | application | i18n やカスタムプロンプト向けの追加ボタンテキスト（例：`["toujours autoriser"]`） |
| `autoAcceptV2.cdpPort` | `9333` | machine | CDP ポート（デフォルトで AG Browser Control の 9222 と競合しない） |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | ファイル編集を自動承認（無効化で diff を手動レビュー） |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Agent がエラーや呼び出し上限に当たったとき Retry / Continue を自動クリック |
| `autoAcceptV2.blockedCommands` | `[]` | application | 絶対に自動実行しないコマンド（例：`rm`、`git push`、`npm publish`） |
| `autoAcceptV2.allowedCommands` | `[]` | application | 設定された場合、**これらのコマンドのみ**自動実行（ホワイトリストモード） |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Pro ライセンスキー——Swarm モード + Telegram Remote を解放 |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Swarm が未処理チャットに遷移する前に要求される無操作秒数（3–60） |

> **ヒント：** 設定はホットリロード——変更は再起動なしに即時反映されます。

---

## 仕組み

### 永続化された CDP + MutationObserver

拡張機能は Chromium の DevTools Protocol への**ブラウザレベルの永続 WebSocket** 接続を維持します。1.5 秒ごとのポーリングではなく、ターゲットごとに 1 回 **MutationObserver** ペイロードを注入します。React が新しいボタン要素をマウントすると observer が即座に反応、ストリーミング出力中の CPU ピークを防ぐために 100ms のリーディングエッジスロットルを適用します。拡張機能は**ホワイトリスト限定のターゲットフィルタ**を使います——`vscode-webview://` ターゲットにのみアタッチし、AG ブラウザ sub-agent を検出すると自動的に CDP ポートを譲り、ArrayBuffer 競合を防ぎます。

### 単一パス DOM スキャナ

ボタンスキャナは 1 サイクルあたり**DOM ツリーをちょうど 1 回だけ**歩き、各ノードに対して全キーワードを同時にチェックします。キーワード数が多いときに UI フリーズを引き起こす可能性のある O(N×D) ではなく、O(D) で済みます。優先順位付きマッチングにより、DOM 順序に関係なく `Run` は常に `Accept` より優先され、`Accept` は常に `Allow` より優先されます。

### Webview ガード

Antigravity の Agent パネルは隔離された Chromium プロセス（OOPIF）で動作します。注入されるスクリプトは `scanAndClick()` の中で遅延された `isAgentPanel()` チェックを使います——注入時点ではなく、スキャンのたびに `.react-app-container` の存在を動的に検証します。これにより `targetCreated` 時点で DOM が hydrate されていないという競合状態を回避します。

### ハートビート自己修復

CDP 接続はハートビートサイクル（10 秒）ごとに既存セッションを検証します。セッションの MutationObserver が死んでいる場合（webview のナビゲーションや React ホットリロードで実行コンテキストがクリアされた）、再接続なしで observer を自動再注入します。連続 3 回到達不能なセッションはクリーンにデタッチ・整理されます。

### 展開ボタンのループ防止

展開系ボタン（例：browser preview の "Expand"）は**セッション 1 回限定**ルールを使います：一度クリックされると、`expandedOnce` Set を介してその CDP セッションで恒久的に抑制されます。これにより、展開パネルを閉じると再クリックがトリガーされる無限再オープンループを防ぎます。新しい Agent 会話が始まると状態は自然にリセットされます。

### ボタン検出

Agent パネル内では、`TreeWalker` が `startsWith` マッチングと**語境界チェック**を組み合わせてテキスト内容でボタンを検索し、誤マッチを防ぎます（例：`accept-test.js` は `accept` にマッチしません）：

| 優先度 | テキスト | マッチ対象 |
|---|---|---|
| 1 | `run` | "Run Alt+d" ボタン（"Always run ^" ドロップダウンではない） |
| 2 | `accept` | Accept ボタン |
| 3 | `always allow` | 権限プロンプト |
| 4 | `allow this conversation` | 会話スコープの権限 |
| 5 | `allow` | 権限プロンプト |
| 6 | `retry` | Retry プロンプト |
| 7 | `continue` | Agent 呼び出し上限後の再開 |

### コマンドフィルタリング

ブロックと許可のコマンドリストは、Run ボタン上のコードブロックに対して**語境界マッチング**を使います。例えば `rm` をブロックすると `rm -rf /tmp` はブロックされますが、`yarn format` や `npm run build` は**ブロックされません**。

---

## 推奨されるブロックコマンド

ダッシュボードには **Load Safety Presets** ボタンがあり、ファイルシステム消去、ディスクフォーマット、データベース削除、force-push、fork 爆弾などをカバーする 50 以上の破壊的コマンドパターンを一括インポートします。

**ワンクリック：** ダッシュボードを開く → **Load Recommended Safety Presets** をクリック。

**一括貼り付け：** ブロック／許可入力欄は**カンマ区切り**の値をサポート——リストを貼り付けて Enter を押すだけ。

<details>
<summary><b>📋 手動：settings.json にコピー</b></summary>

これを `settings.json` に追加（`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`）：

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

アクティベート時、拡張機能はポート 9333 が開いているか確認します（9222 もフォールバックとして確認）。開いていない場合、以下のオプション付き通知を表示：
- **Auto-Fix Shortcut（Windows）** — デスクトップ、スタートメニュー、**タスクバー**の `.lnk` ショートカットにパッチを適用

---

## トラブルシューティング

### 数時間後にボットが動かなくなる

**原因：** (a) Antigravity が Electron プロセスをサイレントに再起動し（自動更新、メモリ圧迫、拡張ホストクラッシュ）、新プロセスに `--remote-debugging-port=9333` が付いていない、または (b) webview の実行コンテキストがナビゲーション／ホットリロードでクリアされた。

**修復：** ハートビート自己修復ロジックが死んだ observer を自動検出・再注入します。それでも動かない場合、**すべての** Antigravity ウィンドウを完全に閉じてから、パッチ済みショートカットで再度開いてください。

### ボットは ON だが何もクリックしない

1. **OFF → ON に切替** — ステータスバーアイコンを 2 回クリックしてポーリングを再開
2. **デバッグポートを確認** — ブラウザで `http://127.0.0.1:9333/json/list` にアクセス。拒否される場合、デバッグポートが死んでいます（上記参照）
3. **Output ログを確認** — `Ctrl+Shift+U` → ドロップダウン → `Anti-Remote-Pro`。`[CDP] ✓ Thread` のような行を探す。1 つもなければ CDP が Agent パネルを見つけられていません

### インストール後にステータスバーアイコンが表示されない

1. `Ctrl+Shift+P` → `Reload Window`
2. VSIX が**依存関係付き**でビルドされているか確認（`ws` パッケージがパッケージに含まれている必要あり）

---

## セーフティ

害を防ぐため、以下のコマンドは**意図的に除外**されています：
- `notification.acceptPrimaryAction` — 破壊的ダイアログを自動クリックしてしまう
- `chatEditing.acceptAllFiles` — サイドバーの Outline トグルを引き起こす
- すべての merge / git コンフリクト関連コマンド — 誤った側を静かに選ぶ可能性
- すべての自動補完／サジェスト関連コマンド — タイピングを破壊する

---

## セキュリティ FAQ

**なぜ `--remote-debugging-port` が必要？**

Antigravity の Agent パネルは隔離された Chromium プロセスで動作します。VS Code 拡張 API はその中の Run / Accept / Allow ボタンを見ることも操作することもできません——それらは登録済みコマンドを持たない React UI 要素だからです。localhost ポート（デフォルト 9333）上の Chrome DevTools Protocol (CDP) がそれに到達する唯一の方法です。

**安全ですか？**

- **localhost のみ** — ポートは `127.0.0.1` にバインドされ、`0.0.0.0` ではありません。外部マシンからは接続できません。
- **自動承認コアはゼロテレメトリ** — DOM スキャン、ボタンマッチング、コマンドフィルタリングはネットワークコールを行いません。
- **唯一の外向き通信**は (a) ライセンス検証、(b) Telegram Bot API（ペアリング時のみ）、(c) Swarm モード用の署名済みコアペイロード取得。3 つともデフォルトでオフです。
- **署名済み Pro ペイロード。** Swarm コアエンジンは Ed25519 署名され、Node worker 内で検証後に RAM でコンパイルされます——中間者攻撃が悪意あるスキャナを忍び込ませることはできません。
- **標準的な開発ワークフロー** — `--remote-debugging-port` は VS Code 拡張開発者や Electron アプリのデバッグで使われるのと同じフラグです。
- **ショートカットパッチャーはスコープ付き** — 自動修復はターゲットパスに "Antigravity" を含む `.lnk` ファイルのみを変更します。
- **Antigravity のファイルは一切変更されない** — この拡張機能は完全に外部 VS Code 拡張として動作します。アンインストール後は痕跡ゼロ。

**Telegram のチャットは私のコードを読みますか？**

あなたが**明示的に求めた**ものだけ。`/peek` はアクティブな Agent パネルの可視テキストを返します。`/prompt` はあなたのメッセージを送り込みます。拡張機能はコード、diff、スクリーンショット、テレメトリを Telegram にプッシュすることはありません。

---

## ライセンス

MIT
