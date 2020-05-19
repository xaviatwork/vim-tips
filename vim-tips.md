# Vim básico (y no tanto)

> En algunas instalaciones de Linux se instala el paquete `vim-tiny`, que contiene una versión sin ayuda y con alguna limitación de funciones. Puedes comprobar la versión instalada invocando el comando de ayuda: 
> Pulsa `ESC` para asegurarte que estás en modo *normal* y escribe `:help` (seguido de Enter).
> En la ayuda se recomienda instalar el paquete completo de `vim` o alguno versión alternativa completa.

## Modos

Cuando lanzas Vim, entras en modo *normal*; si quieres empezar a introducir texto, debes pasar al modo de *inserción* (con el que puedes editar texto).

Para cambiar a modo de *inserción*, pulsa la letra `i`; para salir del modo de *inserción* y volver al modo *normal*, pulsa la tecla *escape* (ESC).

Si quieres entrar en el modo para insertar texto en una nueva línea, usa `o` en vez de `i`.

### Editar texto

Los pasos básicos para crear un fichero, editar texto, guardarlo y salir, son los siguientes:

1. Desde la línea de comando, escribe `vi` para lanzar el editor (sin ningún fichero previo)
1. Pulsa `i` para entrar en el modo de *inserción*
1. Escribe! ;)
1. Pulsa `ESC` para volver al modo *normal*
1. Escribe `:w`, seguido de un espacio y del nombre incluida la ruta donde quieres guardar el fichero que acabas de crear. Por ejemplo `:w ~/Documentos/test1.txt`
1. Escribe `:q` para salir (`quit`)

## Porqué Vim

Hay dos argumentos habituales entre los defensores de usar Vim por encima de cualquier otro editor de texto:

1. Vim está en todas partes: cualquier distribución de Linux y MacOS traen Vim preinstalado. Si tradicionalmente en el *datacenter* había una gran presencia de servidores Linux, con la llegada del *cloud* un gran número de equipos con los que -quizás- debas interaccionar sean Linux; y en todos ellos, grandes y pequeños (Raspberry Pi, por ejemplo), encontrarás Vim.
1. Vim te permite ser más productivo/más ágil o alguna variante por el estilo. Vim es un editor de texto que se puede usar completamente desde el teclado. Esto significa que incluso cuando paras de escribir y pasas a modificar el texto (copiar y pegar, guardar, abrir un nuevo fichero, etc...) sigues "escribiendo", es decir, usando el teclado. Algunos argumentan que el no tener que separar las manos del teclado para usar el mouse te hace mucho más productivo.

En mi caso, quiero aprender Vim más por la primera razón que por la segunda, aunque tu caso puede ser diferente.

## "Filosofía" Vim

Como los comandos de Vim se introducen desde el teclado y hay un montón parece que será necesario tener una gran memoria para recordarlos todos. Sin embargo, esto no es del todo así, aunque -en mi opinión- ayuda acostumbrarse a *pensar* (o como mínimo *traducir*) las acciones que quieres realizar a inglés; los atajos más habituales comienzan con la letra de la acción en inglés; por ejemplo `w` para *escribir al disco, guardar* (*write*), salir, `q` (*quit*) o `i` para *insert*.

