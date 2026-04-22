diff --git a/planner-src/README.md b/planner-src/README.md
index 7b9a37504d29b8655e69473abfb6a4a1a320f471..1e14049c2c0c8f50f5655bb93178bf453e445223 100644
--- a/planner-src/README.md
+++ b/planner-src/README.md
@@ -1,48 +1,63 @@
 # Planner AT · Fontes editáveis
 
 Versão editável do `Planner-offline1.html`. Os módulos estão separados em arquivos individuais — edite qualquer `.js` ou `.css` e recarregue o browser.
 
 ## Como rodar
 
 Por causa do `type="text/babel"` com `src=`, **é necessário um servidor HTTP local** (Chrome bloqueia XHR de `file://`).
 
 ### Opção 1 — Python (tem em qualquer Mac/Linux, Windows com Python instalado)
 ```bash
 cd planner-src
 python3 -m http.server 8000
 ```
 Abra http://localhost:8000
 
 ### Opção 2 — Node
 ```bash
 npx serve planner-src
 ```
 
 ### Opção 3 — VSCode
 Instale a extensão **Live Server** → clique direito em `index.html` → "Open with Live Server".
 
+
+## Publicar no GitHub Pages
+
+Este repositório já possui workflow para publicar automaticamente a pasta `planner-src/` no GitHub Pages (`.github/workflows/deploy-pages.yml`).
+
+### Passo a passo
+
+1. Faça push para a branch `main`.
+2. No GitHub, vá em **Settings → Pages** e em **Build and deployment** selecione **Source: GitHub Actions**.
+3. Aguarde o workflow **"Deploy planner-src to GitHub Pages"** finalizar (aba **Actions**).
+4. A URL final normalmente fica:
+   - `https://<seu-usuario>.github.io/<seu-repo>/`
+
+> Observação: como o build publica `planner-src` como raiz do site, o `index.html` já abre direto no link acima.
+
 ## Estrutura
 
 ```
 planner-src/
 ├── index.html              # Carrega tudo em ordem
 ├── src/
 │   ├── style.css           # Todo o CSS
 │   ├── 01-constants.js     # STATUSES, PRIORITIES, TEAM_SEED, PROJECTS_SEED, SEED_TASKS
 │   ├── 02-icons.js         # Componente <Icon/> + <Avatar/> + <BrandMark/>
 │   ├── 03-hooks.js         # useHistory, useHotkeys, ToastHost, HotkeysHelp
 │   ├── 04-kanban.js        # KanbanView, KanbanCard
 │   ├── 05-timeline.js      # TimelineView (Gantt com drag)
 │   ├── 06-task-modal.js    # TaskModal (edição de tarefa)
 │   ├── 07-notifications.js # NotifBell, ViewsMenu, IntegrationModal (.ics, webhook)
 │   ├── 08-sync.js          # SyncPanel, useAutoFileSync, import/export JSON
 │   ├── 09-settings.js      # SettingsPanel (equipe/projetos)
 │   └── 10-app.js           # App principal + render raiz
 ├── vendor/
 │   ├── react.development.js
 │   ├── react-dom.development.js
 │   └── babel.min.js         # Compila JSX em runtime
 └── fonts/                   # Inter Tight + JetBrains Mono (woff2)
 ```
 
 ## Ordem de carregamento (importa!)
