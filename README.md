# SGI - Sistema de Gestion de Inventario

Proyecto academico (UNIBE, Clase 2.1 -> Tarea 5.0) que propone la arquitectura de backend
y frontend para el Sistema de Gestion de Inventario definido en la Tarea 4.0 (casos de uso).

Este repositorio contiene unicamente la estructura de carpetas y archivos (la mayoria vacios
o con contenido minimo de configuracion). La implementacion se ira completando en clases
posteriores.

## Arquitectura general

Aplicacion cliente-servidor desacoplada, comunicada por una API REST en JSON:

  frontend (Next.js, puerto 3000)  <--- HTTPS/JSON --->  backend (PHP API REST, puerto 8000)  --->  MySQL/MariaDB

- backend/: API REST en PHP puro, organizada en capas (Controller -> Service -> Repository -> Model). Ver backend/README.md
- frontend/: aplicacion Next.js (App Router) que consume la API. Ver frontend/README.md

## Por que esta arquitectura

- Separacion total front/back: cada uno se despliega, escala y versiona de forma independiente.
- Capas en el backend: evita controladores con logica de negocio y SQL mezclados; facilita pruebas y mantenimiento.
- App Router de Next.js: cada carpeta bajo src/app es una ruta real, alineada 1 a 1 con los modulos del sistema.

## Modulos del sistema (segun casos de uso de la Tarea 4.0)

- Usuarios / Auth
- Productos y Categorias
- Inventario (entradas, salidas, movimientos)
- Alertas de stock minimo
- Proveedores
- Compras (ordenes de compra)
- Auditorias
- Reportes

## Proximos pasos (fuera del alcance de esta tarea)

1. composer install en backend/
2. npm install en frontend/
3. Implementar migraciones, modelos, controladores y paginas.
