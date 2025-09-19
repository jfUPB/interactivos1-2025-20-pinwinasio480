# Evidencias de la unidad 5

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


R/ 

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


