---
title:   Configuración en Windows
isChild: true
anchor:  windows_setup
---

## Configuracion en Windows {#windows_setup_title}

Puedes descargar los binarios desde [windows.php.net/download][php-downloads]. Después de la extración de PHP, es recomendable agregar el [PATH][windows-path] a la raiz de tu directorio PHP (Donde esta localizado php.exe) para que puedas ejecutar PHP desde cual sitio.

Para el aprendizaje t desarrollo local puedes usar el Servidor Web Integrado con PHP 5.4+ por tanto no necesitas preocuparte por configurarlo. Si te gustaria algo "Todo-en-Uno" los cuales incluyen un servidor web completo y MySQL también entonces herramientas como [Web Platform Installer][wpi], [XAMPP][xampp], [EasyPHP][easyphp], [OpenServer][openserver] and [WAMP][wamp] te ayduarán a tener un entorno de desarrollo listo y corriendo rapidamente. Hay que mencionar, que  estas herramientas seran un poco diferentes a entornos de producción por lo cual se muy cuidadoso de las diferencias de entornos si estas trabajando en Windows y desplegando en Linux.

Si necesitas correr tu sistema de produccion en Windows entonces IIS7 te dará mas estabilidad y mejor desempeño. Puedes usar [phpmanager][phpmanager] (a GUI plugin for IIS7) para hacer configuraciones y administraciones simples de PHP. IIS7 viene con FastCGI integrado y listo para usar, solo necesitaras configurar PHP como un manejador.

Para soporte y recursos adicionales esta un [area dedicada en iis.net][php-iis] para PHP.

Generalemente correr tu aplicacion en diferentes entornos en desarrollo y production puede llevar a extraño errores apareciendo cuando vas en directo. Si estas desarrollando en Windows y desplegando en Linux (u otro distinto a Windows) entonces deberias considerar el uso de una [Maquina Virtual](/#virtualization_title).

Chris Tankersley tiene un post en su blog de mucha ayuda sobre cuales herramientas el usa para hacer [Desarrollos PHP usando Windows][windows-tools].

[easyphp]: http://www.easyphp.org/
[phpmanager]: http://phpmanager.codeplex.com/
[openserver]: http://open-server.ru/
[wamp]: http://www.wampserver.com/en/
[php-downloads]: http://windows.php.net/download/
[php-iis]: http://php.iis.net/
[windows-path]: http://www.windows-commandline.com/set-path-command-line/
[windows-tools]: http://ctankersley.com/2015/07/01/developing-on-windows/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[xampp]: http://www.apachefriends.org/en/xampp.html
