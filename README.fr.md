<div align="center">

<a href="https://antigravity.apiai.eu.cc/?lang=fr"><img src="https://antigravity.apiai.eu.cc/assets/icon.png" alt="Anti-Remote-Pro" width="96" height="96"></a>

# Anti-Remote-Pro

**Le pilote automatique privé d'abord, anti-bannissement et contrôlable par Telegram pour [Antigravity](https://antigravity.dev) — l'assistant de codage IA de Google.**
**Un seul compte Google, un nombre illimité d'appareils.**

### [🌐 Site Officiel &nbsp;·&nbsp; Télécharger Maintenant →](https://antigravity.apiai.eu.cc/?lang=fr)

<sub>
  📖 <b>Lire ceci en :</b>
  <a href="./README.md">English</a> &nbsp;·&nbsp;
  <a href="./README.zh-CN.md">简体中文</a> &nbsp;·&nbsp;
  <a href="./README.zh-TW.md">繁體中文</a> &nbsp;·&nbsp;
  <a href="./README.ja.md">日本語</a> &nbsp;·&nbsp;
  <a href="./README.ko.md">한국어</a> &nbsp;·&nbsp;
  <a href="./README.es.md">Español</a> &nbsp;·&nbsp;
  <b>Français</b> &nbsp;·&nbsp;
  <a href="./README.de.md">Deutsch</a> &nbsp;·&nbsp;
  <a href="./README.pt.md">Português</a> &nbsp;·&nbsp;
  <a href="./README.ru.md">Русский</a> &nbsp;·&nbsp;
  <a href="./README.ar.md">العربية</a> &nbsp;·&nbsp;
  <a href="./README.hi.md">हिन्दी</a>
</sub>

</div>

Accepte automatiquement les étapes de l'Agent, les commandes du terminal, les modifications de fichiers et les demandes de permission afin que l'Agent livre votre travail sans intervention manuelle — tout en gardant chaque octet sur votre machine et en vous permettant de piloter chacune de vos machines depuis votre téléphone.

