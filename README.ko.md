<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=ko"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**[Antigravity](https://antigravity.dev)(Google AI 코딩 어시스턴트)를 위한, 프라이버시 우선·차단 방지·Telegram 원격 제어를 지원하는 자동 조종 확장 기능.**
**Google 계정 하나로, 기기 수 무제한.**

### [🌐 공식 사이트 &nbsp;·&nbsp; 지금 다운로드 →](https://antigravity.apiai.eu.cc/?lang=ko)

<sub>
  📖 <b>다른 언어로 읽기:</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <a href="./README.zh-CN.md">简体中文</a> &nbsp;·&nbsp;
  <a href="./README.zh-TW.md">繁體中文</a> &nbsp;·&nbsp;
  <a href="./README.ja.md">日本語</a> &nbsp;·&nbsp;
  <b>한국어</b> &nbsp;·&nbsp;
  <a href="./README.es.md">Español</a> &nbsp;·&nbsp;
  <a href="./README.fr.md">Français</a> &nbsp;·&nbsp;
  <a href="./README.de.md">Deutsch</a> &nbsp;·&nbsp;
  <a href="./README.pt.md">Português</a> &nbsp;·&nbsp;
  <a href="./README.ru.md">Русский</a> &nbsp;·&nbsp;
  <a href="./README.ar.md">العربية</a> &nbsp;·&nbsp;
  <a href="./README.hi.md">हिन्दी</a>
</sub>

</div>

Agent 단계, 터미널 명령, 파일 편집, 권한 프롬프트를 자동 승인하여 Agent 가 여러분의 작업을 완전히 핸즈프리로 처리합니다. 모든 데이터는 로컬에 유지되며, 모든 기기를 휴대폰으로 원격 조종할 수 있습니다.

