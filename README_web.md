# Web Sal y Pimienta Metropolitano — v1 (borrador)

Una sola página estática: `index.html` + `img/`. Sin build, sin dependencias. Sube la carpeta tal cual a Netlify/Vercel/cualquier hosting.

## Qué editar
- **Menú del día:** lo cambia el bar desde la ventana del respondedor (`replies/menu_web.py` reescribe el bloque `const MENU_DIA = {...};`). **No cambies el formato de ese bloque** (claves `precio`, `primeros`, `segundos`, `postre`, cierre `};` en su propia línea) o la ventana dejará de encontrarlo.
- **Horario, próximo partido:** al final de `index.html`, bloque `DATOS EDITABLES` (`HORARIO`, `PROXIMO_PARTIDO`).
- **Carta:** constante `CARTA` en el mismo bloque (copia de `../carta/carta.json`).
- **Fotos:** sustituir archivos en `img/` manteniendo el nombre (hero_fachada.jpg = portada). Recomendado ≤1600 px de ancho, JPG calidad 78.
- **WhatsApp:** todos los botones apuntan a `wa.me/34910660207` (el fijo del bar). Confirmar con el dueño si tienen WhatsApp Business en otro número y hacer buscar/reemplazar.
- **Reseñas:** sección `#opiniones`, tres citas reales de Google (Miriam, Eder, Lalo). Enlace de reseña: g.page/r/CZbwO-Q7u0hQEBE/review.
- **Mapa:** iframe de Google Maps por place_id + botón "Abrir en Google Maps" de respaldo.

## Pendiente antes de publicar
- Aviso legal / privacidad / cookies (los enlaces del pie están vacíos). Si solo hay el iframe de Google Maps y fuentes de Google, basta con un aviso legal + política de privacidad sencillos.
- Dominio: salypimientarestaurante.com (si se recupera) o salypimientametropolitano.com.
- Fotos nuevas del dueño (terraza con gente de día, equipo, interior, platos estrella).
- Favicon y og:image definitivos con el logo original.
- Versión en inglés completa (ahora solo un párrafo en "Día de partido").

## Diseño
Paleta: papel #F3EBDD · tinta #1C1917 · rojo #C8102E · cerveza #D9A441. Tipografías: Caveat (títulos, la manuscrita de la carta/app) + Barlow (texto). Idea: la web es la pizarra del bar.

## Despliegue (GitHub + Vercel) — cuentas del bar desde 2026-10-11
- Repo: https://github.com/emeritalalangui-lgtm/Sal-y-pimienta (público, rama `main`).
- Web: https://sal-y-pimienta-livid.vercel.app (Vercel del bar, "Continue with GitHub"; Framework Other, sin build, output `.`).
- Copia local en la lap del bar: `Escritorio\Sal-y-pimienta`. La ventana del respondedor (`Documents\SalyPimienta\replies\menu_web.py`)
  edita el bloque `MENU_DIA` de `index.html`, hace commit y push; cada push a `main` redespliega solo en 1-2 min.
- Vídeo de portada: `video/comida.mp4` (720×900, 30 s, bucle, sin audio) generado con ffmpeg a partir de las fotos `img/pro_*.jpg`.
  Para regenerarlo con fotos nuevas, ver `Documents\SalyPimienta\PENDIENTES.md`.
- Rediseño 2026-10-11: concepto familiar, estilo sobrio (Forum + Abhaya Libre, blanco/negro), sin secciones de partido.
