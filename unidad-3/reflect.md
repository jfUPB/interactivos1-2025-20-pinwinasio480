# Unidad 3


## 🤔 Fase: Reflect

# Unidad 3


## 🤔 Fase: Reflect

### Actividad 08

#### Autoevaluación

#### El objetivo aquí es doble. Primero, que recuperes de tu memoria los conceptos de diseño y programación con máquinas de estados sin ayuda externa. Este esfuerzo por recordar (práctica de recuperación) es clave para un aprendizaje duradero. Segundo, que reflexiones sobre tu proceso de diseño y depuración, una habilidad esencial para cualquier ingeniero.

#### 📤 Bitácora

#### En tu bitácora, sin consultar tu código, diagramas o notas, responde a las siguientes preguntas con us propias palabras. Concéntrate en el esfuerzo de recordar, no en la perfección de la respuesta.

#### Parte 1: recuperación de conocimiento (Retrieval Practice)

*1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?*

Al igual que la anterior unidad, no recuerdo exactamente lo que es. Si tuviera que decir una definición o una forma sobre que interpreto yo lo que es, es un sistema donde estan relacionados o conectados las entradas, salidas y transiciones. Tomando en cuenta los ejemplos que vimos en actividades previas (asi como los diagramas), supongo que los cuatro componentes fundamentales son: Estados, transiciones, eventos y acciones.

*2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender varios eventos y tareas “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit o en p5.js. ¿Qué problema soluciona en comparación con usar funciones como sleep()?*

Esta tecnica considero util para no saturar el programa con tantos requerimientos, es decir, que no se llegue a trabar o fallar en el momento en el que se haga más de una acción en un estado, por ejemplo, en esta unidad, fue de gran ayuda para que el programa recibiera correctamente la información tanto del micro:bit como de las teclas, ya sea para aumentar o disminuir el tiempo, otro detalle es que la maquina de estados hace que dichos eventos no esten forzosamente en todos los estados, sino en los que el usuario decida asignarlos, de esa forma uno evita en el caso de la bomba que el contador aumente el tiempo o disminuya el doble, lo cual hace que no haya que implementar cooldowns con el sleep en cada función.
   
*3. Imagina que tienes que añadir una nueva funcionalidad a la bomba: si se recibe un evento especial (por ejemplo, una combinación de botones o un comando serial) mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?*

Algo similar al codigo que puse en la contraseña, reconozco que en esta parte no tengo fresco como eexactamente se debe implementar, pero considero que si con la contraseña se coloco un acumulador (no se si sea el nombre más ideal para decirle en este contexto) provocaba que al oprimir 'A', 'B', 'A', me regresara a la configuración, aqui la "clave" seria que si oprimo la combinación 'B', 'A', 'B', si la bomba esta en 30 segundos, esta se reduzca a 15.
   
*4. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.*

Un vector de prueba es un procedimiento se realiza en programas o en otro contexto con el proposito de verificar el funcionamiento de determinada cosa. En el caso de esta unidad, en la actividad 5, hicimos uso de los vectores para verificar el funcionamiento de la bomba 3.0, en esta unidad recuerdo que era: Estado Inicial, Evento, Acción, Estado Final. 
Y en un programa de maquina de estados, es crucial cuando se requiere verificar que determinado evento y/o acción funcione en condiciones optimas, por poner un ejemplo y con temor a equivocarme:

| Estado Inicial | Evento | Acción | Estado final |
|----------------|----------------|----------------|----------------|
| CONFIG | Oprimir botón 'A' | Aumentar +1 el contador de la bomba | CONFIG |
   
#### Parte 2: reflexión sobre tu proceso (Metacognición)

*1. ¿Qué parte del diseño de la bomba te resultó más desafiante: crear el diagrama de estados o traducir ese diagrama a código? ¿Por qué?*

