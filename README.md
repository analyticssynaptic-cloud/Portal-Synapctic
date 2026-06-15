# SYNAPTIC — Despliegue en GitHub Pages

Esta carpeta contiene todo lo necesario para publicar el sitio en GitHub Pages.

## Contenido de la carpeta

- `index.html` — Landing completa (hero + servicios + sector zero + neural nexus + contacto).
- `zona-underground.png` — Imagen de fondo de la zona Sector Zero.
- `zona-digital-void.png` — Imagen de fondo de la zona Neural Nexus.
- `.nojekyll` — Evita que GitHub procese el sitio con Jekyll (necesario para que sirva los archivos tal cual).
- `README.md` — Este instructivo.

⚠️ **Importante**: los tres archivos (`index.html` y las dos `.png`) DEBEN quedar en la misma carpeta raíz del repositorio. No los muevas a subcarpetas o las imágenes no cargarán.

---

## Paso a paso para publicar (modo fácil, sin git)

### 1) Crea una cuenta en GitHub
Si aún no tienes: ve a https://github.com y regístrate.

### 2) Crea un repositorio nuevo
1. Click en el **+** arriba a la derecha → **New repository**.
2. **Repository name**: ponle algo como `synaptic` o `synaptic-landing`.
3. Selecciona **Public** (GitHub Pages gratis solo funciona en repos públicos).
4. **NO** marques "Add a README file" (ya tienes uno).
5. Click **Create repository**.

### 3) Sube los archivos
1. En la pantalla del repo vacío, click en **uploading an existing file** (link azul al centro).
2. Arrastra los **4 archivos** de esta carpeta a la zona de upload:
   - `index.html`
   - `zona-underground.png`
   - `zona-digital-void.png`
   - `.nojekyll`
3. Espera a que terminen de subir (el `index.html` pesa ~6 MB porque incluye el video del hero embebido en base64; puede tardar 1-3 min según tu conexión).
4. En "Commit changes" baja al final y click **Commit changes**.

### 4) Activa GitHub Pages
1. Dentro del repo, click en **Settings** (arriba a la derecha).
2. En el menú izquierdo, click **Pages**.
3. En **Source** selecciona **Deploy from a branch**.
4. En **Branch** elige `main` y carpeta `/ (root)`. Click **Save**.
5. Espera 30-90 segundos. Recarga la página de Settings → Pages.
6. Aparecerá: **Your site is live at** `https://TU_USUARIO.github.io/synaptic/`
7. Click en la URL y verifica que cargue. ¡Listo!

---

## Cómo actualizar el sitio después

Cuando quieras cambiar algo (texto, imágenes, código):

1. Edita los archivos localmente.
2. En tu repositorio en GitHub, entra al archivo que quieres actualizar.
3. Click en el ícono del **lápiz** (Edit) o sube reemplazos con **Add file → Upload files**.
4. Commit los cambios.
5. En 30-60 segundos GitHub Pages republica automáticamente.

---

## Notas técnicas

- **Tiempo de carga inicial**: el sitio tarda 3-6 segundos en aparecer porque desempaqueta el video del hero (está embebido en el HTML como base64 + gzip). Verás un cartel "Unpacking..." abajo a la derecha mientras tanto. Esto es normal y solo pasa la primera vez (después queda en caché del navegador).
- **El video del hero está en bucle infinito**: se reactiva automáticamente cada vez que termina sus ~10 segundos, sin necesidad de click. Si NO lo ves repetirse, abre la consola del navegador (F12 → Console) y comparte cualquier error que veas.
- **Imágenes faltantes**: si las zonas Sector Zero / Neural Nexus se ven negras sin fondo, significa que las `.png` no se subieron junto al `index.html`. Vuelve al paso 3 y súbelas a la raíz del repo.
- **Dominio personalizado**: si quieres usar `tudominio.com` en vez de la URL `github.io`, en Settings → Pages → Custom domain pones tu dominio y configuras un CNAME apuntando a `TU_USUARIO.github.io` en el panel DNS de tu proveedor.

---

## Alternativa: subir con Git (modo avanzado)

Si prefieres usar línea de comandos:

```bash
cd "deploy-github-pages"
git init
git add .
git commit -m "Initial deploy"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/synaptic.git
git push -u origin main
```

Luego activa Pages como en el paso 4.

---

## Soporte

Si algo no funciona:
1. Abre la consola del navegador (F12) en la URL de GitHub Pages.
2. Mira la pestaña **Console** y la pestaña **Network**.
3. Revisa si hay errores 404 (archivo faltante) o errores de JavaScript.
