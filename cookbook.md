# Cookbook - Diseño Web Avanzado

Por Alan Badillo Salas [ badillo.soft@hotmail.com | https://twitter.com/badillosoft | https://github.com/badillosoft ]

## Contenido

### Parte I - Introducción al desarrollo web

1. Crear una aplicación web _HTML 5_
2. Modificar el diseño de una aplicación web utilizando _CSS_
3. Modificar la funcionalidad de una aplicación web utilizando _JavaScript_
4. Mostrar un menú de alerta personalizado
5. Consumir un servicio web en _json_

### Parte II - Almacenamiento

1. Guardar un valor
2. Recuperar un valor guardado
3. Sincronizar un objeto de configuración
4. Recordar los datos de un formulario

### Parte III - Geolocalización

1. Obtener las coordenadas de geolocalización
2. Mostrar un mapa con las coordenadas específicas
3. Mostrar un mapa con las coordenas del usuario
4. Añadir un pin al mapa y guardarlo
5. Ir a un pin guardado

### Parte IV - Canvas

1. Dibujar figuras básicas
2. Animar una figura
3. Dibujar una función
4. Almacenar un dibujo
5. Dibujar un dibujo almacenado

### Parte V - Diseño avanzado

1. Controles en _Bootstrap_
2. Implementar el _Material Design_
3. Introducción a _JQuery Mobile_

## Parte I - Introducción al desarrollo web

### Crear una aplicación web _HTML 5_

Para construir una aplicación _HTML 5_ usaremos la etiqueta `<!DOCTYPE html>` al principio de nuestro archivo _html_, incluiremos las nuevas etiquetas implementadas y evitaremos las obsoletas como se puede ver en http://www.w3schools.com/html/html5_intro.asp

> __HTML__ - Plantilla básica de una aplicación en _HTML 5_

~~~html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Title of the document</title>
    
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    
    <script src="myscript.js"></script>
  </head>
  
  <body>
    Content of the document......
  </body>
</html> 
~~~

### Modificar el diseño de una aplicación web utilizando _CSS_

Podemos modificar el diseño de una aplicación web utilizando _css_. Las definiciones deben ponerse dentro de `<head>` medinte las etiquetas `<style>` si queremos un estilo local o `<link>` si queremos un estilo contenido en un archivo. Los estilos se aplicarán conforme se vayan cargando y la prioridad será: primero los estilos definidos en el elemento mediante el atributo `style`, ejemplo `<div style="background-color: red; color: blue;">`, luego los contenidos en la etiqueta `<style>`, ejemplo `<style>div { background-color: red; color: blue; }` y finalmente los contenidos en el archivo, ejemplo `<link rel="stylesheet" type="text/css" href="mystyle.css">`.

> __HTML__ - Incluir un estilo local al archivo _html_

~~~html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Title of the document</title>
    
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    
    <style>
      body {
        background-color: #333;
      }
    </style>
    
    <script src="myscript.js"></script>
  </head>
  
  <body>
    Content of the document......
  </body>
</html> 
~~~

> __HTML__ - Cambiar el color de fondo de los elementos con la clase `change` cuando el cursor este sobre ellos

~~~html
<style>
  .change {
    background-color: red;
  }
  
  .change:hover {
    background-color: blue;
  }
</style>

...

<div class="change">
  <h1>Hola mundo</h1>
</div>
~~~

### Modificar la funcionalidad de una aplicación web utilizando _JavaScript_

Al igual que con _css_ podemos incluir nuestro código dentro del archivo _html_ mediante el cuerpo de la etiqueta `<script>` o dentro de un archivo con extensión `.js` y `<script src="archivo.js">`.

_JavaScript_ nos permite utilizar los controles de _html_ mediante _DOM_. Para recuperar un control _html_ podemos hacerlo mediante el objeto `document` el cual nos proveé varios métodos como `getElementById`.

> __JS__ - Recuperar un control _html_ mediante su _id_ cuando la página ya esta lista

~~~js
var control = null;

window.onload = function () {
  control = document.getElementById("mi_id");
};
~~~

> __HTML__ - Definir un control para que el usuario ingrese texto y asignarle un _id_

~~~html
<input id="mi_id" type="text" placeholder="Escribe algo aquí" />
~~~

El orden de los atributos en una etiqueta _html_ no importa. El _id_ del control debe ser único para cada elemento.

> __JS__ - Recuperar y cambiar los atributos estándares de un elemento _html_ mediante _javascript_

~~~js
var control = null;

window.onload = function () {
  control = document.getElementById("mi_id");
  
  control.value = "Mi id es: " + control.id;
};
~~~

Observa que el control es el `input` definido antes y el valor de la caja será el texto `Mi id es: ...` donde `...` será el _id_ de la caja recuperado en _javascript_. Como esto se está haciendo cuando se invoca a la función `onload` del objeto `window` se mandará a llamar cuando la página este cargada, es decir, que el usuario verá la caja con ese texto desde un principio.

Lo anterior se conoce como _delegamiento_ o uso de _delegados_. Los _delegados_ son funciones bien conocidas por el navegador que se mandan a llamar cuando ocurre un evento, en este caso el objeto `window` tiene un delegado llamado `onload` el cual es una variable que guarda una función, cada que se manda a llamar la página y se completa manda a llamar a la función `window.onload`, cuando nostros cambiamos el valor del delegado `window.onload = function () { ... };` por una función anónima, entonces mandará a llamar a nuestra función en vez de llamar a la que tenía antes (la cual no hacia nada).

Para ilustar esto más a detalle, un botón tiene un delegado llamado `onclick` el cual tampoco hace nada, la siguiente receta recupera el elemento `<button id="mi_boton">Pulsame</button>` definido en un archivo _html_ para mostrar un mensaje de alerta cada que se pulsa el botón, es decir, cada que ocurre la llamada al delegado `onclick` del botón.

> __JS__ - Modificar el evento `onclick` del elemento `<button>` mediante sobrecarga de _delegados_

~~~js
var boton = null;

window.onload = function () {
  boton = document.getElementById("mi_boton");
  
  boton.value = function () {
    alert("Me has pulsado :)");
  };
};
~~~

Observe que modificamos el delegado `onclick` del control recuperado en _javascript_ para sobreescribir su funcionalidad con la función anónima `function () { alert("Me has pulsado :)"); };`.

Puedes revisar los eventos de los controles en http://www.w3schools.com/tags/ref_eventattributes.asp

También podemos modificar directamente los eventos desde la definición de la etiqueta en _html_ esto nos ahorra tener que recuperar el control en _javascript_ lo cual es útil en algunos casos como el anterior. Para modificar el evento sólo hay que definir el atributo que lleva el nombre del evento y mandar a llamar a una función nombrada que hayamos definido en el _script_.

> __HTML__ - Modificar el evento `onclick` del elemento `<button>` mediante ejecución directa

~~~html
<button onclick="saludar()">Pulsame</button>
~~~

Cada que se genere el evento clic del botón mandará a llamar a la función `saludar()`, no olvide poner los paréntesis `()` en la llamada a la función. La función saludar debe estar declarada en el _script_. Observe que ya no es necesario definir un _id_ para el elemento ni recuperarlo en el _script_ ni hacer uso del punto de entrada `window.onload`

> __JS__ - Declarar la función saludar

~~~js
function saludar() {
  alert("Hola mundo");
}
~~~

### Mostrar un menú de alerta personalizado

Para crear un mensaje de alerta utilizaremos _css_ y algunas etiquetas que contengan los datos:

> __HMTL__ - Estructura de la caja de alerta

~~~html
<div id="box_all" class="box-all" onclick="hideAlert()">
  <div id="box_alert" class="box-alert">
    <h1>Usuario no válido</h1>
    <p>El usuario o la contraseña es incorrecta</p>
  </div>
</div>
~~~

Aplicamos el siguiente diseño para la caja:

> __CSS__ - Diseño de la caja de alerta

~~~css
.box-all {
  display: none;
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0);
  transition: background-color 1s;
}

