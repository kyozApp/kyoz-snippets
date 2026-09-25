# Kyoz Snippets (`kyoz-snippets`)

Colección de snippets de alta velocidad para el editor **Zed**, diseñados para el
desarrollo diario de entidades, lógica de negocio y componentes CRUD en **SvelteKit**,
**Svelte 5 (Runes)**, **Remote Functions (`$app/server`)** y **Valibot**.

> [!TIP]
> **Inicialización de Proyectos:** La configuración base de herramientas (Tailwind v4,
> Biome, Paraglide, temas, modales y toasts) ya viene resuelta en la plantilla oficial.
> Para crear un nuevo proyecto ejecuta:
>
> ```bash
> pnpm dlx degit kyozApp/template-sveltekit mi-proyecto
> ```

---

## 🚀 Snippets Disponibles

### 📘 TypeScript (`.ts`) - Validaciones con Valibot

Los esquemas de validación utilizan el estándar de contratos de entrada (`body`, `params`,
`query`) y salida (`response`).

#### 1. Estructuras Completas de Entidad (CRUD Rápido)

| Prefijo                | Ruta recomendada                                  | Descripción                                                                          |
| :--------------------- | :------------------------------------------------ | :----------------------------------------------------------------------------------- |
| `kyoz-valibot-form`    | `src/lib/validations/.../*.form.validation.ts`    | Esquemas Valibot para creación y actualización de formularios (`Create` y `Update`). |
| `kyoz-valibot-command` | `src/lib/validations/.../*.command.validation.ts` | Esquema Valibot para validación de parámetros en mutaciones remotas (`Command`).     |
| `kyoz-valibot-query`   | `src/lib/validations/.../*.query.validation.ts`   | Esquemas completos para lista (con `query` y `response`) y detalle (`params`).       |

#### 2. Micro-Snippets de Bloques Modulares

Para construir o extender esquemas personalizados:

| Prefijo                       | Bloque Generado                   | Propósito                                              |
| :---------------------------- | :-------------------------------- | :----------------------------------------------------- |
| `kyoz-valibot-block-body`     | `body: v.object({ ... })`         | Contrato de entrada de datos con tipo inferido `Body`. |
| `kyoz-valibot-block-params`   | `params: v.object({ id })`        | Parámetros identificadores de ruta o URL.              |
| `kyoz-valibot-block-query`    | `query: v.object({ page... })`    | Filtros URL para paginación, límites y búsqueda.       |
| `kyoz-valibot-block-response` | `response: v.pipe(..., readonly)` | Salida tipada e inmutable de consultas backend.        |

#### 3. Micro-Snippets Atómicos de Campo (Entrada vs Salida)

##### 📥 Entrada (`in`) — Formularios y Peticiones HTTP

| Prefijo                   | Tipo y Parseo            | Descripción                                          |
| :------------------------ | :----------------------- | :--------------------------------------------------- |
| `kyoz-valibot-in-string`  | `string`                 | Limpieza con `v.trim()`, `v.minLength()`, max limit. |
| `kyoz-valibot-in-number`  | `string` → `number`      | Parseo desde string con `v.toNumber()` y `minValue`. |
| `kyoz-valibot-in-boolean` | `string` → `boolean`     | Parseo booleano con `v.parseBoolean()` (switches).   |
| `kyoz-valibot-in-date`    | `string` (ISO Timestamp) | Validación de fecha con `v.isoTimestamp()`.          |
| `kyoz-valibot-in-uuid`    | `string` (UUID v4)       | Validación de llaves foráneas con `v.uuid()`.        |

##### 📤 Salida (`out`) — Respuestas desde DB / PostgreSQL