> 💡 **Vous voulez démarrer rapidement ?** Le [site officiel](https://antigravity.apiai.eu.cc/?lang=fr) propose un guide complet, des captures d'écran en direct, les tarifs Pro et le dernier téléchargement `.vsix` — le tout en 12 langues.

---

## 🔥 Pourquoi Anti-Remote-Pro

### 🔒 1. Confidentialité Absolue — votre code ne quitte jamais votre portable

- **Pipeline 100 % local.** Toute la détection des boutons, le scan du DOM et le filtrage des commandes s'exécutent à l'intérieur de votre processus VS Code / Antigravity. Aucun prompt, aucune capture, aucun diff ne quitte jamais la machine.
- **Port de débogage uniquement en localhost.** Le CDP est lié strictement à `127.0.0.1:9333`. Aucun hôte externe sur le LAN, sur le Wi-Fi d'un café, ou sur un réseau de coworking ne peut l'atteindre — vérifié par le binding du socket, pas seulement par une promesse.
- **Zéro télémétrie.** Le cœur d'auto-acceptation n'effectue aucun appel d'analytics, aucun rapport de crash, aucune « statistique d'usage anonyme ». Le seul trafic sortant va vers Telegram (uniquement si vous l'appairez) et vers le serveur de licences (uniquement pour vérifier votre clé).
- **Attachement aux cibles uniquement par whitelist.** La couche CDP s'attache **uniquement** aux cibles `vscode-webview://` correspondant au panneau de l'Agent. Elle refuse de s'attacher à vos autres onglets, sub-agents de navigateur, ou toute cible Chromium non-Antigravity.
- **Payload du cœur signé.** Le moteur du cœur Pro est récupéré sous forme de payload signé Ed25519, vérifié à l'intérieur d'un worker Node, et compilé en RAM — jamais écrit sur disque, jamais altérable par un homme du milieu.
- **Aucune modification d'Antigravity lui-même.** Nous ne patchons, ne réempaquetons, ni ne hookons les binaires d'Antigravity. CDP purement externe — désinstallez et il ne reste aucune trace.

### 📱 2. Contrôle à Distance par Telegram — pilotez Antigravity depuis n'importe où

Appairez votre IDE à un bot Telegram une seule fois, et votre téléphone devient une télécommande complète pour l'Agent :

- **`/prompt <texte>`** — envoyez un nouveau prompt à la conversation active depuis n'importe où sur la planète. Recolle automatiquement les messages de 4096 caractères découpés par Telegram.
- **`/peek [N]`** — lisez la dernière réponse de l'Agent directement dans Telegram, sans avoir à réveiller votre portable.
- **Envoyez une photo avec légende** — joint la capture au prompt pour un débogage visuel en déplacement.
- **`/pause` & `/resume`** — basculez le coupe-circuit global depuis votre téléphone. Le verrou de fichier inter-fenêtres garantit que chaque fenêtre Antigravity obéit instantanément.
- **`/stop`** — arrête la réponse en cours de génération.
- **Commandes signées HMAC.** Chaque commande Telegram est vérifiée avec une clé HMAC par appareil. Un chat Telegram divulgué ne suffit *pas* à contrôler votre IDE.
- **Élection de maître unique.** Quand vous avez 5 fenêtres Antigravity ouvertes, une seule remporte le verrou maître et traite les commandes — pas d'envois en double, pas de conditions de course.

### 🛡️ 3. Stratégie Anti-Bannissement Pionnière dans l'Industrie

La plupart des auto-clickers font flagger les comptes parce qu'ils tapent les endpoints à une cadence fixe et cliquent pendant que l'humain tape encore. Anti-Remote-Pro est conçu à l'opposé :

- **Rythme humain.** Polling actif à 500 ms avec **±20 % de jitter aléatoire** + backoff exponentiel (plafonné à 30 s) sur les erreurs consécutives. Aucun intervalle mécaniquement parfait à fingerprinter.
- **Smart-sleep en inactivité.** Sans session CDP active, le moteur tombe à un heartbeat de 5 s — pression IPC quasi nulle quand vous êtes absent.
- **Fenêtre de grâce de 20 secondes pendant l'activité utilisateur.** Si l'utilisateur tape dans le chat, défile dans le webview ou bouge le curseur de l'éditeur, **tous les auto-clics sont reportés**. Le bot attend littéralement que vous vous arrêtiez, donc il ne co-clique jamais pendant que vous lisez.
- **Aucun patch binaire.** Les fichiers d'Antigravity, settings.json, et le répertoire de données utilisateur sont en lecture seule pour cette extension. Les mises à jour automatiques officielles et les vérifications d'intégrité passent proprement parce que rien n'est modifié.
- **CDP en loopback uniquement.** Aucun listener TCP, aucun forwarding distant. Le flag `--remote-debugging-port=9333` est un flag de débogage Electron standard — le même que celui utilisé en interne par Microsoft, Google et JetBrains.
- **Pare-feu de commandes strict.** Liste de blocage intégrée + liste blanche stricte optionnelle + 50+ **Safety Presets** soigneusement choisis (rm -rf, force-push, drop database, fork bombs, effaceurs de disque, suppressions de registre…). Le bot *refusera* d'exécuter une commande destructive même si l'Agent insiste.
- **Clic unique par session pour les boutons d'expansion.** Élimine la boucle de « réouverture infinie » qui risque de déclencher les heuristiques anti-abus.
- **Cession instantanée au sub-agent navigateur officiel.** Quand l'outillage navigateur d'AG active le port 9222, notre worker se détache et s'écarte — pas de collision de port, pas de signature de double attachement.

> Effet combiné : du point de vue du backend de l'Agent, vous avez l'air d'un utilisateur humain légèrement plus rapide que la moyenne, impeccablement poli.

### 🌍 4. Multi-Langue — 12 langues, des milliards d'utilisateurs couverts

Anti-Remote-Pro embarque les traductions complètes de l'UI (commandes, paramètres, tableau de bord, notifications, réponses Telegram). Choisissez dans le menu déroulant du tableau de bord, ou laissez-le détecter automatiquement la langue de votre IDE.

| # | Langue | Nom natif | Régions principales |
|---|---|---|---|
| 1 | Anglais | English | 🇺🇸 USA · 🇬🇧 UK · 🇨🇦 Canada · 🇦🇺 Australie · 🇮🇪 Irlande · 🇳🇿 Nouvelle-Zélande · 🇿🇦 Afrique du Sud · 🇸🇬 Singapour · 🇮🇳 Inde (IT) |
| 2 | Chinois Simplifié | 简体中文 | 🇨🇳 Chine continentale · 🇸🇬 Singapour · 🇲🇾 Malaisie |
| 3 | Chinois Traditionnel | 繁體中文 | 🇹🇼 Taïwan · 🇭🇰 Hong Kong · 🇲🇴 Macao |
| 4 | Espagnol | Español | 🇪🇸 Espagne · 🇲🇽 Mexique · 🇦🇷 Argentine · 🇨🇴 Colombie · 🇨🇱 Chili · 🇵🇪 Pérou · 🇻🇪 Venezuela · +14 autres |
| 5 | Français | Français | 🇫🇷 France · 🇨🇦 Canada (Québec) · 🇧🇪 Belgique · 🇨🇭 Suisse · 🇱🇺 Luxembourg · 🇲🇨 Monaco · grande partie de l'Afrique de l'Ouest et Centrale |
| 6 | Hindi | हिन्दी | 🇮🇳 Inde · 🇫🇯 Fidji |
| 7 | Portugais (BR) | Português | 🇧🇷 Brésil · 🇵🇹 Portugal · 🇦🇴 Angola · 🇲🇿 Mozambique |
| 8 | Russe | Русский | 🇷🇺 Russie · 🇧🇾 Biélorussie · 🇰🇿 Kazakhstan · 🇰🇬 Kirghizistan · 🇺🇿 Ouzbékistan · 🇺🇦 Ukraine |
| 9 | Arabe | العربية (RTL) | 🇸🇦 Arabie Saoudite · 🇦🇪 EAU · 🇪🇬 Égypte · 🇶🇦 Qatar · 🇰🇼 Koweït · 🇧🇭 Bahreïn · 🇴🇲 Oman · 🇯🇴 Jordanie · 🇲🇦 Maroc · 🇩🇿 Algérie · 🇹🇳 Tunisie · 🇮🇶 Irak · +10 autres |
| 10 | Japonais | 日本語 | 🇯🇵 Japon |
| 11 | Allemand | Deutsch | 🇩🇪 Allemagne · 🇦🇹 Autriche · 🇨🇭 Suisse · 🇱🇮 Liechtenstein · 🇱🇺 Luxembourg |
| 12 | Coréen | 한국어 | 🇰🇷 Corée du Sud |

- **Détection automatique** suit `vscode.env.language` — l'extension sert votre locale immédiatement au premier lancement.
- **Override manuel** via le menu déroulant de langue du Tableau de bord (persiste entre les rechargements).
- **RTL aware** — l'UI arabe inverse la direction de mise en page automatiquement (`dir="rtl"`).
- **Surcharges de mots-clés personnalisées** — `autoAcceptV2.customButtonTexts` vous permet d'ajouter des libellés de bouton localisés pour toute chaîne d'UI que nous n'avons pas encore traduite (par ex. `["toujours autoriser", "siempre permitir"]`).

### 🔗 5. Synchro Multi-Appareils avec Connexion Google — un compte, toutes vos machines

**Connectez-vous une fois avec Google** et Anti-Remote-Pro vous suit partout — bureau, portable, PC personnel, station de travail, Windows, macOS, Linux.

- **Google OAuth en un clic.** `Anti-Remote-Pro: Login with Google` ouvre votre navigateur, complète l'OAuth Google standard, et redirige vers l'IDE via un gestionnaire d'URI sécurisé `vscode://Pro.antigravity-autoaccept/auth`. Pas de copier-coller de clé de licence, pas de manège d'e-mails.
- **La licence Pro se synchronise automatiquement entre appareils.** Votre abonnement est lié à votre compte Google, pas à une seule machine. Installez sur l'appareil n°2, n°3, n°10 — connectez-vous et Pro se débloque instantanément. Le serveur de licences vérifie chaque `machineId` par rapport à votre compte à chaque rafraîchissement.
- **Exécutez sur un nombre illimité d'appareils simultanément.** Portable du travail, bureau de la maison, machine de dev distante, une VM par client — tous peuvent exécuter Anti-Remote-Pro en parallèle sous le même compte.
- **Flottes parallèles.** Chaque appareil opère indépendamment avec son propre CDP / Swarm / pare-feu de commandes, vous pouvez donc avoir un portable qui mouline la Conversation A pendant que votre bureau exécute la Conversation B — aucun ne vole le focus à l'autre.
- **Appairage Telegram par appareil.** Chaque machine s'appaire au bot Telegram séparément et obtient sa propre clé HMAC. Vous pouvez les nommer dans le flux d'appairage (par ex. « MacBook », « WorkPC ») et les adresser individuellement depuis le même chat Telegram.
- **Coordination inter-fenêtres sur la même machine.** Quand vous avez plusieurs fenêtres Antigravity ouvertes sur un seul appareil, un protocole de verrou de fichier maintient leur état pause/reprise synchronisé en moins d'une seconde — pas de doubles clics, pas de bagarre.
- **Révocation instantanée.** `Anti-Remote-Pro: Logout` efface le token local et indique au serveur d'invalider cet appareil. Portable perdu ? Déconnectez-vous depuis une autre machine + `Refresh Pro Status` et l'ancienne machine s'éteint.
- **Refresh Pro Status.** Changement de plan ou abonnement renouvelé ? Une commande retire les derniers droits — pas de réinstallation, pas de redémarrage.

> En pratique : connectez-vous une fois sur vos 3 ordinateurs, appairez chacun au même bot Telegram, et votre téléphone devient une télécommande centrale pour toute votre flotte de codage.

---

## ⚡ Capacités Centrales en Un Coup d'Œil

- **Auto-clic** Run / Accept / Always Allow / Allow this conversation / Continue / Retry sur tout le panneau de l'Agent — conscient des priorités, donc `Run` gagne toujours sur `Accept`.
- **Auto-acceptation des modifications de fichiers** avec un seul interrupteur — désactivez-le à tout moment pour examiner les diffs manuellement.
- **Pare-feu de commandes** — mode blocage de motifs ou liste blanche stricte, les deux avec correspondance par limite de mot.
- **Safety presets** — import en un clic de 50+ motifs de commandes destructives (effaceurs de système de fichiers, formateurs de disque, force-push, drops de BD, fork bombs).
- **Mode Swarm (Pro)** — fait tourner automatiquement les conversations en attente de l'Agent Manager et les exécute sans intervention en arrière-plan.
- **Telegram Remote (Pro)** — télécommande IDE complète : `/prompt`, `/peek`, prompts photo, `/pause`, `/resume`, `/stop`, avec auth HMAC.
- **Connexion Google + synchro multi-appareils (Pro)** — un compte Google, appareils illimités ; callback OAuth via gestionnaire d'URI `vscode://` ; vérification de licence par appareil.
- **Pause inter-fenêtres** — mettre en pause dans une fenêtre Antigravity diffuse via verrou de fichier à toutes les autres fenêtres en <1 s.
- **Journal d'activité + Tableau de bord** — voyez chaque bouton cliqué, chaque session CDP, chaque commande Telegram en direct.
- **Dump de diagnostic** — copie un payload de débogage structuré dans le presse-papiers pour un support en un message.
- **Raccourci Auto-Fix** — patcheur `.lnk` Windows (Bureau / Menu Démarrer / Barre des tâches) pour le flag `--remote-debugging-port`.
- **Auto-réparation par heartbeat** — les MutationObservers morts (effacés par la navigation du webview / hot-reload) sont détectés et ré-injectés automatiquement toutes les 10 s.

---

## Ce qu'il fait

Quand l'Agent Antigravity propose des modifications de fichiers, des commandes de terminal, ou demande des permissions d'outils, cette extension les auto-accepte pour que vous n'ayez pas à cliquer sur chaque bouton manuellement.

**Deux stratégies, zéro interférence :**

| Stratégie | Ce qu'elle gère | Comment |
|---|---|---|
| **VS Code Commands** (500 ms + jitter) | Étapes de l'Agent, commandes terminal | Appelle les commandes natives d'acceptation d'Antigravity |
| **CDP + MutationObserver** (orienté événements) | Run, Accept, Always Allow, Continue, Retry | Script injecté une seule fois, réagit instantanément aux changements DOM |

---

## Configuration

### 1. Activer le Mode Débogage (Obligatoire)

L'extension a besoin du Chrome DevTools Protocol pour cliquer sur les boutons de permission. Lancez Antigravity avec :

```
--remote-debugging-port=9333
```

> **Pourquoi le port 9333 ?** Le Browser Control intégré d'Antigravity (le bouton Chrome dans la barre d'outils) utilise le port 9222 par défaut. Utiliser le même port cause un conflit `EADDRINUSE` sur macOS/Linux. Le port 9333 évite cela complètement.

<details>
<summary><b>🪟 Windows</b></summary>

**Automatique :** Au premier lancement, l'extension détecte si le port est fermé et affiche **"Auto-Fix Shortcut"** — cliquez pour patcher automatiquement votre raccourci `.lnk`.

**Manuel :** Clic droit sur votre raccourci Antigravity → Propriétés → ajoutez à Cible :
```
--remote-debugging-port=9333
```

</details>

<details>
<summary><b>🍎 macOS</b></summary>

**Option 1 — App Automator (recommandé) :**
1. Ouvrez **Automator** → Nouveau document → **Application**
2. Cherchez **« Exécuter le script shell »** dans la bibliothèque
3. Collez : `open -a "Antigravity" --args --remote-debugging-port=9333`
4. Enregistrez sous « AntiGravity Launcher » sur le Bureau ou dans Applications

**Option 2 — Alias terminal** (ajoutez à `~/.zshrc`) :
```bash
alias antigravity='open -a "Antigravity" --args --remote-debugging-port=9333'
```

> **Note :** Le nom de l'app doit correspondre exactement. Vérifiez avec `ls /Applications/ | grep -i anti`

**Option 3 — Binaire Electron direct** (si `open -a` ne passe pas les args correctement) :
```bash
alias antigravity='/Applications/Antigravity.app/Contents/MacOS/Electron --remote-debugging-port=9333 & disown'
```

</details>

<details>
<summary><b>🐧 Linux</b></summary>

**Option 1 — Éditer le fichier `.desktop` :**
```bash
# Trouvez-le :
find /usr/share/applications ~/.local/share/applications -name "*ntigravity*" 2>/dev/null

# Éditez la ligne Exec :
Exec=/path/to/antigravity --remote-debugging-port=9333 %F
```

**Option 2 — Alias shell** (ajoutez à `~/.bashrc` ou `~/.zshrc`) :
```bash
alias antigravity='antigravity --remote-debugging-port=9333'
```

**Option 3 — Script wrapper :**
```bash
#!/bin/bash
/opt/Antigravity/antigravity --remote-debugging-port=9333 "$@"
```

</details>

### 2. Installer l'Extension

**Depuis VSIX (recommandé) :**
1. Récupérez le dernier paquet `.vsix`
2. Dans Antigravity : `Ctrl+Shift+P` → `Extensions: Install from VSIX`
3. Sélectionnez le fichier téléchargé
4. Reload Window

**Manuel :**
1. Copiez le répertoire `src/`, `package.json`, et `package-lock.json` vers :
   ```
   ~/.antigravity/extensions/Pro.antigravity-autoaccept-<version>/
   ```
2. Lancez `npm install` dans ce répertoire (installe la dépendance `ws`)
3. Reload Window

---

## Utilisation

### Commandes de base

- **Bascule :** Cliquez sur `⚡ Auto: ON` / `✕ Auto: OFF` dans la barre d'état
- **Ou :** `Ctrl+Shift+P` → `Anti-Remote-Pro: Toggle ON/OFF`
- **Tableau de bord :** Cliquez sur l'icône du tableau de bord dans la barre d'état pour voir l'état CDP, les sessions actives, le journal d'activité et le sélecteur de langue
- **Logs :** Panneau Output → `Anti-Remote-Pro`

### Commandes Pro

Toutes les fonctionnalités Pro sont accessibles via la Palette de Commandes (`Ctrl+Shift+P`) :

| Commande | Ce qu'elle fait |
|---|---|
| `Anti-Remote-Pro: Login with Google` | Connectez-vous pour synchroniser votre licence Pro entre appareils |
| `Anti-Remote-Pro: Logout` | Effacer la licence locale + le compte connecté |
| `Anti-Remote-Pro: Refresh Pro Status` | Forcer une re-vérification de licence contre le serveur |
| `Anti-Remote-Pro: Connect Telegram Bot` | Lance le flux d'appairage — ouvre le bot dans Telegram, tapez **Start** pour lier cette machine |
| `Anti-Remote-Pro: Disconnect Telegram Bot` | Révoque la clé HMAC pour cette machine |
| `Anti-Remote-Pro: Refresh Swarm Mode (bust cache)` | Force le re-téléchargement du payload du cœur signé |
| `Anti-Remote-Pro: Pause/Resume Swarm Mode` | Coupe-circuit global (également lié à `Ctrl+Shift+S`) |
| `Anti-Remote-Pro: Fix Missing Conversations` | Re-sème l'index de conversations de Swarm si la barre latérale semble désynchronisée |

> **Astuce :** `Ctrl+Shift+S` est le moyen le plus rapide de mettre en pause/reprendre Swarm + auto-acceptation quand un coéquipier humain rejoint votre session.

---

## Workflow Multi-Agent

### ⚠️ Limitation de l'Agent Manager (sans Mode Swarm)

L'Agent Manager d'Antigravity utilise un **webview unique partagé** — seul le DOM de la conversation active est rendu. Les conversations en arrière-plan sont complètement démontées. Sans le Mode Swarm, l'API VS Code Commands et CDP ne peuvent atteindre que la conversation visible actuellement.

### ✅ Solution : Mode Swarm (Pro)

Le Mode Swarm résout cela en faisant tourner le focus sur toutes les conversations en attente, laissant des dizaines d'agents en arrière-plan s'exécuter sans intervention :

- Scanne chaque conversation dans la barre latérale et choisit celle avec du travail en attente.
- Respecte votre paramètre idle-seconds pour ne jamais voler le focus pendant que vous tapez.
- Conscient inter-fenêtres : mettre en pause une fenêtre met en pause toutes via diffusion par verrou de fichier.
- Sûr par défaut : payload du cœur signé, pare-feu de commandes toujours appliqué.

### Solution de repli : Duplicate Workspace (gratuit)

Si vous n'avez pas de licence Pro, vous pouvez quand même exécuter 2–3 agents en parallèle :

1. Cliquez sur **File → Duplicate Workspace**
2. Cela ouvre une seconde fenêtre Antigravity connectée au même projet
3. Démarrez un chat dans la Fenêtre 1 et un autre chat dans la Fenêtre 2
4. Chaque fenêtre a son propre webview — l'extension auto-clique les boutons dans **les deux fenêtres simultanément**

---

## Paramètres

| Paramètre | Par défaut | Portée | Description |
|---|---|---|---|
| `autoAcceptV2.pollInterval` | `500` | window | Intervalle de polling de base en ms (±20 % de jitter appliqué automatiquement) |
| `autoAcceptV2.customButtonTexts` | `[]` | application | Textes de bouton supplémentaires pour i18n ou prompts personnalisés (par ex. `["toujours autoriser"]`) |
| `autoAcceptV2.cdpPort` | `9333` | machine | Port CDP (par défaut évite le conflit avec AG Browser Control sur 9222) |
| `autoAcceptV2.autoAcceptFileEdits` | `true` | window | Auto-accepter les changements d'édition de fichier (désactivez pour examiner les diffs manuellement) |
| `autoAcceptV2.autoRetryEnabled` | `true` | window | Auto-cliquer Retry / Continue quand l'Agent atteint des erreurs ou des limites d'invocation |
| `autoAcceptV2.blockedCommands` | `[]` | application | Commandes à NE JAMAIS auto-exécuter (par ex. `rm`, `git push`, `npm publish`) |
| `autoAcceptV2.allowedCommands` | `[]` | application | Si défini, SEULES ces commandes seront auto-exécutées (mode whitelist) |
| `autoAcceptV2.proLicenseKey` | `""` | machine-overridable | Clé de licence Pro — débloque le Mode Swarm + Telegram Remote |
| `autoAcceptV2.swarmIdleSeconds` | `15` | window | Secondes d'inactivité utilisateur avant que Swarm navigue vers un chat en attente (3–60) |

> **Astuce :** Les paramètres sont rechargés à chaud — les changements prennent effet immédiatement sans redémarrer.

---

## Comment Ça Marche

### CDP Persistant + MutationObserver

L'extension maintient une **connexion WebSocket persistante au niveau navigateur** au DevTools Protocol de Chromium. Au lieu de poller toutes les 1,5 s, elle injecte un payload **MutationObserver** une fois par cible. L'observer réagit instantanément quand React monte de nouveaux éléments boutons, avec un throttle leading-edge de 100 ms pour empêcher les pics CPU pendant les sorties en streaming. L'extension utilise un **filtre de cibles uniquement par whitelist** — elle s'attache uniquement aux cibles `vscode-webview://` et cède automatiquement le port CDP quand le sub-agent navigateur d'AG est détecté, prévenant les conflits ArrayBuffer.

### Scanner DOM en Une Passe

Le scanner de boutons parcourt l'arbre DOM **exactement une fois** par cycle, vérifiant tous les mots-clés simultanément contre chaque nœud. C'est O(D) au lieu de O(N×D) qui pourrait causer des gels d'UI avec beaucoup de mots-clés. La correspondance consciente des priorités garantit que `Run` bat toujours `Accept`, qui bat toujours `Allow`, indépendamment de l'ordre du DOM.

### Garde Webview

Le panneau de l'Agent Antigravity tourne dans un processus Chromium isolé (OOPIF). Le script injecté utilise une vérification différée `isAgentPanel()` à l'intérieur de `scanAndClick()` — vérifiant l'existence de `.react-app-container` dynamiquement à chaque scan plutôt qu'au moment de l'injection. Cela évite une condition de course où le DOM est non hydraté lors de `targetCreated`.

### Auto-Réparation par Heartbeat

La connexion CDP valide les sessions existantes à chaque cycle de heartbeat (10 s). Si le MutationObserver d'une session est mort (contexte d'exécution effacé par une navigation webview ou un hot-reload React), elle ré-injecte automatiquement l'observer — pas besoin de reconnexion. Les sessions injoignables 3 fois consécutives sont proprement détachées et élaguées.