.box-alert {
  position: absolute;
  top: -200px;
  transition: top 1s;
  left: calc(50% - 150px);
  width: 300px;
  padding: 30px;
  margin: auto;
  text-align: center;
  background-color: white;
  box-shadow: 0px 0px 5px 1px rgba(255, 0, 0, 0.4);
  color: #666;
}

.box-alert h1 {
  font-size: 1.1em;
}

.box-alert p {
  font-size: 0.8em;
  text-align: left;
  margin-top: 20px;
}
~~~

Finalmente programamos la funcionalidad para esconder y mostrar:

> __JS__ - Mostrar la caja de alerta

~~~js
var box_all = document.getElementById("box_all");
var box_alert = document.getElementById("box_alert");

box_alert.style.top = "0px";
box_all.style.height = "100%";
box_all.style.backgroundColor = "rgba(0, 0, 0, 0.4)";
~~~
> __JS__ - Ocultar la caja de alerta

~~~js
var box_all = document.getElementById("box_all");
var box_alert = document.getElementById("box_alert");

box_alert.style.top = "-200px";
//box_all.style.height = "0%";
box_all.style.backgroundColor = "rgba(0, 0, 0, 0)";

setTimeout(function () {
  box_all.style.display = "none";
}, 1000);
~~~

### Consumir un servicio web en _json_

