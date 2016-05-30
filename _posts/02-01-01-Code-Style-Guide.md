---
title:  Guía de estilo de programación
anchor: guia_de_estilo_de_programacion
---

# Guía de estilo de programación {#guia_de_estilo_de_programacion_title}

La comunidad de PHP es grande y diversa, compuesta de innumerables librerías, frameworks y componentes. Es común para los desarrolladores PHP elegir varios de estos componentes y combinarlos dentro de un mismo proyecto. Por esto es importante que el código PHP se adhiera (en la medida de las posibilidades) a un estilo de programación común que permita de manera sencilla combinar e integrar varias librerías en sus proyectos.

El [Framework Interop Group][fig] ha propuesto y aprobado una serie de recomendaciones de estilos. No todas ellas relacionadas al estilo de programación, pero si algunas como [PSR-0][psr0], [PSR-1][psr1], [PSR-2][psr2] y [PSR-4][psr4]. Estas recomendaciones son simplemente un grupo de reglas que algunos proyectos como Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium entre otros están comenzando a adoptar. Puedes usarlas para tus proyectos o seguir utilizando tu propio estilo de programación.

Lo ideal sería que escribas código PHP que se adhiera a un estándar conocido. Dicho estándar pudiese ser cualquier combinación de los PSR mencionados anteriormente, o algún estándar de programación creado por PEAR o ZEND. Esto con la finalidad que otros desarrolladores puedan leer y trabajar con tu código de manera sencilla y las aplicaciones que implementen tus componentes puedan tener consistencia aunque estén trabajando con código de un tercero.

* [Más sobre PSR-0][psr0]
* [Más sobre PSR-1][psr1]
* [Más sobre PSR-2][psr2]
* [Más sobre PSR-4][psr4]
* [Más sobre PEAR Coding Standards][pear-cs]
* [Más sobre Symfony Coding Standards][symfony-cs]

Otra recomendación es usar [PHP_CodeSniffer][phpcs] para verificar que el código no va en contra de cada una de estas recomendaciones o utilizar plugins para el editor texto que uses como por ejemplo [Sublime Text 2][st-cs] que permitan obtener en tiempo real información sobre el código que no se adhiera al estilo de programación elegido.

Puedes corregir o mejorar de forma automática el diseño de tu código usando una de estas dos herramientas: La primera es [PHP Coding Standards Fixer][phpcsfixer] que tiene una base de estilos de código bien probada. La otra herramienta es [php.tools][phptools] que se hizo muy popular gracias a plugins como [sublime-phpfmt][sublime-phpfmt] del editor Sublime Text, a pesar de ser nueva esta última herramienta, tiene grandes mejoras en el rendimiento, lo que significa que la corrección en tiempo real que el editor ofrece es más fluida.

Puedes ejecutar el comando phpcs desde la consola de comandos de la siguiente manera:

    phpcs -sw --standard=PSR2 file.php

El comando anterior mostrará los errores y alguna descripción de como solventarlos.
También es de gran ayuda incluir el comando anterior en un hook de git, de esa forma ramas del repositorio local que contengan violaciones contra el estándar elegido no podrá entrar en el repositorio principal hasta que dichas violaciones sean corregidas.

Es preferible el idioma inglés para dar nombre a cualquier símbolo dentro de la infraestructura de código. Los comentarios pueden ser escritos en cualquier idioma que sea fácilmente legible por todas las partes presentes y futuras que pueden estar trabajando sobre la base del código.


[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
[phptools]: https://github.com/phpfmt/php.tools
[sublime-phpfmt]: https://github.com/phpfmt/sublime-phpfmt
