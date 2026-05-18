# 6. Eventos y formularios

[← Índice](README.md) | [← Anterior: 5. Estado](05-estado-hooks.md) | [Siguiente: 7. Comunicación →](07-comunicacion-componentes.md)

---

## Eventos en React

React usa eventos sintéticos. Tipa el handler según el elemento:

```tsx
const onClick = (e: React.MouseEvent<HTMLButtonElement>) => {
  e.preventDefault();
};

const onChange = (e: React.ChangeEvent<HTMLInputElement>) => {
  console.log(e.target.value);
};
```

## Inputs controlados

El valor del input vive en el **estado**; el input lo refleja y notifica cambios:

```tsx
const [email, setEmail] = useState('');

<input
  type="email"
  value={email}
  onChange={(e) => setEmail(e.target.value)}
/>;
```

## Formularios

```tsx
const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
  e.preventDefault();
  // enviar email, validar, etc.
};

<form onSubmit={handleSubmit}>...</form>
```

## Lab: formulario interactivo

1. Formulario con nombre, email y mensaje (todos controlados).
2. Al enviar (`preventDefault`), muestra un resumen debajo o en consola.
3. Botón deshabilitado si falta el email (validación mínima).
