# Ambiente de desarrollo para LARAVEL 8

A continuacion se detallan los pasos para tener un ambiente de desarrollo para LARAVEL. 

Se parte de la consideracion que este ambiente esta montado sobre docker, de esta forma no es requerido tener instalado PHP en el equipo.


## Versiones implementadas


PHP: 8.2.1

Laravel: v9.48.0

MySQL: 8.0-oracle


## Instalacion

**Generacion de Imagen Base PHP**

Generar la imagen base de PHP, con el comando:

```bash

docker build ./docker/php/build -t php-dev:8-alpine

```

### Version reciente de LARAVEL

Si desea tener una version reciente de LARAVEL puede eliminar la carpeta src y descargar una version actualizada.

```bash
rm -r src && mkdir src

docker run --rm --interactive --tty --volume $PWD/src:/app composer create-project laravel/laravel .

```


**Arrancar el ambiente de desarrollo**

Se debe ejecutar las imagenes del ambiente.

```bash

docker-compose up -d

```