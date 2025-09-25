# Actividad 0.3 - Práctica Telnet/HTTP

## 1. ¿Qué es Telnet?

Telnet es un protocolo de red que permite la comunicación bidireccional con un servidor a través de una interfaz de línea de comandos. Aunque ha sido reemplazado en gran medida por SSH debido a preocupaciones de seguridad, Telnet sigue siendo útil para pruebas y diagnósticos de red.  

---

## 2. ¿Cómo habilitar Telnet en Windows 10?

Para habilitar Telnet en Windows 10, sigue estos pasos:

1. Abre el **Panel de Control**.  
2. Selecciona **Programas** y luego **Activar o desactivar las características de Windows**.  
3. En la lista de características, marca la casilla **Cliente Telnet**.  
4. Haz clic en **Aceptar** y espera a que se complete la instalación.  

Una vez habilitado, puedes acceder a Telnet desde el **Símbolo del sistema** escribiendo telnet.

---

## 3. ¿Cómo utilizar Telnet para realizar peticiones HTTP?

Para realizar una petición HTTP utilizando Telnet, sigue estos pasos:

1. Abre el **Símbolo del sistema**.  
2. Escribe el siguiente comando para conectarte al servidor web: telnet **www.ejemplo.com 80**
Una vez conectado, escribe la siguiente solicitud HTTP:
GET / HTTP/1.1

Presiona **Enter** dos veces para enviar la solicitud.
El servidor responderá con los encabezados HTTP y el contenido de la página solicitada.

---

## 4. Ejemplo de una petición y respuesta HTTP utilizando Telnet

Conectándose a 'www.profesordeinformatica.com' en el puerto 80: **telnet www.profesordeinformatica.com 80**
GET / HTTP/1.1
Host: www.profesordeinformatica.com
La respuesta del servidor incluirá los encabezados HTTP y el contenido de la página principal.

---

## 5. ¿Qué es el Three-Way Handshake en TCP?

El **Three-Way Handshake** es el proceso utilizado por el protocolo TCP para establecer una conexión confiable entre un cliente y un servidor. Consiste en tres pasos:

1. **SYN:** El cliente envía un segmento SYN al servidor para iniciar la conexión.  
2. **SYN-ACK:** El servidor responde con un segmento SYN-ACK para confirmar la solicitud de conexión.  
3. **ACK:** El cliente envía un segmento ACK para confirmar la recepción del SYN-ACK y completar el establecimiento de la conexión.  

Este proceso asegura que ambos extremos están listos para la transmisión de datos.

