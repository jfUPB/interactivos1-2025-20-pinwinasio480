# Evidencias de la unidad 8

## Actividad 01

### En esta fase de la unidad vas a seleccionar un tema musical (o un concepto visual que desees explorar) que te guste y vas a definir el concepto de las visuales que quieres crear. Ten presente que estas visuales las controlarás en tiempo real desde un dispositivo móvil y el micro:bit.

#### *🧐🧪✍️ Reporta en tu bitácora*

#### - Documenta los referentes visuales que te inspiren.

![Vector de fondo de patrón de ecualizador rojo _ Vector gratuito](https://github.com/user-attachments/assets/028ae885-9dce-4769-9aee-45d368c39989)

![Base para rapear](https://github.com/user-attachments/assets/30c44406-03bf-4561-b866-2d35a9e784b0)

![Download Abstract Music Circle Equalizer Background for free](https://github.com/user-attachments/assets/1e83877e-b9b6-45af-a4a9-b6c5363ca64d)


#### - Define el concepto de las visuales que quieres crear.

El concepto de las visuales en cuestion, seria remotar algo similar a las de la unidad 7, es decir, un ecualizador lineal como el de los DJs que este sincronizado al ritmo de la cancion. En la unidad habia elegido colores como azul, rojo, morado y rosa. Aqui quiero hacerlo con colores rgb en general y con otra canción, talvez Untouchable - ITZY.

#### - Explica cómo el móvil y el micro:bit controlarán las visuales.

Desde el movil, con un circulo que aparece en la pantalla como en la unidad 7, puedo controlar el color de las visuales (es decir, dependiendo de la posición en mobile, cambiara el color del ecualizador), y por medio del micro:bit, si yo oprimo el botón 'a', si lo oprimo, el brillo del color de las visuales aumentara, disminuira o volvera a la original, y con el botón 'b', si lo mantengo oprimido, puedo las visuales pueden cambiar la saturación de las visuales, ya sea a color o hasta dejarlas blancas independientemente de donde se ponga el circulo.

#### - Haz un bocetos de todas las interfaces del sistema.

![Boceto programa Unidad 8 Samuel Gómez Espitia](https://github.com/user-attachments/assets/27bddfd1-baf5-43d7-a6ee-06b8dbbcafd4)

![Boceto programa Unidad 8 Samuel Gómez Espitia](https://github.com/user-attachments/assets/c4e98495-8c7c-4bba-a088-23450d63f528)

![Boceto programa Unidad 8 Samuel Gómez Espitia (1)](https://github.com/user-attachments/assets/91c8c588-5f8d-43c5-b404-8dcb0dc056cc)

![Boceto programa Unidad 8 Samuel Gómez Espitia (3)](https://github.com/user-attachments/assets/821de49d-e244-4fef-b13c-0806dcfedfe6)

#### - Haz un diagrama que explique cómo se comunicarán los diferentes componentes del sistema.

![Diagrama Unidad 8](https://github.com/user-attachments/assets/7a1f68d1-05a8-45af-8218-693ebf2be45a)

## Actividad 02

- Diseña una aplicación interactiva que use el touch del móvil para controlar una visuales de tema musical de tu elección. Las visuales correrán en una aplicación de escritorio (desktop). Recuerda que ambas aplicaciones las construirás usando p5.js y utilizando el servidor Node.js como puente.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/f943c1ed-441b-4f65-995f-42ba60999fd3" />

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


  
- Implementa tu diseño. Puedes usar IA generativa para ayudarte a escribir el código, pero primero debes hacer el diseño de lo que quieres.
  
- Incluye todos los códigos (servidor y clientes) en tu bitácora.

desktop (sketch.js):

```
let socket;
let circleX = 150;
let circleY = 200;

let song;
let fft;
const numBars = 32;

// Web Serial vars
let reader;
let keepReading = false;

// Visual control vars
let brillo = 200;        // 0 - 255
let saturacion = 100;    // 0 - 100
let saturacionHold = false;

function preload() {
  song = loadSound('music.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);

  // desbloqueo de audio por interacción
  userStartAudio();

  // FFT y asignación de input
  fft = new p5.FFT(0.8, numBars);
  fft.setInput(song);

  // Socket IO (mantengo la funcionalidad touch/mobile)
  socket = io();

socket.on('message', (data) => {
  if (data?.type === 'touch') {
    // Escalamos de nuevo las coordenadas normalizadas que vienen del móvil
    circleX = data.x * width;
    circleY = data.y * height;
  }
});
  socket.on('disconnect', () => console.log('⚠️ Desconectado del servidor'));

  // Botón para conectar micro:bit vía Web Serial
  const btn = createButton('Conectar micro:bit');
  btn.position(10, 10);
  btn.style('z-index', '10');
  btn.mousePressed(requestSerialPort);

  // Instrucción breve en pantalla (opcional)
  const hint = createP('Click canvas to start audio. Luego pulsa "Conectar micro:bit" y acepta el puerto en el navegador.');
  hint.position(10, 40);
  hint.style('color', '#ddd');
  hint.style('z-index', '10');
  hint.style('font-family', 'sans-serif');
  hint.style('font-size', '12px');
}

function draw() {
  background(0);

  // lectura FFT
  let spectrum = fft.analyze();

  // Color base dependiente del touch / posición del círculo
  colorMode(RGB);
  let r = map(circleY, 0, height, 255, 0);
  let g = map(circleX, 0, width, 0, 255);
  let b = map(circleY, 0, height, 0, 255);
  let rgbCol = color(r, g, b);

  // Convertir a HSB para manejar saturación y brillo
  colorMode(HSB, 360, 100, 255);
  let baseHue = hue(rgbCol);

  // Si hold de saturación está activo, desaturamos gradualmente
  if (saturacionHold) {
    saturacion = max(0, saturacion - 0.8); // ajuste de velocidad
  }

  let col = color(baseHue, saturacion, brillo);
  noStroke();
  fill(col);

  // Dibujar barras del ecualizador usando el color calculado
  let barWidth = width / numBars;
  for (let i = 0; i < numBars; i++) {
    let h = map(spectrum[i], 0, 255, 0, height);
    fill(col);
    rect(i * barWidth, height - h, barWidth - 2, h);
  }
}

function mousePressed() {
  // desbloqueo audio y start loop
  if (getAudioContext().state !== 'running') {
    getAudioContext().resume();
  }
  if (!song.isPlaying()) {
    song.loop();
  }
}

// -------------------- Web Serial funcs --------------------

async function requestSerialPort() {
  if (!('serial' in navigator)) {
    console.error('Web Serial API no soportada en este navegador.');
    return;
  }
  try {
    const port = await navigator.serial.requestPort();
    await port.open({ baudRate: 115200 });
    const decoder = new TextDecoderStream();
    port.readable.pipeTo(decoder.writable);
    const inputStream = decoder.readable;
    reader = inputStream.getReader();
    keepReading = true;
    readSerialLoop();
    console.log('Serial abierto con micro:bit');
  } catch (err) {
    console.error('Error abriendo puerto serial:', err);
  }
}

async function readSerialLoop() {
  while (keepReading) {
    try {
      const { value, done } = await reader.read();
      if (done) break;
      if (!value) continue;
      // puede venir múltiples líneas; procesar cada una
      value.split(/\r?\n/).forEach(line => {
        const cmd = line.trim();
        if (!cmd) return;
        handleMicrobitCommand(cmd);
      });
    } catch (err) {
      console.error('Error leyendo serial:', err);
      break;
    }
  }
}

// Mapear comandos del micro:bit a efectos visuales
function handleMicrobitCommand(cmd) {
  console.log('micro:bit ->', cmd);

  if (cmd === 'brillo_up') {
    brillo = Math.min(brillo + 40, 255);
  } else if (cmd === 'brillo_down') {
    brillo = Math.max(brillo - 40, 0);
  } else if (cmd === 'brillo_reset') {
    brillo = 200;
  } else if (cmd === 'saturacion_toggle') {
    saturacion = (saturacion === 100) ? 0 : 100;
  } else if (cmd === 'saturacion_hold_start') {
    saturacionHold = true;
  } else if (cmd === 'saturacion_hold_stop') {
    saturacionHold = false;
    saturacion = 100; // restaurar al soltar
  } else {
    // si llega otro texto, ignorar o usar para debug
    console.log('Comando no reconocido:', cmd);
  }
}

/*let socket;
let circleX = 150;
let circleY = 200;

let song;
let fft;
const numBars = 32;

function preload() {
  // Asegúrate de que song.mp3 esté en public/desktop/
  song = loadSound('music.mp3');
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
}*/

```

desktop (index.html):

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ecualizador Desktop</title>

  <!-- p5.js -->
  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/p5.min.js"></script>
  <!-- p5.sound -->
  <script src="https://cdn.jsdelivr.net/npm/p5@1.11.0/lib/addons/p5.sound.min.js"></script>
  <!-- Socket.IO -->
  <script src="https://cdn.socket.io/4.7.5/socket.io.min.js"></script>

  <style>
    body { margin: 0; overflow: hidden; background: black; touch-action: none; }
    canvas { display: block; }
  </style>
</head>
<body>
  <!-- canvas creado por p5 -->
  <script src="sketch.js" defer></script>
</body>
</html>

```
mobile (sketch.js):

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
    let normX = map(lastTouchX, 0, width, 0, 1);
    let normY = map(lastTouchY, 0, height, 0, 1);
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
 if (touches.length > 0) {
    let t = touches[0];
    let normX = t.x / width;   // valor entre 0 y 1
    let normY = t.y / height;  // valor entre 0 y 1

    // 🔹 Actualizar las variables para dibujar el círculo
    lastTouchX = t.x;
    lastTouchY = t.y;

    if (socket && socket.connected) {
      let touchData = {
        type: 'touch',
        x: normX,
        y: normY
      };
      socket.emit('message', touchData);
    }
  }
  return false;
}
```

mobile (index.html):

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

server.js:

```
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');

const app = express();
const server = http.createServer(app); 
const io = socketIO(server); 
const port = 3005;

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

Codigo Python:

```Python
from microbit import *

DEBOUNCE_MS = 200
HOLD_MS = 500

last_a = 0
last_b = 0
b_is_pressed = False
b_hold_sent = False
b_press_time = 0
last_heartbeat = 0

def send(msg):
    print(msg)
    sleep(20)

while True:
    now = running_time()

    # heartbeat cada 5s
    if now - last_heartbeat > 5000:
        send("hb")
        last_heartbeat = now

    # BOTÓN A
    if button_a.was_pressed():
        if now - last_a > DEBOUNCE_MS:
            send("brillo_up")
            last_a = now

    # BOTÓN B
    if button_b.is_pressed():
        if not b_is_pressed and (now - last_b > DEBOUNCE_MS):
            b_is_pressed = True
            b_press_time = now
            send("b_pressed")

        elif b_is_pressed and not b_hold_sent and (now - b_press_time >= HOLD_MS):
            send("saturacion_hold_start")
            b_hold_sent = True

    else:
        if b_is_pressed:
            if b_hold_sent:
                send("saturacion_hold_stop")
            else:
                send("saturacion_toggle")
            b_is_pressed = False
            b_hold_sent = False
            last_b = now

    sleep(10)
```

## Autoevaluación

Siguiendo la rubrica de esta última unidad, cumpli con la realización de todas las actividades de investigación (mostrar referencias, definir el concepto, explicar como funciona el mobile y micro:bit de forma resumida, mostrar conceptos del programa y el diagrama). No obstante, apesar de eso, el apply lo hice, pero la parte de micro:bit no funciona del todo bien, es debido a esto que esa actividad no queda valida. Por lo que mi nota final de esta unidad es 3.0. 










