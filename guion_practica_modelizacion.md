# Modelización de las interacciones ecológicas. Desde el crecimiento exponencial hasta las relaciones interespecíficas

> + **_Tipo de material_**: <span style="display: inline-block; font-size: 12px; color: white; background-color: #4caf50; border-radius: 5px; padding: 5px; font-weight: bold;"> Prácticas</span> 
> + **_Versión_**: 2024-2025
> + **_Asignatura (grado)_**: Ecología (Ciencias ambientales). 
> + **_Autor_**: Curro Bonet-García (fjbonet@uco.es)
> + **_Duración_**: Una sesión de 1.5 horas en clase y otras 1.5 horas en casa.

![portada](https://raw.githubusercontent.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/main/imagenes/portada.png)

## Objetivos

Esta práctica tiene los siguientes objetivos:
+ Disciplinares:
  + Reforzar el conocimiento adquirido sobre los siguientes aspectos de poblaciones y comunidades:
    + Dinámicas poblacionales en ausencia de interacciones ecológicas (crecimiento exponencial).
    + Dinámicas poblacionales considerando la competencia intraespecífica (crecimiento logístico).
    + Relaciones entre depredadores y presas e implicaciones sobre sus dinámicas poblacionales.
    + Relaciones entre especies que compiten por los mismos recursos.
  + Consecuencias de las relaciones anteriores en el ensamblaje de comunidades reales.
  + Constatar el efecto de la retroalimentación negativa y positiva en las interacciones presa-depredador.
  + Constatar cómo la homeostasis es una propiedad emergente cuando interactúan presas y depredadores.
+ Instrumentales:

  + Aprender el concepto de modelo basado en procesos.
    + Concepto de variable de estado.
    + Concepto de parámetro de un modelo.
    + Conceptos de ejecución y lapso de tiempo.
  + Distinguirlos de los modelos espacialmente explícitos.
  + Conocer el funcionamiento de Vensim como herramienta para realizar modelos basados en procesos. 


## Contextualización ecológica

El contexto ecológico de esta práctica es el bloque de temas de teoría en los que abordamos la dinámica poblacional y las interacciones interespecíficas. En concreto, para entender bien lo que hacemos aquí deberás estar familiarizado con los siguientes temas:

+ [Aspectos generales sobre poblaciones ecológicas.](https://rawcdn.githack.com/aprendiendo-cosas/Te_poblaciones_ecologia_ccaa/main/guion_poblaciones_general.html)
+ [Competencia intraespecífica.](https://rawcdn.githack.com/aprendiendo-cosas/Te_poblaciones_comp_intra_ecologia_ccaa/main/guion_competencia_intraespecifica.html)
+ [Interacciones ecológicas. Depredación.](https://rawcdn.githack.com/aprendiendo-cosas/Te_depredacion_ecologia_ccaa/main/guion_depredacion.html) En clase vimos solo la parte "teórica" de este tema. En el guión tienes todo el material.
+ [Interacciones ecológicas. Competencia interespecífica](https://rawcdn.githack.com/aprendiendo-cosas/Te_comp_inter_ecologia_ccaa/main/guion_competencia_interespecifica.html). Competencia interespecífica. 



## Modelos basados en procesos

Los modelos son representaciones simplificadas de la realidad que nos ayudan a conocerla mejor. En nuestro caso los modelos ecológicos nos ayudan a comprender cómo funcionan los ecosistemas.

En el proceso de construcción de un modelo, simpflificamos la realidad y "quitamos" ciertas variables. Por ejemplo, un mapa es un modelo en el que la simplificación consiste en que el tamaño de los objetos no es el real. La capacidad explicativa de un modelo depende de este proceso de "reducción de la dimensionalidad".

Sin embargo, al mismo tiempo ocurre que un modelo es tanto mejor cuanto más ajustado está a la realidad. Eso genera un aparente dilema que se resuelve indicando que cuando construimos un modelo establecemos una relación simétrica con la realidad. La siguiente figura muestra esta situación. 

![modelo](https://raw.githubusercontent.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/main/imagenes/simetria.png)

Esta simetría tiene varias implicaciones a efectos prácticos:

+ Es muy importante que las variables que simulemos sean relevantes en la realidad. Por ejemplo, si queremos saber cómo cambia la evolución del número de conejos en función del número de linces, no tiene sentido que incorporemos a nuestro modelo el efecto de la dureza del suelo.

+ También es crítico establecer las relaciones entre las variables que queremos simular y la realidad. El establecimiento de este paralelismo es determinante. Si queremos simular cómo crece un árbol, debemos de, por ejemplo, definir cómo medimos ese crecimiento: altura, tamaño del tronco, etc.

+ Asimismo debe de haber un proceso de traducción de las preguntas que le hacemos a la realidad en preguntas que le formulamos al modelo. En el ejemplo anterior, evaluar cómo crece un árbol (pregunta a la realidad) se puede traducir en: ¿cómo cambia la altura de un árbol en función del clima? (pregunta al modelo).

+ Otra cuestión clave es la interpretación de los resultados obtenidos por un modelo. Éstos han de ser analizados críticamente, teniendo en cuenta el proceso de modelización y la información tomada para ejecutarlo. El hecho de que los resultados salgan de un modelo no indican que sean inherentemente correctos.

Usamos modelos todo el rato para interpretar la realidad a nuestro alrededor. Los mapas son ejemplos muy buenos de modelos. Pero el concepto de "asignatura" que usamos aquí también es un modelo. Usamos esta idea como una forma de aproximarnos a una realidad compleja que no comprendemos.

Hay muchos tipos de modelos diferentes, pero en nuestro caso, solo haremos referencia a dos tipos. 

+ Modelos espacialmente explícitos: entre las variables que se contemplan está el espacio. Estos modelos permiten simular cómo se distribuye en el espacio una o varias variables. Es decir, contemplan el espacio y sus dimensiones. Los SIG o los mapas son modelos espacialmente explícitos. 
+ Modelos temporalmente explícitos: En este caso los modelos tienen en cuenta el transcurrir del tiempo, así que nos permiten conocer cómo cambian las variables simuladas en el dominio del tiempo.  ¿Qué modelos temporalmente explícitos hemos visto muchas veces a lo largo de la asignatura?

En esta práctica utilizaremos modelos temporalmente explícitos. En dichos modelos los procesos ocurren en el eje del tiempo (y no en el del espacio). Eso hace que durante su ejecución veamos cómo cambia a lo largo del tiempo el valor numérico de una o varias variables importantes para la comunidad estudiada. Para entender la estructura de los modelos que vamos a usar, es necesario definir una serie de conceptos: 

+ Variables del modelo. 
  + Variables de estado. Cambian en cada ejecución del modelo en cada lapso de tiempo. Se refieren a los descriptores del sistema cuya variación a lo largo del tiempo nos interesa conocer. Por ejemplo:
    + 	Nº de presas en tiempo t
    + 	Nº de depredadores en tiempo t
    + 	En el software que utilizaremos  se usa una metáfora: el depósito. A más nivel del depósito, más alto es el valor numérico de la variable de estado.
  + Parámetros del modelo. Se mantienen constantes durante la ejecución del modelo. Podemos cambiarlos pero los valores que toman se aplican a toda la ejecución del modelo. Es decir, cambian de ejecución en ejecución.
    + 	Tasa de natalidad.
    + 	Tasa de mortalidad.
    + 	Número inicial de presas y depredadores.

+ Matemáticas subyacentes: ecuaciones diferenciales. Estas herramientas nos permiten cuantificar cómo cambian las variables de estado en cada diferencial de tiempo. 



## Software para construir modelos

Al igual que usamos los SIG para representar los cambios de ciertas variables ambientales en el domino del espacio, existen herramientas informáticas que nos permiten hacer lo mismo a lo largo del tiempo. Estas herramientas son las que usamos para generar modelos basados en procesos (la palabra proceso lleva implícita la componente temporal). En nuestro caso usaremos dos herramientas:
+ **Vensim** es una potente aplicación que permite simular multitud de situaciones de la realidad (no solo en el ámbito de la ecología, sino también en la ingeniería). Tiene una versión gratuita que puedes descargar [aquí ](https://vensim.com/free-download/#ple)(selecciona PLE y pon un correo. Te enviarán un mensaje con un enlace para descargar el instalable). Es una aplicación muy fácil de usar. Abajo tienes algunas pinceladas para iniciarte en su manejo:
  + [Este](https://youtu.be/itB3IBESny0) vídeo muestra gráficamente los principales elementos del programa. 
  + En [este](https://github.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/raw/main/descargables/instrucciones_vensim.pdf) documento (preparado por el profesor Diego Jordano Barbudo) puedes ver una descripción detallada de las principales herramientas que usaremos de Vensim. 
  
+ **Stella** es muy parecido al anterior, pero no dispone de versión gratuita. No lo vamos a usar directamente, pero veremos algunos ejemplos de modelos hechos con esta herramienta que están disponibles en internet. 



## Secuencia de acciones de la práctica

Durante esta práctica iremos comprobando cómo se "construye" una comunidad ecológica paso a paso. Utilizaremos una metáfora parecida a la que aplicamos cuando hicimos nuestra primera comunidad ecológica con [bolas de corcho](https://rawcdn.githack.com/aprendiendo-cosas/Te_comunidades_diversidad_ecologia_ccaa/2024_2025/guion_comunidades_diversidad.html). En este proceso iremos complicando la comunidad poco a poco. Partiremos de una población de una única especie que crece exponencialmente. Luego veremos cómo evoluciona esa población si añadimos competencia intraespecífica. Añadiremos más especies que interactúan de diferentes maneras: unas depredan a otras y unas compiten con otras. En todos los casos analizaremos mediante modelos de procesos cómo las interacciones modifican la dinámica poblacional. 

Además de lo anterior trataremos de evaluar cómo en este proceso cambia la "estabilidad" del sistema. Consideraremos que un sistema ecológico es tanto más estable cuanto menos cambian a lo largo del tiempo las abundancias de las poblaciones que lo constituyen. Las grandes oscilaciones en los números poblacionales suelen aumentar el riesgo de extinción de las poblaciones. Trataremos de evaluar de manera visual la estabilidad de las comunidades que simularemos en esta práctica.

En las siguientes secciones se muestran los distintos estados "evolutivos" de los modelos que iremos trabajando durante la práctica. Generaremos tres modelos con Vensim y experimentaremos con otros dos modelos creados también con Vensim que están disponibles en internet. Las dos siguientes figuras muestran de manera resumida los modelos que crearemos y con los que trabajaremos.



![modelos_vensim](https://raw.githubusercontent.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/2022-2023/imagenes/modelos_vensim.png)

![modelos_vensim](https://raw.githubusercontent.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/2022-2023/imagenes/experimentos.png)




## 1. Crecimiento exponencial de una población de conejos

En esta simulación veremos cómo crece una población sin ningún tipo de relación con el entorno. Aunque sabemos que esto no ocurre en realidad, tiene interés realizarla porque nos permite ver la magnitud de la idea de crecimiento exponencial. Cualquier entidad biológica que vive sin limitación crecerá exponencialmente. Esto ocurre solo en circunstancias en las que un organismo tiene a su disposición recursos ilimitados. 

Para construir el modelo empezamos haciendo lo siguiente:
1. En el menú "File" crea un nuevo modelo haciendo click en "New Model". eso abrirá una ventana con varias opciones. Completa las siguientes:
    + Initial time: 2000
    + Final time: 2040
    + Time step: indica la duración del lapso de tiempo mínimo que usa el modelo cuando se ejecuta. En nuestro caso usaremos 0.03125. Esto equivale a unos 10 días.
    + Units for time: Escribe "año".

2. Crear variable de estado ("level") llamada *Nº conejos*.

3. Creamos "tasa" llamada *Nacimientos conejos*. El punto de inicio debe de estar a la izquierda de la anterior y finaliza en *Nº conejos.*

4. Crear variable llamada *Tasa natalidad conejos*.

5. Creamos "tasa" llamada *Muertes conejos*. Empieza en *Nº conejos* y termina a su derecha.

6. Creamos variable llamada *Tasa mortalidad conejos*.

7. Mediante flechas conectamos los siguientes elementos:

      + *Tasa natalidad conejos* con *Nacimientos conejos*

      + *Nº conejos* con *Nacimientos conejos*.

      + *Nº conejos* con *Muertes conejos*.

      + *Tasa mortalidad conejos* con *Muertes conejos*.

8. Añadimos las siguientes ecuaciones (botón "equations"):

      + *Nacimientos conejos = Nº conejos \* Tasa de natalidad conejos*

      + *Nº conejos = Nacimientos conejos-Muertes conejos*. Número de inicial de conejos= 100

      + *Muertes conejos = Nº conejos \* Tasa mortalidad conejos*.

      + *Tasa natalidad conejos* = 2

      + *Tasa mortalidad conejos* = 0.02

9. Guarda el modelo y dale este nombre: *1_conejo_exponencial.mdl*. Puedes descargarlo [aquí](https://github.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/raw/main/descargables/1_conejo_exponencial.mdl.zip) si no has podido construirlo correctamente. 

10. Damos nombre a la ejecución: *conejo_exponencial_2_002* y la ejecutamos.

11. Al ver la gráfica con el resultado ¿Cómo de rápido crece el número de conejos?, ¿por qué da la sensación de que solo crece a partir del año 2036?, ¿Cuántos conejos hay en el año 2020?. Para contestar a esta última pregunta puedes ver la tabla de datos generada por el modelo. Para ello basta con seleccionar la variable de estado *Nº conejos* y luego el botón "Table".
12. Cambiamos la tasas de mortalidad del conejo: 0.05
13. Damos nombre a la ejecución: *conejo_exponencial_2_005* y la ejecutamos. Vemos la gráfica del número de conejos. ¿Qué diferencias hay entre las dos gráficas? ¿a qué se deben?



## 2. Crecimiento logístico de una población de conejos

Creamos un modelo de crecimiento logístico para el conejo. Contemplamos en este caso la competencia intraespecífica. Esto implica definir la capacidad de carga del sistema. Al contemplar este tipo de interacción veremos cómo el crecimiento exponencial pasa a ser logístico. Para ello hemos de crear y/o modificar los siguientes elementos del modelo ya existente:

1. Partiendo del modelo *1_conejo_exponencial.mdl* hacemos lo siguiente:
    1.1. Creamos variable *capacidad de carga* y le damos el valor de 2000 (usando el botón "equations").
    1.2. Conectamos esta nueva variable con *Nacimientos conejos*.
    1.3. Modificamos la ecuación de *Nacimientos conejos* para que incluya a la capacidad de carga: *Nº conejos \* Tasa de natalidad conejos \* (1-Nº conejos / Capacidad de carga)*.
  15. Guardamos el modelo con otro nombre (save as): *2_conejo_logistico.mdl*. Puedes descargarlo [aquí](https://github.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/raw/main/descargables/2_conejo_logistico.mdl.zip) si no has conseguido hacerlo. 
  15. Ahora cerramos vensim y, en el explorador de archivos, borramos todos los archivos que tengan extensión "vdfx". Esto hará que la gráfica que se crea con la nueva ejecución sea visible y no se solape con las que hemos hecho en los modelos anteriores.
  15. Damos nombre a la ejecución: *conejo_logistico_2_005* y la ejecutamos. Vemos la gráfica del número de conejos. ¿Qué ves? 



## 3. Comunidad con dos especies y depredación: linces depredando conejos y conejos creciendo exponencialmente (sin competencia intraespecífica)

1. Abrimos el modelo *1_conejo_exponencial.mdl*
2. Incorporalos los siguientes elementos: 
   2.1. Crear variable de estado ("level") llamada *Nº linces*.
   2.2. Creamos "tasa" llamada *Nacimientos linces*. El punto de inicio está a la izquierda de la anterior y finaliza en *Nº linces.*
3. Crear variable llamada *Tasa natalidad linces*
4. Creamos "tasa" llamada *Muertes linces*. Empieza en *Nº linces* y termina a su derecha.
5. Creamos variable llamada *Tasa mortalidad linces*.
6. Mediante flechas conectamos lo siguiente:
   + *Tasa natalidad linces* con *Nacimientos linces*
   + *Nº linces* con *Nacimientos linces*.
   + *Nº linces* con *Muertes linces*.
   + *Tasa mortalidad linces* con *Muertes linces*.
7. Añadimos las siguientes ecuaciones (botón "equations"):
   + *Nacimientos linces = Nº linces \* Tasa de natalidad linces*
   + *Nº linces = Nacimientos linces-Muertes linces*. Número de inicial de linces= 100
   + *Muertes linces = Nº linces \* Tasa mortalidad linces*.
   + *Tasa natalidad linces* = 0.01
   + *Tasa mortalidad linces* = 0.6
8. Además, debemos de relacionar las dinámicas poblacionales de ambas especies a través de la depredación. Lo veremos con más detalle en las sesiones de teoría, pero asumiremos que el número de linces afecta (negativamente) a la mortandad de los conejos y que el número de conejos afecta (positivamente) al nacimiento de los linces. En términos del modelo de Vensim, esto implica:

     + Añadir flecha desde *Nº conejos* hasta *Nacimientos linces*
     + Modificar la ecuación de *Nacimientos linces* así: *Nº linces \* Tasa de natalidad linces \* Nº conejos*
     + Añadir flecha desde *Nº linces* hasta *Muertes conejos"
     + Modificar la ecuación de *Muertes conejos* así: *Nº conejos \* Tasa mortalidad conejos \* Nº linces*
9. Guardamos el modelo con este nombre: *3_conejo_exponencial_lince.mdl*. Puedes descargarlo [aquí](https://github.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/raw/main/descargables/3_conejo_exponencial_lince.mdl.zip).
10. Nombramos la ejecución: *conejo_exp_lince* y la ejecutamos. Mostramos las gráficas de *Nº conejos* y *Nº linces* . ¿Cómo se interpretan las gráficas obtenidas? ¿qué diferencias ves respecto a las del modelo anterior?



## 4. Comunidad con dos especies y depredación: linces depredando conejos y conejos creciendo logísticamente (con competencia intraespecífica)

1. Partimos del modelo anterior (*3_conejo_exponencial_lince.mdl*) sobre el que incoraremos el "freno" provocado por la competencia intraespecífica: capacidad de carga del medio los conejos:
1.1.  Creamos variable *capacidad de carga conejos* y le damos el valor de 2000 (usando el botón "equations")
1.2. Conectamos esta nueva variable con *Nacimientos conejos*.
1.3. Modificamos la ecuación de *Nacimientos conejos* para que incluya a la capacidad de carga: *Nº conejos \* Tasa de natalidad conejos \* (1-Nº conejos / Capacidad de carga)*.
2. Damos nombre a la ejecución: *conejo_log_lince* y la ejecutamos. Vemos la gráfica del número de conejos y de linces. Puedes comparar los resultados de este modelo (con competencia intraespecífica para el conejo) con los del anterior (sin competencia intraespecífica). ¿cuál de las dos situaciones consideras que es más "estable"?
3. Guardamos este nuevo modelo: *4_conejo_logistico_lince.mdl*. Puedes descargarlo [aquí](https://github.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/raw/main/descargables/4_conejo_logistico_lince.mdl.zip).



## 5. Comunidad con tres especies, depredación y caza

El objetivo de este modelo es analizar cómo afecta a la dinámica de tres especies la extracción de ejemplares mediante la caza. La comunidad objetivo está formada por hierba, herbívoros y carnívoros. Las poblaciones de herbáceas están limtadas por la disponibilidad de agua (que no se puede controlar en el modelo). Las de herbívoros vienen controladas por las poblaciones de hierba. Y las de depredadores por las de presas. Esta ocasión no construiremos ningún modelo, sino que usaremos uno existente. Está disponible en [esta](https://exchange.iseesystems.com/public/creativelearningexchange/predator-prey-biomass-levelc/index.html#page1) web. Analizaremos las consecuencias que tiene la caza de depredadores y de presas en este sistema. Concretamente realizaremos los siguientes experimentos:
+ Ejecutar el modelo sin cazar presas ni depredadores. ¿qué dinámica se presenta al final?
+ Ejecutar el modelo extrayendo mediante caza un 10% de las presas anuales. ¿de qué forma afecta esto a la dinámica de las poblaciones?, ¿obtenemos una dinámica más o menos estable que antes?
+ Ahora ejecutamos el modelo extrayendo el 10% de los depredadores. ¿se produce un efecto parecido a lo observado más arriba?, ¿por qué?
+ A continuación ejecutamos el modelo de manera que cambiamos los parámetros cad 5 años. Intentamos generar más estabilidad en el sistema mediante la retirada de presas y de depredadores. 
+ Por último, ejecutamos el modelo teniendo en cuenta una serie de perturbaciones que ocurren el sistema de imprevisto. Veremos cómo aparecen sequías, enfermedades en las presas, etc. Además, los cazadores y habitantes de la zona nos irán avisando de sus necesidades. Debemos de trata de atenderlas intentando que las dinámicas poblacionales de las tres especies que conforman el modelo no se vean afectadas. 

## 6. Comunidad con dos especies que compiten entre sí y con un depredador. Concepto de nicho ecológico.

Aquí estudiaremos el impacto que tiene la competencia interespecífica en una comunidad de crustaceos en un ambiente intermareal. Usaremos un modelo disponible en [esta](http://virtualbiologylab.org/ModelsHTML5/BarnacleCompetition/BarnacleCompetitionModel.html) web. Para entender bien el proceso que ocurre en este ejemplo, debemos conocer también el concepto de nicho ecológico. [Este](https://es.khanacademy.org/science/ap-biology/ecology-ap/community-ecology/a/niches-competition) artículo de Khan Academy lo explica muy bien. 

Haremos los siguientes experimentos en el modelo anterior:
+ Eliminar *Chthamalus* del área superior. Ejecutar el modelo y anotar el resultado después de 50 días. ¿qué ocurre?, ¿reemplaza *Balanus* a la especie eliminada?, ¿Por qué?
+ Ahora elimina todos los *Balanus*. Ejecutar el modelo y anota el resultado después de 50 días. ¿qué ocurre? , ¿reemplaza *Chthalamalus* a *Balanus*?, ¿por qué?
+ Ahora añadiremos depredadores (*Thais*). ¿Qué ocurre transcurridos 50 días?, 
+ ¿Cuál de las dos especies estudiadas tiene un nicho realizado más grande?
+ Según hemos visto, ¿qué pasaría si eliminarámos todos los *Balanus* e impidiésemos su reprodución? ¿Y si hacemos lo mismo con "*Chthalamadus*".



## 7. Modelo de dinámica poblacional de los ecosistema de Sierra Nevada

Si has leído el guión hasta aquí y has hecho lo que en él se indica, te habrás familiarizado con el uso de Vensim. Desde un punto de vista de la ecología, habrás comprobado cómo las poblaciones de las especies estudiadas se hacen más estables conforme se van añadiendo interacciones interespecíficas.

Los modelos que hemos visto hasta ahora simulan en lapsos de tiempo pequeños cómo evolucionan las poblaciones de varias especies. Las ecuaciones matemáticas que rigen estos modelos son las que hemos visto en teoría y en prácticas: la exponencial, la logística, las que describen la depredación, etc. A partir de aquí la situación es diferente. 

En esta sección analizaremos cómo cambia la estructura de edades de una población a lo largo del tiempo. Trabajaremos con una única especie y veremos cómo, a lo largo del tiempo, va cambiando el número de jóvenes, organismos reproductores y organismos senescentes (viejos). Esto nos permitirá "animar" un histograma de tamaños o de edades de una población para saber cuál sería su comportamiento a lo largo del tiempo. Cuando estudiamos en teoría las pirámides poblacionales vimos cómo, por ejemplo, la estructura poblacional de México tenía más jóvenes que la de Suecia. Esto nos hizo pensar que el primer país tenía una demografía más "fuerte" y que encaraba el paso del tiempo con más probabilidad de supervivencia. 

El objetivo de esta actividad es simular cómo podría evolucionar una población determinada a partir de los datos mostrados en el histograma de frecuencias generado en la práctica correspondiente. Esto nos permitirá saber si le histograma obtenido en su momento corresponde con una población en equilibrio, que tiende a crecer o que está en declive. 

Para lograr este objetivo trabajaremos con un modelo de Vensim que tiene las siguientes variables de estado (Stocks):

+ Número de juveniles.
+ Número de reproductores.
+ Número de senescentes o viejos.

Se definen unas tasas de paso entre cada una de esas categorías. Además, cada categoría tiene una tasa de mortalidad concreta. Una última variable importante relacionada con la demografía de la población es la natalidad, que aplica únicamente a los juveniles (lógicamente). Por último, hay un factor externo que reduce la población de las tres clases de edad en un 30%. Esta perturbación externa ocurre solo una vez en un año a elegir por el usuario (el modelo se ejecuta de 2000 a 2100).

La siguiente imagen muestra la estructura del modelo en Vensim.

![modelo_estructura](https://raw.githubusercontent.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/main/imagenes/modelo_estructura_edades.png)






+ Objetivo: evaluar en qué medida el histograma que obtuvimos representa o no una dinámica poblacional estable
+ Descripción del modelo
+ Descripción de los parámetros que cambian en los distintos ecosistemas
+ Preguntas concretas para cada tipo de ecosistema











****
[Aquí](https://github.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/archive/refs/tags/2024_2025.zip) puedes descargar un archivo .zip que contiene este guión en formato html y todo el material que incluye.

****
Haz click [aquí](https://github.com/aprendiendo-cosas/P_modelizacion_interacciones_ecologia_ccaa/releases) para ver cómo ha cambiado este guión en los distintos cursos académicos.

****
 <p xmlns:cc="http://creativecommons.org/ns#" >El contenido de este repositorio se puede utilizar bajo la siguiente licencia:  <a  href="https://creativecommons.org/licenses/by-nc-sa/4.0/?ref=chooser-v1"  target="_blank" rel="license noopener noreferrer"  style="display:inline-block;">CC BY-NC-SA 4.0<img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"  alt=""><img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"  alt=""><img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/nc.svg?ref=chooser-v1"  alt=""><img  style="height:22px!important;margin-left:3px;vertical-align:text-bottom;"   src="https://mirrors.creativecommons.org/presskit/icons/sa.svg?ref=chooser-v1"  alt=""></a></p> 

<p>Esta licencia no aplica a enlaces a artículos, libros o imágenes no originales. Estos productos tienen su licencia correspondiente.</p>

