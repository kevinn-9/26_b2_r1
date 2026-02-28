# Proyecto - Sistema de Gestión de Estudiantes

Este es un proyecto backend desarrollado con **Java 21** y **Spring Boot** para la gestión de estudiantes. Incluye una API RESTful que permite crear, leer, actualizar y eliminar (CRUD) registros de estudiantes, persistiendo los datos en una base de datos **PostgreSQL**.

## 🚀 Tecnologías Utilizadas

- **Java 21**: Lenguaje de programación.
- **Spring Boot 3.x**: Framework para el desarrollo de la aplicación.
- **Maven**: Gestor de dependencias y construcción.
- **PostgreSQL**: Base de datos relacional.
- **Lombok**: Librería para reducir el código boilerplate (Getters, Setters, etc.).
- **Spring Data JPA**: Abstracción para la capa de persistencia.

## 📋 Requisitos Previos

Asegúrate de tener instalado lo siguiente en tu entorno local:

- [Java JDK 21](https://www.oracle.com/java/technologies/downloads/#java21)
- [Maven](https://maven.apache.org/download.cgi)
- Cliente para probar la API (como [Postman](https://www.postman.com/) o [Insomnia](https://insomnia.rest/)).

## ⚙️ Configuración

La configuración de la base de datos se maneja a través de variables de entorno definidas en un archivo `.env` en la raíz del proyecto.

1.  Copia el archivo de ejemplo:
    ```bash
    copy .env.example .env
    ```

2.  Edita el archivo `.env` y define tus credenciales:
    ```ini
    DB_URL=jdbc:postgresql://localhost:5432/tu_base_de_datos
    DB_USERNAME=tu_usuario
    DB_PASSWORD=tu_contraseña
    ```

> **Nota:** El archivo `.env` está excluido del control de versiones para mantener tus credenciales seguras.

## 🛠️ Instalación y Ejecución (Windows)

1.  **Clonar el repositorio**:
    ```powershell
    git clone <url-del-repositorio>
    cd pi
    ```

2.  **Compilar el proyecto**:
    Asegúrate de estar en la raíz del proyecto y ejecuta:
    ```powershell
    .\mvnw.cmd clean install
    ```
    *Nota: Si tienes Maven instalado globalmente, puedes usar simplemente `mvn clean install`.*

3.  **Ejecutar la aplicación**:
    ```powershell
    .\mvnw.cmd spring-boot:run
    ```

    La aplicación se iniciará en el puerto `8080` (por defecto).

## 🔌 Uso de la API (Endpoints)

La API base es `/api/students`. A continuación se detallan los endpoints disponibles:

### 1. Obtener todos los estudiantes
- **Método**: `GET`
- **URL**: `/api/students`
- **Respuesta**: Lista de estudiantes en formato JSON.

### 2. Obtener un estudiante por ID
- **Método**: `GET`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`

### 3. Obtener un estudiante por Email
- **Método**: `GET`
- **URL**: `/api/students/email/{email}`
- **Ejemplo**: `/api/students/email/ejemplo@correo.com`

### 4. Crear un nuevo estudiante
- **Método**: `POST`
- **URL**: `/api/students`
- **Body (JSON)**:
    ```json
    {
      "firstName": "Juan",
      "lastName": "Pérez",
      "email": "juan.perez@example.com",
      "birthDate": "2000-01-15",
      "phone": "1234567890"
    }
    ```

### 5. Actualizar un estudiante
- **Método**: `PUT`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`
- **Body (JSON)**:
    ```json
    {
      "firstName": "Juan Carlos",
      "lastName": "Pérez",
      "email": "juan.perez@example.com",
      "birthDate": "2000-01-15",
      "phone": "0987654321"
    }
    ```

### 6. Eliminar un estudiante
- **Método**: `DELETE`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`

## 🧪 Ejecutar Pruebas

Para ejecutar las pruebas unitarias y de integración, usa el siguiente comando:

```powershell
.\mvnw.cmd test
```

## 📂 Estructura del Proyecto

```
src/main/java/com/cesde/pi
├── controller    # Controladores REST (StudentController)
├── model         # Entidades JPA (Student)
├── repository    # Interfaces de Repositorio (StudentRepository)
├── service       # Lógica de Negocio (StudentService)
├── dto           # Objetos de Transferencia de Datos
└── exception     # Manejo de Excepciones Globales
```
# Laboratorio: Documentación de Pruebas de API REST

## Información del estudiante
- **nombre** kevin velez barrera

---

## Pruebas de Endpoints

### 1. Crear estudiante (POST)
- **Método**: `POST`
- **URL**: `http://localhots:8080/api/students`
- **Cuerpo de la petición**: 
```json


{
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "phone": "3004445566"
       
    
}
```
- **Código de estado**:`201 Created`
- **Respuesta del servidor**:
```json

{
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "Ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "phone": "3004445566"
       
    
}
```

---

### 2. Obtener lista completa (GET)
- **Método**: `GET`
- **URL**: `http://localhots:8080/api/students`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**:`200 OK`
- **Respuesta del servidor**:
```json
[
    {
        "firstName": "Ana",
        "lastName": "Garcia",
        "email": "Ana.garcia@estudiante.com",
        "birthDate": "2001-03-12",
        "id": 1,
        "phone": "3004445566"
    },
    {
        "firstName": "Camilo",
        "lastName": "Rodriguez",
        "email": "camilo.rodriguez@example.com",
        "birthDate": "1994-09-30",
        "id": 2,
        "phone": "3112223344"
    },
    {
        "firstName": "Valentina",
        "lastName": "Lopez",
        "email": "valentina.lopez@example.com",
        "birthDate": "1998-12-05",
        "id": 3,
        "phone": "3123334455"
    },
    {
        "firstName": "Sebastian",
        "lastName": "Morales",
        "email": "sebastian.morales@example.com",
        "birthDate": "1992-06-14",
        "id": 4,
        "phone": "3134445566"
    }
]
```

### 3. Buscar estudiante por ID (GET)
- **Método**: `GET`
- **URL**: `http://localhost:8080/api/students/1`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**:`200 OK`
- **Respuesta del servidor**:
```json
{
	"firstName": "Ana",
    "lastName": "Garcia",
    "email": "Ana.garcia@estudiante.com",
    "birthDate": "2001-03-1",
    "phone": "3004445566"
       
    
}
```

### 4. Buscar estudiante por Email (GET)
- **Método**: `GET`
- **URL**: `http://localhost:8080/api/students/email/Ana.garcia@estudiante.com`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**: `200 OK`
- **Respuesta del servidor**:
```json
{
    "firstName": "Ana",
    "lastName": "Garcia",
    "email": "Ana.garcia@estudiante.com",
    "birthDate": "2001-03-1",
    "id": 1,
    "phone": "3004445566"
}
```

### 5. Actualizar datos del estudante (PUT)
- **Método**: `PUT`
- **URL**: `http://localhost:8080/api/students/1`
- **Cuerpo de la petición**: 
```json
  {
        "firstName": "Ana Actualizado",
        "lastName": "Garcia",
        "email": "Ana.garcia@estudiante.com",
        "birthDate": "2001-03-1",
        "id": 1,
        "phone": "3004445566"
    }
```
- **Código de estado**: `200 OK`
- **Respuesta del servidor**:
```json
    {
    "firstName": "David Actualizado",
    "lastName": "Martinez",
    "email": "David.ortiz@example.com",
    "birthDate": "1993-05-22",
    "id": 5,
    "phone": "3235622409"
}
```

### 6.Escenario de error: Buscar ID inexistente (GET)
- **Método**: `GET`
- **URL**: `http:localhost:8080/api/students/999`
- **Cuerpo de la petición**: Sin body
```json

```
- **Código de estado**: `404 Not Found`
- **Respuesta del servidor**:
```json

```

### 7. Eliminar registro (DELETE)
- **Método**: `DELETE`
- **URL**: `http:localhost:8080/api/students/4`
- **Cuerpo de la petición**: Sin Body
```json

```
- **Código de estado**: `204 No Content`
- **Respuesta del servidor**:
```json

```


# Cuestionario de Análisis

## 1. ¿Cuál es la diferencia entre los códigos de estado 200 y 201? ¿En qué endpoints se obtuvieron cada uno?

El código *200 (OK)* indica que la solicitud se realizó correctamente y el servidor devuelve información. Generalmente se obtiene en endpoints como:

- GET (consultar datos)
- PUT (actualizar datos)
- DELETE (cuando devuelve confirmación)

El código *201 (Created)* indica que el recurso fue creado exitosamente en el servidor. Se obtiene normalmente en:

- POST (cuando se crea un nuevo registro, por ejemplo, crear un estudiante)

La diferencia principal es que *200 confirma éxito en una operación normal, mientras que **201 confirma que se creó un nuevo recurso*.

---

## 2. En el escenario de error (punto 6), ¿qué información devuelve la API y por qué es importante para el frontend recibir un código 404 en lugar de un 500?

En un error como el 404, la API devuelve un mensaje indicando que el recurso no fue encontrado (por ejemplo: "Estudiante no encontrado").

Es importante que el frontend reciba un *404 (Not Found)* y no un *500 (Internal Server Error)* porque:

- El *404* indica que el problema es que el recurso no existe (error controlado).
- El *500* indica un fallo interno del servidor (error grave o no controlado).

Para el desarrollador frontend, el 404 permite mostrar un mensaje claro al usuario, mientras que el 500 indica que algo está mal en el backend.

---

## 3. ¿Qué sucede en la base de datos PostgreSQL cuando se ejecuta con éxito la petición DELETE?

Cuando la petición DELETE se ejecuta con éxito:

- El registro correspondiente se elimina físicamente de la tabla.
- El cambio queda persistido en la base de datos.
- Si la operación se confirma (commit), el dato ya no puede consultarse posteriormente.

En términos de persistencia, significa que el dato deja de existir en el almacenamiento permanente.

---

## 4. Si intentara crear un estudiante con el mismo email que ya existe en la base de datos, ¿qué sucedería y qué código de error sería el más adecuado?

Si el email tiene una restricción de unicidad (UNIQUE) en la base de datos:

- La base de datos lanzará un error por violación de restricción.
- La API debería capturar ese error.

El código más adecuado para devolver sería:

*409 (Conflict)*

Porque indica que el recurso que se intenta crear entra en conflicto con uno existente.

---

## 5. ¿Por qué utilizamos el método PUT para actualizar y no POST? ¿Cuál es la convención técnica detrás de esta decisión?

Según la convención REST:

- *POST* se usa para crear nuevos recursos.
- *PUT* se usa para actualizar un recurso existente.

La razón técnica es que:

- PUT es idempotente (si se ejecuta varias veces produce el mismo resultado).
- POST no es idempotente (puede crear múltiples recursos si se repite).

Por eso, para actualizar un estudiante ya existente, se usa *PUT*, porque estamos modificando un recurso específico y no creando uno nuevo.