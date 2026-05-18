# 1. Introducción a React y ecosistema

[← Índice](README.md) | [← Anterior: Requisitos](00-requisitos.md) | [Siguiente: 2. Entorno →](02-entorno-desarrollo.md)

---

## Qué es React

React es una librería para construir **interfaces de usuario** mediante **componentes** reutilizables. No es un framework completo: el routing, el estado global o el data fetching suelen añadirse con librerías del ecosistema.

## SPA vs aplicación tradicional

| Tradicional (multi-página) | SPA (Single Page Application) |
|----------------------------|-------------------------------|
| El servidor devuelve HTML nuevo en cada navegación | Una carga inicial; el cliente actualiza la vista |
| Recarga completa | Cambios parciales en el DOM |
| Menos lógica en el navegador | Mucha lógica en JavaScript/TypeScript |

## Arquitectura por componentes

- La UI se divide en **componentes** (piezas con responsabilidad clara).
- Los componentes se **componen** (árbol de componentes).
- Los datos fluyen de padres a hijos (**props**); el estado vive donde se necesita.

## Ecosistema React

- **Vite** — herramienta de desarrollo y build (recomendada en este curso).
- **React Router** — navegación entre vistas.
- **TypeScript** — tipos estáticos en `.ts` / `.tsx`.
- Otras: gestores de estado (Redux, Zustand), testing (Vitest, Testing Library), UI kits (MUI, etc.).

En el siguiente capítulo montarás el entorno con Vite y la plantilla `react-ts`.
