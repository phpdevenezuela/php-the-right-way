---
title:   Vagrant
isChild: true
anchor:  vagrant
---

## Vagrant {#vagrant_title}

[Vagrant] te ayuda a construir *cajas* virtuales sobre la tecnología ofrecida por los más populares entornos de virtualización y configurar las mismas empleado solo un archivo de configuración. Dichas “cajas” pueden ser desplegadas de manera manual o bien puedes emplear algún software de aprovisionamiento tal como [Puppet] o [Chef] para tal fin. Aprovisionar una *caja base* es una forma ideal para asegurar que múltiples cajas pueden ser desplegadas con idénticas características lo que elimina la necesidad de mantener un complicado listado de comandos de instalación. Además, se puede destruir la *caja base* y recrearla sin la necesidad de llevar a cabo muchos pasos, haciendo sumamente fácil la creación de una “instalación fresca”.

Vagrant crea directorios que permiten compartir código entre el sistema anfitrión y la máquina virtual, lo permite crear y editar código en el computador y ejecútalo en la máquina virtual.

### Una pequeña ayuda

Si necesitas de una pequeña ayuda para comenzar a usar Vagrant, a continuación puede encontrar algunos servicios que te serán útiles:

- [Rove][Rove]: es un servicio que permite pregenerar builds típicas de Vagrant, se puede encontrar a PHP entre sus opciones. El aprovisionamiento se hace con Chef.
- [Puphpet][Puphpet]: es una simple interfaz gráfica que permite desplegar máquinas virtuales para el desarrollo en PHP. *Se enfoca principalmente en PHP*, pero más allá de la creación de máquinas virtuales también puede ser usado para lanzar servicios en la nube. El aprovisionamiento se realiza con Puppet.
- [Protobox][Protobox]: es una capa que corre sobre Vagrant y además una aplicación web para la configuración de máquinas virtuales enfocadas al desarrollo web. Un solo archivo [YAML] controla todo lo que es instado en la máquina virtual.
- [Phansible][Phansible]: provee una interfaz sencilla para generar [Playbooks de Ansible] para proyectos basados en PHP.

[Vagrant]: http://vagrantup.com/
[Puppet]: http://www.puppetlabs.com/
[Chef]: https://www.chef.io/
[Rove]: http://rove.io/
[Puphpet]: https://puphpet.com/
[Protobox]: http://getprotobox.com/
[Phansible]: http://phansible.com/
[YAML]: https://es.wikipedia.org/wiki/YAML/
[Playbooks de Ansible]: http://docs.ansible.com/ansible/playbooks.html
