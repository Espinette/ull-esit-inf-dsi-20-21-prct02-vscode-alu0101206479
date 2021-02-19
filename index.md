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

##### 4. Abrir el directorio `~/hello-world` en VSCode

Posteriormente, iremos al menú `File`, haremos clic en la opción `Open Folder...` y seleccionaremos `hello-world` en el menú desplegable. Esto nos abrirá una nueva ventana de VSCode y en el explorador podremos ver el contenido del directorio `~/hello-world`.

##### 5. Añadir el directorio `~/hello-world` a un espacio de trabajo (workspace)

También vamos a añadir el directorio a un espacio de trabajo. Para esto, iremos al menú `File` y seleccionaremos la opción `Add Folder to Workspace...`. Seleccionaremos hello-world en el menú desplegable, se creará un nuevo espacio de trabajo y se añadirá el directorio al mismo si no teniamos ningún espacio de trabajo creado. Para guardar el espacio de trabajo iremos al menú `File` y seleccionaremos la opción `Save Workspace As...`, escribiremos un nombre de fichero y pulsaremos el botón `OK`.

##### 6. Crear el fichero `tsconfig.json` en el directorio `~/hello-world`

Ya acabado lo anterior, crearemos un nuevo fichero en el directorio `~/hello-world`, que se llamará 
`tsconfig.json`, en este se especificarán las opciones del compilador de TypeScript. Lo podemos crear usando la terminal de VSCode o su explorador, el fichero debe contener las siguientes líneas:

```bash
  [~/hello-world()]$cat tsconfig.json 
  {
    "compilerOptions": {
      "target": "ES2018",     # Queremos generar código compatible con uno de los últimos estandares de JavaScript
      "outDir": "./dist",     # El código de JavaScript producto de la compilación se almacenará en un directorio 'dist'
      "rootDir": "./src",     # El código fuente escrito en TypeScript se encontraá en el directorio src
      "module": "CommonJS"    # Estandar para cargar código desde ficheros independientes
    }
  }
```

##### 7. Añadimos un fichero con código de TypeScript

Para ello, primero que nada, debemos ejecutar los siguientes comandos en la terminal del VSCode:

```bash
  # Comprobamos que estamos en la carpeta '~/hello-world'
  [~/hello-world()]$pwd
  /home/usuario/hello-world
  
  # En dicha carpeta, creamos el directorio 'src'
  [~/hello-world()]$mkdir src
  
  # Nos movemos al directorio 'src'
  [~/hello-world()]$cd src
  
  # Creamos el fichero 'index.ts' vacío
  [~/hello-world/src()]$touch index.ts
  
  # Comprobamos que se ha creado correctamente
  [~/hello-world/src()]$ls
  index.ts
```

Ahora, abrimos el fichero index.ts con `vi index.ts` por ejemplo y añadimos las siguientes líneas:

```bash
  let myString: string = "Hola Mundo";
  console.log(myString);
```

##### 8. Compilar el código

Ya tenemos el fichero con el código de TypeScript, ahora lo ejecutamos con el siguiente comando:

```bash
  [~/hello-world()]$tsc
```

Hacer esto nos crea el directorio `dist` con el fichero `index.js` en su interior.

##### 9. Comprobar diferencias entre `./src/index.ts` y `./dist/index.js`

Para comprobar las diferencias entre los dos ficheros podemos usar el siguiente comando:

```bash
  [~/hello-world()]$diff src/index.ts dist/index.js
  1,2c1,2
  < let myString: string = "Hola Mundo"
  < console.log(myString)
  \ No hay ningún carácter de nueva línea al final del archivo
  ---
  > let myString = "Hola Mundo";
  > console.log(myString);
```

Si observamos la salida podemos ver que se diferencian en la declaración de la variable `myString` y en los `;`.

##### 10. Ejecutar el código de JavaScript generado a partir del código de TypeScript

Para finalizar vamos a ejecutar el archivo generado después de la compilación, el archivo `dist/index.js`:

```bash
  [~/hello-world()]$node dist/index.js
  Hola Mundo
```

#### Conclusiones
Como conclusión a la práctica, me ha parecido bastante interesante ya que el Visual Studio Code lo veo super importante para todo informático que programe. También veo muy útil e interesante el tema de las sesiones colaborativas ya que esto facilita mucho el trabajo de los desarrolladores de código.

Cabe destacar también que es la primera vez que tocaba TypeScript y JavaScript, me alegra bastante aprender a utilizarlos debido a que considero que son super importantes en el mundo de la informática.

Por último también he aprendido comandos que no sabía que existían, como el `diff` que te muestra las diferencias entre dos archivos.

#### Bibliografía

Nombre | Enlaces
-------|--------
Introducción a Markdown | https://guides.github.com/features/mastering-markdown/
Información sobre GitHub Pages | https://docs.github.com/en/github/working-with-github-pages
Sitio web de Jekyll | https://jekyllrb.com/
GutHub Learning Lab | https://lab.github.com/
Curso de GitHub Pages | https://lab.github.com/githubtraining/github-pages
Visual Studio Code | https://code.visualstudio.com/
Instalar Visual Studio Code | https://code.visualstudio.com/docs/setup/setup-overview
Tutorial VSCode sobre Additional Components | https://code.visualstudio.com/docs/setup/additional-components
Tutorial VSCode sobre User Interface | https://code.visualstudio.com/docs/getstarted/userinterface
Tutorial VSCode sobre Basic Editing | https://code.visualstudio.com/docs/editor/codebasics
Tutorial VSCode sobre Extension MarketPlace | https://code.visualstudio.com/docs/editor/extension-gallery
Tutorial VSCode sobre IntelliSense | https://code.visualstudio.com/docs/editor/intellisense
Tutorial VSCode sobre Code Navigation | https://code.visualstudio.com/docs/editor/editingevolved
Tutorial VSCode sobre Debugging | https://code.visualstudio.com/docs/editor/debugging
Tutorial VSCode sobre Version Control | https://code.visualstudio.com/docs/editor/versioncontrol
Tutorial VSCode sobre Working with GitHub | https://code.visualstudio.com/docs/editor/github
Tutorial VSCode sobre Integrated Terminal | https://code.visualstudio.com/docs/editor/integrated-terminal
Tutorial VSCode sobre Tasks | https://code.visualstudio.com/docs/editor/tasks
Tutorial VSCode sobre Snippets | https://code.visualstudio.com/docs/editor/userdefinedsnippets
Tutorial VSCode sobre Emmet | https://code.visualstudio.com/docs/editor/emmet
Tutorial VSCode sobre Command Line | https://code.visualstudio.com/docs/editor/command-line
Tutorial VSCode sobre  Multiroot Workspaces | https://code.visualstudio.com/docs/editor/multi-root-workspaces
Tutorial VSCode sobre  Accessibility | https://code.visualstudio.com/docs/editor/accessibility
Conectarnos desde VSCode a una máquina remota por SSH | https://code.visualstudio.com/docs/remote/ssh-tutorial
Informe de la práctica 1 de DSI | https://ull-esit-inf-dsi-2021.github.io/ull-esit-inf-dsi-20-21-prct01-iaas-alu0101206479/
Live Share Extension Pack | https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare-pack
Documentación de Visual Studio Live Share | https://docs.microsoft.com/en-us/visualstudio/liveshare/
Libro Essential TypeScript: From Beginner to Pro | https://learning.oreilly.com/library/view/essential-typescript-from/9781484249796/html/Part_1.xhtml

