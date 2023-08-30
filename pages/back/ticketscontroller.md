# Documentación de la Clase TicketsController

La clase `TicketsController` es un controlador de Spring que maneja operaciones relacionadas con los tickets de solicitud de servicio. Proporciona endpoints para consultar, crear y actualizar tickets, así como obtener estadísticas sobre los tickets por estado y año.

## Endpoints

### `GET /tickets`

Este endpoint devuelve una lista de todos los tickets de solicitud de servicio.

**Parámetros:**

- `Authorization` (Header): Token de autorización.

**Respuesta:**

- 200 OK: Devuelve una lista de tickets en formato JSON.
- 401 Unauthorized: Si el token de autorización no es válido.
- 400 Bad Request: En caso de cualquier otro error.

### `GET /tickets/{id}`

Este endpoint devuelve un ticket específico según su ID.

**Parámetros:**

- `Authorization` (Header): Token de autorización.
- `id` (Path): ID del ticket.

**Respuesta:**

- 200 OK: Devuelve el ticket en formato JSON.
- 401 Unauthorized: Si el token de autorización no es válido.
- 400 Bad Request: En caso de cualquier otro error.

### `POST /tickets`

Este endpoint crea un nuevo ticket.

**Parámetros:**

- `Authorization` (Header): Token de autorización.
- `ticket` (Body): Datos del nuevo ticket.

**Respuesta:**

- 201 Created: El ticket se creó exitosamente.
- 401 Unauthorized: Si el token de autorización no es válido.
- 400 Bad Request: En caso de error al crear el ticket.

### `PUT /tickets/{id}`

Este endpoint actualiza un ticket existente.

**Parámetros:**

- `Authorization` (Header): Token de autorización.
- `id` (Path): ID del ticket a actualizar.
- `ticket` (Body): Datos actualizados del ticket.

**Respuesta:**

- 200 OK: El ticket se actualizó exitosamente.
- 401 Unauthorized: Si el token de autorización no es válido.
- 400 Bad Request: En caso de error al actualizar el ticket.

### `POST /tickets/techicalProgress`

Este endpoint envía una notificación de progreso técnico al remitente del ticket.

**Parámetros:**

- `Authorization` (Header): Token de autorización.
- `remitente` (Query): Correo electrónico del remitente.

**Respuesta:**

- 200 OK: La notificación se envió exitosamente.
- 401 Unauthorized: Si el token de autorización no es válido.
- 400 Bad Request: En caso de error al enviar la notificación.

### `POST /tickets/technicalComplete`

Este endpoint envía una notificación de finalización técnica al remitente del ticket.

**Parámetros:**

- `Authorization` (Header): Token de autorización.
- `remitente` (Query): Correo electrónico del remitente.

**Respuesta:**

- 200 OK: La notificación se envió exitosamente.
- 401 Unauthorized: Si el token de autorización no es válido.
- 400 Bad Request: En caso de error al enviar la notificación.

### Otros Endpoints

Existen endpoints adicionales para obtener estadísticas sobre los tickets por estado y año, como `/ticketsComplete`, `/ticketsRequired`, `/ticketsHold`, `/ticketsAsigned`, `/ticketsOpen`, `/ticketsComplete/{year}`, `/ticketsRequired/{year}`, etc. Los parámetros y respuestas son similares a los mencionados anteriormente.

## Métodos Privados

La clase contiene métodos privados para verificar la autenticación del usuario utilizando el token de autorización.

## Configuración

La clase utiliza anotaciones de Spring para definir su comportamiento, incluyendo `@RestController`, `@CrossOrigin`, y `@RequestMapping`.

## Dependencias

La clase depende de las siguientes clases y servicios:

- `TicketRepository`: Repositorio de tickets para acceder a la base de datos.
- `EmailService`: Servicio para enviar correos electrónicos.
- `UsuarioService`: Servicio para verificar tokens de usuario.

## Autor

Este controlador fue implementado por el equipo de desarrollo de la aplicación.
