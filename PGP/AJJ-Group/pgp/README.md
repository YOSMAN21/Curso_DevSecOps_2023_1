# PGP utilizando Mailvelope
<p align="center">
    <img src="./img/logo_pgp.png" alt="logo" width="500"/>
</p>

##¿Qué es PGP?
PGP es programa que sirve para cifrar y descifrar datos, de tal forma que solo el destinatario legítimo pueda descifrar la información. OpenPGP es el estándar abierto basado en PGP, y el que actualmente se utiliza en todos los programas. Mailvelope es una extensión para Chrome y Firefox que nos va a permitir cifrar y descifrar e-mails de los principales proveedores como Gmail, Outlook y Yahoo Mail.

##¿Qué es Mailvelope?
Es una extensión para los navegadores Google Chrome y Mozilla Firefox que es totalmente gratuita, incorpora el estándar OpenPGP para el cifrado y descifrado de texto en los correos electrónicos, pero es que además permite cifrar los archivos adjuntos de dichos e-mails. Su utilización es muy sencilla si antes has usado algún programa basado en PGP para enviar y recibir correos electrónicos, hoy en RedesZone os vamos a enseñar cómo se configura y cómo se envían los e-mails cifrados para que nadie los lea.

---

## Tabla de contenido
1. Instalación de Mailvelope
    - Adición extensión de navegador
    - Configuración
    - Generación clave pública y privada
    - Verificación clave pública y privada
2. Uso de Mailvelope
    - Agregar contacto por importación
    - Envío de correo firmado
    - Recepción de correo firmado
---

## Instalación de GPG
La instalación de GPG puede variar dependiendo del sistema operativo o distribución que se esté utilizando. A continuación se listan algunas instrucciones generales para los sistemas operativos más comunes:

- **Ubuntu/Debian**: Para instalar GPG en Ubuntu o Debian, se debe abrir una terminal y ejecutar el siguiente comando:

    ```bash
    sudo apt-get install gnupg
    ```

- **Fedora/RHEL**: En Fedora o Red Hat Enterprise Linux (RHEL), se puede instalar GPG con el siguiente comando:

    ```bash
    sudo dnf install gnupg
    ```

- **CentOS**: En CentOS, se puede instalar GPG con el siguiente comando:

    ```bash
    sudo yum install gnupg2
    ```

