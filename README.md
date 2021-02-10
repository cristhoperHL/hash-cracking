
# hash-cracking 

## ¿Que es una funcion hash?

Las funciones hash son diferentes al cifrado.No hay clave, y esta destinado a ser imposible(o muy, muy dificil) volver de la salida a la entrada.

Una funcion hash toma algunos datos de entrada de cualquier tamaño y crea un resumen de esos datos.La salida es de un tamaño fijo.Es dificil predecir cual sera el resultado de cualquier entrada y viceversa. Los buenos algoritmos de hash seran faciles de calcular y lentos para revertir, ademas cualquier cambio en la entrada deberia causar un gran cambio en la salida.

Ahora la razon por la que esto deberia importarnos es porque el hash es usado frecuentemente en la ciberseguridad para verificar que su contraseña sea correcta o verificar la integridad de los datos en general.



La base consiste en aplicar fuerza bruta con una lista de posibles contraseñas convirtiendo cada una de las contraseñas de la lista en un hash y comparandolo con el hash que tenemos.

## Identificando el tipo de hash
Para poder identificar el tipo de hash podemos utilizar herramientas tales como hash-identifier :

![hashidentifier](images/hashident.jpg)

  Hashid :

![hashid](images/hashid.jpg)

Aunque si tiene caracteres especiales es mejor identificarlos por la lista de hashes que tiene hashcat en su documentacion :

![hashcat](images/hashcatvar.jpg)

## Wordlists 

Una vez tenemos el tipo de hash debemos definir que lista de palabras usaremos contra el hash objetivo.Una herramienta muy util para buscar y descargar wordlists conocidas como rockyou.txt,dogs.txt,etc es : 

[wordlistcl](https://github.com/BlackArch/wordlistctl)

o podemos buscarlas manualmente por google.

## Herramientas de craqueo

### Hashcat 
  Es una herramienta bastante usada por la wiki que tiene todo 
  tipo de hashes.Un ejemplo de esto seria :

![hashcatt](images/hashcatvar.jpg)

Una vez tenemos el modo de hash de la wiki podemos usar ese dato para atacar el
hash de esta manera :

```
hashcat -m 1800 hash.txt wordlist.txt
```

### John The Ripper

John the Ripper es otra herramienta con el mismo proposito 
pero es dependiente a un identificar de hashes ya que este no lo hace por
defecto con todos.
Por lo que una vez identifiquemos el tipo de hash con otrasherramientas
buscamos los formatos que contiene john the ripper para atacar los hashes de
esta manera :

```
john --list=formats
```
luego buscamos el formato con el nombre mas parecido al hash que busquemos
y atacamos el hash de esta manera.

```
john hash.txt --wordlist=wordlist.txt --format=md5crypt
```

## Generacion de listas de palabras personalizadas.

Hay muchas herramientas para generar lista de palabras claro que tambien 
se puede ser de manera manual haciendo un algoritmo pero para evitar 
inventar la rueda de nuevo existen herramientas como :


### Cewl
Esta es una herramienta que nos permite generar una lista de palabras 
con los strings de un sitio web(hace un spidering al sitio web y obtiene
todos sus palabras).

[Cewl](https://github.com/digininja/CeWL)

Un ejemplo de como funciona seria este, en donde genera un archivo example.txt
con las palabras de este sitio web.

```
ruby -W0 ./cewl.rb -d 3 -w $(pwd)/example.txt https://example.org
```

### TTPassGen

Es una herramienta para crear wordlist a partir de expresiones regulares.

[TTPassGen](https://github.com/tp7309/TTPassGen)

Ejemplos :

```
python3 ttpassgen.py --rule '[?d]{4:4:*}' pin.txt
```

```
python3 ttpassgen.py --rule '[?l]{1:3:*}' abc.txt
```

Ahora en caso que queramos combinar wordlists podriamos usar esta sintaxis :


```
python3 ttpassgen.py --dictlist 'pin.txt,abc.txt' --rule '$0[-]{1}$1' combination.txt
```



