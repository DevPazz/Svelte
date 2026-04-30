# bparfum

Pequeña SPA en Svelte para mostrar catálogo de decants.

## Descripción

Interfaz cliente estática construida con Svelte + Vite. No hay backend incluido en este repositorio; todo el contenido está servido desde la carpeta pública (`/public`) y el bundle generado por Vite.

## Requisitos

- Node.js 18+ (o LTS compatible)
- npm

## Instalación y ejecución

```bash
npm install
npm run dev    # desarrollo (Vite)
npm run build  # build de producción
npm run preview # previsualizar build
```

## Seguridad y despliegue (recomendaciones rápidas)

- Ejecuta `npm audit` y actualiza dependencias si se reportan vulnerabilidades.
- Compila para producción (`npm run build`) y sirve los archivos estáticos por HTTPS.
- No publiques source maps en producción.
- Configura cabeceras de seguridad en el servidor/CDN:
	- `Content-Security-Policy` (bloquear `unsafe-inline`, usar nonces/hashes para scripts cuando haga falta)
	- `Strict-Transport-Security` (HSTS)
	- `X-Frame-Options: DENY` o `SAMEORIGIN`
	- `Referrer-Policy` y `X-Content-Type-Options: nosniff`
- No incluyas secretos ni credenciales en el repositorio; usa variables de entorno o servicios de secretos en el servidor.
- Si más adelante añades uploads, valida tipos y tamaños y escapa nombres de fichero.

## Estructura principal

- `index.html` - entrada estática
- `src/` - código fuente Svelte
	- `src/App.svelte` - UI principal
	- `src/main.js` - montaje de la app
- `public/` - assets públicos (imágenes, video)
- `vite.config.js`, `svelte.config.js` - configuración de build

## Siguientes pasos recomendados

- Ejecutar `npm audit` y compartir resultados si quieres que los revise.
- Añadir un `LICENSE` si vas a publicar el repo.

---

Si quieres, puedo añadir una sección de despliegue (ej. configuración para Netlify, Vercel, o un servidor estático) o ejecutar `npm audit` aquí y revisar los hallazgos.
