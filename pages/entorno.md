# **Requisitos previos para el desarrollo y despliegue.**

# Configuración de Entorno

¡Bienvenido a la página de Configuración de Entorno! Aquí te guiaremos a través del proceso de levantar el proyecto que combina la potencia de React en el front-end y Spring en el back-end. A continuación, te proporcionamos instrucciones detalladas sobre cómo configurar, compilar y ejecutar esta aplicación para lograr una experiencia de desarrollo fluida.

## Levantando el Proyecto React:

### Requisitos Previos:

Asegúrate de tener Node.js y npm instalados en tu sistema. Puedes verificar su instalación ejecutando los comandos `node -v` y `npm -v` en tu terminal.

### Navega al Directorio Front-End:

Abre la terminal y navega hasta el directorio donde se encuentra el código del front-end de tu proyecto.

### Instala Dependencias:

Ejecuta `npm install` para instalar todas las dependencias necesarias definidas en el archivo `package.json`.

### Iniciar el Servidor de Desarrollo:

Utiliza el comando `npm start` para levantar un servidor de desarrollo. Tu aplicación React estará disponible en [http://localhost:3000](http://localhost:3000).

## Levantando el Proyecto Spring:

### Configuración de la Base de Datos:

Asegúrate de configurar correctamente la base de datos en la configuración de Spring, incluyendo URL, usuario y contraseña.

### Navega al Directorio Back-End:

En tu terminal, navega hasta el directorio del back-end de tu proyecto.

### Compilación y Empaquetado:

Utiliza herramientas de construcción como Maven o Gradle para compilar y empaquetar tu proyecto Spring en un archivo `.war`.

### Configuración de Rutas Estáticas:

Una vez que tienes el archivo `.war`, despliégalo en un servidor de aplicaciones compatible, como Apache Tomcat. Asegúrate de configurar correctamente las rutas estáticas para los archivos generados por React.

## Integrando el Front-End con el Back-End:

### Copia de los Archivos de Build:

Después de compilar el proyecto React, copia la carpeta `build` generada en la carpeta `static` del proyecto Spring. Esto permitirá que Spring sirva los archivos estáticos de React.

### Configuración de Rutas en Spring:

Asegúrate de configurar las rutas adecuadas en Spring para manejar las solicitudes al front-end y al back-end de manera correcta.

Siguiendo estos pasos, lograrás levantar y desplegar tanto el front-end React como el back-end Spring en un entorno armonioso. Esta configuración te permitirá aprovechar al máximo las capacidades combinadas de estas tecnologías y ofrecer una experiencia completa y eficiente en tu proyecto.
