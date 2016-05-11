---
title:   Configuración en MAC
isChild: true
anchor:  mac_setup
---

## Configuración en MAC {#mac_setup_title}

OS X viene con PHP preempaquetado pero normalmente esta un poco detrás de la version estable. Mavericks tiene 5.4.17, Yosemite tiene 5.5.9 y El Capitan tiene 5.5.29, pero con PHP 7.0 fuera eso a menudo no es suficientemente bueno.

Hay multiples maneras de instalar PHP en OS X.

### Instalar PHP vie Homebrew

[Homebrew] es un poderoso manejador de paquetes para OX, él cual puede ayduarte a instalar PHP y varias extensiones facilmente.
[Homebrew PHP] es un repositorio que contiene "fórmulas" realacionadas con PHP para Homebrew, y te dejará instalar PHP.

Ene ste punto, puedes instalar `php53`, `php54`, `php55`, `php56` o `php70`  usando el comando `brew install`, y alternar entre ella modificando la variable `PATH`. Alternativamente puede usar [brew-php-switcher][brew-php-switcher] el cual alternará automaticamente por ti.

### Instalar PHP via Macports

El Proyecto [MacPorts] es una iniciativa de comunidad de codigo-abierto para diseñar un sistema de facil-de-usar para la compilacion, instalacion y actualizacion ya sea por medio de la linea de comandos, X11 o programas de codigo-abierto basados en Aqua en el sistema operativo OS X.

MacPorts es compatible con binarios pre-compilados, por tanto no necesitas recompilar cada dependecia de los archivos tarball desde la fuente, salvando tu vida si no tiene ningún paquete instalado en tu sistema.

En este punto, puedes instalar `php54`, `php55`, `php56` o `php70` usando el comando `port install`, por ejemplo:

    sudo port install php56
    sudo port install php70

Y puedes correr el comando `select` para cambiar tu version de PHP activa:

    sudo port select --set php php70

### Instalar PHP via phpbrew

[phpbrew] es una herramienta para la instalacion y adminitracion de multiples versiones de PHP. Esto puede ser de mucha utilidad si tienes dos diferentes aplicaciones/proyectos que requieran versiones diferentes de PHP, y no estas usando maquinas virtuales.

### Instalar PHP via Instalador Binario de Liip

Otra popular opcion es [php-osx.liip.ch] el cual provee un metodo de instalación para las versiones 5.3 a la 7.0.
No sobreescribir los binarios de PHP instalados por Apple, pero instala
todo en un locacion separada (/usr/local/php5).

### Compilar desde la Fuente

Otra opcion que te da el control sobre la version de PHP que instalas, es [compilarla tu mismo][mac-compile].
En ese caso asegurate de tener instalado ya sea [Xcode][xcode-gcc-substitution] o  un Sustituto ["Herramientas de Linea de Comandos para XCode"] de Apple descargable desde el Centro de Desarrolladores de Apple (Apple's Mac Developer Center).

### Instaladores Todo-en-Uno

Las soluciones listadas arriba manejan principalmente PHP en si mismo, y no proveen cosas como apache, Nginx o SQL server.
Soluciones "Todo-en-Uno" como [MAMP][mamp-downloads] y [XAMPP][xampp] instalaran estos otros programas por ti y los atará todos juntos, pero la fácil configuracion trae consigo una compensacion en flexibilidad.

[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: http://php-osx.liip.ch/
[mac-compile]: http://php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[xampp]: http://www.apachefriends.org/en/xampp.html
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher
