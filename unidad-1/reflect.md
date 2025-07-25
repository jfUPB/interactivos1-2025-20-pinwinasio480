# Unidad 1

## 🤔 Fase: Reflect

### Actividad 7

### Parte 1: recuperación de conocimiento (Retrieval Practice) 

*Basándote en los ejemplos que vimos de sistemas físicos interactivos al iniciar el curso, describe las tres características que definen a un sistema físico interactivo.*

Las tres caracteristicas que recuerdo que debe tener un sistema físico interactivo es: Contar con Input y Output; se basa en la interración del usuario con el software al accionar los inputs; facilita al usuario crear productos y prototipos en menos tiempo.

*Explica el modelo input-process-output de Patrick Hübner usando como ejemplo el sistema que construiste con micro:bit y p5.js en la Actividad 06. ¿Cuál fue el input, cuál fue el proceso y cuál fue el output?*

Siendo honesto, no recuerdo como es el input-process-output de Hübner, aunque en relación a lo demás (no se si sea valido), recuerdo que el input de la actividad 6 era el boton que se oprimiera y la información serial; el output era el boton de ConnectToMicro:bit/Disconnect y lo visual; y en el proceso, el sistema se encargaba de detectar si el usuario oprimio ese botón, pintando el cuadrado de color rojo, de lo contrario, el cuadrado se pintaba de verde (se representaba con 'A' al oprimir boton indicado, al hacer algo contrario, era señalado como 'N'.

*¿Cuál es la función de la línea uart.write('A') en el código del micro:bit y qué función en p5.js se encarga de “escuchar” ese mensaje?*

Su funcion era mostrarle al usuario el botón oprimido (en este caso, la tecla 'A'), con respecto a la función en p5.js, no recuerdo cual era.

*¿Cuál es la diferencia fundamental entre el arte/diseño tradicional y el arte/diseño generativo?*

El arte tradicional, como su nombre lo indica, es más inclinado a realizar obras y otro tipos de arte manualmente, mientras que en el arte generativo, el usuario hace uso de sistemas, algoritmos, programas, codigo y etc con el fin realizar obras de forma más dinamica y unica, el ejemplo que recuerdo de clase es el Plotter, que permitia replicar un mismo cuadro pero con variaciones para darle diferencias.

*Imagina que quieres que un círculo en p5.js cambie a un color aleatorio cada vez que sacudes el micro:bit. Describe qué tendrías que programar en el micro:bit y qué tendrías que programar en p5.js para lograrlo.*

Con este punto tampoco se como responder, si hablamos de usar cosas como if, que es lo más obvio, 

*Parte 2: reflexión sobre tu proceso (Metacognición)*

*¿Qué fue más desafiante para ti en esta unidad: la parte conceptual (entender qué es un sistema físico interactivo) o la parte técnica (hacer que el micro:bit y p5.js se comunicaran)? ¿Por qué?*

La parte tecnica fue la que más me dio dificultad, especialmente al tratarse de recordar y escribir codigo, porque en la parte conceptual, apesar de que tengo algunas falencias, se me hizo más facil de comprender y guardarlo en mi memoria ligeramente a largo plazo.

*Describe el momento “¡Aha!” que tuviste cuando lograste que una acción en el micro:bit (presionar un botón, sacudirlo) tuviera un efecto visible en el canvas de p5.js por primera vez. ¿Qué fue lo que entendiste en ese instante?*

Fue bastante satisfactorio, y lo digo enserio, aun conservo las fotos y videos en mi celular de como me funcino el codigo en el p5.js, y eso que al inicio tenia miedo por que crei que era muchisimo más dificil de lo que parecia, en cuanto a que entendi, es que incluso en aparatos como un micro:chip, y con algo de codigo, se puede llevar a cabo un sistema fisico interactivo sencillo, como dicen por ahi: menos es más.

*Al inicio de la unidad te pregunté: “¿Este curso para qué me sirve?”. Después de experimentar y construir tu primer prototipo, ¿Cómo ha cambiado o se ha vuelto más concreta tu respuesta a esa pregunta?*

Digamos que cambio mi forma de ver el curso dando un giro de 180 grados, porque al entrar aqui, tenia la mentalidad de que esto solo aplicaba para la linea de Experiencias Interactivas, no obstante, tras ver los ejemplos dados por el profe, asi como haber construido mi primer prototipo, logre comprender mejor que este curso es bastante util para cualquiera de los tres enfasis, claro, siempre y cuando el usuario sepa usar codigo.

*El tutorial de la Actividad 05 te llevó paso a paso. ¿Cómo te sentiste con ese método de aprendizaje? ¿Te dio seguridad o preferirías haberlo intentado por tu cuenta desde el principio?*

Personalmente, no importa el contexto, siempre prefiero tener una guia paso a paso como el de esa actividad si se trata de enfrentarse a algo de lo que nunca he hecho o no estoy tan enterado. En cierto modo, me dio bastante seguridad mientras lo iba desarollando, pero eso no cambia que al inicio me abrumara por la cantidad de pasos que tenia, porque tan solo ver la cantidad de pasos, creia que era algo que podia tardar hasta una semana completa, es más cosa de que aveces los nervios me hacen imaginar que sera muy complicado.

### Actividad 8

*Encuentra un compañero de trabajo.*

Valentina Garzón.

*Intercambien las URLs de sus bitácoras de aprendizaje.*

[Bitacora de Valentina Garzón (la que revise)](https://github.com/jfUPB/interactivos1-2025-20-Valengp2006/blob/unidad1/apply/unidad-1/apply.md)

*Concéntrate en la Actividad 06: control de movimiento con micro:bit de tu compañero. Lee su código (Python y JavaScript).*

Codigo de ella de JavaScript

```
let port;
let connectBtn;
let connectionInitialized = false;
let x = 100;

function setup() {
  createCanvas(400, 400);
  background(220);
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(80, 300);
  connectBtn.mousePressed(connectBtnClick);
}

function draw() {
  background(220);

  if (port.opened() && !connectionInitialized) {
    port.clear();
    connectionInitialized = true;
  }

  if (port.availableBytes() > 0) {
    let dataRx = port.read(1);
    if (dataRx == "A") {
      x -= 10;
    } else if (dataRx == "B") {
      x += 10;
    }
  }

  ellipseMode(CENTER);
  fill("red");
  ellipse(x, height / 2, 50, 50);

  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
  } else {
    connectBtn.html("Disconnect");
  }
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}

Codigo de Python:

```Python

from microbit import *

uart.init(baudrate=115200)
display.show(Image.SILLY)

while True:
    if button_a.is_pressed():
        uart.write('A')
    if button_b.is_pressed():
        uart.write('B')
```

*Tu compañero resolvió el problema de manera diferente a ti, qué hizo diferente, qué aprendiste de su solución. En tu bitácora documenta lo anterior y escribe, como si le estuvieras explicando, lo que tú hiciste y por qué es diferente a lo que hizo tu compañero.*



### Actividad 9

*Continuar: ¿Qué actividad, video o ejemplo de esta unidad te resultó más inspirador o te ayudó más a entender el potencial de los sistemas físicos interactivos?*

Los que mencione en mi Actividad 1, el de Mario Kart Home Circuit y el de ProCreate, fue lo que hizo que entendiera que el potencial de los sistemas fisicos interactivos no solo se limita a las experiencias interactivas, sino tambien a los videojuegos y la animación digital, asi como ejemplos como el del logo de musica de Luxemburgo (no recuerdo el nombre exacto) que permitia hacer el mismo logo pero con ondas de sonido (no se como se dice jeje) que se mueven al mismo tiempo que el ritmo y musica que toque el artista.

*Dejar de hacer: ¿Hubo alguna parte que te pareció demasiado abstracta, muy rápida o confusa? ¿Hay algo que crees que podríamos cambiar para que sea más claro?*

Es más cosa personal mia, pero lo que más me parecio confuso es la comprensión de que cosa es un Input y que es un Output dentro de un determinado sistema fisico interactivo, repito, esto es más problema mio, el profesor no tiene la culpa. Y sobre que se podria cambiar...honestamente no se que decir.

*Empezar a hacer: ¿Qué te genera más curiosidad ahora? ¿Te gustaría explorar más sensores del micro:bit (luz, temperatura), crear visualizaciones más complejas en p5.js o ver más ejemplos de proyectos artísticos?*

No me habia planteado esa pregunta previamente, pero leyendo el enunciado, si me gustaria explorar que más hace el micro:bit, aunque con lo de visualizaciones complejas...me llama tambien la atención, especialmente porque algunos ejemplo que vi me recordaban a esas pantallas de congelado de Windows XP con tuvos que iban avanzando, algo que de niño si me llegaba a dar curiosidad.

*Balance inspiración vs. técnica: ¿Cómo sentiste el equilibrio entre ver los videos inspiradores de la Actividad 01 y la parte técnica de conectar las herramientas en las actividades 03-06?*

Se me hizo bastante equilibrado, si la intención de los videos era darnos una introducción al curso de forma creativa con ejemplos creativos en la actividad 01, y ya en las actividades 03-06 enseñarnos a como poner en practica un sistema desde cero de forma simple, le doy bastante merito al profesor.

*Comentario adicional: ¿Hay algo más que quieras compartir sobre tu experiencia en esta unidad introductoria?*

La verdad...no, generalmente no suelo ser de muchas palabras (salvo cuando estoy inspirado de más)...bueno, rectifico, si hay algo que me gustaria compartir, y es que hasta ahora, tenia mis dudas y temores (que sigo teniendo en algunos casos porque seguramnte en las proximas unidades la dificultad ira aumentando), pero gracias a lo vivido en la Unidad 1, me dio razones para que este curso comenzara a gustarme (no digo que antes no me gustara, sino que tenia mis dudas).

