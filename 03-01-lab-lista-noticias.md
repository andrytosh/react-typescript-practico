# 3.1. Lab — Lista de noticias (map, props y key)

[← Capítulo 3](03-jsx-renderizado.md) | [← Lab 2.1](02-01-lab-vite.md) | [Índice](README.md) | [Lab 4.1 →](04-01-lab-composicion.md)

---

## Objetivo del laboratorio

Cargar noticias desde un **JSON**, crear el componente **`Noticia`**, renderizar la lista con **`.map()`**, pasar **props** y usar **`key`** estable. No usarás `useState` en este lab.

## Tiempo estimado

45–60 minutos.

## Archivos que crearás o modificarás

| Archivo | Acción |
|---------|--------|
| `src/data/noticias.json` | Crear |
| `src/components/Noticia.tsx` | Crear |
| `src/App.tsx` | Modificar en varios pasos |

## Prerrequisitos

- [2.1 Lab Vite](02-01-lab-vite.md) completado.
- `npm run dev` ejecutándose en la raíz de tu proyecto.

## Resultado esperado

Tres noticias (título + contenido). Consola del navegador **sin** el warning *Each child in a list should have a unique "key" prop*.

---

## Paso 1 — Datos en JSON

**Objetivo:** tener datos fijos y reproducibles fuera del componente.

1. Crea `src/data/`.
2. Crea **`src/data/noticias.json`** con este contenido **exacto**:

```json
[
  {
    "id": "n1",
    "titulo": "Historiadores descubren que el caballo blanco de Santiago era blanco",
    "contenido": "Rem ab, animi ea pariatur praesentium at omnis obcaecati officia ipsum."
  },
  {
    "id": "n2",
    "titulo": "El caballo del ajedrez crea su propio juego de equitación",
    "contenido": "Necessitatibus, sed nostrum fugit consectetur aliquam quaerat repellat."
  },
  {
    "id": "n3",
    "titulo": "La orquesta del buque en el Canal de Suez se niega a dejar de tocar",
    "contenido": "Consectetur et consequatur sint. Quibusdam, nihil quasi modi dolorum."
  }
]
```

**Comprobación:** JSON válido; tres elementos con `id` distintos.

---

## Paso 2 — Componente `Noticia`

**Objetivo:** encapsular la vista de una noticia.

Crea **`src/components/Noticia.tsx`**:

```tsx
export type NoticiaData = {
  id: string
  titulo: string
  contenido: string
}

type NoticiaProps = {
  noticia: NoticiaData
}

export function Noticia({ noticia }: NoticiaProps) {
  return (
    <article style={{ border: '1px solid #ccc', margin: '1rem 0', padding: '1rem' }}>
      <h2>{noticia.titulo}</h2>
      <p>{noticia.contenido}</p>
    </article>
  )
}
```

**Comprobación:** TypeScript sin errores en ese archivo.

---

## Paso 3 — Importar el JSON

**Objetivo:** comprobar la importación antes del `.map()`.

Sustituye **todo** **`src/App.tsx`**:

```tsx
import noticias from './data/noticias.json'

function App() {
  return (
    <div>
      <h1>Noticias</h1>
      <p>Hay {noticias.length} noticias en el JSON.</p>
    </div>
  )
}

export default App
```

**Comprobación:** en pantalla lees `Hay 3 noticias en el JSON.`

**Si TypeScript protesta por el import:** en `tsconfig.app.json` debe existir `"resolveJsonModule": true` (la plantilla `react-ts` ya lo trae).

---

## Paso 4 — Listar con `.map()` **sin** `key`

**Objetivo:** ver el listado y el warning de React en consola.

Sustituye **todo** **`src/App.tsx`** por:

```tsx
import noticias from './data/noticias.json'
import { Noticia } from './components/Noticia'

function App() {
  return (
    <div>
      <h1>Noticias</h1>
      {noticias.map((noticia) => (
        <Noticia noticia={noticia} />
      ))}
    </div>
  )
}

export default App
```

**Comprobación:**

- Ves **tres** noticias en pantalla.
- En consola (F12) aparece el warning sobre **`key`**.


---

## Paso 5 — Añadir `key` estable

**Objetivo:** quitar el warning usando el `id` del dato.

Cambia solo la línea del `map` a:

```tsx
{noticias.map((noticia) => (
  <Noticia key={noticia.id} noticia={noticia} />
))}
```

**Comprobación:** las tres noticias siguen visibles; el warning **desaparece** de la consola.

---

## Paso 6 — Mensaje si la lista está vacía

**Objetivo:** practicar renderizado condicional con `&&`.

Debajo de `<h1>Noticias</h1>`, añade:

```tsx
{noticias.length === 0 && <p>No hay noticias publicadas.</p>}
```

**Comprobación:** con el JSON actual el mensaje **no** se muestra.

**Prueba extra:** renombra temporalmente `noticias.json` (por ejemplo a `noticias.json.bak`), guarda y recarga. Debe aparecer el mensaje y probablemente un error de import; restaura el nombre del archivo después.

---

## Si algo falla

| Síntoma | Qué revisar |
|---------|-------------|
| `Cannot find module './data/noticias.json'` | Ruta y nombre del archivo; debe estar en `src/data/`. |
| Pantalla en blanco | Consola del navegador; suele faltar `export` o hay error de sintaxis en `App.tsx`. |
| Warning de `key` no sale en paso 4 | Asegúrate de **no** poner `key=` en ese paso. |
| `noticia` subrayado en rojo | El prop se llama `noticia`; en el `map` usa `noticia={noticia}`. |

---

## Retos

| Reto | Enunciado | Criterio de éxito |
|------|-----------|-------------------|
| A | Añade una cuarta noticia al JSON. | Aparece sin cambiar el `.map()`. |
| B | Muestra el contenido solo de la noticia `n1`; el resto solo título. | Usa condicional en `Noticia` o en `App`. |
| C | Explica por escrito por qué `key={index}` es peor que `key={noticia.id}` si reordenas la lista. | Dos frases en tu cuaderno o README del proyecto. |

---

## Qué has practicado

- Importar JSON en Vite/TypeScript.
- `.map()` para generar listas en TSX.
- Props tipadas y `key` con identificador estable.
- Condicional `{condicion && <elemento />}`.

**Siguiente:** [Capítulo 4](04-componentes.md) → [Lab 4.1 Composición](04-01-lab-composicion.md).
