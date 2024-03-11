# Primera version estable / First stable version - Necstin List v.0.1.03.05-beta - First release

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

>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/b8fb0e70-89a1-4003-ba20-10e081fdc1cd)
>

Configuraciones: / _Configurations:_
>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/dd5b0cf8-2b97-4ec1-90a9-4d0272d64271)



Y algunas otras utilidades: / _Some other utilities included:_
>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/bfcf3794-9166-48ac-9753-3b2d41c7e31f)
>

> [!NOTE]
>
> - [X] ¡El instalador de versiones está listo! 
>
>Solo selecciona las versiones que deseas instalar.
>
>
> - [X] _Release installer is ready!_
>
> _Just select the versions you want to install._


>![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/966a5ea1-8d8b-45e5-b4f6-4f2062006819)




Esta versión ha cambiado para trabajar con archivos CSV simples, para gestionar listas de espera, UsersDB, archivos de configuración, etc... anteriormente se utilzaban bases de datos SQLite, sin embargo, por tratarse de bases de datos pequeñas y que a veces las consultas a bases de datos pueden ser bloqueadas por los servidores, se optó por trabajar con archivos CSV.

> _This version has changed to work with simple CSV files, to manage waiting lists, UsersDB, configuration files, etc... previously SQLite databases were used, but because they are small databases and sometimes queries to databases can be blocked by servers, we chose to work with CSV files._

# Necstin List v.0.1.03.10-beta

## Esta versión 0.1.03.10 inluye dos cambios esenciales: 
### Se integró la capacidad de elegir y mostrar una imagen de usuario en las notificaciones para facilitar el reconocimiento del usuario que ha relalizado la acción, esta imagen puede ser mostrada u ocultada. 

>_This version 0.1.03.10 includes two essential changes:_
>_The ability to choose and display a user image in notifications has been integrated. This makes it easier to identify the user who performed the action. This image can be shown or hidden._

![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/1108fd90-cf7b-4ac2-9ae3-8fbf9d2deb58)

una vez que el usuario elija una imagen, será procesada y añadida a un archivo Json, contenido en la carpeta del modelo en cuestión, desde donde se leera cada vez que se lance una notificación.

>_Once the user chooses an image, it will be processed and added to a JSON file. This file is located in the folder of the model in question. The image will be read from this file each time a notification is launched._

### Y además se ha añadido un botón para poder mostrar un mensaje personalizado para todos los usuarios que estén en el modelo. Este mensaje se mostrará una vez, cuando sea lanzado o cada vez que se inicie EventMonitor y puede ser ocultado por el usuario.

>_Además se ha añadido un botón para poder mostrar un mensaje personalizado para todos los usuarios que estén en el modelo. Este mensaje se mostrará una vez, cuando sea lanzado o cada vez que se inicie EventMonitor y puede ser ocultado por el usuario._

![image](https://github.com/maxgmoon/Necstin-List/assets/66993948/d0f32f9e-a836-4f2b-bd06-59f4706c5afc)


Este mensaje se desplegará por medio un archivo de registro en la misma carpeta que el Archivo EventsLog.logixt el cual tiene un formato:
[Tittle=tittle]
[Message=message]
el cual puede ser modificado manualmente, sin embargo es preferente que se use la herrameinta integrada en EventMonitor.

>_This message will be displayed through a log file located in the same folder as the EventsLog.logixt file. The file follows a specific format:_
>
>_[Title=title]_
>_[Message=message]_
>_Although the message can be modified manually, it is preferable to use the tool integrated into EventMonitor._

Ademas, se han realizado algunas otras correciones menores en código.
>_Additionally, some other minor code fixes have been implemented._