Para consumir un servicio web en _json_ es necesario comprobar que este funcionando correctamente, por ejemplo, pruebe la _api_ libre de https://randomuser.me/. Una vez que la url funciona y nos devuelve objetos _json_ la integramos mediante jquery:

> __HTML__ - Integrar _jquery_ a la aplicación

~~~html
<!DOCTYPE html>
<html>
  <head>
    ...
    <script src="https://code.jquery.com/jquery-3.1.0.min.js"></script>
    ...
  </head>
  ...
</html>
~~~

Posteriormente cada que queramos recuperar los datos realizamos una petición _ajax_:

> __JS__ - Petición _ajax_

~~~js
...

$.ajax({
  url: "https://randomuser.me/api", // URL del servicio web
  dataType: "json", // Tipo de respuesta del servicio web
  success: function (data) { // Función que procesa los datos devueltos por el servidor
    console.log(data); // Procesamos aquí los datos, podemos llamar a otra función si queremos
  },
  error: function (err) { // Función que procesa cualquier error durante la petición _ajax_
    console.log("Hubo un error al obtener los datos", err); // Procesamos aquí el error
  }
});

...
~~~

## Parte II - Almacenamiento

### Guardar un valor

> __JS__ - Guardar un valor local y por sesión

~~~js
localStorage.setItem("mi_clave", "mi_valor");
sessionStorage.setItem("mi_clave", "mi_valor");
~~~

### Recuperar un valor guardado

> __JS__ - Recuperar un valor local y por sesión

~~~js
var mi_valor = localStorage.getItem("mi_clave");
var mi_valor = sessionStorage.getItem("mi_clave");
~~~

### Sincronizar un objeto de configuración

Para guardar un objeto complejo lo convertiremos en una cadena de texto con el formato _json_ mediante `JSON.stringify(obj)`, para recuperar el objeto desde una cadena _json_ usaremos `JSON.parse(cad)` este procedimiento se conoce como serialización y deserialización respectivamente.

Primero definimos nuestro objeto de configuración

> __JS__ - Objeto de configuración

~~~js
var conf = {
  recordar: false
};
~~~

Serializamos el objeto para guardarlo

> __JS__ - Guardar un objeto de configuración

~~~js
localStorage.setItem("config", JSON.stringify(conf));
~~~

Deserializamos el objeto recuperado para obtener la configuración

> __JS__ - Recuperar un objeto de configuración

