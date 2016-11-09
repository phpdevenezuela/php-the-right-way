---
isChild: true
title:   Capas de Abstracción
anchor:  capas_de_abstraccion
---

## Capas de Abstracción {#capas_de_abstraccion_title}

Muchos frameworks proveen sus propias capas de abstracción y estas pueden o no situarse por encima de [PDO][1]. Estos suelen emular características de un sistemas de bases de datos que no se encuentran en otro envolviendo sus consultas en métodos PHP, dándole la capa de abstracción de bases de datos real en vez de sólo la abstracción de conexión que provee PDO.

Esto, por supuesto, añadirá un poco de sobrecarga, pero si usted está construyendo una aplicación portátil que tiene que trabajar con MySQL, PostgreSQL y SQLite, esa sobrecarga se justificará en aras de de obtener un código limpio.

Algunas capas de abstracción se han construido usando los estándares de espacios de nombres [PSR-0][psr0] o [PSR-4][psr4] por lo que pueden ser instaladas en cualquier aplicación que desee:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]


[1]: http://php.net/book.pdo
[2]: http://www.doctrine-project.org/projects/dbal.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
