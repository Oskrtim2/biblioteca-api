# Biblioteca API

API REST para un sistema de gestión de biblioteca, desarrollada con Spring Boot y MongoDB Atlas.

Este proyecto fue hecho como parte del taller de Diseño de Software (4° semestre). La idea es manejar el CRUD completo de libros siguiendo la arquitectura por capas.

## Tecnologías usadas

- Java 21
- Spring Boot 3.3.0
- Spring Data MongoDB
- MongoDB Atlas (cluster gratuito M0)
- Lombok
- Maven

## Estructura del proyecto

```
src/main/java/com/biblioteca/
├── controller/       → Endpoints REST
├── dto/              → Objetos de transferencia (Request/Response)
├── model/            → Entidades de MongoDB
├── repository/       → Acceso a datos
├── service/          → Lógica de negocio
│   └── impl/         → Implementaciones
└── BibliotecaApiApplication.java
```

## Cómo ejecutar

1. Clonar el repositorio
2. Abrir el proyecto en IntelliJ IDEA
3. Configurar la URI de MongoDB Atlas en `src/main/resources/application.properties`
4. Ejecutar `BibliotecaApiApplication.java`

La API corre en `http://localhost:8080`

## Endpoints

| Método | URL | Descripción |
|--------|-----|-------------|
| POST | `/api/libros` | Crear un libro |
| GET | `/api/libros` | Listar todos los libros |
| GET | `/api/libros/{id}` | Consultar un libro por ID |
| PUT | `/api/libros/{id}` | Actualizar un libro |
| DELETE | `/api/libros/{id}` | Eliminar un libro |

## Ejemplo de uso (Postman)

**Crear un libro** — `POST /api/libros`
```json
{
  "isbn": "978-0-13-468599-1",
  "titulo": "Clean Code",
  "autor": "Robert C. Martin",
  "anioPublicacion": 2008,
  "categoria": "Programación"
}
```

**Respuesta** — `201 Created`
```json
{
  "id": "64a8f2b3c4d5e6f7a8b9c0d1",
  "isbn": "978-0-13-468599-1",
  "titulo": "Clean Code",
  "autor": "Robert C. Martin",
  "anioPublicacion": 2008,
  "categoria": "Programación"
}
```

## Configuración de MongoDB Atlas

En el archivo `application.properties` hay que poner la cadena de conexión del cluster:

```properties
spring.data.mongodb.uri=mongodb+srv://usuario:contraseña@tu-cluster.mongodb.net/biblioteca_db?retryWrites=true&w=majority
```

El cluster se puede crear gratis en [mongodb.com/atlas](https://www.mongodb.com/atlas) con el tier M0.