~~~js
var conf = localStorage.getItem("config");

console.log(conf.recordar);
~~~

### Recordar los datos de un formulario

Creamos los un formulario

> __HTML__ - Formulario HTML con usuario y contraseña

~~~html
<label for="txt_usuario">Usuario:</label>
<input id="txt_usuario" placeholder="Usuario" >
<label for="txt_clave">Contraseña:</label>
<input id="txt_clave" type="password" placeholder="Contraseña" >
<input id="chk_recordar" type="checkbox" onchage="sincronizar()" checked >
<label for="chk_recordar">Recordar</label>
~~~

Recuperamos los elementos en _javascript_ mediante su _id_

> __JS__ - Recuperar los elementos

~~~js
var txt_usuario = null, txt_clave = null, chk_recordar = null;

window.onload = function() {
  txt_usuario = document.getElementById("txt_usuario");
  txt_clave = document.getElementById("txt_clave");
  chk_recordar = document.getElementById("chk_recordar");
};
~~~

Recuperamos el valor guardado del `checkbox` para determinar si el usuario quizó guardar los datos

> __JS__ - Recuperar los elementos

~~~js
var txt_usuario = null, txt_clave = null, chk_recordar = null, config = { recordar: false, usuario: "", clave: "" };

window.onload = function() {
  txt_usuario = document.getElementById("txt_usuario");
  txt_clave = document.getElementById("txt_clave");
  chk_recordar = document.getElementById("chk_recordar");
  
  // Recuperamos la configuración guardada (si existe)
  var saved_config = localStorage.getItem("config");
  
  // Si hay una configuración previa
  if (saved_config) {
    // Reemplazamos el objeto de configuración [ver II.3]
    config = JSON.parse(saved_config);
  } else {
    // Sino, guardamos el objeto de configuración por defecto creado arriba
    localStorage.setItem("config", JSOSN.stringify(config));
  }
  
  // Ajustamos los valores de las cajas según la configuración
  txt_usuario.value = config.usuario;
  txt_clave.value = config.clave;
};
~~~

Sincronizamos el checkbox con el objeto de configuración

> __JS__ - Sincronizar el objeto de configuración

~~~js
// Definimos la función que sincroniza la configuración
function sincronizar() {
  // Ajustamos los valores de configuración según los valores de los controles
  config.recuperar = chk_recuperar.checked;
  
  if (config.recuperar) {
    // En modo recuperar la configuración guarda los valores de usuario y contraseña
    config.usuario = txt_usuario.value;
    config.clave = txt_clave.value;
  } else {
    // Sino, borramos los datos almacenados en usuario y contraseña
    config.usuario = "";
    config.clave = "";
  }
  
  localStorage.setItem("config", JSOSN.stringify(config));
}
~~~

## Parte III - Geolocalización

### Obtener las coordenadas de geolocalización

Obtendremos las coordenadas mediante el _web api_ `navigator.geolocation` como se describe en https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/Using_geolocation

> __JS__ - Obtener las coordenadas de geolocalización

~~~js
navigator.geolocation.getCurrentPosition(function(position) {
  console.log(position.coords.latitude, position.coords.longitude);
});
~~~

### Mostrar un mapa con las coordenadas específicas

Usaremos los mapas de _google_ como se describe en http://www.w3schools.com/googleapi/default.asp

> __HTML__ - Ajustar la región del mapa

~~~html
<div id="box_map"></div>
~~~

> __CSS__ - Ajustar el diseño de la región del mapa

~~~css
* {
  padding: 0;
  margin: 0;
  user-select: none;
}

html, body {
  height: 100%;
}

#box_map {
  width: 100%;
  height: 100%;
  background-color: gray;
}
~~~

> __JS__ - Construir el objeto `map`

~~~js
var map = null;

google.maps.event.addDomListener(window, "load", initialize);

