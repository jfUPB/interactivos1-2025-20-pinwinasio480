
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

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7da92ff4-016c-48f2-b240-b80b9c12e3c9" />

#### Inicia el servidor.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/022f1eb4-420a-4953-a981-112b1817d2f5" />

#### Intenta acceder a http://localhost:3000/page1. ¿Funciona?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/11c71f4f-98b8-4da8-bc80-9e52c6f63a39" />

Dice que no se puede obtener page1.

#### Ahora intenta acceder a http://localhost:3000/pagina_uno. ¿Funciona?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8e491742-656d-44a0-a1be-dc4aab71c8de" />

Ahora si me aparece sincronizando datos.

#### ¿Qué te dice esto sobre cómo el servidor asocia URLs con respuestas? Restaura el código.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/dddfd9ef-9be6-4c9f-8385-717e37f08335" />

R/ Me dice que el servidor debe tener una coincidencia exacta con la URL para poder funcionar, de lo contrario, esta no servira debido a que no sabra que respuesta dar, que eso es otro detalle, por lo que interpreto, cada URL esta asociada con una respuesta especifica, es como un mapa, tiene que ir hasta una parte especifica o no habra nada.

### 🧐🧪✍️ Experimenta (PARTE 2)

#### Asegúrate de que el servidor esté corriendo (npm start).

#### Abre http://localhost:3000/page1 en una pestaña. Observa la terminal del servidor. ¿Qué mensaje ves? Anota el ID.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/f748d593-6803-4cec-be8a-0263835f7b01" />

```
A user connected - ID: uai0Psj73MREhqeKAAAB
Received win1update from ID: uai0Psj73MREhqeKAAAB Data: { x: 0, y: 0, width: 1528, height: 738 }
Debug - Connected clients: 1, Page1: 1, Page2: 0, Synced: 0
Sync status: pages=false, synced=false, clients=1
Debug - Connected clients: 1, Page1: 1, Page2: 0, Synced: 1
Sync status: pages=false, synced=true, clients=1
```
El ID que me aparece por parte de page1 es: uai0Psj73MREhqeKAAAB

#### Abre http://localhost:3000/page2 en OTRA pestaña. Observa la terminal. ¿Qué mensaje ves? ¿El ID es diferente?

<img width="918" height="255" alt="image" src="https://github.com/user-attachments/assets/997eb9b0-d255-461c-90b9-3a6767076f69" />

```
A user connected - ID: XJsc-9cA7vdYVW0RAAAD
Received win2update from ID: XJsc-9cA7vdYVW0RAAAD Data: { x: 0, y: 0, width: 1528, height: 738 }
Debug - Connected clients: 2, Page1: 1, Page2: 1, Synced: 1
Sync status: pages=true, synced=false, clients=2
Debug - Connected clients: 2, Page1: 1, Page2: 1, Synced: 1
Sync status: pages=true, synced=false, clients=2
Debug - Connected clients: 2, Page1: 1, Page2: 1, Synced: 2
All clients are fully synced
```
El ID de page2 no es el mismo que el de page1, en page2 el ID es: XJsc-9cA7vdYVW0RAAAD

#### Cierra la pestaña de page1. Observa la terminal. ¿Qué mensaje ves? ¿Coincide el ID con el que anotaste?

<img width="411" height="24" alt="image" src="https://github.com/user-attachments/assets/80cd87b9-4627-4b43-a011-e6075c08e3ae" />

```
User disconnected - ID: uai0Psj73MREhqeKAAAB
```
Si, coincide con el ID que aparecio al abrir la pestaña page1.

#### Cierra la pestaña de page2. Observa la terminal.

<img width="413" height="27" alt="image" src="https://github.com/user-attachments/assets/c93ecfae-ff8f-487f-8f9c-09fac8d77d57" />

```
User disconnected - ID: XJsc-9cA7vdYVW0RAAAD
```
Al igual que page1, en page2 tambien coinciden los IDs.

### 🧐🧪✍️ Experimenta (PARTE 3)

#### Inicia el servidor y abre page1 y page2.

#### Mueve la ventana de page1. Observa la terminal del servidor. ¿Qué evento se registra (win1update o win2update)? ¿Qué datos (Data:) ves?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/45be3899-a57d-41dd-8be4-6550d52f6f3e" />

Al mover la ventana de page1, se registra win1update, y los datos de data que veo son la posición en X y Y, asi como el ancho y alto (width y height).
Por ejemplo:

```
Data: { x: 160, y: 76, width: 762, height: 444 }
```

#### Mueve la ventana de page2. Observa la terminal. ¿Qué evento se registra ahora? ¿Qué datos ves?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/24889f0e-8b89-41dc-b48b-7196f137d551" />

