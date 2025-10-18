# 🔍 Actividad: Directivas de configuración en Apache

## `<IfModule>`
**Uso:**  
Se utiliza para comprobar si un módulo de Apache está cargado antes de aplicar una configuración. Evita errores cuando el módulo no está disponible.

**Ejemplo:**
```apache
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteRule ^index\.html$ index.php [L]
</IfModule>
```

---

## `LoadModule`
**Uso:**  
Sirve para cargar un módulo específico de Apache. Cada módulo añade funcionalidades adicionales al servidor (como SSL, reescritura de URLs, etc.).

**Ejemplo:**
```apache
LoadModule rewrite_module modules/mod_rewrite.so
```

---

## `Include`
**Uso:**  
Permite incluir archivos de configuración adicionales dentro del archivo principal (`httpd.conf` o similar). Se utiliza para organizar mejor la configuración.

**Ejemplo:**
```apache
Include conf/extra/httpd-vhosts.conf
```

---

## `<Directory>`
**Uso:**  
Define reglas y permisos para un directorio específico del sistema de archivos.

**Ejemplo:**
```apache
<Directory "/var/www/html">
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
```

---

## `<Files>`
**Uso:**  
Aplica configuraciones específicas a uno o varios archivos concretos.

**Ejemplo:**
```apache
<Files "config.php">
    Require all denied
</Files>
```

---

## `<Location>`
**Uso:**  
Se usa para aplicar directivas a una ruta de URL (no al sistema de archivos). Ideal para controlar el acceso a una parte específica del sitio.

**Ejemplo:**
```apache
<Location "/admin">
    AuthType Basic
    AuthName "Zona restringida"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Location>
```

---

## `<VirtualHost>`
**Uso:**  
Define configuraciones para un sitio web o dominio virtual (permite alojar varios sitios en un mismo servidor).

**Ejemplo:**
```apache
<VirtualHost *:80>
    ServerName www.ejemplo.com
    DocumentRoot "/var/www/ejemplo"
    ErrorLog ${APACHE_LOG_DIR}/ejemplo-error.log
    CustomLog ${APACHE_LOG_DIR}/ejemplo-access.log combined
</VirtualHost>
```

---

## ¿Qué son los ficheros `.htaccess`?
Los archivos **`.htaccess`** (Hypertext Access) son archivos de configuración distribuida que permiten aplicar directivas de Apache en directorios específicos sin modificar el archivo principal del servidor.

**Características principales:**
- Se colocan en el directorio donde se desea aplicar la configuración.
- Requieren que en la configuración del servidor se permita `AllowOverride`.
- Pueden controlar accesos, redirecciones, errores personalizados, reescritura de URLs, entre otros.
- Son leídos en tiempo de ejecución por Apache, lo que permite cambios sin reiniciar el servicio (aunque pueden impactar el rendimiento si se abusan).

**Ejemplo de `.htaccess`:**
```apache
# Activar reescritura
RewriteEngine On

# Redirigir /antiguo a /nuevo
Redirect 301 /antiguo /nuevo

# Reescritura de URL amigable
RewriteRule ^producto/([0-9]+)$ producto.php?id=$1 [L]

# Bloquear acceso a archivos .env
<Files ".env">
    Require all denied
</Files>
```

---

*Fin de la actividad en Markdown.*