Si estás acostumbrado a usar atajos de teclado en tu sistema operativo (con interfaz gráfica), Windows, Linux o MacOs, ya te habrás encontrado con esta "necesidad" de tener que traducir los atajos. En algunos casos al "localizar" el sistema operativo también se traducen los atajos; pero a mí esto me confunde más todavía, ya que estoy muy acostumbrado a los atajos "ingleses" (no suelo usar la interfaz en castellano). Así me encuentro que al pulsar `Ctrl+A` para *seleccionar todo* (*all*, en inglés) lo que pasa es que se **a**bre un nuevo documento... `Ctrl+S+ subraya cuando quiero *guardar* (*save*), etc.

La moraleja de todo esto es doble: cuando asocias determinadas acciones a combinaciones de teclas, las realizas de forma automática, instintiva; ese es el "encanto" de Vi. La segunda "lección" es que esas acciones las puedes realizar mediante el teclado, con lo que realmente el cambio de escribir a ejecutar comandos es ínfimo.

Si los atajos de teclado en Vim se redujeran a una colección más o menos amplia de combinaciones de teclas -abrir, cerrar, copiar y pegar- Vim no ofrecería nada especial. La **potencia** de Vim está en la capacidad de combinar acciones para crear algo equivalente a las *macros* que ofrecen algunos editores; pero con sobre la marcha, simplemente pensando en *qué quieres hacer* (ahí es donde ayuda lo de *pensar* en inglés).

Un ejemplo sencillo: al acabar de escribir una palabra, ves que no es exactamente lo que quieres decir y quieres borrarla. Puedes bulsar `Delete` una y otra vez hasta que borres todas las letras de la palabra. También puedes hacerlo, en general en un editor mediante la combinación "Shift"+ (para seleccionar), "Alt" y el cursor "<-"; con esto seleccionas desde el cursor hacia "atrás" (de ahí el uso de "<-") y una vez tienes seleccionada la palabra, pulsa `Supr`.

En Vim, pulsarías `ESC` (para salir del modo de inserción y volver al modo normal), y pulsarías `d1b`. Esto, traducido sería **d** (*delete*, borrar), 1, **b** (*backwards*, hacia atrás). No hace falta que le indiques `1 palabra hacia atrás`; Vim ya sabe que si quisieras borrar sólo una letra usarías la tecla `Del`, así que borra la siguiente "unidad de texto", la "palabra".

Lo destacable es cómo se combina una acción con un número de veces y una unidad; ¿borrar 3 líneas? `d3l`. Si el "verbo" para copiar es *yank*, ¿cómo copias una palabra entera? Exacto, `yw`. Y si quieres pegar tres veces esa palabra: `3pw` (*3 paste word*, repite tres veces la acción de pegar la palabra copiada).

Como ves, las combinaciones de acciones se parecen mucho a dar órdenes sobre "qué tiene que hacer Vim" de una manera muy "programática", como si dieras instrucciones a un robot. Y aunque pueda parecer un poco raro al principio, poco a poco se convierte en la forma "natural" de dirigirte a Vim para que haga lo que quieres que haga.

## Configuración "al vuelo"

Otra cosa que puedes hacer sobre la marcha en Vim es configurarlo; estos cambios tienen efecto inmediato, pero sólo duran hasta que cierras el editor. Para que los cambios de configuración sean permanentes debes guardarlos en el fichero de configuración de Vim.

Si estás editando un documento en Vim y te das cuenta de que no sabes en qué linea estás (VIm no lo muestra por ningún sitio), puedes pulsar `Ctrl+g` (en modo normal) para que en Vim aparezca una especia de "línea de estado" en la que indica la línea y columna actual. Pero esta información se oculta de nuevo en cuanto pulsas cualquier tecla. 
Como la mayoría de editores puede mostrar en el borde izquierdo de la ventana el número de línea. Para indicar a Vim que muestre los números debes usar el comando `set`.

1. Pulsa `ESC` para volver al modo normal
1. Pulsa `:set number` seguido de `Enter`
1. Pulsa `i ` para seguir escribiendo...

Si en algún momento te cansas de tener números de línea -o ya no los necesitas-, repite el proceso pero ahora especifica `:set nonumber` para hacerlos desaparecer.

De nuevo la idea detrás del funcionamiento de Vim es interrumpirte lo mínimo posible y que sigas a lo tuyo.
Si usas alguna configuración -como los números de línea- de forma habitual, debes incluirla en el fichero de configuración de Vim (generalmente `~/.vimrc`).

## Pestañas en Vim

Aunque se trata de una aplicación "de pantalla negra", Vim proporciona pestañas como cualquier editor moderno.
Si quieres modificar el fichero `~./.vimrc` antes de que se te olvide pero no quieres dejar a medias el documento en el que estás trabajando, abre una nueva pestaña y modifica el fichero.

1. Pulsa `ESC` para volver al modo normal
1. Escribe `:tabnew ~/.vimrc` para abrir el fichero de configuración de Vim en una nueva pestaña 
1. Pulsa `i` para cambiar al modo de *inserción*
1. Introduce `set number`
1. Pulsa `ESC` para volver al modo *normal*
1. Pulsa `:w` para guardar

Si quieres dejar el fichero de configuración abierto en una pestaña -por si necesitas realizar algún cambio más-, puedes cambiar de pestaña mediante `gt` (desde el modo *normal*) (*go tab*, ir a pestaña).

Si tienes muchas pestañas abiertas puedes cambiar a una específica mediante, por ejemplo, `3gt` (repite tres veces, ves a la siguiente pestaña (desde la primera), o lo que es lo mismo, ves a la tercera pestaña).

Para volver a la pestaña anterior, usa `gT` o usa `:tabp`.

Los comandos para navegar entre pestañas (*tabs*) son todos de este estilo: `:tabedit`,  `:tabfirst`, `:tablast` o `:tabclose`... Si sólo quieres conservar la pestaña actual y cerrar el resto, `:tabonly`.

Recuerda que para descartar los cambios en otras pestañas que no tengas guardados debes añadir `!`.

## Múltiples ventanas

Otra de esas cosas que -por ahora- sólo he usado en editores de texto en entornos gráficos: dividir la pantalla; en Vim se puede conseguir mediante: `:split` (para dividir la ventana horizontalmente) o `vsplit` para una división vertial.

Para cambiar el *foco* de la pantalla se usa `ctrl+w` seguido de la tecla de cursor (o las `hjkl` para indicar a qué ventana quieres cambiar el foco). Cuidado con `ctrl+w` ya que en muchas aplicaciones este es el atajo de teclado para cerrar la ventana...

Puedes cerrar una ventana adicional mediante `:q`, pero me ha gustado el comando para cerrar *todas* las otras ventanas `:only`.

Recuerda que puedes copiar y pegar entre distintas pestañas y ventanas, lo que es especialmente útil (esta era una de esas cosas que echaba de menos hasta ahora, usando `screen` o `tmux` en equipos remotos.

## Bookmarks

Aunque puedes desplazarte con facilidad dentro del texto de un fichero en Vim, puedes poner un *bookmark* en alguna línea particular de interés en el fichero.

Para ello, usa `:m a`, donde puedes usar en vez de `a` cualquier letra minúscula (de la `a` a la `z`) como *marcador*.

Puedes consultar todos los marcadores que tienes definidos mediante `:marks`.

Para saltar a una marca concreta, usa (desde el modo normal) ``a` (o la letra que hayas usado como marca).

