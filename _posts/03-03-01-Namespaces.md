---
isChild: true
anchor:  namespaces
---

## Namespaces {#namespaces_title}

Como mencionamos anteriormente, la comunidad de PHP tiene muchos desarrolladores creando una gran cantidad de código. Esto quiere decir que existe la posibilidad que dos librerías diferentes utilicen el mismo nombre para una clase en su código. Cuando las dos librerías se usan dentro del mismo namespace colisionan y causan problemas.

_Los Namespaces_ resuelven este problema. Como se describe en el manual de referencia de PHP, los namespaces son similares a los directorios que separan los archivos en el sistema operativo. Dos archivos con el mismo nombre pueden coexistir en directorios separados. Igualmente, dos clases de PHP con el mismo nombre pueden coexistir en namespaces separados, es tan simple como eso.

Es importante que separe su código con un namespace para que pueda ser usado por otros desarrolladores sin la preocupación de que cause conflictos con otras librerías.

Uno de los métodos recomendados para el uso de namespaces se indica en el [PSR-4][psr4], el cual se propone proveer una convención estándar para los archivos, clases y los namespaces, lo cual facilita el intercambio y uso del código en diferentes proyectos.

En Octubre del 2014 la PHP-FIG el tildó como obsoleto el estándar anterior de autocarga: [PSR-0][psr0], el cual ha sido reemplazado con el [PSR-4][psr4]. Actualmente ambos aún son perfectamente utilizables y PSR-0 no va a desaparecer. PSR-4 requiere al menos PHP 5.3 y muchos de los proyectos que actualmente implementan PSR-0 corresponden a la versión 5.2 de PHP. Afortunadamente muchos de esos proyectos realizados en versiones de PHP inferiores a la 5.3 se han ido actualizando a versiones superiores, por lo cual PSR-0 se usa cada vez menos.

Si va a utilizar un estándar de autocarga para una nueva aplicación o paquete, entonces es casi seguro que debe mirar PSR-4.

* [Leer acerca de Namespaces][namespaces]
* [Leer acerca de PSR-0][psr0]
* [Leer acerca de PSR-4][psr4]

[namespaces]: http://php.net/es/language.namespaces
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