### Prévention de Boucle du Bouton d'Expansion

Les boutons de type expansion (par ex. « Expand » de la prévisualisation navigateur) utilisent une règle de **clic-une-fois-par-session** : une fois cliqués, ils sont supprimés de manière permanente pour cette session CDP via un Set `expandedOnce`. Cela empêche la boucle de réouverture infinie de l'overlay où fermer le panneau étendu déclenche un re-clic. L'état se réinitialise naturellement quand une nouvelle conversation Agent commence.

### Détection de Boutons

À l'intérieur du panneau de l'Agent, un `TreeWalker` cherche les boutons par contenu textuel en utilisant la correspondance `startsWith` avec des **vérifications de limite de mot** pour empêcher les faux positifs (par ex. `accept-test.js` ne correspondra pas à `accept`) :

| Priorité | Texte | Correspondances |
|---|---|---|
| 1 | `run` | bouton « Run Alt+d » (pas le menu déroulant « Always run ^ ») |
| 2 | `accept` | bouton Accept |
| 3 | `always allow` | prompts de permission |
| 4 | `allow this conversation` | permissions à portée de conversation |
| 5 | `allow` | prompts de permission |
| 6 | `retry` | prompts Retry |
| 7 | `continue` | reprise après limite d'invocation de l'Agent |