function initialize () {
  
  var properties = {
    center: new google.maps.LatLng("19.434353", "-99.130010"),
    zoom: 15,
    mapTypeId: google.maps.MapTypeId.ROADMAP,
    disableDefaultUI: true
  };
  
  map = new google.maps.Map(document.getElementById("box_map"), properties);
}
~~~

### Mostrar un mapa con las coordenas del usuario

> __JS__ - Centrar el mapa en las coordenadas del usuario

~~~js
navigator.geolocation.getCurrentPosition(function(user_position) {
  var position = new google.maps.LatLng(user_position.coords.latitude, user_position.coords.longitude);
  map.setCenter(position);
});
~~~

### Añadir un pin al mapa y guardarlo

> __JS__ - Poner un marcador en el mapa

~~~js
var position = new google.maps.LatLng("19.1234", "-99.1234");

var marker = new google.maps.Marker({
	position: position
});

marker.setMap(map);
~~~

> __JS__ - Mostrar una ventana de información en el marcador cuando se pulsa click

~~~js
var info = new google.maps.InfoWindow({
	content: "<strong>Hola mundo</strong>"
});

google.maps.event.addListener(marker, 'click', function () {
	info.open(map, marker);
});
~~~

> __JS__ - Guardar los datos de un marcador

~~~js
var position = {
  lat: "19.1234",
  lng: "99.1234"
};

localStorage.setItem("mi_pin", JSON.srtingify(position));
~~~

### Ir a un pin guardado

> __JS__ - Recuperar los datos de un marcador

~~~js
var position = JSON.parse(localStorage.getItem("mi_pin"));

var marker = new google.maps.Marker({
	position: new google.maps.LatLng(position.lat, position.lng);
});

marker.setMap(map);
~~~

## Parte IV - Canvas

Usaremos la siguiente plantilla básica para utilizar canvas

> __JS__ - Plantilla para usar canvas

~~~js
var canvas = null, ctx = null;
    
// Cargamos los eventos `load` y `resize` de `window`
window.addEventListener("load", initialize);
window.addEventListener("resize", resize);

// Inicializa el objeto canvas y el contexto, invoca los loops para actualizar y dibujar
function initialize () {
	canvas = document.getElementById("canvas");
	ctx = canvas.getContext("2d");

	resize();
	update();
	draw();
};

// Si la ventana es redimensionada mantiene la misma resolución
function resize() {
	var aspect = window.innerWidth / window.innerHeight, resolution = 300;
	canvas.width = resolution;
	canvas.height = resolution / aspect;
}

// TODO: Colocar variables de control aquí
// Ejemplo: var x = 0;

// Actualizamos las variables de control
function update() {
	// TODO: Completar lógica aquí
	
	// Creamos el loop para actualizar cada 60 fps aproximadamente
	requestAnimationFrame(update);
}

// Dibujamos objetos usando o no las variables de control
function draw() {
	// Borramos toda la pantalla
	ctx.clearRect(0, 0, canvas.width, canvas.height);
	
	// TODO: Dibujar aquí

	// Creamos el loop para dibujar cada 60 fps aproximadamente
	requestAnimationFrame(draw);
}
~~~

### Dibujar figuras básicas

Las figuras básicas se pueden dibujar mediante las funciones ya programadas del contexto `ctx` como `strokeRect` para un rectángulo pintado en el borde, `fillRect` para un rectángulo relleno, cada figura cuenta con un conjunto de parámetros como `x`, `y`, `w`, `h`, `r`, `angle`, ..., los cuales dependen del tipo de figura.

Podemos cambiar el color de contorno o de relleno mediante `ctx.strokeStyle = color` y `ctx.fillStyle = color` donde `color` puede ser un color nombrado, un hexadecimal de 3 valores o de 6, ejemplo `#F00` o `FF0000`, un _rgb_ como `rgb(255, 0, 0)` o un _rgba_ como `rgba(255, 0, 0, 0.5)`, véase http://www.w3schools.com/css/css_colors.asp.

