---
layout: page
title: Patrones de Diseño
---

# Patrones de Diseño

Hay muchas maneras de estructurar el código y el proyecto para tu aplicación web, y puedes poner tanto o tan poco
pensado como te gusta en la arquitectura. Pero suele ser una buena idea seguir a patrones comunes porque hará tu código 
más fácil de mantener y más fácil de entender para otros.

* [Architectural pattern on Wikipedia](https://en.wikipedia.org/wiki/Architectural_pattern)
* [Software design pattern on Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern)

## Patrón Fábrica (Factory)

Uno de los patrones de diseño más utilizados es el patrón de fábrica (Factory). Este es un patrón que simplemente es una 
clase que crea el objeto que desea utilizar. Considera el siguiente ejemplo del patrón de fábrica:

{% highlight php %}
<?php
class Automovil
{
    private $vehiculo_marca;
    private $vehiculo_modelo;

    public function __construct($marca, $modelo)
    {
        $this->vehiculo_marca = $marca;
        $this->vehiculo_modelo = $modelo;
    }

    public function get_marca_y_modelo()
    {
        return $this->vehiculo_marca . ' ' . $this->vehiculo_modelo;
    }
}

class AutomovilFactory
{
    public static function crear($marca, $modelo)
    {
        return new Automovil($marca, $modelo);
    }
}

// hacer que la fabrica cree el objeto Automóvil
$veyron = AutomovilFactory::crear('Bugatti', 'Veyron');

print_r($veyron->get_marca_y_modelo()); // outputs "Bugatti Veyron"
{% endhighlight %}

Este código utiliza una fábrica para crear el objeto Automóvil. Hay dos posibles beneficios para construir tu 
código de esta manera, el primero es que si necesitas cambiar, renombrar o reemplazar la clase de automóvil más tarde, 
puedes hacerlo y sólo tendrás que modificar el código de la fábrica, en lugar de Cada lugar en tu proyecto que utiliza 
la clase de Automóvil. El segundo beneficio posible es que si la creación del objeto es un trabajo complicado se puede 
hacer toda la lógica en la fábrica, en lugar de repetirlo cada vez que desees crear una nueva instancia.

Usar el patrón Factory no siempre es necesario (o acertado). El código de ejemplo usado aquí es tan simple que una 
fábrica simplemente agregaría complejidad innecesaria. Sin embargo, si está realizando un proyecto lo bastante grande o 
complejo, puedes ahorrar un montón de problemas en el camino mediante el uso de fábricas.

* [Factory pattern on Wikipedia](https://en.wikipedia.org/wiki/Factory_pattern)

## Controlador Frontal (Front Controller)

El patrón Controlador Frontal es donde tienes un único punto de entrada para tu aplicación web (por ejemplo, index.php) 
que maneja todas las peticiones. Este código es responsable de cargar todas las dependencias, procesar la solicitud y 
enviar la respuesta al navegador. El patrón Controlador Frontal puede ser beneficioso porque alienta el código modular 
y te da un lugar central para conectar el código que debe ejecutarse para cada solicitud (como la sanitización de 
entrada).

* [Front Controller pattern on Wikipedia](https://en.wikipedia.org/wiki/Front_Controller_pattern)

## Modelo-Vista-Controlador (Model-View-Controller)

El patrón de modelo-vista-controlador (MVC) y sus parientes HMVC y MVVM te permiten dividir el código en objetos lógicos 
que servirán a fines muy específicos. Los modelos sirven como capa de acceso a datos donde los datos que se obtienen y 
devuelven en formatos utilizables en toda tu aplicación. Los controladores manejan la solicitud, procesan los datos 
devueltos de los modelos y cargan las vistas para enviar la respuesta. Y las vistas son plantillas de visualización 
(html, xml, etc) que se envían en la respuesta al navegador web.

MVC es el patrón arquitectónico más común utilizado en los [frameworks PHP](https://github.com/codeguy/php-the-right-way/wiki/Frameworks) mas populares.

Aprende mas acerca de MVC y sus patrones parientes:

* [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller)
* [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller)
* [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
