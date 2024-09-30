# Sistema de Gestión de Proyectos (Project Management System)

## Descripción del ejercicio

Crear un sistema que permita a los usuarios gestionar proyectos, tareas dentro de esos proyectos y asignar tareas a diferentes usuarios. La API se desarrollará con Laravel y la interfaz con Vue.js.

---

## Parte 1: Backend con Laravel (API REST)

### Requerimientos

1. **Autenticación de usuarios:** Utilizar Laravel Passport para la autenticación con OAuth2.
2. **Modelo de Proyecto:**
   - **Campos:**
     - `id` (autoincremental)
     - `name` (string, requerido)
     - `description` (texto largo, requerido)
     - `status` (string, requerido, valores: `activo`, `completado`, `archivado`)
     - `owner_id` (relación con el usuario, tipo `foreign key`)
     - `created_at` (timestamp)
     - `updated_at` (timestamp)

3. **Modelo de Tarea:**
   - **Campos:**
     - `id` (autoincremental)
     - `project_id` (relación con el proyecto, tipo `foreign key`)
     - `title` (string, requerido)
     - `description` (texto largo, opcional)
     - `status` (string, requerido, valores: `pendiente`, `en progreso`, `completada`)
     - `assigned_to` (relación con el usuario, tipo `foreign key`, opcional)
     - `created_at` (timestamp)
     - `updated_at` (timestamp)

4. **Endpoints requeridos:**
   - `POST /api/projects`: Crear un nuevo proyecto.
   - `GET /api/projects`: Listar todos los proyectos del usuario autenticado.
   - `GET /api/projects/{id}`: Obtener detalles de un proyecto específico.
   - `PUT /api/projects/{id}`: Actualizar un proyecto.
   - `DELETE /api/projects/{id}`: Eliminar un proyecto.
   - `POST /api/projects/{id}/tasks`: Crear una nueva tarea para un proyecto específico.
   - `GET /api/projects/{id}/tasks`: Listar todas las tareas de un proyecto específico.
   - `PUT /api/tasks/{id}`: Actualizar una tarea.
   - `DELETE /api/tasks/{id}`: Eliminar una tarea.

5. **Políticas de acceso:** Implementar políticas para asegurar que los usuarios solo puedan acceder a sus propios proyectos y tareas. 

---

## Parte 2: Frontend con Vue.js

### Requerimientos

1. **Autenticación de usuarios:**
   - Crear un formulario de inicio de sesión y registro, que utilice OAuth2 para autenticarse.
   - Almacenar el token de autenticación en `localStorage`.

2. **Gestión de Proyectos y Tareas:**
   - Crear una vista de dashboard que muestre una lista de proyectos del usuario autenticado.
   - Dentro de cada proyecto, permitir la visualización y gestión de tareas.
   - Implementar la creación, actualización y eliminación de proyectos y tareas utilizando componentes Vue.js.
   - Utilizar `Vuex` para el manejo del estado de los proyectos y tareas.

---

## Diagrama Entidad-Relación (ER)

Este es un diagrama que modela las entidades para el sistema de gestión de proyectos:

```
+—————————————————––+        +——————————————————––+
|      User         |        |       Project      |
+—————–————————————–+        +—————––—————————————+
| id (PK)           |  <––>  | id (PK)            |
| name              |        | name               |
| email             |        | description        |
| password          |        | status             |
+—————————————————––+        | owner_id (FK)      |
| updated_at        |        | created_at         |
+—————––————————————+        | updated_at         |
                             +—————––—————————————+


+—————————————————––+     
|       Task        |
+—————–————————————–+
| id (PK)           |
| project_id (FK)   |
| title             |
| description       |
| status            |
| assigned_to (FK)  |
| created_at        |
| updated_at        |
+—————––————————————+
```

#### Relación:
- **1 usuario tiene muchos proyectos** (`One-to-Many`).
- **1 proyecto tiene muchas tareas** (`One-to-Many`).
- **1 tarea puede ser asignada a un usuario** (`Many-to-One`).

---

## Criterios de evaluación

1. **Backend (Laravel)**:
   - Uso correcto de Laravel Passport para la autenticación.
   - Buen manejo de rutas y controladores en el CRUD de proyectos y tareas.
   - Implementación efectiva de políticas de acceso.
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

- **Backend**: Proyecto Laravel completo con autenticación, modelos, controladores y políticas configuradas.
- **Frontend**: Aplicación Vue.js funcional para la gestión de proyectos y tareas.
