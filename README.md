# Sistema de Gestión de Contactos (Contacts Management System)

## Descripción del ejercicio

Crear un sistema que permita a los usuarios autenticados gestionar sus contactos (crear, leer, actualizar y eliminar). La API se desarrollará con Laravel y la interfaz con Vue.js.

---

## Parte 1: Backend con Laravel (API REST)

### Requerimientos

1. **Autenticación de usuarios:** Utilizar Laravel Breeze para configurar la autenticación por API (JWT o Sanctum).
2. **CRUD de Contactos:** Crear un CRUD para los contactos. Cada usuario solo puede ver, crear, actualizar y eliminar sus propios contactos.
   - **Modelo:** `Contact`
   - **Campos:**
     - `id` (autoincremental)
     - `name` (string, requerido)
     - `email` (string, opcional)
     - `phone` (string, opcional)
     - `user_id` (relación con el usuario autenticado, tipo `foreign key`)
     - `created_at` (timestamp)
     - `updated_at` (timestamp)

3. **Endpoints requeridos:**
   - `POST /api/contacts`: Crear un nuevo contacto.
   - `GET /api/contacts`: Listar todos los contactos del usuario autenticado.
   - `GET /api/contacts/{id}`: Obtener detalles de un contacto específico.
   - `PUT /api/contacts/{id}`: Actualizar un contacto.
   - `DELETE /api/contacts/{id}`: Eliminar un contacto.

4. **Políticas de acceso:** Utilizar políticas de Laravel para asegurarse de que los usuarios solo puedan manipular sus propios contactos.

---

## Parte 2: Frontend con Vue.js

### Requerimientos

1. **Autenticación de usuarios:**
   - Implementar un formulario de inicio de sesión que se comunique con la API para autenticar al usuario.
   - Almacenar el token de autenticación (usando `localStorage` o `Vuex`).

2. **Gestión de Contactos:**
   - Crear un dashboard que muestre una lista de contactos del usuario autenticado.
   - Implementar formularios para **crear**, **actualizar** y **eliminar** contactos.
   - Utilizar componentes de Vue.js para dividir el código y facilitar la reutilización.

---

## Diagrama Entidad-Relación (ER)

Este es un diagrama simplificado que modela las entidades para el sistema de gestión de contactos:

```

+—————————————————––+        +——————————————————––+
|      User         |        |      Contact       |
+—————–————————————–+        +—————–—————————————–+
| id (PK)           |  <––>  | id (PK)            |
| name              |        | name               |
| email             |        | email              |
| password          |        | phone              |
+—————–————————————–+        | user_id (FK)       |
| created_at        |        +—————––—————————————+
| updated_at        |
+—————––————————————+

```

#### Relación:
- **1 usuario tiene muchos contactos** (`One-to-Many`): Cada usuario puede tener múltiples contactos asociados, pero un contacto pertenece a un único usuario.

---

## Criterios de evaluación

1. **Backend (Laravel)**:
   - Uso correcto de Laravel Breeze para autenticación basada en API.
   - Buen manejo de rutas y controladores en el CRUD de contactos.
   - Correcta implementación de políticas de acceso (cada usuario solo puede manejar sus propios contactos).
   - Código limpio y buenas prácticas en el uso de Laravel.

2. **Frontend (Vue.js)**:
   - Fluidez en la autenticación y manejo de token.
   - Manejo eficiente del estado de la aplicación.
   - Implementación de componentes Vue.js reutilizables.
   - Correcta comunicación con el backend a través de las API.

3. **General:**
   - Calidad y claridad del código.
   - Buen uso del control de versiones (Git).
   - Documentación mínima sobre cómo ejecutar el proyecto.

---

## Instrucciones adicionales

1. El candidato debe utilizar **Git** para el control de versiones, asegurándose de hacer commits frecuentes y descriptivos.
2. El proyecto debe ser entregado en un repositorio de GitHub/GitLab con las instrucciones necesarias para clonar y ejecutar tanto el backend como el frontend.
3. Se evaluará no solo si el CRUD funciona, sino también el estilo de código, buenas prácticas y la comprensión de la arquitectura API REST.

---

## Entrega esperada

- **Backend**: Proyecto Laravel con rutas, controladores, modelos y autenticación configurados.
- **Frontend**: Aplicación Vue.js con un sistema funcional de autenticación y gestión de contactos.
