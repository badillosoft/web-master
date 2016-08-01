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
