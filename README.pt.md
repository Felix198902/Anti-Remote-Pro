<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=pt"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**O piloto automático que prioriza a privacidade, resistente a banimentos e controlado por Telegram para o [Antigravity](https://antigravity.dev) — o assistente de codificação com IA do Google.**
**Uma conta Google, dispositivos ilimitados.**

### [🌐 Site Oficial &nbsp;·&nbsp; Baixe Agora →](https://antigravity.apiai.eu.cc/?lang=pt)

<sub>
  📖 <b>Leia em:</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <a href="./README.zh-CN.md">简体中文</a> &nbsp;·&nbsp;
  <a href="./README.zh-TW.md">繁體中文</a> &nbsp;·&nbsp;
  <a href="./README.ja.md">日本語</a> &nbsp;·&nbsp;
  <a href="./README.ko.md">한국어</a> &nbsp;·&nbsp;
  <a href="./README.es.md">Español</a> &nbsp;·&nbsp;
  <a href="./README.fr.md">Français</a> &nbsp;·&nbsp;
  <a href="./README.de.md">Deutsch</a> &nbsp;·&nbsp;
  <b>Português</b> &nbsp;·&nbsp;
  <a href="./README.ru.md">Русский</a> &nbsp;·&nbsp;
  <a href="./README.ar.md">العربية</a> &nbsp;·&nbsp;
  <a href="./README.hi.md">हिन्दी</a>
</sub>

</div>

Aceita automaticamente passos do Agent, comandos do terminal, edições de arquivos e prompts de permissão para que o Agent entregue seu trabalho sem precisar de cliques manuais — mantendo cada byte na sua máquina e permitindo que você pilote cada uma de suas máquinas pelo telefone.

