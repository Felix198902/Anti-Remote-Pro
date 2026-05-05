<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=es"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**El piloto automático con privacidad ante todo, resistente a baneos y controlable por Telegram para [Antigravity](https://antigravity.dev) — el asistente de codificación con IA de Google.**
**Una cuenta de Google, dispositivos ilimitados.**

### [🌐 Sitio Oficial &nbsp;·&nbsp; Descarga Ya →](https://antigravity.apiai.eu.cc/?lang=es)

<sub>
  📖 <b>Lee esto en:</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <a href="./README.zh-CN.md">简体中文</a> &nbsp;·&nbsp;
  <a href="./README.zh-TW.md">繁體中文</a> &nbsp;·&nbsp;
  <a href="./README.ja.md">日本語</a> &nbsp;·&nbsp;
  <a href="./README.ko.md">한국어</a> &nbsp;·&nbsp;
  <b>Español</b> &nbsp;·&nbsp;
  <a href="./README.fr.md">Français</a> &nbsp;·&nbsp;
  <a href="./README.de.md">Deutsch</a> &nbsp;·&nbsp;
  <a href="./README.pt.md">Português</a> &nbsp;·&nbsp;
  <a href="./README.ru.md">Русский</a> &nbsp;·&nbsp;
  <a href="./README.ar.md">العربية</a> &nbsp;·&nbsp;
  <a href="./README.hi.md">हिन्दी</a>
</sub>

</div>

Acepta automáticamente los pasos del Agent, los comandos de terminal, las ediciones de archivos y las solicitudes de permisos para que el Agent complete tu trabajo sin intervención manual, manteniendo cada byte en tu máquina y permitiéndote pilotar todas tus máquinas desde el teléfono.

