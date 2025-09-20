
# Evidencias de la unidad 5

## Actividad 1

### Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?

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

NOTA: Mi principal pregunta mientras redactaba este ejercicio, es: ¿Como es posible determinar la cantidad de bytes por medio de los bits? tras una investigación para recordar, en base a lo que entiendo, cada 8 bits equivalen a un bit, entonces: 16 bits + 16 bits = 4 bytes; 8 bits + 8 bits = 2 bytes, y como resultado, ahi estarian los 6 bytes correspondientes.

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

Si por defecto yo asigno:


🧐🧪✍️ Captura el resultado del experimento. ¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario?

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 142742" src="https://github.com/user-attachments/assets/f09b6ed4-1506-4d34-bc95-2ae27e7429ff" />

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 142759" src="https://github.com/user-attachments/assets/76b6ed9a-e211-4a06-9562-f5e08a15eaac" />

Actividad 3

🧐🧪✍️ Explica por qué en la unidad anterior teníamos que enviar la información delimitada y además marcada con un salto de línea y ahora no es necesario.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b4731043-9dfa-4b0a-a8a8-02cd8948e4e0" />

Con lo anterior en mente, ahora vas a modificar el código de p5.js para leer los datos en formato binario. Sin embargo, al igual que con el código del micro:bit, te pediré que primero verifiquemos si los datos se están enviando correctamente.

///////////////////////////

CODIGO LARGO MODIFICADO

🧐🧪✍️ Compara el código de la unidad anterior relacionado con la recepción de los datos seriales que ves ahora. ¿Qué cambios observas?

Se elimina connectionInitialized = false

Y en lugar de que los datos lea hasta que \n, ahora lee los 6 bytes.

Ahora te voy a pedir que ejecutes el código de p5.js muchas veces y que estés muy atento a la consola. Lo que haremos es a tratar de reproducir un error que tiene este código. El error es de sincronización y se produce cuando los 6 bytes que lee el código de p5.js no corresponden a los mismos 6 bytes que envía el micro:bit.

![CAPTURAACTIVIDAD3](https://github.com/user-attachments/assets/b7fb22f0-8e29-4cf2-99ac-4a780772d370)

🧐🧪✍️ ¿Qué ves en la consola? ¿Por qué crees que se produce este error?

En la consola veo que esta en true el botón 'a', lo se debe a que no tengo el framing y eso genera que los datos no esten sincronizados, asi que tecnicamente es una señal fantasma si es que se le puede decir asi.

Para solucionar este tipo de problemas, es usual que los comunicaciones seriales implementen una estrategia de sincronización. La estrategia que vamos a usar se denomina framing y consiste en enviar un byte de inicio y un byte de fin del paquete.

//CODIGO DE PYTHON CON FRAMING
//LO MISMO CON P5


![Captura de pantalla 2025-09-17 545960](https://github.com/user-attachments/assets/3100f83d-698b-4693-bced-11826bf1bdee)


🧐🧪✍️ Analiza el código, observa los cambios. Ejecuta y luego observa la consola. ¿Qué ves?

*EXPLICACION DE CAMBIOS EN EL PROGRAMA* Y al reproducirlo, ahora ya no me sale que es true tanto el a pressed como el microbit activo, sino que solo el botón a.

La versión final de los programas de micro:bit y p5.js son las siguientes:

*CODIGO DE PYTHON + P5 NUEVO*

🧐🧪✍️ ¿Qué cambios tienen los programas y ¿Qué puedes observar en la consola del editor de p5.js?

*EXPLICACION DE AMBOS CODIGOS* Ya me deja controlar el programa con libertad como en la actividad 1 en lugar de que solo se oprima a.

![Captura de pantalla 2025-09-17 FINAL ACTIVIDAD 3](https://github.com/user-attachments/assets/3f5b2329-af29-4d05-b66e-8e9d0759d3ba)

Actividad 4

Vas a documentar en tu bitácora todo el proceso de construcción de la aplicación, mostrando las pruebas intermedias que hiciste, los errores que encontraste y cómo los solucionaste.

Primer error: no funciona el programa (python esta en binario y mi p5 no)
Prueba 2: Hice modificaciones sugeridad por Gemini modificando el p5.js, sigue sin funcionar

Vas a realizar múltiples experimentos analizando el comportamiento de la aplicación que construiste. Reporta el proceso de experimentación en la bitácora. Con estas evidencias debes demostrar que has comprendido los conceptos y técnicas vistas en esta unidad.












