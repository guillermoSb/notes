# Trayectorias Y Circuitos

#### Def 16
Un **paseo** o **trayectoria** es una secuencia de vértices conectados por aristas. Usualmente se definen así: *(e1,e2,e3)*. Por ejemplo:

![[IMG_8EC7282ABA72-1.jpeg | 300]]

#### Def 17
Un paseo ([[#Def 16]]) simple no debe de incluir la misma arista dos veces. El paseo de la imagen anterior es simple.

#### Def 18 
Un paseo ([[#Def 16]]) elemental no tiene el mismo vértice dos veces. O sea que no hay dos aristas que tengan el mismo vértice inicial o final.

#### Def 19
Un circuito es un paseo ([[#Def 16]]) en el que el vértice terminal es igual al vértice inicial.

#### Def 20
El circuito puede ser un paseo simple ([[#Def 17]])

#### Def 21
Un circuito también puede ser elemental ([[#Def 18]]).


#### Teorema 1
En un grafo con n vértices, cuando hay un paseo entre dos vértices *v1* y *v2*, entonces entonces existe un paseo con no más de *n-1* aristas entre ambos vértices.

![[Pasted image 20220815172018.png]]

#### Def 22
A un grafo se le llama conexo si existe un paseo entre cualesquiera 2 vértices. No conexo en otro caso
#### Def 23
Un grafo dirigido es conexo si el grafo no dirigido derivado de el es conexo.
#### Def 24
Un grafo dirigido se le llama fuertemente conexo si para cualquiera dos vértices hay un paseo entre *v1* y *v2* y viceversa.

# Trayectorias Más Cortas en Grafos Pesados

	Si G=(V,E,w) es un grafo pesado, w es una función que va de E --> R+. O sea al ingresar una arista a la función, se nos devuelve un peso para esa arista.

Por ejemplo

![[Pasted image 20220815173300.png | 400]]

#### Def 25
La longitud de un paseo G es la suma de las longitudes de sus aristas. En el ejemplo anterior la longitud entre Petén y Guatemala es de 750.

	El algoritmo de E.W. Dijkstra nos ayuda a solucionar el problema de encontrar el paseo más corto.

Pasos para el algoritmo para encontrar la distancia más corta hacia cualquier vértice de G:
1. Sea P = {a} y T = V\\{a}. Para todo t que pertenece a T, l(t) = w(a,t).
2. Seleccionar el vértice en T que tiene el indice más pequeño con respecto a P. A este vértice se le llamará x.
3. Si x es el vértice que se desea alcanzar desde a, entonces el procedimiento termina. Si no, P'=PU{x} y T'=T\\{x}, calcular su índice con respecto a P' de la siguiente forma: l(t) = min{l(t),l(x)+w(x,t)}
4. Repetir el paso 2 y 3 y usar P'=P y T'=T

