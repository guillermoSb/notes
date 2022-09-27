# Maquinas de estado finito


#### Def 1
Una **n-ada** ordenada es un *conjunto ordenado* con n elementos.

Ejemplo
A = {a,b,c,d,....,x,y,z} el alfabeto
la palabra hola es una 4-ada del alfabeto.


==NOTA== Se usa la notación A^n para denotar el conjunto de todas las sucesiones de n letras en A. Y se utiliza la notación A^+ para denotar el conjunto de sucesiones desde una letra hasta n letras.

#### Def 2
Si A es un conjunto finito, es el alfabeto del lenguaje. Un lenguaje es un subconjunto de A+.

Ejemplo
A = {a,b,c}
L1 = {a,aa,ab,ac,abc,cab}
L2 ={}
L3 = {aba, ab, ac, abc, cab}

==NOTA== como los lenguajes son conjuntos, podemos aplicar todas las operaciones de conjuntos a ellos.

#### Def 3
Las gramáticas especifican la estructura de las frases de un lenguaje.
Se componen de 
1. Conjunto de terminales T
2. Conjunto de no terminales N
3. Conjunto de producciones P
4. No terminal N que es el símbolo inicial

Pregunta: En gramática para las cadenas de 3 caracteres

#### Def 4
Una gramática es de tipo 3 si todas sus producciones son de la siguiente forma.
A -> a, A -> aB. o A -> a, A -> Ba



#### Def 5
Una máquina de estado finito está especificada por
1. Conjunto de estados S
2. Un estado inicial S0
3. Caracteres de entrada I
4. Caracteres de salida O
5. Función de transición 
6. Función de salida

En este caso la función de salida especifíca que caracter se le asigna a cada estado. Por ejemplo
s0 - 0
s1 - 0
s2 - 1

#### Def 6
Dos máquinas son equivalentes si a partir de el estado inicial producen la misma sucesión de salida cuando se les da la misma sucesión de entrada.

![[Captura de Pantalla 2022-09-27 a la(s) 4.16.04 p.m..png]]
Las dos máquinas son equivalentes para la cadena 1122212212
![[Captura de Pantalla 2022-09-27 a la(s) 4.16.21 p.m..png]]

`Pergunta: Para saber si la máquina es equivalente se debe probar con todas las sucesiones?`

#### Def 7 
Dos estados son equivalentes si al recibir una sucesión de entrada producen la misma sucesión de salida sin importar en cuál de los dos se empiece.
- Podemos reducir el autómata uniendo los estados que son equivalentes.
![[Captura de Pantalla 2022-09-27 a la(s) 4.21.49 p.m..png]]