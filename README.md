# TareasAPI
Taller de creacion de API REST con .NET

Para la realización inicial del taller se siguen los pasos del siguiente tutorial: https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-5.0&tabs=visual-studio
Nos aseguramos de elegir la versión de ASP.NET que vayamos a usar (en este caso ha sido la 5.0)

La diferencia que se va a incluir respecto del tutorial original de Microsoft, es que este está pensado para usar una base de datos "InMemory", para hacerlo más sencillo. Sin embargo, 
en nuestro caso usaremos una base de datos SQL que crearemos usando la aproximación Code First y usaremos las librerías de EntityFramework para gestionarla. Leer más: https://www.entityframeworktutorial.net/code-first/what-is-code-first.aspx

Lo que se ha realizado es:
1. Crear un proyecto nuevo de tipo ASP.NET Core Web API y probarlo (viene por defecto con una aplicación plantilla). Modificamos el launchUrl (ver tutorial)
2. Crear el modelo de datos en código, en este caso se define una única entidad que serían las tareas en una clase llamada TodoItem. Importante respetar nombre del campo identidad Id.
3. Se crea el DbContext, que será una clase que heredando de DbContext incluirá un DbSet para la entidad TodoItem. El contexto será lo que maneje como un envoltorio
el acceso a la base de datos, y que luego será gestionado por un servicio inyector de dependencias.
4. Desde el administrador de paquetes NuGet del proyecto, buscamos e instalamos el EntityFramework.SqlServer (ya que vamos a usar un SQL Server como servidor de base de datos)
5. Se realizan una serie de cambios en el archivo Startup.cs (esto es diferente en ASP.NET 6.0, ver tutorial) para comentar la parte de swagger y registrar el contexto de base de datos en 
el servicio contenedor de inyección de dependencias. (Ver código subido)
6. Hacemos scaffolding para generar automáticamente una serie de métodos de la API para manejar un CRUD para la entidad indicada, en el caso será para TodoItem

En este punto ya sólo nos quedará crear la base de datos usando el modelo creado, para luego probar la API usando Postman.

Para llevar nuestro modelo a una base de datos SQL Server, Visual Studio tiene unas herramientas de migración (si la base de datos ya existe no tiene sentido usarlas tal cual,
hay que estudiar el caso). Vamos a:
1. Crear la cadena de conexion: 
Si abrimos la consola del gestión de paquetes del proyecto y ejecutamos las siguientes instrucciones:

7. Add-Migration InitialCreate
Update-Database
Aquí, en el paso Add a Model, veréis el paso que os comento: https://docs.microsoft.com/en-us/aspnet/core/tutorials/razor-pages/model?view=aspnetcore-5.0&tabs=visual-studio




Tecnologías de acceso a datos vistas: EntityFramework, Code First, API REST y herramienta Postman.
Otras interesantes: Swagger, estándar OpenAPI. Inyección de Dependencias. Método scaffolding.
