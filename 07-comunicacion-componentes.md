# 7. Comunicación entre componentes

[← Índice](README.md) | [← Anterior: 6. Eventos](06-eventos-formularios.md) | [Siguiente: 8. Routing →](08-routing.md)

---

## Flujo unidireccional

Los datos bajan por **props**. Los hijos notifican al padre con **callbacks** en props.

```tsx
type HijoProps = {
  valor: number;
  onIncrementar: () => void;
};

function Hijo({ valor, onIncrementar }: HijoProps) {
  return <button type="button" onClick={onIncrementar}>{valor}</button>;
}

function Padre() {
  const [total, setTotal] = useState(0);
  return <Hijo valor={total} onIncrementar={() => setTotal((t) => t + 1)} />;
}
```

## Elevación de estado

Si dos hermanos deben compartir datos, **sube el estado** al ancestro común y pásalo por props.

## Lab: sincronización

1. `Padre` con estado `seleccionado: string | null`.
2. `ListaOpciones` recibe opciones y `onSeleccionar(id)`.
3. `Detalle` recibe el id seleccionado y muestra información.
4. Sin estado global: todo en el padre.
