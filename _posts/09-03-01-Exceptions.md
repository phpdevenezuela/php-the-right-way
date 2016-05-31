---
title:   Excepciones
isChild: true
anchor:  excepciones
---

## Excepciones {#excepciones_title}

Las Excepciones son una parte estándar de los lenguajes de programación mas populares, pero frecuentemente son pasados por alto por programadores PHP. Lenguajes como Ruby son extremadamente estrictos en el manejo de Excepciones, por lo que cada vez que algo va mal como una petición HTTP fallida, o una consulta a la DB esta equivocada, o incluso si un recurso como una imagen no puede ser encontrado, Ruby (o las gemas instaladas) arrojará una excepción en la pantalla para hacerle saber instantáneamente que hay un error.

PHP es muy poco exigente con esto, y una llamada a `file_get_contents()` generalmente solo obtendría un `FALSE` y una advertencia. Muchos framework antiguos como CodeIgniter solo retornaría un false, registraría un mensaje en su propiedad logs y tal vez le dejaría usar un método como `$this->upload->get_error()` para ver lo que salio mal. El problema aquí es que tiene que ir buscando el error y verificar la documentación para ver cual es el método de error es para esta clase, en lugar de tener lo que hizo de forma obvia.

Otro problema es cuando automáticamente las clases arrojan un error en pantalla y salen del proceso. Cuando hace esto impedirá que otro desarrollador pueda manejar ese error de forma dinámica. Las excepciones puede ser arrojadas para que otro desarrollador este consciente de un error; y así ellos puedan elegir como manejarlo. Por ejemplo:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // Falla la Validación
}
catch(Fuel\Email\SendingFailedException $e)
{
    // El manejador no puede enviar el Correo
}
finally
{
    // ejecutado sin importar si se ha sido arrojada una excepcion y antes de que la reaunudar la ejecución normal.
}
{% endhighlight %}

### Excecpciones SPL

La clase genérica `Exception` provee muy poco contexto de depuración para el desarrollador; Sin embargo, para remediarlo, es posible crear un tipo de `Exception` especializada con una sub-clases de la clase genérica `Exception`:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Esto significa que puede agregar múltiples bloques catch y manejar las diferentes Excepciones de distintas maneras. Esto lo puede llevar a la creación de muchas Excepciones personalizadas, algunas de las cuales podrían haber sido evitadas usando las Excepciones SPL proporcionadas en la [Extensión SPL][splext].

Si por ejemplo usa el Método Mágico `__call()` y un método invalido es solicitado entonces en lugar de arrojar una Excepción estándar (lo cual seria muy vago), o crear una Excepción personalizada solo para esto, podría solo `throw new BadMethodCallException;`. 

* [Leer sobre Excepciones][exceptions]
* [Leer sobre Exceciones SPL][splexe]
* [Anidando Excepciones en PHP][nesting-exceptions-in-php]
* [Buenas Prácticas para Excepciones en PHP 5.3][exception-best-practices53]


[splext]: /#standard_php_library
[exceptions]: http://php.net/language.exceptions
[splexe]: http://php.net/spl.exceptions
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
