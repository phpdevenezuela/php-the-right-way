---
isChild: true
title:   Extensión MySQL
anchor:  extension_mysql
---

## Extensión MySQL {#extension_mysql_title}

La extensión [mysql] para PHP es extremadamente vieja y ha sido sustituida por dos nuevas extensiones:

- [mysqli]
- [pdo]

El desarrollo de [mysql] no sólo se detuvo hace mucho tiempo, sino que además está [oficialmente en desuso a partir de la versión 5.5.0 de PHP][mysql_deprecated] y **será oficialmente [eliminada de PHP en la versión 7.0][mysql_removed].**

Para evitar el tener que excavar en las configuraciones de su `php.ini` para saber qué módulo está usando, una opción es buscar `mysql_*` en el editor de su preferencia. Si cualquier función tal como `mysql_connect()` o `mysql_query()` son encontradas en esa búsqueda, entonces `mysql` está siendo usada.

Incluso si no está usando PHP 7.0 aún, no tener en cuenta esta actualización tan pronto como sea posible dará lugar a unos mayores problemas cuando la actualización 7.0 de PHP esté cercana. Así pues, su mejor opción será reemplazar el uso de la extensión [mysql] en sus aplicaciones, sustituyéndola por las extensiones [mysqli] o [pdo]. Empiece a planificar esos cambios dentro de sus cronogramas de desarrollo y así evitará tener que hacer las cosas a toda prisa.

**Si se está actualizando desde [mysql] a [mysqli], tenga cuidado con las guías de actualización para flojos que sugieren que puede simplemente buscar y reemplazar `mysql_*` con `mysqli_*`. Eso no sólo es que una burda simplificación, sino que además no toma en cuenta las ventajas que ofrece al mysqli, tales como parámetros vinculados (bound parameters), que también se ofrece en [PDO][pdo].**

* [PHP: Elegir una API](http://php.net/manual/es/mysqlinfo.api.choosing.php)
* [PDO Tutorial for MySQL Developers](http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers)

[mysql]: http://php.net/mysql
[mysql_deprecated]: http://php.net/migration55.deprecated
[mysql_removed]: http://php.net/manual/es/migration70.removed-exts-sapis.php
[mysqli]: http://php.net/mysqli
[pdo]: http://php.net/pdo
[mysql_api]: http://php.net/mysqlinfo.api.choosing
[pdo4mysql_devs]: http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers
