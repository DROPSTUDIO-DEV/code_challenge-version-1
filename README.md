# Sistema de Reservas de Vuelos (Flight Booking System)

## Descripción del ejercicio

Crear un sistema que permita a los usuarios buscar y reservar vuelos. La API se desarrollará con Laravel y la interfaz con Vue.js. Además, implementaremos un sistema de pagos simulado.

---

## Parte 1: Backend con Laravel (API REST)

### Requerimientos

1. **Autenticación de usuarios:** Utilizar Laravel Passport para la autenticación con OAuth2.
2. **Modelo de Vuelo:**
   - **Campos:**
     - `id` (autoincremental)
     - `flight_number` (string, requerido)
     - `departure_city` (string, requerido)
     - `arrival_city` (string, requerido)
     - `departure_time` (datetime, requerido)
     - `arrival_time` (datetime, requerido)
     - `price` (decimal, requerido)
     - `seats_available` (integer, requerido)
     - `created_at` (timestamp)
     - `updated_at` (timestamp)

3. **Modelo de Reserva:**
   - **Campos:**
     - `id` (autoincremental)
     - `user_id` (relación con el usuario, tipo `foreign key`)
     - `flight_id` (relación con el vuelo, tipo `foreign key`)
     - `number_of_seats` (integer, requerido)
     - `total_price` (decimal, requerido)
     - `status` (string, requerido, valores: `confirmada`, `cancelada`)
     - `created_at` (timestamp)
     - `updated_at` (timestamp)

4. **Endpoints requeridos:**
   - `GET /api/flights`: Listar todos los vuelos.
   - `GET /api/flights/{id}`: Obtener detalles de un vuelo específico.
   - `POST /api/bookings`: Crear una nueva reserva (debe verificar la disponibilidad de asientos).
   - `GET /api/bookings`: Listar todas las reservas del usuario autenticado.

5. **Simulación de pagos:** Implementar una lógica simple que simule un proceso de pago exitoso al crear una reserva.

---

## Parte 2: Frontend con Vue.js

### Requerimientos

1. **Autenticación de usuarios:**
   - Crear un formulario de inicio de sesión y registro que utilice OAuth2.
   - Almacenar el token de autenticación en `localStorage`.

2. **Búsqueda y Reserva de Vuelos:**
   - Crear una vista que permita a los usuarios buscar vuelos por ciudad de salida y llegada.
   - Mostrar una lista de vuelos con opción de ver detalles.
   - Implementar un formulario de reserva que permita seleccionar el número de asientos y confirme la reserva.
   - Mostrar una lista de reservas del usuario autenticado.

---

## Diagrama Entidad-Relación (ER)

Este es un diagrama que modela las entidades para el sistema de reservas de vuelos:

```
+—————————————————––+        +——————————————————––+
|      User         |        |       Flight       |
+—————–————————————–+        +—————––—————————————+
| id (PK)           |  <––>  | id (PK)            |
| name              |        | flight_number      |
| email             |        | departure_city     |
| password          |        | arrival_city       |
+—————————————————––+        | departure_time     |
| updated_at        |        | arrival_time       |
+—————––————————————+        | price              |
| seats_available   |        +—————––—————————————+
| created_at        |
| updated_at        |
+—————––————————————+

+—————————————————––+ 
|       Booking     |
+—————–————————————–+
| id (PK)           |
| user_id (FK)      |
| flight_id (FK)    |
| number_of_seats   |
| total_price       |
| status            |
| created_at        |
| updated_at        |
+—————––————————————+

```

#### Relación:
- **1 usuario tiene muchas reservas** (`One-to-Many`).
- **1 vuelo puede tener muchas reservas** (`One-to-Many`).

---

## Criterios de evaluación

1. **Backend (Laravel)**:
   - Uso correcto de Laravel Passport para la autenticación.
   - Buen manejo de rutas y controladores en el CRUD de vuelos y reservas.
   - Implementación efectiva de lógica para simular pagos.
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

- **Backend**: Proyecto Laravel completo con autenticación, modelos, controladores y lógica de simulación de pagos.
- **Frontend**: Aplicación Vue.js funcional para la búsqueda y reserva de vuelos.
