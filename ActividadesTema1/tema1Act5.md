# Configuración de Apache para dir1 y dir2

## 1. Creación de los directorios
**sudo mkdir -p /var/www/dir1**
sudo mkdir -p /var/www/dir2

---

## 2. Diferencia entre Order / Deny / Allow y Require (Apache 2.4)

### Configuración antigua 1
<Directory /var/www/example1>
    Order Deny,Allow
    Deny from All
    Allow from 192.168.1.100
</Directory>
- Primero deniega todo, luego permite solo 192.168.1.100.  
- Resultado: solo esa IP puede acceder.

### Configuración antigua 2
<Directory /var/www/example1>
    Order Allow,Deny
    Deny from All
    Allow from 192.168.1.100
</Directory>
- Primero permite, luego deniega.  
- Resultado: se niega todo, incluso 192.168.1.100.

### Equivalente en Apache 2.4 con Require
<Directory /var/www/example1>
    Require ip 192.168.1.100
</Directory>

---

## 3. Configuración de dir1

### Requisitos
- Permitir acceso desde 10.3.0.100
- Permitir acceso desde marisma.intranet
- Permitir acceso desde cualquier subdominio de marisma.intranet
- Permitir acceso desde 10.3.0.100/16
- Modificación final: permitir marisma.intranet y no permitir 10.3.0.101

### Configuración
<Directory /var/www/dir1>
    Options Indexes FollowSymLinks
    AllowOverride All

    <RequireAll>
        Require host marisma.intranet
        Require not ip 10.3.0.101
    </RequireAll>
</Directory>

---

## 4. Configuración de dir2

### Requisitos
- Permitir acceso a 10.3.0.100/8
- No permitir acceso desde marisma.intranet

### Configuración
<Directory /var/www/dir2>
    Options Indexes FollowSymLinks
    AllowOverride All

    <RequireAll>
        Require ip 10.0.0.0/8
        Require not host marisma.intranet
    </RequireAll>
</Directory>

> Alternativa compatible en todas las versiones 2.4:
<Directory /var/www/dir2>
    Options Indexes FollowSymLinks
    AllowOverride All

    <RequireAll>
        Require ip 10.0.0.0/8
        <RequireNone>
            Require host marisma.intranet
        </RequireNone>
    </RequireAll>
</Directory>

