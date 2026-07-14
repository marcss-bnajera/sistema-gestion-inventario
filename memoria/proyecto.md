# Sistema de Gestion de Inventario - Memoria del Proyecto

## Informacion General
- **Repositorio:** git@github.com:marcss-bnajera/sistema-gestion-inventario.git
- **Tipo:** Monorepo con submodulos
- **Metodologia:** Scrum (3 Sprints de 90 min)
- **Rama principal:** main
- **Fecha de inicio:** 2026-07-14

## Arquitectura

```
sistema-gestion-inventario/
├── gestion-inventario-auth/          # .NET 8 - Autenticacion (Puerto 5000/5001)
├── gestion-inventario-service-inventory/  # Express 5 - Inventario (Puerto 3001)
├── gestion-inventario-service-reports/    # Express 5 - Alertas y Reportes (Puerto 3005)
├── gestion-inventario-frontend/           # React + Vite (Puerto 5173)
├── memoria/                               # Documentacion del proyecto
└── .gitmodules
```

## Mi Rol
- **Backend Developer (Servicio B - Alertas y Reportes)**
- **GitHub:** Jcraxker (jackfallasoficial@gmail.com)

## Estado de los Submodulos

### 1. gestion-inventario-auth (.NET 8)
- **Puerto:** 5000/5001
- **Estado:** Completo
- **Commits:** 16 commits en main
- **Funcionalidades:**
  - Registro de usuarios
  - Inicio de sesion
  - JWT
  - PostgreSQL
- **Dependiente de:** Ninguno

### 2. gestion-inventario-service-inventory (Express 5)
- **Puerto:** 3001
- **Estado:** Completo
- **Commits:** 8 commits en main
- **Funcionalidades:**
  - CRUD Productos
  - Categorias
  - Entradas de inventario
  - Salidas de inventario
  - MongoDB
- **Dependiente de:** Auth (JWT)

### 3. gestion-inventario-service-reports (Express 5) - MI SERVICIO
- **Puerto:** 3005
- **Estado:** Completo (Sprint 1 y 2)
- **Commits en main:** 7 commits
- **Endpoints implementados:**
  - GET /alerts/low-stock (productos con stock bajo)
  - GET /alerts/out-of-stock (productos agotados)
  - GET /reports/top-products (productos mas vendidos)
  - GET /reports/categories (resumen por categoria)
  - GET /reports/summary (resumen general)
- **Dependiente de:** Auth (JWT) + Service A (HTTP)

### 4. gestion-inventario-frontend (React + Vite)
- **Puerto:** 5173
- **Estado:** En progreso
- **Commits:** 10 commits en main
- **Estructura:**
  ```
  src/
  ├── app/           # App principal, router
  ├── features/      # Modulos (auth, dashboard)
  ├── service/       # Servicios API (authService.js)
  ├── shared/        # Componentes compartidos (Layout)
  ├── assets/        # Recursos estaticos
  └── styles/        # Estilos globales
  ```
- **Funcionalidades implementadas:**
  - Login/Registro (LoginForm, RegisterForm)
  - Dashboard basico (DashboardPage)
  - Layout con header/nav
  - Rutas protegidas (AppRouter)
  - Zustand (authStore)
  - Servicio de autenticacion (authService.js)
- **Faltantes:**
  - Paginas de alertas (low-stock, out-of-stock)
  - Paginas de reportes (top-products, categories, summary)
  - Servicio para consumir Service B
  - Consumo de Service A (productos, entradas, salidas)
- **Dependiente de:** Auth + Service A + Service B

## Historial de Commits en Main (Service Reports)

| Hora | Commit | Descripcion |
|------|--------|-------------|
| 07:55 | 12a23c5 | feat: Commit Inicial |
| 08:17 | f7a815f | feat: estructura base del servicio |
| 08:42 | 87d1869 | Merge PR #2 |
| 09:03 | c6de65c | fix: env loading order |
| 09:18 | ab0c417 | feat: validacion params |
| 09:31 | 8300ac9 | feat: error handler |
| 09:50 | 1e06eff | Merge PR #4 |

## Pull Requests (Service Reports)

| PR | Titulo | Rama | Estado | Merge |
|----|--------|------|--------|-------|
| #2 | feat: estructura base | feat/service-reports-base | MERGED | 08:42 |
| #4 | feat: alertas y reportes | feat/sprint2-alertas-reportes | MERGED | 09:50 |

## Dependencias de Service B

```json
{
  "axios": "^1.18.1",
  "cors": "^2.8.6",
  "dotenv": "^17.4.2",
  "express": "^5.2.1",
  "express-rate-limit": "^8.5.2",
  "helmet": "^8.3.0",
  "jsonwebtoken": "^9.0.3",
  "mongoose": "^9.7.4",
  "morgan": "^1.11.0"
}
```

## Variables de Entorno (.env)

```
PORT=3005
NODE_ENV=development
URI_MONGODB=mongodb://localhost:27018/gestionInventario
INVENTORY_SERVICE_URL=http://localhost:3001/gestionInventario/v1
JWT_SECRET=55dtnITgUBY2ocnp8myCLtbJRdNWkCfdvhkcIS3OMpJScZkDwZFvB0yxRqZjoMpf7QbUqXO94cCrpNxUvIeWeg==!
JWT_EXPIRE=24h
```

## Docker

- **MongoDB reports:** Puerto 27018
- **MongoDB main:** Puerto 27017
- **Container:** gestion-inventario-mongo-reports

## Estructura de Service B

```
gestion-inventario-service-reports/
├── configs/
│   ├── app.js                    # Servidor Express
│   ├── db.js                     # Conexion MongoDB
│   ├── cors-configuration.js     # CORS
│   └── helmet-configuration.js   # Seguridad
├── controllers/
│   ├── alert-controller.js       # Logica de alertas
│   └── report-controller.js      # Logica de reportes
├── middlewares/
│   ├── handle-errors.js          # Manejo de errores + AppError
│   ├── request-limit.js          # Rate limiting
│   ├── validate-jwt.js           # Validacion JWT
│   └── validate-params.js        # Validacion query params
├── routes/
│   ├── alert-routes.js           # Rutas de alertas
│   └── report-routes.js          # Rutas de reportes
├── index.js                      # Punto de entrada
├── package.json
├── docker-compose.yml
├── .env
├── .gitignore
└── README.md
```

## Credenciales Compartidas

- **JWT Secret:** 55dtnITgUBY2ocnp8myCLtbJRdNWkCfdvhkcIS3OMpJScZkDwZFvB0yxRqZjoMpf7QbUqXO94cCrpNxUvIeWeg==!
- **Puertos:** Auth=5000, ServiceA=3001, ServiceB=3005, Frontend=5173
- **MongoDB:** 27017 (main), 27018 (reports)
