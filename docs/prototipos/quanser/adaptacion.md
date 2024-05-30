# Adaptación del cableado para el uso de las maquetas de Quanser con microcontroladores como Arduino, STM32, ESP32 o incluso SBCs como Raspberry Pi, LattePanda Alpha, BeagleBone, etc...

*El experimento 3 DOF Hover proporciona un banco de pruebas económico para comprender y desarrollar leyes de control para la dinámica de vuelo y el control de vehículos con despegue vertical.* [1]

*El módulo de péndulo giratorio invertido se conecta a la unidad base del servo giratorio, ampliando los temas de mecatrónica y controles que se pueden enseñar. El módulo de péndulo desafía a los estudiantes no solo a modelar y controlar un péndulo, sino también a aprender sobre sistemas de control híbridos ajustando un sistema de control oscilante. Además de enseñar conceptos de control intermedio, el péndulo rotatorio invertido se puede utilizar para la investigación en diversas áreas, incluido el control difuso.* [2]

<img src="img\three_dof_hover_quanser.jpg"  style="width:auto;height:200px;">

<img src="img\rotary_inverted_pendulum_quanser.jpg"  style="width:auto;height:200px;">

Ambas maquetas están compuestas por encoders de cuadratura y motores de corriente continua, estos nos permiten obtener la posición y actuar sobre la maqueta.

## Adaptar los encoders

Para poder leer el encoder, una opción, es acoplarnos al conector que utilizaba Quanser, un conector DIN 5 pines:

<img src="img\conector-din-5-pines-macho.jpg" style="width:auto;height:200px;">

Por tanto, nuestro objetivo es contruir un cable compatible con el encoder que podamos leer con Arduino.

Es por ello que primero miraremos que clase de encoders monta. Los encoders que utilizan las maquetas son los HEDS-9X00 que requieren seguir el siguiente esquema:

<img src="img\encoder_heds_9100_schematic.png" style="width:auto;height:200px;">

Este esquema es útil cuando el Arduino puede leer señales a 5V. Como vemos utilizaremos unas resistencias entorno a las 3 KΩ. Pero si tenemos un Arduino que funciona a 3.3 V tenemos que realizar una pequeña modificación, y es poner la resistencia de pull-up a 3.3 V:

<img src="img\schematic_3_3_V.png" style="width:auto;height:200px;">

Para montar este esquema con los cables originales de quanser tenemos que tener precaución porque el color del cable (primera imagen) no coincide con los colores que se ven del siguiente conector (el resto de imágenes) (en estos conectores el canal index no está conectado):

<img src="img\cable_y_pcb_in_progress.jpg"  style="width:auto;height:200px;">
<img src="img\conector_din_5_vista_1.jpg" style="width:auto;height:200px;">
<img src="img\conector_din_5_vista_2.jpg" style="width:auto;height:200px;">
<img src="img\conector_encoder.jpg"  style="width:auto;height:200px;">

Este cable sigue el siguiente patrón, para el cable que he construido, he seguido más o menos el mismo patrón de color que el conector externo, de ahí el color entre paréntesis:

<img src="img\tabla_conexión.png" style="width:auto;height:200px;">
<img src="img\cable_zoom.jpg" style="width:auto;height:200px;">
<img src="img\salida_conector.jpg" style="width:auto;height:200px;">

Si por otra parte compramos los conectores de internet y queremos construir nuestro propio cable tenemos el siguiente esquema, añadiendo la parte del esquemático con las resistencias de pull-up:

<img src="img\conector_din_5_vista_detallada.jpg" style="width:auto;height:200px;">

## Adaptar los motores

Para la adaptación de los motores el proceso es mucho más "sencillo", ya que sólo debemos tener acceso a la información del datasheet del motor y un multimetro, con la intención de saber la intensidad consumida por el motor.

Por ejemplo, con un fuente de alimentación regulable, que suelen contar un display para visualizar la intensidad consumida, conectamos motor directamente y anotamos la intensidad, personalmente con el voltaje a 12 Voltios cualquier de estos dos prototipos funciona.

Para el prototipo del 3 DOF Hover se necesita entorno a 3 Amperios por motor, 12 A en total, mientras que para el prototipo del péndulo con 1 A es suficiente en nominal, aunque si bien es cierto que cuando hay cambios con una dinámica bastante agresiva, se necesita una fuente con algo de margen.

Mi recomendación es usar una fuente de PC que nos proporciona estos 12 V, y una amperaje muy decente para este propósito, cualquier fuente de un PC de sobremesa actual o algo antiguo puede tener o superar los 180 Watts, más de los 12 A necesarios para los prototipos.

Una vez tenemos elegida la fuente, pasamos a los drivers, debemos elegir un driver capaz de soportar esta intensidad, la suerte que tenemos hoy en dia es que por poco dinero podemos tener un driver que supla estas características, yo compré estos drivers por Aliexpress que para este propósito cumplen su papel.

<img src="img\foto_driver_dc.png"  style="width:auto;height:200px;">

Por ejemplo, este driver tiene salida para dos motores de corriente continua con una intensidad de 8 A nominal por canal de motor, y es bastante sencillo de usar, su uso depende de cada driver.

<img src="img\driver_dc_logic.png"  style="width:auto;height:200px;">

