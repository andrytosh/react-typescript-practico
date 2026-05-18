# 3. JSX y renderizado

[← Índice](README.md) | [← Anterior: 2. Entorno](02-entorno-desarrollo.md) | [Siguiente: 4. Componentes →](04-componentes.md)

---

## TSX (JSX + TypeScript)

En archivos `.tsx` mezclas **marcado** y **lógica**:

```tsx
const titulo = 'Hola';
return <h1>{titulo}</h1>;
```

## Expresiones embebidas

Entre `{ }` va cualquier expresión JavaScript válida: variables, llamadas, operadores ternarios.

## Renderizado condicional

```tsx
{estaLogado ? <p>Bienvenido</p> : <p>Inicia sesión</p>}
{error && <p className="error">{error}</p>}
```

## Listas y `key`

```tsx
type Item = { id: number; texto: string };

items.map((item) => <li key={item.id}>{item.texto}</li>);
```

`key` debe ser **estable y única** entre hermanos (evita usar solo el índice si la lista cambia de orden).

## Lab: render dinámico y condicional

En `mi-app`:

1. Crea un array de 3–5 elementos con `id` y `texto`.
2. Muéstralos en una lista con `.map` y `key`.
3. Añade un botón que alterne entre dos vistas (condicional) o filtre la lista.
4. Tipa el array con `type` o `interface`.