### Filtrage de Commandes

Les listes de commandes bloquées et autorisées utilisent la **correspondance par limite de mot** contre le bloc de code au-dessus d'un bouton Run. Par exemple, bloquer `rm` bloquera `rm -rf /tmp` mais PAS `yarn format` ou `npm run build`.

---

## Commandes Bloquées Recommandées

Le tableau de bord inclut un bouton **Load Safety Presets** qui importe en masse 50+ motifs de commandes destructives couvrant les effaceurs de système de fichiers, les formateurs de disque, les drops de bases de données, les force-push et les fork bombs.

**En un clic :** Ouvrez le Tableau de bord → cliquez sur **Load Recommended Safety Presets**.

**Coller en masse :** Les entrées bloqué / autorisé prennent en charge les valeurs **séparées par des virgules** — collez une liste et appuyez sur Entrée.

<details>
<summary><b>📋 Manuel : Copier dans settings.json</b></summary>

Ajoutez ceci à votre `settings.json` (`Ctrl+Shift+P` → `Preferences: Open User Settings (JSON)`) :

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

### Auto-Réparation CDP

À l'activation, l'extension vérifie si le port 9333 est ouvert (avec 9222 en repli). Sinon, elle affiche une notification avec :
- **Auto-Fix Shortcut (Windows)** — patche les raccourcis `.lnk` sur le Bureau, le Menu Démarrer, **et la Barre des tâches**

