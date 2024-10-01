# Caddy AI2

## Proyecto

Este es el modelo antiguo del RBCar de Robotnik. Este fue adquirido ya hace unos años por el AI2 para los proyectos IDEMOV, IDECONA [IDECONA AI2](https://idecona.ai2.upv.es/index.htm). El grupo de trabajo [CO3 UPV](https://github.com/CO3-UPV) ahora ha heredado este coche. Internamente hemos decidido llamarle Caddy AI2.

![Rbcar AI2](img/rbcar-ai2.jpeg)

Como venía diciendo, este prototipo se hereda de un proyecto anterior: [IDECONA AI2](https://idecona.ai2.upv.es/article/proyectos-final-de-carrera-1.html), os recomiendo ver el material [Multimedia - IDECONA AI2](https://idecona.ai2.upv.es/videos-1.html). 

El coche tiene una compleja y no demasiado documentada información sobre como es el cableado, esquemas eléctricos, etc... A nivel software funciona actualmente con una versión obsoleta de ROS 1 Indigo Igloo con Ubuntu 14 (sin parche del tiempo de real - PREEMPT RT).

La intención es actualizar el coche adaptando las piezas de hardware y software necesarias para tener un coche con la versión actual de ROS 2 Humble y Ubuntu 22 (es posible que con PREEMPT RT).

### Partimos de la base de software

Tenemos los repositorios de código de Robotnik y otros extraídos de un backup de código del workspace del robot:

- <https://github.com/racarla96/ros1_caddy_ai2_rbcar_sim>
- <https://github.com/racarla96/ros1_caddy_ai2_rbcar_common>
- <https://github.com/racarla96/ros1_caddy_ai2_robotnik_sensors>
- <https://github.com/racarla96/ros1_caddy_ai2_rbcar_robot> (rescatado del coche, muy importante)

De estos paquetes, se han eliminado las ramas de ROS posteriores a indigo-devel, porque corresponden al nuevo modelo de Robotnik, conservando sólo la rama de indigo-devel.