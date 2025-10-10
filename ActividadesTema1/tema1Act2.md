# Configuración básica de Apache

## 1. Apache utilizará el puerto 81 además del 80 

Abrimos la terminal de ubuntu e iniciamos apache:

**sudo systemctl start apache2**


Para poder configurar los puertos de apache, debemos de encontrar y editar el archivo ports.conf (esto en ubuntu 2.4.58), para ello primero escribimos:

**ls -l /etc/apache2**
![Iniciar Apache](Act2_imgs/paso1.1.PNG)

Esto mostrará todos los archivos y carpetas que contiene apache, una vez localizamos nuestro archivo ports.conf escribimos:

**sudo nano /etc/apache2/ports.conf**

A continuación se nos abrirá el archivo. La primera vez que lo abras, verás lo siguiente o parecido:
![Iniciar Apache](Act2_imgs/paso1.2.PNG)

Lo único que haremos será escribir abajo de 'Listen 80', el nombre del puerto al que queremos configurar: Listen 81
![Iniciar Apache](Act2_imgs/paso1.3.PNG)
Así quedaría, le damos a guardar y salimos del archivo.


Lo aconsejable sería ahora reiniciar apache, podemos hacer esto escribiendo:

**sudo systemctl restart apache2**
![Iniciar Apache](Act2_imgs/paso1.4.PNG)

Ahora, si escribimos en nuestro buscador **http://localhost:80** se nos abrirá la web default de Apache (normal, estamos utilizando el puerto predeterminado que teníamos antes):
![Iniciar Apache](Act2_imgs/paso1.5.PNG)

Pero ahora, también podemos conectarnos al puerto 81 con: **http://localhost:81**
![Iniciar Apache](Act2_imgs/paso1.6.PNG)


## 2. Añadir el dominio “marisma.intranet” en el fichero “hosts”

En la terminal, necesitamos editar el archivo de hosts, hacemos esto escribiendo:

**sudo nano /etc/hosts**
![Iniciar Apache](Act2_imgs/paso2.1.PNG)

Así es como debería de verse:
![Iniciar Apache](Act2_imgs/paso2.2.PNG)

Una vez dentro escribimos al final:

**10.4.0.31 marisma.intranet**
![Iniciar Apache](Act2_imgs/paso2.3.PNG)
Se puede escribir cualquier IP, yo pondré la mía local 10.4.0.31, luego guardamos y cerramos.
![Iniciar Apache](Act2_imgs/paso2.5.PNG)

Si nos vamos al navegador y escribimos **http://marisma.intranet** nos aparecerá la página web default de Apache:
![Iniciar Apache](Act2_imgs/paso2.4.PNG)

## 3. Cambia la directiva “ServerTokens” para mostrar el nombre del producto.

En la terminal, debemos de editar el archivo security.conf (el cual está dentro de conf-enabled), que podemos ver si hacemos ls -l /etc/apache2 tal que así:
![Iniciar Apache](Act2_imgs/paso3.1.PNG)

Para entrar en el archivo escribimos:

**sudo nano /etc/apache2/conf-enabled/security.conf**
![Iniciar Apache](Act2_imgs/paso3.2.PNG)

Debería de verse tal que así:
![Iniciar Apache](Act2_imgs/paso3.3.PNG)

En la línea que pone ServerTokens OS escribimos:

**ServerTokens ProductOnly**
![Iniciar Apache](Act2_imgs/paso3.4.PNG)
![Iniciar Apache](Act2_imgs/paso3.5.PNG)

Luego guardamos y cerramos el archivo, procediendo a reiniciar apache.

Después de que se reinicie, escribimos:

**curl -I http://localhost**

Nos sale esto:
![Iniciar Apache](Act2_imgs/paso3.6.PNG)

Fíjate que en Server solo aparece 'Apache'. Si no se hubiera editado el archivo de security.conf saldría esto:
![Iniciar Apache](Act2_imgs/paso3.7.PNG)
(he hecho esto revertiendo los cambios hechos en el ejercicio para probar la diferencia entre 'OS' y 'ProductOnly')

## 4. Comprueba si se visualiza el pie de página en las páginas generadas por Apache

Dentro del archivo de security.conf (sino, siempre puedes poner sudo nano /etc/apache2/conf-enabled/security.conf en la terminal), si bajamos un poco nos toparemos con:
![Iniciar Apache](Act2_imgs/paso4.1.PNG)

En mi caso, ServerSignature está activado, vamos a desactivarlo (Off):
![Iniciar Apache](Act2_imgs/paso4.2.PNG)

Ahora guardamos, salimos, reiniciamos apache y nos vamos a nuestro buscador, pondremos:

**http://localhost/nombredepaginainexistente**


La diferencia entre tener ServerSignature en 'On' o en 'Off' es el pie de página.
En Off:
![Iniciar Apache](Act2_imgs/paso4.3.PNG)

En On:
![Iniciar Apache](Act2_imgs/paso4.4.PNG)

## 5. Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.

Voy a crear las 2 carpetas con:

**sudo mkdir /var/www/html/prueba**
**sudo mkdir /var/www/html/prueba2**
![Iniciar Apache](Act2_imgs/paso5.1.PNG)

