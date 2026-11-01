# API REST de Productos — Spring Boot

API REST para administrar un catálogo de productos y categorías, con seguridad basada en JWT y documentación interactiva con Swagger. Proyecto académico (UNAM) desarrollado una funcionalidad por rama, integrando cada una con pull requests.

## Tecnologías

- Java 17 · Spring Boot 3.4
- Spring Web · Spring Data JPA · Bean Validation
- Spring Security + JWT (autorización por roles)
- MySQL
- Swagger / OpenAPI (springdoc)
- Maven

## Funcionalidades

- CRUD de **categorías** y **productos**, con activación y desactivación lógica.
- **Carga de imágenes** de productos.
- **Validación** de datos de entrada con DTOs.
- **Manejo centralizado de excepciones** con respuestas de error uniformes.
- **Seguridad**: filtro JWT que lee el token `Bearer`, extrae los permisos y protege los endpoints por rol (`ADMIN`).
- **Documentación** de la API en Swagger UI.

## Arquitectura

```
controller  →  service  →  repository  →  MySQL
     ↑             ↑
    DTOs       entidades JPA
```

- `api/controller`: endpoints REST (`/category`, `/product`, `/product-image`).
- `api/service`: lógica de negocio.
- `api/repository`: acceso a datos con Spring Data JPA.
- `api/dto`: objetos de entrada y salida.
- `config`: seguridad (JWT, CORS) y OpenAPI.
- `exception`: manejo global de errores.

## Endpoints principales

| Método | Ruta | Descripción |
| --- | --- | --- |
| GET | `/category` | Lista las categorías |
| GET | `/category/active` | Lista las categorías activas |
| POST | `/category` | Crea una categoría |
| PUT | `/category/{id}` | Actualiza una categoría |
| PATCH | `/category/{id}/enable` · `/disable` | Activa o desactiva una categoría |
| GET | `/product` | Lista los productos |
| GET | `/product/{id}` | Consulta un producto |
| POST | `/product` | Crea un producto |
| PUT | `/product/{id}` | Actualiza un producto |
| PATCH | `/product/{id}/enable` · `/disable` | Activa o desactiva un producto |
| POST | `/product-image` | Sube una imagen de producto |

## Cómo ejecutarlo

Requisitos: Java 17, Maven y MySQL.

```bash
cd product
# configura tu base de datos en src/main/resources/application.properties
./mvnw spring-boot:run
```

Documentación: `http://localhost:8080/swagger-ui/index.html`

## Historial de desarrollo

Cada práctica se desarrolló en su propia rama y se integró con pull requests:

`p2_api-product` → `p3_jpa` → `p4_exception` → `p5_crud-category` → `p6_product_image` → `p8_swagger` → `p7_login`

## Autor

Edwin Rodríguez Nevárez · edrodnev@gmail.com
