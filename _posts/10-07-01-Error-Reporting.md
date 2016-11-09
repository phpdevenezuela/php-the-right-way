---
title:   Reporte de Errores
isChild: true
anchor:  reporte_de_errores
---

## Reporte de Errores {#reporte_de_errores_title}

El registro de errores puede ser muy útil para encontrar los lugares donde existen problemas en su aplicación, pero también puede exponer información acerca de la estructura de su aplicación al exterior. Para proteger efectivamente su aplicación de problemas que pudieran ser causados por la salida de mensajes de error, necesita configurar su servidor de desarrollo de diferente manera que su servidor de producción.

### Desarrollo

Para mostrar los errores durante el **desarrollo** de su aplicación, configure las siguientes opciones en su archivo `php.ini`:

{% highlight ini %}
display_errors = On
display_startup_errors = On
error_reporting = -1
log_errors = On
{% endhighlight %}

> Pasando el valor `-1` se mostrarán todos los posibles errores, aún cuando nuevos niveles y constantes sean agregados en futuras versiones de PHP.
> La constante `E_ALL` tiene el mismo comportamiento desde la versión 5.4.0. - [php.net](http://php.net/es/function.error-reporting)

La constante `E_STRICT` fue introducida en la versión 5.3.0 y no es parte de `E_ALL`, sin embargo, se convirtió en parte de `E_ALL`a partir de la versión 5.4.0. ¿Qué significa esto? Pues, que para mostrar todos los posibles errores en la versión 5.3 debes usar los valores `-1` o `E_ALL | E_STRICT`.

**Reportando cada posible error por versión de PHP**

* &lt; 5.3 `-1` o `E_ALL`
* &nbsp; 5.3 `-1` o `E_ALL | E_STRICT`
* &gt; 5.3 `-1` o `E_ALL`

### Producción

Para ocultar los errores en su entorno de producción, configure su archivo `php.ini` de la siguiente manera:

{% highlight ini %}
display_errors = Off
display_startup_errors = Off
error_reporting = E_ALL
log_errors = On
{% endhighlight %}

Con estas opciones en su entorno de producción, los errores seguirán siendo alamcenados en los registros de errores de su servidor web, pero no serán mostrados al usuario. Para más información en cuanto a estas opciones, vea el manual de PHP:

* [error_reporting](http://php.net/es/errorfunc.configuration#ini.error-reporting)
* [display_errors](http://php.net/es/errorfunc.configuration#ini.display-errors)
* [display_startup_errors](http://php.net/es/errorfunc.configuration#ini.display-startup-errors)
* [log_errors](http://php.net/es/errorfunc.configuration#ini.log-errors)