Ahora, dentro de dichas carpetas, voy a añadir 2 html por cada una, sus nombres serán index.html y pr1.html para prueba y pr2.html para prueba2:

**sudo mkdir /var/www/html/prueba/index.html**
![Iniciar Apache](Act2_imgs/paso5.2.PNG)
![Iniciar Apache](Act2_imgs/paso5.3.PNG)
**sudo mkdir /var/www/html/prueba2/index.html**
![Iniciar Apache](Act2_imgs/paso5.4.PNG)
![Iniciar Apache](Act2_imgs/paso5.5.PNG)

**sudo mkdir /var/www/html/prueba/pr1.html**
![Iniciar Apache](Act2_imgs/paso5.6.PNG)
![Iniciar Apache](Act2_imgs/paso5.7.PNG)
**sudo mkdir /var/www/html/prueba2/pr2.html**
![Iniciar Apache](Act2_imgs/paso5.8.PNG)
![Iniciar Apache](Act2_imgs/paso5.9.PNG)

Para comprobar que se han creado correctamente, vamos a nuestro navegador y escribimos:

**http://localhost/[aquí va el nombre del archivo que queremos visualizar]**

En nuestros casos serían:

**http://localhost/prueba (despliega su index.html)**
![Iniciar Apache](Act2_imgs/paso5.91.PNG)
**http://localhost/prueba/pr1.html**
![Iniciar Apache](Act2_imgs/paso5.92.PNG)
**http://localhost/prueba2 (despliega su index.html)**
![Iniciar Apache](Act2_imgs/paso5.93.PNG)
**http://localhost/prueba2/pr2.html**
![Iniciar Apache](Act2_imgs/paso5.94.PNG)

## 6. Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”

Para redireccionar prueba a prueba2 vamos a crear un archivo dentro del primer directorio que haga la redirección:

**sudo nano /var/www/html/prueba/.htaccess**
![Iniciar Apache](Act2_imgs/paso6.1.PNG)
Dentro suya escribimos:

**Redirect 301 /prueba /prueba2**
![Iniciar Apache](Act2_imgs/paso6.2.PNG)
Guardamos y salimos. Ahora, debemos entrar en la configuración de Apache y darle permisos al directorio 'prueba' para que se cumpla la redirección:

**sudo nano /etc/apache2/apache2.conf**

Así es como se ve el contenido de apache2.conf originalmente:
![Iniciar Apache](Act2_imgs/paso6.3.PNG)

Es en este apartado donde escribiremos el nuevo permiso:

<'Directory /var/www/html/prueba>
	AllowOverride All'
<'/Directory'>
![Iniciar Apache](Act2_imgs/paso6.4.PNG)

Guardamos, lo cerramos y reiniciamos apache (sudo systemctl restart apache2).
![Iniciar Apache](Act2_imgs/paso6.5.PNG)

Ahora, cuando vamos a nuestro navegador, si intentamos ir a nuestra carpeta 'prueba', se nos redireccionará a 'prueba2':
![Iniciar Apache](Act2_imgs/paso6.6.PNG)
![Iniciar Apache](Act2_imgs/paso6.7.PNG)

Esto significa que no podremos abrir ni el index.html ni el pr1.html de prueba, puesto que siempre se redirecciona a prueba2, 
donde su index.html es diferente y donde no existe pr1.html, por lo que ese en concreto da error:
![Iniciar Apache](Act2_imgs/paso6.8.PNG)

## 7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.

Entramos de nuevo en htaccess:

**sudo nano /var/www/html/prueba/.htaccess**

Editamos su contenido, como solo queremos pasar un archivo, tenemos que especificarlo:

**Redirect 301 /prueba/pr1.html /prueba2/pr2.html**
![Iniciar Apache](Act2_imgs/paso7.1.PNG)

Guardamos, salimos y reiniciamos apache.

Si ahora nos vamos a nuestro localhost y ponemos la dirección de nuestro archivo (pr1.html en mi caso):

**http://localhost/prueba/pr1.html**
![Iniciar Apache](Act2_imgs/paso7.2.PNG)

Nos redirecciona a:
**http://localhost/prueba2/pr2.html**
![Iniciar Apache](Act2_imgs/paso7.3.PNG)


Para demostrar que esto SOLO redirecciona el archivo en concreto, he sacado captura entrando al index.html de prueba, cosa que antes (cuando redireccionabamos todo), no podiamos:

**http://localhost/prueba**
![Iniciar Apache](Act2_imgs/paso7.4.PNG)

## 8. Usa la directiva userdir.

En la terminal escribimos **sudo a2enmod userdir**, seguido de reiniciar apache (te pedirá la contraseña a la hora de activar mod_userdir)
![Iniciar Apache](Act2_imgs/paso8.1.PNG)

A continuación deberemos editar el archivo userdir.conf, concretamente el apartado de requerimientos:

Para abrir el archivo userdir.conf, escribimos en la terminal:
**sudo nano /etc/apache2/mods-enabled/userdir.conf** (podemos averiguar dónde está mods-enabled con **ls -l apache2**)
![Iniciar Apache](Act2_imgs/paso8.2.PNG)

