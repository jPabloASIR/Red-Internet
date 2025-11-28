# Práctica servidores web 1º Trimestre.

## 1. Instalación del servidor web apache. Dos dominios mediante el archivo hosts. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python.

Para instalar apache en ubuntu linux escribimos: **sudo apt install apache2** en la terminal.

A continuación, lo habilitamos con: **sudo systemctl enable --now apache2**
![Descargando Apache](1&2&3&4&5/paso1.PNG)

Con apache instalado y habilitado, ahora deberíamos de poder acceder al index.html que viene por defecto escribiendo la IP de nuestra VM en un buscador (podemos saber nuestra IP con **hostname -I**.
![Descargando Apache](1&2&3&4&5/paso2.PNG)

Para poder usar 2 dominios necesitamos editar el archivo hosts, para ello, lo abrimos con: **sudo nano /etc/hosts**
![Descargando Apache](1&2&3&4&5/paso3.PNG)

Una vez dentro, escribimos nuestra IP y al lado, los dominios (**centro.intranet y departamentos.centro.intranet**)
![Descargando Apache](1&2&3&4&5/paso4.PNG)

Una vez guardados los cambios, crearemos sus respectivos directorios y le daremos los permisos para que puedan ser leídos.
![Descargando Apache](1&2&3&4&5/paso5.PNG)

Ahora tenemos que crear los archivos para cada directorio:
![Descargando Apache](1&2&3&4&5/paso6.PNG)

Su contenido:
![Descargando Apache](1&2&3&4&5/paso7.PNG)

Hacemos lo mismo para el otro directorio:
![Descargando Apache](1&2&3&4&5/paso8.PNG)

Su contenido:
![Descargando Apache](1&2&3&4&5/paso9.PNG)


Ahora, para que podamos cargar nuestros scripts que necesitaremos para este trabajo y nuestras aplicaciones, deberemos instalar: **sudo apt install libapache2-mod-wsgi-py3 -y**
![Descargando Apache](1&2&3&4&5/paso91.PNG)

Con esto podremos crear ahora una aplicación.
![Descargando Apache](1&2&3&4&5/paso92.PNG)

Contenido de la aplicación:
![Descargando Apache](1&2&3&4&5/paso996.PNG)

A continuación, habilitamos centro.intranet y departamentos.centro.intranet.
![Descargando Apache](1&2&3&4&5/paso94.PNG)

Ahora debemos instalar el módulo para PHP
![Descargando Apache](1&2&3&4&5/paso95.PNG)

![Descargando Apache](1&2&3&4&5/paso96.PNG)


Damos permisos a las directivas anteriormente creadas.
![Descargando Apache](1&2&3&4&5/paso97.PNG)

Instalar el módulo de mariadb: **sudo apt install mariadb-server -y**
![Descargando Apache](1&2&3&4&5/paso98.PNG)

![Descargando Apache](1&2&3&4&5/paso99.PNG)

![Descargando Apache](1&2&3&4&5/paso991.PNG)

Ahora procederemos a crear los usuarios para la base de datos, para ello nos conectamos a la DB como administrador.
![Descargando Apache](1&2&3&4&5/paso992.PNG)

Crearemos una DB dentro de mariadb, un usuario con permisos de administrador.
![Descargando Apache](1&2&3&4&5/paso993.PNG)

Con todo correctamente configurado, podremos conectarnos a centro.intranet (wordpress).
![Descargando Apache](1&2&3&4&5/paso994.PNG)

De igual forma, podremos conectarnos a departamentos.centro.intranet (aplicación python).
![Descargando Apache](1&2&3&4&5/paso997.PNG)


--



## 2. Adicionalmente protegeremos el acceso a la aplicación python mediante autenticación.

Para poder agregar contraseñas a los usuarios, deberemos primero instalar el módulo: **sudo apt install apache2-utils -y**
Una vez instalado, para asignar contraseñas a los usuarios es: **sudo htpasswd -c /etc/apache2/.htpasswd [nombre_del_usuario]
![Descargando Apache](6/paso1.PNG)

Además, le hice modificaciones al archivo de departamentos.centro.intranet.
![Descargando Apache](6/paso2.PNG)

Una vez realizados los cambios reiniciamos apache.
![Descargando Apache](6/paso3.PNG)

La próxima vez, al iniciar nos aparecerá lo siguiente:
![Descargando Apache](6/paso4.PNG)

Por lo tanto, funciona.


--



## 3. Instala y configura awstat.

Para instalar awstat escribimos en la terminal: **sudo apt install apache2 awstats libgeo-ip-perl libgeo-ipfree-perl -y**
![Descargando Apache](7/paso1.PNG)

Habilitamos el módulo cgi para que mueste contenido web y reiniciamos apache.
![Descargando Apache](7/paso2.PNG)

Crearemos un archivo para hospedar la web de centro.intranet
![Descargando Apache](7/paso3.PNG)

![Descargando Apache](7/paso4.PNG)

Creamos también otro archivo para ejecutar scripts.
![Descargando Apache](7/paso5.PNG)

![Descargando Apache](7/paso91.PNG)

Habilitamos todo y reiniciamos apache.
![Descargando Apache](7/paso7.PNG)

![Descargando Apache](7/paso8.PNG)

Actualizamos awstat.
![Descargando Apache](7/paso9.PNG)

Comprobamos que funciona.
![Descargando Apache](7/paso92.PNG)



--



Instalamos nginx: **sudo apt install nginx -y**
![Descargando Apache](8/paso1.PNG)

Creamos el archivo donde estará nuestro segundo servidor.
![Descargando Apache](8/paso2.PNG)

Su contenido:
![Descargando Apache](8/paso3.PNG)

phpinfo(); Es una función nativa de PHP que imprime en pantalla información detallada sobre la configuración del servidor, la versión de PHP, los módulos instalados, las variables de entorno y otras directivas de configuración.
![Descargando Apache](8/paso4.PNG)

Instalamos php: **sudo apt install php** (el resto es solo para instalar extensiones y demás)
![Descargando Apache](8/paso5.PNG)

Instalamos también phpmyadmin: **sudo apt install phpmyadmin -y**
![Descargando Apache](8/paso6.PNG)

Mientras se instala, nos pedirá configurarlo, primero lo configuramos con servidor web a apache2.
![Descargando Apache](8/paso7.PNG)

Le damos a Sí a configurar la base de datos para phpmyadmin.
![Descargando Apache](8/paso8.PNG)

Ahora le asignaremos una contraseña a phpmyadmin.
![Descargando Apache](8/paso9.PNG)

Comprobación de que funciona:
![Descargando Apache](8/paso93.PNG)

Vista desde un usuario dentro de phpmyadmin.
![Descargando Apache](8/paso94.PNG)
