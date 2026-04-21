# Memoria de Configuración: Servidor marisma.local

## 0. Instalar todo lo que necesitamos

![Trabajo1](pasos/0.PNG)
![Trabajo1](pasos/1.PNG)

## 1. Copiar base de datos de Bind9

sudo apt update  
sudo apt purge -y bind9 bind9utils bind9-doc  
sudo rm -rf /etc/bind  
sudo rm -rf /var/cache/bind  
sudo apt install -y bind9 bind9utils  
sudo cp /etc/bind/db.local /etc/bind/db.marisma.local
![Trabajo1](pasos/2.PNG)

## 2. Configurar los archivos (crear_subdominio.sh, crear_vhost.sh y crear_db.sh) y otorgarle permisos

![Trabajo1](pasos/3.PNG)

![Trabajo1](pasos/4.PNG)
![Trabajo1](pasos/5.PNG)
![Trabajo1](pasos/5.2.PNG)
![Trabajo1](pasos/6.PNG)
![Trabajo1](pasos/7.PNG)

### Comprobación de que todo está activo y sin errores:
![Trabajo1](pasos/7.2.PNG)
![Trabajo1](pasos/7.3.PNG)

## 3. Crear usuario pablo con IP de la VM

![Trabajo1](pasos/8.PNG)

## 4. Crear base de datos para el usuario pablo

![Trabajo1](pasos/9.PNG)

## 4. Generar la configuración de apache para pablo

![Trabajo1](pasos/91.PNG)

## 5. Comprobamos que nuestra VM conoce a marisma.local y habilitamos la configuración de phpmyadmin
![Trabajo1](pasos/92.PNG)

![Trabajo1](pasos/93.PNG)

## 6. Instalar servidor FTP

![Trabajo1](pasos/94.PNG)

### Tenemos que quitar la # de 'Default Root -'
![Trabajo1](pasos/95.PNG)

### También tenemos que configurar el archivo tls.conf con lo siguiente:
![Trabajo1](pasos/96.PNG)

## 7. Añadir usuario y habilitar el módulo del servidor web de apache

![Trabajo1](pasos/97.PNG)

![Trabajo1](pasos/98.PNG)

## 8. Comprobaciones de que todo funciona:

![Trabajo1](pasos/end1.PNG)

![Trabajo1](pasos/end2.PNG)

![Trabajo1](pasos/end3.PNG)