> 💡 **¿Quieres empezar rápido?** El [sitio oficial](https://antigravity.apiai.eu.cc/?lang=es) incluye una guía completa, capturas de pantalla en vivo, precios Pro y la última descarga `.vsix` — todo en 12 idiomas.

---

## 🔥 Por qué Anti-Remote-Pro

### 🔒 1. Privacidad Absoluta — tu código nunca sale de tu portátil

- **Pipeline 100% local.** Toda la detección de botones, el escaneo del DOM y el filtrado de comandos se ejecutan dentro de tu proceso de VS Code / Antigravity. Ningún prompt, captura de pantalla o diff abandona jamás la máquina.
- **Puerto de depuración solo en localhost.** El CDP se vincula estrictamente a `127.0.0.1:9333`. Ningún host externo en la LAN, en el Wi-Fi de una cafetería o en una red de coworking puede alcanzarlo — verificado por el binding del socket, no solo por una promesa.
- **Cero telemetría.** El núcleo de auto-aceptación no realiza llamadas de análisis, informes de fallos ni "estadísticas anónimas de uso". El único tráfico saliente es hacia Telegram (solo si lo emparejas) y al servidor de licencias (solo para verificar tu clave).
- **Conexión a targets solo por whitelist.** La capa CDP se conecta **únicamente** a targets `vscode-webview://` que coincidan con el panel del Agent. Se niega a conectarse a tus otras pestañas, sub-agentes del navegador o cualquier target de Chromium que no sea de Antigravity.
- **Payload del núcleo firmado.** El motor del núcleo Pro se obtiene como un payload firmado con Ed25519, se verifica dentro de un worker de Node y se compila en RAM — nunca se escribe en disco, nunca es manipulable por un hombre-en-el-medio.
- **Sin modificación del propio Antigravity.** No parchamos, reempaquetamos ni hookeamos los binarios de Antigravity. CDP puramente externo — desinstalas y no queda rastro.

### 📱 2. Control Remoto por Telegram — maneja Antigravity desde cualquier lugar

Empareja tu IDE con un bot de Telegram una vez, y tu teléfono se convierte en un mando a distancia completo para el Agent:

- **`/prompt <texto>`** — envía un nuevo prompt a la conversación activa desde cualquier lugar del planeta. Une automáticamente los mensajes de 4096 caracteres divididos por Telegram.
- **`/peek [N]`** — lee la última respuesta del Agent directamente en Telegram, sin necesidad de despertar tu portátil.
- **Envía una foto con título** — adjunta la captura al prompt para depuración visual mientras estás en movimiento.
- **`/pause` y `/resume`** — activa el interruptor de apagado global desde tu teléfono. El bloqueo de archivos entre ventanas garantiza que cada ventana de Antigravity obedezca al instante.
- **`/stop`** — detiene la respuesta que se está generando actualmente.
- **Comandos firmados con HMAC.** Cada comando de Telegram se verifica con una clave HMAC por dispositivo. Un chat de Telegram filtrado *no* es suficiente para controlar tu IDE.
- **Elección de maestro único.** Cuando tienes 5 ventanas de Antigravity abiertas, solo una gana el bloqueo maestro y procesa comandos — sin envíos duplicados, sin condiciones de carrera.

### 🛡️ 3. Estrategia Anti-Baneo Pionera en la Industria

La mayoría de los auto-clickers se ganan el marcado de cuentas porque golpean los endpoints a un ritmo fijo y hacen clic mientras el humano aún está escribiendo. Anti-Remote-Pro está diseñado de la forma opuesta:

- **Ritmo humano.** Polling activo a 500 ms con **±20% de jitter aleatorio** + backoff exponencial (limitado a 30 s) en errores consecutivos. Sin intervalos mecánicamente perfectos que puedan detectarse como huella.
- **Smart-sleep en inactividad.** Sin sesión CDP activa, el motor cae a un heartbeat de 5 s — presión IPC prácticamente cero cuando estás ausente.
- **Ventana de gracia de 20 segundos con el usuario activo.** Si el usuario está escribiendo en el chat, desplazándose por el webview o moviendo el cursor del editor, **todos los auto-clicks se posponen**. El bot literalmente espera a que pares, así que nunca co-hace clic mientras lees.
- **Sin parcheo de binarios.** Los archivos de Antigravity, settings.json y el directorio de datos de usuario son solo lectura para esta extensión. Las actualizaciones automáticas oficiales y las verificaciones de integridad pasan limpiamente porque nada se modifica.
- **CDP solo en loopback.** Sin listener TCP, sin reenvío remoto. El flag `--remote-debugging-port=9333` es un flag estándar de depuración de Electron — el mismo que usan Microsoft, Google y JetBrains internamente.
- **Firewall de comandos duro.** Lista negra integrada + lista blanca estricta opcional + 50+ **Safety Presets** curados (rm -rf, force-push, drop database, fork bombs, limpiadores de disco, eliminaciones de registro…). El bot *se negará* a ejecutar un comando destructivo incluso si el Agent insiste.
- **Clic-una-vez-por-sesión para los botones de expandir.** Elimina el bucle de "reapertura infinita" que corre el riesgo de activar heurísticas antiabuso.
- **Cesión instantánea al sub-agente oficial del navegador.** Cuando la herramienta del navegador de AG activa el puerto 9222, nuestro worker se desconecta y sale del camino — sin colisión de puertos, sin firma de doble conexión.

> El efecto combinado: desde la perspectiva del backend del Agent, pareces un usuario humano ligeramente más rápido que la media, impecablemente cortés.

### 🌍 4. Multi-Idioma — 12 idiomas, miles de millones de usuarios cubiertos

Anti-Remote-Pro trae traducciones completas de la UI (comandos, ajustes, panel, notificaciones, respuestas de Telegram). Elige del desplegable en el panel, o deja que detecte automáticamente el idioma de tu IDE.

| # | Idioma | Nombre nativo | Regiones principales |
|---|---|---|---|
| 1 | Inglés | English | 🇺🇸 EE. UU. · 🇬🇧 Reino Unido · 🇨🇦 Canadá · 🇦🇺 Australia · 🇮🇪 Irlanda · 🇳🇿 Nueva Zelanda · 🇿🇦 Sudáfrica · 🇸🇬 Singapur · 🇮🇳 India (TI) |
| 2 | Chino Simplificado | 简体中文 | 🇨🇳 China continental · 🇸🇬 Singapur · 🇲🇾 Malasia |
| 3 | Chino Tradicional | 繁體中文 | 🇹🇼 Taiwán · 🇭🇰 Hong Kong · 🇲🇴 Macao |
| 4 | Español | Español | 🇪🇸 España · 🇲🇽 México · 🇦🇷 Argentina · 🇨🇴 Colombia · 🇨🇱 Chile · 🇵🇪 Perú · 🇻🇪 Venezuela · +14 más |
| 5 | Francés | Français | 🇫🇷 Francia · 🇨🇦 Canadá (Quebec) · 🇧🇪 Bélgica · 🇨🇭 Suiza · 🇱🇺 Luxemburgo · 🇲🇨 Mónaco · gran parte de África Occidental y Central |
| 6 | Hindi | हिन्दी | 🇮🇳 India · 🇫🇯 Fiyi |
| 7 | Portugués (BR) | Português | 🇧🇷 Brasil · 🇵🇹 Portugal · 🇦🇴 Angola · 🇲🇿 Mozambique |
| 8 | Ruso | Русский | 🇷🇺 Rusia · 🇧🇾 Bielorrusia · 🇰🇿 Kazajistán · 🇰🇬 Kirguistán · 🇺🇿 Uzbekistán · 🇺🇦 Ucrania |
| 9 | Árabe | العربية (RTL) | 🇸🇦 Arabia Saudí · 🇦🇪 EAU · 🇪🇬 Egipto · 🇶🇦 Qatar · 🇰🇼 Kuwait · 🇧🇭 Baréin · 🇴🇲 Omán · 🇯🇴 Jordania · 🇲🇦 Marruecos · 🇩🇿 Argelia · 🇹🇳 Túnez · 🇮🇶 Irak · +10 más |
| 10 | Japonés | 日本語 | 🇯🇵 Japón |
| 11 | Alemán | Deutsch | 🇩🇪 Alemania · 🇦🇹 Austria · 🇨🇭 Suiza · 🇱🇮 Liechtenstein · 🇱🇺 Luxemburgo |
| 12 | Coreano | 한국어 | 🇰🇷 Corea del Sur |

- **Detección automática** sigue `vscode.env.language` — la extensión sirve tu locale inmediatamente en el primer arranque.
- **Override manual** mediante el desplegable de idioma del Panel (persiste entre recargas).
- **Consciente de RTL** — la UI árabe voltea la dirección del diseño automáticamente (`dir="rtl"`).
- **Sobreescrituras de palabras clave personalizadas** — `autoAcceptV2.customButtonTexts` te permite añadir etiquetas de botón localizadas para cualquier cadena de UI que aún no hayamos traducido (p. ej. `["toujours autoriser", "siempre permitir"]`).

### 🔗 5. Sincronización Multi-Dispositivo con Inicio de Sesión de Google — una cuenta, todas tus máquinas

**Inicia sesión una vez con Google** y Anti-Remote-Pro te sigue a todas partes — escritorio, portátil, PC de casa, estación de trabajo del trabajo, Windows, macOS, Linux.

- **Google OAuth con un clic.** `Anti-Remote-Pro: Login with Google` abre tu navegador, completa el OAuth estándar de Google y redirige de vuelta al IDE mediante un manejador de URI seguro `vscode://Pro.antigravity-autoaccept/auth`. Sin copiar/pegar claves de licencia, sin baile de correos.
- **La licencia Pro se sincroniza automáticamente entre dispositivos.** Tu suscripción está vinculada a tu cuenta de Google, no a una máquina individual. Instala en el dispositivo #2, #3, #10 — inicia sesión y Pro se desbloquea al instante. El servidor de licencias verifica cada `machineId` contra tu cuenta en cada actualización.
- **Ejecuta en un número ilimitado de dispositivos simultáneamente.** Portátil del trabajo, escritorio de casa, caja de desarrollo remota, una VM por cliente — todos pueden ejecutar Anti-Remote-Pro en paralelo bajo la misma cuenta.
- **Flotas paralelas.** Cada dispositivo opera independientemente con su propio CDP / Swarm / firewall de comandos, así que puedes tener un portátil procesando la Conversación A mientras tu escritorio ejecuta la Conversación B — ninguno roba el foco al otro.
- **Emparejamiento de Telegram por dispositivo.** Cada máquina se empareja con el bot de Telegram por separado y obtiene su propia clave HMAC. Puedes nombrarlas en el flujo de emparejamiento (p. ej. "MacBook", "WorkPC") y direccionarlas individualmente desde el mismo chat de Telegram.
- **Coordinación entre ventanas en la misma máquina.** Cuando tienes múltiples ventanas de Antigravity abiertas en un dispositivo, un protocolo de bloqueo de archivos mantiene su estado de pausa/reanudación sincronizado en menos de un segundo — sin clics duplicados, sin peleas.
- **Revocación instantánea.** `Anti-Remote-Pro: Logout` borra el token local y le dice al servidor que invalide ese dispositivo. ¿Perdiste un portátil? Cierra sesión desde otra máquina + `Refresh Pro Status` y la máquina antigua queda a oscuras.
- **Refresh Pro Status.** ¿Cambiaste de plan o renovaste tu suscripción? Un comando vuelve a tirar los últimos derechos — sin reinstalación, sin reinicio.

> En la práctica: inicia sesión una vez en tus 3 ordenadores, empareja cada uno al mismo bot de Telegram, y tu teléfono se convierte en un mando central para toda tu flota de codificación.

---

## ⚡ Capacidades Centrales de un Vistazo

- **Auto-clic** Run / Accept / Always Allow / Allow this conversation / Continue / Retry en todo el panel del Agent — con prioridad, así que `Run` siempre gana a `Accept`.
- **Auto-aceptar ediciones de archivos** con un interruptor — apágalo en cualquier momento para revisar diffs manualmente.
- **Firewall de comandos** — modo bloqueo de patrones o lista blanca estricta, ambos con coincidencia por límite de palabra.
- **Safety presets** — importación con un clic de 50+ patrones de comandos destructivos (limpiadores de sistema de archivos, formateadores de disco, force-push, drops de BD, fork bombs).
- **Modo Swarm (Pro)** — rota automáticamente por las conversaciones pendientes del Agent Manager y las ejecuta sin intervención en segundo plano.
- **Telegram Remote (Pro)** — control remoto completo del IDE: `/prompt`, `/peek`, prompts con foto, `/pause`, `/resume`, `/stop`, con autenticación HMAC.
- **Inicio de sesión con Google + sincronización multi-dispositivo (Pro)** — una cuenta de Google, dispositivos ilimitados; callback de OAuth con manejador de URI `vscode://`; verificación de licencia por dispositivo.
- **Pausa entre ventanas** — pausar en una ventana de Antigravity se difunde vía bloqueo de archivos a todas las demás ventanas en <1 s.
- **Registro de actividad + Panel** — mira cada botón pulsado, cada sesión CDP, cada comando de Telegram en vivo.
- **Volcado de diagnóstico** — copia un payload de depuración estructurado al portapapeles para soporte con un mensaje.
- **Atajo Auto-Fix** — parchador de `.lnk` de Windows (Escritorio / Menú Inicio / Barra de tareas) para el flag `--remote-debugging-port`.
- **Auto-reparación por heartbeat** — los MutationObservers muertos (borrados por navegación del webview / hot-reload) son detectados y re-inyectados automáticamente cada 10 s.

---

## Qué hace

Cuando el Agent de Antigravity propone ediciones de archivos, comandos de terminal o pide permisos de herramientas, esta extensión los auto-acepta para que no tengas que hacer clic en cada botón manualmente.

**Dos estrategias, cero interferencia:**

| Estrategia | Qué maneja | Cómo |
|---|---|---|
| **VS Code Commands** (500 ms + jitter) | Pasos del Agent, comandos de terminal | Llama a los comandos nativos de aceptación de Antigravity |
| **CDP + MutationObserver** (orientado a eventos) | Run, Accept, Always Allow, Continue, Retry | Script inyectado una vez, reacciona al instante a los cambios del DOM |

---

## Configuración

### 1. Activar Modo Depuración (Obligatorio)

La extensión necesita el Chrome DevTools Protocol para hacer clic en los botones de permisos. Lanza Antigravity con:

```
--remote-debugging-port=9333
```

> **¿Por qué el puerto 9333?** El Browser Control integrado de Antigravity (el botón de Chrome en la barra de herramientas) usa el puerto 9222 por defecto. Usar el mismo puerto causa un conflicto `EADDRINUSE` en macOS/Linux. El puerto 9333 evita esto por completo.

<details>
<summary><b>🪟 Windows</b></summary>

**Automático:** En el primer arranque, la extensión detecta si el puerto está cerrado y muestra **"Auto-Fix Shortcut"** — haz clic para parchar automáticamente tu acceso directo `.lnk`.

**Manual:** Clic derecho en tu acceso directo de Antigravity → Propiedades → añade al Target:
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**Opción 1 — App de Automator (recomendado):**
1. Abre **Automator** → Nuevo documento → **Aplicación**
2. Busca **"Ejecutar script de shell"** en la biblioteca
3. Pega: `open -a "Antigravity" --args --remote-debugging-port=9333`
4. Guárdalo como "AntiGravity Launcher" en el Escritorio o en Aplicaciones

**Opción 2 — Alias en terminal** (añade a `~/.zshrc`):
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **Nota:** El nombre de la app debe coincidir exactamente. Comprueba con `ls /Applications/ | grep -i anti`

**Opción 3 — Binario Electron directo** (si `open -a` no pasa los argumentos correctamente):
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**Opción 1 — Edita el archivo `.desktop`:**
```bash
# Encuéntralo:
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# Edita la línea Exec:
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**Opción 2 — Alias de shell** (añade a `~/.bashrc` o `~/.zshrc`):
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**Opción 3 — Script wrapper:**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. Instalar la Extensión

**Desde VSIX (recomendado):**
1. Obtén el último paquete `.vsix`
2. En Antigravity: `Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. Selecciona el archivo descargado
4. Reload Window

**Manual:**
1. Copia el directorio `src/`, `package.json` y `package-lock.json` a:
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. Ejecuta `npm install` en ese directorio (instala la dependencia `ws`)
3. Reload Window

---

## Uso

### Comandos básicos

- **Alternar:** Haz clic en `⚡ Auto: ON` / `✕ Auto: OFF` en la barra de estado
- **O:** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **Panel:** Haz clic en el icono del panel en la barra de estado para ver el estado de CDP, sesiones activas, registro de actividad y selector de idioma
- **Logs:** Panel Output → `Anti-Remote-Pro`

### Comandos Pro

Todas las funciones Pro son accesibles a través de la Paleta de Comandos (`Ctrl+Shift+P`):

| Comando | Qué hace |
|---|---|
| `Anti-Remote-Pro: Login with Google` | Inicia sesión para sincronizar tu licencia Pro entre dispositivos |
| `Anti-Remote-Pro: Logout` | Borra la licencia local + cuenta iniciada |
| `Anti-Remote-Pro: Refresh Pro Status` | Fuerza una re-verificación de licencia contra el servidor |
| `Anti-Remote-Pro: Connect Telegram Bot` | Inicia el flujo de emparejamiento — abre el bot en Telegram, toca **Start** para vincular esta máquina |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | Revoca la clave HMAC para esta máquina |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | Fuerza la re-descarga del payload del núcleo firmado |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | Interruptor de apagado global (también vinculado a `Ctrl+Shift+S`) |
| `Anti-Remote-Pro: Fix Missing Conversations` | Re-siembra el índice de conversaciones de Swarm si la barra lateral parece desincronizada |

> **Consejo:** `Ctrl+Shift+S` es la forma más rápida de pausar/reanudar Swarm + auto-aceptar cuando un compañero humano entra en tu sesión.

---

## Flujo Multi-Agent

### ⚠️ Limitación del Agent Manager (sin Modo Swarm)

El Agent Manager de Antigravity usa un **webview único compartido** — solo se renderiza el DOM de la conversación activa. Las conversaciones en segundo plano están completamente desmontadas. Sin el Modo Swarm, tanto la API de VS Code Commands como CDP solo pueden alcanzar la conversación visible actualmente.

### ✅ Solución: Modo Swarm (Pro)

El Modo Swarm resuelve esto rotando el foco por todas las conversaciones pendientes, dejando que docenas de agentes en segundo plano se ejecuten sin intervención:

- Escanea cada conversación en la barra lateral y elige la que tiene trabajo pendiente.
- Respeta tu ajuste de segundos inactivos para no robar nunca el foco mientras escribes.
- Consciente entre ventanas: pausar cualquier ventana pausa todas vía broadcast de bloqueo de archivos.
- Seguro por defecto: payload del núcleo firmado, firewall de comandos sigue aplicándose.

### Alternativa: Duplicar Workspace (gratis)

Si no tienes licencia Pro, aún puedes ejecutar 2–3 agentes en paralelo:

1. Clic en **File → Duplicate Workspace**
2. Esto abre una segunda ventana de Antigravity conectada al mismo proyecto
3. Inicia un chat en la Ventana 1 y otro chat en la Ventana 2
4. Cada ventana tiene su propio webview — la extensión hace auto-clic en los botones en **ambas ventanas simultáneamente**

---

## Ajustes

| Ajuste | Por defecto | Alcance | Descripción |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | Intervalo base de polling en ms (±20 % jitter aplicado automáticamente) |
| `autoAcceptV2.customButtonTexts` | `[]` | application | Textos de botón adicionales para i18n o prompts personalizados (p. ej. `["toujours autoriser"]`) |
| `autoAcceptV2.cdpPort` | `9333` | machine | Puerto CDP (por defecto evita el conflicto con AG Browser Control en 9222) |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | Auto-aceptar cambios de edición de archivos (desactívalo para revisar diffs manualmente) |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Auto-clic Retry / Continue cuando el Agent choca con errores o límites de invocación |
| `autoAcceptV2.blockedCommands` | `[]` | application | Comandos que NUNCA se auto-ejecutarán (p. ej. `rm`, `git push`, `npm publish`) |
| `autoAcceptV2.allowedCommands` | `[]` | application | Si se establece, SOLO estos comandos se auto-ejecutarán (modo whitelist) |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Clave de licencia Pro — desbloquea Modo Swarm + Telegram Remote |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Segundos de inactividad del usuario antes de que Swarm navegue a un chat pendiente (3–60) |

> **Consejo:** Los ajustes se recargan en caliente — los cambios surten efecto inmediatamente sin reiniciar.

---

## Cómo Funciona

### CDP Persistente + MutationObserver

La extensión mantiene una **conexión WebSocket persistente a nivel de navegador** al DevTools Protocol de Chromium. En vez de hacer polling cada 1,5 s, inyecta un payload **MutationObserver** una vez por target. El observer reacciona al instante cuando React monta nuevos elementos de botón, con un throttle de leading-edge de 100 ms para prevenir picos de CPU durante salidas en streaming. La extensión usa un **filtro de target solo por whitelist** — solo se conecta a targets `vscode-webview://` y cede automáticamente el puerto CDP cuando se detecta el sub-agente del navegador de AG, previniendo conflictos de ArrayBuffer.

### Escáner DOM de Una Pasada

El escáner de botones recorre el árbol DOM **exactamente una vez** por ciclo, comprobando todas las palabras clave simultáneamente contra cada nodo. Esto es O(D) en vez de O(N×D) que podría causar congelamientos de UI con muchas palabras clave. La coincidencia con prioridad asegura que `Run` siempre vence a `Accept`, que siempre vence a `Allow`, independientemente del orden del DOM.

### Guardia del Webview

El panel del Agent de Antigravity se ejecuta en un proceso Chromium aislado (OOPIF). El script inyectado usa una comprobación diferida de `isAgentPanel()` dentro de `scanAndClick()` — verifica la existencia de `.react-app-container` dinámicamente en cada escaneo en vez de en el momento de la inyección. Esto evita una condición de carrera donde el DOM está sin hidratar en `targetCreated`.

### Auto-Reparación por Heartbeat

La conexión CDP valida sesiones existentes cada ciclo de heartbeat (10 s). Si el MutationObserver de una sesión está muerto (contexto de ejecución borrado por navegación del webview o hot-reload de React), automáticamente re-inyecta el observer — sin necesidad de reconexión. Las sesiones inalcanzables 3 veces consecutivas se desvinculan limpiamente y se podan.

### Prevención del Bucle del Botón de Expandir

Los botones de tipo expandir (p. ej. "Expand" de la previsualización del navegador) usan una regla de **clic-una-vez-por-sesión**: una vez pulsados, se suprimen permanentemente para esa sesión CDP vía un Set `expandedOnce`. Esto previene el bucle de reapertura infinita del overlay donde cerrar el panel expandido dispara un re-clic. El estado se resetea naturalmente cuando comienza una nueva conversación del Agent.

### Detección de Botones

Dentro del panel del Agent, un `TreeWalker` busca botones por contenido de texto usando coincidencia `startsWith` con **comprobaciones de límite de palabra** para prevenir falsos positivos (p. ej. `accept-test.js` no coincidirá con `accept`):

| Prioridad | Texto | Coincidencias |
|---|---|---|
| 1 | `run` | Botón "Run Alt+d" (no el desplegable "Always run ^") |
| 2 | `accept` | Botón Accept |
| 3 | `always allow` | Prompts de permisos |
| 4 | `allow this conversation` | Permisos con alcance de conversación |
| 5 | `allow` | Prompts de permisos |
| 6 | `retry` | Prompts de Retry |
| 7 | `continue` | Reanudación tras límite de invocaciones del Agent |

### Filtrado de Comandos

Las listas de comandos bloqueados y permitidos usan **coincidencia por límite de palabra** contra el bloque de código arriba de un botón Run. Por ejemplo, bloquear `rm` bloqueará `rm -rf /tmp` pero NO `yarn format` o `npm run build`.

---

## Comandos Bloqueados Recomendados

El panel incluye un botón **Load Safety Presets** que importa en masa 50+ patrones de comandos destructivos cubriendo limpiadores de sistema de archivos, formateadores de disco, drops de bases de datos, force-pushes y fork bombs.

**Un clic:** Abre el Panel → haz clic en **Load Recommended Safety Presets**.

**Pegado en masa:** Las entradas de bloqueados / permitidos soportan valores **separados por comas** — pega una lista y pulsa Enter.

<details>
<summary><b>📋 Manual: Copia a settings.json</b></summary>

Añade esto a tu `settings.json` (`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`):

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

### Auto-Reparación CDP

Al activarse, la extensión comprueba si el puerto 9333 está abierto (con 9222 como fallback). Si no, muestra una notificación con:
- **Auto-Fix Shortcut (Windows)** — parcha los accesos directos `.lnk` en el Escritorio, Menú Inicio, **y Barra de Tareas**

---

## Solución de Problemas

### El bot deja de funcionar después de unas horas

**Causa:** O bien (a) Antigravity reinicia silenciosamente su proceso Electron (auto-actualizaciones, presión de memoria o crash del host de extensiones) y el nuevo proceso no tiene `--remote-debugging-port=9333`, o (b) el contexto de ejecución del webview fue borrado por una navegación / hot-reload.

**Arreglo:** La lógica de auto-reparación por heartbeat detecta y re-inyecta observers muertos automáticamente. Si aún no funciona, cierra **todas** las ventanas de Antigravity por completo, luego reábrelas desde tu acceso directo parchado.

### El bot está ON pero no hace clic en nada

1. **Alterna OFF → ON** — haz clic dos veces en el icono de la barra de estado para reiniciar el polling
2. **Comprueba el puerto de depuración** — visita `http://127.0.0.1:9333/json/list` en un navegador. Si lo rechaza, el puerto de depuración está muerto (ver arriba)
3. **Comprueba los logs de Output** — `Ctrl+Shift+U` → desplegable → `Anti-Remote-Pro`. Busca líneas `[CDP] ✓ Thread`. Si no hay ninguna, CDP no puede encontrar el panel del Agent

### El icono de la barra de estado no aparece tras la instalación

1. Ejecuta `Ctrl+Shift+P` → `Reload Window`
2. Verifica que el VSIX se construyó **con** dependencias (el paquete `ws` debe estar incluido)

---

## Seguridad

Comandos deliberadamente **excluidos** para prevenir daños:
- `notification.acceptPrimaryAction` — auto-clicaría diálogos destructivos
- `chatEditing.acceptAllFiles` — causa alternancia del Outline de la barra lateral
- Todos los comandos de merge / conflicto git — podrían escoger silenciosamente el lado equivocado
- Todos los comandos de autocompletado / sugerencia — corromperían tu escritura

---

## FAQ de Seguridad

**¿Por qué esto necesita `--remote-debugging-port`?**

El panel del Agent de Antigravity se ejecuta en un proceso Chromium aislado. La API de Extensiones de VS Code no puede ver ni interactuar con los botones Run / Accept / Allow dentro de él — son elementos de UI de React sin comandos registrados. El Chrome DevTools Protocol (CDP) en un puerto de localhost (por defecto 9333) es la única forma de alcanzarlos.

**¿Es seguro?**

- **Solo localhost** — el puerto se vincula a `127.0.0.1`, no a `0.0.0.0`. Ninguna máquina externa puede conectarse.
- **Cero telemetría en el núcleo de auto-aceptación** — escaneo del DOM, coincidencia de botones y filtrado de comandos nunca hacen llamadas de red.
- **El único tráfico saliente** es (a) verificación de licencia, (b) API del Bot de Telegram — y solo si la emparejas, y (c) obtención del payload del núcleo firmado para el Modo Swarm. Los tres están apagados por defecto.
- **Payload Pro firmado.** El motor del núcleo Swarm está firmado con Ed25519 y verificado dentro de un worker de Node antes de compilarse en RAM — un hombre-en-el-medio no puede colar un escáner malicioso.
- **Flujo de trabajo de desarrollo estándar** — `--remote-debugging-port` es el mismo flag usado por desarrolladores de extensiones de VS Code y depuración de apps Electron.
- **El parchador de accesos directos tiene alcance** — el auto-fix solo modifica archivos `.lnk` cuyo path de destino contiene "Antigravity".
- **Sin archivos de Antigravity modificados** — esta extensión se ejecuta enteramente como una extensión externa de VS Code. Desinstálala y no queda rastro.

**¿Mi chat de Telegram leerá mi código?**

Solo lo que *tú* pidas explícitamente. `/peek` devuelve el texto visible del panel del Agent activo; `/prompt` envía tu mensaje dentro. La extensión nunca envía proactivamente código, diffs, capturas ni telemetría a Telegram.

---

## Licencia

MIT
