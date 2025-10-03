
# Evidencias de la unidad 6

## Actividad 1

<img width="1902" height="982" alt="image" src="https://github.com/user-attachments/assets/23434884-3008-449e-a7cb-06e44d4d4f64" />

### ¿Qué ocurrió en la terminal cuando ejecutaste npm install? ¿Cuál crees que es su propósito?

R/ Me aparecio el siguiente mensaje:

```
added 120 packages, and audited 121 packages in 2s

17 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
npm notice
npm notice New major version of npm available! 10.9.3 -> 11.6.1
npm notice Changelog: https://github.com/npm/cli/releases/tag/v11.6.1
npm notice To update run: npm install -g npm@11.6.1
npm notice
```
Si desglosamos parte por parte, al instalar npm, el proposito es informarme todo el proceso que hubo al instalar npm, en este caso: Se instalaron 120 paquetes y 121 se revisaron para detectar vulnerabilidades en los mismos; Despues destaca que 17 paquetes por parte de sus autores estan buscando apoyo economico (fund) debido a que son de código abierto; Más abajo, nos menciona que no se encontraron problemas de seguridad o vulnerabilidad en los paquetes instalados; y finalmente en cada npm notice nos comentan diferentes cosas, destacando como por ejemplo que hay una nueva versión disponible de npm y una y una sugerencia de como actualizar nuestra versión.

### ¿Qué mensaje específico apareció en la terminal después de ejecutar npm start? ¿Qué indica este mensaje?

R/ 

```
$ npm start

> nodejs-test-1@1.0.0 start
> node server.js

Server is listening on http://localhost:3000
```
Aqui aparecen dos mensajes: El primero indica el nombre y versión de mi proyecto, mientras que el segundo es un comando ejecutable, es decir, Node.js esta corriendo el archivo server.js y que el servidor esta escuchando al enlace localhost en donde se este ejecutando el programa.

### Describe lo que ves inicialmente en page1 y page2 en tu navegador.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d685825d-e048-45f9-a074-770a795980d8" />

<img width="1896" height="1055" alt="image" src="https://github.com/user-attachments/assets/7cee9a8d-0ea3-4862-8d12-aca5d5cb8a21" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/80c7a27f-a68a-4a95-896a-68bcc06e39b8" />

R/ En cada uno veo dos circulos rojos bordeados de negro en cuyas mitades hay una linea negra que conecta con el otro circulo.

### ¿Qué mensajes aparecieron en la terminal del servidor cuando abriste page1 y page2?

<img width="1919" height="965" alt="image" src="https://github.com/user-attachments/assets/e99a4d36-cdb9-4f5c-8722-8e4c695c850d" />

R/ Como se aprecia en la captura, me aparece que, cada vez que mueva alguna de las ventanas, me dira que se recibio un winupdate (1 o 2 dependiendo de la ventana movida) y los datos de X, Y, Ancho y Alto actualizados, además de un debug del cliente, las dos páginas y la sincronización.

### Describe qué sucede en ambas páginas del navegador cuando mueves una de las ventanas. ¿Cambia algo visualmente? ¿Qué mensajes aparecen (si los hay) en la consola del navegador (usualmente accesible con F12 -> Pestaña Consola) y en la terminal del servidor?

 <img width="1913" height="1079" alt="image" src="https://github.com/user-attachments/assets/3b7559dc-6ee1-4b46-b83a-87fe2efc3c1b" />

 <img width="1919" height="1072" alt="image" src="https://github.com/user-attachments/assets/f89ef686-8a12-4322-8e61-8816defb3cf1" />

R/ Al mover alguna de las dos ventanas, los circulos juntos con sus hilos se pueden juntar o alejar dependiendo de la distancia entre ambas ventanas, incluso se puede poner un circulo encima de otro; visualmente aparte de lo que mencione el programa se mantiene intacto en su gran mayoria, incluso aumentando o disminuyendo el tamaño de la ventana, el tamaño de los circulos no cambiara, como mencione anteriormente, solo cambia su posición. En la consola del navegador aparecen mensajes como:

```
page2.js:51 Sync status: SYNCED
page2.js:44 Received valid remote data: {x: -68, y: 116, width: 811, height: 438}
2page2.js:51 Sync status: SYNCED
page2.js:44 Received valid remote data: {x: -69, y: 116, width: 811, height: 438}
2page2.js:51 Sync status: SYNCED
page2.js:44 Received valid remote data: {x: -70, y: 115, width: 811, height: 438}
```
<img width="958" height="657" alt="image" src="https://github.com/user-attachments/assets/2c9f1946-5e1d-4856-bede-ddddaa1611ce" />

