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






