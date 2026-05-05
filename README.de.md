<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=de"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**Der datenschutzorientierte, sperrresistente, per Telegram steuerbare Auto-Pilot für [Antigravity](https://antigravity.dev) — Googles KI-Codierungsassistenten.**
**Ein Google-Konto, unbegrenzte Geräte.**

### [🌐 Offizielle Website &nbsp;·&nbsp; Jetzt herunterladen →](https://antigravity.apiai.eu.cc/?lang=de)

<sub>
  📖 <b>Lesen Sie dies in:</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <a href="./README.zh-CN.md">简体中文</a> &nbsp;·&nbsp;
  <a href="./README.zh-TW.md">繁體中文</a> &nbsp;·&nbsp;
  <a href="./README.ja.md">日本語</a> &nbsp;·&nbsp;
  <a href="./README.ko.md">한국어</a> &nbsp;·&nbsp;
  <a href="./README.es.md">Español</a> &nbsp;·&nbsp;
  <a href="./README.fr.md">Français</a> &nbsp;·&nbsp;
  <b>Deutsch</b> &nbsp;·&nbsp;
  <a href="./README.pt.md">Português</a> &nbsp;·&nbsp;
  <a href="./README.ru.md">Русский</a> &nbsp;·&nbsp;
  <a href="./README.ar.md">العربية</a> &nbsp;·&nbsp;
  <a href="./README.hi.md">हिन्दी</a>
</sub>

</div>

Akzeptiert Agent-Schritte, Terminal-Befehle, Datei-Bearbeitungen und Berechtigungsabfragen automatisch, sodass der Agent Ihre Arbeit freihändig auslieft — während jedes Byte auf Ihrer Maschine bleibt und Sie jede Ihrer Maschinen vom Telefon aus steuern können.

