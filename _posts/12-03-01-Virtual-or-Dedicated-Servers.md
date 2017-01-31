---
title:   Servidores Virtuales y Dedicados
isChild: true
anchor:  servidores_virtuales_y_dedicados
---

## Servidores Virtuales y Dedicados {#servidores_virtuales_y_dedicados_title}

Si te sientes cómodo con la Administración de Sistemas o si deseas aprender sobre ella, los servidores virtuales o dedicados te dan el control completo sobre el entorno de producción de tu aplicación.

### nginx y PHP-FPM

PHP a través del manejador de procesos integrado FastCGI (FPM por sus siglas en inglés) hace una pareja perfecta con [nginx] el cual es un servidor web ligero y de alto rendimiento. Usa menos memoria que Apache y puede manejar mejor una mayor cantidad de solicitudes concurrentes. Esto es especialmente importante cuando se trata de servidores virtuales que no poseen mucha memoria.

* [Lee más sobre nginx][nginx]
* [Lee más sobre PHP-FPM][phpfpm]
* [Lee más sobre configurar nginx y PHP-FPM de forma segura][secure-nginx-phpfpm]

### Apache y PHP

PHP y apache comparten una larga historia juntos. Apache es ampliamente configurable y hay muchos [módulos][apache-modules] disponibles para extender su funcionalidad. Es una opción popular para los servidores compartidos y para frameworks y aplicaciones *open source* como WordPress. Desafortunadamente Apache por defecto usa muchos más recursos que nginx y no puede manejar tantos visitantes al mismo tiempo.

Apache tiene muchas posibles configuraciones para correr PHP, la más común y fácil de configurar es el [prefork MPM] con mod_php5. A pesar de que no es la más eficiente con la memoria, es la más simple de poner a trabajar y usar. Esta es probablemente la mejor opción si no deseas profundizar demasiado en los aspectos de la Administración de Sistemas. Ten en cuenta que si usas mod_php5 DEBES usar el prefork MPM.

Alternativamente, si deseas exprimir de Apache más rendimiento y estabilidad puedes entonces tomar ventaja del mismo sistema FPM que nginx y correr el [worker MPM] o el [event MPM] con mod_fastcgi o mod_fcgid. Esta configuración será mucho más eficiente con la memoria y mucho más veloz, sin embargo su configuración implica más trabajo.

* [Lee más sobre Apache][apache]
* [Lee más sobre Módulos de Multiprocesamiento (Multi-Processing Modules: MPM)][apache-MPM]
* [Lee más sobre mod_fastcgi][mod_fastcgi]
* [Lee más sobre mod_fcgid][mod_fcgid]

[nginx]: http://nginx.org/
[phpfpm]: http://php.net/manual/es/install.fpm.php
[secure-nginx-phpfpm]: https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/
[apache-modules]: http://httpd.apache.org/docs/2.4/es/mod/
[prefork MPM]: http://httpd.apache.org/docs/2.4/mod/prefork.html
[worker MPM]: http://httpd.apache.org/docs/2.4/mod/worker.html
[event MPM]: http://httpd.apache.org/docs/2.4/mod/event.html
[apache]: http://httpd.apache.org/
[apache-MPM]: http://httpd.apache.org/docs/2.4/mod/mpm_common.html
[mod_fastcgi]: https://docs.oracle.com/cd/B31017_01/web.1013/q20204/mod_fastcgi.html
[mod_fcgid]: http://httpd.apache.org/mod_fcgid/