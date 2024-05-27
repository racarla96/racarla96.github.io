# LEGO EV3 con ROS 1 Noetic para Debian Buster de EV3Dev

## Proceso de uso de la imagen

NOTA: La primera vez que iniciemos el brick, nos pedirá que presionemos el botón del centro para continuar, puede ser se reinicie solo o tengamos que quitarle la batería.

Aquí puedes descargar la imagen ya preparada para quemar en la SD: 
- https://mega.nz/file/VW8FFTYB#5yEJ2ZTeHwKv5_rbyt10Wcyl_gSJvv8q2AhG3_GTggQ


Luego, para poder utilizar ROS debemos cambiar el ROS_MASTER_URI por la dirección apropiada donde se este ejecutando el ROS Core.

Para programar en C++ o Python tenemos la siguiente documentación: https://ev3dev-lang.readthedocs.io/en/latest/

Establecer el setup de Visual Studio Code:
[Youtube - Setting up VS Code EV3 Python programming by Nigel Ward](https://www.youtube.com/watch?v=TNXqizQTZhs)

## Proceso de construcción de la imagen

El proceso ha tenido una dificultad media alta debido a la obsolescencia del equipo y a la falta de información, pero la justa y necesaria para componer el puzzle. 

El objetivo para resolver el puzzle es instalar ROS 1 en el LEGO EV3. Haciendo una primera busqueda por internet, encontramos: https://wiki.ros.org/Robots/EV3, y encontramos dos opciones: *There is a Debian linux variant: ev3dev and a Yocto Linux variant under development.*; una imagen con Debian realizada por EV3Dev y otra imagen de Yocto Linux. 

Al haber trabajado previamente con LEGO, la imagen de EV3Dev, ya me es conocida, y consiste en grabar una imagen (un fichero) en una SD, y la ponemos en el robot carga el sistema y ya podemos desarrollar aplicaciones en Python, MicroPython y C++. [EV3Dev - Documentation - Programming Languages](https://www.ev3dev.org/docs/programming-languages/) 

Además, la página de ROS nos comenta que existe una herramienta para crear las imágenes: *Brickstrap is a tool for creating bootable image files for embedded systems using Debian Linux.*; llamada Brickstrap, esta en su última versión genera la imagen a partir de una imagen de Docker, la única pega es que solo funciona en Linux. 

¿Y porque no hago una maquina virtual en mi Windows e instalo algún Linux y luego Docker? Esto no es posible de momento por el tipo de virtualización de Windows. Así pues, para generar la imagen necesitamos tener acceso a una maquina con Linux, o instalarlo en nuestro PC, si nuestra intención es generar una nueva imagen. En cambio, **si solo queremos compilar un ejemplo (código) en nuestro Windows con Docker Desktop, y enviarlo a nuestro brick de LEGO, no habrá problema**, de hecho es lo sugerido por EV3Dev. [Using Docker to Cross-Compile](https://www.ev3dev.org/docs/tutorials/using-docker-to-cross-compile/)

Por otra parte, tenemos que la versión Debian 9 Strecth, es la última versión compilada en su página web por el grupo EV3Dev, esta versión de Debian no tiene compatibilidad directa con ROS, aunque da igual, porque hay que realizar la compilación desde cero. Aunque por otra parte, en su repositorio, tenemos la versión Debian 10 Buster y Debian 11 Bullseye: https://github.com/ev3dev/docker-library, nos decantamos por Debian 10 Buster, porque es la versión compatible con ROS 1 Noetic, y aunque tengamos que compilarlo, habrá cierta coherencia con otras instalaciones y versiones de paquetes. Además, en un PC de sobremesa también instalaremos Debian 10 Buster, y así tenemos el mismo OS tanto en el LEGO como en el PC.

<img src="img\ros_install_platform.png" style="width:auto; height:200px; display: block; margin-left: auto; margin-right: auto;">

Asumiendo que ya tienes una instalación de Linux, por ejemplo Debian 10 Buster para AMD64 con docker instalado, para poder usar en un futuro Brickstrap, el **procedimiento** por encima sería, empezar por aquí [github - ev3dev - docker library](https://github.com/ev3dev/docker-library) hasta llegar aquí, a este paso *docker run --rm -it ev3 su -l robot*, aquí evitamos este comando *docker run --rm -it ev3* para poder ejecutar comando como usuario root. Hacemos los comandos para realizar la instalación siguiendo algunos de los pasos [github - moriarty - brickstrap-build](https://github.com/moriarty/ros-ev3/blob/master/brickstrap-build-status.md) y [ROS 1 Noetic - Installing from source](https://wiki.ros.org/noetic/Installation/Source) adaptándolo a la versión de ROS 1 Noetic, si quieres más info, mirar el TODO: ENLACE, pero lo que hacemos es ir anotando los comandos, puede ser que tengas que volver a empezar varias veces. Una vez, hayamos terminado con el Docker, **no lo cierres**, desde otra terminal hacemos un commit y hacemos el proceso para pasarlo a una SD, si funciona y nos gusta, podemos quedarnos en este paso haciendo un commit, busca en Internet. Aunque podemos hacerlo más elegante, pasándo los comandos a un fichero Dockerfile y subiendolo a un repositorio como DockerHub para que la comunidad se beneficie de nuestro proyecto.

En resumen, hemos generado una receta de Docker a partir de la imagen de [ev3dev/ev3dev-buster-ev3-generic](https://github.com/ev3dev/docker-library) y siguiendo los pasos de instalación, hemos instalado ROS1 1 Noetic desde el source code y empaquetado en una nueva imagen resolviendo las problemáticas que aparecen con las depedencias. 

Para descargar la imagen de Docker, aquí la tienes:
https://hub.docker.com/repository/docker/racarla96/lego-ev3dev-debian-buster-ros-noetic/general

#### Enlace de referencia
- https://github.com/moriarty/ros-ev3 -> https://github.com/moriarty/ros-ev3/blob/master/brickstrap-build-status.md
- https://gcore.com/learning/how-to-transfer-move-a-docker-image-to-another-system/
- https://github.com/ev3dev/docker-library
- https://github.com/ev3dev/brickstrap
- https://www.ev3dev.org/
- https://wiki.ros.org/noetic/Installation
- https://wiki.ros.org/Robots/EV3