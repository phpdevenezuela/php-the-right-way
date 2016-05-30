---
title:   Configuración en Windows
isChild: true
anchor:  configuracion_en_windows
---

## Configuración en Windows {#configuracion_en_windows_title}

Puede descargar los binarios desde [windows.php.net/download][php-downloads]. Después de extraer los archivos de PHP, es recomendable agregar el [PATH][windows-path] a la raíz de tu directorio PHP (Donde esta localizado php.exe) para que pueda ejecutar PHP desde cualquier lugar de su sistema.

Para el aprendizaje y desarrollo local puedes usar el Servidor Web Integrado de PHP 5.4 o superior, por tanto no necesita preocuparse por configurar un servidor web por separado. Si desea alguna solución "Todo-en-Uno", los cuales incluyen un servidor web completo y MySQL, entonces herramientas como [Web Platform Installer][wpi], [XAMPP][xampp], [EasyPHP][easyphp], [OpenServer][openserver] and [WAMP][wamp] le ayudarán a tener un entorno de desarrollo corriendo de forma fácil y rápida. Hay que mencionar, que estas herramientas son un poco diferentes a las que usará en su sistema de producción, así que tenga cuidado de las diferencias en el entorno de su aplicación si es que la desarrolla en Windows pero la despliega en Linux.

Si necesita correr su sistema de producción en Windows entonces IIS7 le dará un entorno más estable y mejor desempeño. Puede usar herramientas como [phpmanager][phpmanager] (un complemento GUI para IIS7) para simplificar las configuraciones y administraciones de PHP en este servidor. IIS7 viene con FastCGI integrado y listo para su uso, solo necesitará apuntar a PHP como un controlador.

Para mayor información y recursos adicionales diríjase al [área dedicada en iis.net][php-iis] para PHP.

Generalmente cuando corre una aplicación en diferentes entornos de desarrollo y de producción puede experimentar diversos errores. Si estas desarrollando en Windows y desplegando en Linux (u otro sistema distinto a Windows) entonces es recomendable considerar el uso de una [Maquina Virtual](/#virtualization_title).

Chris Tankersley tiene un post de mucha ayuda sobre cuales herramientas usa para hacer [Desarrollos PHP usando Windows][windows-tools].

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
