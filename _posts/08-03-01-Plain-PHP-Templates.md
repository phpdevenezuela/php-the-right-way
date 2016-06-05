---
title:   Plantillas con PHP plano
isChild: true
anchor:  plantillas_con_php_plano
---

## Plantillas con PHP plano {#plantillas_con_php_plano_title}

Las plantillas con PHP plano son simplemente archivos de texto que usan código PHP nativo. Es la opción más utilizada ya que PHP en realidad es un lenguaje propio para plantillas. Tan simple como que puedes combinar código PHP dentro de cualquier otro tipo de código como por ejemplo HTML. El uso de este tipo de plantillas es un beneficio para los desarrolladores PHP ya que no es necesario aprender un nueva sintaxis para la creación de plantillas, conocería las funciones disponibles y en los editores de texto cuentan con resaltado de sintaxis y autocompletado incorporado. Además, las plantillas planas PHP tienden a ser muy rápidas ya que no necesitan proceso de compilación.

Cada framework de PHP moderno emplea algún tipo de sistema de plantilla, la mayoría de los cuales usan PHP plano por defecto. Más allá de los frameworks, librerías como [Plates][plates] or [Aura.View][aura] facilitan el trabajo con plantillas planas PHP pero ofreciendo funcionalidades de sistemas modernos de plantillas como lo son la herencia, layouts y extensiones.

### Un simple ejemplo del uso de plantillas con PHP plano

Usando la librería [Plates][plates].

{% highlight php %}
<?php // perfil_usuario.php ?>

<?php $this->insert('cabecera', ['titulo' => 'Perfil del Usuario']) ?>

<h1>Perfil del Usuario</h1>
<p>Hola, <?=$this->escape($nombre)?></p>

<?php $this->insert('pie_de_pagina') ?>
{% endhighlight %}

### Ejemplo del uso de plantillas planas PHP con herencia.

Usando la librería [Plates][plates].

{% highlight php %}
<?php // plantilla.php ?>

<html>
<head>
    <title><?=$titulo?></title>
</head>
<body>

<main>
    <?=$this->section('contenido')?>
</main>

</body>
</html>
{% endhighlight %}

{% highlight php %}
<?php // perfil_usuario.php ?>

<?php $this->layout('plantilla', ['titulo' => 'Perfil del Usuario']) ?>

<h1>Perfil del Usuario</h1>
<p>Hola, <?=$this->escape($nombre)?></p>
{% endhighlight %}


[plates]: http://platesphp.com/
[aura]: https://github.com/auraphp/Aura.View
