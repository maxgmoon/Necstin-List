### Primera version estable / First stable version - Necstin List v.0.8-24.25.02-beta - First release

Necstin list es un plugin para Revit que agrega algunas funciones al trabajo colaborativo. El principal objetivo: tener un control sobre las actualiazaciones de los usuarios en el modelo. 
Basicamente el uso de dos botones principales manejarán una lista de espera para poder tener un control en cuanto a tiempos de sincronización. 

> _"Necstin List is a plugin for Revit that adds some features to collaborative work. Its main objective is to have control over user updates in the model. Essentially, the use of two main buttons will manage a waiting list to control synchronization times._

La lógica detrás: el usuario en sesión en el modelo, utilizará el botón Joinlist para tomar un lugar en la lista, y esta se gestionará automaticamente conforme los usuarios sincronicen sus cambios.
La primera vez que se abra un modelo y se utilice NecstinList se le perdirá al usuario que asocie un nombre a su revit ID para poder guardarlo en la base de datos (archivos CSV por cada modelo). 

> _The logic behind it: the user logged into the model will use the 'Join List' button to take a place in the list, and it will be managed automatically as users synchronize._
> _The first time a model is opened and Necstin List is used, the user will be asked to associate a name with their Revit ID to save it in the database (CSV files for each model)."_

>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/a79250a9-9cff-4843-aa4b-d2e3c60861ea)
>


Los archivos base (Usersdb.dixt y waitlist.dixt) se generan una vez por cada modelo en la misma carpeta del proyecto de Revit. En el caso de un proyecto colaborativo en un servidor local, estos archivos se crean automáticamente. Sin embargo, para los proyectos que se trabajan en BIM 360, la carpeta en la que se crearán estos archivos se solicitará al usuario la primera vez que intente unirse a la lista a través de JoinList. Dado que se trata de un modelo trabajado en la nube, no hay ninguna referencia a una carpeta de proyecto local, por lo que esta carpeta debe asignarse para que todos los usuarios puedan acceder a ella.

> _The base files (Usersdb.dixt and waitlist.dixt) are created once per model in the same folder of the Revit project. In the case of a collaborative project on a local server, these files are generated automatically. However, for projects worked on in BIM 360, the folder where these files will be created will be prompted to the user the first time they attempt to join the list via JoinList. Since it is a model worked on in the cloud, there is no reference to any local project folder, so this folder must be assigned for all users to access it._

>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/a71dc62c-757a-4649-89da-515f955667ea)
>

EventsLog.logixt es el archivo donde se registran trodos los eventos referentes a la sincronización del modelo, Entrada, Salida, Inicio y finalización de la sincronización, incluyendo el estatus "Succeeded", "Cancelled" o "Failed", dependiendo del estado que Revit devuelva, Finalización de sincronización, etc...

> _The EventsLog.logixt file is where all events related to model synchronization are recorded: Entry, Exit, Start and completion of synchronization, including statuses like 'Succeeded,' 'Cancelled,' or 'Failed,' depending on the state returned by Revit, synchronization completion, etc._

>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/a86ec8e5-a013-4cec-8bd2-ae3a9f914d97)
>

Configuraciones: / _Configurations:_
>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/ae819d8f-3155-4350-8723-f0f06e80a850)


Y bueno, algunas otras utilidades: / _Some other utilities included:_
>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/bfcf3794-9166-48ac-9753-3b2d41c7e31f)
>

>[!NOTE]
Instalación:
Por ahora la instalación see puede hacer de manera manual, en la siguiente version, se incluirá un instalador par poder elegir las versiones de revit necesarias.

>[!NOTE]
>_Installation:_
>_For now, the installation can be done manually. In the next version, an installer will be included to choose the necessary Revit versions._ 

Rutas :
1) AppData\Roaming\Autodesk\Revit\Addins\2023 <-- {Versión de Revit deseada}  - En esta ruta colocaremos el archivo manifest NecstinList.addin, en esa misma ruta crearemos una subcarpeta llamada NecstinList (Cuidar mayusculas y minusculas), y dentro colocaremos el archivo NecstinList.dll

> Paths:
> _AppData\Roaming\Autodesk\Revit\Addins\2023 <-- {Desired Revit Version} - In this path, we will place the manifest file NecstinList.addin. Within the same path, we will create a subfolder named NecstinList (please mind the capitalization), and inside it, we'll place the NecstinList.dll file._

> ![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/e822fa1d-3ddf-4c7e-8036-4049bcbafa5c)
> 

2) AppData\Roaming\NecstinList <-- (Deberemos crear la carpeta - cuidar mayusculas y minusculas). - En esta ruta colocaremos el ejecutable EventMonitor2.0.exe
> _AppData\Roaming\NecstinList <-- (We should create the folder - mind the capitalization). - In this path, we will place the executable EventMonitor2.0.exe_
> ![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/e41bc7da-d544-45a0-80bd-34730fe0d0e4)


En algunos casos será necesario desbloquear los archivos NecstinList.dll y EventMonitor2.0.exe al ser arvchivos provenientes de la web, windows 10 en adelante, bloquearán los archivos por defecto.
Solamente tendremos que volver a las rutas dar clic derecho en el archivo, clic en "Propiedades", marcar la casilla "Desbloquear" y clic en aceptar. Listo, ahora podremos ejectuar el plugin sin problemas.
>_In some cases, it will be necessary to unblock the files NecstinList.dll and EventMonitor2.0.exe since they are files from the web. Starting from Windows 10, the files will be blocked by default. Simply navigate back to the paths, right-click on the file, click on 'Properties,' check the 'Unblock' box, and click 'OK.' That's it! Now you can run the plugin without any issues._
>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/e48fd3b9-82be-4e84-aef5-7f88993491e6)


La instalación manual solo es necesaria para esta version beta. 
- [ ] La siguiente versión incluirá un instalador de versiones (en desarrollo).
>_The manual installation is only necessary for this beta version._
>- _[ ] The next version will include a version installer (currently in development)._
>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/966a5ea1-8d8b-45e5-b4f6-4f2062006819)




Esta versión ha cambiado para trabajar con archivos CSV simples, para gestionar listas de espera, UsersDB, archivos de configuración, etc... anteriormente se utilzaban bases de datos SQLite, sin embargo, por tratarse de bases de datos pequeñas y que a veces las consultas a bases de datos pueden ser bloqueadas por los servidores, se optó por trabajar con archivos CSV.

> _This version has changed to work with simple CSV files, to manage waiting lists, UsersDB, configuration files, etc... previously SQLite databases were used, but because they are small databases and sometimes queries to databases can be blocked by servers, we chose to work with CSV files._
