---
title:   Cifrado de Contraseñas
isChild: true
anchor:  cifrado_de_contrasenas
---

## Cifrado de Contraseñas {#cifrado_de_contrasenas_title}

Eventualmente todos terminamos creando una aplicación PHP basada en la conexión de usuarios. Los nombres de usuarios y
contraseñas son almacenados en la base de datos y usadas luego para autenticar a los usuarios conectados.

Es muy importante que las contraseñas sean cifradas a través de una [función hash criptográfica][3] antes de almacenarlas.
Un cifrado través de hash es irreversible, una vez que la función ha sido aplicada a la contraseña del usuario. Esto
produce una cadena de longitud fija que no puede ser revertida. Esto significa que puede comparar un hash contra otro para determinar si ambos proceden de la misma cadena de origen, pero no se puede determinar la cadena original. Si las contraseñas no están hasheadas y se accede a la base de datos por un tercero no autorizado, todas las cuentas de usuario están comprometidas. Algunos usuarios pueden (por desgracia) utilizar la misma contraseña para otros servicios. Por lo tanto, es importante tomar en serio la seguridad.

**Hash de contraseñas con `password_hash`**

En PHP 5.5 fue introducida la función `password_hash()`. En este momento está usando BCrypt, el algoritmo más fuerte actualmente soportado por PHP. Se actualizará en el futuro para apoyar a más algoritmos, según sea necesario. La función `password_compat` fue creada para proveer compatibilidad a las versiones PHP >= 5.3.7.

A continuación hacemos hash a una cadena de texto y seguidamente comprobamos el hash con una nueva cadena. Debido a que las fuentes de nuestras dos cadenas son distintas (‘contraseña-secreta’ vs ‘contraseña-errada’) la conexión fallará.

{% highlight php %}
<?php
require 'contrasena.php';

$contrasenaConHash = password_hash('contraseña-secreta', PASSWORD_DEFAULT);

if (password_verify('contraseña-errada', $contrasenaConHash)) {
    // Contraseña Correcta
} else {
    // Contraseña Errada
}
{% endhighlight %}

* [Leer acerca de `password_hash()`] [1]
* [`password_compat` for PHP >= 5.3.7 && < 5.5] [2]
* [Leer acerca hashing en cuanto a la criptografía] [3]
* [PHP `password_hash()` RFC] [4]

[1]: http://php.net/es/function.password-hash
[2]: https://github.com/ircmaxell/password_compat
[3]: https://es.wikipedia.org/wiki/Función_hash_criptográfica
[4]: https://wiki.php.net/rfc/password_hash