- **MacOS**: Si se está usando macOS, puede instalar GPG a través de Homebrew. Primero, se instala Homebrew siguiendo las instrucciones en [https://brew.sh/](https://brew.sh/). Luego, se abre una terminal y ejecuta el siguiente comando:

    ```shell
    brew install gnupg
    ```

- **Windows**: En Windows, se puede instalar GPG usando Gpg4win. Se puede descargar la última versión de Gpg4win desde [https://gpg4win.org/](https://gpg4win.org/) y seguir las instrucciones de instalación.

---

## Comandos básicos
GPG posee una gran variedad de argumentos que permiten realizar diversas operaciones. A continuación se describen los comandos mas usados de GPG.  

Cabe aclarar que el uso de GPG se sustenta bajo la siguiente estructura:
```bash
gpg [options] [files]
```

- **gpg --help**  
    Despliega toda la información acerca de los principales parámetros posibles para utilizar. Además de la versión y los algoritmos soportados.
- **gpg --version**  
    Muestra la versión utilizada de GPG, sus algoritmos, y dependencias.
- **gpg --gen-key**  
    Genera un nuevo par de claves pública/privada
- **gpg --import <archivo>**  
    Importa una clave pública o privada desde un archivo
- **gpg --export --armor \<id de clave\>**  
    Exporta la clave pública especificada en - formato ASCII-armored
- **gpg --encrypt --recipient <id de clave> <archivo>**  
    Encripta un archivo con la clave pública especificada
- **gpg --decrypt \<archivo\>**  
    Desencripta un archivo
- **gpg --sign \<archivo\>**  
    Firma un archivo con la clave privada del usuario
- **gpg --verify \<archivo\>**  
    Verifica la firma de un archivo
- **gpg --list-keys**  
    lista las claves públicas del usuario
- **gpg --list-secret-keys**  
    Lista las claves privadas del usuario

Para mayor información acerca de todo el universo de comandos, puede consultar la documentación completa en la página oficial del proyecto GnuPG: [https://gnupg.org/documentation/index.html](https://gnupg.org/documentation/index.html).

---

## Caso de uso
El uso de llaves asimétricas permite dar un paso más haya en la seguridad al momento de transferir información a través de internet. Es por esto que en este ejemplo/caso de utilización, se va a ejecutar el ejercicio de encriptar un archivo, compartir la llave pública, y desencriptar el archivo a partir de la misma.

1. Se listan las llaves con el comando
    ```bash
    gpg --list-keys
    ```
    Inicialmente, si no se tienen llaves agregadas, el resultado va a ser vació.
2. Se genera una par de llaves con el comando
    ```bash
    gpg --full-gen-key
    ```
    Al ejecutar el comando, se inician una serie de preguntas que parametrizan la creación de las llaves.

    1. Que tipo de llave se quiere crear:
        ```bash
        gpg (GnuPG) 2.2.27; Copyright (C) 2021 Free Software Foundation, Inc.
        This is free software: you are free to change and redistribute it.
        There is NO WARRANTY, to the extent permitted by law.

        Please select what kind of key you want:
        (1) RSA and RSA (default)
        (2) DSA and Elgamal
        (3) DSA (sign only)
        (4) RSA (sign only)
        (14) Existing key from card
        Your selection? 1
        ```
        En este caso se va a usar el algoritmo por defecto **`RSA`**.
    2. Cual va a ser la longitud en bits de las llaves:
        ```bash
        RSA keys may be between 1024 and 4096 bits long.
        What keysize do you want? (3072) 4096
        Requested keysize is 4096 bits
        ```
        En este caso se va a digitar **`4096`**.
    3. Cual va a ser el tiempo de expiración de las llaves:
        ```bash
        Please specify how long the key should be valid.
               0 = key does not expire
            <n>  = key expires in n days
            <n>w = key expires in n weeks
            <n>m = key expires in n months
            <n>y = key expires in n years
        Key is valid for? (0) 1
        ```
        En este caso se va a digitar **``1``** que hace referencia a un dia como de duración de las llaves antes de que expiren. En caso de que sea una semana seria **`1w`**, etc.
    4. Confirmar la fecha:
        ```bash
        Key expires at Mon 20 Mar 2023 02:00:38 AM -05
        Is this correct? (y/N) y
        ```
        Luego de seleccionar el tiempo de expiración, se muestra la fecha en que expirarían las llaves. Ademas, pide confirmación.
    5. Generar la identidad del usuario
        ```bash
        GnuPG needs to construct a user ID to identify your key.

        Real name: John Doe
        Email address: johndow@prueballave.com
        Comment: Prueba diploomado
        You selected this USER-ID:
            "John Doe (Prueba diploomado) <johndow@prueballave.com>"

        Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
        ```
        De primera mano se digita la información respectiva al nombre, el correo electrónico y algún comentario. Luego se digita **`o`** para confirmar que todos los datos están OK.
    6. Digitar contraseña
        ```bash
        ┌──────────────────────────────────────────────────────┐
        │ Please enter the passphrase to                       │
        │ protect your new key                                 │
        │                                                      │
        │ Passphrase: ________________________________________ │
        │                                                      │
        │       <OK>                              <Cancel>     │
        └──────────────────────────────────────────────────────┘
        ```
        Se digita la contraseña de las llaves y se presiona **`OK`**. Es importante recalcar que la contraseña no puede ser olvidada, ya que se perderá acceso a las llaves y a los archivos que hayan sido encriptados con dichas llaves.

        En caso de que se ingrese una contraseña poco segura, aparecerá la siguiente advertencia:
        ```bash
        ┌───────────────────────────────────────────────────────┐
        │ Warning: You have entered an insecure passphrase.     │
        │                                                       │
        │ A passphrase should be at least 8 characters long.    │
        │                                                       │
        │ <Take this one anyway>         <Enter new passphrase> │
        └───────────────────────────────────────────────────────┘
        ```
        Donde se decide cambiarla o dejar la misma.
    7. Generar entropía
        ```bash
        We need to generate a lot of random bytes. It is a good idea to perform
        some other action (type on the keyboard, move the mouse, utilize the
        disks) during the prime generation; this gives the random number
        generator a better chance to gain enough entropy.
        We need to generate a lot of random bytes. It is a good idea to perform
        some other action (type on the keyboard, move the mouse, utilize the
        disks) during the prime generation; this gives the random number
        generator a better chance to gain enough entropy.
        ```
        Se deben seguir las instrucciones dadas, tales como mover el mouse, presionar alguna tecla del teclado, etc. Esto con el fin de agregar una variable única a las llaves.
    
    Al completarse todos los pasos, se genera la llave. Se informa de donde se almacena, el hash, el algoritmo usado, la información del usuario y la fecha de expiración.
    ```bash
    gpg: key 5FD5273BA77B4225 marked as ultimately trusted
    gpg: directory '/home/ex/.gnupg/openpgp-revocs.d' created
    gpg: revocation certificate stored as '/home/ex/.gnupg/openpgp-revocs.d/7E09B594444474318E1308405FD5273BA77B4225.rev'
    public and secret key created and signed.

    pub   rsa4096 2023-03-19 [SC] [expires: 2023-03-20]
        7E09B594444474318E1308405FD5273BA77B4225
    uid                      John Doe (Prueba diploomado) <johndow@prueballave.com>
    sub   rsa4096 2023-03-19 [E] [expires: 2023-03-20]
    ```
3. Se listan, de nuevo, las llaves con el comando
    ```bash
    gpg --list-keys
    ```
    Ahora, en este caso, luego de haber creado la llave, aparecerá listada:
    ```bash
    gpg: checking the trustdb
    gpg: marginals needed: 3  completes needed: 1  trust model: pgp
    gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
    gpg: next trustdb check due at 2023-03-20
    /home/ex/.gnupg/pubring.kbx
    ---------------------------
    pub   rsa4096 2023-03-19 [SC] [expires: 2023-03-20]
        7E09B594444474318E1308405FD5273BA77B4225
    uid           [ultimate] John Doe (Prueba diploomado) <johndow@prueballave.com>
    sub   rsa4096 2023-03-19 [E] [expires: 2023-03-20]
    ```
4. 