---
title:   Configuración en MAC
isChild: true
anchor:  mac_setup
---

## Configuración en MAC {#mac_setup_title}

OS X viene con PHP preempaquetado pero normalmente se encuentra en versiones anteriores a la version estable actual. El sistema "Mavericks" viene con PHP 5.4.17 configurado, "Yosemite" con PHP 5.5.9 y "El Capitan" tiene PHP 5.5.29, pero tras la liberacion de PHP 7.0 estas configuraciones no suelen ser suficientes.

Hay multiples maneras de instalar PHP en OS X.

### Instalar PHP vie Homebrew

[Homebrew] es un poderoso manejador de paquetes para OX, él cual puede ayudarle a instalar PHP y varias extensiones facilmente.
[Homebrew PHP] es un repositorio que contiene "fórmulas" para instalar y manejar PHP con Homebrew.

En este punto, puedes instalar `php53`, `php54`, `php55`, `php56` o `php70`  usando el comando `brew install`, y cambiar entre ellas modificando la variable `PATH`. Alternativamente puede usar [brew-php-switcher][brew-php-switcher] el cual alternará automaticamente por ti.

### Instalar PHP via Macports

El Proyecto [MacPorts] es una iniciativa de comunidad oopen-source para diseñar un sistema facil-de-usar para la compilación, instalación y actualización ya sea por medio de la linea de comandos, X11 o programas de fuente abierta basados en Aqua en el sistema operativo OS X.

MacPorts es compatible con binarios pre-compilados, por tanto no necesitas recompilar cada dependecia de los archivos tarball desde la fuente, ahorrandole futuros problemas si no tiene ningún paquete necesario instalado en su sistema.

En este punto, puedes instalar `php54`, `php55`, `php56` o `php70` usando el comando `port install`, por ejemplo:

    sudo port install php56
    sudo port install php70

Y puedes correr el comando `select` para cambiar tu version de PHP activa:

    sudo port select --set php php70

### Instalar PHP via phpbrew

[phpbrew] es una herramienta para la instalación y administración de multiples versiones de PHP. Esto puede ser de mucha utilidad si tienes dos diferentes aplicaciones y/o proyectos que requieran versiones diferentes de PHP, y no estes usando máquinas virtuales.

### Instalar PHP via Instalador Binario de Liip

Otra opción muy popular es [php-osx.liip.ch], el cual provee un metodo de instalación para las versiones PHP desde 5.3 a la 7.0.
Esto no sobreescribirá los binarios de PHP instalados por Apple, sino que instlara los nuevos en una ubicación separada (/usr/local/php5).

### Compilar desde la Fuente

Otra opción que le da el control sobre la version de PHP que va a instala, es [compilarla ud mismo][mac-compile].
En ese caso asegurasece de tener instalado [Xcode][xcode-gcc-substitution] o  un Sustituto ["Herramientas de Linea de Comandos para XCode"] de Apple que se encuentre dispoible para la descarga desde el Centro de Desarrolladores de Apple (Apple's Mac Developer Center).

### Instaladores Todo-en-Uno

Las soluciones listadas arriba manejan principalmente la instalación solo de PHP, y no proveen cosas como apache, Nginx o SQL server.
Soluciones "Todo-en-Uno" como [MAMP][mamp-downloads] y [XAMPP][xampp] instalaran todos estos otros programas por ud, pero la fácil configuración de este tipo de soluciones trae consigo una penalización en flexibilidad.

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
