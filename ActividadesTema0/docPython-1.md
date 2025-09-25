# Actividad 0.5: Prácticas Servidor Web Python

## Instalación de Python

Para instalar Python basta con descargarlo desde su página oficial: [python.org](https://www.python.org/downloads/).  
![Descargando Python](Python/Python1.PNG)

Una vez lo descargamos, procederemos a su instalación. Primero marcaremos la opción de **‘Install Now’**, lo que llevará a la instalación automática con los ajustes recomendados.  
![Instalación](Python/Python2.PNG)

Después de esperar a que se termine la instalación, podremos cerrar la ventana pulsando **Close**.  
![Cierre del instalador](Python/Python3.PNG)

---

## Abrir Python en CMD

Para abrir Python basta con escribir 'python' en nuestro CMD.  
Para salir del intérprete y volver a la terminal normal, simplemente escribimos 'exit()'.  

Para hacer un servidor personal bastan con poner **python -m http.server 8000**.
![Crear Server Python](Python/Python4.PNG)
Ahora, con **localhost:8000** aparece la siguiente página:
![localhost Server Python](Python/Python5.PNG)
Como no tengo ninguna página, ha aparecido el listado de archivos.

---

## Crear un servidor HTTP

Para hacer un http server primero debemos crear un archivo: **notepad server.py** será el mío.
![Crear Server HTTP](Python/Python6.PNG)

La primera vez que se crea un archivo saldrá un mensaje de si queremos crear dicho archivo, simplemente le damos a 'Sí'
![Creación archivo HTTP](Python/Python7.PNG)

El contenido de mi archivo:
![Contenido archivo HTTP](Python/Python8.PNG)

Reinicio mi localhost y ahora aparece el nuevo contenido de mi página:
![Nuevo contenido localhost](Python/Python9.PNG)

## Crear un dummy server

Para el dummy server el proceso es el mismo:
![Contenido archivo dummy](Python/Python91.PNG)
![Funciona (da error, que es lo que se supone que debe de dar puesto que el puerto está ocupado)](Python/Python92.PNG)



