# Evidencias de la unidad 5

## Bitacora Unidad 5 (Actividades 1, 2 y 3, para la autoevaluación)

### Actividad 1

Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?

La comunicación entre ambas partes se basa principalmente en como el micro:bit envia los datos al computador por medio del UART Serial (por lo que he estado investigando, es el hardware utilizado en los micro:bits), siendo Python el sensor y P5 la interfaz y pantalla por parte del usuario.

Pasando a los datos que se envian, los cuales son cuatro sensores del mismo micro:bit, cada mensaje contiene lo siguiente:

- xValue (Acelerometro en X)
- yValue (Acelerometro en Y)
- aState (estado True o False del botón 'a')
- bState (estado True o False del botón 'b')

Si vemos el código de Python proporcionado por el profesor, esto se encuentra en esta linea:

```Python

data = "{},{},{},{}\n".format(xValue, yValue, aState,bState)
uart.write(data)

```
Viendo esto, me he llegado a preguntar: Considerando que el micro:bit cuenta con más funciones como "Shake", "Speaker" o presionar el Pin (Touch) (no recuerdo con exactitud si las versiones que utilizamos en clase cuentan con esto último), alguno de los cuatro sensores que estan presentes en ASCII se pueden reemplazar con algunos de los que mencione? Me da curiosidad imaginar que fuese posible cambiar los mensajes de True y False de 'a' y 'b' por mensajes para indicar True o False de cuando se agita el micro:bit o se oprime el pin del mismo.

### ¿Cómo es la estructura del protocolo ASCII usado?

La estrucuta de ASCII se basa en mensajes de texto con formato CVS (es un tipo de extensión en donde los valores son separados por comas).

Si volvemos a revisar el codigo de Python:

```Python

<xValue>,<yValue>,<AState>,<BState>\n

```

Un ejemplo de como se pueden ver estos valores seria:

```Python

200, 100, True, False\n

```
Aquí nos indica que el valor de X esta en 200, el de Y en 100, que el botón 'a' esta oprimido pero el de 'b' no, y el "\n" al final es para indicar el fin del mensaje (esto vendria siendo framing, en las actividades posteriores se hara uso de framing).

### Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.

```JavaScript

if (port.availableBytes() > 0) {
  let data = port.readUntil("\n"); 
  if (data) {
    data = data.trim();            
    let values = data.split(",");  
    if (values.length == 4) {
      microBitX = int(values[0]) + windowWidth / 2;
      microBitY = int(values[1]) + windowHeight / 2;
      microBitAState = values[2].toLowerCase() === "true";
      microBitBState = values[3].toLowerCase() === "true";
      updateButtonStates(microBitAState, microBitBState);
    }
  }
}

```
Si vamos parte por parte, el 'let = data' pide al programa usar framing para leer los mensajes completos (como mencione anteriormente '\n' indica el final del mensaje, esto se refleja en: readUntil("\n")); data.trim() lo que hace es limpiar posibles espacios o saltos de líneas extras (en términos informales, sirve para no dejar cabos sueltos); data.split(",") convierte el string en un arreglo conformado por cuatro valores, que son los de los cuatro sensores, vuelvo a repetir, los acelerometros de X y Y y los estados de 'a' y 'b', nunca viene mal hacer un recordatorio. Ya pasando a la parte de conversión, int() es para las coordenadas del acelerómetro (números enteros); === "true" en microBitAState y microBitBState funciona para los estados de 'a' y 'b' para los True y False; y los ajustes de las coordenadas mencionados anteriormente +  windowWidth/2 y + windowHeight/2 se encargan de centrar los dibujos en la pantalla, como resultado, los datos del micro:bit se mapean a coordenadas y estados en p5.js.

### ¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?


```JavaScript

function updateButtonStates(newAState, newBState) {
  if (newAState === true && prevmicroBitAState === false) {
    lineModuleSize = random(50, 160);
    clickPosX = microBitX;
    clickPosY = microBitY;
    print("A pressed");
  }

  if (newBState === false && prevmicroBitBState === true) {
    c = color(random(255), random(255), random(255), random(80, 100));
    print("B released");
  }

  prevmicroBitAState = newAState;
  prevmicroBitBState = newBState;
}


```

