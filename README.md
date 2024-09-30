# Plataforma de Aprendizaje Online (Online Learning Platform)

## Descripción del ejercicio

Crear una plataforma que permita a los usuarios registrarse, explorar cursos, inscribirse y realizar seguimiento de su progreso. La API se desarrollará con Laravel y la interfaz con Vue.js.

---

## Parte 1: Backend con Laravel (API REST)

### Requerimientos

1. **Autenticación de usuarios:** Utilizar Laravel Passport para la autenticación con OAuth2.
2. **Modelo de Curso:**
   - **Campos:**
     - `id` (autoincremental)
     - `title` (string, requerido)
     - `description` (texto largo, requerido)
     - `instructor_id` (relación con el usuario, tipo `foreign key`)
     - `created_at` (timestamp)
     - `updated_at` (timestamp)

3. **Modelo de Inscripción:**
   - **Campos:**
     - `id` (autoincremental)
     - `user_id` (relación con el usuario, tipo `foreign key`)
     - `course_id` (relación con el curso, tipo `foreign key`)
     - `progress` (decimal, requerido, valores entre 0 y 100)
     - `created_at` (timestamp)
     - `updated_at` (timestamp)

4. **Endpoints requeridos:**
   - `GET /api/courses`: Listar todos los cursos disponibles.
   - `GET /api/courses/{id}`: Obtener detalles de un curso específico.
   - `POST /api/enrollments`: Inscribirse en un curso (debe verificar si el usuario ya está inscrito).
   - `GET /api/enrollments`: Listar todos los cursos en los que el usuario está inscrito.

---

## Parte 2: Frontend con Vue.js

### Requerimientos

1. **Autenticación de usuarios:**
   - Crear un formulario de inicio de sesión y registro que utilice OAuth2.
   - Almacenar el token de autenticación en `localStorage`.

2. **Exploración y Gestión de Cursos:**
   - Crear una vista que permita a los usuarios explorar cursos disponibles.
   - Implementar un formulario para inscribirse en un curso.
   - Mostrar una lista de cursos en los que el usuario está inscrito, junto con su progreso.

---

## Diagrama Entidad-Relación (ER)

Este es un diagrama que modela las entidades para la plataforma de aprendizaje online:

```

+—————————————————––+        +——————————————————––+
|      User         |        |       Course       |
+—————–————————————–+        +—————––—————————————+
| id (PK)           |  <––>  | id (PK)            |
| name              |        | title              |
| email             |        | description        |
| password          |        | instructor_id (FK) |
+—————————————————––+        | created_at         |
| updated_at        |        | updated_at         |
+—————––————————————+        +—————––—————————————+


+—————————————————––+
|     Enrollment    |
+—————–————————————–+
| id (PK)           |
| user_id (FK)      |
| course_id (FK)    |
| progress          |
| created_at        |
| updated_at        |
+—————––————————————+

```

#### Relación:
- **1 usuario tiene muchas inscripciones** (`One-to-Many`).
- **1 curso puede tener muchas inscripciones** (`One-to-Many`).

---

## Criterios de evaluación

1. **Backend (Laravel)**:
   - Uso correcto de Laravel Passport para la autenticación.
   - Buen manejo de rutas y controladores en el CRUD de cursos y inscripciones.
   - Código limpio y buenas prácticas en el uso de Laravel.

2. **Frontend (Vue.js)**:
   - Fluidez en la autenticación y manejo de token.
   - Estructura clara del estado en `Vuex`.
   - Implementación de componentes Vue.js reutilizables.
   - Correcta comunicación con el backend a través de las API.

3. **General:**
   - Calidad y claridad del código.
   - Buen uso del control de versiones (Git).
   - Documentación sobre cómo ejecutar el proyecto.

---

## Instrucciones adicionales

1. El candidato debe utilizar **Git** para el control de versiones.
2. El proyecto debe ser entregado en un repositorio de GitHub/GitLab con instrucciones para clonar y ejecutar tanto el backend como el frontend.
3. Se evaluará no solo el funcionamiento, sino también el estilo de código, buenas prácticas y comprensión de la arquitectura API REST.

---

## Entrega esperada

- **Backend**: Proyecto Laravel completo con autenticación, modelos y controladores.
- **Frontend**: Aplicación Vue.js funcional para la exploración y gestión de cursos.

