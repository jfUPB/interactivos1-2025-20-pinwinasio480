# Evidencias de la unidad 7

# *NOTA: La carpeta la nombre Unidad6Samuel por error, realmente estamos en la unidad 7, para aclarar.*

## Actividad 1

### *🧐🧪✍️ Reporta en tu bitácora*

### - ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?

![WhatsApp Image 2025-10-10 at 2 18 09 PM](https://github.com/user-attachments/assets/0ff521ef-c77e-48ad-a76a-f1e44f4e42b4)

R/ https://szk7c3zl-3000.use2.devtunnels.ms/

Porque con esta URL ya se esta esppecificando el puerto al que se esta escuchando, además de que con este tipo de enlaces, al final debe modificar con desktop o mobile dependiendo del dispositivo al que se conecte.

### - Describe brevemente qué hace npm install y npm start.

<img width="1600" height="899" alt="image" src="https://github.com/user-attachments/assets/7e9d1b3b-26e7-41b1-bebc-9509bc3bf748" />

<img width="848" height="199" alt="image" src="https://github.com/user-attachments/assets/af18dc35-0e5a-4804-9e68-42cbdebcbebd" />

R/ npm install en este caso descarga 88 paquetes de los cuales 89 fueron auditados y 14 son gratuitos (sus programadores buscan financiación). Y npm start nos indica que ya inicio el repositorio que estamos usando, que el git se conecto al servidor .js y nos dice el puerto en el que se esta escuchando el servidor, en este caso, en el puerto 3000.

### - ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/0b9646ae-939c-4713-b1a3-7f4a240d59e3" />

<img width="1912" height="1079" alt="image" src="https://github.com/user-attachments/assets/e7b65219-ba70-40bf-b1d6-ac1fd983b2f7" />

R/ Los mensajes son iguales. "New client connected", sin importar cual de los dos se conecte, siempre saldra el mismo mensaje, incluso cuando se desconectan ("Client disconnected")..

### - Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?

https://github.com/user-attachments/assets/b4e9d121-7932-43ec-8caf-f6a0d559bd50

R/ Afortunadamente la interración fue un exito, no hubo retrasos a nivel de fps, salvo un segundo al inicio cuando movia el circulo por primera vez, pero tras moverlos de forma recta tanto en horizontal como vertical y hacer movimientos circulares, no detecte retrasos en el movimiento.

## Actividad 2

### *🧐🧪✍️ Reporta en tu bitácora*

### - Explica con tus propias palabras: ¿Por qué es necesario Dev Tunnels en este escenario y cómo funciona conceptualmente?

R/ DevTunnels es necesario porque permite que el servidor que se ejecuta localmente en mi computador (localhost) pueda ser accesible desde mi celular, incluso si no están en la misma red o si la red bloquea conexiones externas. Conceptualmente, DevTunnels crea un túnel seguro entre mi servidor local y una URL pública temporal, de modo que cualquier dispositivo pueda conectarse a esa dirección y comunicarse con mi servidor como si estuviera en Internet.

### - Describe la función de touchMoved() y por qué se usa la variable threshold en el cliente móvil.

R/ touchMoved() se encarga de llamar o detectar los movimientos de X y Y que haga el usuario, threshold() en el cliente móvil se usar para verificar si el último movimiento supera el umbral, esto con el fin de evitar la saturación de mensajes cuando este minimamente temblando el dispositivo o haya movimientos fanstama (movimientos que según el programa pasan, pero realmente no suceden).

### - Compara brevemente Dev Tunnels con simplemente usar la IP local. ¿Cuáles son las ventajas y desventajas de cada uno?

R/ Dev Tunnels: Permite acceder al servidor desde cualquier lugar sin estar en la misma red, es más seguro y no necesita configuraciones adicionales, aunque puede ser un poco más lento.

IP local: Es más rápido porque la conexión es directa, pero solo funciona si el celular y el computador están conectados a la misma red WiFi, y puede requerir ajustes en el firewall o red.

### - Coloca en tu bitácora capturas de pantalla del sistema completo funcionando. Esto lo puedes hacer abriendo tanto el mobile como el desktop en tu computador y tomando una captura de pantalla de todos los involucrados (celular, computador y terminal).

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/4651ac6f-8b0b-4aa9-ab76-0337233150ac" />

<img width="1916" height="1079" alt="image" src="https://github.com/user-attachments/assets/e78fcafc-7e35-4800-add1-5ac4902a4248" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/28ed818b-e63e-42d3-aa00-5b72d4a1143f" />

https://github.com/user-attachments/assets/2a0abf67-604e-492e-8360-ab7633822d28

## Actividad 3

### *🧐🧪✍️ Reporta en tu bitácora*

### ¿Cuál es la función principal de express.static(‘public’) en este servidor? ¿Cómo se compara con el uso de app.get(‘/ruta’, …) del servidor de la Unidad 6?

R/ express.static('public') permite que el servidor sirva automáticamente todos los archivos que se encuentren en la carpeta public (por ejemplo, HTML, CSS, JS, imágenes, etc.), sin necesidad de definir rutas específicas.
En cambio, en la Unidad 6 se utilizaban rutas manuales con app.get('/page1', ...) o app.get('/page2', ...), donde cada una debía enviar un archivo concreto.

### Explica detalladamente el flujo de un mensaje táctil: ¿Qué evento lo envía desde el móvil? ¿Qué evento lo recibe el servidor? ¿Qué hace el servidor con él? ¿Qué evento lo envía el servidor al escritorio? ¿Por qué se usa socket.broadcast.emit en lugar de io.emit o socket.emit en este caso?

R/ En el cliente móvil, el evento touchMoved() detecta el movimiento del dedo y envía las coordenadas (x, y) al servidor mediante socket.emit('message', touchData). El servidor recibe ese mensaje con socket.on('message', (message) => { ... }). Luego, el servidor retransmite el mensaje a los demás clientes conectados (por ejemplo, el cliente de escritorio) usando socket.broadcast.emit('message', message).
En el cliente de escritorio, se recibe con socket.on('message', (data) => { ... }), donde se puede usar esa información para mover un objeto en pantalla o mostrar el resultado. Se usa socket.broadcast.emit porque este método envía el mensaje a todos los clientes excepto al que lo originó (el móvil), evitando que el dispositivo que envió el mensaje lo reciba de nuevo.

### Si conectaras dos computadores de escritorio y un móvil a este servidor, y movieras el dedo en el móvil, ¿Quién recibiría el mensaje retransmitido por el servidor? ¿Por qué?

R/ El mensaje sería recibido por los dos computadores de escritorio, pero no por el móvil que lo envió. Esto ocurre porque el servidor utiliza socket.broadcast.emit, el cual envía los datos a todos los clientes conectados excepto al emisor. De este modo, el móvil no recibe su propio mensaje de vuelta, evitando duplicar la información o generar comportamientos erróneos.

### ¿Qué información útil te proporcionan los mensajes console.log en el servidor durante la ejecución?

R/ Los console.log del servidor permiten monitorear en tiempo real el comportamiento del sistema. Por ejemplo:

- Muestran cuándo se conecta o desconecta un cliente, lo que ayuda a verificar si el servidor está recibiendo conexiones correctamente.
- Permiten ver los datos enviados por el cliente (Received message => ...), confirmando que el mensaje táctil llegó correctamente.
- En conjunto, estos registros sirven para depurar, probar y validar la comunicación entre los distintos clientes y el servidor.

## Actividad 4

### *🧐🧪✍️ Reporta en tu bitácora*

### Realiza un diagrama donde muestres el flujo completo de datos y eventos entre los tres componentes: móvil, servidor y escritorio. Puedes ilustrar con un ejemplo de coordenadas táctiles (x, y) y cómo viajan a través del sistema.

<img width="1080" height="1920" alt="mobilesketch js" src="https://github.com/user-attachments/assets/f3445b77-bb04-4ecc-868f-67e683feb742" />

## Actividad: APPLY

### *🧐🧪✍️ Reporta en tu bitácora*

### Diseña una aplicación interactiva que use el touch del móvil para controlar una visuales de tema musical de tu elección. Las visuales correrán en una aplicación de escritorio (desktop). Recuerda que ambas aplicaciones las construirás usando p5.js y utilizando el servidor Node.js como puente.

*Primera idea (DESCARTADA) Mi idea aqui es hacer una especie de visual de ecualizador radial. En el desktop se vera el ecualizador radial con fondo negro, y desde el celular, se puede mover el ecualizador, dependiendo de la posicion este sera mas o menos potente el ecualizador, asi mismo, influira el color, como si fuera RGB, en una parte es roja, arriba es naranja, derecha verde, abajo azul, izquierda morado, naranja arriba, etc. La canción seria de electronica o Dupsted, estilo NCS, para que el ritmo quede más acople.*

IDEA FINAL: En la pantalla Desktop habrá un ecualizador como los de los DJs en un fondo negro, dicho ecualizador estará al ritmo de la canción Desmeon - Undone de NCS, con mobile puedes cambiar el color de las visuales del ecualizador moviendo el dedo con el touch, mientras más arriba será rojo, derecha rosado, azul abajo y cian izquierda.

Nota: Hasta ahora me funciona el mobile, pero no el desktop.

### Implementa tu diseño. Puedes usar IA generativa para ayudarte a escribir el código, pero primero debes hacer el diseño de lo que quieres.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/29cab1d6-06ea-4d8f-b986-f9aa5c101a23" />

### Incluye todos los códigos (servidor y clientes) en tu bitácora.

### Desktop

Index.html:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ecualizador Desktop</title>

<!-- p5.js -->
<script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
<!-- p5.sound.js -->
<script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/addons/p5.sound.min.js"></script>
<!-- Socket.IO -->
<script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>
<!-- Tu sketch -->
<script src="sketch.js" defer></script>

  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: black;
      touch-action: none;
    }

    canvas {
      display: block;
    }
  </style>
