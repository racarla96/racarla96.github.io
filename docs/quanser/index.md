# Adaptación de las maquetas de Quanser para utilizarlas con Arduino o ESP32 y Simulink

*El experimento 3 DOF Hover proporciona un banco de pruebas económico para comprender y desarrollar leyes de control para la dinámica de vuelo y el control de vehículos con despegue vertical.* [1]

*El módulo de péndulo giratorio invertido se conecta a la unidad base del servo giratorio, ampliando los temas de mecatrónica y controles que se pueden enseñar. El módulo de péndulo desafía a los estudiantes no solo a modelar y controlar un péndulo, sino también a aprender sobre sistemas de control híbridos ajustando un sistema de control oscilante. Además de enseñar conceptos de control intermedio, el péndulo rotatorio invertido se puede utilizar para la investigación en diversas áreas, incluido el control difuso.* [2]

<img src="img\three_dof_hover_quanser.jpg" alt="three_dof_hover_quanser.jpg" height="200px"><img src="img\rotary_inverted_pendulum_quanser.jpg" alt="rotary_inverted_pendulum_quanser.jpg" height="200px">

Ambas maquetas están compuestas por motores y encoders que nos permiten obtener la posición a través de encoders de cuadratura y actuar a través de los motores de corriente continua sobre la maqueta.

## Adaptar los encoders

Para poder leer el encoder, una opción, es acoplarnos al conector que utilizaba Quanser, un conector DIN 5 pines:

<img src="img\conector-din-5-pines-macho.jpg" alt="conector-din-5-pines-macho.jpg" height="200px">

Por tanto, nuestro objetivo es contruir un cable compatible con el encoder que podamos leer con Arduino.

Es por ello que primero miraremos que clase de encoders monta. Los encoders que utilizan las maquetas son los HEDS-9100 que requieren seguir el siguiente esquema:

<img src="img\encoder_heds_9100_schematic.png" alt="encoder_heds_9100_schematic.png" height="200px">

Este esquema es útil cuando el Arduino puede leer señales a 5V. Como vemos utilizaremos unas resistencias entorno a las 3 KΩ. Pero si tenemos un Arduino que funciona a 3.3 V tenemos que realizar una pequeña modificación, y es poner la resistencia de pull-up a 3.3 V:

<img src="img\schematic_3_3_V.png" alt="schematic_3_3_V.png" height="200px">

Para montar este esquema con los cables originales de quanser tenemos que tener precaución porque el color del cable (primera imagen) no coincide con los colores que se ven del siguiente conector (las demás imagenes) (en estos conectores el canal index no está conectado):

<img src="img\cable_y_pcb_in_progress.jpg" alt="cable_y_pcb_in_progress.png" height="200px">

<img src="img\conector_din_5_vista_1.jpg" alt="conector_din_5_vista_1.png" height="200px"><img src="img\conector_din_5_vista_2.jpg" alt="conector_din_5_vista_2.png" height="200px">
<img src="img\conector_encoder.jpg" alt="conector_encoder.png" height="200px">

Este cable sigue el siguiente patrón, para el cable que he construido, he seguido más o menos el mismo patrón de color que el conector externo, de ahí el color entre paréntesis:

<img src="img\tabla_conexión.png" alt="tabla_conexión.png" height="200px">
<img src="img\cable_zoom.jpg" alt="cable_zoom.png" height="200px">

<img src="img\salida_conector.jpg" alt="salida_conector.png" height="200px">

Si por otra parte compramos los conectores de internet y queremos contruir nuestro propio cable tenemos el siguiente esquema, añadiendo la parte del esquematico con las resistencias de pull-up:

<img src="img\conector_din_5_vista_detallada.jpg" alt="conector_din_5_vista_detallada.png" height="200px">


### Más sobre encoder de cuadratura
- [https://makeatronics.blogspot.com/2013/02/efficiently-reading-quadrature-with.html](https://makeatronics.blogspot.com/2013/02/efficiently-reading-quadrature-with.html)
- [https://electronics.stackexchange.com/questions/360637/quadrature-encoder-most-efficient-software-implementation](https://electronics.stackexchange.com/questions/360637/quadrature-encoder-most-efficient-software-implementation)

## Enlaces de referencia
- [1] https://www.quanser.com/products/3-dof-hover/
- [2] https://www.quanser.com/products/rotary-inverted-pendulum/