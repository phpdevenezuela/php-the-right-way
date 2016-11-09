---
isChild: true
title:   Extensión PDO
anchor:  extension_pdo
---

## Extensión PDO {#extension_pdo_title}

[PDO] es una librería para la abstracción de conexiones a bases de datos &mdash; fue incluida dentro de PHP a partir de la versión 5.1.0 &mdash; y provee una interfaz común para comunicarse con diferentes bases de datos. Por ejemplo, puede usarla de manera idéntica para escribir la interfaz de comunicación con MySQL o SQLite:

{% highlight php %}
// PDO + MySQL
$pdo = new PDO('mysql:host=ejemplo.com;dbname=basededatos', 'usuario', 'contraseña');
$sql = $pdo->query("SELECT algun_campo FROM alguna_tabla");
$fila = $sql->fetch(PDO::FETCH_ASSOC);
echo htmlentities($fila['algun_campo']);

// PDO + SQLite
$pdo = new PDO('sqlite:/path/db/basededatos.sqlite');
$sql = $pdo->query("SELECT algun_campo FROM alguna_tabla");
$fila = $sql->fetch(PDO::FETCH_ASSOC);
echo htmlentities($fila['algun_campo']);
{% endhighlight %}

PDO NO traducirá sus consultas SQL y tampoco emulará características ausentes; PDO sólo se conecta con múltiples tipos de bases de datos usando la misma API.

Más importante aún, `PDO` le permitirá inyectar entradas externas de manera segura en sus sentencias SQL (p.e. IDs), sin tener que preocuparse por los ataques de inyección SQL (SQL injection).

Esto es posible gracias al uso de las declaraciones (statements) y parámetros vinculados (bound parameters) de PDO.

Supongamos que un script PHP recibe un ID numérico como un parámetro de una consulta. Este ID se usará para buscar un registro de usuario en una base de datos. Esta es la manera `incorrecta` de hacer esto:

{% highlight php %}
$pdo = new PDO('sqlite:/path/db/users.db');
$pdo->query("SELECT nombre FROM usuarios WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

Ese es un código terrible. Al hacerlo, estaría insertando un parámetro _crudo_ en su sentencia SQL. Hacerlo significaría que podrían hackearle más rápido que inmediatamente, usando una técnica llamada [SQL Injection](http://wiki.hashphp.org/Validation). Sólo imagine que un hacker pase un parámetro inventado `id` llamando a una URL como `http://dominio.com/?id=1%3BDELETE+FROM+usuarios`. Esto le asignaría el valor `1;DELETE FROM users` a la variable global `$_GET['id']` ¡lo cual borraría todos los registros de su tabla `usuarios`! Para evitarlo, debe _desinfectar_ la entrada ID usando parámetros vinculados (bound parameters).

{% highlight php %}
$pdo = new PDO('sqlite:/path/db/users.db');
$stmt = $pdo->prepare('SELECT nombre FROM usuarios WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); // <-- Desinfectado automáticamente por PDO
$stmt->execute();
{% endhighlight %}

Ese es el código correcto. Se usa un parámetro vinculado (bound parameter) en una declaración PDO. Esto escapa la entrada externa ID antes de que esta sea introducida a la base de datos, previendo posibles ataques de SQL Injection.

Para escrituras, como INSERT o UPDATE, aún es especialmente crítico [filtrar los datos](#data_filtering) primero y sanear cualesquiera otras cosas (eliminación de las etiquetas HTML, JavaScript, etc.). PDO sólo limpia el SQL, no su aplicación.

* [Aprenda más sobre PDO]

Debe tomar en cuenta que las conexiones de bases de datos usan recursos. Anteriormente no era extraño agotar los recursos del sistema si las conexiones no eran cerradas explícitamente, sin embargo, esto era más común en otros lenguajes. Usando PDO puede cerrar las conexiones explícitamente destruyendo el objeto, garantizando así que todas las referencias restantes se eliminan, p.e. asignándole un valor `null` al objeto PDO. Si no lo hace de manera explícita, automáticamente PHP cerrará la conexión cuando su script finalice - a menos claro, que esté usando conexiones persistentes.

* [Aprenda acerca de conexiones PDO]

[Objetos de datos de PHP]: http://www.php.net/manual/es/book.pdo.php
[Conexiones y su administración]: http://php.net/manual/es/pdo.connections.php
[Características obsoletas en PHP 5.5.x]: http://php.net/manual/es/migration55.deprecated.php
[SQL Injection]: http://wiki.hashphp.org/Validation

[pdo]: http://php.net/pdo
[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql