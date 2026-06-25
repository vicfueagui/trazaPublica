# Guía para publicar cambios

Esta guía explica cómo hacer que los cambios locales de la landing **Traza Pública** se reflejen en GitHub y Cloudflare Pages.

## Flujo normal

1. Entra a la carpeta del proyecto:

```bash
cd /Users/admin/Documents/landingPage_tramites/traza-publica-landing
```

2. Revisa qué archivos cambiaron:

```bash
git status -sb
```

3. Prueba el sitio localmente con Docker:

```bash
docker compose up --build
```

Abre:

```text
http://localhost:4321
```

4. En otra terminal, valida el build de producción:

```bash
docker compose exec -T traza-publica-landing npm run build
```

5. Agrega los cambios a git:

```bash
git add .
```

6. Crea un commit con un mensaje claro:

```bash
git commit -m "describe brevemente el cambio"
```

Ejemplos:

```bash
git commit -m "update contact information"
git commit -m "update profile name"
git commit -m "replace dashboard mockups"
git commit -m "adjust landing copy"
```

7. Sube los cambios a GitHub:

```bash
git push
```

8. Cloudflare Pages desplegará automáticamente los cambios desde la rama `main`.

URL pública actual:

```text
https://trazapublica.pages.dev/
```

## Cómo confirmar que Cloudflare ya publicó

1. Entra a Cloudflare.
2. Ve a **Workers & Pages**.
3. Abre el proyecto `trazapublica`.
4. Revisa la sección **Deployments**.
5. Confirma que el último commit aparezca como exitoso.
6. Abre la landing en una ventana privada o recarga sin caché.

## Qué archivos no se deben subir manualmente

Estos archivos o carpetas se generan automáticamente y están ignorados por `.gitignore`:

```text
node_modules
dist
.astro
```

No necesitas subir `dist` a GitHub. Cloudflare ejecuta `npm run build` y genera `dist` durante el despliegue.

## Si aparece un error de Astro en Docker

Si ves este error:

```text
Another astro dev server is already running
```

Ejecuta:

```bash
rm -f .astro/dev.json
docker compose up --build
```

El proyecto también tiene un script Docker que limpia ese archivo automáticamente:

```bash
npm run dev:docker
```

## Datos importantes del despliegue

Repositorio:

```text
https://github.com/vicfueagui/trazaPublica
```

Rama de producción:

```text
main
```

Configuración de Cloudflare Pages:

```text
Framework preset: Astro
Build command: npm run build
Output directory: dist
NODE_VERSION: 22.12.0
```

## Checklist rápido antes de publicar

- Revisar que el sitio cargue localmente.
- Revisar que WhatsApp, correo, Calendly y formulario sigan funcionando.
- Ejecutar build sin errores.
- Revisar `git status -sb`.
- Hacer commit.
- Hacer push.
- Confirmar despliegue exitoso en Cloudflare Pages.
