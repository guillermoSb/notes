
# Grafos Planares
---
[[01 Teoría de Grafos]]

#### Def 32
Un grafo es aplanable si lo podemos dibujar de manera plana sin que ninguna arista se cruce. *Excepto en vértices comunes*.

![[Pasted image 20220816141630.png|500]]

#### Def 33
Una región de un grafo aplanable debe de estar acotada por aristas y no puede dividirse en más sub áreas. En el ejemplo anterior un área podría ser el triángulo que se forma arriba.

![[Pasted image 20220816142404.png|150]]

#### Teorema 7
Para cualquier grafo *aplanable conexo* [[01 Teoría de Grafos#Def 22]], v-e+r = 2. v es vértices, e es el número de aristas y r es el número de regiones. Esta se llama ==Formula de Euler para grafos aplanables==


![[Pasted image 20220816142947.png|300]]
#### Def 35
Dos grafos G1 y G2 son isomorfos bajo vértices de grado dos si es isomorfo o se puede hacer una transformación mediante repetición de inserciones o eliminaciones de vértices de grado dos

![[Pasted image 20220816150405.png|300]]
Ejemplo:

![[Pasted image 20220816151018.png]]

#### Teorema 8 (Kuratowski)
Podemos aplanar un grafo si y solo sí no **contiene** a cualquier subgrafo que sea isomorfo bajo vértices de grado 2 a cualquiera de los grafos v=5 y k=6
![[7C246454-8DBC-487A-9A9F-ABD7B7142543.jpeg|400]]

Ejemplo: No es aplanable por el teorema. Siempre es necesario re dibujar el grafo, en este caso no lo hice. Pero si se puede re dibujar para que parezca un grafo k33

![[Pasted image 20220816152613.png]]