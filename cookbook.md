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
3. Recordar los datos de un formulario
4. Sincronizar un objeto de configuración

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
4. Introducción a _React_
5. Introducción a _Angular JS_

## Parte I - Introducción al desarrollo web

## 1. Crear una aplicación web _HTML 5_

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

## 2. Modificar el diseño de una aplicación web utilizando _CSS_

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

## 3. Modificar la funcionalidad de una aplicación web utilizando _JavaScript_

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

## 4. Mostrar un menú de alerta personalizado

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

## 5. Consumir un servicio web en _json_
