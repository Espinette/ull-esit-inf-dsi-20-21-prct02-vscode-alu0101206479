# Informe
## Práctica 2 - Instalación y configuración de Visual Studio Code
### Desarrollo de Sistemas Informáticos
### ACOIDAN MESA HERNANDEZ - alu0101206479@ull.edu.es

#### Introducción

Esto es un informe para poder llevar a cabo la **práctica 2 de Desarrollo de Sistemas Informáticos**, hemos aprendido bastantes funcionalidades de **Visual Studio Code**, así como añadir extensione y conectarnos por `SSH` a nuestra máquina virtual. Tambien cabe destacar que hemos dado el primer paso con JavaScript y TypeScript y hemos aprendido a usar sesiones colaborativas.

#### Objetivos

Los objetivos de esta práctica han sido por un lado instalar Visual Studio Code y configurarlo para poder conectarnos a nuestra máquina remota por `SSH`, por otro lado aprender a usar las sesiones colaborativas y por último hacer un primer proyecto en TypeScript.

#### Pasos a seguir para instalar Visual Studio Code (Si no lo tuviese instalado)

[Visual Studio Code (VSCode)](https://code.visualstudio.com/) es uno de los entornos más utilizados por los desarrolladores. Yo en mi caso ya lo tenía instalado por lo que no me hizo falta hacer esto, pero si no lo tienes se puede instalar haciendo uso del siguiente comando:

```bash
  acoidan@ordenador:~$ sudo apt install code
```

O también se puede hacer uso de snap:

```bash
  acoidan@ordenador:~$ sudo snap install code --classic
```

#### Pasos a seguir para configurar Visual Studio Code para conectarse a una máquina remota por SSH

##### 1. Tener hecha la práctica 1
Para realizar esto debemos haber llevado acabo la [Práctica 1](https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-alu0101206479/) y tener conectada la VPN de la ULL.

Una vez hecho esto, deberiamos poder conectarnos a nuestra máquina virtual por `SSH` nada más ejecutando el comando:

```bash
  ssh iaas-dsi
```

Pero con el nombre correspondiente que le hayamos puesto a la máquina en la Práctica 1.

##### 2. Abrir VSCode e instalar *Remote - SSH*
Ahora lo que debemos hacer es abrir una ventana de VSCode y pulsar `Ctrl + Shift + X` para abrir el buscador de extensiones de la interfaz, una vez abierto buscaremos la extensión *Remote - SSH* y la instalaremos pulsando el botón *Install*. Si se pierde haciendo esto, puede mirar la página del [Extension Marketplace de VSCode](https://code.visualstudio.com/docs/editor/extension-gallery).

A continuación, pulsaremos `F1` o `Ctrl + Shidt + P` para abrir la paleta de comandos, una vez abierta introduciremos `SSH` y pulsaremos sobre `Connect to Host...`. Si hemos hecho todos los pasos de la práctica 1 nos deberá aparecer el nombre de nuestra máquina virtual en el menú desplegable y si no aparece deberemos editar el fichero `~/.ssh/config` añadiendole las líneas necesarias como hicimos en la anterior práctica. Posteriormente pulsaremos en el nombre de la máquina virtual, se abrirá una nueva ventana de VSCode y se iniciará en esta la conexión SSH.

Para comprobar que esta bien conectado, podemos observar en la parte inferior izquierda, en un área de color verde, el nombre de la máquina virtual a la que estamos conectados. Pero para asegurarnos deberíamos pulsar en la parte superior donde pone *Terminal* y en el menú desplegable darle a *New Terminal...*, esto nos abrirá una terminal. En esta deberíamos observar que el formato del prompt esta cambiado a como lo habíamos cambiado a la práctica 1 y ejecutaremos el comando:

```bash
  # Nos mostrará el nombre del host máquina virtual a la que estamos conectados
  [~()]$hostname
  iaas-dsi
```

#### Pasos para poder realizar sesiones colaborativas con Visual Studio Live Share
En Visual Studio Code podemos iniciar sesiones colaborativas a través de la extensión [Live Share Extension Pack](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare-pack), la cual permite colaborar en las tareas de desarrollo en tiempo real.

##### 1. Instalar la extensión Live Share Extension Pack
Lo primero que debemos hacer es instalar la extension Live Share Extension Pack, la cual nos instalará dos sub-extensiones, Live Share y Live Share Audio. Esto lo podremos hacer como hicimos en los *pasos para configurar Visual Studio Code para conectarse a una máquina remota por SSH*.

Es importante destacar que si estamos conectados por SSH a una máquina remota como la del IaaS, las extensiones se instalarán en dicha máquina remota y no en la máquina local. Para instalar las extensiones en la máquina local deberemos conectarnos de la máquina remota y para instalarlas en la máquina remota deberemos conectarnos a ella.

##### 2. Iniciar una sesión colaborativa para probar
Para iniciar una sesión colaborativa, primero, deberemos hacer click en el botón *Live Share* en la parte inferior izquierda de la ventana del VSCode. Esto nos pedirña que iniciemos sesión con nuestra cuenta de GitHub o de Microsoft la primera vez (Sirve para que otros desarrolladores nos identifiquen).

Ya iniciada la sesión nos debería salir nuestro nombre de usuario con el que hayamos iniciado sesión donde se encontraba el botón *Live Share*. Posteriormente iremos al botón `File` y pulsaremos `Open File...` para abrir un archivo. Una vez abierto, iremos a la parte inferior izquierda donde pone *Session Details* y veremos los detalles de la sesión, ahí podemos invitar a participantes, iniciar una llamada de audio, etc.

Si nos han quedado dudas, podemos leer la [documentación de Visual Studio Live Share](https://docs.microsoft.com/en-us/visualstudio/liveshare/).

```bash
  ssh usuario@10.6.XXX.XXX
```

#### Pasos para realizar un primer proyecto en TypeScript: “Hola Mundo”

##### 1. Instalar las extensiones necesarias

En primer lugar, debemos instalar como ya hemos hecho anteriormente las extensiones **Vim** (Un editor de texto) y **ESLint** (Permite realizar comprobaciones de estilo sobre ficheros que incluyen código fuente en JavaScript y TypeScript) en VSCode.

##### 2. Instalar el compilador de TypeScript

Abriremos una conexión por `SSH` en el VSCode, abriremos una nueva terminal y ejecutaremos los siguientes comandos:

```bash
  # La opción --global permite instalar el paquete de manera global
  [~()]$npm install --global typescript

  added 1 package, and audited 2 packages in 2s

  found 0 vulnerabilities
  [~()]$tsc --version
  Version 4.1.5
```

##### 3. Crear el directorio hello-world y el fichero package.json

A continuación, ejecutaremos los siguientes comandos para crear los directorios y ficheos necesarios:

```bash
  # Comprobamos que estamos situados en la carpeta personal de la maquina remota virtual
  [~()]$pwd
  /home/usuario
  
  # Creamos el directorio 'hello-world'
  [~()]$mkdir hello-world
  
  # Nos movemos al directorio 'hello-world'
  [~()]$cd hello-world/
  
  # Creamos un fichero denominado 'package.json' y observamos su contenido, este fichero establecerá las depenedencias de desarrollo y ejecutará el proyecto a modo de paquetes de los que depende el proyecto actual
  [~/hello-world()]$npm init --yes
  Wrote to /home/usuario/hello-world/package.json:

  {
    "name": "hello-world",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [],
    "author": "",
    "license": "ISC"
  }

  # Mostramos lo que contiene el directorio 'hello-world'
  [~/hello-world()]$ls -lrtha
  total 12K
  drwxr-xr-x 26 usuario usuario 4,0K feb  9 18:46 ..
  drwxrwxr-x  2 usuario usuario 4,0K feb  9 18:48 .
  -rw-rw-r--  1 usuario usuario  225 feb  9 18:48 package.json
  [~/hello-world()]$
```

##### 3. Abrir el directorio `~/hello-world` en VSCode

Posteriormente, iremos al menú `File`, haremos clic en la opción `Open Folder...` y seleccionaremos `hello-world` en el menú desplegable. Esto nos abrirá una nueva ventana de VSCode y en el explorador podremos ver el contenido del directorio `~/hello-world`.

##### 3. Abrir el directorio `~/hello-world` a un espacio de trabajo (workspace)

También vamos a añadir el directorio a 






Después, te pide que introduzcas la contraseña, la cual es `usuario` y una vez introducida el propio sistema te pedirá que cambies la contraseña. Para ello te hará introducir la contraseña actual (`usuario`) y posteriormente te hará introducir dos veces la nueva contraseña *(Es recomendable que la apuntes en algún lugar seguro para que no se te olvide)*.

Posteriormente se nos habrá cerrado la sesión por lo que nos conectaremos de nuevo a través de `ssh` e introduciremos como contraseña la nueva.

##### 4. Modificar el nombre del host de la máquina virtual
Para hacer esto modificaremos el fichero `/etc/hostname`, el cual contiene el nombre del host de la máquina (el cual sera `ubuntu`) y lo cambiaremos por el nombre que queramos, en mi caso ha sido `iaas-dsi`. Para hacer esto ejecutaremos los siguientes comandos:

```bash
  # Mostramos el nombre de la máquina
  usuario@ubuntu:~$ cat /etc/hostname
  ubuntu
  
  # Lo cambiamos editando el fichero
  usuario@ubuntu:~$ sudo vi /etc/hostname
  
  # Mostramos el nombre nuevamente para comprobar que se haya cambiado
  usuario@ubuntu:~$ cat /etc/hostname
  iaas-dsi
```

A parte de esto, tambien deberemos modificar ciertos parámetros en el fichero `/etc/hosts`:

```bash
  # Mostramos el contenido del fichero (las ip seguido de los nombres de los hosts)
  usuario@ubuntu:~$ cat /etc/hosts
  127.0.0.1	localhost
  127.0.1.1	ubuntu
  ...

  # Editamos el fichero para cambiar el nombre del host local (ubuntu) por el que habíamos puesto
  usuario@ubuntu:~$ sudo vi /etc/hosts

  # Mostramos el contenido del fichero nuevamente para comprobar que se haya cambiado
  usuario@ubuntu:~$ cat /etc/hosts
  127.0.0.1	localhost
  127.0.1.1	iaas-dsi
  ...
```

Ya hemos cambiado el nombre de host antiguo `ubuntu`, por el nuevo.

##### 5. Actualizar los cambios y reiniciar la máquina virtual
Ahora, actualizaremos la máquina con los siguientes comandos:

```bash
  usuario@ubuntu:~$ sudo apt update
  ...
  usuario@ubuntu:~$ sudo apt upgrade
  ...
```

Y reiniciamos la máquina virtual:

```bash
  usuario@ubuntu:~$ sudo reboot
  Connection to 10.6.XXX.XXX closed by remote host.
  Connection to 10.6.XXX.XXX closed.
```

##### 6. Añadir como host de la maquina local la máquina virtual

Antes de volver a conectarnos a la máquina virtual, editaremos el fichero `/etc/hosts` de la máquina local para incluir la información de conexión a la máquina virtual y así poder conectarnos sin tener que usar la IP, sino solo con el usuario y el nombre del host.

```bash
  # Mostramos el contenido del fichero (las ip seguido de los nombres de los hosts)
  acoidan@ordenador:~$ cat /etc/hosts
  127.0.0.1	localhost
  127.0.1.1	ordenador
  ...
  
  # Editamos el fichero para añadir la línea '10.6.XXX.XXX	iaas-dsi' con el nombre que queramos, en mi caso 'iaas-dsi'
  acoidan@ordenador:~$ sudo vi /etc/hosts

  # Mostramos el contenido del fichero nuevamente para comprobar que se haya cambiado
  acoidan@ordenador:~$ cat /etc/hosts
  127.0.0.1	localhost
  127.0.1.1	ordenador
  10.6.XXX.XXX	iaas-dsi
  ...
```

##### 7. Configurar la infraestructura de la clave pública-privada de nuestra máquina local

Para comprobar si ya tenemos generada una clave pública-privada ejecutaremos el comando:

```bash
  acoidan@ordenador:~$ cat .ssh/id_rsa.pub 
  ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDhVLdhoSjuanwqdKnXeTo7U6M0Clcf3upzQ5Y9AXbJl04FoFgLQrcvlbnpPlXCzp4+GGXlf9SjpCooqNcZ22q2EwwW50MyjaxGqzdb0yWOk1/HYjhpcKnKyVLlgpBvDKwAlg4JXwvFkQq+WCmmazC6/+3kOhkQw4SWkBvzz1vf5LMDOF1Ja8j2isWwxebgSf9nxRlbDaaRXa1mkkRAwm1sglRwTU7h/fG7LIYvbTs+Cs7KtVyMTxbdYPLv4tHHekOCL5G3Ewd966drZ8edUE/Q5gDxk+9umHzDYZ729yV7LE6IWPyJ5sxfhP6acdbHiDIqiYm4Z8in84OB8c4hVtVAkIIhRqecC3RYf52Sv6UgRZNj0QDNUcHksPXY1OhsctPgXEXD2OIxuL9lHxPmD2Jt5cFCBoux7yRUth8/nho43OYUyv79yw2XCLCF6ZAZ0wvabfBvFa2m4k8ueNXfPRl/x/Zf37JNh5PjZA6/NYq0+sxPVSZoYFlG8tuKK5GPMz0= acoidan@ordenador
```

Yo por ejemplo como se puede observar ya había generado mi par de claves pública-privada. Si nos pone que el fichero no existe deberemos ejecutar lo siguiente:

```bash
  acoidan@ordenador:~$ ssh-keygen
```

Tomaremos los valores por defecto, para ello pulsaremos intro sin escribir absolutamente nada. Una vez generadas las claves, ejecutaremos el siguiente comando para permitir copiar su clave pública desde la máquina local a la virtual y en la pregunta introduciremos `yes`:

```bash
  acoidan@ordenador:~$ ssh-copy-id usuario@iaas-dsi
  The authenticity of host 'iaas-dsi (10.6.XXX.XXX)' can't be established.
  ECDSA key fingerprint is SHA256:1Xm4M66FeBUSiykP7SqJgObwjmVs2gEouBhy1PTWDV4.
  Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
  /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
  /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
  usuario@iaas-dsi's password: 

  Number of key(s) added: 1

  Now try logging into the machine, with:   "ssh 'usuario@iaas-dsi'"
  and check to make sure that only the key(s) you wanted were added.
```

Una vez hecho esto, iniciaremos sesión en la máquina virtual por `SSH` nada mas usando el usuario y el nombre y nos tendría que dejar.

```bash
  acoidan@ordenador:~$ ssh usuario@iaas-dsi
  Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-135-generic x86_64)

   * Documentation:  https://help.ubuntu.com
   * Management:     https://landscape.canonical.com
   * Support:        https://ubuntu.com/advantage

    System information as of Fri Feb  5 10:16:46 WET 2021

  ...

  Last login: Fri Feb  5 10:14:25 2021 from 10.20.53.243
  usuario@iaas-dsi:~$
```

##### 7. Modificar el fichero de configuración SSH de la máquina local para no tener que introducir el usuario para iniciar sesión en la máquina virtual

Si a parte de no tener que usar la IP a la hora de iniciar sesión, tampoco se quisiera utilizar el nombre de usuario (`usuario`), podemos configurar el fichero `~/.ssh/config` en la máquina local ejecutando lo siguiente:

```bash
  # Creamos el fichero vacío
  acoidan@ordenador:~$ touch ~/.ssh/config
  
  # Editamos el fichero y añadimos 3 líneas, la primera 'Host iaas-dsi', la segunda ' HostName iaas-dsi' y la tercera 'User usuario' (La línea 1 y 2 deben tener el nombre de la máquina que le hayamos puesto)
  acoidan@ordenador:~$ vi ~/.ssh/config
  
  # Mostramos el contenido del fichero nuevamente para comprobar que se haya cambiado
  acoidan@ordenador:~$ cat ~/.ssh/config 
  Host iaas-dsi
    HostName iaas-dsi
    User usuario
```

Ahora nos podemos conectar a la máquina virtual por `SSH` simplemente con el nombre correspondiente:

```bash
  acoidan@ordenador:~$ ssh iaas-dsi
```


#### Pasos a seguir para instalar git y Node.js en la máquina virtual del IaaS

##### 1. Instalare git en la máquina virtual
Lo haremos ejecutando el siguiente comando:

```bash
  usuario@iaas-dsi:~$ sudo apt install git
  Leyendo lista de paquetes... Hecho
  Creando árbol de dependencias       
  Leyendo la información de estado... Hecho
  git ya está en su versión más reciente (1:2.25.1-1ubuntu3).
  0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
```

##### 2. Configurar git en la máquina virtual
Para configurar git se puede seguir la guia [configurar git por primera vez](https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Configurando-Git-por-primera-vez), pero la configuración se reduce básicamente en los siguientes comandos con los datos correspondientes:

```bash
  # Añadimos el nombre de usuario
  usuario@iaas-dsi:~$ git config --global user.name "ACOIDAN MESA HERNANDEZ"
  
  # Añadimos el correo electrónico
  usuario@iaas-dsi:~$ git config --global user.email alu0101206479@ull.edu.es
  
  # Comprobamos que los datos se hayan añadido correctamente
  usuario@iaas-dsi:~$ git config --list
  user.name=ACOIDAN MESA HERNANDEZ
  user.email=alu0101206479ull.edu.es
```

##### 3. Configurar el prompt de la terminal en la máquina virtual
Ahora, configuraremos el prompt de la terminal de la máquina virtual para que aparezca la rama actual en la que nos encontramos cuando accedemos a algún directorio asociado con un repositorio git. Para hacer esto, lo primero que haremos es descargar el script [git prompt](https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh) o crear el fichero `git-prompt.sh` y pegar en este todo el contenido del script mencionado. Lo podemos crear con el comando:

```bash
  usuario@iaas-dsi:~$ vi git-prompt.sh
```

Posteriormente ejecutaremos los siguientes comandos:

```bash
  # Cambiamos el nombre del script
  usuario@iaas-dsi:~$ mv git-prompt.sh .git-prompt.sh
  
  # Le añadimos al final del fichero '.bashrc' la línea 'source ~/.git-prompt.sh' y la línea 'PS1='\[\033]0;\u@\h:\w\007\]\[\033[0;34m\][\[\033[0;31m\]\w\[\033[0;32m\]($(git branch 2>/dev/null | sed -n "s/\* \(.*\)/\1/p"))\[\033[0;34m\]]$''
  usuario@iaas-dsi:~$ vi .bashrc
  
  # Comprobamos el final del fichero para asegurarnos de que se haya añadido correctamente
  usuario@iaas-dsi:~$ tail .bashrc
  ...
  source ~/.git-prompt.sh
  PS1='\[\033]0;\u@\h:\w\007\]\[\033[0;34m\][\[\033[0;31m\]\w\[\033[0;32m\]($(git branch 2>/dev/null | sed -n "s/\* \(.*\)/\1/p"))\[\033[0;34m\]]$'

  # Reiniciamos la terminal
  usuario@iaas-dsi:~$ exec bash -l
  [~()]$
```

Como se puede observar el prompt ha cambiado de `usuario@iaas-dsi:~$` a `[~()]$`.

No obstante para comprobar realmente que el prompt muestra lo que deseamos (la rama actual de trabajo cuando accedemos a un directorio asociado a un repositorio), tendremos que añadir la clave pública de la máquina virtual en la configuración de las claves de nuestra cuenta de GitHub, así nos sera más facil trabajar con repositorios remotos y también podremos clonar el repositorio para hacer la prueba.

Seguramente no tendremos creada la clave pública así que tendremos que crearla como hicimos anteriormente en la máquina local y la copiaremos cuando la mostremos con el comando:

```bash
  [~()]$cat ~/.ssh/id_rsa.pub
```

Una vez copiada, accederemos a la configuración de su cuenta de GitHub (*account settings*), y en la sección SSH and GPG keys, pulsaremos sobre el botón *New SSH key*. En el formulario añadiremos un título para la clave y pegaremos la clave pública de nuestra máquina virtual en el campo de texto *key*. Por último, pulsaremos sobre el botón *Add SSH key*.

Después de hacer esto deberíamos poder clonar nuestro repositorio y una vez clonado entrariamos a él y nos tendría que poner en el prompt la rama actual (que en mi caso es *gh-page*):

```bash
  # Clonamos nuestro repositorio
  [~()]$git clone git@github.com:ULL-ESIT-INF-DSI-2021/prct01-iaas-vscode.git
  Clonando en 'prct01-iaas-vscode'...
  remote: Enumerating objects: 100, done.
  remote: Counting objects: 100% (100/100), done.
  remote: Compressing objects: 100% (79/79), done.
  remote: Total 100 (delta 32), reused 50 (delta 16), pack-reused 0
  Recibiendo objetos: 100% (100/100), 341.75 KiB | 1.63 MiB/s, listo.
  Resolviendo deltas: 100% (32/32), listo.
  
  # Comprobamos que se ha creado el directorio correspondiente
  [~()]$ls
  prct01-iaas-vscode
  
  # Entramos a dicho directorio el cual esta asociado con el repositorio
  [~()]$cd prct01-iaas-vscode/
  [~/prct01-iaas-vscode(gh-page)]$
```

##### 3. Instalar Node Version Manager (nmv), el gestor de versiones Node.js
[Node.js](https://nodejs.org/en/) es un entorno que permite la ejecución de código desarrollado en JavaScript y variantes, como por ejemplo, TypeScript. Para istalar su gestor de versiones ([Node Version Manager](https://github.com/nvm-sh/nvm), deberemos  ejecutar los siguientes comandos:

```bash
  # Lo instalamos
  [~()]$wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
  
  # Reiniciamos la terminal
  [~()]$exec bash -l
  
  # Comprobamos que se ha instalado correctamente
  [~()]$nvm --version
  0.37.2
```

Una vez hecho lo anterior, procederemos a instalar la versión más reciente de Node.js:

```bash
  [~()]$nvm install node
  Downloading and installing node v15.8.0...
  Downloading https://nodejs.org/dist/v15.8.0/node-v15.8.0-linux-x64.tar.xz...
  ####################################################################################################################################################################################### 100,0%
  Computing checksum with sha256sum
  Checksums matched!
  Now using node v15.8.0 (npm v7.5.1)
  Creating default alias: default -> node (-> v15.8.0)
  [~()]$node --version
  v15.8.0
  [~()]$npm --version
  7.5.1
```

##### 4. Si se quisiera instalar una versión concreta de Node.js
Para instalar una versión mas concreta de Node.js, podemos hacer lo siguiente:

```bash
  # Lo instalamos
  [~()]$nvm install 12.0.0
  Downloading and installing node v12.0.0...
  Downloading https://nodejs.org/dist/v12.0.0/node-v12.0.0-linux-x64.tar.xz...
  ####################################################################################################################################################################################### 100,0%
  Computing checksum with sha256sum
  Checksums matched!
  Now using node v12.0.0 (npm v6.9.0)
  
  # Comprobamos que se instaló la versión que queriamos correctamente
  [~()]$node --version
  v12.0.0
  [~()]$npm --version
  6.9.0
```

Y si queremos cambiar entre versiones, podemos ejecutar los siguientes comandos:

```bash
  # Listamos las versiones que tenemos instaladas y con la '->' se nos muestra la versión que está en uso
  [~()]$nvm list
  ->      v12.0.0
          v15.8.0
  default -> node (-> v15.8.0)
  iojs -> N/A (default)
  unstable -> N/A (default)
  node -> stable (-> v15.8.0) (default)
  stable -> 15.8 (-> v15.8.0) (default)
  lts/* -> lts/fermium (-> N/A)
  lts/argon -> v4.9.1 (-> N/A)
  lts/boron -> v6.17.1 (-> N/A)
  lts/carbon -> v8.17.0 (-> N/A)
  lts/dubnium -> v10.23.2 (-> N/A)
  lts/erbium -> v12.20.1 (-> N/A)
  lts/fermium -> v14.15.4 (-> N/A)
  
  # Cambiamos la versión a usar
  [~()]$nvm use v15.8.0 
  Now using node v15.8.0 (npm v7.5.1)
  
  # Listamos la versión que estamos usando
  [~()]$node --version
  v15.8.0
  [~()]$npm --version
  7.5.1
```

#### Conclusiones
Como conclusión a la práctica, considero que git es super importante en la vida de un informático, a la vez que saber usar todo tipo de lenguaje de programación o control de versiones. Por lo tanto considero que una persona se tiene que formar en todos los sentidos de su profesión o trabajo.

Y me alegra que existan este tipo de herramientas que hacen más fáciles la realizaciones de los trabajos de una persona que se dedica a la informática.

#### Bibliografía
Nombre | Enlaces
-------|--------
Introducción a Markdown | https://guides.github.com/features/mastering-markdown/
Información sobre GitHub Pages | https://docs.github.com/en/github/working-with-github-pages
Sitio web de Jekyll | https://jekyllrb.com/
GutHub Learning Lab | https://lab.github.com/
Curso de GitHub Pages | https://lab.github.com/githubtraining/github-pages
Curso 'Communicating using Markdown' | https://lab.github.com/githubtraining/communicating-using-markdown
Documentación de configuración de la VPN de la ULL | https://www.ull.es/servicios/stic/2020/12/01/servicio-de-vpn-de-la-ull/
Servicio IaaS de la ULL | https://iaas.ull.es/
Libro "Pro Git" de Scott Chachon y Ben Straub | https://git-scm.com/book/es/v2
Intrucciones para configurar git por primera vez | https://git-scm.com/book/es/v2/Inicio---Sobre-el-Control-de-Versiones-Configurando-Git-por-primera-vez
Script git prompt | https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh
Curso de introducción a GitHub | https://lab.github.com/githubtraining/introduction-to-github
Curso 'First Week on GitHub' | https://lab.github.com/githubtraining/first-week-on-github
Node Version Manager (nvm) | https://github.com/nvm-sh/nvm
Node.js | https://nodejs.org/en/
Node Package Manager (npm) | https://www.npmjs.com/