Y en la temrinal aun puedo observar como el servidor esta recibiendo de forma optima la posición de los circulos actualizada.

<img width="1022" height="978" alt="image" src="https://github.com/user-attachments/assets/9d9593a5-320b-430f-8e5a-a7a4de10a906" />

## Actividad 2

### A. Piensa en cómo te conectas a Internet en casa o en la Universidad. ¿Usas Wi-Fi? ¿Un cable de red? Eso es simplemente tu “rampa de acceso” a la gran red de carreteras. ¿Qué pasaría si esa rampa se corta? Anota tus ideas.

R/ Yendo por partes, siempre que puedo uso Wi-Fi en mi casa y en la universidad, por una parte, en mi casa contamos con un modem (en mi habitación) y un router en la sala; en la universidad desconozco de donde proviene la señal de internet, pero se me hace increible el como esa red llega por gran parte del campus. Los cables de red por mi parte no los utilizo, o por lo menos no en consolas como Xbox, solo utilizo uno en mi laptop cuando tengo problemas con la conexión en mi laptop, no obstante, mi hermano por ejemplo debe usar un cable de red para mejorar la conexión en su PS4 debido a la distancia de su cuarto con el modem. Y si nos vamos por el termino general, si cortamos esa rampa de acceso, en la generación actual nos estariamos perdiendo de grandes novedades o avances tecnologicos, y por la parte subjetiva, en mi caso los videojuegos, yo al ser dueño de una Xbox Series X, si, puedo seguir jugando algunos juegos en formato fisico o que haya comprado digitalmente de un solo jugador, pero los juegos multijugador online como Fortnite serian inacesibles para mi.

### B. ¿Puedes identificar otros ejemplos de relaciones Cliente-Servidor en tu vida diaria (no necesariamente digitales)? Por ejemplo, al pedir comida en un restaurante. ¿Quién es el cliente y quién el servidor? ¿Qué se pide y qué se entrega?

R/ Un ejemplo que se me ocurre es cuando voy a un banco, en este caso, yo, como cliente, solicito al cajero retirar dinero de mi cuenta de debito, y el cajero siendo el servidor, responde a mi pedido retirando la cantidad que yo solicite. Con respecto al ejemplo del restaurante, el cliente soy al pedirle al mesero la orden que deseo, y el servidor es el restaurante, esto debido a que varios trabajadores los que actuan como el servidor, debido a que el mesero responde recibiedo nuestra orden y los chefs/cocineros responden preparando el plato, bebidas y etc , y finalmente ellos me dan lo que pedi.
 
### C. Toma la URL de tu sitio web favorito. Intenta identificar el protocolo, el nombre de dominio y la ruta (si la hay). ¿Qué crees que pasa si solo escribes el nombre de dominio (ej. www.google.com) sin una ruta específica? ¿Qué “página por defecto” crees que te envía el servidor?

R/ https://www.xbox.com/es-CO/xbox-game-pass?msockid=03d2d907ef7068050406cd0eeedf692f

1. Protocolo: https://
2. Nombre del dominio: www.xbox.com
3. Ruta especifica: /es-CO/xbox-game-pass?msockid=03d2d907ef7068050406cd0eeedf692f

Si escribo solo www.xbox.com, supongo que me mandara a la página principal de xbox, mis hipotesis son: o que enviara a la versión de mi país o a la de Estados Unidos. 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5c042dcc-7d1c-4247-825d-3699efe7f98f" />

Tras escribir solo el nombre del dominio, puedo confirmar que me envio a la página principal de xbox de mi país (Colombia).

### D. Compara HTTP con los protocolos seriales que usaste.

### D.1 ¿Qué similitudes encuentras?

R/ Tanto HTTP como los protocolos seriales tienen un emisor y un receptor, en la unidad anterior el emisor era el micro:bit y el receptor el programa de p5.js, y aqui el emisor es el cliente y el receptor el servidor; en ambas se necesitan formatos acordados, anteriormente era ASCII o binario, ahora son textos estructurados (lineas con método, cabeceras y cuerpo).

### D.2 ¿Qué diferencias clave ves?

R/ Por parte de los protocolos serias, son dos dispositivos directos y se mandan datos simples, mientras que con HTTP es con redes globales y se envian cabeceras, métodos, estados, etc. Tambien esta como se transportan los datos, con un serial es con un puerto de cables, pero con HTTP es con Protocolos de Control de Transmisión y de internet (TCP/IP).

### D.3 ¿Por qué crees que HTTP necesita ser más complejo que un simple envío de bytes como hacías con el micro:bit?

