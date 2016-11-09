---
title:   Filtrado de Datos
isChild: true
anchor:  filtrado_de_datos
---

## Filtrado de Datos {#filtrado_de_datos_title}

Nunca, jamás, confíes en los datos que provienen del exterior de tu aplicación PHP. Siempre limpia y verifica los datos de entrada antes de usarlos en el código. Las funciones `filter_var()` y `filter_input()` proporcionan limpieza de los datos y verifican la validez del formato del texto (por ejemplo, las direcciones de correo electrónico).

Los datos de entrada exteriores pueden contener cualquier cosa: los datos provenientes de formularios en `$_GET` y `$_POST`, algunos valores provenientes del superglobal `$_SERVER`, el cuerpo de la solicitud HTTP vía la función `fopen('php://input', 'r')`. Recuerde que la entrada externa de datos no está limitada a los datos que provienen de un usuario a través de un formulario, también provienen de la subida y descarga de archivos, valores de sesión, datos de cookies, y los servicios web externos.

Aunque los datos que provienen del exterior pueden ser guardados, combinados y se puede acceder a ellos posteriormente, todavía siguen siendo datos externos. Cada vez que procesa, imprime, concatena, o los incluye con otros datos en el código, pregúntate si los datos han sido filtrados apropiadamente y si son confiables.

Los datos pueden ser _filtrados_ de diferente manera dependiendo de su propósito. Por ejemplo, cuando se pasan datos sin filtrar a la salida de HTML de una página, se corre el riesgo de ejecutar código sin verificar de HTML o JavaScript en el sitio. Esto es conocido (en inglés) como Cross-Site Scripting (XSS), y puede causar mucho daño a su aplicación. Una manera de prevenir estos ataques es limpiar todas las etiquetas de HTML en sus datos de entrada removiéndolas con la función `strip_tags()` o convirtiéndolas en entidades de HTML con las funciones `htmlentities()` o `htmlspecialchars()`.

Otro ejemplo es cuando se pasan opciones que van a ser ejecutadas en la línea de comando. Esto puede ser extremadamente peligroso y en general no es una buena idea. Sin embargo, puede usar la función `escapeshellarg()` que viene incluida en PHP para limpiar los argumentos de ejecución de un comando.

One last example is accepting foreign input to determine a file to load from the filesystem. This can be exploited by
changing the filename to a file path. You need to remove `"/"`, `"../"`, [null bytes][6], or other characters from the
file path so it can't load hidden, non-public, or sensitive files.

Un último ejemplo es el de aceptar la entrada de datos para determinar que archivo se necesita cargar del sistema de archivos. Esto puede ser explotado al cambiar el nombre del archivo a una ruta de archivo diferente. En este caso es necesario remover los caracteres `"/"`, `"../"`, [bytes nulos][6] y otros de la ruta de archivo para que no permita cargar archivos escondidos, no públicos, o sensibles.

* [Lee acerca del filtrado de datos][1]
* [Lee acerca de `filter_var`][4]
* [Lee acerca de `filter_input`][5]
* [Lee acerca del manejo de bytes nulos][6]

### Saneamiento

El saneamiento remueve (o evita) los caracteres ilegales o inseguros que provienen de la entrada de datos externa.

Por ejemplo, deberías sanear la entrada de datos antes de incluirla en el código HTML o insertarla a una consulta de SQL. Cuando utiliza parámetros consolidados con [PDO](#bases_de_datos), este saneará la entrada de datos automáticamente.

A veces es requerido permitir que algunas etiquetas de HTML que se consideren inofensivas puedan ser incluidas en la entrada de datos para una página de su sitio. Esto es algo muy difícil de realizar de una manera segura y muchos lo evitan al usar otros estándares de formato de texto más restrictivos como Markdown o BBCode, aunque librerías que proveen una lista blanca de etiquetas como el [HTML Purifier][html-purifier] se concibieron por esta razón.

[Vea los filtros de Saneamiento][2]

### Deserializar

Es peligroso utilizar la función `unserialize()` para manipular datos provenientes de fuentes desconocidas o de poca confianza. Haciendo esto se le puede permitir a usuarios malintencionados instanciar objetos (con propiedades definidas por el usuario) cuyos destructores serán ejecutados, **incluso si los objetos no se utilizan**. Por lo tanto se debe evitar deserializar datos en los que no se confíe.

Si es absolutamente necesario deserializar datos desde orígenes de poca confianza, use la opción [`allowed_classes`][unserialize] añadida desde a versión PHP 7, que restringe cuales tipos de objetos se les permitirá ser deserializados.

### Validación

La validación asegura que lo que contiene la entrada de datos es lo se esperaba. Por ejemplo, quizás deseas validar una dirección de correo electrónico, un número telefónico, o la edad de un usuario al procesar una solicitud de registro.

[Ver los Filtros de Validación][3]

[1]: http://php.net/es/book.filter
[2]: http://php.net/es/filter.filters.sanitize
[3]: http://php.net/es/filter.filters.validate
[4]: http://php.net/es/function.filter-var
[5]: http://php.net/es/function.filter-input
[6]: http://php.net/es/security.filesystem.nullbytes
[html-purifier]: http://htmlpurifier.org/
[unserialize]: https://secure.php.net/manual/es/function.unserialize.php