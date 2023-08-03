# Proyecto Spring con Spring Cloud y Spring Config Server Client

Este proyecto utiliza el ecosistema de Spring Cloud para gestionar la configuración de una aplicación mediante un servidor de configuración centralizado. La arquitectura involucra varios componentes que trabajan en conjunto para proporcionar configuraciones externas y gestionarlas de manera dinámica. A continuación, se explican los componentes y su funcionamiento:

## Componentes de la arquitectura:

1. **Spring Cloud Config Server:**
   - Este es un servidor centralizado que almacena las configuraciones externas de la aplicación. Estas configuraciones se suelen almacenar en un repositorio git, lo que permite versionar y auditar los cambios en la configuración de la aplicación.
   - Proporciona un API para acceder a las propiedades configuradas para diferentes perfiles y aplicaciones.

2. **Repositorio Git:**
   - Es donde se almacenan las configuraciones externas de la aplicación. Puede ser cualquier sistema de control de versiones git (por ejemplo, GitHub, GitLab, Bitbucket, etc.).
   - Cada aplicación puede tener diferentes archivos de configuración para cada perfil (por ejemplo, desarrollo, producción, pruebas, etc.), y el Config Server se encarga de entregar la configuración correcta según el perfil activo.

3. **Spring Config Server Client:**
   - Es una aplicación que se comunica con el Config Server para obtener su configuración externa.
   - Este cliente es una parte del proyecto Spring que se desarrolla para utilizar las configuraciones proporcionadas por el Config Server.

## Funcionamiento:

1. **Spring Config Server:**
   - Se inicia como un servidor independiente que se conecta al repositorio git para leer las configuraciones almacenadas en él.
   - Cuando el Config Server recibe una solicitud de configuración desde un cliente, verifica el perfil activo y la aplicación específica.
   - Luego, consulta el repositorio git correspondiente para recuperar las configuraciones apropiadas y las devuelve al cliente.

2. **Repositorio Git:**
   - Contiene los archivos de configuración en formato de propiedades, YAML o JSON, según la elección del desarrollador.
   - Puede haber diferentes ramas o directorios para gestionar las configuraciones de diferentes ambientes o perfiles.

3. **Spring Config Server Client:**
   - Esta aplicación Spring se inicia y actúa como un cliente del Config Server.
   - Al arrancar, solicita las configuraciones necesarias al Config Server para la aplicación y el perfil activo.
   - Una vez que recibe las configuraciones, las usa para configurar sus componentes y servicios en tiempo de ejecución.