Ambos eventos se generan de la misma manera, pero con diferentes funciones:

Si newAState pasa de false → true (cuando 'a' se presiona), se dibujaran líneas circulares que siguen el movimiento del micro:bit, o mejor dicho, el movimiento del acelerómetro. Y si newBState pasa de false → true (cuando 'b' se presiona), el color random de c correspondiente a las líneas cambiara. Cabe aclarar que mientras 'a' es Pressed, 'b' es Released, por lo que entiendo, Pressed es cuando se oprime, y Released es cuando se deja de oprimir el botón.

### Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.

<img width="1919" height="1069" alt="Captura de pantalla 2025-09-12 141342" src="https://github.com/user-attachments/assets/a1614e94-1dff-47f7-ab0d-d773d9e92173" />

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 141458" src="https://github.com/user-attachments/assets/71930c94-f176-4bfd-a1b9-ba7eb5bd0b65" />

## Actividad 2

*Abre la aplicación, configura el puerto, deja los valores por defecto y presiona Conectar. Selecciona el puerto del micro:bit (mbed Serial port) y presiona Conectar. Luego, en la sección de Recepción de Datos, en Mostrar datos como, selecciona Texto.*

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 141833" src="https://github.com/user-attachments/assets/07d42ea4-94f8-440b-a4f6-624c0a5f3ab7" />

### 🧐🧪✍️ Captura el resultado del experimento anterior. ¿Por qué se ve este resultado?

Dado a que no se un motivo exacto, y aqui le pedi a la inteligencia artificial que me explicara respecto al tema, en base a lo que entendi, esto se debe a que los datos que se estan mostrando están en binario y no en ASCII, cada mensaje ocupa 6 bytes (en formato 2h2B para indicar que se envian dos enteros cortos y dos enteros sin signo) que representan números y booleanos.

El UART (el hardware del micro:bit) interpreta cada byte como un carácter de texto en el modo del mismo nombre y dado a que la mayoría de los bytes no corresponden a códigos ASCII, como se puede apreciar en la captura de arriba, se pueden observar signos extraños con simbolo de pregunta como rombos negros o cuadros sin relleno y letras o caracteres aleatorios.

Y dado a que el no hay un control en Python en ese momento para regular cuando enviar cada dato, estos se enviaran en forma de bucle cada 100 ms (correspondientes a la cantidad de colocada en sleep como cooldown).

*Ahora cambia la opción de Mostrar datos como a Todo en Hex y vuelve a capturar el resultado.*

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 141919" src="https://github.com/user-attachments/assets/e5ff4fb2-e93e-4b07-a71e-384db056b992" />

### 🧐🧪✍️ Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código?

```Python

data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))

```

Tras cambiarlo al modo Hex, en el que ahora los datos se leen en hexadecimales, lo transmitido corresponde exactamente a la linea de código señalada, esto debido a que la instrucción empaqueta los valores de las variables en bloques binarios compuestos por dos enteros de 16 bits (los de xValue y yValue) y dos enteros de 6 bits (de aState y bState), lo que en total da como resultado 6 bytes. Por lo que en otras palabras, en modo texto (ejercicio anterior) mostrara carcateres y simbolos extraños dado a que muchos de los valores en binario no son legibles, pero al estar en modo hex, se mostraran los valores reales en la misma organización del formato >2h2B.

NOTA: Mi principal pregunta mientras redactaba este ejercicio, es: ¿Como es posible determinar la cantidad de bytes por medio de los bits? tras una investigación para recordar, en base a lo que entiendo, cada 8 bits equivalen a un byte, entonces: 16 bits + 16 bits = 4 bytes; 8 bits + 8 bits = 2 bytes, y como resultado, ahi estarian los 6 bytes correspondientes.

*No te parece que el resultado es un poco más difícil de leer que el texto en ASCII?*

### 🧐🧪✍️ ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?

Voy a ponerlo en cuadro para que quede más organizado:

