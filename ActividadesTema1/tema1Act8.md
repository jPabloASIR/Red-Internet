# Introducción
El servidor web de Apache es uno de los más populares para proveer contenido web en Internet. Cuenta con más de la mitad de todos los sitios web activos en la red y es extremadamente poderoso y flexible.

Apache divide su funcionalidad y componentes en unidades independientes que pueden ser configuradas independientemente. La unidad básica que describe un sitio individual o el dominio llamado *virtual host*.

Estas asignaciones permiten al administrador utilizar un servidor para alojar varios dominios o sitios en una simple interface o IP utilizando un mecanismo de coincidencias. Esto es relevante para cualquiera que busque alojamiento para más de un sitio en un solo VPS.

Cada dominio que es configurado apuntará al visitante a una carpeta específica que contiene la información del sitio, nunca indicará que el mismo servidor es responsable de otros sitios. Este esquema es expandible sin límites de software tanto como el servidor pueda soportar la carga.

En esta guía, te diremos cómo puedes configurar tus virtual hosts de Apache en tu VPS con Ubuntu 14.04. Durante este proceso, aprenderás cómo configurar diferente contenido para diferentes visitantes dependiendo del dominio que soliciten.

# Pre-Requisitos
Antes de empezar este tutorial, deberías crear un usuario no-root siguiendo los pasos del 1 al 4 en esa guía.

Además necesitas tener instalado Apache para poder continuar los siguientes pasos. Si no lo has hecho aún, puedes instalar Apache en tu servidor mediante apt-get:

```bash
sudo apt-get update
sudo apt-get install apache2
```

Después de completar estos pasos, podemos empezar.

Para propósitos de esta guía, mi configuración creará un virtual host para **ejemplo.com** y otro para **pruebas.com**. Se hará referencia a ellos en esta guía, pero tú deberías sustituirlos por tus propios dominios durante el proceso.

# Paso Uno - Crear la Estructura del Directorio
El primer paso que necesitamos es crear la estructura de directorios que mantendrán la información de nuestro sitio.

```bash
sudo mkdir -p /var/www/ejemplo.com/public_html
sudo mkdir -p /var/www/pruebas.com/public_html
```
![Descargando Apache](Act8/Paso1.PNG)


# Paso Dos - Otorgar Permisos
```bash
sudo chown -R $USER:$USER /var/www/ejemplo.com/public_html
sudo chown -R $USER:$USER /var/www/pruebas.com/public_html
sudo chmod -R 755 /var/www
```
![Descargando Apache](Act8/Paso2.PNG)
![Descargando Apache](Act8/Paso3.PNG)

# Paso Tres — Crear una Página de Prueba
Editar el archivo:

```bash
nano /var/www/ejemplo.com/public_html/index.html
```
![Descargando Apache](Act8/Paso4.PNG)

Contenido ejemplo:

```html
<html>
  <head>
    <title>Bienvenido a Ejemplo.com!</title>
  </head>
  <body>
    <h1>Éxito! El Virtual Host ejemplo.com esta funcionando!</h1>
  </body>
</html>
```
![Descargando Apache](Act8/Paso5.PNG)

Copiar para el segundo sitio:

```bash
cp /var/www/ejemplo.com/public_html/index.html /var/www/pruebas.com/public_html/index.html
nano /var/www/pruebas.com/public_html/index.html
```
![Descargando Apache](Act8/Paso6.PNG)

Modificar a:

```html
<html>
  <head>
    <title>Bienvenido a Pruebas.com!</title>
  </head>
  <body>
    <h1>Éxito! El Virtual Host pruebas.com esta funcionando!</h1>
  </body>
</html>
```
![Descargando Apache](Act8/Paso7.PNG)

# Paso Cuatro — Crear Archivos Virtual Host
Copiar la plantilla:

```bash
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/ejemplo.com.conf
sudo nano /etc/apache2/sites-available/ejemplo.com.conf
```
![Descargando Apache](Act8/Paso8.PNG)
![Descargando Apache](Act8/Paso9.PNG)
Contenido esperado:

```apache
<VirtualHost *:80>
    ServerAdmin admin@ejemplo.com
    ServerName ejemplo.com
    ServerAlias www.ejemplo.com
    DocumentRoot /var/www/ejemplo.com/public_html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
![Descargando Apache](Act8/Paso91.PNG)
![Descargando Apache](Act8/Paso92.PNG)
![Descargando Apache](Act8/Paso93.PNG)

Copiar para el segundo dominio:

```bash
sudo cp /etc/apache2/sites-available/ejemplo.com.conf /etc/apache2/sites-available/pruebas.com.conf
sudo nano /etc/apache2/sites-available/pruebas.com.conf
```
![Descargando Apache](Act8/Paso94.PNG)
![Descargando Apache](Act8/Paso95.PNG)

Modificar a:

```apache
<VirtualHost *:80>
    ServerAdmin admin@pruebas.com
    ServerName pruebas.com
    ServerAlias www.pruebas.com
    DocumentRoot /var/www/pruebas.com/public_html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
![Descargando Apache](Act8/Paso96.PNG)

# Paso Cinco — Habilitar los Virtual Hosts
```bash
sudo a2ensite ejemplo.com.conf
sudo a2ensite pruebas.com.conf
sudo service apache2 restart
```
![Descargando Apache](Act8/Paso97.PNG)

Es posible ver este mensaje (no afecta nada):

```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name...
```

# Paso Seis — Configurar el archivo hosts local (Opcional)
En Linux/Mac:

```bash
sudo nano /etc/hosts
```

Agregar:

```
111.111.111.111 ejemplo.com
111.111.111.111 pruebas.com
```
![Descargando Apache](Act8/Paso98.PNG)

# Paso Siete — Probar
Visitar:

```
http://ejemplo.com
http://pruebas.com
```
![Descargando Apache](Act8/Paso99.PNG)
![Descargando Apache](Act8/Paso991.PNG)


Deberás ver las páginas de prueba configuradas anteriormente.
