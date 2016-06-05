---
isChild: true
title:   Interactuando con Bases de Datos
anchor:  interactuando_con_bases_de_datos
---

## Interactuando con Bases de Datos {#interactuando_con_bases_de_datos_title}

Cuando los desarrolladores empiezan a aprender PHP, a menudo terminan mezclando la interacción con la base de datos con su lógica de presentación, usando código que podría tener este aspecto:

{% highlight php %}
<ul>
<?php
foreach ($bd->query('SELECT * FROM tabla') as $fila) {
    echo "<li>".$fila['campo1']." - ".$fila['campo1']."</li>";
}
?>
</ul>
{% endhighlight %}

Esta es una mala práctica por muchas razones, principalmente, porque es difícil de depurar, difícil de poner a prueba, difícil de leer y que va a generar una gran cantidad de campos si se ponen límites.

Si bien hay muchas maneras de resolver esto - dependiendo de si prefiere [POO](/#object-oriented-programming) o [programación funcional](/#functional-programming) -, debe haber un elemento de separación.

Considere el modo más sencillo:

{% highlight php %}
<?php
function cogerTodosLosFoos($bd) {
    return $bd->query('SELECT * FROM tabla');
}

foreach (cogerTodosLosFoos($bd) as $fila) {
    echo "<li>".$fila['campo1']." - ".$fila['campo1']."</li>"; // ¡¡ERROR!!
}
{% endhighlight %}

Ese es un buen comienzo. Ponga esos dos elementos en dos archivos diferentes y tendrá una separación más clara.

Cree una clase y coloque ese método dentro y tendrá un "Modelo". Cree un simple archivo `.php` para colocar la lógica de presentación y tendrá una "Vista", todo eso le acercará mucho a [MVC] - una arquitectura común de la POO en muchos [frameworks](/#frameworks).

**foo.php**

{% highlight php %}
<?php
$bd = new PDO('mysql:host=localhost;dbname=bdprueba;charset=utf8', 'usuario', 'contraseña');

// De acceso a su modelo
include 'modelos/ModeloFoo.php';

// Cree una instancia
$modeloFoo = new ModeloFoo($bd);
// Obtenga la lista de los Foos
$listaFoo = $modeloFoo->cogerTodosLosFoos();

// Muestre la vista
include 'vistas/lista-foo.php';
{% endhighlight %}


**modelos/ModeloFoo.php**

{% highlight php %}
<?php
class ModeloFoo
{
    protected $bd;

    public function __construct(PDO $bd)
    {
        $this->db = $bd;
    }

    public function cogerTodosLosFoos() {
        return $this->db->query('SELECT * FROM tabla');
    }
}
{% endhighlight %}

**vistas/foo-lista.php**

{% highlight php %}
<?php foreach ($listaFoo as $fila): ?>
    <?= $fila['campo1'] ?> - <?= $fila['campo1'] ?>
<?php endforeach ?>
{% endhighlight %}

Esto es, esencialmente, lo mismo que hacen la mayoría de los frameworks modernos, pero un poco más artesanal. Puede que no tenga que hacerlo constantemente, pero mezclar la lógica de presentación y la interacción con la base de datos puede ser un verdadero problema si necesita hacer [pruebas unitarias](/#unit-testing) a su aplicación.

[PHPBridge] tiene un gran recurso llamado [Creando una clase Data - _Creating a Data Class_] que cubre un tema parecido, y es ideal para desarrolladores que desean habituarse a usar el concepto de interacción con bases de datos.


[MVC]: http://code.tutsplus.com/tutorials/mvc-for-noobs--net-10488
[PHPBridge]: http://phpbridge.org/
[Creating a Data Class]: http://phpbridge.org/intro-to-php/creating_a_data_class
