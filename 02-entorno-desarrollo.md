# 2. Entorno de desarrollo

[← Índice](README.md) | [← Anterior: 1. Introducción](01-introduccion-react-ecosistema.md) | [Siguiente: 3. JSX →](03-jsx-renderizado.md)

---

## Node.js y npm

Node permite ejecutar herramientas en la terminal. **npm** instala dependencias y ejecuta scripts (`dev`, `build`, `test`).

## Crear proyecto con Vite

```bash
npm create vite@latest mi-app -- --template react-ts
cd mi-app
npm install
npm run dev
```

La plantilla **react-ts** incluye TypeScript, `src/main.tsx`, `src/App.tsx` y `tsconfig.json`.

## Estructura típica

```
mi-app/
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── src/
    ├── main.tsx      # punto de entrada
    ├── App.tsx       # componente raíz
    ├── App.css
    └── vite-env.d.ts
```

## Herramientas

- **Dev server** (`npm run dev`) — recarga al guardar.
- **TypeScript** — comprueba tipos (`tsc` o el IDE).
- **ESLint** — calidad de código (opcional en el template).

## Lab: proyecto inicial

1. Crea el proyecto con el comando de arriba.
2. Abre la URL que muestra Vite (por defecto `http://localhost:5173`).
3. Edita `App.tsx` y comprueba que la página se actualiza sin recargar manualmente.
4. Haz commit en tu fork con el mensaje `chore: proyecto vite react-ts`.