> 💡 **빠르게 시작하시겠습니까?** [공식 사이트](https://antigravity.apiai.eu.cc/?lang=ko)에서 전체 가이드, 스크린샷, Pro 가격, 최신 `.vsix` 다운로드를 제공합니다——모두 12개 언어로.

---

## 🔥 왜 Anti-Remote-Pro 인가

### 🔒 1. 절대적 프라이버시 — 코드가 노트북을 떠나지 않습니다

- **100% 로컬 파이프라인.** 모든 버튼 감지, DOM 스캔, 명령 필터링이 여러분의 VS Code / Antigravity 프로세스 내부에서 실행됩니다. 프롬프트, 스크린샷, diff 어느 것도 기기를 떠나지 않습니다.
- **localhost 전용 디버그 포트.** CDP 는 `127.0.0.1:9333` 에 엄격히 바인딩됩니다. LAN, 카페 Wi-Fi, 공유 사무실 네트워크의 외부 호스트는 접근할 수 없습니다——약속이 아닌 socket 바인딩으로 보장됩니다.
- **제로 텔레메트리.** 자동 승인 코어는 분석 요청, 크래시 리포트, "익명 사용 통계" 등을 일절 전송하지 않습니다. 외부 트래픽은 (페어링한 경우) Telegram 과 (키 검증용) 라이센스 서버만입니다.
- **화이트리스트 전용 타겟 연결.** CDP 레이어는 Agent 패널과 일치하는 `vscode-webview://` 타겟**에만** 연결합니다. 다른 탭, 브라우저 하위 Agent, Antigravity 가 아닌 Chromium 타겟에는 연결을 거부합니다.
- **서명된 코어 페이로드.** Pro 코어 엔진은 Ed25519 로 서명된 페이로드로 받아, Node worker 내부에서 검증한 뒤 RAM 에서 컴파일됩니다——디스크에 기록되지 않으며, 중간자가 변조할 수 없습니다.
- **Antigravity 자체는 수정하지 않습니다.** Antigravity 바이너리에 패치하거나 재포장하거나 후킹하지 않습니다. 순수 외부 CDP 통신——제거하면 흔적이 남지 않습니다.

### 📱 2. Telegram 원격 제어 — 어디에서나 Antigravity 조종

IDE 와 Telegram 봇을 한 번 페어링하면 휴대폰이 Agent 의 완전한 리모컨이 됩니다:

- **`/prompt <텍스트>`** — 지구 어디에서든 현재 대화에 새 프롬프트를 전송. Telegram 의 4096 자 분할 메시지를 자동으로 이어 붙입니다.
- **`/peek [N]`** — Telegram 안에서 Agent 의 최신 답변을 바로 확인, 노트북을 깨울 필요 없음.
- **캡션 포함 사진 전송** — 스크린샷을 프롬프트에 첨부하여 이동 중에도 시각적 디버깅이 가능.
- **`/pause` & `/resume`** — 휴대폰에서 전역 킬 스위치 전환. 크로스 윈도우 파일 잠금으로 모든 Antigravity 창이 즉시 반영됩니다.
- **`/stop`** — 현재 생성 중인 응답 중단.
- **HMAC 서명 명령.** 모든 Telegram 명령은 기기별 HMAC 키로 검증됩니다. Telegram 채팅이 유출되어도 그것만으로는 IDE 를 제어할 수 없습니다.
- **단일 마스터 선출.** 5개의 Antigravity 창을 열어도 마스터 잠금을 얻은 하나만 명령을 처리합니다——중복 전송 없음, 경쟁 조건 없음.

### 🛡️ 3. 업계 최초의 차단 방지 전략

대부분의 오토 클리커가 계정 플래그를 받는 이유는 고정된 주기로 엔드포인트를 두들기고 사용자가 입력 중인데도 클릭하기 때문입니다. Anti-Remote-Pro 는 정반대로 설계되었습니다:

- **사람 리듬 타이밍.** 500 ms 능동 폴링 + **±20% 랜덤 지터** + 연속 오류 시 지수 백오프(최대 30 s). 지문으로 남길 기계적인 완벽한 간격이 없습니다.
- **유휴 시 스마트 슬립.** 활성 CDP 세션이 없을 때 엔진은 5 초 하트비트로 떨어집니다——자리를 비울 때 IPC 부담이 사실상 0입니다.
- **20 초 사용자 활성 유예 윈도우.** 사용자가 채팅에 타이핑 중, webview 를 스크롤 중, 에디터 커서를 움직이는 중이라면 **모든 자동 클릭이 보류됩니다**. 봇은 말 그대로 여러분이 멈추기를 기다리므로, 읽는 도중에 옆에서 클릭하지 않습니다.
- **바이너리 패치 없음.** Antigravity 파일, settings.json, 사용자 데이터 디렉토리는 이 확장 기능에게 읽기 전용입니다. 아무것도 수정하지 않으므로 공식 자동 업데이트와 무결성 검사를 문제없이 통과합니다.
- **루프백 전용 CDP.** TCP 리스너 없음, 원격 포워딩 없음. `--remote-debugging-port=9333` 플래그는 Microsoft, Google, JetBrains 가 내부적으로 사용하는 것과 동일한 평범한 Electron 디버그 플래그입니다.
- **강력한 명령 방화벽.** 내장 블록리스트 + 선택적 엄격 화이트리스트 + 50+ 개의 엄선된 **Safety Presets**(rm -rf, force-push, drop database, fork 폭탄, 디스크 와이퍼, 레지스트리 삭제 등). Agent 가 고집하더라도 봇은 파괴적인 명령의 실행을 **거부**합니다.
- **확장 버튼은 세션당 한 번.** "무한 재오픈" 루프를 제거하여 남용 휴리스틱에 걸릴 위험을 방지합니다.
- **공식 Browser 하위 Agent 에 즉시 양보.** AG 자체 브라우저 도구가 9222 포트를 활성화하면 우리 worker 는 즉시 분리하고 길을 내어줍니다——포트 충돌 없음, 이중 연결 지문 없음.

> 종합 효과: Agent 백엔드의 관점에서 여러분은 "평균보다 약간 빠르지만 흠잡을 데 없이 예의 바른 인간 사용자"처럼 보입니다.

### 🌍 4. 다국어 — 12개 언어, 수십억 사용자 커버

Anti-Remote-Pro 는 전체 UI 번역을 제공합니다(명령, 설정, 대시보드, 알림, Telegram 응답). 대시보드의 드롭다운에서 선택하거나 IDE 언어를 자동 감지하도록 할 수 있습니다.

| # | 언어 | 현지 이름 | 주요 지역 |
|---|---|---|---|
| 1 | 영어 | English | 🇺🇸 미국 · 🇬🇧 영국 · 🇨🇦 캐나다 · 🇦🇺 호주 · 🇮🇪 아일랜드 · 🇳🇿 뉴질랜드 · 🇿🇦 남아프리카 · 🇸🇬 싱가포르 · 🇮🇳 인도(IT) |
| 2 | 간체 중국어 | 简体中文 | 🇨🇳 중국 본토 · 🇸🇬 싱가포르 · 🇲🇾 말레이시아 |
| 3 | 번체 중국어 | 繁體中文 | 🇹🇼 대만 · 🇭🇰 홍콩 · 🇲🇴 마카오 |
| 4 | 스페인어 | Español | 🇪🇸 스페인 · 🇲🇽 멕시코 · 🇦🇷 아르헨티나 · 🇨🇴 콜롬비아 · 🇨🇱 칠레 · 🇵🇪 페루 · 🇻🇪 베네수엘라 · +14개국 |
| 5 | 프랑스어 | Français | 🇫🇷 프랑스 · 🇨🇦 캐나다(퀘벡) · 🇧🇪 벨기에 · 🇨🇭 스위스 · 🇱🇺 룩셈부르크 · 🇲🇨 모나코 · 서·중앙 아프리카 대부분 |
| 6 | 힌디어 | हिन्दी | 🇮🇳 인도 · 🇫🇯 피지 |
| 7 | 포르투갈어(브라질) | Português | 🇧🇷 브라질 · 🇵🇹 포르투갈 · 🇦🇴 앙골라 · 🇲🇿 모잠비크 |
| 8 | 러시아어 | Русский | 🇷🇺 러시아 · 🇧🇾 벨라루스 · 🇰🇿 카자흐스탄 · 🇰🇬 키르기스스탄 · 🇺🇿 우즈베키스탄 · 🇺🇦 우크라이나 |
| 9 | 아랍어 | العربية (RTL) | 🇸🇦 사우디 · 🇦🇪 UAE · 🇪🇬 이집트 · 🇶🇦 카타르 · 🇰🇼 쿠웨이트 · 🇧🇭 바레인 · 🇴🇲 오만 · 🇯🇴 요르단 · 🇲🇦 모로코 · 🇩🇿 알제리 · 🇹🇳 튀니지 · 🇮🇶 이라크 · +10개국 |
| 10 | 일본어 | 日本語 | 🇯🇵 일본 |
| 11 | 독일어 | Deutsch | 🇩🇪 독일 · 🇦🇹 오스트리아 · 🇨🇭 스위스 · 🇱🇮 리히텐슈타인 · 🇱🇺 룩셈부르크 |
| 12 | 한국어 | 한국어 | 🇰🇷 대한민국 |

- **자동 감지** 는 `vscode.env.language` 를 따릅니다——확장 기능은 첫 실행 시 즉시 여러분의 로케일로 동작합니다.
- **수동 전환** 은 대시보드 언어 드롭다운에서(다시 로드해도 유지됩니다).
- **RTL 인식** — 아랍어 UI 는 레이아웃 방향을 자동으로 반전합니다(`dir="rtl"`).
- **사용자 지정 키워드 재정의** — `autoAcceptV2.customButtonTexts` 로 아직 번역되지 않은 UI 문자열에 대한 지역화 버튼 레이블을 추가할 수 있습니다(예: `["toujours autoriser", "siempre permitir"]`).

### 🔗 5. Google 로그인으로 멀티 디바이스 동기화 — 한 계정, 모든 기기

**Google 로 한 번 로그인**하면 Anti-Remote-Pro 가 어디든 따라갑니다——데스크탑, 노트북, 홈 PC, 업무용 워크스테이션, Windows, macOS, Linux.

- **원클릭 Google OAuth.** `Anti-Remote-Pro: Login with Google` 이 브라우저를 열어 표준 Google OAuth 를 완료한 다음, 안전한 `vscode://Pro.antigravity-autoaccept/auth` URI 핸들러를 통해 IDE 로 돌아옵니다. 라이선스 키 복사 붙여넣기 불필요, 이메일 왕복 불필요.
- **Pro 라이선스는 기기 간 자동 동기화.** 여러분의 구독은 Google 계정에 바인딩되며 개별 머신이 아닙니다. 2, 3, 10 번째 기기에 설치——로그인하면 즉시 Pro 가 해제됩니다. 라이선스 서버는 새로 고침할 때마다 각 `machineId` 를 계정에 대해 검증합니다.
- **무제한 기기 동시 실행.** 업무용 노트북, 집 데스크탑, 원격 개발 박스, 클라이언트별 VM——모두 동일 계정으로 Anti-Remote-Pro 를 병렬 실행 가능.
- **병렬 플릿.** 각 기기는 독립적으로 동작하며 자체 CDP / Swarm / 명령 방화벽을 가집니다. 노트북이 대화 A를 처리하는 동안 데스크탑이 대화 B를 실행할 수 있으며, 서로 포커스를 빼앗지 않습니다.
- **기기별 Telegram 페어링.** 각 머신은 Telegram 봇과 개별적으로 페어링하고 자체 HMAC 키를 받습니다. 페어링 과정에서 이름(예: "MacBook", "WorkPC")을 지정할 수 있으며, 동일한 Telegram 채팅에서 개별적으로 주소 지정 가능.
- **동일 머신 내 창 간 협조.** 한 기기에 여러 Antigravity 창이 열려 있을 때 파일 잠금 프로토콜이 1 초 미만 내에 모든 창의 일시 정지/재개 상태를 동기화합니다——중복 클릭 없음, 충돌 없음.
- **즉시 취소.** `Anti-Remote-Pro: Logout` 은 로컬 토큰을 지우고 서버에 해당 기기 무효화를 지시합니다. 노트북을 잃었나요? 다른 기기에서 로그아웃 + `Refresh Pro Status` 로 옛 기기가 즉시 비활성화됩니다.
- **Refresh Pro Status.** 요금제 변경이나 구독 갱신? 한 개 명령으로 최신 권한을 다시 가져옵니다——재설치, 재시작 불필요.

> 실전 사용: 3대의 컴퓨터에 각각 한 번씩 로그인하고 각각을 동일한 Telegram 봇에 페어링하면, 여러분의 휴대폰이 전체 코딩 플릿의 중앙 리모컨이 됩니다.

---

## ⚡ 핵심 기능 한눈에

- **자동 클릭** Agent 패널의 Run / Accept / Always Allow / Allow this conversation / Continue / Retry——우선순위 인식으로 `Run` 이 항상 `Accept` 보다 먼저입니다.
- **파일 편집 자동 승인**, 토글 하나로 전환——언제든 끄고 diff 를 수동으로 검토 가능.
- **명령 방화벽** — 패턴 블록 또는 엄격한 화이트리스트 모드, 둘 다 단어 경계 매칭 사용.
- **Safety Presets** — 50+ 개의 파괴적 명령 패턴(파일시스템 와이퍼, 디스크 포맷터, force-push, DB drop, fork 폭탄)을 원클릭 가져오기.
- **Swarm 모드(Pro)** — Agent Manager 의 대기 중 대화 간 자동 로테이션, 백그라운드에서 핸즈프리 실행.
- **Telegram Remote(Pro)** — 완전한 IDE 원격: `/prompt`, `/peek`, 사진 프롬프트, `/pause`, `/resume`, `/stop`, HMAC 인증.
- **Google 로그인 + 멀티 디바이스 동기화(Pro)** — 하나의 Google 계정, 무제한 기기; `vscode://` URI 핸들러 OAuth 콜백; 기기별 라이선스 검증.
- **크로스 윈도우 일시 정지** — 한 Antigravity 창에서 일시 정지하면 파일 잠금으로 다른 모든 창에 1 초 이내 브로드캐스트.
- **활동 로그 + 대시보드** — 클릭된 모든 버튼, 모든 CDP 세션, 모든 Telegram 명령을 실시간으로 확인.
- **진단 덤프** — 구조화된 디버그 페이로드를 클립보드에 복사, 메시지 하나로 지원 접수.
- **자동 수정 바로 가기** — Windows `.lnk` 패처(데스크탑 / 시작 메뉴 / 작업 표시줄)로 `--remote-debugging-port` 플래그 적용.
- **하트비트 자가 치유** — webview 탐색 / 핫 리로드로 사라진 MutationObserver 를 10초마다 감지하고 자동 재주입.

---

## 무엇을 하는가

Antigravity Agent 가 파일 편집, 터미널 명령, 도구 권한을 제안할 때 이 확장 기능이 자동 승인하여 일일이 버튼을 클릭할 필요가 없게 합니다.

**두 가지 전략, 제로 간섭:**

| 전략 | 처리 대상 | 구현 방식 |
|---|---|---|
| **VS Code 명령**(500 ms + 지터) | Agent 단계, 터미널 명령 | Antigravity 네이티브 accept 명령 호출 |
| **CDP + MutationObserver**(이벤트 기반) | Run, Accept, Always Allow, Continue, Retry | 타겟당 한 번 스크립트 주입, DOM 변경에 즉시 반응 |

---

## 설정

### 1. 디버그 모드 활성화(필수)

이 확장 기능은 권한 버튼을 클릭하기 위해 Chrome DevTools Protocol 을 필요로 합니다. Antigravity 를 다음 플래그로 실행하세요:

```
--remote-debugging-port=9333
```

> **왜 포트 9333?** Antigravity 내장 Browser Control(툴바의 Chrome 버튼)이 기본적으로 9222 를 사용합니다. 같은 포트를 사용하면 macOS/Linux 에서 `EADDRINUSE` 충돌이 발생합니다. 9333 을 사용하면 이를 완전히 회피합니다.

<details>
<summary><b>🪟 Windows</b></summary>

**자동:** 첫 실행 시 확장 기능이 포트가 닫혀 있음을 감지하고 **"Auto-Fix Shortcut"** 을 표시합니다——클릭하면 `.lnk` 바로 가기에 자동으로 패치를 적용합니다.

**수동:** Antigravity 바로 가기를 우클릭 → 속성 → Target 끝에 추가:
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**옵션 1 — Automator 앱(권장):**
1. **Automator** 열기 → 새 문서 → **응용 프로그램**
2. 라이브러리에서 **"셸 스크립트 실행"** 검색
3. 붙여 넣기: `open -a "Antigravity" --args --remote-debugging-port=9333`
4. "AntiGravity Launcher" 로 데스크탑 또는 응용 프로그램에 저장

**옵션 2 — 터미널 별칭**(`~/.zshrc` 에 추가):
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **참고:** 앱 이름은 정확히 일치해야 합니다. `ls /Applications/ | grep -i anti` 로 확인하세요.

**옵션 3 — Electron 바이너리 직접 실행**(`open -a` 가 인수를 올바르게 전달하지 못할 때):
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**옵션 1 — `.desktop` 파일 편집:**
```bash
# 위치 찾기:
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# Exec 줄 편집:
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**옵션 2 — 셸 별칭**(`~/.bashrc` 또는 `~/.zshrc` 에 추가):
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**옵션 3 — 래퍼 스크립트:**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. 확장 기능 설치

**VSIX 에서(권장):**
1. 최신 `.vsix` 패키지 획득
2. Antigravity 에서: `Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. 다운로드한 파일 선택
4. Reload Window

**수동:**
1. `src/` 디렉토리, `package.json`, `package-lock.json` 을 다음으로 복사:
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. 해당 디렉토리에서 `npm install` 실행(`ws` 의존성 설치)
3. Reload Window

---

## 사용법

### 기본 명령

- **전환:** 상태 표시줄의 `⚡ Auto: ON` / `✕ Auto: OFF` 클릭
- **또는:** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **대시보드:** 상태 표시줄의 대시보드 아이콘을 클릭하여 CDP 상태, 활성 세션, 활동 로그, 언어 선택기 확인
- **로그:** Output 패널 → `Anti-Remote-Pro`

### Pro 명령

모든 Pro 기능은 명령 팔레트(`Ctrl+Shift+P`)에서 접근 가능:

| 명령 | 기능 |
|---|---|
| `Anti-Remote-Pro: Login with Google` | 로그인하여 Pro 라이선스를 기기 간 동기화 |
| `Anti-Remote-Pro: Logout` | 로컬 라이선스 + 로그인 계정 제거 |
| `Anti-Remote-Pro: Refresh Pro Status` | 서버에 대한 라이선스 재검증 강제 |
| `Anti-Remote-Pro: Connect Telegram Bot` | 페어링 흐름 시작——Telegram 에서 봇을 열고 **Start** 탭하여 이 기기 연결 |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | 이 기기의 HMAC 키 취소 |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | 서명된 코어 페이로드 강제 재다운로드 |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | 전역 킬 스위치(`Ctrl+Shift+S` 에도 바인딩) |
| `Anti-Remote-Pro: Fix Missing Conversations` | 사이드바가 동기화되지 않을 때 Swarm 의 대화 인덱스 재시드 |

> **팁:** 사람 동료가 여러분의 세션에 들어왔을 때 Swarm + 자동 승인을 일시 정지/재개하는 가장 빠른 방법은 `Ctrl+Shift+S` 입니다.

---

## 멀티 Agent 워크플로

### ⚠️ Agent Manager 제한(Swarm 모드 없이)

Antigravity 의 Agent Manager 는 **단일 공유 webview** 를 사용합니다——활성 대화의 DOM 만 렌더링되고, 백그라운드 대화는 완전히 unmount 됩니다. Swarm 모드 없이는 VS Code Commands API 와 CDP 모두 현재 보이는 대화에만 도달할 수 있습니다.

### ✅ 해결책: Swarm 모드(Pro)

Swarm 모드는 모든 대기 중 대화 간에 포커스를 로테이션하여 수십 개의 백그라운드 Agent 가 핸즈프리로 실행되도록 해결합니다:

- 사이드바의 모든 대화를 스캔하고 대기 작업이 있는 것을 선택합니다.
- 여러분의 idle-seconds 설정을 존중하여 타이핑 중에는 절대 포커스를 빼앗지 않습니다.
- 크로스 윈도우 인식: 한 창을 일시 정지하면 파일 잠금 브로드캐스트로 모든 창이 일시 정지됩니다.
- 기본적으로 안전: 서명된 코어 페이로드, 명령 방화벽이 여전히 적용됩니다.

### 대안: Duplicate Workspace(무료)

Pro 라이선스가 없어도 2–3 개의 Agent 를 병렬 실행할 수 있습니다:

1. **File → Duplicate Workspace** 클릭
2. 동일한 프로젝트에 연결된 두 번째 Antigravity 창이 열립니다
3. 창 1에서 채팅 시작, 창 2에서 다른 채팅 시작
4. 각 창은 자체 webview 를 가집니다——확장 기능이 **두 창 모두에서 동시에** 버튼을 자동 클릭합니다

---

## 설정 항목

| 설정 | 기본값 | 범위 | 설명 |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | 기본 폴링 간격(ms, ±20% 지터 자동 적용) |
| `autoAcceptV2.customButtonTexts` | `[]` | application | i18n 또는 사용자 지정 프롬프트를 위한 추가 버튼 텍스트(예: `["toujours autoriser"]`) |
| `autoAcceptV2.cdpPort` | `9333` | machine | CDP 포트(기본값이 AG Browser Control 9222 와 충돌 없음) |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | 파일 편집 자동 승인(비활성화하여 diff 수동 검토) |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Agent 가 오류나 호출 한도에 걸렸을 때 Retry / Continue 자동 클릭 |
| `autoAcceptV2.blockedCommands` | `[]` | application | 절대 자동 실행하지 않을 명령(예: `rm`, `git push`, `npm publish`) |
| `autoAcceptV2.allowedCommands` | `[]` | application | 설정 시 **이 명령들만** 자동 실행(화이트리스트 모드) |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Pro 라이선스 키——Swarm 모드 + Telegram Remote 해제 |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Swarm 이 대기 중 채팅으로 이동하기 전에 요구되는 사용자 무조작 초 수(3–60) |

> **팁:** 설정은 핫 리로드되므로——변경이 재시작 없이 즉시 반영됩니다.

---

## 작동 방식

### 지속적 CDP + MutationObserver

확장 기능은 Chromium 의 DevTools Protocol 에 대한 **브라우저 수준의 지속적 WebSocket** 연결을 유지합니다. 1.5초마다 폴링하는 대신 타겟당 **MutationObserver** 페이로드를 한 번 주입합니다. React 가 새 버튼 요소를 마운트하면 observer 가 즉시 반응하며, 스트리밍 출력 중 CPU 피크를 방지하기 위해 100ms 리딩 에지 스로틀을 적용합니다. 확장 기능은 **화이트리스트 전용 타겟 필터**를 사용합니다——`vscode-webview://` 타겟에만 연결하고, AG 브라우저 하위 Agent 가 감지되면 자동으로 CDP 포트를 양보하여 ArrayBuffer 충돌을 방지합니다.

### 단일 패스 DOM 스캐너

버튼 스캐너는 주기당 **DOM 트리를 정확히 한 번** 순회하며, 각 노드에 대해 모든 키워드를 동시에 확인합니다. 키워드가 많을 때 UI 정지를 유발할 수 있는 O(N×D) 대신 O(D) 입니다. 우선순위 기반 매칭으로 DOM 순서와 관계없이 `Run` 이 항상 `Accept` 보다, `Accept` 가 항상 `Allow` 보다 우선합니다.

### Webview 가드

Antigravity 의 Agent 패널은 격리된 Chromium 프로세스(OOPIF)에서 실행됩니다. 주입된 스크립트는 `scanAndClick()` 내부에서 지연된 `isAgentPanel()` 검사를 사용합니다——주입 시점이 아닌 스캔마다 `.react-app-container` 존재를 동적으로 검증합니다. 이는 `targetCreated` 시점에 DOM 이 hydrate 되지 않은 경쟁 조건을 회피합니다.

### 하트비트 자가 치유

CDP 연결은 하트비트 사이클(10초)마다 기존 세션을 검증합니다. 세션의 MutationObserver 가 죽었다면(webview 탐색이나 React 핫 리로드로 실행 컨텍스트가 지워짐) 재연결 없이 observer 를 자동으로 재주입합니다. 연속 3회 도달 불가능한 세션은 깨끗하게 분리되어 정리됩니다.

### 확장 버튼 루프 방지

확장 유형 버튼(예: browser preview 의 "Expand")은 **세션당 한 번** 규칙을 사용합니다: 한 번 클릭되면 `expandedOnce` Set 을 통해 해당 CDP 세션에서 영구히 억제됩니다. 이는 확장된 패널을 닫으면 재클릭을 트리거하는 무한 재오픈 루프를 방지합니다. 새로운 Agent 대화가 시작되면 상태가 자연히 재설정됩니다.

### 버튼 감지

Agent 패널 내부에서 `TreeWalker` 가 `startsWith` 매칭과 **단어 경계 검사**를 사용하여 텍스트 내용으로 버튼을 검색하여 잘못된 매칭을 방지합니다(예: `accept-test.js` 는 `accept` 와 매칭되지 않음):

| 우선순위 | 텍스트 | 매칭 대상 |
|---|---|---|
| 1 | `run` | "Run Alt+d" 버튼("Always run ^" 드롭다운 아님) |
| 2 | `accept` | Accept 버튼 |
| 3 | `always allow` | 권한 프롬프트 |
| 4 | `allow this conversation` | 대화 범위 권한 |
| 5 | `allow` | 권한 프롬프트 |
| 6 | `retry` | Retry 프롬프트 |
| 7 | `continue` | Agent 호출 한도 재개 |

### 명령 필터링

차단/허용 명령 목록은 Run 버튼 위의 코드 블록에 대해 **단어 경계 매칭**을 사용합니다. 예를 들어 `rm` 차단은 `rm -rf /tmp` 는 차단하지만 `yarn format` 이나 `npm run build` 는 **차단하지 않습니다**.

---

## 권장 차단 명령

대시보드에는 파일시스템 와이퍼, 디스크 포맷터, 데이터베이스 삭제, force-push, fork 폭탄을 커버하는 50+ 개의 파괴적 명령 패턴을 일괄 가져오는 **Load Safety Presets** 버튼이 있습니다.

**원클릭:** 대시보드 열기 → **Load Recommended Safety Presets** 클릭.

**일괄 붙여 넣기:** 차단/허용 입력란은 **쉼표로 구분된** 값을 지원합니다——목록을 붙여 넣고 Enter 를 누르세요.

<details>
<summary><b>📋 수동: settings.json 에 복사</b></summary>

이것을 `settings.json` 에 추가(`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`):

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

### CDP 자동 수정

활성화 시 확장 기능은 포트 9333 이 열려 있는지 확인합니다(9222 도 폴백으로 확인). 열려 있지 않으면 다음 옵션과 함께 알림을 표시합니다:
- **Auto-Fix Shortcut(Windows)** — 데스크탑, 시작 메뉴, **작업 표시줄**의 `.lnk` 바로 가기에 패치 적용

---

## 문제 해결

### 봇이 몇 시간 후 작동을 멈춥니다

**원인:** (a) Antigravity 가 Electron 프로세스를 조용히 재시작했거나(자동 업데이트, 메모리 압박, 확장 호스트 충돌) 새 프로세스에 `--remote-debugging-port=9333` 이 없거나, (b) webview 의 실행 컨텍스트가 탐색/핫 리로드로 지워졌습니다.

**수정:** 하트비트 자가 치유 로직이 죽은 observer 를 자동으로 감지하고 재주입합니다. 그래도 작동하지 않으면 **모든** Antigravity 창을 완전히 닫고 패치된 바로 가기에서 다시 엽니다.

### 봇이 ON 이지만 아무것도 클릭하지 않습니다

1. **OFF → ON 전환** — 상태 표시줄 아이콘을 두 번 클릭하여 폴링 재시작
2. **디버그 포트 확인** — 브라우저에서 `http://127.0.0.1:9333/json/list` 방문. 거부되면 디버그 포트가 죽었습니다(위 참조)
3. **Output 로그 확인** — `Ctrl+Shift+U` → 드롭다운 → `Anti-Remote-Pro`. `[CDP] ✓ Thread` 줄을 찾습니다. 없다면 CDP 가 Agent 패널을 찾을 수 없습니다

### 설치 후 상태 표시줄 아이콘이 보이지 않습니다

1. `Ctrl+Shift+P` → `Reload Window`
2. VSIX 가 **의존성과 함께** 빌드되었는지 확인(`ws` 패키지가 포함되어야 함)

---

## 안전

해를 방지하기 위해 **의도적으로 제외된** 명령:
- `notification.acceptPrimaryAction` — 파괴적 대화 상자를 자동 클릭합니다
- `chatEditing.acceptAllFiles` — 사이드바 Outline 토글을 유발합니다
- 모든 merge / git 충돌 명령 — 잘못된 쪽을 조용히 선택할 수 있습니다
- 모든 자동 완성 / 제안 명령 — 타이핑을 손상시킵니다

---

## 보안 FAQ

**왜 `--remote-debugging-port` 가 필요한가?**

Antigravity 의 Agent 패널은 격리된 Chromium 프로세스에서 실행됩니다. VS Code 확장 API 는 그 안의 Run / Accept / Allow 버튼을 보거나 상호작용할 수 없습니다——등록된 명령이 없는 React UI 요소이기 때문입니다. localhost 포트(기본 9333)의 Chrome DevTools Protocol (CDP) 이 그것에 도달하는 유일한 방법입니다.

**안전한가?**

- **localhost 전용** — 포트가 `127.0.0.1` 에 바인딩되며 `0.0.0.0` 이 아닙니다. 외부 머신은 연결할 수 없습니다.
- **자동 승인 코어 제로 텔레메트리** — DOM 스캔, 버튼 매칭, 명령 필터링은 네트워크 호출을 하지 않습니다.
- **유일한 외향 트래픽**은 (a) 라이선스 검증, (b) Telegram Bot API(페어링한 경우만), (c) Swarm 모드 서명된 코어 페이로드 가져오기입니다. 세 가지 모두 기본적으로 꺼져 있습니다.
- **서명된 Pro 페이로드.** Swarm 코어 엔진은 Ed25519 서명되어 있고 Node worker 내에서 검증한 뒤 RAM 에서 컴파일됩니다——중간자가 악성 스캐너를 삽입할 수 없습니다.
- **표준 개발 워크플로** — `--remote-debugging-port` 는 VS Code 확장 개발자와 Electron 앱 디버깅에 사용되는 것과 동일한 플래그입니다.
- **바로 가기 패처는 범위가 제한됨** — 자동 수정은 타겟 경로에 "Antigravity" 가 포함된 `.lnk` 파일만 수정합니다.
- **Antigravity 파일 수정 없음** — 이 확장 기능은 외부 VS Code 확장으로 완전히 실행됩니다. 제거하면 흔적이 남지 않습니다.

**내 Telegram 채팅이 내 코드를 읽나요?**

여러분이 **명시적으로 요청한 것만**. `/peek` 은 활성 Agent 패널의 보이는 텍스트를 반환합니다. `/prompt` 는 여러분의 메시지를 보냅니다. 확장 기능은 코드, diff, 스크린샷, 텔레메트리를 Telegram 에 선제적으로 푸시하지 않습니다.

---

## 라이선스

MIT
