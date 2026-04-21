# Memoria de Configuración: Servidor marisma.local

## 0. Instalar todo lo que necesitamos

![Descargando Apache](practica1tr2/pasos/0.PNG)

## 1. Limpieza y Reinstalación de Bind9

sudo apt update
sudo apt purge -y bind9 bind9utils bind9-doc
sudo rm -rf /etc/bind
sudo rm -rf /var/cache/bind
sudo apt install -y bind9 bind9utils

## 2. Configuración de DNS y Resolución

### Forzar resolución local en el archivo hosts
echo "192.168.206.201 marisma.local pablo.marisma.local pepe.marisma.local" | sudo tee -a /etc/hosts

### Configurar el servidor de nombres prioritario
sudo rm /etc/resolv.conf
echo "nameserver 127.0.0.1" | sudo tee /etc/resolv.conf

### Configuración de zona en Bind9
## Añadir zona "marisma.local" en /etc/bind/named.conf.local

### Configuración del archivo de datos de zona
sudo cp /etc/bind/db.local /etc/bind/db.marisma.local
sudo nano /etc/bind/db.marisma.local

### Verificación y reinicio de servicios
sudo named-checkzone marisma.local /etc/bind/db.marisma.local
sudo systemctl restart bind9
sudo systemctl stop systemd-resolved

## 3. Servidor Web (Apache2) y phpMyAdmin

### Instalación de la pila LAMP
sudo apt install apache2 mariadb-server php libapache2-mod-php php-mysql -y

### Instalación y vinculación de phpMyAdmin
sudo apt install phpmyadmin -y
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin
sudo systemctl restart apache2

## 4. Ejecución de Scripts de Automatización

### Asignación de permisos
chmod +x crear_subdominio.sh crear_vhost.sh crear_db.sh

### Ejecución para el usuario de ejemplo
sudo ./crear_subdominio.sh pablo 192.168.206.201
sudo ./crear_vhost.sh pablo
sudo ./crear_db.sh pablo

## 5. Configuración de FTP Seguro (TLS)

### Instalación de ProFTPD
sudo apt install proftpd -y

### Configuración de seguridad (DefaultRoot)
### Paso: Editar /etc/proftpd/proftpd.conf y activar DefaultRoot ~

### Generación del certificado SSL para TLS
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/proftpd.key -out /etc/ssl/certs/proftpd.crt

### Activación del módulo TLS
### Configurar /etc/proftpd/tls.conf con certificados y TLSRequired on
### Descomentar Include de tls.conf en proftpd.conf

sudo systemctl restart proftpd

## 6. Soporte de Aplicaciones Python

sudo apt install libapache2-mod-wsgi-py3 -y
sudo a2enmod wsgi
sudo systemctl restart apache2

## 7. Gestión de Usuarios y Privilegios

### Creación del usuario en el sistema operativo
sudo useradd -m -s /bin/bash pablo
echo "pablo:1177asdd" | sudo chpasswd

### Asignación de permisos sobre el DocumentRoot
sudo chown -R pablo:pablo /var/www/html/pablo
sudo chmod -R 755 /var/www/html/pablo