R/ Porque no es solo enviar bytes, sino que es más información y recursos (como el tipo de archivo y página) y más clientes y servidores en simultaneo en lugar de uno o muy pocos a los que debe responder.

### E. Piensa en una página web simple, como un formulario de login.

### E.1 ¿Qué parte crees que es HTML (ej. los campos de texto, el botón)?

R/ Los campos de texto donde me pide escribir el nombre de usuario y la contraseña.

### E.2 ¿Qué parte es CSS (ej. el color del botón, el tipo de letra)?

R/ Ambos ejemplos son parte del CSS, pues se trata de la identidad visual de la página, en este caso, el color del botón o botones para iniciar sesión y la fuente de letra de la misma.

### E.4 ¿Qué parte es JavaScript (ej. la comprobación de si escribiste algo antes de enviar, el mensaje de “contraseña incorrecta” que aparece sin recargar la página)?

R/ La reacción al click de iniciar sesión, saltar la advertencia de error ya sea como en el ejemplo, por una contraseña incorrecta, un nombre de usuario incorrecto o un campo vacio.

#### F. Compara el bucle draw() de p5.js con este modelo de “esperar a que algo pase y reaccionar”.

### F.1 ¿Qué ventajas crees que tiene el modelo basado en eventos para una interfaz de usuario web?

R/ Entre las ventajas se encuentra: solo debe ejecutar el código cuando sea necesario (es decir, cuando ocurra el evento) en lugar ejecutarse en un bucle cada 60 segundos, tambien facilitia el manejos de varias interraciones sin que se pregunte si algo cambió todo el tiempo, y en lugar de redibujar toda la pantalla, solamente responde con rapides a las acciones del cliente/usuario.

### F.2 ¿Sería eficiente tener un bucle draw() redibujando toda la página 60 veces por segundo si nada ha cambiado?

R/ No, porque si no se han aplicado cambios, se estaria gastando recursos, además de que redibujar la misma pantalla seria el equivalente a pintar de blanco un lienzo una y otra vez, se actualiza, pero no hay nada.

### G. ¿Por qué crees que podría ser útil usar JavaScript tanto en el cliente (navegador) como en el servidor? ¿Se te ocurre alguna ventaja para los desarrolladores?

R/ Podria ser bastante útil ya que reduciria la cantidad de linea de aprendizaje para desarollar códigos, en este caso, seria una gran ventaja que al tener el cliente y el servidor los mismos lenguajes de programación tambien haria que se puedan compartir cosas como funciones, validaciones o estructuras.

### H. Resume con tus propias palabras la diferencia fundamental entre una comunicación HTTP tradicional y una comunicación usando WebSockets/Socket.IO. ¿En qué tipo de aplicaciones has visto o podrías imaginar que se usa esta comunicación en tiempo real?

R/ Por parte del HTTP tradicional usuario A pide una petición a HTTP, usuario A espera a que esa petición se envie a usuario B y finalmente usuario A recibe una respuesta de usuario B (como el ejemplo del profesor con los correos electronicos); Mientras que con WebSockets/Socket.IO. tanto usuario A como usuario B pueden interactuar de forma simultanea sin tener que pedirle algo a HTTP; ese tipo de interacciónes las veo constantemente en los juegos multijugador en linea como Roblox, donde usuario A y B interactuan al mismo tiempo, aunque tambien esta presente en aplicaciones en los que hay llamadas como WhatsApp o Discord, hasta funciones de google Docs para que más de un usuario modifique un archivo en simultaneo cuenta.

## Actividad 3 

### 🧐🧪✍️ Experimenta (PARTE 1)

#### Detén el servidor si está corriendo.

#### Cambia la primera ruta de /page1 a /pagina_uno.

#### Inicia el servidor.

#### Intenta acceder a http://localhost:3000/page1. ¿Funciona?

#### Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?

#### ¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas? Restaura el código.

### 🧐🧪✍️ Experimenta (PARTE 2)

#### Asegúrate de que el servidor esté corriendo (npm start).

#### Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.

#### Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?

#### Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?

#### Cierra la pestaña de page2. Observa la terminal.

### 🧐🧪✍️ Experimenta (PARTE 3)

#### Inicia el servidor y abre page1 y page2.

#### Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?

#### Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?

#### Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.

### 🧐🧪✍️ Experimenta (PARTE 4)

#### Detén el servidor.

#### Cambia const port = 3000; a const port = 3001;.

#### Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando?

#### Intenta abrir http://localhost:3000/page1. ¿Funciona?

#### Intenta abrir http://localhost:3001/page1. ¿Funciona?

#### ¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.


