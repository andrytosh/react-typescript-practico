# 5. Estado y hooks

[← Índice](README.md) | [← Anterior: 4. Componentes](04-componentes.md) | [Siguiente: 6. Eventos →](06-eventos-formularios.md)

---

## useState

```tsx
import { useState } from 'react';

function Contador() {
  const [cuenta, setCuenta] = useState(0);
  return (
    <div>
      <button type="button" onClick={() => setCuenta((c) => c - 1)}>-</button>
      <span>{cuenta}</span>
      <button type="button" onClick={() => setCuenta((c) => c + 1)}>+</button>
    </div>
  );
}
```

Al cambiar el estado, React **vuelve a renderizar** el componente.

## useEffect

Efectos secundarios: peticiones, suscripciones, sincronizar con el DOM.

```tsx
import { useEffect, useState } from 'react';

function Reloj() {
  const [hora, setHora] = useState(new Date().toLocaleTimeString());

  useEffect(() => {
    const id = setInterval(() => setHora(new Date().toLocaleTimeString()), 1000);
    return () => clearInterval(id);
  }, []);

  return <p>{hora}</p>;
}
```

El array de **dependencias** controla cuándo se vuelve a ejecutar el efecto (`[]` = solo al montar).

## Lab: estado y efectos

1. Contador con `useState`.
2. Componente que muestre la hora actualizada cada segundo con `useEffect` y cleanup.
3. Opcional: input de texto cuyo valor se guarde en estado y se muestre debajo.
