---
title: Trabajando con UTF-8
anchor: php-y-utf8
isChild: true
---

## Trabajando con UTF-8 {#php-y-utf8}

_Esta sección fue escrita originalmente por [Alex Cabal](https://alexcabal.com/) sobre [PHP Best Practices](https://phpbestpractices.org/#utf-8) y se ha utilizado como base para nuestros propias recomendaciones acerca de UTF-8 advice_.

### No hay una sola manera. Sea cuidadoso, detallista y consistente.

Ahora mismo, PHP no soporta Unicode a bajo nivel. Hay formas de asegurarse de que las cadenas UTF-8 sean procesadas correctamente, pero no es sencillo, además requiere que excarvemos en todos los niveles de nuestra aplicación web, desde HTML, pasando por SQL hasta PHP. Nos esforzaremos por hacer un breve resumen práctico.

### UTF-8 al nivel de PHP

Las operaciones básicas con cadenas, como la concatenación de dos cadenas o la asignación de cadenas a variables, sno necesitan nada especial de UTF-8. Sin embargo, la mayoría de las funciones para el manejo de cadenas como `strpos()` o `strlen()`, necesitan consideración especial. A menudo, estas funciones tienen su contrapartida con funciones `mb_*` como por ejemplo: `mb_strpos()` o `mb_strlen()`. Estas cadenas `mb_*` están disponibles para Usted vía la extensión para el manejo de [Cadenas de Caracteres Cadenas Multibyte](http://php.net/manual/es/book.mbstring.php), y están diseñadas específicamente para operar con cadenas Unicode.

Siempre debe usar las funciones `mb_*` para trabajar con cadenas Unicode. Por ejemplo, si usa `substr()` sobre una cadena UTF-8, hay una gran posibilidad de que el resultado incluya algunos caracteres ilegibles. La función adecuada a usar es su contrapartida multibyte, `mb_substr()`.

La parte difícil es acordarse de usar las funciones `mb_*` todo el tiempo. Si lo olvida sólo una vez, su cadena Unicode podría quedar ilegible luego de su procesamiento posterior.

No todas las funciones de cadena tienen una contrapartida `mb_*`. Si no existe alguna para hacer lo que desea, entonces podría haber perdido su suerte.

Debe usarse la función `mb_internal_encoding()` al principio de cualquier script PHP que escriba (o en la parte superior de su script global), y la función `mb_http_output()` justo después, si su script genera salidas hacia un navegador. Definiendo explícitamente la codificación de sus cadenas en cada script le ahorrará muchos dolores de cabeza en el camino.

Adicionalmente, muchas de las funciones PHP que operan sobre cadenas tienen un parámetro opcional que le permite especificar la codificación de caracteres. Siempre se debe indicar explícitamente UTF-8 cuando se les da la opción. Por ejemplo, `htmlentities()` tiene una opción para la codificación de caracteres, y siempre se debe especificar UTF-8 si se trata de este tipo de cadenas. Tenga en cuenta que a partir de PHP 5.4.0, UTF-8 es la codificación por defecto para `htmlentities()` y `htmlspecialchars()`.

Por último, si usted está construyendo una aplicación distribuida y no está seguro de que la extensión `mbstring` se habilitará, entonces considere el uso del paquete de Composer [patchwork/utf8](https://packagist.org/packages/patchwork/utf8). Esto le permitirá usar `mbstring` si está disponible, o usará funciones no UTF-8 en caso contrario.

### UTF-8 a nivel de la Base de Datos

Si su script accede a MySQL, hay grandes posibilidades de que sus cadenas sean almacenadas como cadenas No-UTF-8 aún habiendo tomado todas las precauciones anteriores.

Para asegurarse de que sus cadenas van de PHP a MySQL como UTF-8, establezca el juego de caracteres y el cotejamiento (collation) a `utf8mb4` para su base de datos y todas las tablas, use también `utf8mb4` en su cadena de conexión PDO. Vea el código de ejemplo a continuación. Esto es de _importancia crítica_.

Tenga en cuenta de que debe usar el juego de caracteres `utf8mb4` y no `utf8` para un soporte completo UTF-8. Lea más adelante para saber porque qué.

### UTF-8 a nivel del Navegador

Use la función `mb_http_output()` para asegurarse de que su script PHP genera una salida con cadenas UTF-8 hacia su navegador.

La respuesta HTTP le indicará al navegador que esa página debería considerarse como UTF-8. Anteriormente, para hacer esto, se incluía la [etiqueta `<meta>` charset](http://htmlpurifier.org/docs/enduser-utf8.html) en el `<head>` de la página. Esta solución es perfectamente válida, pero establecer el juego de caracteres en la cabecera `Content-Type` es [mucho más rápido](https://developers.google.com/speed/docs/best-practices/rendering#SpecifyCharsetEarly).

{% highlight php %}
<?php
// Le decimos a PHP que usaremos cadenas UTF-8 hasta el final del script
mb_internal_encoding('UTF-8');

// Le indicamos a PHP que necesitamos una salida UTF-8 hacia el navegador
mb_http_output('UTF-8');

// Nuestra cadena UTF-8 de prueba
$string = 'Êl síla erin lû e-govaned vîn.';

// Transformamos la cadena usando una función multibyte
// Observe que cortamos la cadena en un caracter NO-ASCII con propósitos de demostración
$string = mb_substr($string, 0, 15);

// Conectarse a la base de datos para almacenar la cadena transformada
// Observe el ejemplo PDO en este documento para más información
// ¡Observe el comando `set names utf8mb4`!
$link = new \PDO(
    'mysql:host=your-hostname;dbname=your-db;charset=utf8mb4',
    'your-username',
    'your-password',
    array(
        \PDO::ATTR_ERRMODE => \PDO::ERRMODE_EXCEPTION,
        \PDO::ATTR_PERSISTENT => false
    )
);

// Almacenamos nuestra cadena UTF-8 en nuestra base de datos
// Su BD y tablas están configuradas para usar el juego de caracteres y el cotejamiento (collation) utf8mb4, ¿correcto?
$handle = $link->prepare('insert into ElvishSentences (Id, Body) values (?, ?)');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->bindValue(2, $string);
$handle->execute();

// Recuperamos la cadena guardada para verificar que está correctamente almacenada
$handle = $link->prepare('select * from ElvishSentences where Id = ?');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->execute();

// Almacenamos el resultado en un objeto que nos permitirá generar HTML después
$result = $handle->fetchAll(\PDO::FETCH_OBJ);

header('Content-Type: text/html; charset=UTF-8');
?><!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Página de prueba UTF-8</title>
    </head>
    <body>
        <?php
        foreach($result as $row){
            print($row->Body);  // Esto debería mostrar correctamente en el navegador nuestra cadena UTF-8
        }
        ?>
    </body>
</html>
{% endhighlight %}

### Otras lecturas

* [PHP Manual: Operadores de Cadenas](http://php.net/manual/es/language.operators.string.php)
* [PHP Manual: Funciones de Cadenas](http://php.net/manual/es/ref.strings.php)
    * [`strpos()`](http://php.net/manual/es/function.strpos.php)
    * [`strlen()`](http://php.net/manual/es/function.strlen.php)
    * [`substr()`](http://php.net/manual/es/function.substr.php)
* [PHP Manual: Funciones de Cadenas de Caracteres Multibyte](http://php.net/manual/es/ref.mbstring.php)
    * [`mb_strpos()`](http://php.net/manual/es/function.mb-strpos.php)
    * [`mb_strlen()`](http://php.net/manual/es/function.mb-strlen.php)
    * [`mb_substr()`](http://php.net/manual/es/function.mb-substr.php)
    * [`mb_internal_encoding()`](http://php.net/manual/es/function.mb-internal-encoding.php)
    * [`mb_http_output()`](http://php.net/manual/es/function.mb-http-output.php)
    * [`htmlentities()`](http://php.net/manual/es/function.htmlentities.php)
    * [`htmlspecialchars()`](http://www.php.net/manual/es/function.htmlspecialchars.php)
* [PHP UTF-8 Cheatsheet](http://blog.loftdigital.com/blog/php-utf-8-cheatsheet)
* [Stack Overflow: What factors make PHP Unicode-incompatible?](http://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Stack Overflow: Best practices in PHP and MySQL with international strings](http://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [How to support full Unicode in MySQL databases](http://mathiasbynens.be/notes/mysql-utf8mb4)
* [Brining Unicode to PHP with Portable UTF-8](http://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)