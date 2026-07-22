# SGI - Frontend (Next.js / React)

Interfaz web del Sistema de Gestion de Inventario, construida con Next.js (App Router).
Consume la API REST del backend PHP.

## Principios de la estructura

- src/app/ define las rutas: cada carpeta = una URL real, agrupada por modulo de negocio
- src/components/ui/        -> componentes genericos sin logica de negocio (Button, Table, Modal, Input, Badge)
- src/components/layout/    -> Sidebar, Navbar, Footer
- src/components/<modulo>/  -> componentes especificos (formularios y tablas de ese dominio)
- src/services/             -> toda la comunicacion con la API, una funcion por endpoint
- src/hooks/                -> logica reutilizable (useAuth, useFetch)
- src/context/               -> estado global (sesion del usuario)
- src/constants/ y src/utils/ -> valores fijos y funciones de apoyo

## Estructura

- src/app/layout.jsx, page.jsx, globals.css
- src/app/(auth)/login/page.jsx
- src/app/productos/ (page, nuevo, [id])
- src/app/categorias/page.jsx
- src/app/inventario/ (page, entradas, salidas)
- src/app/compras/ (page, nueva, [id])
- src/app/proveedores/page.jsx
- src/app/reportes/page.jsx
- src/app/auditorias/page.jsx
- src/app/usuarios/page.jsx  (solo Administrador)

## Convencion de nombres

- Paginas: siempre page.jsx (requisito de Next.js App Router)
- Componentes: PascalCase (ProductoForm.jsx)
- Servicios/hooks/utils: camelCase (productoService.js, useAuth.js)

## Como se ejecutaria

cd frontend
copy .env.local.example .env.local
npm install
npm run dev
