# Vue GameStream

Vue GameStream es una aplicación web de catálogo de videojuegos que consume una API REST para mostrar una colección de juegos con sus imágenes, etiquetas, descripción y año de publicación. Permite buscar juegos por título en tiempo real y reproducir trailers o vídeos de cada juego directamente en un modal integrado.

## Características

- Listado de juegos obtenido desde una API REST
- Buscador en tiempo real por título
- Galería de imágenes por juego con navegación por flechas
- Etiquetas de género/categoría por juego
- Reproductor de vídeo en modal con Teleport
- Estado de carga global con componente `SharedLoader`
- Lógica de fetch encapsulada en el composable `useFetch`
- Store reactivo para el modal sin dependencias externas

## Stack tecnológico

| Tecnología | Versión |
|---|---|
| Vue | 3.x (Composition API + `<script setup>`) |
| Vite | 6.x |
| ESLint + Prettier | 9.x / 3.x |
| pnpm | recomendado |

## Estructura del proyecto

```
src/
├── components/
│   ├── Games/          # GameCard, GameLayout, GameModal, GameVideoPlayer, GameGallery, GameTag
│   ├── Icons/          # Iconos SVG como componentes Vue
│   ├── Layout/         # LayoutHero
│   ├── Shared/         # SharedLoader, SharedSearch
│   └── store/          # modalStore (store reactivo manual)
├── composables/
│   └── useFetch.js     # Composable genérico para fetch con isLoading y error
└── App.vue
```

## Instalación y uso

### Instalar dependencias

```sh
pnpm install
```

### Servidor de desarrollo con hot-reload

```sh
pnpm dev
```

### Build de producción

```sh
pnpm build
```

### Previsualizar el build

```sh
pnpm preview
```

### Lint y formato

```sh
pnpm lint
pnpm format
```

## IDE recomendado

[VS Code](https://code.visualstudio.com/) con la extensión [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (desactivar Vetur si está instalado).

Para más detalles sobre la configuración de Vite: [Vite Configuration Reference](https://vite.dev/config/).
