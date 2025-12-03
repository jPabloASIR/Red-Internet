# Documentación de expresiones regulares

## 1. Directorios en /www/ cuyo nombre consista en tres dígitos
### Directorios dentro de /www/ con nombres de exactamente tres dígitos

**^\/www\/(.+\/)?[0-9]{3}**



### ^\/www\/ -> la ruta debe empezar con /www/
### (.+\/)? -> permite directorios intermedios opcionales
### [0-9]{3} -> exactamente tres dígitos al final

---

## 2. Ficheros: *.gif, *.jpeg, *.jpg, *.png
### Coincidir archivos de imágenes con extensiones comunes

**.+\.(gif|jpe?g|png)$**



### .+ -> cualquier nombre de archivo
### \. -> punto literal antes de la extensión
### (gif|jpe?g|png) -> permite gif, jpg, jpeg o png
### $ -> asegura que es el final del nombre

---

## 3. Redireccionar GIF a JPEG en otro servidor
### Redirigir todos los GIF a JPEG en otro servidor

**RedirectMatch "(.+)\.gif$" "http://other.example.com/$1.jpg"**



### (.+)\.gif$ -> captura el nombre del archivo GIF
### $1.jpg -> reemplaza la extensión y apunta al nuevo servidor

---

## 4. Números enteros y decimales
### Coincidir números enteros o decimales

**\d*\.?\d+**



### \d* -> cero o más dígitos antes del punto
### \.? -> punto decimal opcional
### \d+ -> al menos un dígito después del punto o del número entero

---

## 5. Números de teléfono en formato Americano
### Coincidir números tipo 123-123-1234

**\b\d{3}-?\d{3}-?\d{4}\b**



### \b -> límites de palabra
### \d{3}-?\d{3}-?\d{4} -> 3 dígitos, opcional guion, 3 dígitos, opcional guion, 4 dígitos

---

## 6. Palabras (letras)
### Coincidir palabras formadas solo por letras

**[a-zA-Z]+**



### [a-zA-Z] -> letras mayúsculas o minúsculas
### + -> al menos una letra

---

## 7. Códigos hexadecimales de color de 24 o 32 bits
### Coincidir códigos como #FFAABB o 0xFFAABBCC

**(#|0x)?(?:[0-9A-F]{2}){3,4}**



### (#|0x)? -> prefijo opcional # o 0x
### (?:[0-9A-F]{2}){3,4} -> 3 o 4 pares de dígitos hexadecimales

---

## 8. Palabras de 4 letras
### Coincidir palabras con exactamente 4 letras

**\b\w{4}\b**



### \b -> límites de palabra
### \w{4} -> exactamente 4 caracteres alfanuméricos

---

## 9. Número entero sin signo
### Coincidir números enteros positivos

**\b\d+\b**



### \d+ -> uno o más dígitos
### \b -> asegura que es un número completo

---

## 10. Número entero con signo
### Coincidir números enteros con signo opcional

**[-+]?\d+**



### [-+]? -> signo opcional
### \d+ -> dígitos del número

---

## 11. Números reales
### Coincidir números con o sin decimales

**[-+]?(([0-9]*\.[0-9]+)|([0-9]+))**



### [-+]? -> signo opcional
### ([0-9]*\.[0-9]+) -> decimales
### ([0-9]+) -> enteros

---

## 12. Números reales con exponente
### Coincidir números en notación científica

**[-+]?[0-9]*\.?[0-9]+([eE][-+]?[0-9]+)?**


---

## 13. Email
### Coincidir direcciones de correo electrónico válidas

**\b[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}\b**



### Parte local: [a-zA-Z0-9._%+\-]+
### @
### Dominio: [a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}

---

## 14. Números del 0 a 255
### Coincidir cualquier número válido de un octeto IP

**^([01][0-9][0-9]|2[0-4][0-9]|25[0-5])$**



### [01][0-9][0-9] -> 000-199
### 2[0-4][0-9] -> 200-249
### 25[0-5] -> 250-255
### ^ y $ -> aseguran coincidencia exacta
