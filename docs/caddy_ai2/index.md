# Caddy AI2

El proyecto he decidido internamente llamarle Caddy AI2, me gusta el nombre.

En este prototipo se hereda de un proyecto anterior [IDECONA AI2](https://idecona.ai2.upv.es/article/proyectos-final-de-carrera-1.html), os recomiendo ver el material [Multimedia - IDECONA AI2](https://idecona.ai2.upv.es/videos-1.html). 

El coche tiene una compleja y no demasiado documentada información sobre como es el cableado, esquema eléctrico, incluso puede falte alguna pieza. A nivel software funciona actualmente con una versión obsoleta de ROS 1 Indigo Igloo con Ubuntu 14 (sin parche del tiempo de real - PREEMPT RT).

La intención es actualizar el coche adaptando las piezas de hardware y software necesarias para tener un coche con la versión actual de ROS 2 Humble y Ubuntu 22 con PREEMPT RT.

### Partimos de la base de software:

Por una parte, tenemos un backup de código del workspace del robot, incluyen otros paquetes del AI2, etc:
- FALTA ENLACE

Por otra parte, tenemos los repositorios de código de Robotnik:
- https://github.com/CO3-UPV/rbcar_sim
- https://github.com/CO3-UPV/rbcar_common
- https://github.com/CO3-UPV/robotnik_sensors
- https://github.com/CO3-UPV/rbcar_robot (rescatado del coche, esta es realmente importante)

De estos paquetes, se han eliminado las ramas de ROS posteriores a indigo-devel, porque corresponden al nuevo modelo de Robotnik, conservando la rama de indigo-devel.




Cambios en el chasis:
- Se han añadido tres pasamuros a la caja para pasar cableado a su interior de forma sencilla: [Customizable threaded grommet by makmonty - Thingiverse](https://www.thingiverse.com/thing:4372453)