# Diseño Web Adaptativo usando HTML5, CSS3 y Javascript Avanzado

Instructor: Alan Badillo Salas (badillo.soft@hotmail.com | @badillosoft)

Repositorio del curso Diseño Web Adaptativo usando HTML5, CSS3 y Javascript Avanzado.

## Sesión 1

En esta sesión revisamos:

* El diseño en CSS: diseño separado del esqueleto de la aplicación (maquetado)
* _Pseudo-Clases_: variaciones de los selectores cuando ocurre un evento o estado `:hover` | `:focus` | `active`
* _Pseudo-Elementos_: variaciones de los selectores ofrecidas por el contexto `::fist-line` | `::first-child`
* _Selectores por Atributo_: variaciones de los selectores por el valor específico de un selector `input[type="text"]`
* _Flexbox_: sistema de cajas responsivas dividida en propiedades del padre y propiedades de los hijos `display: flex` | `justify-content: center`
* La propiedad _Content_: propiedad que inserta contenido generado antes, durante o después del renderizado `p:after { content: "Hola" }` | `p:before { content: counter(myConter) ".- " }`
* Los _Data-Atributes_: son atributos del usuario insertados en las etiquetas _html_ que no afectan a los atributos estándar `<p data-author="ash"` | `p:after { content: " (" attr(data-author) ")"  }`
* _Micro-Formatos_: son clases que relacionan el contenido con un formato `class="vcard"` | `class="fn n nickname"`
* _Micro-Datos_: indican información sobre el contenido de nuestra clase mediante los atributos `itemscope`, `itemprop`, `itemtype`. Ejemplo `<div itemscope itemtype="http://schema.org/Person>"` | `<p itemprop="name">Ash</p>`
* Como implementar una tarjeta de presentación con _microdatos_ y _microformatos_
* Introducción a los formatos _XML_ y _JSON_: son formatos legibles por el humano para representar datos `<Persona><nombre>Ash</name></Persona>` | `{ "name": "Ash", "friends": ["Brook", "Misty"] }`
* Introducción a _javascript_: variables y funciones: las variables pueden almacenar los tipos `Object {}`, `Array []`, `Number 1, 1.23`, `String "Hola", 'mundo'`, `Boolean true, false`, `Nulleables null, undefined` y `Functions function (a, b, ...) { ... }`. Las funciones pueden ser nombradas `function suma(a, b) { return a + b }` o anónimas `var multi = function (a, b) { return a * b; }`.
* Delegados en _javascript_ y la función `setTimeout`: los delegados son variables en objetos que son llamados como funciones cuando ocurre un evento `var btn = document.getElementById("my_id"); btn.onclick = function () { console.log("Me han pulsado :O") };`. `setTimeout(fn, time);` llama a la función `fn` una vez transcurrido `time` dado en milisegundos `setTimeout(function () { alert("Hola"); }, 5000);`

### Ejercicios realizados

