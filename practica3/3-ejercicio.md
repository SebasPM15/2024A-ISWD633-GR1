## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp

``` docker network create net-wp ```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.

# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es "/var/lib/mysql"
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?

La carpeta db del host inicialmente estará vacía.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

``` docker run -d --name mysql-container --network net-wp -v C:\Users\pilco\Desktop\ejercicio3\db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root_password -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wordpress_user -e MYSQL_PASSWORD=wordpress_password mysql:8 ```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

La carpeta db del host ahora contendrá los archivos y directorios relacionados con la base de datos MySQL que se está ejecutando en el contenedor.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (b) es "/var/www/html"
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

``` docker run -d --name wordpress-container --network net-wp -v C:\Users\pilco\Desktop\ejercicio3\www:/var/www/html -e WORDPRESS_DB_HOST=mysql-container -e WORDPRESS_DB_USER=wordpress_user -e WORDPRESS_DB_PASSWORD=wordpress_password -e WORDPRESS_DB_NAME=wordpress -p 8080:80 wordpress ```


### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al eliminar el contenedor y crearlo nuevamente, los cambios que hayas realizado en WordPress se perderán, ya que los datos se almacenan dentro del contenedor. Sin embargo, los datos de la base de datos MySQL persistirán debido al volumen montado. Por lo tanto, al recrear el contenedor de WordPress, podrás acceder al sitio nuevamente, pero es posible que necesites volver a configurar o reinstalar cualquier cambio o personalización que hayas realizado anteriormente.


