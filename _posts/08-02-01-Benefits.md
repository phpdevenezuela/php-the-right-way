---
title:   Beneficios
isChild: true
anchor:  beneficios_de_las_plantillas
---

## Beneficios {#beneficios_de_las_plantillas_title}

El principal beneficio de usar plantillas es la clara separación que se crea entre la lógica de presentación y el resto de la aplicación. Las plantillas son las únicas responsables de mostrar el contenido con un formato. Las plantillas no son responsables en el proceso de consultas de datos, persistencia o alguna otra tarea compleja de este estilo. Esto conduce a un código más limpio y legible que es de especial ayuda en un entorno de desarrollo donde los programadores  trabajan en código que se ejecuta del lado del servidor (Modelos y Controladores) y los diseñadores trabajan en código que se mostrara del lado del cliente (Markup HTML, CSS, JS).

Las plantillas también mejoran la organización del código de presentación. Usualmente las plantillas son colocadas en una carpeta llamada "views" (por su definición en inglés), cada una definida dentro de un solo archivo. Este enfoque fomenta la reutilización de código donde grandes bloques de código son divididos en piezas más pequeñas y reutilizables, comúnmente llamadas "partials" (por su definición en inglés). Por ejemplo, la cabecera y el pie de página de su sitio web pueden ser definidos como plantillas las cuales se incluyen antes y después de cada plantilla de contenido de una página.

Finalmente, dependiendo de la librería usada, las plantillas pueden ofrecer más seguridad al escapar automáticamente contenido generado por el usuario. Algunas librerías suelen ofrecer un sandbox (entorno de pruebas seguro) donde a los diseñadores se les da acceso a una lista de variables y funciones seguras de ejecutar.