> 💡 **Quer começar rápido?** O [site oficial](https://antigravity.apiai.eu.cc/?lang=pt) tem um guia completo, capturas de tela ao vivo, preços Pro e o último download `.vsix` — tudo em 12 idiomas.

---

## 🔥 Por que o Anti-Remote-Pro

### 🔒 1. Privacidade Absoluta — seu código nunca sai do seu laptop

- **Pipeline 100% local.** Toda a detecção de botões, varredura do DOM e filtragem de comandos rodam dentro do seu processo VS Code / Antigravity. Nenhum prompt, captura de tela ou diff sai jamais da máquina.
- **Porta de depuração apenas em localhost.** O CDP é vinculado estritamente a `127.0.0.1:9333`. Nenhum host externo na LAN, no Wi-Fi de uma cafeteria ou em uma rede de coworking pode alcançá-lo — verificado pelo binding do socket, não apenas por promessa.
- **Telemetria zero.** O núcleo de auto-aceitação não faz chamadas de análise, relatórios de crash, nem "estatísticas anônimas de uso". O único tráfego de saída vai para o Telegram (somente se você parear) e para o servidor de licenças (somente para verificar sua chave).
- **Anexação de target apenas por whitelist.** A camada CDP anexa-se **apenas** a targets `vscode-webview://` que correspondem ao painel do Agent. Recusa-se a anexar a outras abas, sub-agents do navegador, ou qualquer target Chromium não-Antigravity.
- **Payload do núcleo assinado.** O motor do núcleo Pro é obtido como um payload assinado com Ed25519, verificado dentro de um Node worker e compilado em RAM — nunca escrito em disco, nunca alterável por um homem-no-meio.
- **Nenhuma modificação do próprio Antigravity.** Não corrigimos, reempacotamos ou hookamos os binários do Antigravity. CDP puramente externo — desinstale e zero rastros permanecem.

### 📱 2. Controle Remoto por Telegram — pilote o Antigravity de qualquer lugar

Pareie sua IDE com um bot do Telegram uma vez, e seu telefone se torna um controle remoto completo para o Agent:

- **`/prompt <texto>`** — envie um novo prompt para a conversa ativa de qualquer canto do planeta. Reúne automaticamente as mensagens divididas de 4096 caracteres do Telegram.
- **`/peek [N]`** — leia a resposta mais recente do Agent diretamente no Telegram, sem precisar acordar seu laptop.
- **Envie uma foto com legenda** — anexa a captura ao prompt para depuração visual em movimento.
- **`/pause` & `/resume`** — alterne o kill-switch global pelo seu telefone. O lock de arquivo entre janelas garante que cada janela do Antigravity obedeça instantaneamente.
- **`/stop`** — interrompe a resposta atualmente sendo gerada.
- **Comandos assinados com HMAC.** Cada comando do Telegram é verificado com uma chave HMAC por dispositivo. Um chat do Telegram vazado *não* é suficiente para controlar sua IDE.
- **Eleição de mestre único.** Quando você tem 5 janelas do Antigravity abertas, apenas uma vence o lock mestre e processa comandos — sem envios duplicados, sem race conditions.

### 🛡️ 3. Estratégia Anti-Banimento Pioneira no Setor

A maioria dos auto-clickers tem contas marcadas porque martelam endpoints em uma cadência fixa e clicam enquanto o humano ainda está digitando. O Anti-Remote-Pro foi projetado de forma oposta:

- **Ritmo humano.** Polling ativo a 500 ms com **±20 % de jitter aleatório** + backoff exponencial (limitado a 30 s) em erros consecutivos. Sem intervalos mecanicamente perfeitos para serem fingerprinted.
- **Smart-sleep ocioso.** Sem sessão CDP ativa, o motor cai para um heartbeat de 5 s — pressão IPC praticamente zero quando você está ausente.
- **Janela de tolerância de 20 segundos com usuário ativo.** Se o usuário está digitando no chat, rolando o webview ou movendo o cursor do editor, **todos os auto-cliques são adiados**. O bot literalmente espera você parar, então nunca co-clica enquanto você lê.
- **Sem patching binário.** Os arquivos do Antigravity, settings.json, e o diretório de dados do usuário são somente leitura para esta extensão. Atualizações automáticas oficiais e verificações de integridade passam limpas porque nada é modificado.
- **CDP apenas em loopback.** Sem listener TCP, sem encaminhamento remoto. A flag `--remote-debugging-port=9333` é uma flag de depuração padrão do Electron — a mesma que a Microsoft, Google e JetBrains usam internamente.
- **Firewall de comandos rigoroso.** Lista de bloqueio integrada + lista branca estrita opcional + 50+ **Safety Presets** curados (rm -rf, force-push, drop database, fork bombs, limpadores de disco, exclusões de registro…). O bot *recusará* executar um comando destrutivo mesmo se o Agent insistir.
- **Click-once-per-session para botões expandir.** Elimina o loop de "reabertura infinita" que pode acionar heurísticas anti-abuso.
- **Cessão instantânea ao sub-agent oficial do Browser.** Quando a ferramenta de navegador do AG ativa a porta 9222, nosso worker se desanexa e sai do caminho — sem colisão de portas, sem assinatura de dupla anexação.

> Efeito combinado: do ponto de vista do backend do Agent, você parece um usuário humano ligeiramente mais rápido que a média, impecavelmente educado.

### 🌍 4. Multi-idioma — 12 idiomas, bilhões de usuários cobertos

O Anti-Remote-Pro inclui traduções completas da UI (comandos, configurações, dashboard, notificações, respostas do Telegram). Escolha em um dropdown no dashboard, ou deixe-o detectar automaticamente o idioma da sua IDE.

| # | Idioma | Nome nativo | Regiões principais |
|---|---|---|---|
| 1 | Inglês | English | 🇺🇸 EUA · 🇬🇧 Reino Unido · 🇨🇦 Canadá · 🇦🇺 Austrália · 🇮🇪 Irlanda · 🇳🇿 Nova Zelândia · 🇿🇦 África do Sul · 🇸🇬 Singapura · 🇮🇳 Índia (TI) |
| 2 | Chinês Simplificado | 简体中文 | 🇨🇳 China continental · 🇸🇬 Singapura · 🇲🇾 Malásia |
| 3 | Chinês Tradicional | 繁體中文 | 🇹🇼 Taiwan · 🇭🇰 Hong Kong · 🇲🇴 Macau |
| 4 | Espanhol | Español | 🇪🇸 Espanha · 🇲🇽 México · 🇦🇷 Argentina · 🇨🇴 Colômbia · 🇨🇱 Chile · 🇵🇪 Peru · 🇻🇪 Venezuela · +14 outros |
| 5 | Francês | Français | 🇫🇷 França · 🇨🇦 Canadá (Quebec) · 🇧🇪 Bélgica · 🇨🇭 Suíça · 🇱🇺 Luxemburgo · 🇲🇨 Mônaco · grande parte da África Ocidental e Central |
| 6 | Hindi | हिन्दी | 🇮🇳 Índia · 🇫🇯 Fiji |
| 7 | Português (BR) | Português | 🇧🇷 Brasil · 🇵🇹 Portugal · 🇦🇴 Angola · 🇲🇿 Moçambique |
| 8 | Russo | Русский | 🇷🇺 Rússia · 🇧🇾 Bielorrússia · 🇰🇿 Cazaquistão · 🇰🇬 Quirguistão · 🇺🇿 Uzbequistão · 🇺🇦 Ucrânia |
| 9 | Árabe | العربية (RTL) | 🇸🇦 Arábia Saudita · 🇦🇪 EAU · 🇪🇬 Egito · 🇶🇦 Catar · 🇰🇼 Kuwait · 🇧🇭 Bahrein · 🇴🇲 Omã · 🇯🇴 Jordânia · 🇲🇦 Marrocos · 🇩🇿 Argélia · 🇹🇳 Tunísia · 🇮🇶 Iraque · +10 outros |
| 10 | Japonês | 日本語 | 🇯🇵 Japão |
| 11 | Alemão | Deutsch | 🇩🇪 Alemanha · 🇦🇹 Áustria · 🇨🇭 Suíça · 🇱🇮 Liechtenstein · 🇱🇺 Luxemburgo |
| 12 | Coreano | 한국어 | 🇰🇷 Coreia do Sul |

- **Detecção automática** segue `vscode.env.language` — a extensão serve sua locale imediatamente no primeiro lançamento.
- **Override manual** pelo dropdown de idioma do Dashboard (persiste entre recarregamentos).
- **Compatível com RTL** — a UI árabe inverte a direção do layout automaticamente (`dir="rtl"`).
- **Sobreposições de palavra-chave personalizadas** — `autoAcceptV2.customButtonTexts` permite adicionar rótulos de botão localizados para qualquer string de UI que ainda não traduzimos (ex.: `["toujours autoriser", "siempre permitir"]`).

### 🔗 5. Sincronização Multi-Dispositivo com Login Google — uma conta, todas as suas máquinas

**Faça login uma vez com Google** e o Anti-Remote-Pro segue você em todo lugar — desktop, laptop, PC de casa, workstation do trabalho, Windows, macOS, Linux.

- **Google OAuth com um clique.** `Anti-Remote-Pro: Login with Google` abre seu navegador, completa o OAuth padrão do Google e redireciona de volta para a IDE através de um manipulador de URI seguro `vscode://Pro.antigravity-autoaccept/auth`. Sem copia-e-cola de chave de licença, sem dança de e-mails.
- **A licença Pro sincroniza automaticamente entre dispositivos.** Sua assinatura é vinculada à sua conta Google, não a uma única máquina. Instale no dispositivo nº 2, nº 3, nº 10 — faça login e o Pro se desbloqueia instantaneamente. O servidor de licenças verifica cada `machineId` contra sua conta a cada atualização.
- **Execute em um número ilimitado de dispositivos simultaneamente.** Laptop do trabalho, desktop de casa, máquina de dev remota, uma VM por cliente — todos podem rodar o Anti-Remote-Pro em paralelo sob a mesma conta.
- **Frotas paralelas.** Cada dispositivo opera independentemente com seu próprio CDP / Swarm / firewall de comandos, então você pode ter um laptop processando a Conversa A enquanto seu desktop roda a Conversa B — nenhum rouba o foco do outro.
- **Pareamento Telegram por dispositivo.** Cada máquina pareia separadamente com o bot do Telegram e recebe sua própria chave HMAC. Você pode nomeá-las no fluxo de pareamento (ex.: "MacBook", "WorkPC") e endereçá-las individualmente do mesmo chat do Telegram.
- **Coordenação entre janelas na mesma máquina.** Quando você tem múltiplas janelas do Antigravity abertas em um dispositivo, um protocolo de lock de arquivo mantém o estado de pause/resume sincronizado em menos de um segundo — sem cliques duplicados, sem briga.
- **Revogação instantânea.** `Anti-Remote-Pro: Logout` apaga o token local e diz ao servidor para invalidar aquele dispositivo. Perdeu um laptop? Faça logout de outra máquina + `Refresh Pro Status` e a máquina antiga fica no escuro.
- **Refresh Pro Status.** Mudou de plano ou renovou sua assinatura? Um comando re-puxa os direitos mais recentes — sem reinstalação, sem reinício.

> Na prática: faça login uma vez nos seus 3 computadores, pareie cada um com o mesmo bot do Telegram, e seu telefone se torna um controle central para toda sua frota de codificação.

---

## ⚡ Capacidades Centrais em Resumo

- **Auto-clique** Run / Accept / Always Allow / Allow this conversation / Continue / Retry pelo painel do Agent — consciente de prioridade, então `Run` sempre vence sobre `Accept`.
- **Auto-aceitar edições de arquivo** com um interruptor — desligue a qualquer momento para revisar diffs manualmente.
- **Firewall de comandos** — modo de bloqueio por padrões ou whitelist estrita, ambos com correspondência por limite de palavra.
- **Safety presets** — importação com um clique de 50+ padrões de comandos destrutivos (limpadores de filesystem, formatadores de disco, force-push, DB drops, fork bombs).
- **Modo Swarm (Pro)** — rotaciona automaticamente pelas conversas pendentes do Agent Manager e as executa sem intervenção em segundo plano.
- **Telegram Remote (Pro)** — controle remoto completo da IDE: `/prompt`, `/peek`, prompts com foto, `/pause`, `/resume`, `/stop`, com auth HMAC.
- **Login Google + sincronização multi-dispositivo (Pro)** — uma conta Google, dispositivos ilimitados; callback OAuth via manipulador de URI `vscode://`; verificação de licença por dispositivo.
- **Pause entre janelas** — pausar em uma janela do Antigravity transmite via lock de arquivo a todas as outras janelas em <1 s.
- **Log de atividades + Dashboard** — veja cada botão clicado, cada sessão CDP, cada comando do Telegram ao vivo.
- **Dump de diagnóstico** — copia um payload de depuração estruturado para a área de transferência para suporte em uma mensagem.
- **Atalho Auto-Fix** — patcher de `.lnk` do Windows (Desktop / Menu Iniciar / Barra de tarefas) para a flag `--remote-debugging-port`.
- **Auto-cura por heartbeat** — MutationObservers mortos (apagados por navegação do webview / hot-reload) são detectados e re-injetados automaticamente a cada 10 s.

---

## O que faz

Quando o Agent do Antigravity propõe edições de arquivo, comandos de terminal, ou pede permissões de ferramenta, esta extensão os auto-aceita para que você não precise clicar em cada botão manualmente.

**Duas estratégias, zero interferência:**

| Estratégia | O que ela manipula | Como |
|---|---|---|
| **VS Code Commands** (500 ms + jitter) | Passos do Agent, comandos de terminal | Chama os comandos nativos de aceitação do Antigravity |
| **CDP + MutationObserver** (orientado a eventos) | Run, Accept, Always Allow, Continue, Retry | Script injetado uma vez, reage instantaneamente a mudanças no DOM |

---

## Configuração

### 1. Ativar Modo de Depuração (Obrigatório)

A extensão precisa do Chrome DevTools Protocol para clicar em botões de permissão. Inicie o Antigravity com:

```
--remote-debugging-port=9333
```

> **Por que a porta 9333?** O Browser Control integrado do Antigravity (botão Chrome na barra de ferramentas) usa a porta 9222 por padrão. Usar a mesma porta causa um conflito `EADDRINUSE` no macOS/Linux. A porta 9333 evita isso completamente.

<details>
<summary><b>🪟 Windows</b></summary>

**Automático:** No primeiro lançamento, a extensão detecta se a porta está fechada e mostra **"Auto-Fix Shortcut"** — clique para corrigir automaticamente seu atalho `.lnk`.

**Manual:** Clique com o botão direito no atalho do Antigravity → Propriedades → adicione ao Destino:
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**Opção 1 — App Automator (recomendado):**
1. Abra o **Automator** → Novo Documento → **Aplicativo**
2. Procure por **"Executar Script de Shell"** na biblioteca
3. Cole: `open -a "Antigravity" --args --remote-debugging-port=9333`
4. Salve como "AntiGravity Launcher" no Desktop ou em Aplicativos

**Opção 2 — Alias do terminal** (adicione ao `~/.zshrc`):
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **Nota:** O nome do app deve corresponder exatamente. Verifique com `ls /Applications/ | grep -i anti`

**Opção 3 — Binário Electron direto** (se `open -a` não passar args corretamente):
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**Opção 1 — Edite o arquivo `.desktop`:**
```bash
# Encontre-o:
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# Edite a linha Exec:
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**Opção 2 — Alias do shell** (adicione ao `~/.bashrc` ou `~/.zshrc`):
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**Opção 3 — Script wrapper:**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. Instalar a Extensão

**Do VSIX (recomendado):**
1. Obtenha o pacote `.vsix` mais recente
2. No Antigravity: `Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. Selecione o arquivo baixado
4. Reload Window

**Manual:**
1. Copie o diretório `src/`, `package.json`, e `package-lock.json` para:
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. Execute `npm install` nesse diretório (instala a dependência `ws`)
3. Reload Window

---

## Uso

### Comandos básicos

- **Alternar:** Clique em `⚡ Auto: ON` / `✕ Auto: OFF` na barra de status
- **Ou:** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **Dashboard:** Clique no ícone do dashboard na barra de status para ver status do CDP, sessões ativas, log de atividades e seletor de idioma
- **Logs:** Painel Output → `Anti-Remote-Pro`

### Comandos Pro

Todos os recursos Pro são acessíveis pela Paleta de Comandos (`Ctrl+Shift+P`):

| Comando | O que faz |
|---|---|
| `Anti-Remote-Pro: Login with Google` | Faça login para sincronizar sua licença Pro entre dispositivos |
| `Anti-Remote-Pro: Logout` | Limpa a licença local + conta logada |
| `Anti-Remote-Pro: Refresh Pro Status` | Força uma re-verificação da licença contra o servidor |
| `Anti-Remote-Pro: Connect Telegram Bot` | Inicia o fluxo de pareamento — abre o bot no Telegram, toque em **Start** para vincular esta máquina |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | Revoga a chave HMAC desta máquina |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | Força o re-download do payload do núcleo assinado |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | Kill-switch global (também vinculado a `Ctrl+Shift+S`) |
| `Anti-Remote-Pro: Fix Missing Conversations` | Re-semeia o índice de conversas do Swarm se a sidebar parecer fora de sincronia |

> **Dica:** `Ctrl+Shift+S` é a forma mais rápida de pausar/retomar Swarm + auto-aceitação quando um colega humano entra na sua sessão.

---

## Workflow Multi-Agent

### ⚠️ Limitação do Agent Manager (sem Modo Swarm)

O Agent Manager do Antigravity usa um **único webview compartilhado** — apenas o DOM da conversa ativa é renderizado. Conversas em segundo plano são completamente desmontadas. Sem o Modo Swarm, tanto a API VS Code Commands quanto o CDP só conseguem alcançar a conversa visível atualmente.

### ✅ Solução: Modo Swarm (Pro)

O Modo Swarm resolve isso rotacionando o foco por todas as conversas pendentes, permitindo que dezenas de agentes em segundo plano rodem sem intervenção:

- Escaneia cada conversa na sidebar e escolhe a que tem trabalho pendente.
- Respeita sua configuração de idle-seconds para nunca roubar o foco enquanto você digita.
- Consciente entre janelas: pausar qualquer janela pausa todas via broadcast de lock de arquivo.
- Seguro por padrão: payload do núcleo assinado, firewall de comandos ainda se aplica.

### Alternativa: Duplicar Workspace (gratuito)

Se você não tem licença Pro, ainda pode rodar 2–3 agents em paralelo:

1. Clique em **File → Duplicate Workspace**
2. Isso abre uma segunda janela do Antigravity conectada ao mesmo projeto
3. Inicie um chat na Janela 1 e outro chat na Janela 2
4. Cada janela tem seu próprio webview — a extensão auto-clica botões em **ambas as janelas simultaneamente**

---

## Configurações

| Configuração | Padrão | Escopo | Descrição |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | Intervalo base de polling em ms (±20 % de jitter aplicado automaticamente) |
| `autoAcceptV2.customButtonTexts` | `[]` | application | Textos extras de botão para i18n ou prompts personalizados (ex.: `["toujours autoriser"]`) |
| `autoAcceptV2.cdpPort` | `9333` | machine | Porta CDP (padrão evita conflito com AG Browser Control em 9222) |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | Auto-aceitar mudanças de edição de arquivo (desative para revisar diffs manualmente) |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Auto-clicar Retry / Continue quando o Agent atinge erros ou limites de invocação |
| `autoAcceptV2.blockedCommands` | `[]` | application | Comandos para NUNCA auto-executar (ex.: `rm`, `git push`, `npm publish`) |
| `autoAcceptV2.allowedCommands` | `[]` | application | Se definido, APENAS estes comandos serão auto-executados (modo whitelist) |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Chave de licença Pro — desbloqueia Modo Swarm + Telegram Remote |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Segundos de inatividade do usuário antes do Swarm navegar para um chat pendente (3–60) |

> **Dica:** As configurações são recarregadas a quente — mudanças entram em vigor imediatamente sem reiniciar.

---

## Como Funciona

### CDP Persistente + MutationObserver

A extensão mantém uma **conexão WebSocket persistente em nível de navegador** com o DevTools Protocol do Chromium. Em vez de fazer polling a cada 1,5 s, ela injeta um payload **MutationObserver** uma vez por target. O observer reage instantaneamente quando o React monta novos elementos de botão, com throttle de leading-edge de 100 ms para evitar picos de CPU durante saídas em streaming. A extensão usa um **filtro de target apenas por whitelist** — ela só anexa a targets `vscode-webview://` e cede automaticamente a porta CDP quando o sub-agent do navegador AG é detectado, prevenindo conflitos de ArrayBuffer.

### Scanner de DOM em Passada Única

O scanner de botões percorre a árvore DOM **exatamente uma vez** por ciclo, verificando todas as palavras-chave simultaneamente contra cada nó. Isso é O(D) em vez de O(N×D), que poderia causar congelamentos de UI com muitas palavras-chave. A correspondência consciente de prioridade garante que `Run` sempre vence `Accept`, que sempre vence `Allow`, independentemente da ordem do DOM.

### Guarda de Webview

O painel do Agent do Antigravity roda em um processo Chromium isolado (OOPIF). O script injetado usa uma verificação adiada `isAgentPanel()` dentro de `scanAndClick()` — verificando a existência de `.react-app-container` dinamicamente em cada scan em vez de no momento da injeção. Isso evita uma race condition onde o DOM está sem hidratação em `targetCreated`.

### Auto-Cura por Heartbeat

A conexão CDP valida sessões existentes a cada ciclo de heartbeat (10 s). Se o MutationObserver de uma sessão está morto (contexto de execução apagado por navegação do webview ou hot-reload do React), ela re-injeta o observer automaticamente — sem necessidade de reconexão. Sessões inalcançáveis 3 vezes consecutivas são desanexadas e podadas limpamente.

### Prevenção de Loop do Botão Expandir

Botões do tipo expandir (ex.: "Expand" da prévia do navegador) usam uma regra de **clique-uma-vez-por-sessão**: uma vez clicados, são suprimidos permanentemente para aquela sessão CDP via um Set `expandedOnce`. Isso previne o loop infinito de reabertura do overlay onde fechar o painel expandido dispara um re-clique. O estado é resetado naturalmente quando uma nova conversa do Agent começa.

### Detecção de Botões

Dentro do painel do Agent, um `TreeWalker` busca botões por conteúdo de texto usando correspondência `startsWith` com **verificações de limite de palavra** para prevenir falsos positivos (ex.: `accept-test.js` não corresponderá a `accept`):

| Prioridade | Texto | Corresponde a |
|---|---|---|
| 1 | `run` | botão "Run Alt+d" (não o dropdown "Always run ^") |
| 2 | `accept` | botão Accept |
| 3 | `always allow` | prompts de permissão |
| 4 | `allow this conversation` | permissões com escopo de conversa |
| 5 | `allow` | prompts de permissão |
| 6 | `retry` | prompts Retry |
| 7 | `continue` | retomada após limite de invocação do Agent |

### Filtragem de Comandos

As listas de comandos bloqueados e permitidos usam **correspondência por limite de palavra** contra o bloco de código acima de um botão Run. Por exemplo, bloquear `rm` bloqueará `rm -rf /tmp` mas NÃO `yarn format` ou `npm run build`.

---

## Comandos Bloqueados Recomendados

O dashboard inclui um botão **Load Safety Presets** que importa em massa 50+ padrões de comandos destrutivos cobrindo limpadores de filesystem, formatadores de disco, drops de banco de dados, force-pushes e fork bombs.

**Um clique:** Abra o Dashboard → clique em **Load Recommended Safety Presets**.

**Cole em massa:** As entradas de bloqueado / permitido suportam valores **separados por vírgula** — cole uma lista e pressione Enter.

<details>
<summary><b>📋 Manual: Copiar para settings.json</b></summary>

Adicione isto ao seu `settings.json` (`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`):

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

### Auto-Fix do CDP

Na ativação, a extensão verifica se a porta 9333 está aberta (com 9222 como fallback). Se não, mostra uma notificação com:
- **Auto-Fix Shortcut (Windows)** — corrige atalhos `.lnk` no Desktop, Menu Iniciar **e Barra de Tarefas**

---

## Solução de Problemas

### Bot para de funcionar após algumas horas

**Causa:** Ou (a) o Antigravity reinicia silenciosamente seu processo Electron (auto-atualizações, pressão de memória ou crash do extension host) e o novo processo não tem `--remote-debugging-port=9333`, ou (b) o contexto de execução do webview foi apagado por uma navegação / hot-reload.

**Correção:** A lógica de auto-cura por heartbeat detecta e re-injeta observers mortos automaticamente. Se ainda não funcionar, feche **todas** as janelas do Antigravity completamente, e reabra do seu atalho corrigido.

### Bot está ON mas não clica em nada

1. **Alternar OFF → ON** — clique duas vezes no ícone da barra de status para reiniciar o polling
2. **Verifique a porta de depuração** — visite `http://127.0.0.1:9333/json/list` em um navegador. Se ela recusar, a porta de depuração está morta (veja acima)
3. **Verifique os logs do Output** — `Ctrl+Shift+U` → dropdown → `Anti-Remote-Pro`. Procure por linhas `[CDP] ✓ Thread`. Se não houver nenhuma, o CDP não consegue encontrar o painel do Agent

### Ícone da barra de status não aparece após instalação

1. Execute `Ctrl+Shift+P` → `Reload Window`
2. Verifique se o VSIX foi construído **com** dependências (o pacote `ws` deve estar incluído)

---

## Segurança

Comandos deliberadamente **excluídos** para prevenir danos:
- `notification.acceptPrimaryAction` — auto-clicaria em diálogos destrutivos
- `chatEditing.acceptAllFiles` — causa alternância do Outline da sidebar
- Todos os comandos de merge / conflito git — poderiam silenciosamente escolher o lado errado
- Todos os comandos de autocompletar / sugestão — corromperiam sua digitação

---

## FAQ de Segurança

**Por que isso precisa de `--remote-debugging-port`?**

O painel do Agent do Antigravity roda em um processo Chromium isolado. A API de Extensões do VS Code não consegue ver ou interagir com os botões Run / Accept / Allow lá dentro — eles são elementos de UI React sem comandos registrados. O Chrome DevTools Protocol (CDP) em uma porta localhost (padrão 9333) é a única maneira de alcançá-los.

**É seguro?**

- **Apenas localhost** — a porta vincula-se a `127.0.0.1`, não a `0.0.0.0`. Nenhuma máquina externa pode se conectar.
- **Telemetria zero no núcleo de auto-aceitação** — varredura do DOM, correspondência de botões e filtragem de comandos nunca fazem chamadas de rede.
- **O único tráfego de saída** é (a) verificação de licença, (b) API do Bot do Telegram — e somente se você parear, e (c) busca do payload do núcleo assinado para o Modo Swarm. Os três estão desligados por padrão.
- **Payload Pro assinado.** O motor do núcleo Swarm é assinado com Ed25519 e verificado dentro de um Node worker antes de ser compilado em RAM — um homem-no-meio não pode infiltrar um scanner malicioso.
- **Workflow padrão de dev** — `--remote-debugging-port` é a mesma flag usada por desenvolvedores de extensões VS Code e depuração de apps Electron.
- **O patcher de atalhos tem escopo** — o auto-fix só modifica arquivos `.lnk` cujo caminho de destino contém "Antigravity".
- **Nenhum arquivo do Antigravity modificado** — esta extensão roda inteiramente como uma extensão VS Code externa. Desinstale e cada rastro desaparece.

**Meu chat do Telegram lerá meu código?**

Apenas o que *você* explicitamente pedir. `/peek` retorna o texto visível do painel do Agent ativo; `/prompt` envia sua mensagem para dentro. A extensão nunca envia proativamente código, diffs, capturas ou telemetria para o Telegram.

---

## Licença

MIT
