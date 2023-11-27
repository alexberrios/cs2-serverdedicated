# Crear servidor de CS2 #
## 1. Tener ubuntu instalado ##
## 2. Mantener siempre actualizado ubuntu ##
```
    sudo apt-get update
    sudo apt-get upgrade
```
## 3. Instalar ##
```
    sudo apt-get install lib32gcc1
``` 
es esencial para que el servidor de cs2 se ejecute.

## 4. Comandos basicos de linux ##
```
    Para movernos entre carpetas se utiliza cd
    cd /la/ruta/donde/voy : hacia adelante
    cd .. : hacia atras
    ./ : para ejecutar algo en la carpeta donde estoy el "." le indica a linux "aqui"
    ls -lh : lista el contenido de la carpeta de forma ordenada y con valores legibles por humanos
    sudo : para ejecutar comandos en modo admin
    ~ : marca el home de sesion de usuario
```
## 5. Descargar e instalar archivos de CS2 Server ##
## 5.1 crear usuario y carpeta Steam ##
El primer comando crea un nuevo usuario para ejecutar SteamCMD de forma segura
el segundo te logea con ese usuario
el tercer comando crea la carpeta **Steam** en el home del usuario **steam** y con cd te deja ubicado en la carpeta
```
    sudo useradd -m steam = 
    su - steam
    mkdir ~/Steam && cd ~/Steam
    mkdir server/cs2-ds
```
## 5.2 Descargar e instalar SteamCMD ##
El primer comando descargar y extare SteamCMD
El segundo comando instala un administrador sevidor de CS2
El ejecuta **steamcmd.sh** esto instala steamCMD
```
    curl -sqL "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz" | tar zxvf -
    sudo apt-get install tmux screen -y;
    ./steamcmd.sh
```

## 5.3 Descargar e instalar CS2 ##
Si ves que el prompt ```Steam>``` puedes comenzar la descarga de los archivos de CS2 Server 
El primer comando indica la ruta para instalar cs2 force_install_dir
IMPORTANTE ```/full/path/to/cs2-ds/``` debe ser reemplazado con la ruta donde vamos a dejar cs2, para en este caso creamos ```~/Steam/server/cs2-ds/```
El segundo comando es para iniciar sesion con una cuenta de steam
El tercer comando instala los archivos de Counter-Strike 2 dedicated server y verifica la integridad
una vez finalizado el comando anterior se puede cerrar steamCMD con ```quit```
```
    force_install_dir /full/path/to/cs2-ds/
    login <username> <password>
    app_update 730 validate
    quit
```
## 6. Configurar el servidor
Luego de descargar e instalar los archivos del servidor dedicado el siguiente paso es customizar las opciones del tu servidor.
El primer comando no lleva a la ruta donde esta instalado el servidor de CS2
una vez ahi ejecutar el segundo comando ```ls -l``` para verificar que esten los archivos y exista **server.cfg**.
Modificar el archivo **server.cfg** 
Para pegar texto en nano, puedes usar el atajo de teclado Ctrl+Shift+V o Ctrl+Insert dependiendo de tu sistema operativo.
Para guardar los cambios en nano, usa el atajo de teclado Ctrl+O, luego presiona Enter para confirmar el nombre del archivo.

Para cerrar nano, usa el atajo de teclado Ctrl+X. Si has realizado cambios sin guardar, nano te preguntará si quieres guardarlos antes de salir.

```
    cd ~/Steam/server/cs2-ds/
    ls -l
    nano server.cfg
```
## 7. Iniciar servidor de CS2 ##
Aca nos vamos a dirigir a la carpeta donde se descargo cs2 server
y vamos a ejecutar cs2 para iniciar el servidor
```
    cd ~/Steam/server/cs2-ds/
    ./cs2 -dedicated +map de_dust2
```
si deseas puedes cutomizar el tipo de juego
Competitive

```./cs2 -dedicated +map de_dust2 +game_mode 1 +game_type 0```
Wingman

```./cs2 -dedicated +map de_dust2 +game_mode 2 +game_type 0```
Casual

```./cs2 -dedicated +map de_dust2 +game_mode 0 +game_type 0```
Deathmatch

```./cs2 -dedicated +map de_dust2 +game_mode 2 +game_type 1```
Custom

```./cs2 -dedicated +map de_dust2 +game_mode 0 +game_type 3```

## 8. Monitorear y manejar tu servidor ##
Despues de iniciar el servidor vamos a poder ejecutar comandos como kick, status, changelevel
```
    sm_restart = reinicia el servidor
    changelevel
    kick
    banid
    status
    log on = habilita que se guarden logs de servidor
    maxplayers 

```
