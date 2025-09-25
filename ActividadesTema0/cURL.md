# Actividad 0.4 - cURL

## 1. ¿Qué es cURL?

cURL es una herramienta de línea de comandos y una biblioteca para transferir datos con sintaxis de URL. Es compatible con muchos protocolos, incluidos HTTP, HTTPS, FTP, SCP, SFTP, LDAP, entre otros. Se utiliza comúnmente para interactuar con APIs, descargar archivos y realizar pruebas de conectividad de red.  

---

## 2. Ejemplos de uso de cURL

A continuación, se presentan cinco ejemplos prácticos de cómo utilizar cURL:


1. **Obtener el contenido de una página web: curl https://www.example.com**
Este comando realiza una solicitud GET a la URL especificada y muestra el contenido HTML de la página.

2. **Descargar un archivo y guardarlo con el nombre original: curl -O https://www.example.com/archivo.zip**
Usa la opción -O para guardar el archivo con el nombre que tiene en el servidor.

3. **Enviar datos con una solicitud POST: curl -X POST -d "usuario=juan&clave=1234" https://www.example.com/login**
Envía los datos del formulario al servidor utilizando el método POST.

4. **Incluir encabezados HTTP personalizados: curl -H "Authorization: Bearer token" https://www.example.com/api/datos**
Agrega un encabezado de autorización a la solicitud GET.

5. **Seguir redirecciones HTTP: curl -L https://www.example.com**
La opción '-L' permite que cURL siga las redirecciones HTTP hasta llegar al destino final.

---

## 3. Recursos adicionales

Para obtener más información sobre cURL y explorar más ejemplos, puedes consultar la documentación oficial:  


Manual de cURL: https://curl.se/docs/manual.html
