# PROCESADORA MONEGRO MC - GitHub Pages

Esta carpeta es una copia estatica de la aplicacion para publicarla en GitHub Pages.

## Que incluye

- Pantalla de login corporativa.
- Panel admin.
- Produccion.
- Ventas.
- Produccion vs venta.
- Asistencia.
- Empleados.
- Organizacion.
- Reportes y auditoria.
- Datos exportados desde PostgreSQL en la carpeta `data`.
- Fotos demo exportadas en la carpeta `uploads`.
- Datos actuales: 24 sucursales, 114 usuarios, 5,615 reportes de produccion, 54,983 detalles de produccion, 193,458 ventas y 2,196 asistencias.

## Importante

- No usa PostgreSQL en GitHub Pages.
- No usa backend.
- No sincroniza cambios con tu PC.
- Los cambios que hagas en la pagina publicada son temporales en el navegador.
- La base estatica esta dividida en varios JSON para evitar pantalla en blanco y errores por archivos grandes.

## Archivos obligatorios para subir

Sube todo el contenido de `git-hub page`, incluyendo:

```txt
index.html
.nojekyll
assets
data
uploads
README.md
```

Dentro de `data` deben estar:

```txt
database-index.json
core.json
production.json
sales-001.json
sales-002.json
sales-003.json
sales-004.json
```

La carpeta `uploads` tambien debe subirse completa para que se vean las fotos de produccion en GitHub Pages.

## Credenciales demo

- Admin: `Gerencia@procesadoramonegro.com`
- Contrasena: cualquier texto en esta copia estatica

## Regenerar la copia

Esta carpeta ya esta lista para subir a GitHub Pages. Si en el futuro regeneras otra copia desde la app local, usa el mismo nombre de carpeta final:

```powershell
node scripts\export-github-pages-demo.js
$env:VITE_STATIC_DEMO="1"
npm.cmd --prefix frontend run build -- --base ./ --outDir "../tmp/github-build" --emptyOutDir
```

Luego copia el build generado dentro de esta carpeta `git-hub page`:

```powershell
Get-ChildItem -Path ".\git-hub page\assets" -Filter "index-*.*" | Remove-Item -Force
Copy-Item -Path ".\tmp\github-build\assets\*" -Destination ".\git-hub page\assets" -Force
Copy-Item -Path ".\tmp\github-build\index.html" -Destination ".\git-hub page\index.html" -Force
Copy-Item -Path ".\backend\uploads\*" -Destination ".\git-hub page\uploads" -Force
New-Item -ItemType File -Path ".\git-hub page\.nojekyll" -Force
```

## Subir cambios

Desde dentro de esta carpeta:

```cmd
git add .
git commit -m "Actualizar pagina estatica"
git push
```

Si Git muestra `dubious ownership`, ejecuta una sola vez:

```cmd
git config --global --add safe.directory "C:/Desktop/APLICACION ASISTENCIA/git-hub page"
```
