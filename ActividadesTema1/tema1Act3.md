# Directivas de Apache

## Directivas de identificación

### 1. `ServerName`
- **Descripción**: Especifica el nombre del servidor. Se usa para indicar el nombre de dominio o la dirección IP del servidor que Apache utilizará para identificar el host.
- **Valor por defecto**: No tiene valor por defecto; es necesario especificarlo si se requiere.
- **Ubicación de definición**: Generalmente definida en el archivo de configuración principal de Apache (`httpd.conf` o `apache2.conf`).

### 2. `ServerAdmin`
- **Descripción**: Define la dirección de correo electrónico del administrador del servidor. Se utiliza para fines de contacto en los mensajes de error del servidor.
- **Valor por defecto**: `webmaster@localhost` (aunque debe configurarse según el servidor).
- **Ubicación de definición**: Normalmente en el archivo `httpd.conf` o en los archivos de configuración de los sitios habilitados.

### 3. `ServerTokens`
- **Descripción**: Controla la cantidad de información que Apache incluye en los encabezados HTTP. Si está configurado para mostrar información detallada, podría exponer la versión del servidor, lo que podría ser un riesgo de seguridad.
- **Valor por defecto**: `Full` (muestra la versión completa del servidor y el sistema operativo).
- **Ubicación de definición**: Usualmente en el archivo `httpd.conf` o en los archivos de configuración de seguridad de Apache.

---

## Directivas de localización de ficheros

### 1. `DocumentRoot`
- **Descripción**: Define el directorio raíz de documentos para el servidor web. Apache servirá los archivos de este directorio cuando se acceda a la raíz del servidor.
- **Valor por defecto**: `/var/www/html` en sistemas Linux (puede variar según la distribución).
- **Ubicación de definición**: En el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

### 2. `ErrorLog`
- **Descripción**: Especifica la ubicación del archivo donde Apache guardará los registros de errores del servidor.
- **Valor por defecto**: `logs/error_log` en el directorio de instalación de Apache.
- **Ubicación de definición**: Definido en el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

### 3. `CustomLog`
- **Descripción**: Define la ubicación y el formato de los registros de acceso de Apache. Los logs de acceso registran todas las solicitudes HTTP al servidor.
- **Valor por defecto**: `logs/access_log`.
- **Ubicación de definición**: Usualmente en el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

### 4. `ServerRoot`
- **Descripción**: Define la ubicación raíz de la instalación de Apache. Es el directorio donde Apache busca su configuración y otros archivos esenciales.
- **Valor por defecto**: `/etc/httpd` (en sistemas basados en Red Hat) o `/etc/apache2` (en sistemas basados en Debian).
- **Ubicación de definición**: Generalmente en el archivo `httpd.conf` o `apache2.conf`.

---

## Directivas de control de la conexión

### 1. `Timeout`
- **Descripción**: Especifica el tiempo máximo que Apache esperará para recibir la totalidad de una solicitud o respuesta. Si el tiempo de espera se excede, la conexión se cerrará.
- **Valor por defecto**: `300` segundos.
- **Ubicación de definición**: Usualmente en el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

### 2. `KeepAlive`
- **Descripción**: Controla si Apache mantiene las conexiones abiertas para múltiples solicitudes. Si está habilitado, Apache reutiliza las conexiones para manejar varias solicitudes HTTP sin necesidad de abrir nuevas conexiones.
- **Valor por defecto**: `On`.
- **Ubicación de definición**: En el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

### 3. `MaxKeepAliveRequests`
- **Descripción**: Especifica el número máximo de solicitudes que se pueden realizar en una conexión de Keep-Alive. Después de alcanzar este número, la conexión se cierra.
- **Valor por defecto**: `100`.
- **Ubicación de definición**: En el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

### 4. `KeepAliveTimeout`
- **Descripción**: Define el tiempo que Apache esperará para recibir la siguiente solicitud en una conexión de Keep-Alive antes de cerrarla.
- **Valor por defecto**: `5` segundos.
- **Ubicación de definición**: En el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

---

## Otras

### 1. `LogLevel`
- **Descripción**: Define el nivel de detalle de los logs generados por Apache. Puede tomar valores como `debug`, `info`, `warn`, `error`, `crit`, entre otros.
- **Valor por defecto**: `warn`.
- **Ubicación de definición**: Generalmente en el archivo de configuración principal (`httpd.conf` o `apache2.conf`).

### 2. `LogFormat`
- **Descripción**: Define el formato personalizado para los registros de acceso de Apache. Permite ajustar qué información se incluye en los logs de acceso.
- **Valor por defecto**: La directiva `CommonLogFormat` es comúnmente utilizada.
- **Ubicación de definición**: Usualmente en el archivo de configuración de Apache (`httpd.conf` o `apache2.conf`).

