# Documentación de la Clase EmailService

La clase `EmailService` es un servicio en Spring que se encarga de manejar el envío y la recepción de correos electrónicos. Proporciona métodos para leer correos electrónicos entrantes desde una bandeja de entrada IMAP y para enviar correos electrónicos utilizando el protocolo SMTP.

## Atributos

La clase utiliza atributos que son configurados a través de propiedades de la aplicación:

- `emailUsername`: Usuario del correo electrónico.
- `emailPassword`: Contraseña del correo electrónico.
- `emailHost`: Host del servidor de correo entrante (IMAP).
- `emailPort`: Puerto del servidor de correo entrante (IMAP).
- `emailProtocol`: Protocolo para el servidor de correo entrante (IMAP).
- `emailSender`: Dirección de correo electrónico del remitente.
- `emailSmtpHost`: Host del servidor SMTP saliente.
- `emailSmtpPort`: Puerto del servidor SMTP saliente.
- `emailSmtpProtocol`: Protocolo para el servidor SMTP saliente.
- `emailSmtpUser`: Usuario del servidor SMTP saliente.
- `emailsmtpSender`: Dirección de correo electrónico del remitente para el servidor SMTP.

## Métodos

### `readIncomingMail()`

Este método lee correos electrónicos entrantes desde una bandeja de entrada IMAP configurada. Retorna una lista de mensajes (`Message`) correspondientes a los correos electrónicos entrantes.

**Excepciones:**

- `MessagingException`: Se lanza si ocurre un error al leer los correos electrónicos.

### `sendEmail(String recipient, String subject, String body)`

Este método envía un correo electrónico utilizando el protocolo SMTP.

**Parámetros:**

- `recipient` (String): Correo electrónico del destinatario.
- `subject` (String): Asunto del correo electrónico.
- `body` (String): Cuerpo del correo electrónico.

**Excepciones:**

- `MessagingException`: Se lanza si ocurre un error al enviar el correo electrónico.

## Configuración

Los atributos de configuración son inyectados a través de la anotación `@Value` utilizando las propiedades de la aplicación.

## Dependencias

El servicio depende de las siguientes bibliotecas y clases:

- `javax.mail`: Proporciona clases para el envío y la recepción de correos electrónicos.
- `org.springframework.beans.factory.annotation.Value`: Utilizada para inyectar valores de propiedades.