| Prefijo                    | Tipo Nativo DB              | Descripción                                        |
| :------------------------- | :-------------------------- | :------------------------------------------------- |
| `kyoz-valibot-out-string`  | `v.string()`                | Campo de texto simple de retorno.                  |
| `kyoz-valibot-out-number`  | `v.number()`                | Valor numérico nativo desde PostgreSQL.            |
| `kyoz-valibot-out-boolean` | `v.boolean()`               | Booleano nativo desde PostgreSQL.                  |
| `kyoz-valibot-out-date`    | `v.pipe(string, timestamp)` | Fecha ISO timestamp devuelta por la base de datos. |
| `kyoz-valibot-out-uuid`    | `v.pipe(string, uuid)`      | Identificador único UUID validado.                 |

---

### ⚡ TypeScript (`.ts`) - SvelteKit Remote Functions

Snippets específicos de SvelteKit para la capa de servidor RPC (`$app/server`):

| Prefijo                  | Ruta recomendada                         | Descripción                                                                     |
| :----------------------- | :--------------------------------------- | :------------------------------------------------------------------------------ |
| `kyoz-sv-remote-form`    | `src/lib/remote/.../*.form.remote.ts`    | Remote Form (`form(...)`) con `$app/server`, base de datos y refresco reactivo. |
| `kyoz-sv-remote-command` | `src/lib/remote/.../*.command.remote.ts` | Remote Command (`command(...)`) con validación y ejecución de mutaciones.       |
| `kyoz-sv-remote-query`   | `src/lib/remote/.../*.query.remote.ts`   | Remote Query (`get...List`, `get...Details`) para lectura y carga asíncrona.    |

---

### 🍊 Svelte (`.svelte`) - Componentes UI de Dominio (Svelte 5 Runes)

Snippets de componentes de interfaz que consumen directamente las Remote Functions:

| Prefijo               | Ruta recomendada                        | Descripción                                                                         |
| :-------------------- | :-------------------------------------- | :---------------------------------------------------------------------------------- |
| `kyoz-sv-comp-form`   | `src/lib/components/.../*Form.svelte`   | Formulario reactivo conectado a Remote Form con boundary, estado pending y toasts.  |
| `kyoz-sv-comp-table`  | `src/lib/components/.../*Table.svelte`  | Tabla reactiva conectada a Remote Query con boundary, loader y buscador reactivo.   |
| `kyoz-sv-comp-button` | `src/lib/components/.../*Button.svelte` | Botón reactivo para Remote Command con spinner de carga y feedback de notificación. |

---

## 🔄 Flujo de Trabajo para Nuevas Entidades

Para cada nueva entidad de tu sistema (ej: `cliente`, `producto`, `orden`):

1. **Validaciones (`src/lib/validations/cliente/`):**
   - `cliente.form.validation.ts` → `kyoz-valibot-form` (y campos con `kyoz-valibot-in-*`)
   - `cliente.command.validation.ts` → `kyoz-valibot-command`
   - `cliente.query.validation.ts` → `kyoz-valibot-query` (y campos con `kyoz-valibot-out-*`)

2. **Remote Functions (`src/lib/remote/cliente/`):**
   - `cliente.form.remote.ts` → `kyoz-sv-remote-form`
   - `cliente.command.remote.ts` → `kyoz-sv-remote-command`
   - `cliente.query.remote.ts` → `kyoz-sv-remote-query`

3. **Componentes UI (`src/lib/components/cliente/`):**
   - `ClienteForm.svelte` → `kyoz-sv-comp-form`
   - `ClienteTable.svelte` → `kyoz-sv-comp-table`
   - `EliminarClienteButton.svelte` → `kyoz-sv-comp-button`

---

## 📦 Instalación y Uso en Zed

### Como extensión local de desarrollo (Recomendado)

1. Abre Zed.
2. Abre la paleta de comandos (`Ctrl + Shift + P` en Linux/Windows o `Cmd + Shift + P` en macOS).
3. Ejecuta la acción: `zed: install dev extension`.
4. Selecciona la carpeta de este repositorio (`~/proyectos/kyoz-snippets`).