El diagrama se me hizo sencillo recordando el que hice la anterior unidad, el problema viene con traducir el código de Python a JavaScript, siendo honesto, tuve que usar Inteligencia Artificial en algunas partes de las dos actividades Apply debido a que me empecé a frustrar cuando comparaba códigos de P5.JS y Micro: bit Python no notaba diferencias a primera vista, eso no significa que absolutamente todo el código fue hecho con la IA, sino que también hubo partes en las que intentaba poner a prueba líneas de código o conceptos que hayamos visto previamente en las anteriores unidades, como es el caso de cuando se crea un Canva, y hacer que el if funcione cuando oprima un botón y haga la acción. Y donde reconozco que use más IA, fue en la actividad 7. No me gusta entregar cosas incompletas, y dado a que no tuve tiempo de hacer esta actividad en clase por estar estancado en la actividad 6, tuve que improvisar el código de P5.JS ya que si bien, hay conceptos que reconozco de unidades pasadas, hay otros que se kme hicieron nuevos o nos los recordaba del todo, y digo el de P5.JS, ya que con el de Python no se me hizo tan difícil pensar en como seria para controlarlo, puesto que ya habiamos hecho en la Unidad 1 un código muy similar, solo que en este caso ya no es solo cuando se oprime 'a' y 'b', sino que también se debe tomar en cuenta cuando se agita el micro:bit y cuando se oprime el botón de pin (no recuerdo si ese era el nombre exacto, pero es el que asignamos con la letra 't' para volver al estado de config estando en el estado exploded.
   
*2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?*

Hay un error, que hasta ahora no he podido solucionar, y no quise preguntarle a la IA, primero porque no quiero sobrepasarme con hacer trampa y segundo, porque quería intentar probar que otras opciones experimentar, aunque no pude solucionarlo. El problema en si, es con la contraseña, cuando oprimo la clave 'A', 'B', 'A', funciona, pero solo si las letras están en mayúsculas, ya que si las tengo en minúsculas, no servirá. Algo similar me paso cuando se aumenta y disminuye el contador, cuando se activa y cuando oprimo el pin, en donde se me había pasado declarar también las letras minúsculas y solo tenia las mayúsculas (key == 'A') || (key == 'a'). Por una parte, fue ahí que caí en cuenta que las mayúsculas y minúsculas en P5 se declaran por separado, y por el otro, mientras que con eso me funciono, con la contraseña no me funcionaba incluso haciendo este cambio.
   
*3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?*

Además de las explicaciones que dio el profesor sobre los cambios que se realizaron por ejemplo de la bomba 2.0 a 3.0, algo que podría decirse que me sirvió para recordar algunas líneas de código, fue revisar nuevamente algunas de actividades previas, tanto para comprobar el funcionamiento en esta unidad, como para recordar sus funcionamientos.
   
*4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?*

Ya había mencionado un ejemplo para algún evento de un videojuego en donde haya un contador, dado a que por la forma en el que hicimos las unidades, una posible forma es que en un videojuego donde haya eventos estilo contador, puedo hacer que en si se activa cierta contraseña, el jugador gana el evento y pasa al siguiente, de lo contrario, el jugador perderá y será un game over asegurado. 

### Actividad 09

#### Feedback

#### Mi objetivo es crear la mejor experiencia de aprendizaje posible, y tu perspectiva es esencial para lograrlo. Este es tu espacio para darme feedback honesto y directo sobre esta unidad, lo que me ayudará a refinarla para futuros estudiantes.

#### 📤 Bitácora

#### Responde a las siguientes preguntas con total sinceridad. ¡Cada comentario es valioso!

*1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?*

Las actividades de las bombas, y los cambios que se hicieron al pasar a la bomba 3.0, algunos elementos indispensables fueron el uso de más clases como es el caso de bombTask o el de radio.
   
*2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso? ¿Qué cambiarías o eliminarías?*

La actividad 6 y 7, debido a que se me hizo confuso el cambio de Python a P5, y más ya que intentaba ver que cambios había entre ambas versiones de códigos previos, y no podía ver las diferencias a primera vista.
   
*3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?*

Tener más ejemplos sobre que se puede modificar o cambiar al hacer la transición de un formato a otro (es decir, más ejemplos sobre que se debe modificar al pasar de Python a P5.JS).
   
*4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa a diseñar y programar uno complejo? ¿Por qué?*

4, más que todo porque lo que más se me complica, es hacer programación en P5, en Python me he podido defender con algunos conceptos que vimos en las dos unidades anteriores, pero en el caso de P5, entender que se debe modificar, quitar o agregar fue lo que se me hizo más caótico.
   
*5. Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?*

Algo que me gustaria comentar, es que se me hizo demasiado frustrante el hecho de que el Apply si o si requiriera un micro:bit fisico, ¿que es lo que tiene de malo? que solo teníamos una oportunidad de hacer la actividad 7, y tomando en cuenta de que uno puede demorarse demasiado tiempo resolviendo las actividades (algunas, no todas, como es el caso de esta Actividad 6), hace que el proceso de aprendizaje se vuelva frustrante. Y sobre cuando dije "¡Aha!", puedo mencionar cuando caí en cuenta de que en la actividad 7, el posible código que se podía usar en Python, era casi el mismo que uno que hicimos dos unidades atrás.

