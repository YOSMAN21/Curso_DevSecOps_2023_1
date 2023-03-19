# PGP utilizando Mailvelope
<p align="center">
    <img src="./img/logo_pgp.png" alt="logo" width="500"/>
</p>

## ¿Qué es PGP?
PGP es programa que sirve para cifrar y descifrar datos, de tal forma que solo el destinatario legítimo pueda descifrar la información. OpenPGP es el estándar abierto basado en PGP, y el que actualmente se utiliza en todos los programas. Mailvelope es una extensión para Chrome y Firefox que nos va a permitir cifrar y descifrar e-mails de los principales proveedores como Gmail, Outlook y Yahoo Mail.

## ¿Qué es Mailvelope?
Es una extensión para los navegadores Google Chrome y Mozilla Firefox que es totalmente gratuita, incorpora el estándar OpenPGP para el cifrado y descifrado de texto en los correos electrónicos, pero es que además permite cifrar los archivos adjuntos de dichos e-mails. Su utilización es muy sencilla si antes has usado algún programa basado en PGP para enviar y recibir correos electrónicos, hoy en RedesZone os vamos a enseñar cómo se configura y cómo se envían los e-mails cifrados para que nadie los lea.

---

## Tabla de contenido
1. Instalación de Mailvelope.
    - Adición extensión de navegador.
    - Configuración.
    - Generación clave pública y privada.
    - Verificación clave pública y privada.
	
2. Aplicación de Mailvelope para envío de correos.
    - Agregar contacto por importación.
    - Envío de correo firmado.
    - Recepción de correo firmado.
---

## 1. Instalación de Mailvelope

- Abrir en el navegador la página web de Mailvelope y descargar la extensión:
https://mailvelope.com/en

![Imagen 0](./img/0.png)

- Instalar la extensión en el navegador.

![Imagen 1](./img/1.png)

- Utilizar el ícono de la extensión de Mailvelope, en el navegador, para ingresar.

![Imagen 2](./img/2.png)

- Utilizar el botón "Generar llave" para configurar la llave pública y privada.

![Imagen 3](./img/3.png)

- Colocar el nombre de la llave, correo electrónico y contraseña.

![Imagen 4](./img/4.png)

- Aparecerá un aviso de generación de llave, esperar unos segundos...

![Imagen 5](./img/5.png)

- Una vez finalizado el proceso, aparecerá un mensaje de confirmación y la llave aparecerá en el listado.

![Imagen 6](./img/6.png)

- Cuando se crea una llave, se puede utilizar la opción "Avanzado" para definir el tipo de algoritmo encriptación, el tamaño de la llave y la fecha de caducidad de la misma.

![Imagen 7](./img/7.png)

- Desde el listado de claves disponible, se puede ver el datalle de cada una si se hace clic sobre la misma.

![Imagen 9](./img/9.png)

## 2. Aplicación de Mailvelope para envío de correos.

- Se puede exportar una llave para el envío e integración como contacto, en otro navegador.

![Imagen 10](./img/10.png)

- Utilizar la opción importar contactos, para agregar un archivo llave .asc

![Imagen 11](./img/11.png)

- Se muestra los datos del contacto contenido en la llave que se está importando.

![Imagen 12](./img/12.png)

- Se puede verificar una llave por confirmación en el correo, donde con la clave se puede visualizar.

![Imagen 13](./img/13.png)