> 💡 **Schnellstart?** Die [offizielle Seite](https://antigravity.apiai.eu.cc/?lang=de) bietet einen vollständigen Leitfaden, Live-Screenshots, Pro-Preise und den neuesten `.vsix`-Download — alles in 12 Sprachen.

---

## 🔥 Warum Anti-Remote-Pro

### 🔒 1. Absolute Privatsphäre — Ihr Code verlässt nie Ihren Laptop

- **100 % lokale Pipeline.** Die gesamte Button-Erkennung, das DOM-Scannen und die Befehlsfilterung laufen innerhalb Ihres VS Code / Antigravity-Prozesses. Keine Prompts, keine Screenshots, keine Diffs verlassen jemals die Maschine.
- **Debug-Port nur auf Localhost.** CDP wird strikt an `127.0.0.1:9333` gebunden. Kein externer Host im LAN, im Café-WLAN oder im Coworking-Netzwerk kann es erreichen — verifiziert durch Socket-Bindung, nicht nur durch Versprechen.
- **Null Telemetrie.** Der Auto-Accept-Kern führt keine Analyse-Aufrufe, Crash-Reports oder „anonymen Nutzungsstatistiken" durch. Der einzige ausgehende Verkehr geht zu Telegram (nur wenn Sie es koppeln) und zum Lizenzserver (nur zur Schlüsselverifikation).
- **Whitelist-only Target-Attach.** Die CDP-Schicht verbindet sich **nur** mit `vscode-webview://`-Targets, die zum Agent-Panel passen. Sie verweigert die Verbindung zu Ihren anderen Tabs, Browser-Sub-Agents oder jedem Nicht-Antigravity-Chromium-Target.
- **Signiertes Kern-Payload.** Die Pro-Kern-Engine wird als Ed25519-signiertes Payload geladen, in einem Node-Worker verifiziert und im RAM kompiliert — niemals auf Disk geschrieben, niemals durch einen Man-in-the-Middle manipulierbar.
- **Keine Modifikation von Antigravity selbst.** Wir patchen, repacken oder hooken keine Antigravity-Binaries. Reines externes CDP — deinstallieren und es bleiben null Spuren.

### 📱 2. Telegram-Fernsteuerung — steuern Sie Antigravity von überall

Koppeln Sie Ihre IDE einmal mit einem Telegram-Bot, und Ihr Telefon wird zur vollständigen Fernbedienung für den Agent:

- **`/prompt <Text>`** — senden Sie einen neuen Prompt an die aktive Konversation, von überall auf dem Planeten. Vereint automatisch die 4096-Zeichen-Nachrichten-Aufteilungen von Telegram.
- **`/peek [N]`** — lesen Sie die neueste Antwort des Agents direkt in Telegram, ohne Ihren Laptop aufwecken zu müssen.
- **Senden Sie ein Foto mit Bildunterschrift** — fügt den Screenshot dem Prompt für visuelles Debugging unterwegs hinzu.
- **`/pause` & `/resume`** — schalten Sie den globalen Kill-Switch von Ihrem Telefon aus um. Cross-Window-Dateisperre garantiert, dass jedes Antigravity-Fenster sofort gehorcht.
- **`/stop`** — hält die aktuell generierte Antwort an.
- **HMAC-signierte Befehle.** Jeder Telegram-Befehl wird mit einem geräteindividuellen HMAC-Schlüssel verifiziert. Ein geleakter Telegram-Chat reicht *nicht* aus, um Ihre IDE zu kontrollieren.
- **Single-Master-Election.** Wenn Sie 5 Antigravity-Fenster geöffnet haben, gewinnt nur eines die Master-Sperre und verarbeitet Befehle — keine Doppelsendungen, keine Race Conditions.

### 🛡️ 3. Branchenweit Erste Anti-Sperr-Strategie

Die meisten Auto-Klicker werden gesperrt, weil sie Endpunkte in fester Kadenz anhämmern und klicken, während der Mensch noch tippt. Anti-Remote-Pro ist genau umgekehrt entworfen:

- **Menschen-Rhythmus-Timing.** Aktives Polling bei 500 ms mit **±20 % Zufalls-Jitter** + exponentiellem Backoff (gedeckelt bei 30 s) bei aufeinanderfolgenden Fehlern. Keine maschinenperfekten Intervalle zum Fingerprinting.
- **Smart-Sleep im Leerlauf.** Ohne aktive CDP-Sitzung fällt die Engine auf einen 5-Sekunden-Heartbeat — praktisch null IPC-Druck, wenn Sie weg sind.
- **20-Sekunden-Karenz für aktive Benutzer.** Wenn der Benutzer im Chat tippt, das Webview scrollt oder den Editor-Cursor bewegt, werden **alle Auto-Klicks zurückgestellt**. Der Bot wartet buchstäblich, bis Sie aufhören, sodass er nie mit Ihnen mitklickt, während Sie lesen.
- **Kein Binary-Patching.** Antigravity-Dateien, settings.json und das Benutzerdaten-Verzeichnis sind für diese Erweiterung schreibgeschützt. Offizielle Auto-Updates und Integritätsprüfungen laufen sauber durch, weil nichts modifiziert wird.
- **Loopback-only CDP.** Kein TCP-Listener, kein Remote-Forwarding. Das Flag `--remote-debugging-port=9333` ist ein gewöhnliches Electron-Debug-Flag — dasselbe, das Microsoft, Google und JetBrains intern verwenden.
- **Harte Befehls-Firewall.** Eingebaute Blockliste + optionale strikte Allowlist + 50+ kuratierte **Safety Presets** (rm -rf, force-push, drop database, Fork-Bomben, Disk-Wiper, Registry-Löschungen…). Der Bot *weigert sich*, einen destruktiven Befehl auszuführen, selbst wenn der Agent darauf besteht.
- **Click-once-per-session für Expand-Buttons.** Eliminiert die „Endlos-Wiederöffnen"-Schleife, die Missbrauchsheuristiken auslösen könnte.
- **Sofortiges Nachgeben gegenüber dem offiziellen Browser-Sub-Agent.** Wenn AGs eigenes Browser-Tooling Port 9222 aktiviert, löst sich unser Worker und geht aus dem Weg — keine Port-Kollision, keine doppelte Attach-Signatur.

> Kombinierter Effekt: Aus der Sicht des Agent-Backends sehen Sie aus wie ein leicht überdurchschnittlich schneller, makellos höflicher menschlicher Benutzer.

### 🌍 4. Mehrsprachig — 12 Sprachen, Milliarden Nutzer abgedeckt

Anti-Remote-Pro liefert vollständige UI-Übersetzungen (Befehle, Einstellungen, Dashboard, Benachrichtigungen, Telegram-Antworten). Wählen Sie aus dem Dropdown im Dashboard oder lassen Sie es Ihre IDE-Sprache automatisch erkennen.

| # | Sprache | Eigenname | Hauptregionen |
|---|---|---|---|
| 1 | Englisch | English | 🇺🇸 USA · 🇬🇧 UK · 🇨🇦 Kanada · 🇦🇺 Australien · 🇮🇪 Irland · 🇳🇿 Neuseeland · 🇿🇦 Südafrika · 🇸🇬 Singapur · 🇮🇳 Indien (IT) |
| 2 | Vereinfachtes Chinesisch | 简体中文 | 🇨🇳 Festlandchina · 🇸🇬 Singapur · 🇲🇾 Malaysia |
| 3 | Traditionelles Chinesisch | 繁體中文 | 🇹🇼 Taiwan · 🇭🇰 Hongkong · 🇲🇴 Macau |
| 4 | Spanisch | Español | 🇪🇸 Spanien · 🇲🇽 Mexiko · 🇦🇷 Argentinien · 🇨🇴 Kolumbien · 🇨🇱 Chile · 🇵🇪 Peru · 🇻🇪 Venezuela · +14 weitere |
| 5 | Französisch | Français | 🇫🇷 Frankreich · 🇨🇦 Kanada (Québec) · 🇧🇪 Belgien · 🇨🇭 Schweiz · 🇱🇺 Luxemburg · 🇲🇨 Monaco · großer Teil West- und Zentralafrikas |
| 6 | Hindi | हिन्दी | 🇮🇳 Indien · 🇫🇯 Fidschi |
| 7 | Portugiesisch (BR) | Português | 🇧🇷 Brasilien · 🇵🇹 Portugal · 🇦🇴 Angola · 🇲🇿 Mosambik |
| 8 | Russisch | Русский | 🇷🇺 Russland · 🇧🇾 Belarus · 🇰🇿 Kasachstan · 🇰🇬 Kirgistan · 🇺🇿 Usbekistan · 🇺🇦 Ukraine |
| 9 | Arabisch | العربية (RTL) | 🇸🇦 Saudi-Arabien · 🇦🇪 VAE · 🇪🇬 Ägypten · 🇶🇦 Katar · 🇰🇼 Kuwait · 🇧🇭 Bahrain · 🇴🇲 Oman · 🇯🇴 Jordanien · 🇲🇦 Marokko · 🇩🇿 Algerien · 🇹🇳 Tunesien · 🇮🇶 Irak · +10 weitere |
| 10 | Japanisch | 日本語 | 🇯🇵 Japan |
| 11 | Deutsch | Deutsch | 🇩🇪 Deutschland · 🇦🇹 Österreich · 🇨🇭 Schweiz · 🇱🇮 Liechtenstein · 🇱🇺 Luxemburg |
| 12 | Koreanisch | 한국어 | 🇰🇷 Südkorea |

- **Auto-Erkennung** folgt `vscode.env.language` — die Erweiterung liefert Ihre Locale sofort beim ersten Start.
- **Manuelles Override** über das Sprach-Dropdown im Dashboard (bleibt über Reloads erhalten).
- **RTL-bewusst** — die arabische UI dreht die Layout-Richtung automatisch um (`dir="rtl"`).
- **Eigene Schlüsselwort-Overrides** — `autoAcceptV2.customButtonTexts` ermöglicht es Ihnen, lokalisierte Button-Labels für jeden UI-String hinzuzufügen, den wir noch nicht übersetzt haben (z. B. `["toujours autoriser", "siempre permitir"]`).

### 🔗 5. Multi-Geräte-Sync mit Google-Anmeldung — ein Konto, alle Ihre Maschinen

**Melden Sie sich einmal mit Google an** und Anti-Remote-Pro folgt Ihnen überallhin — Desktop, Laptop, Heim-PC, Arbeits-Workstation, Windows, macOS, Linux.

- **Ein-Klick Google OAuth.** `Anti-Remote-Pro: Login with Google` öffnet Ihren Browser, schließt den Standard-Google-OAuth-Flow ab und leitet über einen sicheren `vscode://Pro.antigravity-autoaccept/auth`-URI-Handler zurück zur IDE. Kein Lizenzschlüssel-Copy-Paste, kein E-Mail-Tanz.
- **Pro-Lizenz synchronisiert automatisch zwischen Geräten.** Ihr Abonnement ist an Ihr Google-Konto gebunden, nicht an eine einzelne Maschine. Auf Gerät #2, #3, #10 installieren — anmelden und Pro wird sofort freigeschaltet. Der Lizenzserver verifiziert jede `machineId` bei jedem Refresh gegen Ihr Konto.
- **Gleichzeitige Ausführung auf unbegrenzt vielen Geräten.** Arbeitslaptop, Heim-Desktop, Remote-Dev-Box, eine VM für jeden Kunden — alle können Anti-Remote-Pro parallel unter demselben Konto ausführen.
- **Parallele Flotten.** Jedes Gerät arbeitet unabhängig mit eigener CDP / Swarm / Befehls-Firewall, sodass ein Laptop Konversation A bearbeiten kann, während Ihr Desktop Konversation B ausführt — keiner stiehlt dem anderen den Fokus.
- **Pro-Gerät-Telegram-Kopplung.** Jede Maschine koppelt sich separat mit dem Telegram-Bot und erhält ihren eigenen HMAC-Schlüssel. Sie können sie im Kopplungs-Flow benennen (z. B. „MacBook", „WorkPC") und sie individuell aus demselben Telegram-Chat ansprechen.
- **Cross-Window-Koordination auf derselben Maschine.** Wenn Sie mehrere Antigravity-Fenster auf einem Gerät geöffnet haben, hält ein Dateisperren-Protokoll deren Pause/Resume-Zustand in unter einer Sekunde synchron — keine Doppelklicks, kein Streit.
- **Sofortiger Widerruf.** `Anti-Remote-Pro: Logout` löscht das lokale Token und teilt dem Server mit, dieses Gerät zu invalidieren. Laptop verloren? Von einer anderen Maschine ausloggen + `Refresh Pro Status` und die alte Maschine geht dunkel.
- **Refresh Pro Status.** Plan geändert oder Abo erneuert? Ein Befehl zieht die neuesten Berechtigungen erneut — keine Neuinstallation, kein Neustart.

> In der Praxis: Melden Sie sich einmal auf Ihren 3 Computern an, koppeln Sie jeden mit demselben Telegram-Bot, und Ihr Telefon wird zur zentralen Fernbedienung für Ihre gesamte Coding-Flotte.

---

## ⚡ Kernfähigkeiten auf einen Blick

- **Auto-Klick** Run / Accept / Always Allow / Allow this conversation / Continue / Retry über das gesamte Agent-Panel — prioritätsbewusst, sodass `Run` immer vor `Accept` gewinnt.
- **Auto-Akzeptieren von Datei-Bearbeitungen** mit einem Schalter — jederzeit ausschaltbar, um Diffs manuell zu prüfen.
- **Befehls-Firewall** — Muster-Block oder strikter Whitelist-Modus, beide mit Wortgrenzen-Matching.
- **Safety Presets** — Ein-Klick-Import von 50+ destruktiven Befehlsmustern (Dateisystem-Wiper, Disk-Formatierer, force-push, DB-Drops, Fork-Bomben).
- **Swarm-Modus (Pro)** — rotiert automatisch durch ausstehende Agent-Manager-Konversationen und führt sie freihändig im Hintergrund aus.
- **Telegram Remote (Pro)** — vollständige IDE-Fernsteuerung: `/prompt`, `/peek`, Foto-Prompts, `/pause`, `/resume`, `/stop`, mit HMAC-Auth.
- **Google-Anmeldung + Multi-Geräte-Sync (Pro)** — ein Google-Konto, unbegrenzte Geräte; `vscode://`-URI-Handler-OAuth-Callback; Pro-Gerät-Lizenzverifikation.
- **Cross-Window-Pause** — Pausieren in einem Antigravity-Fenster sendet via Dateisperre an jedes andere Fenster in <1 s.
- **Aktivitäts-Log + Dashboard** — sehen Sie jeden geklickten Button, jede CDP-Sitzung, jeden Telegram-Befehl live.
- **Diagnose-Dump** — kopiert ein strukturiertes Debug-Payload in die Zwischenablage für Ein-Nachricht-Support.
- **Auto-Fix Shortcut** — Windows-`.lnk`-Patcher (Desktop / Startmenü / Taskleiste) für das `--remote-debugging-port`-Flag.
- **Heartbeat-Selbstheilung** — tote MutationObservers (durch Webview-Navigation / Hot-Reload gelöscht) werden alle 10 s erkannt und automatisch wieder injiziert.

---

## Was es tut

Wenn der Antigravity-Agent Datei-Bearbeitungen, Terminal-Befehle vorschlägt oder Tool-Berechtigungen anfordert, akzeptiert diese Erweiterung sie automatisch, sodass Sie nicht jeden Button manuell klicken müssen.

**Zwei Strategien, null Interferenz:**

| Strategie | Was sie verarbeitet | Wie |
|---|---|---|
| **VS Code Commands** (500 ms + Jitter) | Agent-Schritte, Terminal-Befehle | Ruft Antigravitys native Accept-Befehle auf |
| **CDP + MutationObserver** (event-getrieben) | Run, Accept, Always Allow, Continue, Retry | Skript einmal injiziert, reagiert sofort auf DOM-Änderungen |

---

## Einrichtung

### 1. Debug-Modus aktivieren (Erforderlich)

Die Erweiterung benötigt das Chrome DevTools Protocol, um Berechtigungs-Buttons zu klicken. Starten Sie Antigravity mit:

```
--remote-debugging-port=9333
```

> **Warum Port 9333?** Antigravitys eingebauter Browser Control (Chrome-Button in der Toolbar) verwendet standardmäßig Port 9222. Derselbe Port verursacht einen `EADDRINUSE`-Konflikt auf macOS/Linux. Port 9333 vermeidet dies vollständig.

<details>
<summary><b>🪟 Windows</b></summary>

**Automatisch:** Beim ersten Start erkennt die Erweiterung, ob der Port geschlossen ist, und zeigt **„Auto-Fix Shortcut"** an — klicken Sie, um Ihre `.lnk`-Verknüpfung automatisch zu patchen.

**Manuell:** Rechtsklick auf Ihre Antigravity-Verknüpfung → Eigenschaften → an Ziel anhängen:
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**Option 1 — Automator-App (empfohlen):**
1. Öffnen Sie **Automator** → Neues Dokument → **Programm**
2. Suchen Sie **„Shell-Skript ausführen"** in der Bibliothek
3. Einfügen: `open -a "Antigravity" --args --remote-debugging-port=9333`
4. Als „AntiGravity Launcher" auf dem Schreibtisch oder in Programme speichern

**Option 2 — Terminal-Alias** (zu `~/.zshrc` hinzufügen):
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **Hinweis:** Der App-Name muss exakt übereinstimmen. Prüfen Sie mit `ls /Applications/ | grep -i anti`

**Option 3 — Direktes Electron-Binary** (falls `open -a` Argumente nicht korrekt durchreicht):
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**Option 1 — `.desktop`-Datei bearbeiten:**
```bash
# Finden:
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# Exec-Zeile bearbeiten:
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**Option 2 — Shell-Alias** (zu `~/.bashrc` oder `~/.zshrc` hinzufügen):
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**Option 3 — Wrapper-Skript:**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. Erweiterung installieren

**Aus VSIX (empfohlen):**
1. Holen Sie sich das neueste `.vsix`-Paket
2. In Antigravity: `Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. Wählen Sie die heruntergeladene Datei
4. Reload Window

**Manuell:**
1. Kopieren Sie das `src/`-Verzeichnis, `package.json` und `package-lock.json` nach:
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. Führen Sie `npm install` in diesem Verzeichnis aus (installiert die `ws`-Abhängigkeit)
3. Reload Window

---

## Verwendung

### Grundbefehle

- **Umschalten:** Klicken Sie in der Statusleiste auf `⚡ Auto: ON` / `✕ Auto: OFF`
- **Oder:** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **Dashboard:** Klicken Sie auf das Dashboard-Symbol in der Statusleiste, um CDP-Status, aktive Sitzungen, Aktivitäts-Log und Sprachauswahl zu sehen
- **Logs:** Output-Panel → `Anti-Remote-Pro`

### Pro-Befehle

Alle Pro-Funktionen sind über die Befehlspalette (`Ctrl+Shift+P`) erreichbar:

| Befehl | Was er tut |
|---|---|
| `Anti-Remote-Pro: Login with Google` | Anmelden, um Ihre Pro-Lizenz zwischen Geräten zu synchronisieren |
| `Anti-Remote-Pro: Logout` | Lokale Lizenz + angemeldeten Account löschen |
| `Anti-Remote-Pro: Refresh Pro Status` | Lizenz-Re-Check gegen den Server erzwingen |
| `Anti-Remote-Pro: Connect Telegram Bot` | Kopplungs-Flow starten — öffnet den Bot in Telegram, tippen Sie **Start**, um diese Maschine zu verbinden |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | HMAC-Schlüssel für diese Maschine widerrufen |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | Erneuten Download des signierten Kern-Payloads erzwingen |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | Globaler Kill-Switch (auch an `Ctrl+Shift+S` gebunden) |
| `Anti-Remote-Pro: Fix Missing Conversations` | Swarms Konversationsindex neu seeden, wenn die Sidebar nicht synchron wirkt |

> **Tipp:** `Ctrl+Shift+S` ist der schnellste Weg, Swarm + Auto-Accept zu pausieren/fortzusetzen, wenn ein menschlicher Teamkollege Ihre Sitzung betritt.

---

## Multi-Agent-Workflow

### ⚠️ Agent-Manager-Limitation (ohne Swarm-Modus)

Antigravitys Agent Manager verwendet ein **einzelnes geteiltes Webview** — nur das DOM der aktiven Konversation wird gerendert. Hintergrund-Konversationen sind vollständig unmounted. Ohne Swarm-Modus können sowohl die VS Code Commands API als auch CDP nur die aktuell sichtbare Konversation erreichen.

### ✅ Lösung: Swarm-Modus (Pro)

Der Swarm-Modus löst dies, indem er den Fokus über alle ausstehenden Konversationen rotiert und Dutzende Hintergrund-Agents freihändig laufen lässt:

- Scannt jede Konversation in der Sidebar und wählt diejenige mit ausstehender Arbeit.
- Respektiert Ihre Idle-Sekunden-Einstellung, sodass er nie den Fokus stiehlt, während Sie tippen.
- Cross-Window-bewusst: Pausieren eines Fensters pausiert alle via Dateisperren-Broadcast.
- Sicher per default: signiertes Kern-Payload, Befehls-Firewall gilt weiterhin.

### Fallback: Workspace duplizieren (kostenlos)

Wenn Sie keine Pro-Lizenz haben, können Sie trotzdem 2–3 Agents parallel ausführen:

1. Klicken Sie auf **File → Duplicate Workspace**
2. Dies öffnet ein zweites Antigravity-Fenster, das mit demselben Projekt verbunden ist
3. Starten Sie einen Chat in Fenster 1 und einen weiteren Chat in Fenster 2
4. Jedes Fenster hat sein eigenes Webview — die Erweiterung klickt Buttons in **beiden Fenstern gleichzeitig**

---

## Einstellungen

| Einstellung | Standard | Geltungsbereich | Beschreibung |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | Basis-Polling-Intervall in ms (±20 % Jitter automatisch angewandt) |
| `autoAcceptV2.customButtonTexts` | `[]` | application | Zusätzliche Button-Texte für i18n oder benutzerdefinierte Prompts (z. B. `["toujours autoriser"]`) |
| `autoAcceptV2.cdpPort` | `9333` | machine | CDP-Port (Standard vermeidet Konflikt mit AG Browser Control auf 9222) |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | Datei-Bearbeitungen automatisch akzeptieren (deaktivieren, um Diffs manuell zu prüfen) |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Retry / Continue automatisch klicken, wenn der Agent auf Fehler oder Aufruflimits stößt |
| `autoAcceptV2.blockedCommands` | `[]` | application | Befehle, die NIE automatisch ausgeführt werden (z. B. `rm`, `git push`, `npm publish`) |
| `autoAcceptV2.allowedCommands` | `[]` | application | Wenn gesetzt, werden NUR diese Befehle automatisch ausgeführt (Whitelist-Modus) |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Pro-Lizenzschlüssel — schaltet Swarm-Modus + Telegram Remote frei |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Sekunden Benutzer-Inaktivität, bevor Swarm zu einem ausstehenden Chat navigiert (3–60) |

> **Tipp:** Einstellungen werden hot-reloaded — Änderungen treten sofort ohne Neustart in Kraft.

---

## Wie es funktioniert

### Persistentes CDP + MutationObserver

Die Erweiterung pflegt eine **persistente WebSocket-Verbindung auf Browser-Ebene** zum DevTools Protocol von Chromium. Statt alle 1,5 s zu pollen, injiziert sie ein **MutationObserver**-Payload einmal pro Target. Der Observer reagiert sofort, wenn React neue Button-Elemente mountet, mit 100 ms Leading-Edge-Throttle, um CPU-Spitzen während Streaming-Ausgaben zu verhindern. Die Erweiterung verwendet einen **Whitelist-only Target-Filter** — sie verbindet sich nur mit `vscode-webview://`-Targets und gibt den CDP-Port automatisch frei, wenn der AG-Browser-Sub-Agent erkannt wird, was ArrayBuffer-Konflikte verhindert.

### Single-Pass-DOM-Scanner

Der Button-Scanner durchläuft den DOM-Baum **genau einmal** pro Zyklus und prüft alle Schlüsselwörter gleichzeitig gegen jeden Knoten. Das ist O(D) statt O(N×D), was bei vielen Schlüsselwörtern UI-Freezes verursachen könnte. Prioritätsbewusstes Matching stellt sicher, dass `Run` immer `Accept` schlägt, was immer `Allow` schlägt, unabhängig von der DOM-Reihenfolge.

### Webview-Wache

Antigravitys Agent-Panel läuft in einem isolierten Chromium-Prozess (OOPIF). Das injizierte Skript verwendet eine verzögerte `isAgentPanel()`-Prüfung innerhalb von `scanAndClick()` — verifiziert die Existenz von `.react-app-container` dynamisch bei jedem Scan statt zur Injektionszeit. Dies vermeidet eine Race Condition, bei der das DOM bei `targetCreated` nicht hydratisiert ist.

### Heartbeat-Selbstheilung

Die CDP-Verbindung validiert bestehende Sitzungen bei jedem Heartbeat-Zyklus (10 s). Wenn der MutationObserver einer Sitzung tot ist (Ausführungskontext durch Webview-Navigation oder React-Hot-Reload gelöscht), injiziert sie den Observer automatisch erneut — keine Wiederverbindung nötig. Sitzungen, die 3 Mal in Folge unerreichbar sind, werden sauber abgekoppelt und entfernt.

### Expand-Button-Schleifen-Prävention

Expand-Type-Buttons (z. B. „Expand" der Browser-Vorschau) verwenden eine **Click-once-per-session**-Regel: einmal geklickt, werden sie für diese CDP-Sitzung dauerhaft via `expandedOnce`-Set unterdrückt. Dies verhindert die Endlos-Overlay-Wiederöffnen-Schleife, bei der das Schließen des erweiterten Panels einen Re-Klick auslöst. Der Zustand wird bei einer neuen Agent-Konversation natürlich zurückgesetzt.

### Button-Erkennung

Innerhalb des Agent-Panels durchsucht ein `TreeWalker` Buttons nach Textinhalt mit `startsWith`-Matching und **Wortgrenzen-Prüfungen**, um Falsch-Positive zu verhindern (z. B. matcht `accept-test.js` nicht `accept`):

| Priorität | Text | Matches |
|---|---|---|
| 1 | `run` | „Run Alt+d"-Button (nicht „Always run ^"-Dropdown) |
| 2 | `accept` | Accept-Button |
| 3 | `always allow` | Berechtigungs-Prompts |
| 4 | `allow this conversation` | Konversationsbezogene Berechtigungen |
| 5 | `allow` | Berechtigungs-Prompts |
| 6 | `retry` | Retry-Prompts |
| 7 | `continue` | Fortsetzung nach Agent-Aufruflimit |

### Befehlsfilterung

Blockierte und erlaubte Befehlslisten verwenden **Wortgrenzen-Matching** gegen den Codeblock über einem Run-Button. Beispielsweise blockiert `rm` den Befehl `rm -rf /tmp`, aber NICHT `yarn format` oder `npm run build`.

---

## Empfohlene blockierte Befehle

Das Dashboard enthält einen **Load Safety Presets**-Button, der 50+ destruktive Befehlsmuster massenhaft importiert, die Dateisystem-Wiper, Disk-Formatierer, Datenbank-Drops, Force-Pushes und Fork-Bomben abdecken.

**Ein-Klick:** Dashboard öffnen → klicken Sie auf **Load Recommended Safety Presets**.

**Massen-Einfügen:** Die Eingaben für blockiert / erlaubt unterstützen **kommagetrennte** Werte — fügen Sie eine Liste ein und drücken Sie Enter.

<details>
<summary><b>📋 Manuell: in settings.json kopieren</b></summary>

Fügen Sie dies zu Ihrer `settings.json` hinzu (`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`):

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

### CDP-Auto-Fix

Bei der Aktivierung prüft die Erweiterung, ob Port 9333 offen ist (mit 9222 als Fallback). Wenn nicht, zeigt sie eine Benachrichtigung mit:
- **Auto-Fix Shortcut (Windows)** — patcht `.lnk`-Verknüpfungen auf dem Desktop, im Startmenü **und in der Taskleiste**

---

## Fehlerbehebung

### Bot hört nach einigen Stunden auf zu funktionieren

**Ursache:** Entweder (a) Antigravity startet seinen Electron-Prozess still neu (Auto-Updates, Speicherdruck oder Extension-Host-Crash) und der neue Prozess hat kein `--remote-debugging-port=9333`, oder (b) der Ausführungskontext des Webview wurde durch eine Navigation / Hot-Reload gelöscht.

**Fix:** Die Heartbeat-Selbstheilungslogik erkennt und re-injiziert tote Observer automatisch. Wenn es immer noch nicht funktioniert, schließen Sie **alle** Antigravity-Fenster vollständig und öffnen Sie sie dann von Ihrer gepatchten Verknüpfung erneut.

### Bot ist ON, klickt aber nichts

1. **OFF → ON umschalten** — klicken Sie zweimal auf das Statusleisten-Symbol, um das Polling neu zu starten
2. **Debug-Port prüfen** — besuchen Sie `http://127.0.0.1:9333/json/list` in einem Browser. Wenn er ablehnt, ist der Debug-Port tot (siehe oben)
3. **Output-Logs prüfen** — `Ctrl+Shift+U` → Dropdown → `Anti-Remote-Pro`. Suchen Sie nach `[CDP] ✓ Thread`-Zeilen. Wenn keine vorhanden sind, kann CDP das Agent-Panel nicht finden

### Statusleisten-Symbol erscheint nach Installation nicht

1. Führen Sie `Ctrl+Shift+P` → `Reload Window` aus
2. Prüfen Sie, ob das VSIX **mit** Abhängigkeiten gebaut wurde (das `ws`-Paket muss enthalten sein)

---

## Sicherheit

Befehle, die zur Schadenverhinderung **bewusst ausgeschlossen** sind:
- `notification.acceptPrimaryAction` — würde destruktive Dialoge automatisch klicken
- `chatEditing.acceptAllFiles` — verursacht Sidebar-Outline-Toggling
- Alle Merge- / Git-Konflikt-Befehle — könnten still die falsche Seite wählen
- Alle Autovervollständigungs- / Vorschlagsbefehle — würden Ihre Eingabe korrumpieren

---

## Sicherheits-FAQ

**Warum braucht das `--remote-debugging-port`?**

Antigravitys Agent-Panel läuft in einem isolierten Chromium-Prozess. Die VS Code Extension API kann die Run / Accept / Allow-Buttons darin weder sehen noch mit ihnen interagieren — sie sind React-UI-Elemente ohne registrierte Befehle. Das Chrome DevTools Protocol (CDP) auf einem Localhost-Port (Standard 9333) ist der einzige Weg, sie zu erreichen.

**Ist es sicher?**

- **Nur Localhost** — der Port bindet an `127.0.0.1`, nicht an `0.0.0.0`. Keine externe Maschine kann sich verbinden.
- **Null Telemetrie im Auto-Accept-Kern** — DOM-Scanning, Button-Matching und Befehlsfilterung machen niemals Netzwerk-Aufrufe.
- **Der einzige ausgehende Verkehr** ist (a) Lizenzverifikation, (b) Telegram-Bot-API — und nur, wenn Sie sie koppeln, und (c) Abruf des signierten Kern-Payloads für den Swarm-Modus. Alle drei sind standardmäßig aus.
- **Signiertes Pro-Payload.** Die Swarm-Kern-Engine ist Ed25519-signiert und wird in einem Node-Worker verifiziert, bevor sie im RAM kompiliert wird — ein Man-in-the-Middle kann keinen Schurken-Scanner einschleusen.
- **Standard-Dev-Workflow** — `--remote-debugging-port` ist dasselbe Flag, das von VS Code-Extension-Entwicklern und Electron-App-Debugging verwendet wird.
- **Verknüpfungs-Patcher hat begrenzten Geltungsbereich** — der Auto-Fix modifiziert nur `.lnk`-Dateien, deren Zielpfad „Antigravity" enthält.
- **Keine Antigravity-Dateien modifiziert** — diese Erweiterung läuft vollständig als externe VS Code-Erweiterung. Deinstallieren und alle Spuren sind weg.

**Liest mein Telegram-Chat meinen Code?**

Nur, was *Sie* explizit anfordern. `/peek` gibt den sichtbaren Text des aktiven Agent-Panels zurück; `/prompt` sendet Ihre Nachricht hinein. Die Erweiterung pusht niemals proaktiv Code, Diffs, Screenshots oder Telemetrie an Telegram.

---

## Lizenz

MIT
