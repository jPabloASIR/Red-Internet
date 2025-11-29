# Reescritura de URLs con Apache y PHP

## 1. Objetivo
# Enunciado: Crear URLs amigables que redirijan a un script PHP (`operacion.php`) realizando operaciones matemáticas básicas (suma, resta, multiplicación, división).
# Explicación:
# Se utiliza `mod_rewrite` de Apache para transformar URLs legibles por humanos en parámetros GET que PHP pueda procesar.

---

## 2. Configuración de Apache sin .htaccess
# Enunciado: Configurar el VirtualHost para aplicar reglas de reescritura directamente sin usar `.htaccess`.
# Solución:
# Editar `/etc/apache2/sites-available/000-default.conf` e insertar dentro del bloque <VirtualHost *:80>:
<Directory /var/www/html/actividad>
    Options FollowSymLinks
    AllowOverride None
    RewriteEngine On
    RewriteBase /actividad/
    RewriteRule ^([a-z]+)/([0-9]+)/([0-9]+)$ operacion.php?op=$1&op1=$2&op2=$3 [L]
</Directory>
# Explicación:
# RewriteEngine On -> activa el módulo de reescritura.
# RewriteBase /actividad/ -> establece la base de la URL que se va a reescribir.
# RewriteRule ^([a-z]+)/([0-9]+)/([0-9]+)$ ... -> captura la operación y dos números de la URL y los pasa como parámetros GET a operacion.php.
# [L] -> indica que si coincide esta regla, no se aplicarán más reglas.


---

## 4. Reiniciar Apache
**sudo systemctl restart apache2**


---

## 5. URLs de prueba


http://localhost/actividad/suma/3/5  
http://localhost/actividad/resta/10/2  
http://localhost/actividad/multiplica/4/6  
http://localhost/actividad/divide/20/5

# Apache convierte estas URLs en llamadas a `operacion.php?op=suma&op1=3&op2=5`, etc., mostrando el resultado de la operación.


# Ejercicios de reescritura:
# [José Domingo - mod_rewrite](http://www.josedomingo.org/pledin/2011/10/ejemplos-del-modulo-rewrite-en-apache-2-2/)
