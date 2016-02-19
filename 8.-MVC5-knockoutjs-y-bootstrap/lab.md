#WebApps con C-Sharp
###MVC5 - KnockOut - Bootstrap
###Conectándonos con DocumentDB

Este tutorial te permitirá conocer y manejar los conceptos y principios de desarrollo de Asp.Net MVC, al mismo tiempo te ayudará a comprender el manejo de ajax utilizando knockout, así como los conceptos de diseño utilizando Bootstrap.

AL final tendremos una aplicación modular que te permita cargar los datos de manera dinámica utilizando una base de datos NoSql Azure DocumentDB.

Para esto es necesario contar con:
- Visual Studio 2015 cualquiera de sus versiones, puedes descargar la versión gratuita [Visual Studio Community aquí](https://www.visualstudio.com/downloads/download-visual-studio-vs).
- Una cuenta de Azure (Azure Pass)
- Haber hecho el ejercicio para la creación de una [Base de datos en DocumentDB aquí](https://github.com/Ninja-Labs/azure/blob/master/6.%20WebApps%20MVC%20Core%20and%20Entity%20Framework/Lab%202/lab.md) o en este [otro link](http://DocumentDB_Miguel)

##Tareas
- [Tarea 1 - MVC 5 WebApps.](#tarea-1)
- [Tarea 2 - Crear una aplicación web ASP.Net MVC.](#tarea-2)
- [Tarea 3 - Instalando las Librerías requeridas para nuestro ejemplo.](#tarea-3)
- [Tarea 4 - Construyendo Nuestro Model (Modelo).](#tarea-4)
- [Tarea 5 - Nuestro Controller (Controlador).] (#tarea-5)
- [Tarea 6 - Nuestra View (Vista).] (#tarea-6)
- [Tarea 7 - Creando los Archivos de enrutado (condicional).] (#tarea-7)
- [Tarea 8 - Knockoutjs conectándonos con el controller.] (#tarea-8)
- [Tarea 9 - Mostrando datos en nuestra vista.] (#tarea-9)
- [Tarea 10 - Desde Cero sobre HTML.] (#tarea-10)
- [Tarea 11 - Bootstrap para nuestra UI Html.] (#tarea-11)
- [Tarea 12 - Vínculos de interés.] (#tarea-12)

###Tarea 1
####MVC 5 WebApps
Modelo Vista Controlador es un paradigma de programación que distribuye la carga del código con base en los 3 componentes que la integran, un resumen podría ser el de la siguiente grafica:

![MVC](img/MVCBasic.png)

Otra manera de verlo sería agregando un componente Usuario al paradigma de MVC.

![MVC](img/MVCBasic1.png)

Se puede encontrar más información y profundizar en el tema en diferentes sitios en internet así como en publicaciones, al final dejaremos un listado de vínculos que podrían ser de interés para ésto.

###Tarea 2
####Crear una aplicación web ASP.Net MVC
Para nuestro laboratorio utilizaremos Visual Studio 2015 (VS) y utilizando el framework 4.6

- Abrimos Visual Studio y seleccionamos la opción Crear Nuevo Proyecto y seleccionamos la opcion Web para ver las plantillas correspondientes, seleccionamos ASP.NET Web Applicacion (aplicaciones web de Asp.Net).

![MVC](img/T01_01.png)

- En la ventana que se abre seleccionamos la opción Empty (vacia) y dejamos sin seleccional la casilla Host in the cloud (Host en la nube). También seleccionaremos los folders y librerías que necesitamos para iniciar, en este caso MVC y Web API (como se ve en la grafica de abajo) que requeriremos para nuestro trabajo y hacemos clic en OK.

![MVC](img/T01_02.png)

- Se abrirá nuestro ambiente de desarrollo en el que veremos las carpetas y archivos que cargó la plantilla por defecto, debería verse así:

![MVC](img/T01_03.png)

###Tarea 3
####Instalando las Librerías requeridas para nuestro ejemplo
Para nuestro proyecto requerimos instalar o actualizar las libresrías que necesitaremos y son:
-- DocumentDB
-- NewtonSoft
-- jQuery
-- Knockoutjs
-- Bootstrap

- Aunque hay diferentes formas de cargar las librerías que requerimos, en este proyecto vacio vamos a cargarlas utilizando NuGet Packages (Paquetes NuGet), para esto hacemos clic derecho sobre <strong>References</strong> y hacemos clic sobre la opción Manage Nuget Packages.

![MVC](img/T03_01.png)

- Para las ultimas versiones de VS se abrirá la ventana que permitirá seleccionar si lo que queremos es buscar (Browse), ver los paquetes instalados (Installed), o que paquetes pueden ser actualizados (Updates). Seleccionaremos la opción Browse.

![MVC](img/T03_02.png)

- En la caja de texto de búsqueda escribiremos DocumentDB para buscar la librería correspondiente, escribiremos Microsoft.Azure.DocumentDB y al resultado seleccionaremos la opción Microsoft.Azure.DocumentDB y dejaremos la ultima versión estable que aparezca en el listado de la derecha.

![MVC](img/T03_03.png)

- Hacemos clic en Install (Instalar) y los aceptamos (clic en OK y Aceptar) en las ventanas emergentes que aparezcan.

Al revisar en las referencias podemos ver que ha quedado instalada la referencia de Azure Document Client.

![MVC](img/T03_04.png)

- Ahora realizaremos el mismo procedimiento para instalar los paquetes correspondientes de Newtonsoft, esto nos permitirá trabajar con formatos json dentro de nuestro sistema, requerido para comunicarnos con DocumentDB. 

Es necesario aclarar que Newtonsoft ya esta instalado dentro de la aplicación, sin embargo el procedimiento nos permitirá descargar la última versión estable del paquete. Hacemos clic sobre la opción update (Actualizar).

![MVC](img/T03_05.png)

Si aparecen ventanas emergentes hacemos clic en OK o aceptar.

- Ahora instalaremos jQuery realizando el mismo procedimiento que hemos realizado hasta ahora escribiendo jQuery en el cuadro de texto de búsqueda del NuGet package.

Hacemos clic sobre Install (instalar), si aparecen ventanas emergentes hacemos clic en OK o aceptar.

![MVC](img/T03_06.png)

- Debe aparecer una nueva carpeta Scripts con los archivos javascript corresponsdientes a jquery dentro de la nueva carpeta.

![MVC](img/T03_07.png)

- El siguiente paso es instalar knockoutjs, para esto realizaremos el procesimiento de buscarlo en el NuGet packages e instalamos de la misma forma que hemos instalado los paquetes anteriores.

![MVC](img/T03_08.png)

- Aparecen los archivos correspondientes dentro de la carpeta Scripts de nuestro proyecto.

![MVC](img/T03_09.png)

- Ahora finalizaremos instalando el paquete de Bootstrap que utilizaremos en las tareas finales de nuestro laboratorio, el procedimiento es el mismo que con los elementos anteriores dentro del manejador de paquetes NuGet.

![MVC](img/T03_10.png)

- Acá el resultado es especial ya que tendremos una carpeta Content que tendrá los estilos asociados con Bootstrap, una carpeta Fonts que trae unas fuentes especiales que nos permitiran implementar grifos o imágenes como si fueran fuentes de tezto y también tenemos los archivos javascript asociados a Bootstrap para poder implementar funcionalidades de diseño.

![MVC](img/T03_11.png)

Con el procedimiento anterior, ya estamos preparados para construir nuestra aplicación.

###Tarea 4
####Construyendo Nuestro Model (Modelo)

Nos basaremos en el ejercicio realizado con [DocumentDB anterior](https://github.com/Ninja-Labs/azure/blob/master/6.%20WebApps%20MVC%20Core%20and%20Entity%20Framework/Lab%202/lab.md) del cual tomaremos el código y lo integrarémos a nuestra aplicación.

- Lo que haremos es crear la clase <strong>Movie</strong> dentro de nuestra carpeta Models, haciendo clic derecho sobre la carpeta y seleccionando la opción Add->New Item... (Agregar->Nuevo elemento)

![MVC](img/T04_01.png)

- A esta clase deberá quedar de la siguiente manera:
```
using System;
using Newtonsoft.Json;

namespace MVC_HOL.Models
{
    public class Movie
    {
        [JsonProperty(PropertyName = "id")]
        public string Id { get; set; }

        [JsonProperty(PropertyName = "name")]
        public string Name { get; set; }

        [JsonProperty(PropertyName = "description")]
        public string Description { get; set; }

        [JsonProperty(PropertyName = "year")]
        public int Year { get; set; }

        [JsonProperty(PropertyName = "genre")]
        public string Genre { get; set; }
    }
}
```

- El valor ```[JsonProperty(PropertyName = "id")]``` viene de Newtonsoft.Json y es el valor que le daremos al nombre de ese campo dentro del formato Json que se construirá de nuestro modelo. 

- Ahora crearemos la clase <strong>MovieRepository</strong> dentro de nuestra carpeta Models, haciendo clic derecho sobre la carpeta y seleccionando la opción Add->New Item... (Agregar->Nuevo elemento)

![MVC](img/T04_01.png)

- Trabajaremos con 'C#', por esa razón en la ventana emergente seleccionaremos esta opción en lenguaje, así como seleccionaremos Code (Código) y la plantilla Class (Clase), recordemos darle el nombre <strong>Movie</strong> y hacemos clic en Add (Agregar)

![MVC](img/T04_04.png)

- Lo que haremos es crear la clase <strong>MovieRepository</strong> dentro de nuestra carpeta Models, haciendo clic derecho sobre la carpeta y seleccionando la opción Add->New Item... (Agregar->Nuevo elemento)

![MVC](img/T04_01.png)

- Trabajaremos con 'C#', por esa razón en la ventana emergente seleccionaremos esta opción en lenguaje, así como seleccionaremos Code (Código) y la plantilla Class (Clase), recordemos darle el nombre <strong>MovieRepository</strong> y hacemos clic en Add (Agregar)

![MVC](img/T04_02.png)

- Al final nuestra carpeta Models deberá quedar con estos dos archivos:

![MVC](img/T04_05.png)

- A nuestra clase MovieRepository le agregamos la referencia <strong>using System.Collections.Generic</strong>, <strong>using System.Linq</strong>, <strong>using System.Threading.Tasks</strong> para trabajar un método asíncrono, <strong>using Microsoft.Azure.Documents</strong>, <strong>using Microsoft.Azure.Documents.Client</strong>, <strong>using Microsoft.Azure.Documents.Linq</strong> estás últimas para poder llamar a las clases correspondientes de conexión a DocumentDB.

- Luego le agregaremos las variables de conexión, así como el llamado al cliente correspondiente, el código debe quedar de la siguiente manera:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.Azure.Documents;
using Microsoft.Azure.Documents.Client;
using Microsoft.Azure.Documents.Linq;

namespace MVC_HOL.Models
{
    public class MovieRepository
    {
        private const string EndpointUrl = "https://suendpoint.documents.azure.com:443/";//la direccion del endpoint de su conexión
        private const string AuthorizationKey = "Su_AuthorizationKey==";
        private const string CollectionId = "movies";
        private const string DatabaseId = "azurecampdb";

        private static DocumentClient client;

        private static DocumentClient Client
        {
            get
            {
                if (client == null)
                    client = new DocumentClient(new Uri(EndpointUrl), AuthorizationKey);

                return client;
            }
        }
		
		//código para database
		...
		
		
		//codigo para collection
		...
    }
}
```

- En este punto empezaremos a construir la conexión con el acceso a datos agregando el código que nos permitirá conectarnos con el repositorio de datos:
```
	private static Database database;
    private static Database Database
    {
        get
        {
            if (database == null)
                database = GetOrCreateDatabase(DatabaseId);

            return database;
        }
    }
```
- Ahora nos conectámos con la colección dentro de la base de datos:
```
	private static DocumentCollection collection;
    private static DocumentCollection Collection
    {
        get
        {
            if (collection == null)
            {
                collection = GetOrCreateCollection(Database.SelfLink, CollectionId);
            }

            return collection;
        }
    }

```
- Agregamos los métodos que comprueban si existe la base de datos, si no existe la crea, así mimso el método que crea o verifica si existe la colección.
```
	public static Database GetOrCreateDatabase(string databaseId)
    {
        var db = Client.CreateDatabaseQuery()
                        .Where(d => d.Id == databaseId)
                        .AsEnumerable()
                        .FirstOrDefault();

        if (db == null)
            db = client.CreateDatabaseAsync(new Database { Id = databaseId }).Result;

        return db;
    }

	public static DocumentCollection GetOrCreateCollection(string databaseLink, string collectionId)
    {
        var col = Client.CreateDocumentCollectionQuery(databaseLink)
                          .Where(c => c.Id == collectionId)
                          .AsEnumerable()
                          .FirstOrDefault();

        if (col == null)
        {
            col = client.CreateDocumentCollectionAsync(databaseLink,
                new DocumentCollection { Id = collectionId },
                new RequestOptions { OfferType = "S1" }).Result;
        }

        return col;
    }
```
- Ahora agregaremos el método que trae todos los datos asociados con nuestra clase Movie 
```
	public static IEnumerable<Movie> GetAllMovies()
    {
        var movies = Client.CreateDocumentQuery<Movie>(Collection.SelfLink).AsEnumerable();
        return movies;
    }
```
- Continuamos con el método que nos trae un único dato de la base de datos utilizando el Id del objeto que llamamos:
```
	public static Movie GetMovieById(string id)
    {
        var movie = Client.CreateDocumentQuery<Movie>(Collection.SelfLink)
            .Where(d => d.Id == id)
            .AsEnumerable()
            .FirstOrDefault();

        return movie;
    }
```
- Por último le agregamos el método que permitirá agregar un nuevo registro a la base de datos:
```
	public static async Task<Movie> CreateMovie(Movie entity)
    {
        Document doc = await Client.CreateDocumentAsync(Collection.SelfLink, entity);
        Movie movie = (Movie)(dynamic)doc;

        return movie;
    }
```
Éste último método es de tipo asíncrono por eso es necesario plantear que es una tarea y al mismo tiempo agregarle las palabras reservadas async y await, así como la referencia using System.Threading.Tasks.

#####El código completo de la clase MovieRepository.cs quedaría de la siguiente manera:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.Azure.Documents;
using Microsoft.Azure.Documents.Client;
using Microsoft.Azure.Documents.Linq;

namespace MVC_HOL.Models
{
    public class MovieRepository
    {
        private const string EndpointUrl = "https://suendpoint.documents.azure.com:443/";//la direccion del endpoint de su conexión
        private const string AuthorizationKey = "Su_AuthorizationKey==";
        private const string CollectionId = "movies";
        private const string DatabaseId = "azurecampdb";

        private static DocumentClient client;

        private static DocumentClient Client
        {
            get
            {
                if (client == null)
                    client = new DocumentClient(new Uri(EndpointUrl), AuthorizationKey);

                return client;
            }
        }

        private static Database database;
        private static Database Database
        {
            get
            {
                if (database == null)
                    database = GetOrCreateDatabase(DatabaseId);

                return database;
            }
        }

        public static Database GetOrCreateDatabase(string databaseId)
        {
            var db = Client.CreateDatabaseQuery()
                            .Where(d => d.Id == databaseId)
                            .AsEnumerable()
                            .FirstOrDefault();

            if (db == null)
                db = client.CreateDatabaseAsync(new Database { Id = databaseId }).Result;

            return db;
        }

        private static DocumentCollection collection;
        private static DocumentCollection Collection
        {
            get
            {
                if (collection == null)
                {
                    collection = GetOrCreateCollection(Database.SelfLink, CollectionId);
                }

                return collection;
            }
        }

        public static DocumentCollection GetOrCreateCollection(string databaseLink, string collectionId)
        {
            var col = Client.CreateDocumentCollectionQuery(databaseLink)
                              .Where(c => c.Id == collectionId)
                              .AsEnumerable()
                              .FirstOrDefault();

            if (col == null)
            {
                col = client.CreateDocumentCollectionAsync(databaseLink,
                    new DocumentCollection { Id = collectionId },
                    new RequestOptions { OfferType = "S1" }).Result;
            }

            return col;
        }

        public static IEnumerable<Movie> GetAllMovies()
        {
            var movies = Client.CreateDocumentQuery<Movie>(Collection.SelfLink).AsEnumerable();
            return movies;
        }

        public static Movie GetMovieById(string id)
        {
            var movie = Client.CreateDocumentQuery<Movie>(Collection.SelfLink)
                .Where(d => d.Id == id)
                .AsEnumerable()
                .FirstOrDefault();

            return movie;
        }

        public static async Task<Movie> CreateMovie(Movie entity)
        {
            Document doc = await Client.CreateDocumentAsync(Collection.SelfLink, entity);
            Movie movie = (Movie)(dynamic)doc;

            return movie;
        }
    }
}
```

#####Recordemos que es necesario reemplazar la información de las variables EndpointUrl y AuthorizationKey por los valores que obtenemos de nuestra cuenta de Azure DocumentDB

###Tarea 5
####Nuestro Controller (Controlador)

#####Tarea 5.1 Web API Controller

- Vamos a crear nuestra clase Controladora haciendo clic derecho sobre la carpeta Controllers->Add->Controller (Agregar Controller)

![MVC](img/T05_01.png)

- En este punto podemos crear un controlador, ya sea para manejo del codigo o un tipo de servicio Web API, para este ejercicio seleccionaremos la opción de Web API Controller Empty (Vacio):

![MVC](img/T05_02.png)

- Lo llamaremos MoviesController

![MVC](img/T05_03.png)

- Nuestra carpeta Controllers se verá con la clase que acabamos de crear.

![MVC](img/T05_04.png)

- Con esto ya tenemos la base para empezar a construir un esquema que se conecte con la base de datos y con Knockoutjs podemos trabajar la interface de usuario.

- Ahora agregaremos el código necesario a nuestro controlador iniciando con el siguiente código de base:
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Web.Http;

namespace MVC_HOL.Controllers
{
    public class MoviesController : ApiController
    {
    }
}
```
En donde <strong>MoviesController : ApiController</strong> nos indica que esta clase hereda de la clase ApiController.

- Agreamos el método que nos traerá una colección de datos de tipo IEnumerable de todas las películas guardadas (si las hay).
```
	public IEnumerable<Movie> GetAllMovies()
    {
        var movies = MovieRepository.GetAllMovies();
        return movies;
    }
```
- ahora agregamos el método que nos trae un único objeto de tipo Movie utilizando el Id.
```
	public Movie GetMoviesById(string id)
    {
        return MovieRepository.GetMovieById(id);
    }
```
- Y luego el método que nos permitirá agregar un nuevo registro en nuestra base de datos:
```
	public async Task<IHttpActionResult> PostMovie(Movie movie)
        {
            if (!ModelState.IsValid)
            {
                return BadRequest(ModelState);
            }

            await MovieRepository.CreateMovie(movie);

            return CreatedAtRoute("DefaultApi", new { id = movie.Id }, movie);

        }
```
Éste último método es de tipo asíncrono por eso es necesario plantear que es una tarea y al mismo tiempo agregarle las palabras reservadas async y await, así como la referencia using System.Threading.Tasks.

#####El código completo quedaría de la siguiente manera:
```
using System;
using System.Collections.Generic;
using System.Threading.Tasks;
using System.Web.Http;
using MVC_HOL.Models;

namespace MVC_HOL.Controllers
{
    public class MoviesController : ApiController
    {
        public IEnumerable<Movie> GetAllMovies()
        {
            var movies = MovieRepository.GetAllMovies();
            return movies;
        }

        public Movie GetMoviesById(string id)
        {
            return MovieRepository.GetMovieById(id);
        }

        public async Task<IHttpActionResult> PostMovie(Movie movie)
        {
            if (!ModelState.IsValid)
            {
                return BadRequest(ModelState);
            }

            await MovieRepository.CreateMovie(movie);

            return CreatedAtRoute("DefaultApi", new { id = movie.Id }, movie);

        }
    }
}
```

#####Tarea 5.2 HomeController
- Vamos a crear un controlador para asociarlo con una vista haciendo clic derecho sobre la carpeta Controllers->Add->Controller (Agregar Controller)

![MVC](img/T05_01.png)

- Para crear este controlador seleccionaremos la primera opción que es crear un controlador vacio (Controller Empty):

![MVC](img/T05_05.png)

- Lo llamaremos HomeController.

![MVC](img/T05_06.png)

- Nuestra carpeta Controllers ahora se verá de esta manera:

![MVC](img/T05_07.png)

- El resultado es una clase cuyo código debera verse de la siguiente manera:

![MVC](img/T05_08.png)

- Si observamos nuestra carpeta Views en el explorador de la solución podemos ver que se ha agregado la carpeta Home que estará asociada con el controlador HomeController.

![MVC](img/T06_01.png)

######Esta será la base para continuar con la siguiente tarea.

###Tarea 6
####Nuestra View (Vista)

- Teniendo abierta la clase HomeController (Tarea 5.2), hacemos clic derecho sobre el método Index y seleccionamos la opción Add View (Agregar Vista)

![MVC](img/T06_02.png)

- En la ventana que se abre debemos dejar el nombre Index, así como seleccionada la opción Empty (without model) ya que no vamos a traer los datos de ningún modelo específico sino que esto lo haremos más adelante a través de javascript.

![MVC](img/T06_03.png)

Al hacer clic sobre Add (Agregar) ocurren varias cosas con nuestro proyecto, entre otras:

- Se genera un archivo de tipo Razor en la carpeta Home dentro de Views llamado Index.cshtml
- Se genera un archivo de tipo Razor en la carpeta Shared dentro de Views llamado _Layour.cshtml que será la página maestra base del proyecto.
- Si no hubieramos implementado jQuery ni Bootstrap, se hubieran agregado automáticamente estos paquetes.
- Dentro de Content se agregó una nueva hoja de estilos llamada Site.css
- Dentro de la carpeta Scripts se agregó la libreria de javascript Modernizr.

![MVC](img/T06_04.png)

- Presionamos la tecla F5 para que se abra el proyecto en el explorador web, lo que nos mostrará la página Index con diseño predefinido, este diseño viene del archivo _Layout.cshtml

![MVC](img/T06_05.png)

- Toma por defecto la página Index de Home por que esta predefinida dentro del clase de configuración RouteConfig.cs que esta dentro de la carpeta App_Start, al igual que la ruta del ApiController esta en la clase WebApiConfig.cs dentro de la misma carpeta.

![MVC](img/T06_06.png)

#####Si existen estas clases, podemos realizar lo siguiente:

- Si hemos cerrado el navegador volvamos a abrirlo presionando la tecla F5, en la barra de direcciones agregemos API/Movies lo que nos mostrará la información que trae de la base de datos por defecto es la lista de todos los registros en formato Json, si no hay registros debe mostrar una página con un par de corchetes cuadrados.
En el caso de este ejemplo que ya hay registros preguardados en la base de datos muestra lo siguiente:

![MVC](img/T06_07.png)

- Cerremos el navegador y si es necesario detengamos la ejecución de la aplicación haciendo clic en el boton detener de Visual Studio.

![MVC](img/T06_08.png)

#####Si no existen estas clases, es necesario crearlas

###Tarea 7
#### Creando los Archivos de enrutado (condicional)

Como se mencionó en la tarea anterior, si no existen las clases RouteConfig.cs y/o WebApiConfig.cs dentro de la carpeta App_Start, es necesario crearlos, si existen estas clases podemos pasar a la tarea 8 si lo desean.

- Lo primero que haremos en esta tarea es crear la clase RouteConfig.cs dentro de la carpeta App_Start de la misma manera en que se crearon las clases dentro de la carpeta Models, haciendo clic derecho sobre  la carpeta App_Start, seleccionando la opción Add->New Item y escogiendo la opción Code de la ventana que se abre y la plantilla Class.

![MVC](img/T07_01.png)

![MVC](img/T07_02.png)

- La clase RouteConfig debe quedar de la siguiente manera, en donde contendrá el mapeado de las rutas que trabajará internamente "{controller}/{action}/{id} (parámetro opcional)" y por defecto tendrá la siguiente ruta controller = "Home", action = "Index", id = UrlParameter.Optional, por esa razón toma al Index del Home por defecto.
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Mvc;
using System.Web.Routing;

namespace MVC_HOL
{
    public class RouteConfig
    {
        public static void RegisterRoutes(RouteCollection routes)
        {
            routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

            routes.MapRoute(
                name: "Default",
                url: "{controller}/{action}/{id}",
                defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
            );
        }
    }
}
```

- Lo siguiente es crear la clase WebApiConfig.cs dentro de la carpeta App_Start de la misma manera en que se crearon las clases dentro de la carpeta Models, haciendo clic derecho sobre  la carpeta App_Start, seleccionando la opción Add->New Item y escogiendo la opción Code de la ventana que se abre y la plantilla Class.

![MVC](img/T07_01.png)

![MVC](img/T07_03.png)

- La clase WebApiConfig debe quedar de la siguiente manera, en donde contendrá el mapeado de las rutas que trabajará internamente "api/{controller}/{id} (parámetro opcional)" y en este caso no hay valor por defecto.
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web.Http;

namespace MVC_HOL
{
    public static class WebApiConfig
    {
        public static void Register(HttpConfiguration config)
        {
            // Web API configuration and services

            // Web API routes
            config.MapHttpAttributeRoutes();

            config.Routes.MapHttpRoute(
                name: "DefaultApi",
                routeTemplate: "api/{controller}/{id}",
                defaults: new { id = RouteParameter.Optional }
            );
        }
    }
}
```

- Para que queden activas es necesario abrir la clase Global.asax y realizar la configuración cuando la aplicación inicia: método Application_Start.

![MVC](img/T07_04.png)

- Deberá agregarse dos lineas de código:
```
	GlobalConfiguration.Configure(WebApiConfig.Register);
    RouteConfig.RegisterRoutes(RouteTable.Routes);
```
El código completo de Global.asax debería verse similar a:
```
using System;
using System.Web;
using System.Web.Mvc;
using System.Web.Routing;
using System.Web.Http;

namespace MVC_HOL
{
    public class Global : HttpApplication
    {
        void Application_Start(object sender, EventArgs e)
        {
            // Code that runs on application startup
            AreaRegistration.RegisterAllAreas();
            GlobalConfiguration.Configure(WebApiConfig.Register);
            RouteConfig.RegisterRoutes(RouteTable.Routes);            
        }
    }
}
```
- Compilamos la solución haciendo clic en la pestaña Build y luego en Build Solution:
![MVC](img/T07_05.png)

Ejecutamos utilizando la tecla F5 y realizamos los ultimos dos pasos de la Tarea 6.

###Tarea 8
####Knockoutjs conectándonos con el Apicontroller

El ideal es trabajar al mismo tiempo esta parte y la vista (Tarea 9), sinembargo por orden vamos a trabajar todo el código javascript primero y después veremos el resultado en las siguientes tareas.

- Vamos a crear nuestro archivo javascript con el que conectaremos al ApiController utilizando knockoutjs, para esto hacemos clic derecho del mouse sobre la carpeta Scripts y seleccionamos Add->New Folder (Agregar nuevo folder) y le daremos el nombre de <strong>movie</strong> (o el nombre que sea significativo dentro del proyecto).

![MVC](img/T08_01.png)

![MVC](img/T08_02.png)

- En esta carpeta movie haremos clic derecho del ratón y seleccionamos Add->New Item y en la ventana que se abre seleccionaremos la opción Web y la plantilla JavaScript File (Archivo JavaScript), lo llamaremos movies.js.

![MVC](img/T08_03.png)

![MVC](img/T08_04.png)

Con esto ya tendremos nuestro javascript para trabajar con los datos.

![MVC](img/T08_05.png)

- Abrimos nuestro archivo movies.js (si no esta abierto) e iniciamos la construcción de nuestro código y empezamos. 

- knockout es un esquema que trabaja con un patón del tipo Modelo Vista y Vista del Modelo o Model View ViewModel (MVVM).

- Lo primero que construimos en nuestro javascript será la función en donde implementaremos el código, para este ejercicio la llamaremos ViewModel, al final haremos el llamado utilizando el objeto <strong>ko</strong> que maneja knockoutjs para hacer el llamado de nuestro ViewModel. El código resultante iniciaria de la siguiente forma:
```
var ViewModel = function () {
    
};

ko.applyBindings(new ViewModel());
```

- Dentro de nuestra función ViewModel agregamos un llamado a la información con la que trabajaremos var selft=this y crearemos dos variables una para el listado de las películas, otra para imprimir un error si lo hay y la última para traer la información de una película que seleccionemos (detalle de la película):

```
	var self = this;
    self.movies = ko.observableArray();
    self.error = ko.observable();
	self.detail = ko.observable();
```

ko.observableArray tiene la estructura dentro de la librería del knockout para traer una lista de datos.
ko.observable trae información (un texto, un número, etc),.

- Ahora vamos a crear un objeto que lo utilizaremos en el momento en que tengamos que crear una película.
```
	self.newMovie = {
        id: ko.observable(),
        name: ko.observable(),
        description: ko.observable(),
        year: ko.observable(),
        genre: ko.observable()
    }
```

- Continuamos agregando una variable que contendrá la ruta de la Api con la que nos comunicaremos:
```
	var moviesUri = "/api/movies/";
```
Recordemos que ésta Api la creamos en tareas anteriores (Revisar Tarea 6 y Tarea 7)

- Agregamos la función de jQuery que nos permite información que integra código de lado cliente y servidor (Asynchronous JavaScript and XML - AJAX).
```
	function ajaxHelper(uri, method, data) {
        self.error(""); // Clear error message
        return $.ajax({
            type: method,
            url: uri,
            dataType: "json",
            contentType: "application/json",
            data: data ? JSON.stringify(data) : null
        }).fail(function (jqXHR, textStatus, errorThrown) {
            self.error(errorThrown);
        });
    }

```

- En este punto ya tenemos la base para hacer el llamado correspondiente a nuestro código, por eso ahora se agregará la función <strong>getAllMovies</strong> que traé el listado de las películas, la que se conecta con el ApiController 'ajaxHelper(moviesUri, "GET")' y carga la información en la variable movies 'self.movies(data)'
```
	function getAllMovies() {
        ajaxHelper(moviesUri, "GET").done(function (data) {
            self.movies(data);
        });
    }	
```
Se esta comunicando a través del GET del ApiController en su método GetAllMovies, en donde trae el listado de las películas, convirtiéndolo en un formato legible para el javascript.

![MVC](img/T08_06.png)

- Ahora incluiremos la funcion getMovieDetail que nos traé un registro específico pasándole la dirección del ApiController y el Id del registro requerido 'ajaxHelper(moviesUri + item.id, "GET")' y los datos quedaran asociados a la variable details 'self.detail(data)'.
```
self.getMovieDetail = function (item) {
        ajaxHelper(moviesUri + item.id, "GET").done(function (data) {
            self.detail(data);
        });
    }
```
Se esta comunicando a través del GET del ApiController en su método GetMoviesById, en donde trae el un unico objeto de tipo Movie.

![MVC](img/T08_07.png)

- Para complementar, construimos la funcion addMovie la que nos permite guardar registros asociándola al objeto que creamos anteriormente llamado newMovie, en donde le pasamos los valores del objeto creando el objeto movie.
pasamos el parámetro de dirección y el objeto movie utilizando un método de tipo POST 'ajaxHelper(moviesUri, "POST", movie)' para pasar la información al ApiController 'self.movies.push(item)'.
```
	self.addMovie = function (formElement) {
        var movie = {
            id: self.newMovie.id(),
            name: self.newMovie.name(),
            genre: self.newMovie.genre(),
            description: self.newMovie.description(),
            year: self.newMovie.year()
        };

        ajaxHelper(moviesUri, "POST", movie).done(function (item) {
            self.movies.push(item);
        });
    };
```
A través del POST se comunica con el método PostMovie dentro del ApiController.

![MVC](img/T08_08.png)

- Cerrando la fucnion ViewModel le decimos que ejecute por defecto el método que trae todo el listado de las películas 'getAllMovies'
```
getAllMovies();

```
El código completo se debería ver así:

```
var ViewModel = function () {
    var self = this;
    self.movies = ko.observableArray();
    self.error = ko.observable();
    self.detail = ko.observable();

    //Objeto de tipo Movie
    self.newMovie = {
        id: ko.observable(),
        name: ko.observable(),
        description: ko.observable(),
        year: ko.observable(),
        genre: ko.observable()
    }

    var moviesUri = "/api/movies/";

    //jQuery Ajax
    function ajaxHelper(uri, method, data) {
        self.error(""); // Clear error message
        return $.ajax({
            type: method,
            url: uri,
            dataType: "json",
            contentType: "application/json",
            data: data ? JSON.stringify(data) : null
        }).fail(function (jqXHR, textStatus, errorThrown) {
            self.error(errorThrown);
        });
    }

    //Trae todos los registros
    function getAllMovies() {
        ajaxHelper(moviesUri, "GET").done(function (data) {
            self.movies(data);
        });
    }

    //Traé un único registro
    self.getMovieDetail = function (item) {
        ajaxHelper(moviesUri + item.id, "GET").done(function (data) {
            self.detail(data);
        });
    }

    //Agrega un nuevo registro
    self.addMovie = function (formElement) {
        var movie = {
            id: self.newMovie.id(),
            name: self.newMovie.name(),
            genre: self.newMovie.genre(),
            description: self.newMovie.description(),
            year: self.newMovie.year()
        };

        ajaxHelper(moviesUri, "POST", movie).done(function (item) {
            self.movies.push(item);
        });
    };

    //Carga los datos al iniciar.
    getAllMovies();
};

ko.applyBindings(new ViewModel());
```

#####Ahora vamos a integrar todo lo anterior a nuestra vista Index dentro del Home.

###Tarea 9
######Mostrando datos en nuestra vista




























