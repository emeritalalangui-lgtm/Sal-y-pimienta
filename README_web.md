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

## Despliegue (GitHub + Vercel)

**Migración prevista (2026-10):** el repo pasa de `BioPhysicistRam/Sal-y-pimienta` a una cuenta de GitHub del bar (Transfer ownership) y el despliegue a un Vercel del bar (Continue with GitHub → Import). Motivo: el menú del día se publica a diario desde la lap del bar y Vercel Hobby bloquea commits de autores ajenos al proyecto. Después: cambiar `URL_WEB` en `replies/menu_web.py`, `web` en `replies/datos_fijos.json`, el enlace en la ficha de Google, y borrar el proyecto viejo de Vercel. Pasos detallados en `replies/README_AGENTE.md` §4.5.

Solo se sube **esta carpeta `web/`** como repo. Nunca la carpeta `13_Sal_y_pimienta` entera (tiene el PDF del plan, la carta y fotos en alta que no deben ser públicas).

```powershell
cd "C:\Users\Ramon\Documents\Organizado\03_Trabajo\13_Sal_y_pimienta\web"
git init
git add .
git commit -m "Web Sal y Pimienta v1"
gh repo create salypimienta-web --public --source=. --push
```

Sin `gh`: crear el repo vacío en GitHub y luego
`git remote add origin https://github.com/<usuario>/salypimienta-web.git && git branch -M main && git push -u origin main`.

En Vercel: **Add New → Project → Import** el repo → Framework "Other", sin build command, output directory `.` → Deploy.
Da una URL `*.vercel.app`; el dominio propio se añade después en Settings → Domains.
Cada `git push` a `main` redespliega solo.