</head>
<body>
</body>
</html>

```

Sketch.js:
```
let socket;
let circleX = 150;
let circleY = 200;

let song;
let fft;
const numBars = 32;

function preload() {
  // Asegúrate de que song.mp3 esté en public/desktop/
  song = loadSound('song.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);

  // Requiere interacción para iniciar audio en navegadores modernos
  userStartAudio();

  fft = new p5.FFT(0.8, numBars);

  socket = io();

  socket.on('connect', () => console.log('✅ Conectado al servidor'));

  socket.on('message', (data) => {
    console.log("📨 Datos recibidos:", data);
    if (data?.type === 'touch') {
      circleX = data.x;
      circleY = data.y;
    }
  });

  socket.on('disconnect', () => console.log('⚠️ Desconectado del servidor'));
}

function draw() {
  background(0);

  // Verifica si el audio está sonando
  console.log("🎵 ¿Está sonando?", song.isPlaying());

  let spectrum = fft.analyze();

  // Color reactivo al input del móvil
  let r = map(circleY, 0, height, 255, 0);
  let g = map(circleX, 0, width, 0, 255);
  let b = map(circleY, 0, height, 0, 255);
  let col = color(r, g, b);

  noStroke();
  fill(col);

  // Dibujar barras del ecualizador
  let barWidth = width / numBars;
  for (let i = 0; i < numBars; i++) {
    let h = map(spectrum[i], 0, 255, 0, height);
    rect(i * barWidth, height - h, barWidth - 2, h);
  }
}

function mousePressed() {
  console.log("🖱️ mousePressed activado");

  // Forzar desbloqueo del contexto de audio
  if (getAudioContext().state !== 'running') {
    getAudioContext().resume();
  }

  // Iniciar la música si no está sonando
  if (!song.isPlaying()) {
    song.loop();
  }
}

/*let socket;
let circleX = 200;
let circleY = 200;
const port = 3000;

function setup() {
    createCanvas(300, 400);
    background(220);
    socket = io(); 

    socket.on('connect', () => {
        console.log('Connected to server');
    });

    socket.on('message', (data) => {
        console.log(`Received message:`, data);
        if (data && data.type === 'touch') {
            circleX = data.x;
            circleY = data.y;
        }
    });    

    socket.on('disconnect', () => {
        console.log('Disconnected from server');
    });

    socket.on('connect_error', (error) => {
        console.error('Socket.IO error:', error);
    });
}

function draw() {
    background(220);
    fill(255, 0, 0);
    ellipse(circleX, circleY, 50, 50);
}*/


```

### Mobile

Index.html:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mobile Visualizer Control</title>

  <!-- p5.js -->
  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>

  <!-- Socket.IO -->
  <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>

  <!-- Script del móvil -->
  <script src="sketch.js" defer></script>

  <style>
    body {
      margin: 0;
      overflow: hidden;
      touch-action: none;
      background: black;
    }

    canvas {
      display: block;
    }
  </style>
</head>
<body>
</body>
</html>

```

Sketch.js:
```
let socket;
let lastTouchX = null;
let lastTouchY = null;
const threshold = 5;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  socket = io();

  socket.on('connect', () => {
    console.log('Connected to server');
  });

  socket.on('disconnect', () => {
    console.log('Disconnected from server');
  });

  socket.on('connect_error', (error) => {
    console.error('Socket.IO error:', error);
  });
}

function draw() {
  background(0);

  if (lastTouchX !== null && lastTouchY !== null) {
    let r = map(lastTouchY, 0, height, 255, 0);
    let g = map(lastTouchX, 0, width, 0, 255);
    let b = map(lastTouchY, 0, height, 0, 255);
    fill(r, g, b);
    noStroke();
    ellipse(lastTouchX, lastTouchY, 50, 50);
  }

  fill(255);
  textAlign(CENTER, CENTER);
  textSize(18);
  text('Move your finger to change colors', width / 2, height - 30);
}

function touchMoved() {
  if (socket && socket.connected) {
    let dx = abs(mouseX - lastTouchX);
    let dy = abs(mouseY - lastTouchY);

    if (dx > threshold || dy > threshold || lastTouchX === null) {
      let touchData = {
        type: 'touch',
        x: mouseX,
        y: mouseY
      };
      socket.emit('message', touchData);

      lastTouchX = mouseX;
      lastTouchY = mouseY;
    }
  }
  return false;
}

/*let socket;
let lastTouchX = null; 
let lastTouchY = null; 
const threshold = 5;

function setup() {
    createCanvas(300, 400);
    background(220);
    socket = io();

    socket.on('connect', () => {
        console.log('Connected to server');
    });

    socket.on('message', (data) => {
        console.log(`Received message: ${data}`);
    });

    socket.on('disconnect', () => {
        console.log('Disconnected from server');
    });

    socket.on('connect_error', (error) => {
        console.error('Socket.IO error:', error);
    });
}

function draw() {
    background(220);
    fill(255, 128, 0);
    textAlign(CENTER, CENTER);
    textSize(24);
    text('Touch to move the circle', width / 2, height / 2);
}

function touchMoved() {
    if (socket && socket.connected) { 
        let dx = abs(mouseX - lastTouchX);
        let dy = abs(mouseY - lastTouchY);

        if (dx > threshold || dy > threshold || lastTouchX === null) {
            let touchData = {
                type: 'touch',
                x: mouseX,
                y: mouseY
            };
            socket.emit('message', touchData);

            lastTouchX = mouseX;
            lastTouchY = mouseY;
        }
    }
    return false;
}*/

```

### Server.js

```
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3006;

app.use(express.static('public'));

io.on('connection', (socket) => {
    console.log('New client connected');
    socket.on('message', (message) => {
        console.log('Received message =>', message);
        socket.broadcast.emit('message', message);
    });

    socket.on('disconnect', () => {
        console.log('Client disconnected');
    });
});

server.listen(port, () => {
    console.log(`Server is listening on http://localhost:${port}`);
});
```

## Autoevaluación

Para el momento en el que hago la autoevaluación, he cumplido con todos los ejercicios y puntos de la investigación (incluso en algunos mostrando capturas y videos del procedimiento y diagrama). Lo cual equivale a 3.0. No obstante, en el apply tengo escrita el diseño de mi programa de visuales, en caso de que solo sea escrito, esto me suma hasta 3.66 (3.7). En caso de que no suba nada más, es porque estoy teniendo dificultades con el código, especialmente porque aveces los prompts que le doy a la IA no funcionan o no concuerdan con mi idea del todo.

PD: El 3.66 viene de que el apply cuesta 2,0, y si dividimos el 100% de este apply, que en total son 3 puntos, cada punto seria de 33.33%.

3.0 de las actividades de investigación + 2.0 * 0,33 da como resultado 0.66, por lo que 3.0 + 0.66 = 3.66 (3.7). En caso de que la descripción del diseño no sea valida y que no haya subido código funcional, la nota final queda en 3.0.

ACTUALIZACIÓN: Ya logre hacer el código funcional, si el profe valida lo que voy a presentar, mi nota final es 5.0, ya que aparte de cumplir con las investigaciones, tambien cumpli con el apply.






