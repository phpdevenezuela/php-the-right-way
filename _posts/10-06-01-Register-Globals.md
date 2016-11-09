---
isChild: true
anchor:  register_globals
---

## Register Globals {#register_globals_title}

**NOTA:** Desde PHP 5.4.0 la configuración de `register_globals` ha sio removida y no se puede usar más. Esto sólo está incluído como una guía para todo aquel que se encuentre en el proceso de actualización de alguna aplicación.

Cuando se habilita la configuración de `register_globals`, algunos tipos de variables (incluyendo los de `$_POST`, `$_GET` y `$_REQUEST`) se encuentren disponibles en el ámbito global de la aplicación. Esto puede conducir fácilmente a problemas de seguridad ya que la aplicación no tiene una manera efectiva de verificar de dónde provienen esos datos.

Por ejemplo: `$_GET['foo']` estaría disponible a través de `$foo`, lo cual puede alterar temporalmente las variables que no han sido declaradas.

Si estás usando una versión de PHP < 5.4.0 __asegúrate__ que `register_globals` está en __off__.

* [Leer acerca de Register Globals](http://php.net/es/security.globals)
