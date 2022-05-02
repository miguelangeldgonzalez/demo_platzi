Los permisos son las capcidades que tiene cada usuario dentro del sistema opeartivo, no todos los usarios pueden hacer todas las acciones sobre ciertos archivos y carpetas.

Cuando listamos archivos utilizando el comando ```ls -l ``` la primera columna que nos aparece es la de permisos.

![image.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/image%28121%29.png){height="" width=""}

## Tipo de Archivo

El primer caracter puede ser uno de estos 3:

| Atributo | Tipo de archivo |
| --- | --- |
| - | Es un arvhico normal, como un documento de texto, una foto, un video, etc. |
| d | Por **directory** es un directorio |
| l | Es un enlace simbólico. Es algo que veremos en próximas clases |
| b | Bloque especial, son archivos que manejan información para el sistema, como la información de un disco duro |

![Sin título.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/Sin%20t%C3%ADtulo%284%29.png){height="" width=""}

## Permisos de usuario

Los siguientes caracteres se leen de 3 en 3, por cada uno de los tipos de usuario.

### Owner 

El dueño del archivo, sino se ha cambiado es quien lo creo y tiene mayor jerarquía sobre los otros 3. Le corresponden los primeros 3 caraceteres de los permisos.

### Group

Por no estar dándole los mismos permisos a varios usuarios, se crean grupos de usuarios en los que se le dan los mismo permisos a varios usuarios. A estos usuarios le corresponden el cuarto, quinto y secto caracter de los permisos de usuarios y tienen mayor jerarquía que el último.

### World

También llamado otros, es cualquier otro usuario que no pertenezca a un grupo de usuario y tampoco sea el dueño, este tiene la menor jerarquía.

## Tipos de permisos


| Símbolo | Sígnificado | Permiso |
| --- | --- | --- |
| r | readable | Significa que puede er su contenido |
| w | writable | El usuario puede editar el contenido del archivo, también el nombre y los permisos |
| x | executable | El usuario puede ejecutarlo en caso de que sea un programa |

Los permisos se escriben en ese orden rwx, para indicar que el permiso no esta disponible se escribe un guión.

Ahora que sabes todo esto vamos con un ejercicio. Observa el siguiente grupo de permisos:
```
drwxr-xr-x
```
Recuerda que el primer caracter es el tipo y los siguientes se cuentan de 3 en 3 representando cada usuario.


| d | rwx | r-x | r-x |
| --- | --- | --- | --- |
| Esto es un directorio | owner | group | world |
|| El dueño puede leer, escribir y ejecutar | El grupo puede leer y ejecutar | Los demás pueden leer y ejecutar |

Vamos con otro

```
-rw-r--r--
```


| - | rw- | r-- | r-- |
| --- | --- | --- | --- |
| Esto es un archivo normal, como una imágen o un video | owner | group | world |
| | El dueño puede leer y escribir | El grupo sólo puede leer | El resto sólo puede leer |

## Representando permisos de forma octal

Si organizamos los permisos de esta forma

| r | w | x |
| --- | --- | --- |

E indicamos con un cero si el usuario no tiene el permiso y con un uno si el usuario si lo tiene, pongamos de ejemplo el permiso r-x:

| r | w | x |
| --- | --- | --- |
| 1 | 0 | 1 |

Y ahora esos números los leemos en binario nos quedaría así.

| r | w | x |
| --- | --- | --- |
| 1 | 1 | 1 |
|| 7 |

Si repetimos esto con el resto de las combinaciones tenemos un número por cada combinación de permiso, por ejemplo el permiso ```r-x``` queda así:

| r | - | x |
| --- | --- | --- |
| 1 | 0 | 1 |
|| 5 |

Usando todo esto podemos leer el conjunto de permisos ```rwxr-xr--```, así:

| r | w | x | | r | - | x | | r | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | 1 | 1| | 1 | 0 | 1 | | 1 | 0 | 0 | 0 |
|| 7 |||| 5 |||| 1 |||


## Ejercicios

Este concepto puede ser algo complicado así que lo mejor es prácticar, te dejaré unos ejercicios para que se te haga más fácil interpretar esto.

Convierte los siguientes permisos a símbolos y en su representación numérica:

1. De un directorio, el **dueño** tiene permiso de lectura y escritura, el **grupo** tiene permisos de escritura y ejecución y **world** no tiene permisos.
2. De un enlace simbólico el **dueño** tiene todos los permisos, el **grupo** y **world** sólo de lectura.
3. De un archivo comun todos tienen todos los permisos, pero el **world** no tiene permiso de ejecución.

Sé que puedes lograr estos ejercicios, solo revisa las tablas alrededor de la clase. Y si sientes que necesitas más información puedes preguntar a la comunidad o prácticar en la terminal.