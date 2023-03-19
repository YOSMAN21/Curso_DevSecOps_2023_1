# GPG por linea de comandos
<p align="center">
    <img src="./imgs/logo-gpg.png" alt="logo" width="500"/>
</p>

GPG es un software, basado en el estándar RFC4880, que firma y cifrado de código abierto que esta inspirado en PGP, se puede considerar como la alternativa OpenSource. Como lo mencionan en la pagina oficial de GPG:

> GnuPG is a complete and free implementation of the OpenPGP standard as defined by RFC4880 (also known as PGP). GnuPG allows you to encrypt and sign your data and communications; it features a versatile key management system, along with access modules for all kinds of public key directories. GnuPG, also known as GPG, is a command line tool with features for easy integration with other applications. A wealth of frontend applications and libraries are available. GnuPG also provides support for S/MIME and Secure Shell (ssh). 

Existen diversos comandos que permiten realizar una gran diversidad de tareas relacionadas al cifrado, firma y distribución de llaves.
El uso por consola de comandos varia dependiendo de las condiciones de cada sistema operativo, pero la esencia se mantiene, ya que es un software multiplataforma.

---

## Tabla de contenido
1. Instalación de GPG
2. Comandos básicos

---

## Instalación de GPG
La instalación de GPG puede variar dependiendo del sistema operativo o distribución que se este utilizando. A continuación se listan algunas instrucciones generales para los sistemas operativos más comunes:

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

- **MacOS**: Si se está utilizando macOS, puede instalar GPG a través de Homebrew. Primero, se instala Homebrew siguiendo las instrucciones en [https://brew.sh/](https://brew.sh/). Luego, se abre una terminal y ejecuta el siguiente comando:

    ```shell
    brew install gnupg
    ```

- **Windows**: En Windows, se puede instalar GPG utilizando Gpg4win. Se puede descargar la última versión de Gpg4win desde [https://gpg4win.org/](https://gpg4win.org/) y seguir las instrucciones de instalación.

---

## Comandos básicos
GPG posee una gran variedad de argumentos que permiten realizar diversas operaciones. A continuación se describen los comandos mas usados de GPG.  

Cabe aclarar que el uso de GPG se sustenta bajo la siguiente estructura:
```bash
gpg [options] [files]
```

- **gpg --help**  
    Despliega toda la información acerca de los principales parámetros posibles para usar. Ademas de la version y los algoritmos soportados.
- **gpg --version**  
    Muestra la version usada de GPG, sus algoritmos, y dependencias.
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

