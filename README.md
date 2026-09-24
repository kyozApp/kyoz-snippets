# Kyoz Snippets (`kyoz-snippets`)

Colección de snippets de desarrollo para **Zed**, diseñados para el stack
de **SvelteKit**, **Remote Functions** (`$app/server`), **Valibot**,
componentes **Svelte 5** (Runes), **Prisma 8**, **Biome**, **Hono** y TypeScript.

---

## 🚀 Snippets Disponibles

### 📘 TypeScript (`.ts`) - Remote Functions, Validaciones y Prisma 8

| Prefijo                      | Nombre                         | Descripción                                                                                                       |
| :--------------------------- | :----------------------------- | :---------------------------------------------------------------------------------------------------------------- |
| `kyoz-sv-remote-form`        | **Remote Form Function**       | Crea una función de formulario remoto (`form(...)`) con `$app/server`, base de datos y refresco de caché.         |
| `kyoz-sv-remote-command`     | **Remote Command Function**    | Crea un comando remoto (`command(...)`) con validación de existencia, mutación y refresco de caché.               |
| `kyoz-sv-remote-query`       | **Remote Query Functions**     | Crea funciones remotas de consulta para listado (`get...List`) y detalle (`get...Details`) validadas con Valibot. |
| `kyoz-sv-validation-form`    | **Valibot Form Validation**    | Define esquemas de validación de formulario (`Create` y `Update`) con inferencia de tipos `InferOutput`.          |
| `kyoz-sv-validation-command` | **Valibot Command Validation** | Define el esquema de validación para un comando remoto (`CommandSchema`) con inferencia de tipos.                 |
| `kyoz-sv-validation-query`   | **Valibot Query Validation**   | Define esquemas de validación y respuesta para listado y detalle con tipos `InferOutput`.                         |
| `kyoz-prisma-contract`       | **Prisma 8 Base Contract**     | Estructura base de Contract Builder con modelos `User`, `Session` y enum `Role`.                                  |
| `kyoz-prisma-db`             | **Prisma 8 Singleton DB**      | Inicialización del cliente singleton `db` con `postgres<Contract>` y runtime de Prisma 8.                         |

---

### 🍊 Svelte (`.svelte`) - Componentes y Svelte 5

| Prefijo               | Nombre                       | Descripción                                                                                 |
| :-------------------- | :--------------------------- | :------------------------------------------------------------------------------------------ |
| `kyoz-sv-comp-form`   | **Update Form Component**    | Formulario de actualización que consume Remote Form y Remote Query con validación reactiva. |
| `kyoz-sv-comp-table`  | **Table Component**          | Tabla de listado que consume Remote Query con `<svelte:boundary>` y estados.                |
| `kyoz-sv-comp-button` | **Command Button Component** | Botón reactivo que consume Remote Command con estado de carga y notificaciones.             |

---

### 📄 JSON (`.json`) - Configuraciones del Proyecto

| Prefijo         | Nombre                         | Descripción                                                                                      |
| :-------------- | :----------------------------- | :----------------------------------------------------------------------------------------------- |
| `kyoz-sv-biome` | **Biome Configuration**        | Configuración documentada de Biome (recomendada para `biome.jsonc`) con tabs, linter y Tailwind. |
| `kyoz-sv-zed`   | **Zed Settings Configuration** | Configuración completa de `.zed/settings.json` con tabs, Biome como formateador y Tailwind LSP.  |

> [!NOTE]
> `kyoz-sv-biome` incluye comentarios detallados explicativos en cada sección. Se recomienda
> usar el archivo con el nombre `biome.jsonc` para que Biome y tu linter admitan comentarios.

---

## 📦 Uso en Zed

### Opción 1: Snippets de Usuario nativos (Recomendada)

1. Abre la paleta de comandos en Zed (`Ctrl + Shift + P`).
2. Escribe `snippets: configure snippets`.
3. Selecciona el lenguaje (`svelte`, `typescript` o `json`).
4. Pega el contenido de los JSON de `snippets/` en los archivos respectivos de tu configuración.

### Opción 2: Instalar como extensión local de desarrollo

1. Abre Zed.
2. Abre la paleta de comandos (`Ctrl + Shift + P` en Linux/Windows o `Cmd + Shift + P` en macOS).
3. Ejecuta la acción: `zed: install dev extension`.
4. Selecciona la carpeta de este repositorio.
