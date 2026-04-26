# Configuración de BIND9: Servidor Caché y Forwarding

Este documento detalla los pasos mínimos para transformar un servidor DNS en un resolvedor de caché y, posteriormente, en un configurador de reenvío (forwarding).

## 1. Instalación del servicio
Se realiza la actualización de los índices de paquetes y la instalación de BIND9 junto con sus herramientas de diagnóstico para habilitar las funciones de servidor de nombres.

## 2. Configuración como Servidor DNS de Caché
Para que el servidor actúe como caché, se edita el fichero de opciones de BIND. En este paso, se define una lista de control de acceso (ACL) para permitir consultas únicamente desde la red local o hosts de confianza. Se configura el servidor para que acepte consultas recursivas, permitiendo que busque y almacene en memoria las respuestas de los servidores raíz de internet.

## 3. Configuración como Servidor DNS de Forwarding (Reenvío)
Para evolucionar la configuración hacia un esquema de forwarding, se modifica nuevamente el fichero de opciones. En lugar de resolver directamente contra los servidores raíz, se especifican direcciones IP de servidores DNS externos (como los de Google o Cloudflare) en la sección de "forwarders". Esto permite que el servidor local delegue la resolución a nodos externos, manteniendo una copia en caché de los resultados para acelerar futuras peticiones.

## 4. Validación de la configuración y reinicio
Se utiliza la herramienta de verificación de sintaxis de BIND para asegurar que no existan errores en los ficheros modificados. Una vez validado, se reinicia el servicio para aplicar la nueva política de resolución.

## 5. Pruebas de resolución
Se realizan consultas de nombres de dominio externos para verificar:
- Que el servidor responde correctamente a las peticiones de los clientes autorizados.
- Que la resolución se realiza a través de los reenviadores configurados.
- Que el tiempo de respuesta disminuye en consultas sucesivas, confirmando el funcionamiento de la memoria caché.