* [Ejercicio 1](https://thimbleprojects.org/badillosoft/89031): se creó un menú de navegación y controles de un formulario utilizando `pseudoclases` y `flexbox`
* [Ejercicio 2](https://thimbleprojects.org/badillosoft/89039): se creó una lista de elementos utilizando `counters`, la propiedad `content`, `pseudoclases` y los `data-attributes`
* [Ejercicio 3](https://thimbleprojects.org/badillosoft/89080): se creó una targeta de presentación utilizando `box-shadow`, `border-radius`, `display: block`, `display: inline-block`, `microdatos` y `microformatos`
* [Ejercicio 4](https://thimbleprojects.org/badillosoft/89097): se creó un script que muestra el uso de variables y funciones en _javascript_
* [Ejercicio 5](https://thimbleprojects.org/badillosoft/89171): se creó una caja de bienvenida en _css_ que se muestra al cargar la ventana sobrecargando el delegado `window.onload` y transcurridos 2 segundos `setTimeout(function () { div.style.display = "block"; }, 2000);`

## Sesión 2

* Calculadora: uso de las técnicas de diseño y programación aprendidas.
* Sistema de rejilla: consiste en dividir la pantalla en 12 columnas y definir 12 clases `col-1, col-2, ..., col-12` para combinarlas y sumar 12 para obtener el 100% de la pantalla.
* Instalar una fuente de letra extenrna: mediante el decorador `@fontface` se integra un archivo que define una letra en nuestra página. `@font-face { font-family: lucida; src: url(lucon.ttf); }` para utilizar la fuente tenemos `selector { font-family: lucida }` donde `lucida` es el nombre que queremos darle a la fuente y `lucon.ttf` es el archivo de la fuente.
* Definir una funcionalidad usando los eventos `on`: desde la etiqueta _html_ podemos definir la funcionalidad de un elemento especificando los atributos `on`, por ejemplo `<button onclick="saludar()">` y en el _script_ definimos la funciòn `saludar`, `<script>function saludar() { alert("Hola mundo"); }</script>` también podemos pasar argumentos: `<button onclick="saludar('Hola')">` y en el _script_ definimos la funciòn `saludar`, `<script>function saludar(mensaje) { alert(mensaje); }</script>`.
* Consumir un webservice: definición de servicio web, que es una _url_ que provee `datos cocinados` como un _json_ o _xml_. Para consumirlo ubicamos la url que nos proveerá los datos, por ejemplo [randomuser.me/api](https://randomuser.me/api) y realizamos una petición `ajax` mediante _jquery_: `$ajax({ url: "https://randomuser.me/api", dataType: "json", success: function(data) { console.log(data); } });`, donde `succeess` es el _delegado_ que define que hacer con los datos devueltos por el servidor.
* Transiciones: especifican una animación en _css_ de un estado a otro, cuando se activa la propiedad `transition` con la duración específica, entonces el diseño es suave entre el estado anterior y el nuevo sobre la propiedad especificada: `selector { transition: width 2s }` y `div:hover {  width: 0px }` hacen que los elementos `div` desparezcan cuando el cursor está encima de ellos.
* Transformaciones: transforman elementos mediante _css_ antes de ser renderizados: `h1 { transform: rotate(-90deg) }` rota 90 grados a la izquierda (sentido contrario a las manecillas del reloj) los elementos `h1`. Se pueden aplicar varias transformaciones y serán aplicadas de derecha a izquierda, algunas comunes son `rotate(angle)`, `scale(x, y)`, `translate(x, y)`.

### Ejercicios realizados

* [Ejercicio 1](https://thimbleprojects.org/badillosoft/89363): se creó una calculadora funcional aplicando el diseño de la calculadora de _osx_
* [Ejercicio 2](https://thimbleprojects.org/badillosoft/90071): se creó consumió el servicio web de https://randomuser.me/api mediante una petición `ajax`
* [Ejercicio 3](https://thimbleprojects.org/badillosoft/89402): se creó un menú lateral con efecto de transición y un logo utilizando transformaciones

## Sesión 3

* Alamcenamiento local: consiste en guardar datos en el navegador mediante `localStorage` y `sessionStorage` los cuales permiten almacenar cadenas asociadas a una clave. El almacenamiento local significa almacenamiento persistente que podrá recuperarse tras cerrar el navegador al menos que se borren todos los datos de navegación del sitio. El almacenamiento por sesión persistirá mientras el navegador este abierto. Si queremos guardar un valor debemos utilizar `localStorage.setItem("mi_clave", "mi valor")` o `sessionStorage.setItem("mi_clave", "mi valor")`. Para recuperar un valor hacemos `localStorage.getItem("mi_clave")` o `sessionStorage.getItem("mi_clave")`. Adicionalmente podemos eliminar un valor con `localStorage.removeItem("mi_clave")` o `sessionStorage.removeItem("mi_clave")`.
* Media Querys: en _css_ podemos definir un estilo completo o parcial para cuando ocurren ciertas reglas en el dispositivo como en la pantalla `screen` o en la impresora `printer`. Así por ejemplo podemos aplicar un diseño cuando ocurre un máximo o mínimo de tamaño de pantalla u orientación, ejemplo `@media screen and (max-width: 600px) and (min-width: 300px) { body { background-color: red; } }` establece un fondo de pantalla rojo cuando la pantalla tiene un mínimo de `300px` y un máximo de `600px`.
* La función `calc`: esta función en _css_ nos permite hacer un calculo entre porcentajes y pixeles u otras unidades, ejemplo `left: calc(50% - 150px)` empuja un elemento al 50% de la pantalla y le quita `150px`, si el elemento mide de ancho `300px` este quedará centrado.
* Animaciones: en _css_ podemos hacer animaciones en distintas propiedades utilizando los `kyframes` que son los estados que componen al diseño. Podemos hacer animaciones `from-to` donde especificamos un estado inicial y uno final o porcentajes de `0%% a 100%` donde especificamos el estado en cada porción de la animación, ejemplo `@keyframes giro { from { transform: rotate(0deg); } to { transform: rotate(90deg); } }` la cual define una animación que transforma un elemento y lo rota 90 grados. Para aplicar la animación hacemos `selector { animation-name: giro; animation-duration: 2s; }` puedes revisar otras opciones en http://www.w3schools.com/css/css3_animations.asp

### Ejercicios realizados

* [Ejercicio 1](https://thimbleprojects.org/badillosoft/90132): se creó una aplicación que recuperar valores guardados localmente y por sesión.
* [Ejercicio 2](https://thimbleprojects.org/badillosoft/90138): se creó una aplicación que muestra un formulario para ingresar usuarios aplicando los conceptos de almacenamiento, consumo de webservices y transiciones. El formulario valida usuarios generados por https://randomuser.me/api.
* [Ejercicio 3](https://thimbleprojects.org/badillosoft/90241): se creó una aplicación que muestra diferentes animaciones que se pueden construir en _css_.

## Sesión 4

* Mapas de Google: la _API_ permite mostrar mapas en la aplicación. Necesitamos un contenedor `div` donde mostrar el mapa, luego creamos un objeto llamado mapa como en la siguiente receta:

> __JS__ - Crear un objeto mapa

~~~js
var map = null;

function initialize() {
	var properties = {
		center: new google.maps.LatLng("19.1234", "-99.1234"),
		zoom: 16
		mapType: google.maps.MapType.ROADMAP
	};
	
	var box_map = document.getElementById("box_map");
	
	map = new google.maps.Map(box_map, properties);
}

google.maps.event.addDomListener(window, 'load', initialize());
~~~

> __JS__ - Centrar el mapa a una posición

~~~js
var position = new google.maps.LatLng("19.1234", "-99.1234");

map.setCenter(position);
~~~

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

* Elementos dinámicos: son elementos _html_ que podemos generar desde _javascript_. Para generar un elemento dinámico utilizamos la función `document.createElement("type")` donde `type` es el tipo de elemento que queremos crear, ejemplo suponiendo que existe `<div id="mi_div"></div>`, si queremos insertar una imagen dentro del `div` seguimos la siguiente receta

> __JS__ - Insertar una imagen dinámicamente en `mi_div`

~~~js
// Recuperamos el elemento `div` con id `mi_div`
var mi_div = document.getElementById("mi_div");

// Creamos un elemento de tipo `img`
var img = document.createElement("img");

// Ajustamos el atributo `src`
img.src = "cat.png";
// Ajustamos el atributo `data-author`
img.dataset.author = "badillosoft";
// Ajustamos el estilo
img.style.borderRadius = "50%";

// Insertamos el elemento dinámico `img` en el `div`
mi_div.appendChild(img);
~~~

### Ejercicios realizados

* [Ejercicio 1](https://thimbleprojects.org/badillosoft/90241): se creó una aplicación que activa un panel mediante un enlace y la ``pseudo-clase` de _css_ `:target`.
* [Ejercicio 2](https://thimbleprojects.org/badillosoft/90132): se creó una aplicación que muestra un mapa centrado en el zócalo de la ciudad de méxico con un menú que muestra 3 lugares a los que se puede centrar el mapa.
* [Ejercicio 3](https://thimbleprojects.org/badillosoft/90138): se creó una aplicación derivada del `Ejercicio 1` la cual consume un servicio web que provee los lugares, su descripción y una imagen.
* [Ejercicio 4](https://thimbleprojects.org/badillosoft/90427): se creó una aplicación que utiliza el _web api_ `navigator.onLine` para determinar si la aplicación tiene acceso a internet.

## Sesión 5

* Canvas: la nueva etiqueta `<canvas>` introducida en _html 5_ permite dibujar y hacer animaciones más complejas que en _css_. Para utilizar _canvas_ debemos recuperar el contexto 2d de la etiqueta y ajustar algunos métodos para dibujar y actualizar las variables de control como se muestra en la siguiente receta:

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

// Colocamos las variables de control
var x = 0;

// Actualizamos las variables de control
function update() {
	x += 1;
	
	// Creamos el loop para actualizar cada 60 fps aproximadamente
	requestAnimationFrame(update);
}

// Dibujamos objetos usando o no las variables de control
function draw() {
	// Borramos toda la pantalla
	ctx.clearRect(0, 0, canvas.width, canvas.height);
	
	// Creamos un gradiente usando la variable de control
	var grd = ctx.createLinearGradient(x, 20, x + 50, 20);

	// Agregamos colores al gradiente
	grd.addColorStop(0, "#f00");
	grd.addColorStop(1, "#00f");

	// Ajustamos el color de relleno al gradiente
	ctx.fillStyle = grd;
	// Dibujamos un rectángulo relleno (será el gradiente su relleno)
	ctx.fillRect(x, y, 50, 50);

	// Ajustamos el color de contorno a salmón
	ctx.strokeStyle = "rgb(255, 84, 84)";
	// Dibujamos el contorno de un rectángulo
	ctx.strokeRect(40, 80, 50, 50);

	// Creamos el loop para dibujar cada 60 fps aproximadamente
	requestAnimationFrame(draw);
}
~~~

* JQuery: es una librería para _javascript_ la cual facilita seleccionar elementos _html_, ejemplo, `$("h1")` selecciona todos los elementos `h1` e implementa funcionalidad sobre ellos, ejemplo `$("h1").css("color", "red")` cambia el color de funte a rojo para todos los elementos seleccionados. `$(".active").hide()` oculta todos los elementos con la clase `active` y `$(".active").show()` los muestra. También existen los métodos `fadeIn`, `fadeOut`, `slideUp`, `slideDown` entre otros. Los métodos `on("event", function () { ... })` invocan a la función cuando ocurre el evento `event`, ejemplo, `$("#my_btn").on("click", function () { alert("Hola mundo"); })` muestra una alerta con el texto `hola mundo` cuando ocurre el evento `onclick` sobre el botón con id _my_btn_. También podemos crear elementos dinámicos insertando etiquetas dentro del selector, ejemplo, `var btn = $("<button>Hola</button>")` e insertarlas en otros elementos `$("body").append(btn)` o `btn.appendTo($("body"))`.
* JQuery Mobile: es una librería extendida para integrar proyectos en diversos dispositivos móviles haciendo que el diseño se adapte. Puede encontrar algunos demos para armar un proyecto en http://demos.jquerymobile.com/1.4.5/

### Ejercicios realizados

* [Ejercicio 1](https://thimbleprojects.org/badillosoft/90444): se creó una aplicación que muestra un rectángulo con gradiente rebotando en _canvas_.
* [Ejercicio 2](https://thimbleprojects.org/badillosoft/91059): se creó una aplicación que muestra los beneficios de utilizar _jquery_.
* [Ejercicio 3](https://thimbleprojects.org/badillosoft/90482): se creó una aplicación que introduce algunos conceptos de _jquery mobile_.

https://api.mlab.com/api/1/databases/badillosoft/collections/places?apiKey=ayRRQWTsfrXOpE8za6m5FlXBXXPytqSf

Flip Book en Canvas: https://dl.dropboxusercontent.com/u/7235888/jpageflipper/index.html
http://www.20thingsilearned.com/es-ES/home