|Ventajas|Desventajas|
| --- | --- |
|Cada paquete ocupa menos bytes (no es lo mismo 6 en binario a 10 o un poco más en ASCII)|A simple vista es dificl de leer (alguien que no tenga tanta experiencia se confundira para saber a que corresponde cada byte)|
|Los mensajes se envian con mayor rapidez|Si un byte se pierde o desordena, sera dificl saber donde esta el error|
|No hay caracteres extras en el formato|El micro:bit y p5 deben ponerse deacuerdo con el orden y tamaño de los datos|

*Ahora te voy a proponer un experimento que te permitirá ver mejor los datos.*

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 142200" src="https://github.com/user-attachments/assets/c507e7f4-9347-4000-ae41-4a839314291a" />

### 🧐🧪✍️ Captura el resultado del experimento. ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?

Al hacer el experimento, cuando se agita el micro:bit, además de que ya puedo tener el control de cuando enviar los datos en lugar de que se envien infinitamente, se puede apreciar mejor que se envian un total de 6 bytes. Con el formato >2h2B se relaciona porque en este formato se indica que: > manda en orden los bytes grandes primero, 2h son dos enteros cortos y 2B dos enteros sin signos, lo cual tiene sentido con lo que nos esta enviando en los mensajes, en los dos primeros bytes estan los valores de xValue, en el tercer y cuarto byte estan los valores de yValue, y en los últimos dos estan el True y False de 'a' y 'b' (el quinto byte es el de 'a' y el sexto es el de 'b', 01 indica True y 00 indica False).

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 142200" src="https://github.com/user-attachments/assets/c507e7f4-9347-4000-ae41-4a839314291a" />

🧐🧪✍️ Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?

Un ejemplo siendo xValue negativo (-100), yValue (200), aState True y bState False:

>2h2B

FF 9C   00 C8   01   00

🧐🧪✍️ Captura el resultado del experimento. ¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario?

Cuando agito el micro:bit, la forma en la que los datos son mostrados en la terminal cambia, en el modo HEX me muestra más de 20 bytes por cada Shake (lo más destacable es que cada '0a' indica como si fuera un punto seguido), inicialmente tuve mis dudas sobre porque ya no solo me mostraba 6 bytes, aunque por lo que tengo entendido hasta el momento, es porque primero se envia el paquete binario de 6 bytes de >2h2B, despues se envia una cadena ASCII "ASCII:\n" y posteriormente en texto CSV la representación de los mismos valores. Ya cuando fui al modo Texto, los 6 bytes aparecen como signos como rombos y cuadros con signo de pregunta, seguido de ASCII: y los valores legibles en texto como se puede apreciar en las imagenes de arriba

En cuanto a ventajas y desventajas:

|Ventajas de ASCII|Desventajas de ASCII|Ventajas de Binario|Desventajas de Binario|
| --- | --- | --- | --- |
|Es más facil de entender debido a que esta en texto los datos|Ocupa más espacio de datos como "-2040"|Ocupa menos espacio, solo se transmiten los 6 bytes necesarios|No es muy legible a primera vista|


<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 142742" src="https://github.com/user-attachments/assets/f09b6ed4-1506-4d34-bc95-2ae27e7429ff" />

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 142759" src="https://github.com/user-attachments/assets/76b6ed9a-e211-4a06-9562-f5e08a15eaac" />

### Actividad 3

🧐🧪✍️ Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b4731043-9dfa-4b0a-a8a8-02cd8948e4e0" />

En la unidad 4 teniamos que enviar los datos delimitados y marcados con un salto de línea (\n) porque los valores se enviaban como texto ASCII. Esto hacía que la aplicación dependiera del protocolo para saber dónde terminaba cada paquete, es decir, el salto de línea marcaba el fin del mensaje, que luego se leía con port.readUntil("\n").
En cambio, ahora la información se envía en formato binario, con paquetes de longitud fija, lo que permite que el receptor sepa exactamente cuántos bytes debe leer en cada transmisión. Gracias a esto, ya no es necesario incluir delimitadores ni saltos de línea.

🧐🧪✍️ Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?

En comparación con la unidad 4, ya no se utiliza connectionInitialized ni el port.clear(). Asi mismo, en lugar de leer los datos como texto delimitado por comas y terminado en \n usando port.readUntil("\n"), se leen directamente 6 bytes fijos con port.readBytes(6). Estos bytes se interpretan con un DataView, asignando 2 bytes a microBitX, 2 a microBitY y 1 a cada estado de los botones A y B. En consecuencia, ya no es necesario usar split(",") ni trim(), porque los paquetes llegan en binario con longitud fija.

