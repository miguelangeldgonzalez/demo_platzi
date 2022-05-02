## Cambiar los permisos de un archivo (chmod)

Espero hallas realizado los ejercicios de la clase pasada, pues necesitaráss manejar correctamente esos permisos para esta clase.

Con el comando chmod podemos cambiar los permisos de los archivos de dos formas, una es usando los simbolos (rwx) y otra es con el sistema octal.

Es bastante sencillo camiar los permisos de forma simbólica solo hay que escribir despues del comando ```chmod``` el símbolo del usuario, luego el operador y por último el permiso que quieres agregar o quitar.

```
chmod [simboloDelUsuario][operador][permiso] [archivoParaCambiarSusPermisos]
```

| owner | group | others |
| --- | --- | --- |
| u (de user) | g | o |

| Operador | Función |
| --- | --- |
| + | Añade un permiso |
| - | Quita un permiso |
| = | Asigna un permiso |

Observa los permisos del siguiente archivo:
![image.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/image%28123%29.png){height="" width=""}

Supongamos que queremos añadirle permiso de escritura al grupo entonces tenemos que escribir lo siguiente:
```
chmod g+w ProyectoExplosivo.txt
```

![image.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/image%28124%29.png){height="" width=""}

Puedes cambiar varios permisos de varios usuarios al mismo tiemppo, por ejemplo, si quisieras agregar el permiso de escritura y ejecución al grupo y a otros, sería así:

```
chmod go+wx [archivo]
```

Y si quieres permisos diferentes para cada usuario solo separalos por comas.

```
chmod u+r,g=w [archivo]
```

En ese comando se le añadío el permiso de lectura al dueño y de escritura al grupo. No agregues espacio en las comas o provocarás un error.

También puedes cambiar los permisos usando su forma octal, por ejemplo el conjunto de permisos ```rwxr-xr-x``` en su forma octal es 755.

```
chmod 755 
```

![image.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/image%28125%29.png){height="" width=""}

## Manejo de usuarios (whoami | su)

A veces podemos tener una crisis existencial y no recordar quienes somos, pero en vez de asistir a un terapueta le podemos preguntar a la terminal. El comnando ```whoami```, literlamente "¿Quien soy yo?", te muestra cual es el usuario que se está ejecutando, esto es porque a veces podemos olvidar con cual usuario estamos trabajando.

Cuando listamos los archivos con ```ls -l ``` la tercera columna muestra el nombre del usuario que es propietario del archivo y la cuarta columna muestra el grupo que tiene control sobre el archivo.

![Sin título.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/Sin%20t%C3%ADtulo%285%29.png){height="" width=""}

En mi caso aparece "miguelangel" en ambas columnas porque ese es el usuario que estoy usando y porque el grupo al que pertenece el usuario se llama igual "miguelangel".

Para cambiar de usuario se usa el comando ```su``` **Switch User**, seguido del usuario al que quieres cambiar, en este caso vamos a cambiar al todo poderoso superusuario root.

```
su root
```

Cuando ejecutes este comando te pedíre que coloques su contraseña.

![image.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/image%28127%29.png){height="" width=""}

Y aqui una super advertencia, es más en negrita y mayúsculas para que sientas mejor la advertencia **SUPER ADVERTENCIA**, el superusuario root (si, ese es el nombre técnico) tiene poder para hacer y deshacer con el sistema operativo puedes elimnar cosas que no deberías eliminar y puede hacer mucho desastre, te lo digo por experiencia, usa los privilegios del root con cuidado.

**Bonus**: Si también estás usando Windows Subsystem for Linux (wsl) para este curso y se te olvidó la contresa del root (como a mi). Sigue estos pasos:

* Abre el cmd de windows y ejecuta este comando ```wsl --user root``` esto hará que se inicie en la terminal wsl con el usuario root.
* Luego ejecuta el comando ```passwd root``` el cual te permitirá cambiar la contraseña del usuario root

Ya con esto puedes volver a la terminal de wsl y volver a ejecutar el comando ```su root```.

Volviendo al tema, observa la nueva información de la terminal.

![image.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/image%28128%29.png){height="" width=""}

Ahora te indica antes del arroba que eres el usuario root, y al final de la información te coloca un númeral en vez de un signo de peso, eso significa que tienes altos privilegios en la terminal.

También te puedes dar cuenta que ya la virgulilla no está a pesar de que estas en la misma ruta, eso es porque el home del root no es ese, si quieres ver el home del root ejecuta esto: 

```
cd ~; pwd
```
![image.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/image%28129%29.png){height="" width=""}

Ahora comencemos con lo bueno, vamo a crear un archivo con root y a listarlo a ver que pasa.

```
touch ArchivoRoot.txt; ls -l
```

![Sin título.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/Sin%20t%C3%ADtulo%286%29.png){height="" width=""}

Ahora si intentamos borrar ese archivo con otro usuario que no sea root no vamos a poder porque no tiene los permisos para hacerlo.

## Cambiar el propietario (chown)

Puede que no te quieras hacer responsable de tus archivos así que se los quieres dejar a alguien más, para eso está el comando ```chown``` **Change Owner**. La sintáxis es muy simple:
```
chown [usuarioAlQuePertenecerá] [archivo]
```
![Sin título.png](https://cdn.document360.io/da52b302-22aa-4a71-9908-ba18e68ffee7/Images/Documentation/Sin%20t%C3%ADtulo%287%29.png){height="" width=""}

En la cuarta columna sigue diciendo root, pero eso es porque ese es el nonmbre del grupo.

## Guía

| Comando | Función |
| --- | --- |
| whoami | Muesta el usuario con el que se está trabajando |
| su | **Switch User** Cambia al usuario al que le especifiques |
| chmod | Cambia los permisos de un archivo |
| chown | **Change Owner** Cambia el propietario de un archivo |

## Ejercicios

Para que tengas más práctica manejando los cambios de permisos aquí te dejo unos ejercicios, recuerda que si haces mucho desastre puedes borrar casi lo que sea con el usuario root y ten mucho cuidado con lo que borras.

1. Crea un archivo llamado "ArchivoPoderoso.txt", luego dale los permisos r-xrwxr-xr-x usando la forma simbólica del comando chmod.
2. Crea un archivo con el usuario root llamado "pelota.txt", luego dale los permisos rwxr-x--x usando la forma numérica del comando chmod y luego cambia el propietario a tu usuario principal con chown.
3. Crea un archivo con un nombre bonito y asignale los permisos --------- usando su forma simbólica.