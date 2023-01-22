# Ambiente de desarrollo para LARAVEL 9 con DOCKER

A continuación se detallan los pasos para tener un ambiente de desarrollo para LARAVEL.

Se parte de la consideración que este ambiente está montado sobre docker, de esta forma no es requerido tener instalado PHP en el equipo.


## Instalación

**Paso 1 - Generación de Imagen Base PHP**

Generar la imagen base de PHP, con el comando:

```shell script
docker build ./docker/php/build -t php-dev:8-alpine
```

**Paso 2 - Arrancar el ambiente de desarrollo**

Se debe ejecutar las imágenes del ambiente.

```shell script
docker-compose up -d
```

### Paso Opcional - Versión reciente de LARAVEL

Si requieres utilizar una versión más reciente de LARAVEL que la proporcionada en este proyecto puedes eliminar la carpeta src y descargar una versión actualizada.

Asegurate de realizar este paso cuando éstas iniciando el proyecto, porque si no corres el riesgo de perder todos los cambios desarrollados sobre la versión de LARAVEL que trae este repositorio.

Recuerda verificar que la versión de LARAVEL puede ejecutarse en PHP 8.

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

En el transcurso del desarrollo siempre se requiere ejecutar el CLI de **artisan** , como no tenemos ninguna versión de PHP instalada en nuestro equipo, necesitaremos ejecutar **artisan** en el contenedor de desarrollo.

Para simplificar esta tarea se ha creado el script bash artisan , basta con darle el permiso de ejecución de la siguiente forma:

```shell script
chmod +x artisan
````

La forma de utilizarlo es tal cual lo harías en tu equipo local, por ejemplo:


```shell script
./artisan help
```


## Como hacer debug 

Realmente es importante poder desarrollar LARAVEL desde un contenedor de docker, pero un ambiente de desarrollo no estaria completo sin la capacidad de hacer debug.

Por esta razón se implementa XDEBUG, a continuacion como utilizarlo.

**VSCODE**

Instalar la siguiente extension:  

[PHP Debug](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug)

![PHP Debug](/.images/vcode_debug01.png)

Segun algunos articulos leidos, recomiendan que se utilice en el navegador la extension llamada [Xdebug Helper](https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc) ; pero a mi no me ha hecho falta. Asi que si te llegase a fallar, instalala.  

![Xdebug Helper](/.images/vcode_debug02.png)  

Empieza a hacer debug

![Inicia a escuchar el debug](/.images/vcode_debug03.png)  



**PHPStorm**

Para PHPStorm no se requiere instalar extensiones adicionales, unicamente seguir los siguientes pasos:

Configurar Debug.

Ingresar a Setting > PHP > Debug

![Configuracion de Debug](/.images/phpstorm_debug01.png)


Configurar el mapeo de carpetas del servidor llamador **ace3**  

![Mapeo de Carpetas locales](/.images/phpstorm_debug02.png)  

Empieza a escuchar el puerto debug.  

![Escuchar el puerto Debug](/.images/phpstorm_debug03.png)  




## Versiones implementadas

PHP: **8.2.1**  
Laravel: **v9.48.0**  
MySQL: **8.0-oracle** 



## Documentacion consultada.   


[Debugging Laravel with Xdebug3 and Docker Compose](https://igniz87.medium.com/debugging-laravel-with-xdebug3-and-docker-compose-187a66981869)  

[Como crear un entorno de desarrollo local Laravel Docker](https://youtu.be/ziNXj9CrCQM)