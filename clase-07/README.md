# Diseño y Nuevos Medios → Clase 7  

### Miércoles 17 de abril → jQuery & JSON

#### jQuery

jQuery es una [biblioteca](https://es.wikipedia.org/wiki/Biblioteca_(informática)) de JS que simplifica:

- la manipulación del DOM; 

- el manejo de eventos;

- el desarrollo de animaciones; y 

- el uso de [AJAX](https://www.codementor.io/sheena/ajax-tutorial-web-development-du107rzaq) (Asynchronous JavaScript And XML; una tecnología que permite a una página web actualizarse de forma dinámica sin que tenga que cargarse completamente).

jQuery se puede incluir o vincular a una página web entre etiquetas `<script></script>`. Y funcionará sí y sólo sí ya ha sido vinculada la biblioteca correspondiente: 

```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script>
  //Aquí puedes usar JS simplificado por jQuery
</script>
```

Luego, para utilizar los atajos que ofrece esta biblioteca hay que recordar que, en una oración, el sujeto es quien realiza la acción o de quien se dice algo. Mientras que el predicado describe la acción que realiza el sujeto o lo que se dice del sujeto. Habiendo recordado eso, será fácil comprender qué puede resultar de esto: 

```$("sujeto").predicado();```

Así, por ejemplo, podemos escribir `$(".test").hide()` para indicar que queremos esconder (*hide*) a todos los elementos con clase `test`. ¿Pero bajo qué condiciones esconderlos? Esa condición aún no la definimos, y podríamos hacerlo de la siguiente manera:
 
```
$("button").click(function(){
  $(".test").hide(1000);
});
```

Allí tenemos dos "oraciones". La primera tiene como sujeto a cualquier botón (*button*) y la segunda tiene como sujeto a cualquier elemento de clase *test*. El predicado de la primera es "hacer click" (*click*), mientras el predicado de la segunda es "esconder" (*hide*). Si nos fijamos en los paréntesis `({` y `})`, podemos notar que la segunda oración depende de la primera, con lo que se realizará la acción de la segunda una vez se realice la acción de la primera.

A propósito de paréntesis, una recomendación: Escribir las "oraciones" de jQuery en un contexto que asegure que el documento esté completamente cargado

```
$(document).ready(function(){

  // aquí dentro irían todas las "oraciones" de jQuery que necesitemos.

});
```

Si juntamos todo lo expuesto, tenemos lo siguiente: 

```
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $(".test").hide(1000);
  });
});
</script>
```

Para comenzar a explorar jQuery es conveniente tener un ayudamemoria a la mano: [jQuery CheatSheet](https://htmlcheatsheet.com/jquery/)

#### JSON

[JSON (JavaScript Object Notation)](https://www.json.org/json-es.html) es un formato de texto sencillo para el intercambio de datos. Uno puede tomar un JSON en línea y "parsearlo" para que sus datos se conviertan en los datos de una variable en un JS. 

Tomemos, por ejemplo, este JSON con un sumario de los últimos movimientos telúricos sobre 4.5 que han sido registrados en las últimas 24 horas la USGS: https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_day.geojson

Para almacenar sus datos en una variable de nombre `a` utilizando JS, tenemos que escribir:

```
var request = new XMLHttpRequest();
request.open('GET', ' https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_day.geojson', true);
request.onload = function () {
  var a = JSON.parse(this.response);
  console.log(a);
}
request.send();	
```

Pero se puede escribir menos si utilizamos jQuery: 

```
$.getJSON('https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/4.5_day.geojson', function(a) {
  console.log(a);
});
```
Luego, la será la variable `a` la que contendrá los datos de tal JSON, de acuerdo a las "reglas gramaticales" que correspondan al caso; sea un objeto, un arreglo con objetos, un objeto con arreglos, etc. 

Para el JSON que nos ofrece la USGS, la consulta por la magnitud del temblor más reciente es `a["features"][0]["properties"]["mag"]` ó `a.features[0].properties.mag`

La estructura y sus detalles se explican bajo el subtítulo de "Output" en: https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php


- - - - - - -

#### Referencias:

jQuery:

- [Conceptos básicos de jQuery](https://www.arkaitzgarro.com/jquery/capitulo-3.html#conceptos-basicos-de-jquery)

- [Curso gratis de jQuery](https://codigofacilito.com/cursos/jquery)

- [How jQuery Works](https://learn.jquery.com/about-jquery/how-jquery-works/)

- [Quakit - jQuery Tutorial](https://www.quackit.com/jquery/tutorial/what_is_jquery.cfm)

- [w3schools - jQuery Tutorial](https://www.w3schools.com/jquery/default.asp)

JSON:

- https://github.com/dariusk/corpora

- https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php

- https://jsonlint.com/

- - - - - - - 

###### [SIGUIENTE CLASE →](https://github.com/profesorfaco/dno037-2019/tree/gh-pages/clase-08)