---

## Dépannage

### Le bot s'arrête de fonctionner après quelques heures

**Cause :** Soit (a) Antigravity redémarre silencieusement son processus Electron (mises à jour automatiques, pression mémoire, ou crash de l'host d'extensions) et le nouveau processus n'a pas `--remote-debugging-port=9333`, soit (b) le contexte d'exécution du webview a été effacé par une navigation / hot-reload.

**Correctif :** La logique d'auto-réparation par heartbeat détecte et ré-injecte automatiquement les observers morts. Si ça ne fonctionne toujours pas, fermez **toutes** les fenêtres Antigravity complètement, puis rouvrez depuis votre raccourci patché.

### Le bot est ON mais ne clique sur rien

1. **Bascule OFF → ON** — cliquez deux fois sur l'icône de la barre d'état pour redémarrer le polling
2. **Vérifiez le port de débogage** — visitez `http://127.0.0.1:9333/json/list` dans un navigateur. S'il refuse, le port de débogage est mort (voir ci-dessus)
3. **Vérifiez les logs Output** — `Ctrl+Shift+U` → menu déroulant → `Anti-Remote-Pro`. Cherchez les lignes `[CDP] ✓ Thread`. S'il n'y en a aucune, CDP ne peut pas trouver le panneau de l'Agent

