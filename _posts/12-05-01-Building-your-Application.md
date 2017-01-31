---
title:   Construyendo tu Aplicación
isChild: true
anchor:  construyendo_y_desplegando_tu_aplicacion
---

## Construyendo Y Desplegando Tu Aplicación  {#construyendo_y_desplegando_tu_aplicacion_title}

Si te encuentras haciendo cambios al esquema de base de datos o corriendo pruebas (de forma manual) antes de modificar tus archivos (de forma manual), entonces piénsalo nuevamente. Con cada tarea manual adicional para desplegar tu aplicación las oportunidades para la aparición de errores fatales se multiplican. Bien sea que estés manejando una simple actualización, un completo proceso de implementación o incluso una estrategia continua de integración, en esos casos la [automatización del build][buildautomation] es tu mejor amiga.

Entre las tareas que podrías querer automatizar podemos encontrar: 
* Manejo de dependencias.
* Compilación y minificación de los recursos.
* Corrida de pruebas.
* Creación de la documentación.
* Empaquetado.
* Despliegue.

### Herramientas de automatización del build

Las herramientas de automatización del build pueden ser descritas como una colección de scripts que manejan tareas comunes del despliegue de software. Las herramientas de automatización del build no son parte de tu software, ellas actúan sobre él desde fuera.

Hay muchas herramientas *open source* disponibles que pueden ayudarte con la automatización del build, algunas están escritas en PHP, otras en cambio no lo están, esto ultimo no debe limitarte al momento de usarlas si se ajustan mejor a alguna tarea específica. Aquí proponemos algunos ejemplos de esta clase de software:

**[Phing]** representa la manera más fácil de comenzar a experimentar con el despliegue automático en el mundo de PHP. Con Phing puedes controlar tu empaquetado, despliegue o procesos de prueba desde un solo archivo XML. Phing (el cual está basado en [Apache Ant]) provee un rico set de tareas usualmente necesarias para instalar o actualizar una aplicación web, su funcionalidad puede ser extendida con tareas adicionales personalizadas escritas en PHP.

**[Capistrano]** es un Sistema para “programadores intermedios-avanzados” que permite ejecutar comandos de una forma estructurada y repetible en una o más maquinas remotas. Esta preconfigurado para el despliegue de aplicaciones en Ruby on Rails, sin embargo, hay personas que  **despliegan sistemas en PHP satisfactoriamente** con él. El uso satisfactorio de Capistrano depende de un conocimiento funcional de Ruby y Rake.

El artículo de Dave Gardner sobre [Despliegue de PHP con Capistrano][phpdeploy_capistrano] es un buen punto de partida para los desarrolladores PHP interesados en Capistrano.

**[Chef]** es más que solo un framework de despliegue, es un poderoso framework de integración de sistemas basado en Ruby. No solo despliega tu aplicación, sino que también puede construir todo tu ambiente de servidor o cajas virtuales.

**[Deployer]** es una herramienta de despliegue escrita en PHP, es simple y funcional. Ejecuta tareas de despliegue atómico paralelo y mantiene la consistencia entre servidores. Contiene recetas para tareas comunes en Symfony, Laravel, Zend Framework y Yii.

#### Recursos sobre Chef para desarrolladores PHP:

* [Serie de artículos en tres partes acerca del despliegue de una aplicación LAMP con Chef, Vagrant y EC2][chef_vagrant_and_ec2]
* [Recetario de Chef que te enseñara a instalar y configurar PHP y el sistema de manejo de paquetes PEAR][Chef_cookbook]
* [Serie de video tutoriales sobre Chef][Chef_tutorial]

#### Lecturas adicionales:

* [Automatiza tu proyecto con Apache Ant][apache_ant_tutorial]

### Integración Continua
>La integración continua en una práctica del desarrollo de software en la cual los miembros de un equipo integran su trabajo de manera frecuente, usualmente cada persona hace integraciones diarias, lo que lleva a múltiples integraciones por día. Muchos grupos encuentran que este acercamiento genera una cantidad reducida de problemas de integración y permite al grupo desarrollar software cohesivo de una manera más rápida.

*-- Martin Fowler*

Existen muchas maneras diferentes de implementar la integración continua para PHP. [Travis CI] ha hecho un trabajo grandioso haciendo de la integración continua una realidad, incluso para proyectos pequeños. Travis CI es un servicio hospedado de integración continua para la comunidad open source, está integrado con GitHub y ofrece soporte de primera clase para muchos lenguajes, entre ellos PHP.

#### Lecturas adicionales:

* [Integración continua con Jenkins][Jenkins]
* [Integración continua con PHPCI][PHPCI]
* [Integración continua con Teamcity][Teamcity]

[buildautomation]: http://en.wikipedia.org/wiki/Build_automation
[Phing]: http://www.phing.info/
[Apache Ant]: http://ant.apache.org/
[Capistrano]: https://github.com/capistrano/capistrano/wiki
[phpdeploy_capistrano]: http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/
[Chef]: https://www.chef.io/
[chef_vagrant_and_ec2]: http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/
[Chef_cookbook]: https://github.com/chef-cookbooks/php
[Chef_tutorial]: https://www.youtube.com/playlist?list=PL11cZfNdwNyPnZA9D1MbVqldGuOWqbumZ
[apache_ant_tutorial]: http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/
[Travis CI]: https://travis-ci.org/
[Jenkins]: http://jenkins-ci.org/
[PHPCI]: http://www.phptesting.org/
[Teamcity]: http://www.jetbrains.com/teamcity/
[Deployer]: https://github.com/deployphp/deployer