Al abrirse, nos aparecerá algo similar a esto:
![Iniciar Apache](Act2_imgs/paso8.3.PNG)
(Muy importante la primera línea del código y cuidado con tocar el Directory)

Solo editaremos, por el momento, el apartado de 'Require' a esto:
![Iniciar Apache](Act2_imgs/paso8.3.1.PNG)

Después guardamos, salimos y reiniciamos apache. A continuación, creamos un directorio en nuestro home:

**sudo mkdir -p /home/usuario/public_html**
![Iniciar Apache](Act2_imgs/paso8.4.PNG)

Dentro de dicho archivo, crearemos un archivo:

**echo "<h1>HOLAAA</h1>" > /home/usuario/public_html/index.html**
**En usuario, escribes el nombre de tu cuenta de usuario, el mio es 'pablo'**
![Iniciar Apache](Act2_imgs/paso8.7.PNG)

A continuación, deberemos darle los permisos para poder verlo, de otra forma, saldrá error 403 forbidden:

**chmod 755 /home/pablo**
![Iniciar Apache](Act2_imgs/paso8.8.PNG)
Seguido de eso, reiniciamos apache.

Ahora nos vamos a nuestro navegador y ponemos:

**http://localhost/~pablo**
![Iniciar Apache](Act2_imgs/paso8.9.PNG)
(Denuevo, 'pablo' es mi nombre de cuenta de usuario)

## 9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.

Primero que nada, creamos el directorio donde se mostrará el resultado del redireccionamiento (carpeta_destino):

**mkdir /home/pablo/public_html/carpeta_destino**
![Iniciar Apache](Act2_imgs/paso9.1.PNG)

Dentro de esa carpeta, vamos a crear el archivo que contendrá un mensaje que saldrá por pantalla, se llamará index.html:
**echo "<h1>Carpeta</h1> > /home/pablo/public_html/carpeta_destino/index.html**
![Iniciar Apache](Act2_imgs/paso9.2.PNG)

Similar al ejercicio anterior, le daremos todos los permisos al archivo:

**chmod -R /home/pablo/public_html/carpeta_destino**
![Iniciar Apache](Act2_imgs/paso9.3.PNG)

Ahora vamos a editar el archivo de configuración de Apache:

**sudo nano /etc/apache2/sites-avaliable/000-default.conf**
![Iniciar Apache](Act2_imgs/paso9.4.PNG)

Al entrar, deberías de ver lo siguiente:
![Iniciar Apache](Act2_imgs/paso9.5.PNG)

En el siguiente trocito escribiremos el codigo que contendrá nuestro aliasy la configuración de los permisos del archivo:
![Iniciar Apache](Act2_imgs/paso9.7.PNG)

Revisamos que todo esté bien escrito (sino, nos dará un error al reiniciar apache), guardamos y reiniciamos apache.
![Iniciar Apache](Act2_imgs/paso9.8.PNG)

Ahora abrimos nuestro navegador y escribimos:

**http://localhost/mialias**
![Iniciar Apache](Act2_imgs/paso9.9.PNG)
(En mi caso, el nombre de mi alias es, justamente, 'mialias')


## 10. ¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?

Para poder desactivar la directiva Options, deberemos desactivarla tanto de apache2.conf y 000-default.conf, por lo que necesitaremos editar esos ficheros:

**sudo nano /etc/apache2/apache2.conf**
![Iniciar Apache](Act2_imgs/paso10.1.PNG)

Dentro, en el apartado de Directory, editaremos el apartado Options, y le añadimos -Indexes + FollowSymLinks:
Antes:
![Iniciar Apache](Act2_imgs/paso10.2.PNG)

Despues:
![Iniciar Apache](Act2_imgs/paso10.92.PNG)


Guardamos los cambios, salimos y reiniciamos apache. Puede que nos salga el siguiente aviso:
![Iniciar Apache](Act2_imgs/paso10.4.PNG)

Si nos sale, escribimos:
**systemctl daemon-reload**


Para comprobar si está desactivado o no la directiva Options, creamos un directorio sin index.html con mkdir:
![Iniciar Apache](Act2_imgs/paso10.5.PNG)
(En esta imagen, Options sigue activado, porque todavía no edité nada en 000-default.conf)

Como consecuencia, si intentamos abrir el directorio en nuestro navegador, aparece esto:
![Iniciar Apache](Act2_imgs/paso10.6.PNG)

Esto no es lo que queremos, queremos un error 403 Forbidden.
Vamos a editar el archivo 000-default.conf:
**sudo nano /etc/apache2/sites-enabled/000-default.conf**
![Iniciar Apache](Act2_imgs/paso10.93.PNG)


Una vez hemos editado ambos archivos si hacemos curl -I en nuestro directorio nos saldrá el error:

![Iniciar Apache](Act2_imgs/paso10.91.PNG)

Si lo buscamos en nuestro navegador saldrá el error también:
![Iniciar Apache](Act2_imgs/paso10.9.PNG)

La directiva Options está finalmente desactivada.


