# 8. Routing en React

[← Índice](README.md) | [← Anterior: 7. Comunicación](07-comunicacion-componentes.md) | [Siguiente: 9. APIs →](09-consumo-apis.md)

---

## Instalación

```bash
npm install react-router-dom
```

## BrowserRouter y rutas

```tsx
// main.tsx
import { BrowserRouter } from 'react-router-dom';

createRoot(document.getElementById('root')!).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

```tsx
// App.tsx
import { Routes, Route, Link } from 'react-router-dom';
import Inicio from './pages/Inicio';
import Acerca from './pages/Acerca';

function App() {
  return (
    <>
      <nav>
        <Link to="/">Inicio</Link>
        <Link to="/acerca">Acerca</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Inicio />} />
        <Route path="/acerca" element={<Acerca />} />
      </Routes>
    </>
  );
}
```

## Navegación programática

```tsx
import { useNavigate } from 'react-router-dom';

const navigate = useNavigate();
navigate('/acerca');
```

## Lab: navegación básica

1. Instala `react-router-dom` y sus tipos si hace falta (`@types` suele ir incluido).
2. Crea `pages/Inicio.tsx` y `pages/Contacto.tsx`.
3. Menú con `Link` y ruta comodín `*` con página 404 opcional.
