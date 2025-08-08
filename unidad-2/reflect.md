# Unidad 2


## 🤔 Fase: Reflect

### Actividad 06

#### Autoevaluación
#### Mirando hacia adentro: autoevaluación de máquinas de estados y concurrencia

*El objetivo aquí es doble. Primero, que recuperes de tu memoria los conceptos de diseño y programación con máquinas de estados sin ayuda externa. Este esfuerzo por recordar (práctica de recuperación) es clave para un aprendizaje duradero. Segundo, que reflexiones sobre tu proceso de diseño y depuración, una habilidad esencial para cualquier ingeniero.*

📤 Bitácora

*En tu bitácora, sin consultar tu código, diagramas o notas, responde a las siguientes preguntas con tus propias palabras. Concéntrate en el esfuerzo de recordar, no en la perfección de la respuesta.*

Parte 1: recuperación de conocimiento (Retrieval Practice)

1. Describe con tus palabras qué es una máquina de estados. ¿Cuáles son sus cuatro componentes fundamentales que has utilizado en esta unidad?

No recuerdo exactamante que es una maquina de estados, de lo que he estado haciendo en las actividades, supongo que una forma para gestionar de mejor forma cada uno de los estados en el programa separandolos. Es decir, con el semaforo por ejemplo, tener 3 estados, cada uno representando cada color del semaforo. De los cuatro componentes tampoco me acuerdo, pero intuyo que son Eventos, Acciones, Estados y Transiciones.

2. Explica por qué la técnica de máquina de estados es tan útil para gestionar la “concurrencia” (atender un temporizador y botones “al mismo tiempo”) en un dispositivo con un solo hilo de ejecución como el micro:bit. ¿Qué problema soluciona en comparación con usar funciones como sleep()?

Facilita el rendimiento del programa para no sobre cargar una misma parte del codigo con varias lineas que por medio de cada estado por separado, permite que en cada estado pueda asignar si se pueden oprimir botones, agitar o etc, y nuevamente, no recuerdo que es una maquina de estados, lo que estoy diciendo es en base a lo que estoy intentando recordar, soluciona el tiempo de respuesta entre cada evento que haga el usuario.
  
3. Imagina que tienes que añadir una nueva funcionalidad a la bomba temporizada: si se agita (shake) el micro:bit mientras la cuenta regresiva está activa, el tiempo se reduce a la mitad. ¿Cómo modificarías tu diagrama de máquina de estados para incluir este nuevo evento y acción?

En mi codigo, en el estado STATE_COUNTDOWN añadiria lo siguiente, aunque solo si el contador fue puesto en 30 segundos, ya que no se como hacer que sea para todos los tiempos:

``` Python

if accelerometer.was_gesture():
time_stand -= 15

```
  
5. Explica qué es un “vector de prueba” y por qué es una herramienta crucial para verificar que una máquina de estados funciona como se espera.

Un vector de prueba es una forma de verificar el correcto funcionamiento de alguna parte del codigo. Para que un vector de prueba cumpla con lo necesario, debe tener lo siguiente: Condición incial (el estado actual donde este), Evento: (Lo que se debe realizar), Resultado esperado (Lo que se espera que pase al realizar el evento) y Resultado final (Lo que se obtuvo, si el vector pasa por el programa o no).
   
Parte 2: reflexión sobre tu proceso (Metacognición)

1. ¿Qué parte del diseño de la bomba temporizada te resultó más desafiante: crear el diagrama de estados (Actividad 04) o traducir ese diagrama a código MicroPython (Actividad 05)? ¿Por qué?

La parte más dificl fue hacer que el contador saliera en los LEDs del Micro:bit, no por el codigo, sino porque dependiendo si se muestra como "show" o "scroll" puede hacer que sea o más rapido o más lento la aparición de cada digito.
   
2. Describe un error o “bug” que encontraste al implementar tu programa. ¿Cómo te ayudó pensar en términos de estados, eventos y transiciones a identificar y solucionar el problema?

No se si se considere como un bug, pero si muestro el contador con "show" cuando los números son de dos digitos va reduciendo lento, pero cuando llega a números de un digito, va más lento. Dado a que no soy un experto con el tema del editor de Micro:bit, cambiarlo por scroll, aunque es más lento en ambos tipos de números, es más equilibrado, especialmente para que el evento en donde baje a 0 no se vuelva desbalanceado.
   
3. El problema de la bomba era complejo. ¿Qué estrategia usaste para abordarlo? ¿Comenzaste con una versión simple y añadiste funcionalidades poco a poco?

