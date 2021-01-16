# hash-cracking

  La base consiste en aplicar fuerza bruta con una lista 
  de posibles contraseñas convirtiendo cada una de las 
  contraseñas de la lista en un hash y comparandolo con el 
  hash que tenemos.

## Identificando el tipo de hash
  Para poder identificar el tipo de hash 
  podemos utilizar herramientas tales como 
  hash-identifier :
 
![hashidentifier](images/hashident.jpg)
  
  Hashid :

![hashid](images/hashid.jpg)

  Aunque si tiene caracteres especiales es mejor 
  identificarlos por la lista de hashes que tiene 
  hashcat en su documentacion :

![hashcat](images/hashcatvar.jpg)

## Wordlists 

Una vez tenemos el tipo de hash debemos definir que lista
de palabras usaremos contra el hash objetivo.
Una herramienta muy util para buscar y descargar wordlists
conocidas como rockyou.txt,dogs.txt,etc es : 

[wordlistcl](https://github.com/BlackArch/wordlistctl)

Si deseas saber mas sobre la

## Herramientas de craqueo















