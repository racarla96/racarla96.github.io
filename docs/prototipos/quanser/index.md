# Adaptación de las maquetas de Quanser para utilizarlas con microcontrolador como Arduino, STM32, ESP32 o incluso con Linux con un Raspberry Pi, LattePanda Alpha, BeagleBone, etc...

*El experimento 3 DOF Hover proporciona un banco de pruebas económico para comprender y desarrollar leyes de control para la dinámica de vuelo y el control de vehículos con despegue vertical.* [1]

*El módulo de péndulo giratorio invertido se conecta a la unidad base del servo giratorio, ampliando los temas de mecatrónica y controles que se pueden enseñar. El módulo de péndulo desafía a los estudiantes no solo a modelar y controlar un péndulo, sino también a aprender sobre sistemas de control híbridos ajustando un sistema de control oscilante. Además de enseñar conceptos de control intermedio, el péndulo rotatorio invertido se puede utilizar para la investigación en diversas áreas, incluido el control difuso.* [2]

<img src="img\three_dof_hover_quanser.jpg" alt="three_dof_hover_quanser.jpg" style="width:auto;height:200px;">
<img src="img\rotary_inverted_pendulum_quanser.jpg" alt="rotary_inverted_pendulum_quanser.jpg" style="width:auto;height:200px;">

Ambas maquetas están compuestas por encoders de cuadratura y motores de corriente continua, estos nos permiten obtener la posición y actuar sobre la maqueta.

## Adaptar los encoders

Para poder leer el encoder, una opción, es acoplarnos al conector que utilizaba Quanser, un conector DIN 5 pines:

<img src="img\conector-din-5-pines-macho.jpg" alt="conector-din-5-pines-macho.jpg" style="width:auto;height:200px;">

Por tanto, nuestro objetivo es contruir un cable compatible con el encoder que podamos leer con Arduino.

Es por ello que primero miraremos que clase de encoders monta. Los encoders que utilizan las maquetas son los HEDS-9100 que requieren seguir el siguiente esquema:

<img src="img\encoder_heds_9100_schematic.png" alt="encoder_heds_9100_schematic.png" style="width:auto;height:200px;">

Este esquema es útil cuando el Arduino puede leer señales a 5V. Como vemos utilizaremos unas resistencias entorno a las 3 KΩ. Pero si tenemos un Arduino que funciona a 3.3 V tenemos que realizar una pequeña modificación, y es poner la resistencia de pull-up a 3.3 V:

<img src="img\schematic_3_3_V.png" alt="schematic_3_3_V.png" style="width:auto;height:200px;">

Para montar este esquema con los cables originales de quanser tenemos que tener precaución porque el color del cable (primera imagen) no coincide con los colores que se ven del siguiente conector (las demás imagenes) (en estos conectores el canal index no está conectado):

<img src="img\cable_y_pcb_in_progress.jpg" alt="cable_y_pcb_in_progress.png" style="width:auto;height:200px;">
<img src="img\conector_din_5_vista_1.jpg" alt="conector_din_5_vista_1.png" style="width:auto;height:200px;">
<img src="img\conector_din_5_vista_2.jpg" alt="conector_din_5_vista_2.png" style="width:auto;height:200px;">
<img src="img\conector_encoder.jpg" alt="conector_encoder.png" style="width:auto;height:200px;">

Este cable sigue el siguiente patrón, para el cable que he construido, he seguido más o menos el mismo patrón de color que el conector externo, de ahí el color entre paréntesis:

<img src="img\tabla_conexión.png" alt="tabla_conexión.png" style="width:auto;height:200px;">
<img src="img\cable_zoom.jpg" alt="cable_zoom.jpg" style="width:auto;height:200px;">
<img src="img\salida_conector.jpg" alt="salida_conector.jpg" style="width:auto;height:200px;">

Si por otra parte compramos los conectores de internet y queremos contruir nuestro propio cable tenemos el siguiente esquema, añadiendo la parte del esquematico con las resistencias de pull-up:

<img src="img\conector_din_5_vista_detallada.jpg" alt="conector_din_5_vista_detallada.jpg" style="width:auto;height:200px;">

## Adaptar los motores

