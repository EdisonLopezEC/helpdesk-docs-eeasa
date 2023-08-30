# Documentación de la Clase EmailController

La clase `EmailController` es un controlador de Spring que maneja operaciones relacionadas con el envío y recepción de correos electrónicos. Permite leer correos electrónicos entrantes y enviar correos electrónicos a destinatarios especificados.

## Endpoints

### `GET /email`

Este endpoint lee los correos electrónicos entrantes y crea registros de tickets en la base de datos. Luego, devuelve la lista de tickets en formato JSON.

**Parámetros:**

- Ninguno

**Respuesta:**

- 200 OK: Devuelve una lista de tickets en formato JSON.
- 500 Internal Server Error: En caso de cualquier error interno.

### `POST /email/send`

Este endpoint permite enviar correos electrónicos a un destinatario especificado.

**Parámetros:**

- `recipient` (String): El correo electrónico del destinatario.
- `subject` (String): El asunto del correo electrónico.
- `body` (String): El cuerpo del correo electrónico.

**Respuesta:**

- 200 OK: El correo electrónico se envió exitosamente.
- 500 Internal Server Error: En caso de error al enviar el correo electrónico.

## Métodos Privados

### `getMessageContent(Message message)`

Este método obtiene el contenido de un mensaje de correo electrónico. Puede ser un contenido de texto plano o HTML.

### `scheduleIncomingMailService()`

Este método programa la ejecución periódica del método `getIncomingMail()` para leer los correos electrónicos entrantes.

## Configuración

El controlador utiliza anotaciones de Spring para definir su comportamiento. Estas anotaciones incluyen:

- `@RestController`: Indica que la clase es un controlador que manejará las solicitudes HTTP.
- `@CrossOrigin(origins = "*")`: Permite solicitudes de cualquier origen.
- `@RequestMapping("/email")`: Establece la ruta base para los endpoints en este controlador.

## Inicialización

El método `init()` está anotado con `@PostConstruct`, lo que significa que se ejecutará después de que la clase se haya construido y todas las dependencias se hayan inyectado. En este método, se inicia la tarea programada para leer los correos electrónicos entrantes a intervalos regulares.