Para aplicar un dibujado necesitamos invocar `ctx.stroke()` y/o `ctx.fill()`, generalmente hacemos esto cuando no usamos `strokeShape` o `fillShape`, ejemplo, `ctx.rect(x, y, w, h)`.

> __JS__ - Dibujar un rectángulo relleno en x = 100, y = 200, w = 20, h = 30

~~~js
ctx.fillStyle = "red";
ctx.fillRect(100, 200, 20, 30);
~~~

También podemos usar un gradiente como color de relleno, especificando el punto de partida y el punto de fin usando `createLinearGradient`, revise http://www.w3schools.com/html/html5_canvas.asp para más profundidad en el concepto.

> __JS__ - Aplicar un gradiente lineal sobre un circulo

~~~js
// Creamos el gradiente del punto (0, 0) al (100, 100) que es una diagonal
var grd = ctx.createLinearGradient(0, 0, 100, 100);

grd.addColorStop(0, "red");
grd.addColorStop(0.25, "#00f");
grd.addColorStop(0.5, "#f8a878");
grd.addColorStop(0.75, "rgb(255, 84, 84)");
grd.addColorStop(1, "rgba(127, 127, 127, 0.5)");

ctx.fillStyle = grd;

ctx.beginPath();
// Dibujamos un circulo en el punto (10, 10) de radio 20
// 0 - es el ángulo inicial del arco
// 2 * Math.PI - es el ángulo final del arco, que es equivalente a 360º pero en redianes
ctx.arc(10, 10, 20, 0, 2 * Math.PI);

ctx.closePath();

ctx.fill();
~~~

### Animar una figura

Para animar una figura utilizaremos variables de control para determinar las posiciones de las figuras y actualizarlas en el tiempo

> __JS__ - Animar un triángulo

~~~js
var x = 0, y = 0;

function update() {
	x += 1;
	y += 1;
	...
}

function draw() {
	...
	
	ctx.beginPath();
	// Nos movemos al punto (x, y) sin dibujar nada
	ctx.moveTo(x, y);
	// Nos movemos al punto (x + 10, y) trazando una linea
	ctx.lineTo(x + 10, y);
	// Nos movemos al punto (x + 5, y + 10) trazando una linea
	ctx.lineTo(x + 5, y + 10);
	// Al cerrar el path se crea una linea que va del último punto (x + 5, y + 10) al inicial (x, y)
	ctx.closePath();
	
	// Rellenamos el triángulo
	ctx.fill();
	// Pintamos el borde del triángulo
	ctx.stroke();
	
	...
}
~~~

### Dibujar una función

Para dibujar una función calculamos un arreglo de puntos secuenciales que representan la función, cada punto es un objeto compuesto de una `x` y una `y`.

> __JS__ - Crear un arreglo de puntos basados en una función

~~~js
var points = [];

for (var x = -10; x <= 10; x += 0.5) {
	var y = 100 * Math.sin(x);
	
	points.push({ x: x, y: y });
}
~~~

> __JS__ - Dibujar un arreglo de puntos basados en una función

~~~js
var dx = 100, dy = 100, ex = 1, ey = 1;

ctx.beginPath();

var initialPoint = points[0];

ctx.moveTo(initialPoint.x, initialPoint.y);

points.forEach(function (point) {
	ctx.lineTo(ex * (point.x - dx), ey * (point.y - dy));
});

ctx.closePath();

ctx.stroke();
~~~

Observe que las variables `dx`, `dy` fueron introducidas para centrar la función en el punto `(dx, dy)` y los valores `ex`, `ey` fueron introducidas para escalar la función, si lo desea puede eliminarlas y dejar sólo `ctx.lineTo(point.x, point.y);`

### Almacenar un dibujo

Para almacenar un dibujo o función basta con serializar y deserializar el arreglo de puntos.

> __JS__ - Almacenar un dibujo

~~~js
var points = [];

...

localStorage.setItem("points", JSON.stringify(points));
~~~

### Dibujar un dibujo almacenado

