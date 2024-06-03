# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la se obtiene desde la documentación
![Volúmenes](imagenes/volumen-host.PNG)

``` docker run -d -p 80:80 --name mi_contenedor -v C:\Users\pilco\Desktop\nginx\html:/usr/share/nginx/html nginx:alpine ```

### ¿Qué sucede al ingresar al servidor de nginx?

Tengo un error llamado "403 Forbidden"

### ¿Qué pasa con el archivo index.html del contenedor?

El archivo index.html del contenedor es el archivo principal que se sirve cuando accedes al servidor de Nginx. Si se ha modificado o reemplazado con un nuevo contenido, al acceder al servidor de Nginx verás el contenido del nuevo index.html.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?

Después de descargar un template gratuito desde html5up.net y descomprimirlo dentro de nginx/html, al ingresar al servidor de Nginx se verá el contenido del nuevo template, ya que el servidor ahora estará sirviendo los archivos del template descargado en lugar del archivo index.html original.

### Eliminar el contenedor

``` docker rm mi_contenedor ```


### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

Al crear nuevamente el mismo contenedor con volumen de tipo host a los mismos directorios definidos anteriormente, el contenido de los directorios host se volverá a montar en el contenedor. Esto significa que si se ha realizado cambios en los archivos en los directorios host, esos cambios se reflejarán en el contenedor. Por ejemplo, si has modificado el contenido del template descargado, esos cambios se verán reflejados al acceder al servidor de Nginx.

### ¿Qué hace el comando pwd?

El comando pwd (print working directory) imprime el nombre del directorio de trabajo actual en la consola. En un contexto de Docker, se usa para obtener la ruta absoluta del directorio actual en el host, que luego puede ser utilizada en comandos de Docker, por ejemplo, para montar un volumen tipo host.

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

