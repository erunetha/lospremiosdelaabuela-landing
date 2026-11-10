# Los Premios de la Abuela — Landing page

Sitio estático (HTML + CSS + JS sin dependencias) de **Los Premios de la Abuela**: premios artesanales para perros y gatos.

## Estructura

```
.
├── index.html            # Toda la página (estilos y script incluidos)
├── logo.png              # Logo horizontal (header)
├── logo-principal.png    # Logo principal (hero)
├── img/                  # Ilustraciones del manual de identidad (.webp)
└── .vscode/              # Recomendaciones y ajustes para VS Code
```

## Cambios frecuentes

| Quiero cambiar…            | Dónde                                                                 |
|----------------------------|-----------------------------------------------------------------------|
| Productos y precios        | `index.html` → arreglo `PRODUCTOS` (casi al final, en el `<script>`)  |
| Número de WhatsApp         | `index.html` → constante `WHATSAPP` (formato `52` + 10 dígitos)        |
| Colores de la marca        | `index.html` → variables `:root` al inicio del `<style>`              |
| Textos (historia, consejos)| `index.html` → secciones `#historia`, `.tips`                         |
| Ilustraciones              | Reemplaza el archivo en `img/` con el mismo nombre                    |

La tabla de precios y los botones de "Pedir" se generan solos a partir de `PRODUCTOS`.

## Ver en local

En VS Code instala la extensión recomendada **Live Server** (te la sugiere al abrir la carpeta), abre `index.html` y da clic en **Go Live**.

Sin extensiones:

```bash
python3 -m http.server 8080
# abre http://localhost:8080
```

## Paleta (manual de identidad)

| Nombre         | Hex       |
|----------------|-----------|
| Café Valkiria  | `#5a382b` |
| Avena          | `#fff8ee` |
| Maní           | `#E8CDA9` |
| Manzana        | `#C97F6F` |
| Oliva          | `#899078` |
| Amarillo Max   | `#d8a354` |

Tipografías: *The Seasons* (títulos), *Open Sans* (texto), *Buffalo* (detalles a mano). Mientras no haya licencia web de The Seasons y Buffalo se usan Playfair Display y Caveat como sustitutos (ver variables `--f-*`).

## Publicación

Publicado en **Cloudflare Workers** (assets estáticos) con Wrangler. La configuración está en `wrangler.jsonc`; `.assetsignore` deja fuera lo que no debe subirse.

URL actual: https://lospremiosdelaabuela.oscaradrian-ia.workers.dev

Para publicar una nueva versión (necesita Node y haber hecho `npx wrangler login` una vez):

```bash
npx wrangler deploy
```

Para el dominio propio: Cloudflare → Workers & Pages → `lospremiosdelaabuela` → *Settings* → *Domains & Routes* → agrega `lospremiosdelaabuela.mx` (y redirige `.com` → `.mx`).