### L'icône de la barre d'état n'apparaît pas après l'installation

1. Lancez `Ctrl+Shift+P` → `Reload Window`
2. Vérifiez que le VSIX a été construit **avec** les dépendances (le paquet `ws` doit être inclus)

---

## Sécurité

Commandes délibérément **exclues** pour prévenir les dégâts :
- `notification.acceptPrimaryAction` — auto-cliquerait des dialogues destructifs
- `chatEditing.acceptAllFiles` — cause le basculement de l'Outline de la barre latérale
- Toutes les commandes merge / conflit git — pourraient choisir silencieusement le mauvais côté
- Toutes les commandes d'auto-complétion / suggestion — corrompraient votre saisie

---

## FAQ Sécurité

**Pourquoi ceci a-t-il besoin de `--remote-debugging-port` ?**

Le panneau de l'Agent Antigravity tourne dans un processus Chromium isolé. L'API d'Extensions de VS Code ne peut pas voir ni interagir avec les boutons Run / Accept / Allow à l'intérieur — ce sont des éléments d'UI React sans commandes enregistrées. Le Chrome DevTools Protocol (CDP) sur un port localhost (par défaut 9333) est la seule manière de les atteindre.

**Est-ce sûr ?**

- **Localhost uniquement** — le port se lie à `127.0.0.1`, pas à `0.0.0.0`. Aucune machine externe ne peut se connecter.
- **Zéro télémétrie dans le cœur d'auto-acceptation** — le scan DOM, la correspondance de boutons, et le filtrage de commandes ne font jamais d'appel réseau.
- **Le seul trafic sortant** est (a) la vérification de licence, (b) l'API Bot Telegram — et seulement si vous l'appairez, et (c) la récupération du payload du cœur signé pour le Mode Swarm. Les trois sont désactivés par défaut.
- **Payload Pro signé.** Le moteur du cœur Swarm est signé Ed25519 et vérifié à l'intérieur d'un worker Node avant d'être compilé en RAM — un homme du milieu ne peut pas glisser un scanner malveillant.
- **Workflow de dev standard** — `--remote-debugging-port` est le même flag utilisé par les développeurs d'extensions VS Code et le débogage d'apps Electron.
- **Le patcheur de raccourcis a une portée limitée** — l'auto-fix ne modifie que les fichiers `.lnk` dont le chemin cible contient « Antigravity ».
- **Aucun fichier Antigravity modifié** — cette extension s'exécute entièrement comme une extension VS Code externe. Désinstallez et toute trace disparaît.

**Mon chat Telegram lira-t-il mon code ?**

Seulement ce que *vous* demandez explicitement. `/peek` retourne le texte visible du panneau de l'Agent actif ; `/prompt` y envoie votre message. L'extension ne pousse jamais de manière proactive du code, des diffs, des captures ou de la télémétrie vers Telegram.

---

## Licence

MIT
