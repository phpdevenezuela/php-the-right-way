---
title:   Paradigmas de Programación
isChild: true
anchor:  paradigmas_de_programacion
---

## Paradigmas de Programación {#paradigmas_de_programacion_title}

PHP es un lenguaje flexible y dinámico que permite usar una variedad de técnicas de programación. El lenguaje ha evolucionado dramáticamente a través de los años. Se añadió un modelo de objetos sólido en la versión 5.0 (2004), funciones anónimas y namespaces en PHP 5.3 (2009), y traits en PHP 5.4 (2012).

### Programación Orientada a Objetos

PHP tiene un conjunto muy completo de aspectos que facilitan la programación orientada a objetos (OOP) que incluye la habilidad de crear clases, clases abstractas, interfaces, herencia, constructores, clonación de objetos, excepciones y mucho más.

* [Leer más acerca de PHP Orientado a Objetos][oop]
* [Leer más acerca de Traits][traits]

### Programación Funcional

PHP tiene la capacidad de declarar funciones de primera clase, en otras palabras, una función puede ser asignada a un variable. Las funciones definidas por el usuario, así como las funciones del propio lenguaje, tienen la habilidad de ser referenciadas por un variable e invocadas dinámicamente. Las funciones pueden ser pasadas como argumentos a otras funciones (un aspecto llamado _Funciones de Orden Superior_) y pueden devolver otras funciones.

La recursividad, es un aspecto que le permite a una función a llamarse a sí misma. El lenguaje PHP habilita este tipo de algoritmos, sin embargo, la mayoría del código PHP se enfoca en iteración.

Las funciones anónimas (con soporte para [closure][closure-class]) están presentes en PHP desde la versión 5.3 (2009).

En PHP 5.4 se añadió la habilidad para vincular [closures][closure-class] al ámbito de un objeto y también se mejoró el soporte de funciones de tipo [callable][callables] para que puedan intercambiarse con funciones anónimas en casi todos los casos.

* Continúe leyendo acerca de la [Programación Funcional en PHP](/pages/Functional-Programming.html)
* [Leer acerca de las Funciones Anónimas][anonymous-functions]
* [Leer acerca de la Clase Closure][closure-class]
* [Más detalles en el RFC de Closures][closures-rfc]
* [Leer acerca de Callables][callables]
* [Leer acerca de cómo invocar dinámicamente funciones con `call_user_func_array()`][call-user-func-array]

### Metaprogramación

PHP soporta varias formas de meta-programación por medio de mecanismos como el API de Reflexión y los Métodos Mágicos. Hay muchos Métodos Mágicos disponibles como `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, y otros; Que permiten a los desarrolladores a conectarse con el comportamiento de la clase. A menudo los desarrolladores en Ruby dicen que a PHP le falta la función de `method_missing`, sin embargo los aspectos de esta función están disponibles en `__call()` y `__callStatic()`.

* [Leer acerca de Métodos Mágicos][magic-methods]
* [Leer acerca del API de Reflexión][reflection]
* [Leer acerca de Sobrecarga][overloading]


[oop]: http://php.net/es/language.oop5
[traits]: http://php.net/es/language.oop5.traits
[anonymous-functions]: http://php.net/es/functions.anonymous
[closure-class]: http://php.net/es/class.closure
[closures-rfc]: https://wiki.php.net/rfc/closures
[callables]: http://php.net/es/language.types.callable
[call-user-func-array]: http://php.net/es/function.call-user-func-array
[magic-methods]: http://php.net/es/language.oop5.magic
[reflection]: http://php.net/es/intro.reflection
[overloading]: http://php.net/es/language.oop5.overloading