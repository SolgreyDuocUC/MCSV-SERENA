# Serena API - Microservicios de Gestión Emocional

Conjunto de microservicios desarrollados para la gestión de usuarios, emociones y registros emocionales para la aplicación móvil `Serena`.

---

## Integrantes

* Diego Arias
* Solgrey Medina

---

## Arquitectura de Microservicios

El backend consta de tres microservicios independientes. La justificación de esta arquitectura es la **modularidad**, permitiendo el desarrollo y escalabilidad de cada dominio de negocio por separado.



| Microservicio | Puerto | Responsabilidad | Enlace Swagger (Local) |
| :--- | :--- | :--- | :--- |
| **MCSV-USER** | `8091` | Gestión de Usuarios | `http://localhost:8091/swagger-ui/index.html` |
| **MCSV-EMOTION** | `8092` | Catálogo y CRUD de Emociones | `http://localhost:8092/swagger-ui/index.html` |
| **MCSV-EMOTIONAL-REGISTER** | `8093` | Creación y Consulta de Registros | `http://localhost:8093/swagger-ui/index.html` |

*Se muestran las entidades, controladores y rutas de cada microservicio en la estructura de código fuente.*

---

## Documentación de Endpoints

Se detallan las principales rutas (controladores) y sus métodos utilizados por la aplicación móvil. La comunicación es fluida y refleja los cambios realizados en la base de datos a la aplicación.

### GESTIÓN DE EMOCIONES (MCSV-EMOTION)

| Método | Ruta del Endpoint | Descripción | Ejemplo de Datos de Entrada |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/v1/emotions` | Listar todas las emociones | No aplica |
| `POST` | `/api/v1/emotions` | Crear una emoción | `{ "name": "...", "description": "..." }` |
| `PUT` | `/api/v1/emotions/{id}` | Actualizar emoción por ID | `{ "name": "Alegría intensa" }` |
| `DELETE` | `/api/v1/emotions/{id}` | Eliminar emoción por ID | Identificar en la ruta |

### REGISTRO EMOCIONAL (MCSV-EMOTIONAL-REGISTER)

| Método | Ruta del Endpoint | Descripción | Ejemplo de Datos de Entrada |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/v1/emotional-registers` | Listar todos los registros | No aplica |
| `POST` | `/api/v1/emotional-registers` | Crear un nuevo registro | `{ "date": "...", "emotion": {"id": 1}, "user": {"id": 1} }` |

### GESTIÓN DE USUARIOS (MCSV-USER)