Primero tuve que pensar en cuantos estados habia en el programa, y despues ir uniendo cada estado con otro para saber como funcionaria, todo eso en un diagrama, y describi con palabras que hace cada acción y evento, para luego finalmente ir al editor de Micro:bit e ir escribiendo cada linea, aunque tambien me puse a experimentar con lineas como las de music para que la bomba fuera un poco más interesante (cuando aumenta o disminuye el tiempo, empieza la bomba, disminuye el contador y cuando explota).
   
4. Ahora que entiendes el patrón de máquina de estados, ¿En qué otro tipo de proyecto o sistema de entretenimiento digital crees que podrías aplicarlo?

Supongo que a videojuegos en algun nivel o modo especial, en el que se requiera un contador y dependiendo de las acciones del jugador.

### Actividad 07
#### Coevaluación
#### Aprendiendo juntos: coevaluación constructiva

*Diseñar y programar es solo una parte del trabajo de un ingeniero; analizar y dar feedback sobre el trabajo de otros es igualmente importante. En esta actividad, revisarás el diseño y la implementación de la bomba temporizada de un compañero para ayudarle a mejorar y para ganar una nueva perspectiva.*

📤 Bitácora

1. Encuentra a un compañero de trabajo.

2. Intercambien las URLs de sus bitácoras de aprendizaje.{

3. Revisa con atención las entradas de tu compañero para las Actividades 04 (diagrama de la bomba) y 05 (código y pruebas).
  
4. Analiza de manera crítica el diseño y la implementación de tu compañero y deja un comentario de retroalimentación específico y constructivo.
   
5. Conversa con tu compañero sobre su diseño y código, y discutan sus comentarios.
   
### Actividad 08
#### Feedback
#### Mejorando la experiencia: tu feedback es clave

*Mi objetivo es crear la mejor experiencia de aprendizaje posible, y tu perspectiva es esencial para lograrlo. Este es tu espacio para darme feedback honesto y directo sobre esta unidad, lo que me ayudará a refinarla para futuros estudiantes.*

📤 Bitácora

Responde a las siguientes preguntas con total sinceridad. ¡Cada comentario es valioso!

1. Continuar: ¿Qué actividad, explicación o ejemplo de esta unidad te ayudó más a entender el poder de las máquinas de estados? ¿Qué elemento consideras que es indispensable y debería mantener?

La acticidad 3 (la de los rostros en el LED) me ayudo bastante para comprender el uso de STATE_INIT y los estados que deben crearse dependiendo de lo que se requiera, y como tal, para mi es indispensable como el profe explico el funcionamiento de partes clave, especialmente con los eventos y acciones, ya que eso fue algo con lo que tambien he tenido dificultades para diferenciar.
   
2. Dejar de hacer: ¿Hubo algún paso o actividad que te pareció confuso, innecesariamente complicado o que aportó poco a tu aprendizaje? ¿Qué cambiarías o eliminarías?

Solamente complicada, la del semaforo, aunque fue más por una cuestión personal de que creia que se podia cambiar el color de los LEDs, pero no, y sobre cambiar o eliminar, no sabria que decir al respecto.
   
3. Empezar a hacer: ¿Qué te habría ayudado a entender mejor?

Es dificl, puesto que es muy subjetivo, con lo que ha estado dando el profe diria que es suficiente, aunque igual si tuviera que decir una (por mi parte), diria que un poco más de explicación con el tema de applies como el de esta unidad.
   
4. Ritmo y dificultad: En una escala del 1 (muy fácil) al 5 (muy difícil), ¿Cómo calificarías la dificultad de pasar del análisis de un programa (Actividad 03) al diseño desde cero de uno complejo (Actividad 04 y 05)? ¿Por qué?

3. Porque si bien, hay partes que son faciles de recordar y facilitan el proceso de diseño, hay otras que de plano involucran experimentar con lo que ofrece el editor de Micro:bit, repito, como dije antes, con lo de las lineas de musica para generar sonidos, fue algo interesante, aunque no haya sido solicitado por el profe (salvo el speaker al explotar).
   
5. Comentario adicional: ¿Hay algo más que te gustaría compartir sobre tu proceso de aprendizaje en esta unidad? ¿Algún momento de frustración o de “¡Aha!” que quieras destacar?
    
Todos los "¡Aha!" los dije cada que el codigo funcionaba o identificaba la cantidad de estados que tiene un programa, y con la frustración, el primer dia de la unidad estuve algo decaido emocionalmente, pero fue por que me habia olvidado de asistir a la clase anterior a esta el miercoles pasando aun estando en la U, por lo que en parte pienso que es por eso que no tengo tan fresco lo que es una maquina de estados.


