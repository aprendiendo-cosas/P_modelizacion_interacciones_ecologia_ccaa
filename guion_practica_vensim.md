# Instrucciones para realizar la práctica denominada "Construcción de modelos basados en procesos usando Vensim"


> + **_Versión_**: 2021-2022
> + **_Asignatura (grado)_**: Ecología (Ciencias ambientales). Curso 2020-2021
> + **_Autor_**: Curro Bonet-García (fjbonet@uco.es)
> + **_Duración_**: 3 horas.

![portada](https://github.com/aprendiendo-cosas/P_vensim_depredacion_ecologia_ccaa/raw/2020-2021/imagenes/portada.png)

## Objetivos

Esta práctica tiene los siguientes objetivos:
+ Disciplinares:
  + Reforzar el conocimiento adquirido sobre dinámicas poblacionales de presas y depredadores.
  
  + Constatar el efecto de la retroalimentación negativa y positiva en las interacciones presa-depredador.
  
  + Constatar cómo la homeostasis es una propiedad emergente cuando interactúan presas y depredadores.
  
  + Comprobar el efecto de la incorporación de factores (competencia intraespecífica, depredación) cuando simulamos el crecimiento de poblaciones de presa.
  
+ Instrumentales:

  + Aprender el concepto de modelo basado en procesos.
  + Distinguirlo de los modelos espacialmente explícitos.
  + Conocer el funcionamiento de Vensim como herramienta para realizar modelos basados en procesos. 




## Contextualización ecológica

El contexto ecológico de esta práctica es la depredación y sus efectos sobre las poblaciones de especies implicadas. [Este](https://rawcdn.githack.com/aprendiendo-cosas/Te_depredacion_ecologia_ccaa/2020-2021/guion_depredacion.html) guión muestra los conceptos principales comentados a este respecto durante la asignatura. 


## Modelos basados en procesos

Los modelos son representaciones simplificadas de la realidad que nos ayudan a conocerla mejor. En nuestro caso los modelos ecológicos nos ayudan a comprender cómo funcionan los ecosistemas.

En el proceso de construcción de un modelo, simpflificamos la realidad y "quitamos" ciertas variables. Por ejemplo, un mapa es un modelo en el que la simplificación consiste en que el tamaño de los objetos no es el real. La capacidad explicativa de un modelo depende de este proceso de "reducción de la dimensionalidad".

Sin embargo, al mismo tiempo ocurre que un modelo es tanto mejor cuanto más ajustado está a la realidad. Eso genera un aparente dilema que se resuelve indicando que cuando construimos un modelo establecemos una relación simétrica con la realidad. La siguiente figura muestra esta situación. 

<img src="https://github.com/aprendiendo-cosas/P_vensim_depredacion_ecologia_ccaa/raw/2020-2021/imagenes/simetria.png" alt="simetria" style="zoom:50%;" />

Esta simetría tiene varias implicaciones a efectos prácticos:

+ Es muy importante que las variables que simulemos sean relevantes en la realidad. Por ejemplo, si queremos saber cómo cambia la evolución del número de conejos en función del número de linces, no tiene sentido que incorporemos a nuestro modelo el efecto de la dureza del suelo.

+ También es crítico establecer las relaciones entre las variables que queremos simular y la realidad. El establecimiento de este paralelismo es determinante. Si queremos simular cómo crece un árbol, debemos de, por ejemplo, definir cómo medimos ese crecimiento: altura, tamaño del tronco, etc.

+ Asimismo debe de haber un proceso de traducción de las preguntas que le hacemos a la realidad en preguntas que le formulamos al modelo. En el ejemplo anterior, evaluar cómo crece un árbol (pregunta a la realidad) se puede traducir en: ¿cómo cambia la altura de un árbol en función del clima? (pregunta al modelo).

+ Otra cuestión clave es la interpretación de los resultados obtenidos por un modelo. Éstos han de ser analizados críticamente, teniendo en cuenta el proceso de modelización y la información tomada para ejecutarlo. El hecho de que los resultados salgan de un modelo no indican que sean inherentemente correctos.

Usamos modelos todo el rato para interpretar la realidad a nuestro alrededor. Los mapas son ejemplos muy buenos de modelos. Pero el concepto de "asignatura" que usamos aquí también es un modelo. Usamos esta idea como una forma de aproximarnos a una realidad compleja que no comprendemos.

Hay muchos tipos de modelos diferentes, pero en nuestro caso, solo haremos referencia a dos tipos. 

+ Modelos espacialmente explícitos: entre las variables que se contemplan está el espacio. Estos modelos permiten simular cómo se distribuye en el espacio una o varias variables. Es decir, contemplan el espacio y sus dimensiones. Los SIG o los mapas son modelos espacialmente explícitos. 
+ Modelos temporalmente explícitos: En este caso los modelos tienen en cuenta el transcurrir del tiempo, así que nos permiten conocer cómo cambian las variables simuladas en el dominio del tiempo.  ¿Qué modelos temporalmente explícitos hemos visto muchas veces a lo largo de la asignatura?



## Un ejemplo de modelo para simular la dinámica depredador-presa



En esta práctica simularemos cómo cambian las poblaciones de depredador y de presas cuando interactúan. Veremos en acción los siguientes conceptos:

+ Retroalimentación positiva: a más presas más depredador.
+ Retroalimentación negativa: a más depredador menos presas.
+ Homeostasis resultante de la combinación de ambas retroalimentaciones.

En primer lugar trabajaremos con un modelo muy sencillo:

<iframe
  src="https://exchange.iseesystems.com/public/jondarkow/lotka-volterra-predator-prey-model/index.html#page1"
  style="width:100%; height:450px;"
></iframe>

Para aprender los conceptos anteriores, procederemos estudiando los siguientes elementos:
+ Variables del modelo. 
  + Variables de estado. Cambian en cada ejecución del modelo en cada lapso de tiempo. 
    + 	Nº de presas en tiempo t
    + 	Nº de depredadores en tiempo t
    + 	En Vensim se usa una metáfora: el depósito. A más nivel del depósito, más alto es el valor numérico de la variable de estado.
  + Parámetros del modelo. Se mantienen constantes durante la ejecución del modelo. Podemos cambiarlos pero los valores que toman se aplican a toda la ejecución del modelo. Es decir, cambian de ejecución en ejecución.
    + 	Tasa de natalidad.
    + 	Tasa de mortalidad.
    + 	Número inicial de presas y depredadores.

+ Matemáticas subyacentes: ecuaciones diferenciales. Estas herramientas nos permiten cuantificar cómo cambian las variables de estado en cada diferencial de tiempo. 

## Paso a paso

+ **Población de conejos creciendo exponencialmente**
  
  1. Creamos un modelo de crecimiento exponencial para el conejo:
  
       1.1. Crear variable de estado ("level") llamada *Nº conejos*.
  
       1.2. Creamos "tasa" llamada *Nacimientos conejos*. El punto de inicio está a la izquierda de la anterior y finaliza en *Nº conejos.*
  
       1.3. Crear variable llamada *Tasa natalidad conejos*
  
       1.4 Creamos "tasa" llamada *Muertes conejos*. Empieza en *Nº conejos* y termina a su derecha.
  
       1.5. Creamos variable llamada *Tasa mortalidad conejos*.
  
       1.6. Mediante flechas conectamos lo siguiente:
       
         + *Tasa natalidad conejos* con *Nacimientos conejos*
         + *Nº conejos* con *Nacimientos conejos*.
         + *Nº conejos* con *Muertes conejos*.
         + *Tasa mortalidad conejos* con *Muertes conejos*.
       
       1.7. Añadimos las siguientes ecuaciones (botón "equations"):
       
         + *Nacimientos conejos = Nº conejos \* Tasa de natalidad conejos*
         + *Nº conejos = Nacimientos conejos-Muertes conejos*. Número de inicial de conejos= 100
         + *Muertes conejos = Nº conejos \* Tasa mortalidad conejos*.
         + *Tasa natalidad conejos* = 2
         + *Tasa mortalidad conejos* = 0.02
  
  2. Guarda el modelo y dale este nombre: *1_conejo_exponencial.mdl*
  
  3. Damos nombre a la ejecución: *conejo_exponencial_2_002* y la ejecutamos.
  
  4. Vemos la gráfica de evolución del número de conejos.
  
  5. Cambiamos la tasas de mortalidad del conejo: 0.05
  
  6. Damos nombre a la ejecución: *conejo_exponencial_2_005* y la ejecutamos. Vemos la gráfica del número de conejos. ¿Qué diferencias hay entre las dos gráficas? ¿a qué se deben?
  
+ **Población de conejos creciendo logísticamente**
  Creamos un modelo de crecimiento logístico para el conejo. Contemplamos en este caso la competencia intraespecífica. Esto implica definir la capacidad de carga del sistema. Para ello hemos de crear y/o modificar los siguientes elementos del modelo ya existente:
  
  7. Partiendo del modelo *1_conejo_exponencial.mdl* hacemos lo siguiente:
  
       7.1.  Creamos variable *capacidad de carga* y le damos el valor de 2000 (usando el botón "equations")
       7.2. Conectamos esta nueva variable con *Nacimientos conejos*.
       7.3. Modificamos la ecuación de *Nacimientos conejos* para que incluya a la capacidad de carga: *Nº conejos \* Tasa de natalidad conejos \* (1-Nº conejos / Capacidad de carga)*.
  
  2. Damos nombre a la ejecución: *conejo_logistico_2_005* y la ejecutamos. Vemos la gráfica del número de conejos. ¿Qué ves? ¿Por qué?
  
  3. Cerramos sin guardar los cambios.
  
  4. Abrir el modelo creado anteriormente: *1_conejo_exponencial.mdl* y cambiamos el periodo de ejecución del modelo (initial time 2000. Final time 2005).
  
  5. Damos nombre a la ejecución: *conejo_exponencial_2_002* y ejecutamos de nuevo. Vemos la gráfica.
  
  6. Añadimos de nuevo la variable con la capacidad de carga y modificamos la ecuación de *Nacimientos conejos*. Ver punto 7 para más detalles. 
  
  7. Damos nombre a la ejecución: *conejo_logistico_2_002* y ejecutamos. Mostramos la gráfica del número de conejos. Veremos tanto la correspondiente al crecimiento logístico como a la del exponencial. Ahora sí vemos bien las diferencias entre ambas formas de crecimiento poblacional. 
  
  8. Cambia el periódo de ejecución del modelo. Initial time 2000. Final time 2040. 
  
  9. Guardamos el modelo:  *2_conejo_logistico.mdl*



+ **Comunidad con dos especies y depredación: linces depredando conejos y conejos creciendo exponencialmente (sin competencia intraespecífica)**

  16. Abrimos el modelo *1_conejo_exponencial.mdl*

  17. Incorporalos los siguientes elementos: 
      
      17.1. Crear variable de estado ("level") llamada *Nº linces*.
      
      17.2. Creamos "tasa" llamada *Nacimientos linces*. El punto de inicio está a la izquierda de la anterior y finaliza en *Nº linces.*
      
      17.3. Crear variable llamada *Tasa natalidad linces*
      
      17.4 Creamos "tasa" llamada *Muertes linces*. Empieza en *Nº linces* y termina a su derecha.
      
      17.5. Creamos variable llamada *Tasa mortalidad linces*.
      
      17.6. Mediante flechas conectamos lo siguiente:
      
        + *Tasa natalidad linces* con *Nacimientos linces*
        + *Nº linces* con *Nacimientos linces*.
        + *Nº linces* con *Muertes linces*.
        + *Tasa mortalidad linces* con *Muertes linces*.
      
      17.7. Añadimos las siguientes ecuaciones (botón "equations"):
      
        + *Nacimientos linces = Nº linces \* Tasa de natalidad linces*
        + *Nº linces = Nacimientos linces-Muertes linces*. Número de inicial de linces= 100
        + *Muertes linces = Nº linces \* Tasa mortalidad linces*.
        + *Tasa natalidad linces* = 0.01
        + *Tasa mortalidad linces* = 0.6
      
  18. Además, debemos de relacionar las dinámicas poblacionales de ambas especies a través de la depredación. Lo veremos con más detalle en las sesiones de teoría, pero asumiremos que el número de linces afecta (negativamente) a la mortandad de los conejos y que el número de conejos afecta (positivamente) al nacimiento de los linces. En términos del modelo de Vensim, esto implica:
      + Añadir flecha desde *Nº conejos* hasta *Nacimientos linces*
      + Modificar la ecuación de *Nacimientos linces* así: *Nº linces \* Tasa de natalidad linces \* Nº conejos*
      + Añadir flecha desde *Nº linces* hasta *Muertes conejos"
      + Modificar la ecuación de *Muertes conejos* así: *Nº conejos \* Tasa mortalidad conejos \* Nº linces*
  19. Guardamos el modelo con este nombre: *3_conejo_exponencial_lince.mdl*
  20. Nombramos la ejecución: *conejo_exp_lince* y la ejecutamos. Mostramos las gráficas de *Nº conejos* y *Nº linces* . ¿Cómo se interpretan las gráficas obtenidas? ¿qué diferencias ves respecto a las del modelo anterior?

+ **Comunidad con dos especies y depredación: linces depredando conejos y conejos creciendo logísticamente (con competencia intraespecífica)**
  
  21. Partimos del modelo anterior (*3_conejo_exponencial_lince.mdl*) sobre el que incoraremos el "freno" provocado por la competencia intraespecífica: capacidad de carga del medio los conejos:
       21.1.  Creamos variable *capacidad de carga conejos* y le damos el valor de 2000 (usando el botón "equations")
      21.2. Conectamos esta nueva variable con *Nacimientos conejos*.
      21.3. Modificamos la ecuación de *Nacimientos conejos* para que incluya a la capacidad de carga: *Nº conejos \* Tasa de natalidad conejos \* (1-Nº conejos / Capacidad de carga)*.
  22. Damos nombre a la ejecución: *conejo_log_lince* y la ejecutamos. Vemos la gráfica del número de conejos y de linces. Puedes comparar los resultados de este modelo (con competencia intraespecífica para el conejo) con los del anterior (sin competencia intraespecífica). ¿cuál de las dos situaciones consideras que es más "estable"?
  23. Guardamos este nuevo modelo: *4_conejo_logistico_lince.mdl*

+ **Comunidad de tres especies (depredación y competencia interespecífica): linces y águilas depredando conejos**

