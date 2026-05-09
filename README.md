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

## Credenciales demo

- Admin: `Gerencia@procesadoramonegro.com`
- Contrasena: cualquier texto en esta copia estatica

## Regenerar la copia

Esta carpeta ya esta lista para subir a GitHub Pages. Si en el futuro regeneras otra copia desde la app local, usa el mismo nombre de carpeta final:

```cmd
node scripts\export-github-pages-demo.js
npm.cmd --prefix github-pages-src run build -- --base ./ --outDir "../git-hub page" --emptyOutDir
Compress-Archive -Path "git-hub page\*" -DestinationPath "git-hub page.zip" -Force
```
