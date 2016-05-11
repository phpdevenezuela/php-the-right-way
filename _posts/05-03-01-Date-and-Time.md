---
title:   Fecha y Hora
isChild: true
anchor:  fecha-y-hora
---

## Fecha y Hora {#fecha_y_hora}

PHP dispone de una clase llamada DateTime que le ayuda cuando lee, escribe, compara o hace cálculos con fechas y horas. Existen muchas funciones relacionadas con el manejo de fecha y hora en PHP además de DateTime, sin embargo, esta clase le provee de una excelente interfaz orientada a objetos para los usos más comunes. Puede manejar husos horarios, pero eso está fuera de esta breve introducción.

Para empezar a trabajar con DateTime, se debe convertir una cadena de fecha y la hora en un objeto usando el método `createFromFormat()` o ejecutando `new DateTime`, dicho objeto contendrá la fecha y la hora actuales. Use el método `format()` para convertir nuevamente DateTime a una cadena de salida válida.

{% highlight php %}
<?php
$raw = '15. 11. 1997';
$inicio = DateTime::createFromFormat('d. m. Y', $raw);

echo 'Fecha de inicio: ' . $inicio->format('d/m/Y') . "\n";
{% endhighlight %}

Hacer cálculos con DateTime es posible usando la clase DateInterval. DateTime dispone de métodos como `add()` o `sub()` que toman un objeto DateInterval como argumento. No escriba código que requiera de la misma cantidad de segundos cada día, dicho requerimiento sería invalido por los ajustes en los horarios de verano y los ajustes de los husos horarios. En vez de eso, use intervalos de fecha. Use el método `diff()` para calcular la diferencia entre dos fechas. Dicho método le retornará un nuevo objeto `DateInterval`, que será muy sencillo de mostrar.

{% highlight php %}
<?php
// Crear una copia de $inicio y sumarle 1 mes y 6 días
$final = clone $inicio;
$final->add(new DateInterval('P1M6D'));

$diff = $final->diff($inicio);
echo 'Diferencia: ' . $diff->format('%m mes, %d días (total: %a días)') . "\n";
// Diferencia: 1 mes, 6 días (total: 37 días)
{% endhighlight %}

Usted puede hacer comparaciones sencillas sobre objetos DateTime:

{% highlight php %}
<?php
if ($inicio < $final) {
    echo "¡El inicio es antes del fin!\n";
}
{% endhighlight %}

Pongamos un último ejemplo para demostrar el uso de la clase DatePeriod. Esta vez, para iterar sobre eventos periódicos. Puede tomar dos objetos DateTime, principio y fin, así como el intervalo para el que se retornarán todos los eventos entre ambos.

{% highlight php %}
<?php
// Retorna todos los jueves entre $inicio y $final
$periodInterval = DateInterval::createFromDateString('Primer jueves');
$periodIterator = new DatePeriod($inicio, $periodInterval, $final, DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $fecha) {
    // Muestra cada fecha en el período
    echo $fecha->format('Y-m-d') . ' ';
}
{% endhighlight %}

* [Leer acerca de la clase DateTime][datetime]
* [Leer acerca de como darle formato a fechas][dateformat] (Opciones aceptadas para darle formato a cadenas de fecha)

[datetime]: http://php.net/book.datetime
[dateformat]: http://php.net/function.date
