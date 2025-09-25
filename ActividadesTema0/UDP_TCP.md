# Actividad 0.2 - UDP y TCP: Comparativa de Protocolos de Transporte

## 1. Diferencias entre UDP y TCP

Las diferencias clave entre UDP y TCP incluyen:

- **Conexión:** TCP es orientado a conexión; UDP es sin conexión.  
- **Fiabilidad:** TCP garantiza la entrega de datos; UDP no garantiza la entrega.  
- **Control de flujo:** TCP tiene control de flujo; UDP no.  
- **Retransmisión:** TCP retransmite paquetes perdidos; UDP no.  
- **Orden de entrega:** TCP entrega los paquetes en orden; UDP no garantiza el orden.  
- **Velocidad:** UDP es más rápido debido a su menor sobrecarga.  

---

## 2. ¿Qué aplicaciones usan TCP?

Algunas aplicaciones que utilizan TCP incluyen:

- **HTTP:** Protocolo para la transferencia de páginas web.  
- **SMTP:** Protocolo para el envío de correos electrónicos.  
- **POP3:** Protocolo para la recepción de correos electrónicos.  
- **IMAP:** Protocolo para la gestión de correos electrónicos.  
- **SSH:** Protocolo para acceso remoto seguro a sistemas.  

---

## 3. ¿Qué aplicaciones usan UDP?

Algunas aplicaciones que utilizan UDP incluyen:

- **DNS:** Sistema de nombres de dominio.  
- **DHCP:** Protocolo de configuración dinámica de host.  
- **SNMP:** Protocolo simple de gestión de red.  
- **RTP:** Protocolo para la transmisión de audio y vídeo en tiempo real.  
- **TFTP:** Protocolo de transferencia de archivos trivial.  

---

## 4. ¿Qué capa almacena el puerto?

El número de puerto se almacena en la **capa de transporte** del modelo OSI. Esta capa es responsable de la comunicación entre procesos en diferentes hosts.  

---

## 5. ¿Qué capa almacena la dirección IP?

La dirección IP se almacena en la **capa de red** del modelo OSI. Esta capa se encarga del direccionamiento y enrutamiento de los paquetes de datos.  

---

## 6. ¿Qué es el three-way handshake?

El **three-way handshake** es el proceso utilizado por TCP para establecer una conexión entre un cliente y un servidor. Consiste en tres pasos:

1. **SYN:** El cliente envía un paquete SYN al servidor para iniciar la conexión.  
2. **SYN-ACK:** El servidor responde con un paquete SYN-ACK para confirmar la solicitud.  
3. **ACK:** El cliente envía un paquete ACK para establecer la conexión.  

Este proceso asegura que ambos lados están listos para la comunicación y que la conexión es fiable.
