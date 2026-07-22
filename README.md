# PoLED Electric — Web

Sitio web de PoLED Electric, instalaciones eléctricas de baja tensión.

## Estructura

- **`index.html`** — toda la web (estilos, scripts, logo, y las dos herramientas
  internas —Calculadora REBT y Generador de presupuestos— van incluidas dentro
  de este mismo archivo).
- **`data.json`** — los proyectos, categorías y reseñas que se muestran en la
  web. Es el archivo que se actualiza automáticamente cuando añades, editas o
  borras algo desde el modo edición.

## Cómo funciona el modo edición (¡leer antes de usarlo!)

Al pulsar "Añadir proyecto" / "Añadir reseña" (o editar/borrar uno existente),
la web hace dos cosas:

1. Guarda una copia en tu navegador al instante (para que no se pierda si
   recargas).
2. Publica el cambio en GitHub, sobrescribiendo `data.json` en el
   repositorio, para que **todos los visitantes**, en cualquier dispositivo,
   vean el cambio (tarda entre unos segundos y un minuto en propagarse).

Para que el paso 2 funcione necesitas darle permiso una vez por sesión de
navegador, mediante un **token de acceso personal (PAT)** de GitHub:

### Crear el token

1. Ve a GitHub → foto de perfil (arriba a la derecha) → **Settings**.
2. Baja hasta **Developer settings** (al final del menú lateral izquierdo).
3. **Personal access tokens → Fine-grained tokens → Generate new token**.
4. Ponle un nombre (p. ej. `poled-web-editor`).
5. En **Repository access**, elige **Only select repositories** y selecciona
   `poled.electric`.
6. En **Permissions → Repository permissions**, busca **Contents** y ponlo en
   **Read and write**. No hace falta ningún otro permiso.
7. Genera el token y **cópialo** (solo se muestra una vez).

La primera vez que guardes un cambio en cada navegador, la web te pedirá que
pegues este token. Se queda guardado solo mientras esa pestaña/navegador esté
abierto (no se guarda de forma permanente, por seguridad); si cierras el
navegador tendrás que volver a pegarlo la próxima vez que edites.

**No compartas nunca este token.** Si crees que alguien más lo tiene, ve a
Settings → Developer settings → Personal access tokens y bórralo (revócalo);
luego genera uno nuevo.

### Verifica el nombre de la rama

Dentro de `index.html`, busca esta línea cerca del principio del `<script>`:

```js
const GITHUB_BRANCH="main";
```

Debe coincidir con la rama que usas para publicar la web (la que elegiste en
Settings → Pages). Si tu rama se llama `master` en vez de `main`, cambia esa
línea.

## Fotos de los proyectos

Al subir fotos desde el modo edición, la web las redimensiona y comprime
automáticamente (máx. 1280 px, calidad ~72%) antes de guardarlas, para que
`data.json` no crezca demasiado. Aun así, evita subir más de unas pocas fotos
por proyecto: la API de GitHub tiene un límite de 1 MB por archivo para este
tipo de actualización.

## Copia de seguridad manual

Si la publicación automática fallara (token caducado, sin conexión, límite de
la API alcanzado...), el botón **"Copia de seguridad"** (junto a "Añadir
proyecto", en modo edición) descarga un `data.json` con el estado actual.
Puedes subir ese archivo manualmente al repositorio desde la web de GitHub
(botón "Add file → Upload files") si hiciera falta.

## Dependencias externas (por CDN)

La web necesita conexión a internet para cargar:

- Google Fonts (`Big Shoulders Display`, `Work Sans`, `IBM Plex Mono`)
- [jsPDF](https://github.com/parallax/jsPDF) (generación de PDFs en la calculadora)
- [Lucide Icons](https://lucide.dev/)
- La API de GitHub (`api.github.com`), solo al guardar cambios en modo edición

No hay backend propio: es una web estática con datos guardados en el propio
repositorio de GitHub.

## Publicar con GitHub Pages

1. Sube este repositorio a GitHub (ver más abajo).
2. En el repositorio, ve a **Settings → Pages**.
3. En **Source**, elige tu rama (`main`) y la carpeta `/ (root)`.
4. Guarda. GitHub te dará la URL pública de la web.

**Importante:** si abres `index.html` haciendo doble clic en tu ordenador
(`file://...`), la carga de `data.json` no funcionará por restricciones del
navegador. Para probar en local, usa un servidor simple, por ejemplo:

```bash
python3 -m http.server
```

y abre `http://localhost:8000`.

## Subir este proyecto a GitHub desde cero

```bash
cd poled-electric-web
git init
git add .
git commit -m "Primera versión de la web"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/NOMBRE-DEL-REPO.git
git push -u origin main
```
