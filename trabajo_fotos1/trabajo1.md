# Práctica servidores web 1º Trimestre

## 1. Instalación del servidor web apache. Dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python.

Para instalar apache en ubuntu linux escribimos: **sudo apt install apache2** en la terminal.

A continuación, lo habilitamos con: **sudo systemctl enable --now apache2**
[imagen1]

Con apache instalado y habilitado, ahora deberíamos de poder acceder al index.html que viene por defecto escribiendo la IP de nuestra VM en un buscador (podemos saber nuestra IP con **hostname -I**.
[imagen2]

Para poder usar 2 dominios necesitamos editar el archivo hosts, para ello, lo abrimos con: **sudo nano /etc/hosts**
[imagen3]

Una vez dentro, escribimos nuestra IP y al lado, los dominios (**centro.intranet y departamentos.centro.intranet**)
[imagen995]

Una vez guardados los cambios, crearemos sus respectivos directorios y le daremos los permisos para que puedan ser leídos.
[imagen5]

Ahora tenemos que crear los archivos para cada directorio:
[imagen6]

Su contenido:
[imagen7]

Hacemos lo mismo para el otro directorio:
[imagen8]

Su contenido:
[imagen9]


Ahora, para que podamos cargar nuestros scripts que necesitaremos para este trabajo y nuestras aplicaciones, deberemos instalar: **sudo apt install libapache2-mod-wsgi-py3 -y**
[imagen91]

Con esto podremos crear ahora una aplicación.
[imagen92]

Contenido de la aplicación:
[imagen996]

A continuación, habilitamos centro.intranet y departamentos.centro.intranet.
[imagen94]

Ahora debemos instalar el módulo para PHP
[imagen95]

[imagen96]


Damos permisos a las directivas anteriormente creadas.
[imagen97]

Instalar el módulo de mariadb: **sudo apt install mariadb-server -y**
[imagen98]

[imagen99]

[imagen991]

Ahora procederemos a crear los usuarios para la base de datos, para ello nos conectamos a la DB como administrador.
[imagen992]

Crearemos una DB dentro de mariadb, un usuario con permisos de administrador.
[imagen993]

Con todo correctamente configurado, podremos conectarnos a centro.intranet (wordpress).
[imagen994]

De igual forma, podremos conectarnos a departamentos.centro.intranet (aplicación python).
[imagen997]


--



# Adicionalmente protegeremos el acceso a la aplicación python mediante autenticación

Para poder agregar contraseñas a los usuarios, deberemos primero instalar el módulo: **sudo apt install apache2-utils -y**
Una vez instalado, para asignar contraseñas a los usuarios es: **sudo htpasswd -c /etc/apache2/.htpasswd [nombre_del_usuario]
[imagen1]

Además, le hice modificaciones al archivo de departamentos.centro.intranet.
[imagen2]

Una vez realizados los cambios reiniciamos apache.
[imagen3]

La próxima vez, al iniciar nos aparecerá lo siguiente:
[imagen4]

Por lo tanto, funciona.


--