> __JS__ - Dibujar un dibujo almacenado

~~~js
var points = JSON.parse(localStorage.getItem("points"));

ctx.beginPath();

var initialPoint = points[0];

ctx.moveTo(initialPoint.x, initialPoint.y);

points.forEach(function (point) {
	ctx.lineTo(point.x, point.y);
});

ctx.closePath();

ctx.stroke();
~~~

## Parte V - Diseño avanzado

### Controles en _Bootstrap_

_Bootstrap_ es un framework basado en _css_ que se encarga de implementar un diseño responsivo fácilmente a nuestra aplicación web. Para entender _Bootstrap_ visite http://getbootstrap.com/css/. Lo único que tenemos que hacer es agregarle las clases ya construidas a nuestras etiquetas html para que adopten un diseño mejorado. Para hacer práctica esta receta mostraremos como hacer una ventana de acceso a usuarios utilizando _bootstrap_.

Creamos el esqueleto de la aplicación, la cual consiste en el formulario de acceso a usuarios.

> __HTML__ - Esqueleto de una aplicación de acceso a usuarios con _bootstrap_

~~~html
<!-- Menú de navegación -->
  <nav class="navbar navbar-default">
    <ul class="nav nav-tabs">
      <li class="active"><a href="#" class="active">Inicio</a></li>
      <li><a href="#">Contacto</a></li>
      <li><a href="#">Acerca de</a></li>
    </ul>
  </nav>

  <!-- Contenido -->
  <div class="container">
    <form>
      <div class="form-group">
        <label for="txt_usuario">Usuario:</label>
        <input class="form-control" id="txt_usuario" type="text" placeholder="Usuario" />
      </div>
      <div class="form-group">
        <label for="txt_clave">Contraseña:</label>
        <input class="form-control" id="txt_clave" type="password" placeholder="Contraseña" />
      </div>
      <button class="btn btn-primary pull-right">Iniciar Sesión</button>
    </form>
  </div>
~~~

Como se puede observar sólo debemos colocar los elementos de forma organizada y en cada panel y control agregar las clases necesarias.

### Implementar el _Material Design_

### Introducción a _JQuery Mobile_

_JQuery mobile_ es una librería basada en _JQuery_ para integrar aplicaciones web en diversos dispositivos móviles, tabletas y de escritorio haciendo que el diseño se adapte. Puede encontrar más información en http://demos.jquerymobile.com/1.4.5/

> __HTML__ - Esqueleto de una página de acceso a usuario con _jquery mobile_

~~~html
<div id="login" data-role="page">
	<div data-role="header">
		<h1>Iniciar Sesión</h1>
		<a href="#" class="ui-btn-right">Registrarse</a>
	</div>
	
	<div role="main" class="ui-content">
		<div class="ui-field-contain">
			<label for="username">Usuario:</label>
			<input name="username" id="username" type="text" placeholder="Usuario" data-clear-btn="true" />
		</div>
		
		<div class="ui-field-contain">
			<label for="password">Contraseña:</label>
			<input name="password" id="password" type="password" placeholder="Contraseña" data-clear-btn="true" />
		</div>
	
		<div class="ui-field-contain">
			<a href="#home" data-role="button">ingresar</a>
		</div>
	</div>
</div>
~~~

> __HTML__ - Esqueleto de una página de con información del usuario con _jquery mobile_

~~~html
<div id="home" data-role="page">
	<div id="user-info" data-role="panel" data-display="push">
		<div class="ui-panel-inner" style="text-align: center;">
			<img src="https://avatars3.githubusercontent.com/u/6743118?v=3&s=460" style="width: 150px; height: 150px; border-radius: 50%;" />
		</div>
	</div>
      
	<div data-role="header" style="overflow:hidden;">
		<h1>Inicio</h1>
		<a href="#login" data-icon="carat-l" class="ui-btn-left">atrás</a>
		<a href="#user-info" class="ui-btn-right">User</a>
	</div>
</div>
~~~
