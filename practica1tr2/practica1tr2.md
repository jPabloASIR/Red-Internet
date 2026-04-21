# Memoria de Configuración: Servidor marisma.local

## 1. Preparación del Entorno y Limpieza de DNS
Para asegurar una instalación limpia de Bind9 y evitar conflictos previos, se procede al purgado completo y posterior reinstalación del servicio.

![Trabajo1](pasos/0.PNG)
### Instalación masiva de los paquetes necesarios: Apache, PHP, MariaDB, Bind9, ProFTPD y módulos de Python.

![Trabajo1](pasos/1.PNG)
### Configuración del archivo named.conf.local para declarar la zona maestra "marisma.local" y su ruta de base de datos.

![Trabajo1](pasos/2.PNG)
### Creación del archivo de zona física copiando la plantilla por defecto a db.marisma.local.

---

## 2. Configuración de Scripts de Automatización y Permisos
Se preparan los scripts para la creación automatizada de subdominios, hosts virtuales y bases de datos SQL.

![Trabajo1](pasos/3.PNG)
### Creación del directorio de trabajo scripts_practica y apertura del script de creación de subdominios.

![Trabajo1](pasos/4.PNG)
### Contenido del script para automatizar la creación de directorios web y la actualización de registros en Bind9.

![Trabajo1](pasos/7.PNG)
### Uso de sudo chmod +x para otorgar permisos de ejecución a todos los archivos .sh tras un intento denegado.

### Verificación de servicios:
![Trabajo1](pasos/7.2.PNG)
### Comprobación del estado activo de Apache2 y verificación de que el módulo WSGI está habilitado.

![Trabajo1](pasos/7.3.PNG)
### Activación y comprobación del servicio SSH para permitir la administración remota segura.

---

## 3. Despliegue del Cliente "pablo"
Ejecución de los scripts para dar de alta los servicios del primer usuario.

![Trabajo1](pasos/8.PNG)
### Ejecución de crear_subdominio.sh asignando la IP de la máquina al subdominio pablo.marisma.local.

![Trabajo1](pasos/9.PNG)
### Ejecución de crear_db.sh para generar automáticamente la base de datos pablo_db y su usuario asociado.

![Trabajo1](pasos/91.PNG)
### Ejecución de crear_vhost.sh para generar el archivo de configuración de Apache y habilitar el sitio web de Pablo.

---

## 4. Resolución de Nombres y phpMyAdmin
Ajustes finales para la conectividad interna y la gestión de bases de datos.

![Trabajo1](pasos/92.PNG)
### Configuración manual del archivo /etc/hosts y /etc/resolv.conf para forzar la resolución del dominio marisma.local.

![Trabajo1](pasos/93.PNG)
### Comprobación de que el sistema ya no da "Fallo de resolución" y configuración del enlace simbólico para phpMyAdmin.

---

## 5. Configuración de Servidor FTP Seguro (TLS)
Instalación y endurecimiento de ProFTPD.

![Trabajo1](pasos/94.PNG)
### Acceso al directorio de configuración de ProFTPD para iniciar la personalización del servicio.

![Trabajo1](pasos/95.PNG)
### Edición del archivo proftpd.conf para activar DefaultRoot, confinando a los usuarios en sus carpetas.

![Trabajo1](pasos/96.PNG)
### Configuración del archivo tls.conf definiendo el uso de certificados SSL y obligando el cifrado de datos.

---

## 6. Usuarios de Sistema y Módulos Web
Finalización de permisos y soporte para aplicaciones.

![Trabajo1](pasos/97.PNG)
### Alta del usuario pablo en el sistema operativo y asignación de contraseña para acceso FTP/SSH.

![Trabajo1](pasos/98.PNG)
### Cambio de propietario del directorio web al usuario pablo para permitir la subida de archivos vía FTP.

---

## 7. Comprobaciones Finales de Funcionamiento

![Trabajo1](pasos/end1.PNG)
### Verificación del acceso web mediante el subdominio pablo.marisma.local, confirmando que Apache sirve el contenido correcto.

![Trabajo1](pasos/end2.PNG)
### Comprobación de la resolución DNS interna: el sistema reconoce correctamente tanto el dominio base como el subdominio del cliente.

![Trabajo1](pasos/end3.PNG)
### Validación del acceso a phpMyAdmin desde localhost, permitiendo la gestión de las bases de datos creadas por los scripts.
