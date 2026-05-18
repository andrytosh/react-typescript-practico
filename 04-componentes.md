# 4. Componentes en React

[← Índice](README.md) | [← Anterior: 3. JSX](03-jsx-renderizado.md) | [Siguiente: 5. Estado →](05-estado-hooks.md)

---

## Componentes funcionales

```tsx
type SaludoProps = {
  nombre: string;
};

function Saludo({ nombre }: SaludoProps) {
  return <p>Hola, {nombre}</p>;
}
```

## Props

Datos que el padre pasa al hijo. En TypeScript defines un **tipo** para las props.

## Composición

```tsx
function Tarjeta({ children }: { children: React.ReactNode }) {
  return <article className="tarjeta">{children}</article>;
}

function App() {
  return (
    <Tarjeta>
      <h2>Título</h2>
      <p>Contenido</p>
    </Tarjeta>
  );
}
```

## Reutilización

El mismo componente con distintas props genera distintas instancias en la UI.

## Lab: composición

1. Crea `Tarjeta.tsx` con `children` tipado como `React.ReactNode`.
2. Crea `ListaProductos.tsx` que reciba `productos: { id: number; nombre: string }[]` y renderice varias tarjetas.
3. Usa ambos desde `App.tsx`.
