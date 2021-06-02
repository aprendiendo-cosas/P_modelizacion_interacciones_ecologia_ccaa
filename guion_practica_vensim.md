# Instrucciones para realizar la práctica denominada "Construcción de modelos basados en procesos usando Vensim"


> + **_Versión_**: 2020-2021
> + **_Asignatura (grado)_**: Ecología (Ciencias ambientales). Curso 2020-2021
> + **_Autor_**: Curro Bonet-García (fjbonet@uco.es)
> + **_Duración_**: 2 horas.

![portada](https://github.com/aprendiendo-cosas/P_vensim_depredacion_ecologia_ccaa/raw/main/imagenes/portada.png)

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

El contexto ecológico de esta práctica es la depredación y sus efectos sobre las poblaciones de especies implicadas. [Este](https://aprendiendo-cosas.github.io/Te_depredacion_ecologia_ccaa/guion_depredacion.html) guión muestra los conceptos principales comentados a este respecto durante la asignatura. 


## Modelos basados en procesos

Los modelos son representaciones simplificadas de la realidad que nos ayudan a conocerla mejor. En nuestro caso los modelos ecológicos nos ayudan a comprender cómo funcionan los ecosistemas.

En el proceso de construcción de un modelo, simpflificamos la realidad y "quitamos" ciertas variables. Por ejemplo, un mapa es un modelo en el que la simplificación consiste en que el tamaño de los objetos no es el real. La capacidad explicativa de un modelo depende de este proceso de "reducción de la dimensionalidad".

Sin embargo, al mismo tiempo ocurre que un modelo es tanto mejor cuanto más ajustado está a la realidad. Eso genera un aparente dilema que se resuelve indicando que cuando construimos un modelo establecemos una relación simétrica con la realidad. La siguiente figura muestra esta situación. 

<img src="https://github.com/aprendiendo-cosas/P_vensim_depredacion_ecologia_ccaa/raw/main/imagenes/simetria.png" alt="simetria" style="zoom:50%;" />

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

## Pasos a dar
Durante la práctica usaremos Vensim para generar modelos de crecimiento poblacional dos especies en varias condiciones:
+ Empezamos generando un modelo de crecimiento poblacional del conejo. Veremos cómo al contemplar únicamente la tasa de natalidad natural del conejo, el número de individuos crece exponencialmente. Aquí puedes descargar el modelo para Vensim.
+ A continuación añadiremos depredadores, cuya natalidad está relacionada con la cantidad de conejos. Asimismo, la mortalidad de los conejos está condicionada por la cantidad de depredadores. En este caso se observa un proceso de regulación de las poblaciones de presa y depredador. Aquí puedes descargar el modelo para Vensim.
+ Por último analizaremos cómo se comportan las poblaciones de depredador y de presa si el crecimiento de este último está también condicionado por la competencia intraespecífica. Aquí puedes descargar el modelo para Vensim.

Para generar los modelos anteriores con Vensim puedes seguir los pasos que se muestran en este guión. 



## Vídeos de las sesiones



<iframe width="560" height="315" src="https://www.youtube.com/embed/n-IdN5qgRJY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
