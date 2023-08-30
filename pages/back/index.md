# Estructura del Proyecto

## Configuración de la Aplicación Web

En este archivo de configuración, se definen varias configuraciones relacionadas con la gestión de recursos y filtros para una aplicación web.
El de la clase `WebConfig` realiza una configuración detallada para manejar los recursos estáticos y establece un filtro personalizado para las URLs de la aplicación web.

### Configuración de Recursos

La clase `WebConfig` implementa la interfaz `WebMvcConfigurer` para personalizar la configuración de la aplicación web.

```java
@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void addResourceHandlers(ResourceHandlerRegistry registry) {
        // Configuración de manejo de recursos estáticos

        registry.addResourceHandler("/**")  // Patrón URL para los recursos
                .addResourceLocations("classpath:/static/static")  // Ubicación de los recursos físicos
                .resourceChain(false)  // Desactiva el manejo de la cadena de recursos
                .addResolver(new PathResourceResolver() {
                    @Override
                    protected Resource getResource(String resourcePath, Resource location) throws IOException, java.io.IOException {
                        // Lógica para obtener el recurso solicitado
                        Resource requestedResource = location.createRelative(resourcePath);
                        return requestedResource.exists() && requestedResource.isReadable() ? requestedResource : new ClassPathResource("/static/index.html");
                    }
                });  // Agrega un resolvedor personalizado para recursos
    }

    // Otros métodos de configuración y beans...
}
```

## Explicación

En el código proporcionado, se realiza una configuración importante relacionada con la gestión de recursos y filtros en una aplicación web.

### Configuración de Recursos

En la implementación del método `addResourceHandlers`, se lleva a cabo la configuración del manejo de recursos estáticos:

- Se utiliza el método `addResourceHandlers` para agregar un manejador de recursos a la aplicación web. Este manejador se encargará de servir recursos estáticos, como archivos CSS, imágenes y JavaScript.
- El patrón de URL `"/**"` especifica que todos los recursos, independientemente de su ubicación, serán manejados por este manejador.
- El método `addResourceLocations` define la ubicación física de los recursos estáticos en el sistema de archivos. En este caso, los recursos se buscarán en la ruta `classpath:/static/static`.
- La llamada a `resourceChain(false)` desactiva el manejo de la cadena de recursos, lo que significa que no se realizará una búsqueda en cascada de recursos en diferentes ubicaciones.
- Se agrega un resolvedor personalizado utilizando `addResolver`. Este resolvedor de recursos personalizado extiende `PathResourceResolver` y proporciona una lógica para obtener el recurso solicitado. Si el recurso solicitado existe y es legible, se devuelve ese recurso. De lo contrario, se devuelve un recurso de índice (`index.html`) desde la ubicación de clase (`classpath:/static/index.html`).

### Configuración de Filtros

También se define un filtro utilizando un bean en la clase `WebConfig`:

- Se utiliza el método `spaWebFilter` para crear y registrar un filtro personalizado llamado `SpaWebFilter`.
- El filtro se configura para que actúe en todas las URL (`"/*"`) de la aplicación.
- El filtro `SpaWebFilter` se define y establece como el filtro a utilizar en la configuración.
