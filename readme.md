# Ambiente de desarrollo para LARAVEL 9 con DOCKER

A continuacion se detallan los pasos para tener un ambiente de desarrollo para LARAVEL. 

Se parte de la consideracion que este ambiente esta montado sobre docker, de esta forma no es requerido tener instalado PHP en el equipo.


## Instalacion

**Paso 1 - Generacion de Imagen Base PHP**

Generar la imagen base de PHP, con el comando:

```shell script
docker build ./docker/php/build -t php-dev:8-alpine
```

**Paso 2 - Arrancar el ambiente de desarrollo**

Se debe ejecutar las imagenes del ambiente.

```shell script
docker-compose up -d
```

### Paso Opcional - Version reciente de LARAVEL

Si requieres utilizar una version mas reciente de LARAVEL que la proporcionada en este proyecto puedes eliminar la carpeta src y descargar una version actualizada.

Asegurate de realizar este paso cuando estes iniciando el proyecto, porque sino corres el riesgo de perder todos los cambios desarrollados sobre la version de LARAVEL que trae este repositorio.

Recuerda verificar que la version de LARAVEL puede ejecutarse en PHP 8.

Ejecutar en la consola: 

```shell script
rm -r src && mkdir src
```

```shell script
docker run --rm --interactive --tty \ 
       --volume $PWD/src:/app composer create-project laravel/laravel .
```

## Trabajando con artisan dentro del contenedor.

**Usuarios Linux y MacOS**

En el transcurso del desarrollo siempre se requiere ejecutar el CLI de **artisan** , como no tenemos ninguna version de PHP instalada en nuestro equipo, necesitaremos ejecutar **artisan** en el contenedor de desarrollo.

Para simplificar esta tarea se ha creado el script bash **artisan** , basta con darle el permiso de ejecucion de la siguiente forma:

```shell script
chmod +x artisan
````

La forma de utilizarlo es tal cual lo harias en tu equipo local, por ejemplo:


```shell script
./artisan help
```


## Versiones implementadas

PHP: **8.2.1**  
Laravel: **v9.48.0**  
MySQL: **8.0-oracle** 

