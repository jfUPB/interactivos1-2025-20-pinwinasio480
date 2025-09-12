
# Evidencias de la unidad 5

Actividad 1

Describe cómo se están comunicando el micro:bit y el sketch de p5.js. ¿Qué datos envía el micro:bit?

El micro:bit esta enviando los datos referentes para la verificación de si se oprimieron los botones a y b, asi como si el acelerometro se mueve en las coordenadas X o Y.

¿Cómo es la estructura del protocolo ASCII usado?



Muestra y explica la parte del código de p5.js donde lee los datos del micro:bit y los transforma en coordenadas de la pantalla.



¿Cómo se generan los eventos A pressed y B released que se generan en p5.js a partir de los datos que envía el micro:bit?



Capturas de pantalla de los algunos dibujos que hayas hecho con el sketch.

<img width="1919" height="1069" alt="Captura de pantalla 2025-09-12 141342" src="https://github.com/user-attachments/assets/a1614e94-1dff-47f7-ab0d-d773d9e92173" />

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 141458" src="https://github.com/user-attachments/assets/71930c94-f176-4bfd-a1b9-ba7eb5bd0b65" />

Actividad 2

🧐🧪✍️ Captura el resultado del experimento anterior. ¿Por qué se ve este resultado?

Cooldown de 100 que no se puede controlar

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 141833" src="https://github.com/user-attachments/assets/07d42ea4-94f8-440b-a4f6-624c0a5f3ab7" />

Ahora cambia la opción de Mostrar datos como a Todo en Hex y vuelve a capturar el resultado.

🧐🧪✍️ Captura el resultado del experimento anterior. Lo que ves ¿Cómo está relacionado con esta línea de código?

Si, porque genera lineas en bucle.

data = struct.pack('>2h2B', xValue, yValue, int(aState), int(bState))

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 141919" src="https://github.com/user-attachments/assets/e5ff4fb2-e93e-4b07-a71e-384db056b992" />

🧐🧪✍️ ¿Qué ventajas y desventajas ves en usar un formato binario en lugar de texto en ASCII?

////

🧐🧪✍️ Captura el resultado del experimento. ¿Cuántos bytes se están enviando por mensaje? ¿Cómo se relaciona esto con el formato '>2h2B'? ¿Qué significa cada uno de los bytes que se envían?

Se envian 6 bytes, los ultimos dos son el true y false de los botones a y b.

<img width="1919" height="1079" alt="Captura de pantalla 2025-09-12 142200" src="https://github.com/user-attachments/assets/c507e7f4-9347-4000-ae41-4a839314291a" />

🧐🧪✍️ Recuerda de la unidad anterior que es posible enviar números positivos y negativos para los valores de xValue y yValue. ¿Cómo se verían esos números en el formato '>2h2B'?


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

🧐🧪✍️ ¿Qué ves en la consola? ¿Por qué crees que se produce este error?

Actividad 4





