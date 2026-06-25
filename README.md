# Traza Pública Landing

Landing page estática para validar comercialmente Traza Pública: un servicio y sistema para seguimiento de trámites, gestión de expedientes, trazabilidad documental, responsables, estatus, indicadores y reportes para áreas jurídicas, administrativas y públicas.

El proyecto está construido con Astro, CSS moderno y HTML semántico. No incluye backend, base de datos, login, panel administrativo ni páginas internas.

## Requisitos

- Node.js 22.12.0 LTS o superior
- npm
- Docker Desktop, opcional para correr con contenedores

## Instalar dependencias

```bash
npm install
```

## Correr localmente sin Docker

```bash
npm run dev
```

Astro levantará el sitio normalmente en:

```bash
http://localhost:4321
```

## Correr con Docker Desktop

Desde la raíz del proyecto:

```bash
docker compose up --build
```

Abrir:

```bash
http://localhost:4321
```

Para detener el contenedor:

```bash
docker compose down
```

Si Astro muestra `Another astro dev server is already running`, limpia el estado temporal y reinicia:

```bash
rm -f .astro/dev.json
docker compose up --build
```

## Crear build de producción

```bash
npm run build
```

El sitio estático queda generado en:

```bash
dist
```

También puedes probar el build localmente con:

```bash
npm run preview
```

## Desplegar en Cloudflare Pages

1. Sube este proyecto a un repositorio de GitHub o GitLab.
2. En Cloudflare, entra a Workers & Pages.
3. Crea un nuevo proyecto de Pages y conecta el repositorio.
4. Configura:
   - Framework preset: Astro
   - Build command: `npm run build`
   - Output directory: `dist`
   - Environment variable recomendada: `NODE_VERSION=22.12.0`
5. Guarda y ejecuta el despliegue.
6. Cuando tengas dominio final, actualiza `site` en `astro.config.mjs` y los metadatos de `src/pages/index.astro`.

## Datos que debes revisar antes de publicar

### Ya configurado

- WhatsApp: `https://wa.me/529991445755`.
- Calendly: `https://calendly.com/seuninversordeltiempo`.
- Correo: `seuninversordeltiempo@gmail.com`.
- Logo y favicon: archivos en `public/brand/`, `public/favicon.png` y `public/apple-touch-icon.png`.
- Imagen profesional: `public/profile/victor-fuente.webp`.
- Mockups del sistema: capturas en `public/mockups/`.

### Pendiente o por confirmar

- Dominio: si el dominio final será `https://trazapublica.com`, no hay que cambiar nada. Si será otro, actualiza `astro.config.mjs` y `src/pages/index.astro`.
- Formulario: configurado con Formspree en `https://formspree.io/f/xdarepab`.
- Metadatos SEO: revisa title, description, Open Graph, Twitter Card y JSON-LD antes del dominio final.

### Cómo conectar el formulario

El formulario visible de la página usa Formspree porque el sitio no tiene backend.

Configuración actual:

- Proyecto: `Traza Pública`.
- Formulario: `Contacto landing Traza Pública`.
- Endpoint: `https://formspree.io/f/xdarepab`.

Después de publicar, haz una prueba enviando el formulario desde la landing. Formspree puede pedir confirmación del primer envío o ajustes antispam desde su panel.

## Estructura principal

```text
src/pages/index.astro
src/styles/global.css
public/favicon.png
public/apple-touch-icon.png
public/og-image.svg
public/brand/
public/mockups/
public/profile/
Dockerfile
docker-compose.yml
```

## Notas

- La página no representa a ninguna dependencia pública.
- No se incluyen clientes, certificaciones, testimonios ni alianzas ficticias.
- Los mockups del sistema usan datos ficticios y placeholders editables.
