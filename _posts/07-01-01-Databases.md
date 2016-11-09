---
title:  Bases de Datos
anchor: bases_de_datos
---

# Bases de Datos {#bases_de_datos_title}

En muchas ocasiones su código PHP usará una base de datos para mantener información. Usted tiene varias opciones para conectarse e interactuar con su base de datos. La opción recomendada **hasta la versión 5.1.0 de PHP** era usar controladores nativos tales como [mysqli], [pgsql] o [mssql].

Los controladores nativos son excelentes si solo usa _una_ base de datos en su aplicación, pero si, por ejemplo, está usando MySQL y una pequeña porción de MSSQL, o si necesita conectarse a una base de datos Oracle, entonces no podría usar los mismos controladores. Usted necesitaría aprender a manipular una nueva API por cada base de datos &mdash; y eso sería absurdo.

[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql
