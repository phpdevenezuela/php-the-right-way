---
title:   Plantillas Compiladas
isChild: true
anchor:  plantillas_compiladas
---

## Plantillas Compiladas {#plantillas_compiladas_title}

Mientras que PHP se ha convertido en un lenguaje maduro, orientado a objetos entre muchas otras cosas, [no ha mejorado mucho] [article_templating_engines] como un lenguaje de plantillas. Motores de plantillas compiladas como [Twig], [Brainy], or [Smarty]* llenan este vacío ofreciendo nuevas sintaxis creadas específicamente para plantillas. Desde escapado automático pasando por herencia de plantillas hasta estructuras de control simplificadas, las plantillas compiladas están diseñadas para ser más fáciles de escribir, sencillas para leer y más seguras de usar. Las plantillas compiladas pueden ser incluso compartidas a través de diferentes lenguajes, [Mustache] es un buen ejemplo de esto. Debido a que este tipo de plantillas deben ser compiladas existe un ligero impacto en el rendimiento, sin embargo este impacto puede llegar a ser mínimo con el uso de un sistema de cache apropiado.

**Aunque Smarty ofrece escapado automático, esta característica NO está habilitada por defecto.*

### Un simple ejemplo del uso de plantillas compiladas

Usando la librería [Twig].

{% highlight html+jinja %}
{% raw %}
{% include 'cabecera.html' with {'titulo': 'Perfil del Usuario'} %}

<h1>Perfil del Usuario</h1>
<p>Hola, {{ nombre }}</p>

{% include 'pie_de_pagina.html' %}
{% endraw %}
{% endhighlight %}

### Ejemplo del uso de plantillas compiladas usando herencia

Usando la librería [Twig].

{% highlight html+jinja %}
{% raw %}
// plantilla.html

<html>
<head>
    <title>{% block titulo %}{% endblock %}</title>
</head>
<body>

<main>
    {% block contenido %}{% endblock %}
</main>

</body>
</html>
{% endraw %}
{% endhighlight %}

{% highlight html+jinja %}
{% raw %}
// perfil_usuario.html

{% extends "plantilla.html" %}

{% block titulo %}Perfil del Usuario{% endblock %}
{% block contenido %}
    <h1>Perfil del Usuario</h1>
    <p>Hola, {{ nombre }}</p>
{% endblock %}
{% endraw %}
{% endhighlight %}


[article_templating_engines]: http://fabien.potencier.org/article/34/templating-engines-in-php
[Twig]: http://twig.sensiolabs.org/
[Brainy]: https://github.com/box/brainy
[Smarty]: http://www.smarty.net/
[Mustache]: http://mustache.github.io/
