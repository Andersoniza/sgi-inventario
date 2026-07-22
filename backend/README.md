# SGI - Backend (PHP)

API REST escrita en PHP puro (sin framework), organizada en capas MVC + Services + Repositories,
con autoload PSR-4 via Composer.

## Flujo de una peticion

Request HTTP -> public/index.php (front controller) -> Core/Router.php -> Middlewares (Auth, CORS)
-> Controllers (traduce HTTP, valida entrada) -> Services (reglas de negocio) -> Repositories
(acceso a datos) -> Models (entidades) -> Config/Database.php -> MySQL

## Por que esta separacion

- Controllers: solo traducen HTTP <-> PHP, sin logica de negocio ni SQL.
- Services: concentran las reglas de negocio (ej. AlertaReabastecimientoService decide cuando
  notificar al proveedor). Equivalen a los include/extend de los casos de uso de la Tarea 4.0.
- Repositories: aislan el acceso a datos.
- Models: representan entidades (Producto, Categoria, etc.) sin logica de negocio.

## Estructura

- public/index.php            -> punto de entrada unico de la API
- src/Config/                 -> conexion a BD y configuracion de entorno
- src/Core/                   -> Router, Request, Response, Controller base
- src/Middlewares/            -> AuthMiddleware (JWT), CorsMiddleware
- src/Controllers/            -> Auth, Usuario, Producto, Categoria, MovimientoInventario,
                                  Proveedor, OrdenCompra, Alerta, Auditoria, Reporte
- src/Models/                 -> Usuario, Producto, Categoria, MovimientoInventario, Proveedor,
                                  OrdenCompra, DetalleOrdenCompra, AuditoriaStock
- src/Services/                -> InventarioService, AlertaReabastecimientoService, CompraService,
                                  ReporteService, VentaIntegracionService
- src/Repositories/            -> uno por cada entidad principal
- src/Helpers/                 -> Validator, JwtHelper
- src/Routes/api.php           -> definicion de todas las rutas
- database/migrations/         -> un .sql por tabla, numerado
- database/seeders/            -> datos iniciales
- tests/Unit y tests/Integration

## Mapa de rutas planeado

POST /api/auth/login
GET|POST /api/usuarios
GET|POST|PUT|DELETE /api/productos(/{id})
GET|POST /api/categorias
POST /api/inventario/entradas
POST /api/inventario/salidas
GET /api/inventario/movimientos
GET|POST /api/proveedores
GET|POST /api/compras
PUT /api/compras/{id}/recibir
GET /api/alertas
GET|POST /api/auditorias
GET /api/reportes/inventario
POST /api/ventas/actualizar-stock  (webhook del sistema externo de ventas)

## Como se ejecutaria (cuando ya tenga codigo)

cd backend
copy .env.example .env
composer install
php -S localhost:8000 -t public
