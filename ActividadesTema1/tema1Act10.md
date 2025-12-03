
# PRÁCTICA: CONFIGURACIÓN APACHE SSL



## 1️⃣ Actualizar e instalar Apache y OpenSSL
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 openssl ufw -y

## 2️⃣ Crear clave privada para certificado autofirmado
sudo mkdir -p /etc/ssl/private /etc/ssl/certs
sudo openssl genrsa -out /etc/ssl/private/apache-selfsigned.key 2048

## 3️⃣ Crear certificado autofirmado (válido 365 días)
    sudo openssl req -x509 -key /etc/ssl/private/apache-selfsigned.key \
    -out /etc/ssl/certs/apache-selfsigned.crt -days 365 \
    -subj "/C=ES/ST=Estado/L=Ciudad/O=MiOrganizacion/CN=mivm.no-ip.org"

## 4️⃣ Ajustar permisos de los certificados
sudo chmod 600 /etc/ssl/private/apache-selfsigned.key
sudo chmod 644 /etc/ssl/certs/apache-selfsigned.crt

## 5️⃣ Crear VirtualHost SSL
sudo tee /etc/apache2/sites-available/mivm-ssl.conf > /dev/null <<EOL

    <VirtualHost *:443>
    ServerName mivm.no-ip.org
    ServerAlias www.mivm.no-ip.org
    DocumentRoot /var/www/html

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
    SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key

    <Directory /var/www/html>
        Require all granted
    </Directory>
    </VirtualHost>

    <VirtualHost *:80>
    ServerName mivm.no-ip.org
    ServerAlias www.mivm.no-ip.org
    DocumentRoot /var/www/html

    # Redirige HTTP a HTTPS
    RewriteEngine On
    RewriteRule ^(.*)$ https://%{HTTP_HOST}$1 [R=301,L]
    </VirtualHost>
    

## 6️⃣ Habilitar módulos y sitio en Apache
sudo a2enmod ssl
sudo a2enmod rewrite
sudo a2ensite mivm-ssl.conf
sudo systemctl reload apache2

## 7️⃣ Configurar firewall para HTTP y HTTPS
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
sudo ufw status

## 8️⃣ Configurar /etc/hosts para pruebas locales
Edita /etc/hosts en la VM o en tu máquina cliente y añade:
10.4.0.238   mivm.no-ip.org


