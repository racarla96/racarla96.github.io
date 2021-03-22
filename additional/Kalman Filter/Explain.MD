Esta entrada pretende ser el primer escrito serio de este blog sobre robótica y teoría de control. El objectivo es tratar de dar claridad a aspectos y conceptos de robótica de los cuales hay mucha documentación en inglés, pero muy poca en habla hispana.

Partimos del siguiente problema, calcular la derivada de una función dada en el ordenador, según Wikipedia:

###### Derivative - Wikipedia:
> Differentiation is the action of computing a derivative.

> 'Differentiation' es la acción de calcular una derivada.

En algunos problemas de robótica puede ser posible que necesitemos calcular la derivada de una función dada, esta función puede contener funciones no lineales que a la hora de realizar la derivada analítica o calcular la derivada puede ser tedioso o computacionalmente costoso.

Otro concepto que puede ser importante en estos lares, es el concepto de 'Gradiente':
###### Gradiente - Wikipedia:
> En matemáticas, el ‘gradiente’ es una generalización multivariable de la derivada.

Por ejemplo, que es dada una función f(x,y,z) en la cual x, y, z son números reales, dando como resultado un valor w, se calcula la derivada de esta función respecto a cada variable y el resto se considerarian constante.

Os recomiendo ver estos dos videos de Unicoos:

- [Derivadas Parciales - Unicoos](https://www.youtube.com/watch?v=HVJmcX0-uWI) (Video - 18/03/2021)

En robótica, el concepto de gradiente, también es conocido como el Jacobiano o Matriz jacobiana, según Wikipedia:

###### Matriz y determinante jacobianos - Wikipedia

> La matriz jacobiana es una matriz formada por las derivadas parciales de primer orden de una función. Una de las aplicaciones más interesantes de esta matriz es la posibilidad de aproximar linealmente a la función en un punto. En este sentido, el jacobiano representa la derivada de una función multivariable.

- [Matriz JACOBIANA - Pedro J Viveros - Tutoriales](https://www.youtube.com/watch?v=yb4RadmtoVU) (Video - 18/03/2021) 

También se recomienda ver los conceptos de matriz Hessiana.

##### Enlazando conceptos

¿?


##### Tipos de Differentiation

Una vez tenemos claro porque es necesario el uso de una matriz jacobiana o matrices de hessianas o matrices de n derivadas parciales, queremos saber como calcular la derivada de esta función multivariable con un ordenador.

## Bibliografía
##### Derivative and differentiation:
- [Derivative - Wikipedia](https://en.wikipedia.org/wiki/Derivative) (PDF - 18/03/2021)
- [Gradiente - Wikipedia](https://es.wikipedia.org/wiki/Gradiente) (PDF - 18/03/2021)
- [Gradient - Wikipedia](https://en.wikipedia.org/wiki/Gradient) (PDF - 18/03/2021)
- [El gradiente - Khan Academy](https://es.khanacademy.org/math/multivariable-calculus/multivariable-derivatives/partial-derivative-and-gradient-articles/a/the-gradient) (PDF - 18/03/2021)
- [¿Qué son las funciones multivariables? - Khan Academy](https://es.khanacademy.org/math/multivariable-calculus/thinking-about-multivariable-function/ways-to-represent-multivariable-functions/a/multivariable-functions#:~:text=Una%20funci%C3%B3n%20se%20llama%20multivariable%20si%20su%20entrada%20consiste%20de%20varios%20n%C3%BAmeros.&text=Si%20la%20salida%20de%20una,normalmente%20funciones%20con%20valores%20vectoriales.) (PDF - 18/03/2021)
- [Derivadas Parciales - Unicoos](https://www.youtube.com/watch?v=HVJmcX0-uWI) (Video - 18/03/2021)
- [Matriz y determinante jacobianos](https://es.wikipedia.org/wiki/Matriz_y_determinante_jacobianos) (PDF - 18/03/2021)
- [The Jacobian matrix - Khan Academy](https://www.youtube.com/watch?v=bohL918kXQk) (Video - 18/03/2021)
##### Kalman filter:
- [Extended Kalman Filter - Wikipedia](https://en.wikipedia.org/wiki/Extended_Kalman_filter) (PDF - 18/03/2021)
- [A “quick” review of Error State - Extended Kalman Filter](https://notanymike.github.io/Error-State-Extended-Kalman-Filter/) (PDF - 18/03/2021)

#### Disclaimer - Descargo de responsabilidad:
- No soy un experto en traducción y trato de traducir lo mejor posible los conceptos del inglés al español.
- Guardo copias en PDF y videos con el próposito de guardar el conocimiento en caso de que se borre en la fuente y se incluye en la sección de bibliografía para dar el mérito al autor que se merece.
