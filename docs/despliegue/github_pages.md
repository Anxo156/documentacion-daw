---
sidebar_position: 1
title: Despliegue en GitHub Pages
---

# Despliegue en GitHub Pages

La documentación se genera con **Docusaurus** y se publica como sitio estático en **GitHub Pages**, cumpliendo el requisito RNF-06 (sin servidor propio).

## 1. Configurar `docusaurus.config.js`

Sustituye `TU_USUARIO` por tu usuario de GitHub:

```js
const config = {
  title: 'Ecclesia Primitiva',
  tagline: 'Atlas interactivo de la Iglesia Primitiva',
  url: 'https://TU_USUARIO.github.io',
  baseUrl: '/ecclesia-primitiva/',
  organizationName: 'TU_USUARIO',
  projectName: 'ecclesia-primitiva',
  trailingSlash: false,
  onBrokenLinks: 'throw',
  i18n: { defaultLocale: 'es', locales: ['es'] },

  // Necesario para dibujar los diagramas Mermaid
  markdown: { mermaid: true },
  themes: ['@docusaurus/theme-mermaid'],
};
```

| Campo | Significado |
|---|---|
| `url` | Dominio de GitHub Pages del usuario u organización |
| `baseUrl` | Nombre del repositorio entre barras |
| `organizationName` | Usuario u organización propietaria |
| `projectName` | Nombre del repositorio |

Instala el tema de diagramas:

```bash
npm install @docusaurus/theme-mermaid
```

## 2. Probar en local

```bash
npm run build     # genera la carpeta build/
npm run serve     # sirve build/ en http://localhost:3000/ecclesia-primitiva/
```

Si hay enlaces rotos, la construcción fallará gracias a `onBrokenLinks: 'throw'`.

## 3. Despliegue automático con GitHub Actions

Crea el archivo `.github/workflows/deploy.yml` en la **raíz del repositorio**. Como el sitio está en la carpeta `documentation/`, se indica como directorio de trabajo:

```yaml
name: Desplegar documentación

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: documentation
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
          cache-dependency-path: documentation/package-lock.json
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: documentation/build

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

## 4. Activar Pages en el repositorio

1. Entra en **Settings → Pages** del repositorio.
2. En **Source**, elige **GitHub Actions**.
3. Haz `git push` a la rama `main`.
4. En la pestaña **Actions** comprueba que el flujo termina en verde.

## 5. Resultado

El sitio queda publicado en:

```text
https://TU_USUARIO.github.io/ecclesia-primitiva/
```

## 6. Alternativa manual

Si prefieres no usar Actions, Docusaurus puede publicar en la rama `gh-pages`:

```bash
GIT_USER=TU_USUARIO npm run deploy
```

En ese caso, en **Settings → Pages** elige **Deploy from a branch** y selecciona `gh-pages`.

## 7. Problemas frecuentes

| Síntoma | Causa probable | Solución |
|---|---|---|
| Página en blanco o sin estilos | `baseUrl` incorrecto | Debe ser `/nombre-del-repositorio/` |
| Error 404 en la raíz | Pages no está configurado con GitHub Actions | Revisar Settings → Pages |
| Diagramas como texto | Falta el tema Mermaid | Instalar `@docusaurus/theme-mermaid` y activarlo |
| Falla el build por enlaces | Rutas mal escritas | Corregir los enlaces indicados en el log |
