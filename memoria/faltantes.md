# Faltantes segun PDF - Sprint 3

## Estado Actual de los Servicios

### Service Auth (.NET) ✅ COMPLETO
- [x] Registro de usuarios
- [x] Inicio de sesion
- [x] JWT
- [x] PostgreSQL

### Service A (Inventory) ✅ COMPLETO
- [x] CRUD Productos
- [x] Categorias
- [x] Entradas de inventario
- [x] Salidas de inventario
- [x] MongoDB
- [x] JWT validation

### Service B (Alertas y Reportes) ✅ COMPLETO
- [x] GET /alerts/low-stock
- [x] GET /alerts/out-of-stock
- [x] GET /reports/top-products
- [x] GET /reports/categories
- [x] GET /reports/summary
- [x] JWT validation
- [x] Comunicacion HTTP con Service A
- [x] Manejo de errores
- [x] Validacion de parametros

### Frontend (React) ⚠️ EN PROGRESO
- [x] Login/Registro
- [x] Dashboard basico
- [x] Rutas protegidas
- [ ] Dashboard completo de alertas
- [ ] Pagina de reportes
- [ ] Consumo de Service B desde Frontend
- [ ] Manejo de errores del usuario

## Faltantes para Sprint 3

### Obligatorios (PDF)
1. **Dashboard completo de alertas** - Frontend debe mostrar low-stock y out-of-stock
2. **Reportes completos** - Frontend debe consumir los 5 endpoints de Service B
3. **Resumen general del inventario** - Frontend debe mostrar /reports/summary
4. **Integracion final del sistema** - Todos los servicios comunicandose
5. **Aplicacion completamente funcional** - Todo deve poder usarse desde el Frontend
6. **Pull Request final** - Integrar todo a main

### Mirol (Service B)
- Ya esta completo segun el PDF
- Solo falta que el Frontend consuma mis endpoints
- Puedo ayudar con integracion si es necesario

## Requisitos Minimos Obligatorios (PDF)

- [x] Servicio de Autenticacion independiente
- [x] Arquitectura distribuida (React + 3 services)
- [x] Unico repositorio (Monorepo)
- [x] Registro e inicio de sesion con JWT
- [x] Contrasenas con Argon2 (Auth .NET)
- [x] Cada servicio en puerto diferente
- [x] Cada servicio con su propio proyecto
- [x] MongoDB para persistencia
- [x] Comunicacion HTTP entre servicios
- [x] Minimo 2 endpoints en Auth
- [x] Minimo 5 endpoints en Service A
- [x] Minimo 3 endpoints en Service B (tenemos 5)
- [x] Interfaz funcional
- [x] Metodologia Scrum (3 sprints)
- [x] Trabajo en ramas
- [x] Integracion via Pull Requests
- [x] Historial de commits colaborativo
- [ ] README con instrucciones de ejecucion (falta en raiz)
- [ ] Aplicacion funcionando al finalizar

## Acciones Pendientes

1. **Frontend:** Crear paginas de alertas y reportes
2. **Frontend:** Consumir endpoints de Service B
3. **Integracion:** Probar todo junto
4. **README:** Crear en la raiz del monorepo
5. **PR final:** Integrar todo a main
