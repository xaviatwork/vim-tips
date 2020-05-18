# Vim básico (y no tanto)

## Modos

Cuando lanzas Vim, entras en modo *normal*; si quieres empezar a introducir texto, debes pasar al modo de *inserción* (con el que puedes editar texto).

Para cambiar a modo de *inserción*, pulsa la letra `i`; para salir del modo de *inserción* y volver al modo *normal*, pulsa la tecla *escape* (ESC).

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

### Pestañas en Vim

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