En este caso, viendo la tabla lógica nos podemos hacer una idea del funcionamiento del driver. 

<img src="img\driver_dc_function.png"  style="width:auto;height:200px;">

Para probar este driver o cualquier otro sólo nos queda saber la guinda del pastel y es saber el diagrama del conector con el prototipo. Siguiendo la lógica de la opción elegida con el encoder, es  acoplarnos al conector que utilizaba Quanser para los motores, un conector DIN 4 pines:

<img src="img\conector-din-4-pines-macho.jpg" style="width:auto;height:200px;">

Debemos seguir el esquemático sencillo de la imagen de abajo, y ya tendremos nuestro cable listo. El orden de los polos NO da igual, depende del prototipo, si un prototipo, el motor sólo gira en un sentido, es posible que el otro polo del motor este conectado a GND como El prototipo de Quanser de 3 DOF Hover. En cambio para el prototipo de péndulo giratorio invertido nos da igual que polo conectar porque el motor necesitamos que gire en ambos sentidos, y el driver del motor DC nos permita aplicar dos PWMs, siempre excluyendo uno PWM del otro al aplicarse, es decir, dejar uno a 0 o en su defecto, hay drivers que esto ya lo contemplan y pueden tener un pin DIR para señalar la dirección de giro con un pin digital.

<img src="img\conector-din-4-pines-macho-motor-wiring.jpg" style="width:auto;height:200px;">

!!! danger "Peligro - MUY IMPORTANTE"

    El prototipo de Quanser de 3 DOF Hover tiene la toma de tierra compartida (GND), y como los motores sólo giran en un sentido hay que tener cuidado de como se conecta el motor y el driver que se le proporciona la polaridad adecuada para su correcto funcionamiento, sino este provocará un cortocircuito. Se debe buscar el positivo del conector DIN con el positivo del motor con el positivo la salida cuando se aplica el PWM al driver, con un multimetro es un momento. El otro polo del motor debe estar conectado a GND de la alimentación.

### Apuntes para el proceso de Quanser de 3 DOF Hover

Para el prototipo de Quanser de 3 DOF Hover, como bien dice la nota, tiene la toma de tierra compartida.

<img src="img\three_dof_hover_quanser.jpg" style="width:auto;height:200px;">

Así pues, hay que tener cuidado con el cableado del motor, en este caso yo he optado por seguir este esquema para el conector, dejo los colores rojo y negro, aunque en mi cable sean de color marrón y blanco.

<div class="row">
  <div class="column">
    <img src="img\conector-din-4-pines-macho-motor-wiring-v2.jpg" style="width:auto;height:200px;">
  </div>
  <div class="column">
    <img src="img\cableado_colores.jpg" style="width:auto;height:200px;">
  </div>
</div>

Como podemos ver en las siguientes imágenes, tenemos el driver, tanto los transistores como el esquema que representan, en este caso con un "único" driver de DC para controlar dos motores, el cuál presenta 2 puentes en H completos, es decir, 4 medio puentes en H, podemos usar estos 4 medio puentes para controlar los cuatro motores del aparato, ya que solo necesitamos que funcione en un sentido de giro.

<div class="row">
  <div class="column">
<img src="img\driver_dc_product_size.png" style="width:auto;height:200px;"> 
  <div class="column">
<img src="img\half-bridge.png" style="width:auto;height:200px;">
  </div>
</div>

Por último, comentar esta imagen, aquí podemos ver todos los motores conectados con el cableado blanco mientras los marrones están conectados a la toma de tierra.

<div class="column">
<img src="img\driver_cableado.png" style="width:auto;height:200px;">
</div>

!!! warning "Advertencia - EXPERIENCIA"

    No he acabado de tener buena experiencia con estos drivers porque el disipador no ajusta del todo, cuando les das caña a los motores, los transistores sufren, se calienten, incluso se han llegado a quemar algunos, no acabo de recomendarlos, asegurar el pad térmico para evitar sobrecalentamientos.

## Conclusión

La adaptación de las maquetas de Quanser para microcontroladores como Arduino, STM32, ESP32, o sistemas basados en Linux como Raspberry Pi, LattePanda Alpha, BeagleBone, entre otros, abre nuevas oportunidades en educación e investigación en mecatrónica y control de sistemas. Este proceso implica ajustar los encoders HEDS-9X00 y los motores de corriente continua para su compatibilidad con microcontroladores y fuentes de alimentación comunes. Esta adaptación simplificada, junto con la disponibilidad de componentes estándar y recursos detallados, ofrece una plataforma versátil y accesible para experimentación y aprendizaje, promoviendo el desarrollo de habilidades en control y diseño de sistemas dinámicos.

### Más sobre encoder de cuadratura
- [https://makeatronics.blogspot.com/2013/02/efficiently-reading-quadrature-with.html](https://makeatronics.blogspot.com/2013/02/efficiently-reading-quadrature-with.html)
- [https://electronics.stackexchange.com/questions/360637/quadrature-encoder-most-efficient-software-implementation](https://electronics.stackexchange.com/questions/360637/quadrature-encoder-most-efficient-software-implementation)

## Enlaces de referencia
- [1] https://www.quanser.com/products/3-dof-hover/
- [2] https://www.quanser.com/products/rotary-inverted-pendulum/