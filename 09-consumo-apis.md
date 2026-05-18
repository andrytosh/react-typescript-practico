# 9. Consumo de APIs

[← Índice](README.md) | [← Anterior: 8. Routing](08-routing.md) | [Siguiente: 10. Organización →](10-organizacion-buenas-practicas.md)

---

## Fetch con useEffect

```tsx
type Usuario = { id: number; name: string };

function ListaUsuarios() {
  const [datos, setDatos] = useState<Usuario[]>([]);
  const [cargando, setCargando] = useState(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    let cancelado = false;

    async function cargar() {
      try {
        setCargando(true);
        const res = await fetch('https://jsonplaceholder.typicode.com/users');
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        const json: Usuario[] = await res.json();
        if (!cancelado) setDatos(json);
      } catch (e) {
        if (!cancelado) setError(e instanceof Error ? e.message : 'Error');
      } finally {
        if (!cancelado) setCargando(false);
      }
    }

    cargar();
    return () => {
      cancelado = true;
    };
  }, []);

  if (cargando) return <p>Cargando…</p>;
  if (error) return <p>Error: {error}</p>;

  return (
    <ul>
      {datos.map((u) => (
        <li key={u.id}>{u.name}</li>
      ))}
    </ul>
  );
}
```

## Axios (opcional)

```bash
npm install axios
```

Misma idea: `useEffect` + estados `loading` / `error` / `data`.

## Lab: consumo de API

1. Elige un endpoint público (JSONPlaceholder, etc.).
2. Muestra lista con estados de carga y error.
3. Opcional: detalle al hacer clic usando estado o una segunda ruta.
