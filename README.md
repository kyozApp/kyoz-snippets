# Kyoz Snippets (`kyoz-snippets`)

Colección de snippets de desarrollo para **Zed**, diseñados para el stack
de **SvelteKit**, **Remote Functions** (`$app/server`), **Valibot**,
componentes **Svelte 5** (Runes), **Hono** y TypeScript.

---

## 🚀 Snippets Disponibles

### 📘 TypeScript (`.ts`) - Remote Functions y Validaciones

| Prefijo | Nombre | Descripción |
| :--- | :--- | :--- |
| `kyoz-ts-sv-remote-form` | **Remote Form Function** | Crea una función de formulario remoto (`form(...)`) con `$app/server`, base de datos y refresco de caché. |
| `kyoz-ts-sv-remote-command` | **Remote Command Function** | Crea un comando remoto (`command(...)`) con validación de existencia, mutación y refresco de caché. |
| `kyoz-ts-sv-remote-query` | **Remote Query Functions** | Crea funciones remotas de consulta para listado (`get...List`) y detalle (`get...Details`) validadas con Valibot. |
| `kyoz-ts-sv-validation-form` | **Valibot Form Validation** | Define esquemas de validación de formulario (`Create` y `Update`) con inferencia de tipos `InferOutput`. |
| `kyoz-ts-sv-validation-command` | **Valibot Command Validation** | Define el esquema de validación para un comando remoto (`CommandSchema`) con inferencia de tipos. |
| `kyoz-ts-sv-validation-query` | **Valibot Query Validation** | Define esquemas de validación y respuesta para listado y detalle con tipos `InferOutput`. |

---

### 🍊 Svelte (`.svelte`) - Componentes y Svelte 5

| Prefijo | Nombre | Descripción |
| :--- | :--- | :--- |
| `kyoz-sv-comp-form` | **Update Form Component** | Formulario de actualización que consume Remote Form y Remote Query con validación reactiva. |
| `kyoz-sv-comp-table` | **Table Component** | Tabla de listado que consume Remote Query con `<svelte:boundary>` y estados. |
| `kyoz-sv-comp-button` | **Command Button Component** | Botón reactivo que consume Remote Command con estado de carga y notificaciones. |

---

## 📦 Uso en Zed

### Opción 1: Instalar como extensión local de desarrollo

1. Abre Zed.
2. Abre la paleta de comandos (`Ctrl + Shift + P` en Linux/Windows o `Cmd + Shift + P` en macOS).
3. Ejecuta la acción: `zed: install dev extension`.
4. Selecciona la carpeta de este repositorio (`/home/kyoz/proyectos/kyoz-snippets`).

### Opción 2: Snippets de Usuario nativos

Si prefieres tenerlos globales sin usar el gestor de extensiones:

1. Abre la paleta de comandos en Zed y escribe `snippets: configure snippets`.
2. Pega el contenido de los JSON de `snippets/` en los archivos respectivos de tu configuración.
