# Tema 1 Acts 2.2

## 1. Script que añada un puerto de escucha en el fichero de configuración de Apache.

Iniciamos apache (sudo systemctl start apache2) y escribimos lo siguiente para crear el script:

**nano ~/add_apache_port.sh** (add_apache_port es el nombre de mi script)
![Descargando Apache](tema1Act2.2/1/paso1.PNG)

Dentro, escribimos el contenido de nuestro script.
![Descargando Apache](tema1Act2.2/1/paso2.PNG)

Una vez terminado, lo guardamos, cerramos y procedemos a reiniciar apache2 para que se actualicen los cambios.
![Descargando Apache](tema1Act2.2/1/paso3.PNG)

A continuación, hacemos que el script que hemos creado sea ejecutable con:

**chmod +x ~/add_apache_port.sh**
![Descargando Apache](tema1Act2.2/1/paso4.PNG)

Para ejecutar el script en un puerto, escribimos:

**sudo ~/add_apache_port.sh 8082**
![Descargando Apache](tema1Act2.2/1/paso5.PNG)

Si intentamos ejecutar en un puerto activa, nos saldrá el siguiente mensaje:
![Descargando Apache](tema1Act2.2/1/paso6.PNG)



## 2. Script que añada un nombre de dominio y una ip al fichero hosts.

Creamos el nuevo script:

**nano ~/add_entry_host.sh** (add_entry_host es el nombre de mi script)
![Descargando Apache](tema1Act2.2/2/paso1.PNG)

Dentro, escribimos el contenido de nuestro script.
![Descargando Apache](tema1Act2.2/2/paso2.PNG)
![Descargando Apache](tema1Act2.2/2/paso3.PNG)

Una vez terminamos, lo guardamos, cerramos y procedemos a reiniciar apache2 para que se actualicen los cambios.
![Descargando Apache](tema1Act2.2/2/paso4.PNG)

A continuación, hacemos que el script que hemos creado sea ejecutable con:

**chmod +x add_entry_host.sh**
![Descargando Apache](tema1Act2.2/2/paso5.PNG)

Finalmente, ejecutamos el script:

**sudo ./add_host_entry.sh 10.4.0.31 miejemplo** (miejemplo es el nombre con el que lo ejecuto, la IP se puede obtener usando hostname -I)
![Descargando Apache](tema1Act2.2/2/paso6.PNG)



## 3. Script que nos permita crear una página web con un título, una cabecera y un mensaje

Creamos el nuevo script:

**nano ~/create_webpage.sh** (create_webpage es el nombre de mi script)
![Descargando Apache](tema1Act2.2/3/paso1.PNG)

Dentro, escribimos el contenido de nuestro script.
![Descargando Apache](tema1Act2.2/3/paso2.PNG)
![Descargando Apache](tema1Act2.2/3/paso3.PNG)

Una vez terminamos, lo guardamos, cerramos y procedemos a reiniciar apache2 para que se actualicen los cambios.
![Descargando Apache](tema1Act2.2/3/paso4.PNG)

A continuación, hacemos que el script que hemos creado sea ejecutable con:

**chmod +x create_webpage.sh**
![Descargando Apache](tema1Act2.2/3/paso5.PNG)

Finalmente, ejecutamos el script:

**./create_webpage.sh "Mi sitio web" "Bienvenidos" "Esta es una web creada con un script"**
![Descargando Apache](tema1Act2.2/3/paso6.PNG)

Si todo sale bien, se creará un archivo 'pagina_web.html' en nuestra carpeta actual.
![Descargando Apache](tema1Act2.2/3/pagina7.PNG)
Podemos abrirla en nuestor navegador con:
firefox pagina_web.html
xdg-open pagina_web.html
También puedes buscar 'pagina_web.html' con el explorador de archivos y hacer doble clic en el archivo
![Descargando Apache](tema1Act2.2/3/paso7.PNG)