| Método | Ruta del Endpoint | Descripción | Ejemplo de Datos de Entrada |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/v1/users` | Listar todos los usuarios | No aplica |
| `POST` | `/api/v1/users` | Crear un nuevo usuario | `{ "userName": "...", "userEmail": "..." }` |

### Microservicios y URLs Base

* **MCSV-USER (Gestión de Usuarios y Autenticación)**
  URL Base: [http://localhost:8091](http://localhost:8091)
  Swagger: [http://localhost:8091/swagger-ui/index.html](http://localhost:8091/swagger-ui/index.html)

* **MCSV-EMOTION (Catálogo de Emociones)**
  URL Base: [http://localhost:8092](http://localhost:8092)
  Swagger: [http://localhost:8092/swagger-ui/index.html](http://localhost:8092/swagger-ui/index.html)

* **MCSV-EMOTIONAL-REGISTER (Registros Emocionales)**
  URL Base: [http://localhost:8093](http://localhost:8093)
  Swagger: [http://localhost:8093/swagger-ui/index.html](http://localhost:8093/swagger-ui/index.html)

No se identificaron endpoints externos (de terceros) en la documentación del proyecto.

## Endpoints Principales

### Gestión de Usuarios (MCSV-USER)

* **GET** `/api/v1/users`
  Lista todos los usuarios.

* **POST** `/api/v1/users`
  Crea un nuevo usuario.

* **GET** `/api/v1/users/{id}`
  Obtiene un usuario por su identificador.

* **GET** `/api/v1/users/email/{email}`
  Busca un usuario por correo electrónico.

* **PUT** `/api/v1/users/{id}`
  Actualiza la información de un usuario.

* **DELETE** `/api/v1/users/{id}`
  Elimina un usuario.

### Sesión Activa (MCSV-USER)

* **GET** `/api/v1/user-active-sessions`
  Lista las sesiones activas.

* **GET** `/api/v1/user-active-sessions/{id}`
  Obtiene una sesión activa por ID.

* **POST** `/api/v1/user-active-sessions`
  Crea una sesión activa.

* **PUT** `/api/v1/user-active-sessions/{id}`
  Actualiza una sesión activa.

* **DELETE** `/api/v1/user-active-sessions/{id}`
  Elimina una sesión activa.

### Autenticación con Token (MCSV-USER)

* **POST** `/api/v1/auth/register`
  Registro de usuario con generación de token.

* **POST** `/api/v1/auth/login`
  Inicio de sesión con credenciales y obtención de token.

### Gestión de Emociones (MCSV-EMOTION)

* **GET** `/api/v1/emotions`
  Lista todas las emociones disponibles.

* **GET** `/api/v1/emotions/{id}`
  Obtiene una emoción por ID.

* **POST** `/api/v1/emotions`
  Crea una nueva emoción.

* **PUT** `/api/v1/emotions/{id}`
  Actualiza una emoción existente.

* **DELETE** `/api/v1/emotions/{id}`
  Elimina una emoción.

### Registro Emocional del Usuario (MCSV-EMOTIONAL-REGISTER)

* **GET** `/api/v1/emotional-registers`
  Lista todos los registros emocionales.

* **GET** `/api/v1/emotional-registers/{id}`
  Obtiene un registro emocional por ID.

* **POST** `/api/v1/emotional-registers`
  Crea un nuevo registro emocional.

* **PUT** `/api/v1/emotional-registers/{id}`
  Actualiza un registro emocional existente.

* **DELETE** `/api/v1/emotional-registers/{id}`
  Elimina un registro emocional.

---

## Instrucciones para Ejecutar el Proyecto

1.  **Requisitos:** Entorno de desarrollo Java (JDK 17+) y gestor de dependencias (Maven/Gradle).
2.  **Configuración de BD:** Asegúrese de configurar las credenciales y el tipo de base de datos para cada microservicio en sus respectivos archivos de configuración (`application.properties` o `application.yml`).
3.  **Clonar Repositorio Backend:**
    ```bash
    git clone https://github.com/SolgreyDuocUC/MCSV-SERENA
    ```
4.  **Ejecución:** Ejecutar cada microservicio de forma independiente:
    ```bash
    # Ejemplo de ejecución
    cd MCSV-USER
    ./gradlew bootRun
    ```
5.  **Verificación:** Abrir los enlaces de Swagger (listados en la tabla de Arquitectura) para verificar que los servicios estén operativos antes de iniciar la aplicación móvil.

---

## Código Fuente y Colaboración

### Código Fuente

* **Código Fuente Completo:** `https://github.com/SolgreyDuocUC/MCSV-SERENA`

### Evidencia de Trabajo Colaborativo

* El trabajo se gestionó mediante el uso de ramas y planificación de tareas (Trello u otra herramienta).
* **Commits Individuales:** Revisar el historial de commits en el repositorio para validar las contribuciones de:
    * Diego Arias
    * Solgrey Medina

# Serena - Aplicación de Bienestar Emocional

## Descripción General

Serena es una aplicación móvil desarrollada para el registro y seguimiento de estados emocionales, con el objetivo de fomentar el bienestar mental de los usuarios. La aplicación permite gestionar perfiles, registrar emociones y sincronizar la información con un backend basado en microservicios.

## Integrantes del Equipo

* Diego Arias
* Solgrey Medina

