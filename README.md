# 🛒 ShopForge: E-commerce full stack

Tienda online completa con catálogo, carrito, pago y panel de administración.

> **Estado:** 🚧 en desarrollo 

## Funcionalidades previstas

- [ ] Registro, login y autenticación con JWT
- [ ] Catálogo de productos con categorías, búsqueda y filtros
- [ ] Carrito de compra persistente
- [ ] Checkout con pasarela de pago (Stripe, modo test)
- [ ] Gestión de pedidos y estados
- [ ] Control de stock transaccional
- [ ] Panel de administración (productos, pedidos, usuarios)
- [ ] Envío de correos de confirmación
- [ ] Documentación de la API (OpenAPI/Swagger)
- [ ] Despliegue en producción con base de datos gestionada

## Stack

| Capa | Tecnología |
|------|-----------|
| Backend | Java 21, Spring Boot 3 |
| Seguridad | Spring Security + JWT |
| Persistencia | Spring Data JPA, PostgreSQL, Flyway |
| Frontend | [React / Thymeleaf: por decidir] |
| Tests | JUnit 5, Mockito, Testcontainers |
| DevOps | Docker, GitHub Actions |

## Estructura del proyecto

```
ShopForge/
├── backend/                  # API REST con Spring Boot (organizada por módulos)
│   ├── src/main/java/com/shopforge/
│   │   ├── config/           # Configuración general (CORS, OpenAPI, beans)
│   │   ├── security/         # JWT, filtros, SecurityConfig
│   │   ├── user/             # Usuarios y roles
│   │   ├── catalog/          # Productos y categorías
│   │   ├── cart/             # Carrito
│   │   ├── order/            # Pedidos y estados
│   │   ├── payment/          # Integración con Stripe
│   │   ├── stock/            # Control de stock transaccional
│   │   ├── admin/            # Endpoints del panel de administración
│   │   ├── mail/             # Correos de confirmación
│   │   └── common/           # Utilidades y manejo de excepciones
│   ├── src/main/resources/
│   │   ├── application.yml
│   │   └── db/migration/     # Migraciones Flyway
│   ├── src/test/java/        # Tests (JUnit 5, Mockito, Testcontainers)
│   ├── Dockerfile
│   └── pom.xml
├── frontend/                 # Pendiente de decidir (React / Thymeleaf)
├── docs/                     # Documentación y decisiones de arquitectura
├── .github/workflows/ci.yml  # Integración continua
├── docker-compose.yml
├── .env.example
└── README.md
```

## Cómo ejecutarlo

Requisitos: Docker, y para desarrollo local Java 21 y Maven.

```bash
git clone https://github.com/Panchitis311/ShopForge.git
cd shopforge
cp .env.example .env
docker compose up --build
```

La API quedará disponible en `http://localhost:8080` y el estado en `http://localhost:8080/actuator/health`.

### Desarrollo local

```bash
docker compose up db -d      # solo PostgreSQL
cd backend
mvn spring-boot:run
```

### Tests

```bash
cd backend
mvn verify                   # requiere Docker (Testcontainers)
```

## Hoja de ruta

1. **Fase 1:** modelo de datos, autenticación y catálogo
2. **Fase 2:** carrito y pedidos
3. **Fase 3:** pagos y panel de administración
4. **Fase 4:** tests, documentación y despliegue

## Licencia

MIT
