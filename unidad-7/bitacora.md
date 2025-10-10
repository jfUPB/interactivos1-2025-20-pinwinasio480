# Evidencias de la unidad 7

## 🧐🧪✍️ Reporta en tu bitácora

## *NOTA: La carpeta la nombre Unidad6Samuel por error, realmente estamos en la unidad 7, para aclarar.*
### ¿Qué URL de Dev Tunnels obtuviste? ¿Por qué crees que necesitamos usar esta URL en lugar de http://localhost:3000 o la IP local de tu computador para que el celular se conecte?

R/ https://szk7c3zl-3000.use2.devtunnels.ms/

<img width="1600" height="899" alt="image" src="https://github.com/user-attachments/assets/7e9d1b3b-26e7-41b1-bebc-9509bc3bf748" />

<img width="848" height="199" alt="image" src="https://github.com/user-attachments/assets/af18dc35-0e5a-4804-9e68-42cbdebcbebd" />

Porque con esta URL ya se esta esppecificando el puerto al que se esta escuchando, además de que con este tipo de enlaces, al final debe modificar con desktop o mobile dependiendo del dispositivo al que se conecte.

### Describe brevemente qué hace npm install y npm start.

R/ npm install en este caso descarga 88 paquetes de los cuales 89 fueron auditados y 14 son gratuitos (sus programadores buscan financiación). Y npm start nos indica que ya inicio el repositorio que estamos usando, que el git se conecto al servidor .js y nos dice el puerto en el que se esta escuchando el servidor, en este caso, en el puerto 3000.

### ¿Qué mensajes observaste en la terminal del servidor al conectar el cliente de escritorio y el cliente móvil? ¿Eran diferentes los mensajes o identificadores?

R/ 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/0b9646ae-939c-4713-b1a3-7f4a240d59e3" />

<img width="1912" height="1079" alt="image" src="https://github.com/user-attachments/assets/e7b65219-ba70-40bf-b1d6-ac1fd983b2f7" />

Los mensajes son iguales. "New client connected", sin importar cual de los dos se conecte, siempre saldra el mismo mensaje, incluso cuando se desconectan ("Client disconnected")..

### Describe el comportamiento observado: ¿Funcionó la interacción? ¿Hubo algún retraso (latencia)?

https://github.com/user-attachments/assets/b4e9d121-7932-43ec-8caf-f6a0d559bd50

R/

Afortunadamente la interración fue un exito, no hubo retrasos a nivel de fps, salvo un segundo al inicio cuando movia el circulo por primera vez, pero tras moverlos de forma recta tanto en horizontal como vertical y hacer movimientos circulares, no detecte retrasos en el movimiento.
