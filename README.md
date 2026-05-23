# PROCESADORA MONEGRO MC - GitHub Pages

Esta carpeta contiene la versión web lista para subir a GitHub Pages, pero ahora funciona en modo conectado al backend. Ya no incluye la copia pesada de base de datos en archivos JSON.

## Que incluye

- `index.html`
- `404.html`
- `.nojekyll`
- `assets`
- `github-live-config.json`

## Que ya no debe incluir

No subas ni vuelvas a crear estas carpetas dentro de `git-hub page`:

```txt
data
uploads
```

La carpeta `data` era una copia estática de PostgreSQL para demo sin backend. Esa copia puede hacer pesada la página y provocar congelamientos si el navegador intenta cargar demasiada información.

La carpeta `uploads` tampoco debe ir en el código. Las imágenes deben viajar por la API y guardarse en la base de datos o en el almacenamiento configurado, no como archivos versionados dentro del frontend.

## Regenerar esta carpeta

Desde la carpeta principal de la app:

```cmd
npm run github:prepare
```

Ese comando compila el frontend con:

```txt
VITE_STATIC_DEMO=0
VITE_API_URL=https://procesadora-api-363002432431.us-central1.run.app/api
```

Si cambias el backend de Cloud Run, define `GITHUB_API_URL` antes de regenerar.

Ejemplo:

```powershell
$env:GITHUB_API_URL="https://TU-BACKEND-PUBLICO.com/api"
npm run github:prepare
```

## Subir cambios

Desde dentro de esta carpeta:

```cmd
git add .
git commit -m "Actualizar página conectada al backend"
git push
```

Si Git muestra `dubious ownership`, ejecuta una sola vez:

```cmd
git config --global --add safe.directory "C:/Desktop/APLICACION ASISTENCIA/git-hub page"
```

## Nota

La demo estática vieja sigue existiendo solo como herramienta opcional:

```cmd
npm run github:prepare-static
```

Úsala solamente si quieres una pagina sin backend y aceptas que no sincronice datos.
