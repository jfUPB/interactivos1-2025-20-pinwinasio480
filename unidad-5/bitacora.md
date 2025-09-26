# Evidencias de la unidad 5

## Lo me quedo pendiente por redacatar o responder de las actividades 2 y 3

### Actividad 2

🧐🧪✍️ Captura el resultado del experimento. ¿Qué diferencias ves entre los datos en ASCII y en binario? ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII? ¿Qué ventajas y desventajas ves en usar un formato ASCII en lugar de binario?

Cuando agito el micro:bit, la forma en la que los datos son mostrados en la terminal cambia, en el modo HEX me muestra más de 20 bytes por cada Shake (lo más destacable es que cada '0a' indica como si fuera un punto seguido), inicialmente tuve mis dudas sobre porque ya no solo me mostraba 6 bytes, aunque por lo que tengo entendido hasta el momento, es porque primero se envia el paquete binario de 6 bytes de >2h2B, despues se envia una cadena ASCII "ASCII:\n" y posteriormente en texto CSV la representación de los mismos valores. Ya cuando fui al modo Texto, los 6 bytes aparecen como signos como rombos y cuadros con signo de pregunta, seguido de ASCII: y los valores legibles en texto como se puede apreciar en las imagenes de arriba

En cuanto a ventajas y desventajas:

|Ventajas de ASCII|Desventajas de ASCII|Ventajas de Binario|Desventajas de Binario1
| --- | --- | --- | --- |
|Es más facil de entender debido a que esta en texto los datos|Ocupa más espacio de datos como "-2040"|Ocupa menos espacio, solo se transmiten los 6 bytes necesarios|No es muy legible a primera vista|

🧐🧪✍️ Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?

Un ejemplo siendo xValue negativo (-100), yValue (200), aState True y bState False:

>2h2B

FF 9C   00 C8   01   00

### Actividad 3


## Autoevaluación:

En base a lo que desarolle durante la unidad (y de paso en el reflect para poder mejorar mi nota en base a los criterios)w, acontinuación mencionare la nota que me coloco en cada parametro, asi como la sumatoria total:

| Criterios |  Inicial (0.0 - 1.9) | En desarrollo (2.0 - 3.4) | Logrado (3.5 - 4.4) | Excelente (4.5 - 5.0) | 
| --- | --- | --- | --- | --- | 
| 1. Profundidad de la Indagación | Las preguntas formuladas (o la falta de ellas) son superficiales y la exploración se limita a seguir las instrucciones sin cuestionar el “porqué” de las soluciones. | Se formulan preguntas relevantes, pero se enfocan principalmente en el “cómo” funcionan las partes del código (ej. “¿Cómo usar struct.pack?”). La indagación se centra en resolver problemas técnicos inmediatos. | Se formulan preguntas que comparan y contrastan los protocolos (ej. “¿Cuántos bytes ahorro realmente con el protocolo binario en mi caso específico?”). Se investiga la causa raíz de los errores (ej. “¿Por qué ocurre el error de sincronización?”). | Se formulan preguntas que exploran el diseño y sus implicaciones (ej. “¿Qué otras estrategias de framing existen y cuáles son sus ventajas?” o “¿En qué escenarios un protocolo ASCII podría ser preferible a uno binario, a pesar de su ineficiencia?”). La indagación demuestra una curiosidad por los principios de la comunicación de datos. | 
| 2. Calidad de la Experimentación | Los experimentos se limitan a la simple ejecución del código proporcionado o de las modificaciones indicadas, sin un análisis sistemático. | Se realizan los experimentos guiados y se utiliza la terminal serial o la consola de p5.js para observar los datos, pero sin un análisis profundo de lo observado. | Se diseñan y ejecutan experimentos deliberados y efectivos para verificar hipótesis o el funcionamiento de componentes específicos (ej. enviar valores conocidos para validar la lectura, provocar un error de checksum para verificar su manejo). | Se diseñan experimentos precisos y creativos que no solo verifican, sino que aíslan y demuestran la necesidad de ciertas soluciones o las sutilezas de la comunicación. Por ejemplo, se diseña un caso de prueba para reproducir de forma consistente el error de sincronización antes de implementar la solución de framing. |  
| 3. Análisis y Reflexión | La bitácora es un registro de acciones sin análisis. Se describe lo que se ve (ej. “salen caracteres raros en la terminal”) pero no se explica la causa. Las conclusiones son incorrectas o no están respaldadas por evidencia. | La bitácora describe los resultados, pero la reflexión es superficial. Se identifica el problema (ej. “los datos llegan mal”) pero no se articula claramente por qué una solución (como el framing) lo resuelve a nivel de bytes. | La bitácora conecta claramente la evidencia (capturas de la terminal, logs de la consola, depurador) con la explicación teórica. Se analiza por qué un protocolo sin framing es frágil y cómo la combinación de header y checksum aporta robustez. Se analizan los errores como parte del aprendizaje. | La bitácora demuestra una reflexión profunda que va más allá de la simple verificación. Se analiza el trade-off entre eficiencia de transmisión y complejidad de implementación, y se construye un modelo mental robusto del flujo de datos, desde el microcontrolador hasta la aplicación de p5.js. |  
| 4. Apropiación y Articulación de Conceptos | La bitácora muestra una definición incorrecta o copiada de los conceptos (ej. framing, checksum, DataView). No hay evidencia de comprensión personal. | La bitácora explica los conceptos de forma básica. Se entiende que el protocolo binario “es más rápido”, pero no se puede explicar por qué en términos de representación de datos o flujo de bytes. | La bitácora demuestra una comprensión clara y correcta de cada componente del protocolo. Se explica con palabras propias la función del header, del checksum, del DataView en JavaScript y del empaquetado con struct en MicroPython. | La bitácora demuestra una maestría conceptual. Se explican los conceptos como un sistema interdependiente. Se articula con total claridad y usando analogías propias por qué la comunicación serial es un flujo de bytes asíncrono y cómo un protocolo impone orden sobre ese “caos” para garantizar una comunicación fiable y eficiente. |  