Para la adaptación de los motores el proceso es mucho más sencillo, ya que sólo debemos tener acceso a la información del datasheet del motor o en su defecto a un multimetro o herramienta de medición de la intensidad consumida por el motor.

Por ejemplo, con un fuente de alimentación regulable, que suelen contar un display para visualizar la intensidad consumida, conectamos motor directamente y anotamos la intensidad, personalmente con el voltaje a 12 Voltios cualquier de estos dos prototipos funciona.

Para el prototipo del 3 DOF Hover se necesita entorno a 3 Amperios por motor, 12 A en total, mientras que para el prototipo del péndulo con 1 A es suficiente en nominal, aunque si bien es cierto que cuando hay cambios con una dinámica bastante agresiva, se necesita una fuente con algo de margen.

Mi recomendación es usar una fuente de PC que nos proporciona estos 12 V, y una amperaje muy decente para este proposito, cualquier fuente de un PC de sobremesa actual o algo antiguo puede tener o superar los 180 Watts, más de los 12 A necesarios para los prototipos.

Una vez tenemos elegida la fuente, pasamos a los drivers, debemos elegir un driver capaz de soportar esta intensidad, la suerte que tenemos hoy en dia es que por poco dinero podemos tener un driver que supla estas caracteristicas, yo compré estos drivers por Aliexpress que para este proposito cumplen su papel.

<img src="img\foto_driver_dc.png" alt="foto_driver_dc.png" style="width:auto;height:200px;">

Por ejemplo, este driver tiene salida para dos motores de corriente continua con una intensidad de 8 A nominal por canal de motor, y es bastante sencillo de usar, su uso depende de cada driver.

<img src="img\driver_dc_logic.png" alt="driver_dc_logic.png" style="width:auto;height:200px;">

En este caso, viendo la tabla lógica nos podemos hacer una idea del funcionamiento del driver. 

<img src="img\driver_dc_function.png" alt="driver_dc_function.png" style="width:auto;height:200px;">

Para probar este driver o cualquier otro sólo nos queda saber la guinda del pastel y es saber el diagrama del conector con el prototipo. Siguiendo la lógica de la opción elegida con el encoder, es  acoplarnos al conector que utilizaba Quanser para los motores, un conector DIN 4 pines:

<img src="img\conector-din-4-pines-macho.jpg" alt="conector-din-4-pines-macho.jpg" style="width:auto;height:200px;">

Debemos seguir el esquematico sencillo de la imagen de abajo, y ya tendremos nuestro cable listo. El orden de los polos nos da un poco igual porque siempre los podemos conectar al revés en los bornes o cambiar el sentido del giro mediante código.

<img src="img\conector-din-4-pines-macho-motor-wiring.jpg" alt="conector-din-4-pines-macho-motor-wiring.jpg" style="width:auto;height:200px;">

## Conclusión

La adaptación de las maquetas de Quanser para microcontroladores como Arduino, STM32, ESP32, o sistemas basados en Linux como Raspberry Pi, LattePanda Alpha, BeagleBone, entre otros, abre nuevas oportunidades en educación e investigación en mecatrónica y control de sistemas. Este proceso implica ajustar los encoders HEDS-9100 y los motores de corriente continua para su compatibilidad con microcontroladores y fuentes de alimentación comunes. Esta adaptación simplificada, junto con la disponibilidad de componentes estándar y recursos detallados, ofrece una plataforma versátil y accesible para experimentación y aprendizaje, promoviendo el desarrollo de habilidades en control y diseño de sistemas dinámicos.

### Más sobre encoder de cuadratura
- [https://makeatronics.blogspot.com/2013/02/efficiently-reading-quadrature-with.html](https://makeatronics.blogspot.com/2013/02/efficiently-reading-quadrature-with.html)
- [https://electronics.stackexchange.com/questions/360637/quadrature-encoder-most-efficient-software-implementation](https://electronics.stackexchange.com/questions/360637/quadrature-encoder-most-efficient-software-implementation)

## Enlaces de referencia
- [1] https://www.quanser.com/products/3-dof-hover/
- [2] https://www.quanser.com/products/rotary-inverted-pendulum/