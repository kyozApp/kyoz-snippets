# Kyoz Snippets (`kyoz-snippets`)

Colección de snippets de desarrollo para **Zed**, diseñados para el stack
de **SvelteKit**, **Remote Functions** (`$app/server`), **Valibot**,
componentes **Svelte 5** (Runes), **Prisma 8**, **Biome**, **Tailwind v4** y TypeScript.

---

## 🚀 Snippets Disponibles

### 📘 TypeScript (`.ts`) - Remote Functions, Validaciones, Entorno y Prisma 8

| Prefijo                         | Ruta recomendada                                  | Descripción                                                  |
| :------------------------------ | :------------------------------------------------ | :----------------------------------------------------------- |
| `kyoz-sv-vite`                  | `vite.config.ts`                                  | Configura Vite con Tailwind v4, Remote Functions y Runes.    |
| `kyoz-sv-env`                   | `src/env.ts`                                      | Variables de entorno tipadas con `defineEnvVars` y Valibot.  |
| `kyoz-sv-remote-form`           | `src/lib/remote/.../*.form.remote.ts`             | Remote Form (`form(...)`) con `$app/server`, DB y refresco.  |
| `kyoz-sv-remote-command`        | `src/lib/remote/.../*.command.remote.ts`          | Remote Command (`command(...)`) con validación y mutación.   |
| `kyoz-sv-remote-query`          | `src/lib/remote/.../*.query.remote.ts`            | Funciones de consulta (`get...List`, `get...Details`).       |
| `kyoz-sv-validation-form`       | `src/lib/validations/.../*.form.validation.ts`    | Esquemas Valibot de formulario (`Create` y `Update`).        |
| `kyoz-sv-validation-command`    | `src/lib/validations/.../*.command.validation.ts` | Esquema Valibot para mutaciones remotas.                     |
| `kyoz-sv-validation-query`      | `src/lib/validations/.../*.query.validation.ts`   | Esquemas Valibot para consultas (List y Detail).             |
| `kyoz-sv-hooks`                 | `src/hooks.server.ts`                             | Hooks SvelteKit con sesiones Prisma y sanitización 500.      |
| `kyoz-sv-service-notifications` | `src/lib/services/notifications.svelte.ts`        | Servicio reactivo de notificaciones (`$state`) para toasts.  |
| `kyoz-prisma-contract`          | `src/prisma/contract.ts`                          | Contract Builder con `Role`, `User`, `Session` y relaciones. |
| `kyoz-prisma-db`                | `src/lib/server/db.ts`                            | Cliente singleton `db` con `postgres<Contract>`.             |
| `kyoz-prisma-config`            | `prisma.config.ts`                                | Configuración CLI de Prisma 8 con `ormConfig`.               |

---

### 🍊 Svelte (`.svelte`) - Componentes UI y Svelte 5

| Prefijo                      | Ruta recomendada                                      | Descripción                                                |
| :--------------------------- | :---------------------------------------------------- | :--------------------------------------------------------- |
| `kyoz-sv-layout-root`        | `src/routes/+layout.svelte`                           | Layout raíz con `layout.css`, `ModeWatcher` y Toasts.      |
| `kyoz-sv-comp-notifications` | `src/lib/components/ui/NotificationsContainer.svelte` | Contenedor de notificaciones con Popover API y Sonner.     |
| `kyoz-sv-comp-form`          | `src/lib/components/.../*Form.svelte`                 | Formulario de actualización reactivo con boundary.         |
| `kyoz-sv-comp-table`         | `src/lib/components/.../*Table.svelte`                | Tabla de listado reactiva con boundary y estados.          |
| `kyoz-sv-comp-button`        | `src/lib/components/.../*Button.svelte`               | Botón reactivo para Remote Command con loading state.      |
| `kyoz-sv-comp-theme-toggle`  | `src/lib/components/ui/ThemeToggle.svelte`            | Botón modo oscuro/claro con `mode-watcher` y Lucide.       |
| `kyoz-sv-comp-modal`         | `src/lib/components/ui/modals/Modal.svelte`           | Modal declarativo apilable con `<dialog>` nativo.          |
| `kyoz-sv-comp-modal-basic`   | `src/lib/components/ui/modals/BasicModal.svelte`      | Modal con cabecera, botón cerrar y contenedor scrolleable. |

---

### 📄 JSON (`.json`) - Configuraciones del Proyecto

| Prefijo            | Ruta recomendada     | Descripción                                                 |
| :----------------- | :------------------- | :---------------------------------------------------------- |
| `kyoz-sv-biome`    | `biome.json`         | Configuración de Biome con tabs, linter y orden de imports. |
| `kyoz-sv-zed`      | `.zed/settings.json` | Configuración de workspace de Zed con Biome y Tailwind LSP. |
| `kyoz-sv-tsconfig` | `tsconfig.json`      | Configuración TypeScript de SvelteKit con module preserve.  |

---

### 🎨 CSS (`.css`) - Estilos Globales y Tailwind v4

| Prefijo       | Ruta recomendada        | Descripción                                                     |
| :------------ | :---------------------- | :-------------------------------------------------------------- |
| `kyoz-sv-css` | `src/routes/layout.css` | Estilos globales Tailwind v4 con Inter, z-index y tooltips CSS. |

---

### 🐳 YAML (`.yaml`) - Contenedores e Infraestructura

| Prefijo                 | Ruta recomendada | Descripción                                            |
| :---------------------- | :--------------- | :----------------------------------------------------- |
| `kyoz-compose-postgres` | `compose.yaml`   | Servicio PostgreSQL 18 Alpine con volumen persistente. |

---

### 📝 Markdown (`.md`) - Guías y Flujo de Inicialización

| Prefijo         | Ruta recomendada | Descripción                                                     |
| :-------------- | :--------------- | :-------------------------------------------------------------- |
| `kyoz-sv-setup` | `*.md`           | Runbook completo paso a paso con comandos y snippets del stack. |

---

## 📦 Uso en Zed

### Opción 1: Snippets de Usuario nativos (Recomendada)

1. Abre la paleta de comandos en Zed (`Ctrl + Shift + P`).
2. Escribe `snippets: configure snippets`.
3. Selecciona el lenguaje (`svelte`, `typescript`, `json`, `css`, `yaml` o `markdown`).
4. Pega el contenido de los JSON de `snippets/` en los archivos respectivos de tu configuración.

### Opción 2: Instalar como extensión local de desarrollo

1. Abre Zed.
2. Abre la paleta de comandos (`Ctrl + Shift + P` en Linux/Windows o `Cmd + Shift + P` en macOS).
3. Ejecuta la acción: `zed: install dev extension`.
4. Selecciona la carpeta de este repositorio.