### Calificaciones

#### 1. Profundidad de la Indagación

Nota: 4.4

Motivo: En la primera actividad, al inicio cuando se me pregunto cómo funciona la comunicación entre el micro:bit y el sketch de p5.js, considerado que funciones del micro:bit como el acelerómetro X y Y, junto a los estados ‘a’ y ‘b’ de los botones usan los 6 bytes, me hice la pregunta acerca de sí era posible reemplazar esas funciones para que en el quinto o sexto byte me salga un true o false de ‘shake’ o Pin (Touch). 

Además, en la actividad 2, mientras redacta los ejercicios, me hice la pregunta sobre cómo era posible determinar la cantidad de bytes por medio de los bits, y luego de investigar, debido a que era un concepto que no tenía del todo fresco, destaque el como cada 8 bits equivalen a un byte (en la bitácora puse un bit, pero fue un error de ortografía), e hice la suma de 16 + 16 bits (32) equivalen a 4 bytes del acelerómetro X y Y, y que 16 bytes (de 8 + 8) daban como resultado 2 bytes, correspondientes a ‘a’ y ‘b’ con sus estados True y False.


#### 2. Calidad de la Experimentación

Nota: 4.2

Motivo: En cada una de las 3 actividades realice los experimentos, en cada una adjunte los procesos que conllevaron por medio de capturas de pantalla, incluso en la actividad 2 no solo me limite a mirar lo que me salía en la terminal, sino que cuando se me preguntó “¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?” decidí agitar unas cuantas veces el micro:bit y mostrarlos en las capturas para confirmar hipótesis personales en relación a los estados del microbit y valores, más que todo referente a los estados de los botones ‘a’ y ‘b’, en donde yo mencione y citó “El quinto byte es el de 'a' y el sexto es el de 'b', 01 indica True y 00 indica False”.

#### 3. Análisis y Reflexión

Nota: 3.4

Motivo: En la actividad 3 durante un error de código que solicitaba reproducir el programa de p5 varias veces (y cito, para no alargar tanto explicando el codigo, *"se elimino connectionInitialized = false
y en lugar de que los datos lea hasta \n, ahora lee los 6 bytes"*), podía observar en la consola un estado true del botón ‘a’ que no debería aparecer, mencione que se debía a que al no tener el framing, provoca que los datos no están sincronizados, incluso lo relacione con una señal fantasma, debido a que está ahí, pero no debería estar (en la imagen de la bitacora, este error aparecia afuera de Micro:Bit ready to draw, aclaro que me coloco esta nota ya que no termine de ahondar en otros analisis como los que pedian, especialmente relacionados a Checksum.

#### 4. Apropiación y Articulación de Conceptos

Nota: 4.2

La bitácora demuestra una comprensión clara y correcta de cada componente del protocolo. Se explica con palabras propias la función del header, del checksum, del DataView en JavaScript y del empaquetado con struct en MicroPython.

Motivo:


Nota definitiva: 4.05 (4.0)


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









