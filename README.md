# Sistema de Gestion de Inventario

Aplicacion web funcional para la administracion de inventario, desarrollo con arquitectura distribuida basada en multiples servicios.

## Arquitectura

```
sistema-gestion-inventario/
├── gestion-inventario-auth/          # API de Autenticacion (.NET 8)
├── gestion-inventario-service-inventory/  # API de Inventario (Express 5)
├── gestion-inventario-service-reports/    # API de Alertas y Reportes (Express 5)
├── gestion-inventario-frontend/           # Frontend (React + Vite)
└── memoria/                               # Documentacion del proyecto
```

## Tecnologias

- **Frontend:** React, Vite, Zustand, Axios, React Router
- **Backend:** Node.js, Express 5, .NET 8
- **Base de datos:** MongoDB, PostgreSQL
- **Autenticacion:** JWT (JSON Web Tokens)
- **Contenedores:** Docker

## Puertos

| Servicio | Puerto |
|----------|--------|
| Frontend | 5173 |
| Auth API | 5000/5001 |
| Service A (Inventario) | 3001 |
| Service B (Alertas/Reportes) | 3005 |
| MongoDB Main | 27017 |
| MongoDB Reports | 27018 |

## Instalacion

### Requisitos
- Node.js 18+
- .NET 8 SDK
- Docker y Docker Compose
- Git

### Pasos

1. Clonar el repositorio con submodulos:
```bash
git clone --recursive git@github.com:marcss-bnajera/sistema-gestion-inventario.git
cd sistema-gestion-inventario
```

2. Iniciar contenedores Docker:
```bash
docker-compose up -d
```

3. Instalar dependencias de cada servicio:
```bash
# Auth
cd gestion-inventario-auth
dotnet restore

# Service A
cd ../gestion-inventario-service-inventory
npm install

# Service B
cd ../gestion-inventario-service-reports
npm install

# Frontend
cd ../gestion-inventario-frontend
npm install
```

4. Configurar variables de entorno (copiar .env.example a .env en cada servicio)

5. Iniciar cada servicio:
```bash
# Auth
cd gestion-inventario-auth
dotnet run --project src/AuthService.Api

# Service A
cd gestion-inventario-service-inventory
npm run dev

# Service B
cd gestion-inventario-service-reports
npm run dev

# Frontend
cd gestion-inventario-frontend
npm run dev
```

## Endpoints

### Auth API
- POST /auth/register - Registro de usuarios
- POST /auth/login - Inicio de sesion

### Service A (Inventario)
- GET /products - Listar productos
- GET /products/:id - Obtener producto
- POST /products - Crear producto
- PUT /products/:id - Actualizar producto
- DELETE /products/:id - Eliminar producto
- POST /entries - Registrar entrada
- POST /outputs - Registrar salida
- GET /categories - Listar categorias

### Service B (Alertas y Reportes)
- GET /alerts/low-stock - Productos con stock bajo
- GET /alerts/out-of-stock - Productos agotados
- GET /reports/top-products - Productos mas vendidos
- GET /reports/categories - Resumen por categoria
- GET /reports/summary - Resumen general

## Metodologia

Proyecto desarrollado con Scrum:
- Sprint 1: Configuracion inicial y primeros endpoints
- Sprint 2: Logica principal del sistema
- Sprint 3: Finalizacion e integracion

## Equipo

- Scrum Master (Service Auth)
- Backend Developer (Servicio A)
- Backend Developer (Servicio B) - Jcraxker
- Frontend Developer
