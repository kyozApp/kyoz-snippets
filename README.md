# Kyoz Snippets (`kyoz-snippets`)

Colección de snippets de alta velocidad para el editor **Zed**, diseñados para el desarrollo
diario de APIs y aplicaciones web en **Hono** (OpenAPI / Swagger), **SvelteKit** (Svelte 5 Runes,
Remote Functions `$app/server`), y esquemas de validación desacoplados con **Valibot**.

> [!TIP]
> **Plantillas Oficiales de Desarrollo:**
>
> ```bash
> # Para APIs backend con Hono (OpenAPI, Prisma, Valibot):
> pnpm dlx degit kyozApp/template-hono mi-api
>
> # Para aplicaciones web con SvelteKit (Runes, Remote Functions, Tailwind v4):
> pnpm dlx degit kyozApp/template-sveltekit mi-app
> ```

---

## 🚀 Snippets Disponibles

### 📘 TypeScript (`.ts`) - Validaciones con Valibot

Los esquemas de validación utilizan el estándar de contratos de entrada (`body`, `params`,
`query`) y salida (`response`).

#### 1. Estructuras Completas de Entidad para SvelteKit

| Prefijo                | Ruta recomendada                                  | Descripción                                                                |
| :--------------------- | :------------------------------------------------ | :------------------------------------------------------------------------- |
| `kyoz-valibot-form`    | `src/lib/validations/.../*.form.validation.ts`    | Esquemas Valibot para creación y actualización (`Create` y `Update`).      |
| `kyoz-valibot-command` | `src/lib/validations/.../*.command.validation.ts` | Esquemas para mutaciones atómicas (`ToggleStatus` y `Delete` soft delete). |
| `kyoz-valibot-query`   | `src/lib/validations/.../*.query.validation.ts`   | Esquemas completos para lista (`query` + `response`) y detalle (`params`). |

#### 2. Micro-Snippets de Bloques Modulares (Universales)

Para construir o extender esquemas personalizados en Hono o SvelteKit:

| Prefijo                       | Bloque Generado                   | Propósito                                              |
| :---------------------------- | :-------------------------------- | :----------------------------------------------------- |
| `kyoz-valibot-block-body`     | `body: v.object({ ... })`         | Contrato de entrada de datos con tipo inferido `Body`. |
| `kyoz-valibot-block-params`   | `params: v.object({ id })`        | Parámetros identificadores de ruta o URL (`id` UUID).  |
| `kyoz-valibot-block-query`    | `query: v.object({ page... })`    | Filtros URL para paginación, límites y búsqueda.       |
| `kyoz-valibot-block-response` | `response: v.pipe(..., readonly)` | Salida tipada e inmutable de consultas backend.        |

#### 3. Micro-Snippets Atómicos de Campo (Entrada vs Salida)

##### 📥 Entrada (`in`) — Formularios y Peticiones HTTP

| Prefijo                           | Tipo y Parseo              | Descripción                                                            |
| :-------------------------------- | :------------------------- | :--------------------------------------------------------------------- |
| `kyoz-valibot-in-string`          | `string`                   | Limpieza con `v.trim()`, `v.minLength()`, max limit.                   |
| `kyoz-valibot-in-number`          | `string` → `number`        | Parseo desde string con `v.toNumber()` y `minValue`.                   |
| `kyoz-valibot-in-boolean`         | `string` → `boolean`       | Parseo booleano con `v.parseBoolean()` (switches/checkboxes).          |
| `kyoz-valibot-in-date`            | `string` (ISO Timestamp)   | Validación de fecha con `v.isoTimestamp()`.                            |
| `kyoz-valibot-in-uuid`            | `string` (UUID v4)         | Validación de llaves foráneas con `v.uuid()`.                          |
| `kyoz-valibot-in-email`           | `string` (Email)           | Parseo con `v.trim()`, `v.toLowerCase()` y `v.email()`.                |
| `kyoz-valibot-in-password`        | `string` (Password)        | Contraseña obligatoria (mínimo 8 caracteres) para creación.            |
| `kyoz-valibot-in-password-update` | `string` (Password)        | Contraseña opcional con transformación de vacío a `undefined`.         |
| `kyoz-valibot-in-select-uuid`     | `string` (Select FK)       | Selector de llave foránea UUID con valor por defecto `""`.             |
| `kyoz-valibot-in-select-picklist` | `string` (Select Picklist) | Selector de opciones fijas con `v.picklist()` y default `""`.          |
| `kyoz-valibot-in-digits`          | `string` (Dígitos exactos) | Campo de longitud numérica fija (DNI 8 dígitos, RUC 11 dígitos, etc.). |

##### 📤 Salida (`out`) — Respuestas desde DB / PostgreSQL

| Prefijo                            | Tipo Nativo DB              | Descripción                                                   |
| :--------------------------------- | :-------------------------- | :------------------------------------------------------------ |
| `kyoz-valibot-out-string`          | `v.string()`                | Campo de texto simple de retorno.                             |
| `kyoz-valibot-out-number`          | `v.number()`                | Valor numérico nativo desde PostgreSQL.                       |
| `kyoz-valibot-out-boolean`         | `v.boolean()`               | Booleano nativo desde PostgreSQL.                             |
| `kyoz-valibot-out-date`            | `v.pipe(string, timestamp)` | Fecha ISO timestamp devuelta por la base de datos.            |
| `kyoz-valibot-out-uuid`            | `v.pipe(string, uuid)`      | Identificador único UUID validado.                            |
| `kyoz-valibot-out-nullable-string` | `v.nullable(v.string())`    | Campo de texto que admite `null`.                             |
| `kyoz-valibot-out-nullish-string`  | `v.nullish(v.string())`     | Campo de texto que admite `null` o `undefined` (`deletedAt`). |

