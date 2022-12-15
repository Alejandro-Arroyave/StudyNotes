# CSS

## Especificidad

La especificidad es la jerarquía que utilizan los navegadores para decidir que valores van a aplicar en las propiedades de CSS cuando hay dos o más especificadas, se utiliza un sistema de ponderación o puntuación. La especificidad tiene el siguiente orden de mayor a menor valor de especificidad:

1. Estilos inline: Tiene un valor de 1-0-0-0, o sea que son los que tienen más especificidad.
2. Selector de id: Tiene un valor de 0-1-0-0.
3. Selector de clases: Tienen un valor de 0-0-1-0, este aplica para .clases, atributos[…] y :pseudoclases
4. Selector de elementos: Tienen un valor de 0-0-0-1, este aplica para elementos y ::pseudoelementos (::after, ::before)

El !important está por encima de todos, para que una propiedad de menor puntaje sea aplicada, se le debe de colocar !important justo después de la propiedad. Pero esto es una mala práctica la mayoría de las veces, ya que si abusamos de esto puede resultar en un código difícil de debuguear y de mantener.

El selector universal (*), (*), los combinadores (+, >, ~, etc ) y la pseudo-clase de negación :not() no tienen efecto sobre la especificidad.

Los puntos de especificidad son acumulativos, por lo tanto pueden sumarse y producir varios valores, vamos a ver un ejemplo:

body #content .data img:hover {…}

 ```
body -> 	0-0-0-1
#content ->     0-1-0-0
.data -> 	0-0-1-0
img -> 		0-0-0-1
:hover ->	0-0-1-0
```

El resultado es: 0-1-2-2
