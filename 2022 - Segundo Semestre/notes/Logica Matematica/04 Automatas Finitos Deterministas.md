
#### Def 1
Una cadena es una secuencia de elementos que pertenecen a un alfabeto. La cadena vacía se representa por lambda o epsilon. 

E* = Todas las posibles combinaciones incluyendo la cadena vacía. O sea todas las cadenas ==finitas==.
E^i = Todas las cadenas finitas de largo i.

### Características de la cadena vacía
- Ex = xE = x


#### Def 2
Sea **A** un conjunto no vacío finito un alfabeto. Un lenguaje sobre este alfabeto es un subconjunto de A+.

#### Def 3
Una gramática de estructuras de frase para especificar un lenguaje consta de 4 elementos:
- un conjunto de terminales T
- conjunto de no terminales N
- conjunto de producciones P
- un no terminal especial en N que es el no terminal inicial. S

#### Def 4
Una gramática es una gramática de tipo 3 si todas las producciones de la gramática son de las formas A -> o A -> aB, de manera equivalente, de las formas A -> a o A -> Ba.


### Demostrar que un lenguaje no es regular

#### Teorema 4 
El ==lema del bombeo== dice que sea L un lenguaje de estado finito aceptado por una máquina de estado finito con N estados. Para cualquier sucesión en el lenguaje, cuya longitud es mayor o igual que N (número de estados), la cadena puede escribirse de la forma uvw. De manera que: v