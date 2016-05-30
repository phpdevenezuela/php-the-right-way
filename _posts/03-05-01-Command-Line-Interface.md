---
title:   Línea de Comando (CLI)
isChild: true
anchor:  linea_de_comando
---

## Línea de Comando (CLI) {#linea_de_comando_title}

PHP fue creado principalmente para desarrollar aplicaciones web, pero también es muy útil para implementar programas que corren en la interface de línea de comando (CLI, por sus siglas en inglés). Los programas de línea de comando en PHP pueden ayudarle a automatizar tareas comunes como pruebas, despliegues y la administración de aplicaciones.

Los programas CLI en PHP son muy potentes porque el código de la aplicación se puede utilizar directamente sin tener que crear o asegurar un GUI web para su uso. Por esta razón, ¡asegúrese de no colocar sus programas CLI en su directorio raíz público!

Intente correr PHP desde la línea de comando:

{% highlight console %}
> php -i
{% endhighlight %}

La opción `-i` imprimirá la configuración de PHP, como sucede con la función [`phpinfo()`][phpinfo].

La opción `-a` habilita una consola interactiva muy similar al IRB de Ruby o a la consola interactiva de Python. Existen varias [opciones de línea de comando][cli-options] que resultan muy útiles.

Vamos a escribir un programa simple que imprima “Hola, $nombre”. Para empezar, crearemos un archivo llamado `hola.php` como se muestra a continuación:

{% highlight php %}
<?php
if ($argc !== 2) {
    echo "Instrucciones de Uso: php hola.php [nombre]\n";
    exit(1);
}
$nombre = $argv[1];
echo "¡Hola, $nombre!\n";
?>
{% endhighlight %}

PHP tiene disponibles dos variables especiales basados en los argumentos que recibe el programa el ser ejecutado. La variable de tipo _integer_ [`$argc`][argc] contiene el número de argumentos y la variable de tipo _array_ [`$argv`][argv] que contiene el valor de cada uno de los argumentos que se pasaron durante la ejecución. El primer argumento siempre es el nombre del archivo del programa PHP, que en este caso es `hola.php`.

La expresión `exit()` se puede usar con un número distinto a cero para dejarle saber a la consola que el comando ha fallado. [Aquí puede encontrar los códigos de salida usados comúnmente][exit-codes].

Para ejecutar el programa desde la línea de comando:

{% highlight console %}
> php hola.php
Instrucciones de Uso: php hola.php [nombre]
> php hola.php Mundo
¡Hola Mundo!
{% endhighlight %}

 * [Leer acerca de ejecutar PHP desde la Línea de Comandos][php-cli]
 * [Leer acerca de configurar y ejecutar la línea de Comandos en Windows][php-cli-windows]

[phpinfo]: http://php.net/es/function.phpinfo
[cli-options]: http://php.net/es/features.commandline.options
[argc]: http://php.net/es/reserved.variables.argc
[argv]: http://php.net/es/reserved.variables.argv
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&amp;topic=sysexits
[php-cli]: http://php.net/es/features.commandline
[php-cli-windows]: http://php.net/es/install.windows.commandline