---

### 🔥 TypeScript (`.ts`) - Hono Backend (OpenAPI / Swagger)

Snippets para el desarrollo modular de APIs con **Hono**, **hono-openapi** y **Prisma**:

| Prefijo                            | Ruta recomendada                  | Descripción                                                                                                |
| :--------------------------------- | :-------------------------------- | :--------------------------------------------------------------------------------------------------------- |
| `kyoz-hono-valibot-module`         | `src/modules/.../*.validation.ts` | Módulo completo de validación Hono (`QUERIES` + `COMMANDS`) con OpenAPI.                                   |
| `kyoz-hono-valibot-query-module`   | `src/modules/.../*.validation.ts` | Sección solo de consultas (`list` y `detail`) con metadatos OpenAPI.                                       |
| `kyoz-hono-valibot-command-module` | `src/modules/.../*.validation.ts` | Sección solo de mutaciones (`create`, `update`, `delete`, `toggleStatus`).                                 |
| `kyoz-hono-router`                 | `src/modules/.../*.router.ts`     | Router Hono completo con `describeRoute`, `resolver`, `validator` y 6 endpoints.                           |
| `kyoz-hono-service`                | `src/modules/.../*.service.ts`    | Clase de servicio con métodos estáticos `list`, `findById`, `create`, `update`, `delete` y `toggleStatus`. |
| `kyoz-hono-valibot-field-openapi`  | `src/modules/.../*.validation.ts` | Micro-snippet de campo con `v.description()` y `v.examples()` para Swagger.                                |

---

### ⚡ TypeScript (`.ts`) - SvelteKit Remote Functions

Snippets específicos de SvelteKit para la capa de servidor RPC (`$app/server`):

| Prefijo                  | Ruta recomendada                         | Descripción                                                                             |
| :----------------------- | :--------------------------------------- | :-------------------------------------------------------------------------------------- |
| `kyoz-sv-remote-form`    | `src/lib/remote/.../*.form.remote.ts`    | Remote Form (`form(...)`) con `create` y `update`, base de datos y refresco reactivo.   |
| `kyoz-sv-remote-command` | `src/lib/remote/.../*.command.remote.ts` | Remote Command (`command(...)`) para `toggleStatus` y `delete` con refresco de queries. |
| `kyoz-sv-remote-query`   | `src/lib/remote/.../*.query.remote.ts`   | Remote Query (`get...List`, `get...Details`) para lectura y carga asíncrona.            |

---

### 🍊 Svelte (`.svelte`) - Componentes UI de Dominio (Svelte 5 Runes)

Snippets de componentes de interfaz que consumen directamente las Remote Functions:

| Prefijo               | Ruta recomendada                        | Descripción                                                                         |
| :-------------------- | :-------------------------------------- | :---------------------------------------------------------------------------------- |
| `kyoz-sv-comp-form`   | `src/lib/components/.../*Form.svelte`   | Formulario reactivo conectado a Remote Form con boundary, estado pending y toasts.  |
| `kyoz-sv-comp-table`  | `src/lib/components/.../*Table.svelte`  | Tabla reactiva conectada a Remote Query con boundary, loader y buscador reactivo.   |
| `kyoz-sv-comp-button` | `src/lib/components/.../*Button.svelte` | Botón reactivo para Remote Command con spinner de carga y feedback de notificación. |

---

## 🔄 Flujos de Trabajo Recomendados

### 1. En Hono API (Crear nuevo recurso o módulo)

Para crear un módulo backend (ej: `producto`):

1. **Validaciones:** `src/modules/producto/producto.validation.ts` → `kyoz-hono-valibot-module`
2. **Servicio:** `src/modules/producto/producto.service.ts` → `kyoz-hono-service`
3. **Controlador / Router:** `src/modules/producto/producto.router.ts` → `kyoz-hono-router`
4. **Registro:** Montar `productoRouter` en `src/routes/index.ts`.

### 2. En SvelteKit (Crear nueva entidad full-stack)

Para crear una entidad completa en la aplicación web (ej: `cliente`):

1. **Validaciones (`src/lib/validations/cliente/`):**
   - `cliente.query.validation.ts` → `kyoz-valibot-query` (y campos con `kyoz-valibot-out-*`)
   - `cliente.form.validation.ts` → `kyoz-valibot-form` (y campos con `kyoz-valibot-in-*`)
   - `cliente.command.validation.ts` → `kyoz-valibot-command`

2. **Remote Functions (`src/lib/remote/cliente/`):**
   - `cliente.query.remote.ts` → `kyoz-sv-remote-query`
   - `cliente.form.remote.ts` → `kyoz-sv-remote-form`
   - `cliente.command.remote.ts` → `kyoz-sv-remote-command`

3. **Componentes UI (`src/lib/components/cliente/`):**
   - `ClienteTable.svelte` → `kyoz-sv-comp-table`
   - `ClienteForm.svelte` → `kyoz-sv-comp-form`
   - `EliminarClienteButton.svelte` → `kyoz-sv-comp-button`

---

## 📦 Instalación y Uso en Zed

### Como extensión local de desarrollo (Recomendado)

1. Abre el editor Zed.
2. Abre la paleta de comandos (`Ctrl + Shift + P` en Linux/Windows o `Cmd + Shift + P` en macOS).
3. Ejecuta la acción: `zed: install dev extension`.
4. Selecciona la carpeta de este repositorio (`~/proyectos/kyoz-snippets`).
