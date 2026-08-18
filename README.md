# MNK Labs — sitio web

Sitio institucional de MNK Labs. HTML y CSS estáticos, sin build step ni
dependencias: lo que está en `public/` es exactamente lo que se publica.

## Estructura

```
wrangler.jsonc          configuración del Worker (nombre + directorio de assets)
public/                 todo lo que se sirve públicamente
├── index.html          home: hero, servicios, sistema post-venta, nosotros, contacto
├── _headers            cache-control (evita que el navegador sirva una versión vieja)
├── assets/
│   ├── style.css       hoja de estilos compartida por todas las páginas
│   ├── logo.jpeg       logo original
│   ├── logo-web.jpg    versión optimizada para nav y hero
│   ├── favicon.png     favicon con transparencia
│   └── *.jpg           capturas de los casos
└── proyectos/
    ├── index.html      listado de casos (producción + laboratorio)
    ├── neu.html        sistema de seguimiento post-venta (cliente: Neu+)
    ├── flowpedidos.html
    ├── tremendogol.html
    └── foodstore.html
```

## Ver el sitio en local

No hace falta instalar nada:

```bash
cd public && python3 -m http.server 8000
```

Abrir http://localhost:8000

## Deploy

Automático: cada push a `main` dispara un build en Cloudflare Workers y publica.
No hay que correr nada a mano.

Para revisar el estado de un deploy: Cloudflare Dashboard → Workers & Pages →
`mnklabs` → Deployments.

## Editar el contenido

- **Textos, servicios, secciones** → `public/index.html`
- **Colores y tipografías** → variables al inicio de `public/assets/style.css`
- **Un caso nuevo** → copiar una página de `public/proyectos/`, y agregar la
  tarjeta correspondiente en `public/proyectos/index.html`
