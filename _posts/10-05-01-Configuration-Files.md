---
title:   Archivos de Configuración
isChild: true
anchor:  archivos_de_configuracion
---

## Archivos de Configuración {#archivos_de_configuracion_title}

Cuando archivos de configuración para su aplicación, es tas son algunas de las mejores prácticas a seguir:

- Es recomendable que almacene sus archivos de configuración donde no se pueda acceder a ellos directamente por medio del sistema de archivos.

- Si no tiene otra alternativa más que almacenar sus archivos de configuración en la raíz de documentos de su aplicación, nombrelos con la extensión `.php`. De esta manera, aun si alguien accede a ellos directamente, la información no será impresa en forma de texto a la pantalla.

- La información en los archivos de configuración debe ser protegida ya sea por medio de codificación o con los permisos de grupo/usuario pertinentes en el sistema de archivos.

- Es una buena idea asegurarse que usted no envía los archivos de configuración o de aquellos que contienen información sensible, por ejemplo: contraseñas, tokens de API, etc. a su control de versiones.