```
Data: { x: 372, y: 89, width: 762, height: 444 }
```

Se registra el evento de win2update, y los datos aunque son valores diferentes, son los mismos de page1, es decir, X, Y, width y height.

#### Experimento clave: cambia socket.broadcast.emit(‘getdata’, page1); por socket.emit(‘getdata’, page1); (quitando broadcast). Reinicia el servidor, abre ambas páginas. Mueve page1. ¿Se actualiza la visualización en page2? ¿Por qué sí o por qué no? (Pista: ¿A quién le envía el mensaje socket.emit?). Restaura el código a broadcast.emit.

<img width="962" height="228" alt="image" src="https://github.com/user-attachments/assets/c2ef12b2-72f6-4181-b437-378cd2cd8764" />

<img width="1919" height="1043" alt="image" src="https://github.com/user-attachments/assets/db86c592-20ac-444b-9fd1-7f403865cfcf" />

No se actualiza page2, esto porque socket.emit solo manda al cliente que este envio el mensaje (page1) mientras que al tener broadcast.emit el mensaje tambien sera enviado a los otros clientes (page2).

### 🧐🧪✍️ Experimenta (PARTE 4)

#### Detén el servidor.

#### Cambia const port = 3000; a const port = 3001;.

<img width="1887" height="1061" alt="image" src="https://github.com/user-attachments/assets/2f93b7e8-a426-413c-b174-814fde8cba89" />

#### Inicia el servidor. ¿Qué mensaje ves en la consola? ¿En qué puerto dice que está escuchando?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/92135bcc-ef67-4e65-84cc-77511d864432" />

Esta escuchando en el puerto 3001.

#### Intenta abrir http://localhost:3000/page1. ¿Funciona?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5a9cbb40-5dc7-4731-96b4-406ed990ccba" />

No sirve page1.

#### Intenta abrir http://localhost:3001/page1. ¿Funciona?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/836dc977-3b4c-49ac-a73a-b39002b109b5" />

Ahora con 3001 si.

#### ¿Qué aprendiste sobre la variable port y la función listen? Restaura el puerto a 3000.

R/ Que port se encarga de decirle el programa que puerto es el que debe enviar las respuestas, en este caso 3001, aqui volvemos al tema de coincidencias, si el puerto del código no coincide con el de las pestañas, el programa no va a saber que responder más alla de darte un error.

## Actividad 4

### 🧐🧪✍️ Experimenta (PARTE 1)

#### Abre page2.html en tu navegador (con el servidor corriendo).

#### Abre la consola de desarrollador (F12).

<img width="971" height="663" alt="image" src="https://github.com/user-attachments/assets/8b5d530d-01f4-4feb-bf49-8ae44a603a6f" />

#### Detén el servidor Node.js (Ctrl+C).

#### Refresca la página page2.html. Observa la consola del navegador. ¿Ves algún error relacionado con la conexión? ¿Qué indica?

<img width="965" height="656" alt="image" src="https://github.com/user-attachments/assets/eb56e9fc-9171-4392-91b3-3def985f9616" />

```
http://localhost:3000/socket.io/?EIO=4&transport=polling&t=Pce93Lg net::ERR_CONNECTION_REFUSED
```
El error me indica que la conexión ha sido denegada debido a que el servidor fue detenido.

#### Vuelve a iniciar el servidor y refresca la página. ¿Desaparecen los errores?

<img width="965" height="648" alt="image" src="https://github.com/user-attachments/assets/5abb7644-182c-40b8-a913-fce1e6e3816f" />

Los errores me dejan de salir de forma repetitiva para ahora notificarme que se ha conectado.

### 🧐🧪✍️ Experimenta (PARTE 2)

#### Comenta la línea socket.emit(‘win2update’, currentPageData, socket.id); dentro del listener connect.

<img width="862" height="251" alt="image" src="https://github.com/user-attachments/assets/e0aba5ea-9895-4b7c-9879-b24732c3e1c7" />

#### Reinicia el servidor y refresca page1.html y page2.html.

#### Mueve la ventana de page2 un poco para que envíe una actualización.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e268d926-e90c-4ef7-afa9-2a5ef6e61689" />

#### ¿Qué pasó? ¿Por qué?

R/ No se conecta ninguna de las dos pestañas, por parte de page1, dice "sincronizando datos", pero en page2, dice "Esperando conexión de la otra ventana", esto sucede porque socket.emit es lo que permite que a las page anunciar al servidor sus datos, pero al comentar esa parte del código, page1 seguira esperando a page2, mientras que page2 aunque tambien este conectado, no notificara al resto del servidor

### 🧐🧪✍️ Experimenta (PARTE 3)

#### Abre ambas páginas (es posible que ya las tengas abiertas).

#### Mueve la ventana de page1. Observa la consola del navegador de page2. ¿Qué datos muestra?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3406f4ac-5d29-41ad-9aa6-872e8a3dc123" />

Me muestra los valores de X, Y, width y Height. En la consola del navegador de page2, los valores X y Y se actualizan cuando muevo la pestaña de page1 (cosa que en el propio page2 no se actualiza), algo que no comente antes pero actualmente lo tengo de hipotesis, es que los valores de width y height son los del circulo page2, en la siguiente pregunta voy a comprobar si es cierto.

#### Mueve la ventana de page2. Observa la consola de page1. ¿Qué pasa? ¿Por qué?

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/c6feb155-c031-4b22-a171-c710f50d3f4e" />

Pasa lo mismo que en el caso anterior pero con los papeles invertidos, mientras que si muevo page2, se actualiza X y Y en la consola de page1, en la de page2 esto no sucede porque page2 o page 1 (en el caso anterior) envía sus datos al servidor, y este los reenvía a page1 (page2 en el caso anterior). En la consola de page2 (page1 anteriormente) no se ve reflejado el cambio porque la actualización de los datos está pensada para compartirse con la otra ventana, no consigo misma. Y con esta parte del experimento queda desmentida mi hipotesis, width y height son el tamaño de la ventana, no el movimiento de page2.

### 🧐🧪✍️ Experimenta (PARTE 4)

#### Observa checkWindowPosition() en page2.js y modifica el código del if para comprobar si el código dentreo de este se ejecuta.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/470c6206-6764-4ca4-8a68-45e2ed2e1e63" />

#### Mueve cada ventana y observa las consolas.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/69fe1bdd-dbea-4b70-9899-d599e6c7fd3f" />

#### ¿Qué puedes concluir y por qué?

R/ Con esto puedo concluir que la función checkWindowPosition() solo se activa cuando cambian los valores de la ventana actual (en este caso, page2), lo que significa que cada cliente es responsable de detectar sus propios cambios, tanto de posición como de tamaño, además de enviarlos al servidor. Esto lo menciono porque la sincronización con la otra página ocurre solamente porque el servidor reenvia esos datos.

### 🧐🧪✍️ Experimenta (PARTE 5)

#### Cambia el background(220) para que dependa de la distancia entre las ventanas. Puedes calcular la magnitud del resultingVector usando let distancia = resultingVector.mag(); y luego usa map() para convertir esa distancia a un valor de gris o color. background(map(distancia, 0, 1000, 255, 0)); (ajusta el rango 0-1000 según sea necesario).

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/a4dd229f-cbb6-4c65-867f-95d079477014" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d9f4ce47-cd15-4284-b9a2-7a36386ff557" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7b61aa85-dbd3-4356-a7fb-3ccea9498669" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/f49d150e-8c41-476a-8cf1-c285d1733c83" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2bcab36c-2bfd-4be7-b972-0057eba85d78" />

#### Inventa otra modificación creativa.

En la otra punta (opuesta al ellipse rojo, se crea un ellipse celeste que va aumentando o disminuyendo su tamaño dependiendo de la distancia de las ventanas.

```
     // Esfera con tamaño dinámico
    let tamano = map(distancia, 0, 1000, 120, 20); 
    fill(0, 200, 255);  // color fijo azul celeste
    noStroke();
    ellipse(point1[0], point1[1], tamano, tamano);
```

```
     // Esfera con tamaño dinámico
    let tamano = map(distancia, 0, 1000, 120, 20); 
    fill(0, 200, 255);  // color fijo azul celeste
    noStroke();
    ellipse(point2[0], point2[1], tamano, tamano);
```

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ae566312-3349-439a-85ae-87c0929976da" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9ea3dce7-ccb4-4943-9b81-11e11cdf9a94" />


<img width="1912" height="1079" alt="image" src="https://github.com/user-attachments/assets/e391f244-9cd9-4da6-b9b8-5ec1daa79d79" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/bbbe8fd0-f62a-4755-906a-308533f4d7d9" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/31f76c34-48b6-412b-a7fb-5e068c949037" />

## Actividad 5

## Autoevaluación

Siguiendo los parametros de esta unidad, en donde la cantidad de actividades define la calificación, en caso de que no actualice mi bitacora con algo del apply, considero que mi nota es de 3.0, esto debido a que cumpli con las primeras 4 actividades, incluso en los experimentos deje adjunto capturas de pantalla como sustentación de que si lleve a cabo los experimentos, asi mismo, las preguntas abiertas tambien las logre contestar, y tambien esta el tema de que el apply cuesta dos unidades, entonces, para el momento en el que se cierre la unidad antes de tiempo o diez minutos antes y no tenga nada del apply, considero que es lo más justo y logico.