🧐🧪✍️ ¿Qué ves en la consola? ¿Por qué crees que se produce este error?

![CAPTURAACTIVIDAD3](https://github.com/user-attachments/assets/b7fb22f0-8e29-4cf2-99ac-4a780772d370)

En la consola veo que aparece que el botón A está en true aunque no lo presioné. Tras preguntarle a la inteligencia artificial y en base a lo que recuerdo de la explicación del profesor, esto pasa porque los datos no están enmarcados (sin framing), lo que provoca que no haya sincronización entre el envío y la lectura. Como consecuencia, los bytes se interpretan de manera incorrecta y generan un valor falso (en este caso, en el botón 'a'). Para solucionar esto, se debe usar un protocolo de comunicación que incluya un byte de inicio y fin de paquete, de modo que los datos lleguen alineados y sin errores, lo que en pocas palabras, es la definición de framing.

🧐🧪✍️ Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves?

![Captura de pantalla 2025-09-17 545960](https://github.com/user-attachments/assets/3100f83d-698b-4693-bced-11826bf1bdee)

Tras hacer la modificación en el codigo de Python y P5, pude comparar como anteriormente aparecía en la consola que tanto "A pressed" como "Microbit ready to draw" estaban activos al mismo tiempo en true, aunque en realidad solo deberia estar activo el "A pressed". Después de los cambios realizados, el comportamiento se corrigió y ahora la consola muestra de forma más precisa los estados: únicamente "a pressed" aparece en true, mientras que "Microbit ready to draw" se mantiene en false. Esto ayuda debido a que la modificación permitió una lectura más clara y exacta de los valores enviados por el dispositivo y no causar mezclas como el error visto en la pregunta anterior.

🧐🧪✍️ ¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js?

![Captura de pantalla 2025-09-17 FINAL ACTIVIDAD 3](https://github.com/user-attachments/assets/3f5b2329-af29-4d05-b66e-8e9d0759d3ba)

En el programa de micro:bit nuevo, se modificó la forma de enviar los datos: antes se usaban valores fijos para X, Y y el estado de los botones, pero en la versión final se emplean directamente los valores del acelerómetro y los estados reales de los botones A y B. Por su parte, en el código de p5.js se cambió la manera de interpretar la posición, debido a que ahora los valores de X e Y se ajustan para dibujar en torno al centro de la pantalla en lugar de hacerlo solo en una esquina o mejor dicho, en una sola parte.

En la consola del editor de p5.js se puede observar que ya no solo se muestra el mensaje de “A pressed” como anteriormente con los estados en conjunto, sino que aparecera 'A pressed' y 'B pressed' + la cantidad de veces oprimidas de cada botón. Estos cambios en el código permiten un control más libre y dinámico de la interacción, parecido a la actividad 1 de esta misma unidad.

## Autoevaluación:

En base a lo que desarolle durante la unidad (y de paso en el reflect para poder mejorar mi nota en base a los criterios)a, acontinuación mencionare la nota que me coloco en cada parametro, asi como la sumatoria total:

| Criterios |  Inicial (0.0 - 1.9) | En desarrollo (2.0 - 3.4) | Logrado (3.5 - 4.4) | Excelente (4.5 - 5.0) | 
| --- | --- | --- | --- | --- | 
| 1. Profundidad de la Indagación | Las preguntas formuladas (o la falta de ellas) son superficiales y la exploración se limita a seguir las instrucciones sin cuestionar el “porqué” de las soluciones. | Se formulan preguntas relevantes, pero se enfocan principalmente en el “cómo” funcionan las partes del código (ej. “¿Cómo usar struct.pack?”). La indagación se centra en resolver problemas técnicos inmediatos. | Se formulan preguntas que comparan y contrastan los protocolos (ej. “¿Cuántos bytes ahorro realmente con el protocolo binario en mi caso específico?”). Se investiga la causa raíz de los errores (ej. “¿Por qué ocurre el error de sincronización?”). | Se formulan preguntas que exploran el diseño y sus implicaciones (ej. “¿Qué otras estrategias de framing existen y cuáles son sus ventajas?” o “¿En qué escenarios un protocolo ASCII podría ser preferible a uno binario, a pesar de su ineficiencia?”). La indagación demuestra una curiosidad por los principios de la comunicación de datos. | 
| 2. Calidad de la Experimentación | Los experimentos se limitan a la simple ejecución del código proporcionado o de las modificaciones indicadas, sin un análisis sistemático. | Se realizan los experimentos guiados y se utiliza la terminal serial o la consola de p5.js para observar los datos, pero sin un análisis profundo de lo observado. | Se diseñan y ejecutan experimentos deliberados y efectivos para verificar hipótesis o el funcionamiento de componentes específicos (ej. enviar valores conocidos para validar la lectura, provocar un error de checksum para verificar su manejo). | Se diseñan experimentos precisos y creativos que no solo verifican, sino que aíslan y demuestran la necesidad de ciertas soluciones o las sutilezas de la comunicación. Por ejemplo, se diseña un caso de prueba para reproducir de forma consistente el error de sincronización antes de implementar la solución de framing. |  
| 3. Análisis y Reflexión | La bitácora es un registro de acciones sin análisis. Se describe lo que se ve (ej. “salen caracteres raros en la terminal”) pero no se explica la causa. Las conclusiones son incorrectas o no están respaldadas por evidencia. | La bitácora describe los resultados, pero la reflexión es superficial. Se identifica el problema (ej. “los datos llegan mal”) pero no se articula claramente por qué una solución (como el framing) lo resuelve a nivel de bytes. | La bitácora conecta claramente la evidencia (capturas de la terminal, logs de la consola, depurador) con la explicación teórica. Se analiza por qué un protocolo sin framing es frágil y cómo la combinación de header y checksum aporta robustez. Se analizan los errores como parte del aprendizaje. | La bitácora demuestra una reflexión profunda que va más allá de la simple verificación. Se analiza el trade-off entre eficiencia de transmisión y complejidad de implementación, y se construye un modelo mental robusto del flujo de datos, desde el microcontrolador hasta la aplicación de p5.js. |  
| 4. Apropiación y Articulación de Conceptos | La bitácora muestra una definición incorrecta o copiada de los conceptos (ej. framing, checksum, DataView). No hay evidencia de comprensión personal. | La bitácora explica los conceptos de forma básica. Se entiende que el protocolo binario “es más rápido”, pero no se puede explicar por qué en términos de representación de datos o flujo de bytes. | La bitácora demuestra una comprensión clara y correcta de cada componente del protocolo. Se explica con palabras propias la función del header, del checksum, del DataView en JavaScript y del empaquetado con struct en MicroPython. | La bitácora demuestra una maestría conceptual. Se explican los conceptos como un sistema interdependiente. Se articula con total claridad y usando analogías propias por qué la comunicación serial es un flujo de bytes asíncrono y cómo un protocolo impone orden sobre ese “caos” para garantizar una comunicación fiable y eficiente. |  

### Calificaciones

#### 1. Profundidad de la Indagación

Nota: 5.0

*Se formulan preguntas que exploran el diseño y sus implicaciones*

Motivo: En la primera actividad, mientras redactaba la primera pregunta *Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?* no solo me limite a explicar como se hacia la comunicación entre ambas partes, sino que al final me pregunte si era posible reemplazar en el ASCII (cuando aparecen los 6 bytes) por ejemplos estados True y False de 'a' y 'b' con el de otras funciones del micro:bit como estados de shake o pin touch. Asi mismo, en la segunda actividad en la pregunta *Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código?*  mientras redactaba mi respuesta, comente que lo siguiente y cito *"¿Como es posible determinar la cantidad de bytes por medio de los bits? tras una investigación para recordar, en base a lo que entiendo, cada 8 bits equivalen a un byte, entonces: 16 bits + 16 bits = 4 bytes; 8 bits + 8 bits = 2 bytes, y como resultado, ahi estarian los 6 bytes correspondientes"*, o en otras palabras, me pregunte como uno determina la cantidad bytes con los bits, aunque al final tras sumar la cantidad de bits, me daba como resultado la cantidad de bytes.

### 🧐🧪✍️ Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código?

```Python

data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))

```

Tras cambiarlo al modo Hex, en el que ahora los datos se leen en hexadecimales, lo transmitido corresponde exactamente a la linea de código señalada, esto debido a que la instrucción empaqueta los valores de las variables en bloques binarios compuestos por dos enteros de 16 bits (los de xValue y yValue) y dos enteros de 6 bits (de aState y bState), lo que en total da como resultado 6 bytes. Por lo que en otras palabras, en modo texto (ejercicio anterior) mostrara carcateres y simbolos extraños dado a que muchos de los valores en binario no son legibles, pero al estar en modo hex, se mostraran los valores reales en la misma organización del formato >2h2B.

NOTA: Mi principal pregunta mientras redactaba este ejercicio, es: ¿Como es posible determinar la cantidad de bytes por medio de los bits? tras una investigación para recordar, en base a lo que entiendo, cada 8 bits equivalen a un bit, entonces: 16 bits + 16 bits = 4 bytes; 8 bits + 8 bits = 2 bytes, y como resultado, ahi estarian los 6 bytes correspondientes.


En Actividad 2 me pregunté: “¿Cómo es posible determinar la cantidad de bytes a partir de los bits?”.

Esto demuestra que no me limité a repetir lo dado, sino que busqué más allá.

#### 2. Calidad de la Experimentación

Nota: 5.0

*Se diseñan experimentos precisos y creativos que no solo verifican, sino que aíslan y demuestran la necesidad de ciertas soluciones o las sutilezas de la comunicación.*

Motivo:

Durante la actividad 2, logre por medio de los experimentos ver los datos en texto ASCII y HEX/Binario, no solo limitandome a probarlo asecas, sino que tambien lo comparaba con como cambiaba la interpretación de los bytes en ambas modalidades, además de destacar que en uno de los experimentos, al cambiar los datos a modo texto, me salian caracteres no legibles (simbolos como cuadrados con signos de pregunta) debido a que a diferencia del HEX, en modo texto los valores en binario no son legibles. Y en la tercera actividad, antes y despues de aplicar framing, pude ver los cambios en la consola, aunque no lo mencione en la bitacora, cuando me salia el error con el estado de 'a', probe en muchas ocasiones el programa como prueba y error para ver otros errores aparte, como el que se genere de forma extraña lo que dibuja el programa.

#### 3. Análisis y Reflexión

Nota: 5.0

Motivo: En Actividad 1 expliqué paso a paso cómo trim(), split() e int() transforman los datos en coordenadas.

En Actividad 3 analicé el error del botón A en true y lo conecté con el problema de framing.

En Actividad 2, armé tablas con ventajas y desventajas de ASCII vs binario, mostrando diferencias claras.

#### 4. Apropiación y Articulación de Conceptos

Nota: 5.0

Motivo: En Actividad 1 describí ASCII como formato CSV con delimitador y salto de línea como framing.

En Actividad 2 desglosé struct.pack('>2h2B') y expliqué qué representa cada símbolo y byte.

En Actividad 3 mostré cómo pasamos de texto variable con delimitadores a paquetes binarios fijos, lo que elimina la necesidad de \n.

Nota definitiva: 5.0


## REFLECT

### 1. En la unidad anterior abordaste la construcción de un protocolo ASCII. En esta unidad realizaste lo propio con un protocolo binario. Realiza una tabla donde compares, según la aplicación que modificaste en la fase de aplicación de ambas unidades, los siguientes aspectos: eficiencia, velocidad, facilidad, usos de recursos. Justifica con ejemplos concretos tomados de las aplicaciones modificadas.

R/ No me acuerdo de las comparaciones de los aspectos.

### 2. ¿Por qué fue necesario introducir framing en el protocolo binario?

R/ Para evitar que los datos se mezclen entre si y puedan ser separados. En la actividad 3, si mal no recuerdo, apicamos esto debido a que en le botón 'a' se estaba enviando una condición True que realmente no debia estar ahi.

### 3. ¿Cómo funciona el framing?

R/ El framing funciona enviando el datos al byte del inicio al byte del final para marcarlos.

### 4. ¿Qué es un carácter de sincronización?

R/ Supongo que es un carácter que me permite hacer que tanto el micro:bit como el p5 se puedan sincronizar de forma adecuada.

### 5. ¿Qué es el checksum y para qué sirve?

R/ La función cheksum si mal no recuerdo, sirve para verificar si los datos enviados no han sido alterado son diferentes.

### 6. En la función readSerialData() del programa en p5.js:

### - ¿Qué hace la función concat? ¿Por qué?

```Javascript

function readSerialData() {
    let available = port.availableBytes();
    if (available > 0) {
        let newData = port.readBytes(available);
        serialBuffer = serialBuffer.concat(newData);
    }

```

R/ De lo que recuerdo en relación a como funciona concatenar, se juntan los datos de serialBuffer con los de newData en un solo, esto lo digo en base a lo que recuerdo de la definición de concatenar (es muy probable que este equivocado), esto porque se unen dos datos en uno solo.

### - En la función readSerialData() tenemos un bucle que recorre el buffer solo si este tiene 8 o más bytes ¿Por qué?

```Javascript

  while (serialBuffer.length >= 8) {
    if (serialBuffer[0] !== 0xaa) {
      serialBuffer.shift();
      continue;
    }

```


R/  Por qué la cantidad de bytes por defecto es más corta.

### - En el código anterior qué significa 0xaa?

R/ Signfica el límite hasta el que serialBuffer debe leer los datos.

### - En el código anterior qué hace la función shift y la instrucción continue? ¿Por qué?


R/ No me acuerdo que hace Shift, pero pienso que continue hace que la operación del programa continue, esto si los valores de serialBuffer aun no son mayores o iguales a 8.


### - Si hay menos de 8 bytes qué hace la instrucción break? ¿Por qué?

```Javascript

    if (serialBuffer.length < 8) break;

```

R/ Porque maximo se pueden dar datos de 6 bytes, si se excede esa cantidad, se debe hacer el break como forma de decir "mira, aqui no puedes hacer más debido a que hay más de la cuenta".

### - ¿Cuál es la diferencia entre slice y splice? ¿Por qué se usa splice justo después de slice?

R/ Slice sirve para crear una copia de un arreglo mientras que Splice es la que puede modificar los arreglos, Splice va despues de Slice debido a que se necesita tener creado las copias de los arreglos primeros.

```Javascript

let packet = serialBuffer.slice(0, 8);
serialBuffer.splice(0, 8);

```

### - A la siguiente parte del código se le conoce como programación funcional ¿Cómo opera la función reduce?

```Javascript

    let computedChecksum = dataBytes.reduce((acc, val) => acc + val, 0) % 256;

```

R/ No me acuerdo su funcionamiento, supongo que lo que hace es que el valor de acc y val se reduce en base al porcentaje que se asigne (en este caso, 256%).

### - ¿Por qué se compara el checksum enviado con el calculado? ¿Para qué sirve esto?

```Javascript

if (computedChecksum !== receivedChecksum) {
    console.log("Checksum error in packet");
    continue;
}

```

R/ Para verificar que ambos datos son enviados de igual forma, es decir, esto sirve para verificar que la información recibida por ambas partes sea igual o no haya sido alterado.

### - En el código anterior qué hace la instrucción continue? ¿Por qué?

R/ Continua el proceso del programa.

### - ¿Qué es un DataView? ¿Para qué se usa?

```Javascript

let buffer = new Uint8Array(dataBytes).buffer;
let view = new DataView(buffer);

```

R/ No recuerdo bien su significado, a juzgar por el nombre, intuyo que tiene que ver con algo para poder ver los datos de las filas o columnas.

### - ¿Por qué es necesario hacer estas conversiones y no simplemente se toman tal cual los datos del buffer? 

```Javascript

    microBitX = view.getInt16(0) + windowWidth / 2;
    microBitY = view.getInt16(2) + windowHeight / 2;
    microBitAState = view.getUint8(4) === 1;
    microBitBState = view.getUint8(5) === 1;

```
R/ Para que los datos del acelerometro se pasen a coordenadas y que los estados de los botones 'a' y 'b' funcionen.

















