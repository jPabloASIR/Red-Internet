# Red-Internet

#Tema 0
Ejercicio | Descripción
----------|------------
[Ejercicio0.1](/ActividadesTema0/HTTP_Introduction.html) | HTTP Introducción
[Ejercicio0.2](/ActividadesTema0/UDP_TCP.html) | UDP y TCP
[Ejercicio0.3](/ActividadesTema0/Telnet_http.html) | Telnet/http
[Ejercicio0.4](/ActividadesTema0/Curl.html) | Curl
[Ejercicio0.5](/ActividadesTema0/js04/js04.html) | Python Web Server


<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Actividad 0.2 - UDP y TCP: Comparativa de Protocolos de Transporte</title>
</head>
<body>
  <h1>Actividad 0.2 - UDP y TCP: Comparativa de Protocolos de Transporte</h1>

  <h2>1. Diferencias entre UDP y TCP</h2>
  <p>Las diferencias clave entre UDP y TCP incluyen:</p>
  <ul>
    <li><strong>Conexión:</strong> TCP es orientado a conexión; UDP es sin conexión.</li>
    <li><strong>Fiabilidad:</strong> TCP garantiza la entrega de datos; UDP no garantiza la entrega.</li>
    <li><strong>Control de flujo:</strong> TCP tiene control de flujo; UDP no.</li>
    <li><strong>Retransmisión:</strong> TCP retransmite paquetes perdidos; UDP no.</li>
    <li><strong>Orden de entrega:</strong> TCP entrega los paquetes en orden; UDP no garantiza el orden.</li>
    <li><strong>Velocidad:</strong> UDP es más rápido debido a su menor sobrecarga.</li>
  </ul>

  <h2>2. ¿Qué aplicaciones usan TCP?</h2>
  <p>Algunas aplicaciones que utilizan TCP incluyen:</p>
  <ul>
    <li><strong>HTTP:</strong> Protocolo para la transferencia de páginas web.</li>
    <li><strong>SMTP:</strong> Protocolo para el envío de correos electrónicos.</li>
    <li><strong>POP3:</strong> Protocolo para la recepción de correos electrónicos.</li>
    <li><strong>IMAP:</strong> Protocolo para la gestión de correos electrónicos.</li>
    <li><strong>SSH:</strong> Protocolo para acceso remoto seguro a sistemas.</li>
  </ul>

  <h2>3. ¿Qué aplicaciones usan UDP?</h2>
  <p>Algunas aplicaciones que utilizan UDP incluyen:</p>
  <ul>
    <li><strong>DNS:</strong> Sistema de nombres de dominio.</li>
    <li><strong>DHCP:</strong> Protocolo de configuración dinámica de host.</li>
    <li><strong>SNMP:</strong> Protocolo simple de gestión de red.</li>
    <li><strong>RTP:</strong> Protocolo para la transmisión de audio y vídeo en tiempo real.</li>
    <li><strong>TFTP:</strong> Protocolo de transferencia de archivos trivial.</li>
  </ul>

  <h2>4. ¿Qué capa almacena el puerto?</h2>
  <p>El número de puerto se almacena en la <strong>capa de transporte</strong> del modelo OSI. Esta capa es responsable de la comunicación entre procesos en diferentes hosts.</p>

  <h2>5. ¿Qué capa almacena la dirección IP?</h2>
  <p>La dirección IP se almacena en la <strong>capa de red</strong> del modelo OSI. Esta capa se encarga del direccionamiento y enrutamiento de los paquetes de datos.</p>

  <h2>6. ¿Qué es el three-way handshake?</h2>
  <p>El <strong>three-way handshake</strong> es el proceso utilizado por TCP para establecer una conexión entre un cliente y un servidor. Consiste en tres pasos:</p>
  <ol>
    <li><strong>SYN:</strong> El cliente envía un paquete SYN al servidor para iniciar la conexión.</li>
    <li><strong>SYN-ACK:</strong> El servidor responde con un paquete SYN-ACK para confirmar la solicitud.</li>
    <li><strong>ACK:</strong> El cliente envía un paquete ACK para establecer la conexión.</li>
  </ol>
  <p>Este proceso asegura que ambos lados están listos para la comunicación y que la conexión es fiable.</p>

</body>
</html>
