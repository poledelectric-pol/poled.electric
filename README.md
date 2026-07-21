# PoLED Electric — Web

Sitio web de PoLED Electric, instalaciones eléctricas de baja tensión.

## Estructura

Este proyecto es una **web de un único archivo** (`index.html`). No hace falta
ningún proceso de build ni servidor especial: todo el contenido, estilos,
scripts, imágenes (logo) y las dos herramientas internas están incluidos
dentro de ese mismo archivo.

Herramientas incluidas (se abren en una ventana emergente dentro de la propia
web, sin necesidad de archivos aparte):

- **Calculadora REBT** — cálculo de secciones, protecciones y puesta a tierra
  según el Reglamento Electrotécnico de Baja Tensión.
- **Generador de presupuestos** — creación, guardado y exportación
  (TXT / PDF) de presupuestos para clientes.

## Dependencias externas (por CDN)

La web necesita conexión a internet para cargar:

- Google Fonts (tipografías `Big Shoulders Display`, `Work Sans`, `IBM Plex Mono`)
- [jsPDF](https://github.com/parallax/jsPDF) (generación de PDFs en la calculadora)
- [Lucide Icons](https://lucide.dev/) (iconos)


## Edición de contenidos

Algunas secciones (proyectos del portafolio, etc.) tienen un modo de edición
protegido por contraseña dentro de la propia web. No hace falta tocar el
código para actualizar esos contenidos.
