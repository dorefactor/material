# Comandos varios para la aplicación todo

## Maven
Ejecuta tests, y crear ejecutable
`mvn clean package`

Compila la aplicación
`mvn clean compile`

Ejecuta pruebas unitarias
`mvn clean test`

Ejecutar pruebas de integración
`mvn clean verify`


## Base de datos
La Todo-app necesita de un usuario relacionado a la base de datos,
Se puede ejecutar con un cliente gráfico de mysql(DBeaver) o desde consola

```
CREATE USER IF NOT EXISTS 'todo'@'localhost'
IDENTIFIED BY 'todo123';

GRANT ALL PRIVILEGES ON todo.* TO 'todo'@'localhost'
IDENTIFIED BY 'todo123';
 
CREATE USER IF NOT EXISTS 'todo'@'%'
IDENTIFIED BY 'todo123';

GRANT ALL PRIVILEGES ON todo.* TO 'todo'@'%'
IDENTIFIED BY 'todo123';

 flush PRIVILEGES;
 ```

## Docker
Para poder utilizar base datos o containers de la aplicación debemos tener conocimientos 
de los comandos de docker

Para una mini guía ver:  [fagoner/devs_502_example](https://github.com/fagoner/devs_502_example)

#### docker cli
Ver las imágenes de docker en el servicio
`docker images`

Ver los containers en ejecución
`docker ps -a`

Ejecutar un container basado en una imagen
`docker run hello-world`

Ejecutar nginx, exponiendo un puerto, identificando el container con un nombre en especifíco, y borrando el container luego de ejecutarlo
`docker run --name nginx_example -p 8080:80 nginx:latest`

Detener un container
`docker stop <nombre_contenedor>`
`docker stop <identificador>`

#### docker-compose
Ejecutar un archivo de docker-compose 
`docker-compose up -d`
`docker-compose up -f docker-compose-filename.yml up`

Detener docker-compose
`docker-compose stop`

Borrar los contenedores de docker-compose
`docker-compose rm`

Liberar recurso de docker-compose
`docker-compose down`

Ver logs de un contenedor
`docker logs <identificador>`
`docker logs <nombre_container>`

Ver los contenedores de las imágenes de docker-compose
`docker-compose ps`