# Glosario de términos

## Contenido

??? info "**ACC**: Adaptative Cruise Control - Control de crucero adaptativo""

    Un sistema de control de crucero para vehículos que controla la velocidad longitudinal. El ACC puede mantener una velocidad de referencia deseada o ajustar su velocidad en consecuencia para mantener distancias de conducción seguras con otros vehículos. 

??? info "**EGO**"

    Término para expresar la noción de uno mismo, que se utiliza para referirse al vehículo que se controla de forma autónoma, por oposición a otros vehículos u objetos de la escena.  Se utiliza con mayor frecuencia en la forma ego-vehículo, que significa el vehículo autónomo.

??? info "**AMFE**: Análisis Modal de Fallos y Efectos - **FMEA** Failure mode and effects analysis"

    Un enfoque ascendente del análisis de fallos que examina las causas individuales y determina sus efectos en el sistema de nivel superior.

??? info "**GNSS**: Sistema Mundial de Navegación por Satélite - Global Navigation Satellite System"

    Término genérico para todos los sistemas por satélite que proporcionan una estimación de la posición. El Sistema de Posicionamiento Global (GPS - Global Positioning System) fabricado por Estados Unidos es un tipo de GNSS. Otro ejemplo es el GLONASS (Globalnaya Navigazionnaya Sputnikovaya Sistema) de fabricación rusa. Otro ejemplo es el Galileo "es el sistema paneuropeo de radionavegación y posicionamiento por satélite desarrollado por la Agencia Espacial Europea (ESA) y financiado por la Comisión Europea".

??? info "**AFO - HAZOP**: Análisis Funcional de Operatividad - Estudio de peligros y operabilidad - Hazard and Operability Study"

    Una variación del AMFE (Análisis Modal de Fallos y Efectos) que utiliza palabras guía para hacer una lluvia de ideas sobre conjuntos de posibles fallos que pueden surgir.

??? info "**IMU**: Unidad de medición inercial - Inertial Measurement Unit" 

    Dispositivo sensor compuesto por un acelerómetro y un giroscopio. La IMU se utiliza para medir la aceleración y la velocidad angular del vehículo, y sus datos pueden fusionarse con otros sensores para la estimación del estado.

??? info "**AHRS**: Sistemas de Referencia de Actitud y Rumbo - Attitude and Heading Reference Systems"

    Son un conjunto de distintos sensores tridimensionales que proporcionan información acerca del rumbo, la actitud, y la guiñada de una aeronave o vehículo.

??? info "**LIDAR**: Light Detection and Ranging o Laser Imaging Detection and Ranging"

    Tipo de sensor que detecta el alcance transmitiendo luz y midiendo el tiempo de retorno y los desplazamientos de la señal reflejada.

??? info "**LTI**: Sistema Lineal e Invariante en el Tiempo - Linear Time-Invariant System"

    Un sistema lineal cuya dinámica no cambia con el tiempo. Por ejemplo, un coche que utilice el modelo del bicicleta es un sistema LTI. Si el modelo incluye que los neumáticos se degraden con el tiempo (y cambien la dinámica del vehículo), entonces el sistema ya no sería LTI.

??? info "**LQR**: Regulador Lineal Cuadrático - Linear Quadratic Regulator"

    Un método de control que utiliza la retroalimentación completa del estado. El método trata de optimizar una función de coste cuadrática dependiente del estado y de la entrada de control.

??? info "**MPC**: Control Predictivo - Model Predictive Control"

    Método de control cuya entrada de control optimiza una función de coste definida por el usuario en un horizonte temporal finito. Una forma común de MPC es el LQR (regulador lineal cuadrático) de horizonte finito.

??? info "**NHTSA**: Administración Nacional de Seguridad del Tráfico en Carretera (EEUU) - National Highway Traffic Safety Administration (EEUU)"

    Agencia del Poder Ejecutivo del gobierno de EE.UU. que ha desarrollado un marco de 12 partes para estructurar la evaluación de la seguridad de la conducción autónoma.  El marco puede consultarse aquí. [NTHSA - AUTOMATED DRIVING SYSTEMS 2.0 - A vision for Safety](https://www.nhtsa.gov/sites/nhtsa.dot.gov/files/documents/13069a-ads2.0_090617_v9a_tag.pdf)

??? info "**ODD**: Dominio de Diseño Operativo - Operational Design Domain"

    Conjunto de condiciones en las que un sistema determinado está diseñado para funcionar. Por ejemplo, un coche de conducción autónoma puede tener un sistema de control diseñado para la conducción en entornos urbanos y otro para la conducción en autopista.

??? info "**OEDR**: Detección y Respuesta a Objetos y Eventos - Object and event detection and response"

    La capacidad de detectar objetos y eventos que afectan de forma inmediata a la tarea de conducción, y de reaccionar ante ellos adecuadamente. 

??? info "**PID**: Control Proporcional Integral Derivativo - Proportional Integral Derivative Controller"

    Un método común de control definido por 3 ganancias.

    1) Una ganancia proporcional que escala la salida de control en función de la cantidad de error.

    2) Una ganancia integral que escala la salida de control en función de la cantidad de error acumulado.

    3) Una ganancia derivativa que escala la salida de control en función de la tasa de variación del error.

??? info "**RADAR**: Radio Detección y Alcance - Radio Detection and Ranging"

    Un tipo de sensor que detecta el alcance y el movimiento transmitiendo ondas de radio y midiendo el tiempo de retorno y los desplazamientos de la señal reflejada.

??? info "**SONAR**: Navegación por Sonido - Sound Navigation And Ranging"

    Tipo de sensor que detecta la distancia y el movimiento mediante la transmisión de ondas sonoras y la medición del tiempo de retorno y los desplazamientos de la señal reflejada. 

#### Enlaces de referencia
- <https://www.coursera.org/learn/intro-self-driving-cars>
- <https://es.wikipedia.org/wiki/Galileo_(navegaci%C3%B3n_por_sat%C3%A9lite)>
- <https://dallocas.blogs.upv.es/docencia/vehiculos-autonomos-y-conectados/limitacion-de-los-vehiculos-autonomos-y-conectados-dominios-de-diseno-operativos/>
- <https://taxonomy.connectedautomateddriving.eu/object-and-event-detection-and-response/>