En un teclado configurado en castellan este atajo es un poco fastidioso, ya que ``` se combina con algunos caracteres para producir letras con acento abierto, por lo que a veces, para que se muestre el caracter debes pulsar ```` seguido de espacio, por ejemplo, para que se muestre y después la letra usada como marca :(

### Marcas "del sistema"

Si compruebas las marcas que tienes definidas, verás que **siempre** aparecen dos, como mínimo: una indica la última posición en la que se ha producido un cambio en el texto y otra que representa la posición en la que se abandonó el fichero actual...

En mi caso las *marcas* que aparecen son diferentes a las que se indican en [el wiki Using marks](https://vim.fandom.com/wiki/Using_marks).

## Trucos/Recetas

Una de las cosas más habituales en los artículos sobre Vim en internet es mostrar una lista de combinaciones que permiten hacer una cosa superespecífica de la manera más óptima posible (y que probablemente sólo tenga sentido hacerla si usas Vim). En cualqueir caso, esta guía no estaría completa sin una lista de esas cosas, así que aquí empieza una -inacabale- lista de *trucos* para Vim.

> Disclaimer: sólo apuntaré los trucos que me hayan funcionado y que me sirvan en alguna situación, hay demasiadas cosas que hacer en la vida para tener que pasar el tiempo acumulando cosas que nunca usaré.

### Ir al paréntesis de cierre (sirve para otros caracteres que van en parejas)

El "comando" `%` permite ir al caracter de cierre -o apertura- de un bloque limitado por paréntesis, llaves, paréntesis cuadrados (corchetes).
Esto es ideal cuando estás programando, pero también sirve si estás escribiendo texto. Si estás en el paréntesis de cierre, al pulsar `%` en modo *normal* saltas al paréntesis de apertura. Y viceversa.
Funciona del mismo modo con `{}`, `[]`, `()` (aunque no parece funcionar con  `<` y `>`, comillas, etc.

### Hacer que la tecla `<----` (backspace) borre en Vim

Es una de esas cosas que te vuelven loco hasta que un día descubres cómo solucionarlo. Por algún motivo desconocido, el comportamiento por defecto de la table de borrar (*backspace*) en vim es **no hacer nada**.

Para devolverle el comportamiento esperado, es decir, **borrar**, debes añadir la linea al fichero `~/.vimrc`:

```ini
set backspace=indent,eol,start
```

Referencia: [Backspace key not working in Vim/vi](https://stackoverflow.com/questions/11560201/backspace-key-not-working-in-vim-vi)

Puedes usar este "comando" en combinación con `d` o `y` y así copiar todo el bloque de texto.

### Selección visual

Cuando tienes un mouse, mantienes pulsado el botón principal y lo arrastras y seleccionas lo que haya debajo. Si estás en un entorno "de pantalla negra", simplifica mucho las cosas tener algo de *feedback* visual cuando seleccionas una palabra, una línea, etc...

En Vim, para conseguirlo, debes usar el comando `v` (por *visual*).

1. Pulsa `ESC` para volver al modo normal
1. Pulsa `v` para resaltar la selección
1. Muévete -con los cursores, con comando como `w` o `b`, etc- para seleccionar
1. Haz algo con ello! Por ejemplo, `vyw` y después `p` para copiar y pegar una palabra.

### Buscar

Una de las cosas más habituales cuando estás editando un fichero es buscar algo concreto (que seguramente borrarás o corregirás a continuación).

En Vim usas `/` (en modo normal) para iniciar una búsqueda.

Si quieres buscar `Vim` en este texto:

1. Pulsa `ESC` para volver a modo normal
1. Escribe `/Vim` y pulsa enter.

El cursor encontrará la primera ocurrencia de la cadena que has buscado. Puede buscar la siguiente ocurrencia pulsando  `/` (y Enter) de nuevo. Aunque es mucho más rápido simplemente pulsar `n` para encontrar la siguiente ocurrencia de la búsqueda en el texto (o `N`, para encontrar la anterior).

El tema de la búsqueda tiene más *chicha*, por lo que más adelante volveré con más contenido para esta sección.

### Moverse en el fichero

Parece que el origen de que en Vim las teclas para desplazarse por el texto sean `h j k l` en vez de los cursos "modernos" es porque el teclado de los terminales originales tenía las flechas de los cursores en estas letras ([Key Placement](https://superuser.com/a/599152), incluso hay una foto).

Tratándose de Vim, no podía faltar quien lo justifica indicando que las teclas `hjkl` está, literalmente, bajo tus dedos y es mucho más rápido que tener que desplazar la mano hasta las teclas de cursor... Hay quien incluso dice haber calculado cuánto tiempo ahorra al día usando Vim (calculando el tiempo *perdido* en desplazamientos *inútiles* y le salen como tres minutos al día de ahorro... En fin).

En cualquier caso, puedes usar las teclas de cursor en las versiones modernas de Vim (yo es una de las cosas que no puedo evitar; de hecho, si me fuerzo a usar `hjkl` pierdo más tiempo *pensando* en hacia dónde me quiero mover, etc que no desplazando la mano hacia el cursos y pulsando las teclas sin mirar...)

Sin embargo, sí que es importante que aprendas otros *atajos* para agilizar cómo te desplazas por un texto.

#### Desplazamientos cortos

Empezamos con los desplazamientos "cortos": con `w` (*word*) avanzas al principio de la siguiente palabra (donde "palabra" es un conjunto de letras separadas del resto por un espacio o algún caracter especial como signos de puntuación o comillas). Para volver "hacia atrás", usas `b` (de *backwards*).

Si quieres desplazarte al final de la palabra en la que te encuentras, pulsa `e` (*end*).

#### Desplazamientos un poco más largos

Pulsa `0` para desplazarte al inicio de la línea en la que se encuentra el cursor.

Para desplazarte al final de la línea, pulsa `$`.

De nuevo, puedes usar las teclas *Home* y *End* del teclado y, en general, funcionan como las aplicaciones de escritorio... Debo confesar que a diferencia de `hjkl` sí que uso con cierta frecuencia estos dos *atajos*... Aunque están más cerca en el teclado, el hecho de tenes que combinarlo con *Shift* (para obtener `$`) hace que lo use menos de lo que debería, especialmente en modo *inserción*, ya que tengo que añadirle la tecla `ESC` para pasar a modo normal primero..

#### Desplazamientos medios

En modo normal, puedes desplazarte al principio de la siguiente frase mediante ' )'.

Si quieres avanza hasta el principio del siguiente párrafo, usa `}`.

No conocía estos comandos, así que no los he utilizado nunca.


#### Desplazamientos largos

Para desplazarte al final del fichero, usa `shift+g` (*g* mayúscula).

Si quieres volver al principio del fichero, usa `gg`.

Para ir a cualquier sitio, usa la combinación `#G`, donde *#* es el número de línea al que quieres ir.


## Ejecutar comandos de sistema sin salir de Vim

Puedes ejecutar un comando del sistema operativo (Linux) desde Vim desde el modo *normal* precediendo el ccomando de `:!`. Por ejemplo:

```bash
LICENSE  vim-tips.md

Press ENTER or type command to continue
```

---

Referencia:
- [Why I love Vim: It’s the lesser-known features that make it so amazing](https://www.freecodecamp.org/news/learn-linux-vim-basic-features-19134461ab85/) 
- [How not to be afraid of Vim anymore](https://www.freecodecamp.org/news/how-not-to-be-afraid-of-vim-anymore-ec0b7264b0ae/)
- [7 Vim Tips That Changed My Life (With Demo)](https://www.freecodecamp.org/news/7-vim-tips-that-changed-my-life/) Los *tips* que se indican están muy orientados a la programación; cosas relacionadas con la indentación de bloques, al principio de una línea, etc... Quizás más adelante.
