# Creando figuras con ray tracing

## Esfera
**Propiedades básicas**
- radio
- coordenadas para el centro
- función rayIntersect(self, orig, dir):
	calcular cada valor de la esfera: L, tca, d
	si d es mayor al radio regresar False
	si no regresar true
	


## Renderer
- propiedad scene que tiene una lista de objetos (figuras)
- propiedad camPosition con la posición de la cámara
- función castRay: crea cada rayo
	- recibe el origen del rayo y su dirección
	- busca el intercepto con algún objeto es un booleano
	- busca en cada objeto en la escena llamando a la función que detecta el intercepto mandando el origen y la dirección
	- si hay un intercepto
		- regresar el color actual
		- si no hay intercepto regresar nada

- función glRender: 
	- Pasa pixel por pixel
	- pasa de coordenadas de ventana a coordenadas NDC (-1 a 1)
	- Px  = (((x) / width) * 2) - 1
	- Py = (((y) / height) * 2) - 1
	- Creando la matriz proyección 
		- ángulo de visión, asumiendo que el near plane es 1
		- t = cálculo de top
		- r = t * aspectRatio
	- multiplicamos Px por r 
	- multiplicamos Py por t
	- creamos la dirección a la que va a ir el rayo V3(Px, Py, '-1') 
		- debe de estar normalizada
	- llamar a la función cast ray
	- si la función cast ray regresa un color dibujar un punto 








![[Captura de Pantalla 2022-09-13 a la(s) 7.43.05 p.m..png]]


## Luces

Para calcular el color que se dibuja:
A cada luz le asignamos un integer que indica el tipo de la luz

1. Calcular el color del intercepto si hay intercepto
	1. una variable que guarda el color final del rayo
	2. una variable con el color del objeto (dado por el material del intercepto)
	3. una variable que guarde el color de la luz direccional negro
	4. una variable que guarde el color de la luz ambiental negro
	5. iterar por cada luz en la escena
		1. para la luz direccional
			1. variable que guarda el diffuseColor que inicialmente sera negro
			2. variable que guarda la direccion de la luz * -1
			3. variable que guarda la intensidad de la luz calculada por el producto punto entre el intercepto y la dirección de la luz
			4. asegurarnos que la intensidad siempre es mayor a 0
			5. asignar al diffuse color el nuevo valor rgb de la luz multiplicado por la intencidad
			
			7. calcular ==sombras==
			8. hacer una variable que guarda la intensidad de la sombra. Por defecto es 0
			9. buscar un shadowIntersect que es otro scene intersect **evitar revisar el objeto** para eso pasar una referencia al mismo objeto
			10. El nuevo rayo tiene origen en el que se hizo intersect, la dirección de la luz porque queremos ver si hay un objeto entre la luz y el intercepto
			11. Si el nuevo rayo tiene un intercepto asignar un valor de 1 a la intensidad de la sombra
			12.  sumar a la variable que guarda el color global de la luz direccional el diffuseColor
		2. Para una luz ambiental
			1. variable que guarda el color de la luz ambiental que es el color de la luz ambiental por la intensidad
		3. Para un point light (tiene un origen, un color, constante, valor lineal, valor cuadratico)
			1. la direccion del point light es el punto de origen de la luz - el punto del intersect.
			2. Utilizar cálculos similares a la luz direccional para iluminar los objetos.
			3. 
	1. hacer que el final color sea igual a el color de la luz direccional + el color de la luz ambiental
	2. multiplicar el final color por el color del objeto
	3. hacer que el color final este entre 0 y 1
	4. regresar el color final


## Attenuation
Utilizamos el valor constante, lineal y cuadrático de la luz. La formula para calcularla es
`att = 1.0/(Kc + Kl * d + Kq * d^2)`
Multiplicar la intensidad por el valor de la attenuacion
## Specularidad
Que tan reflectiva es es una superficie. Depende de que tanto absorbe el color mientras más alta, el punto blanco en donde pega la luz es más pequeño.


En la luz direccional: L es el vector de la luz, R es el vector reflejado
`R = 2 * (N . L) * N - L`
1. calcular el vector de reflejo utilizando la formula de arriba.
2. el vector de reflejo debe estar normalizado
3. Calcular la dirección de la vista, que es la resta entre la posición de la cámara y el punto de contacto
4. Normalizarla
5. calcular la intensidad especular, que es la intensidad de la luz por el maximo entre 0 y el producto punto entre la dirección de la vista y el valor del vector de reflejo.
6. Agregar una propiedad al material sobre qué tan especular es por defecto 1
7. elevar la intensidad especular por la propiedad de que tan especular es el material
8. el color especular es la intensidad especular por el color de la luz
9. sumar el diffuseColor por el specColor


![[Captura de Pantalla 2022-09-18 a la(s) 2.44.10 p.m..png]]


## Reflexiones
Algoritmos de Whitted

3 casos
- Superficie opaca
- Superficie reflexiva
	- se emite un rayo
- Superficie transparente
	- se refleja un rayo
	- refracción

Para reflejar un rayo
generamos el nuevo rayo, y buscamos en donde intercepta. Para esto necesitamos **recursión**. 

==Agregar una propiedad global para el max recursion depth==

Agregar una propiedad a un material que indique si es opaca, reflectiva o transparente.

al castear el rayo
- Si el material es opaco, realizar el calculo normal de la luz
- Si el material es reflectivo
	- creamos un vector de reflejo, la normal es la del intercepto y la dirección es la del rayo ==negada==.?
	- Obtener el nuevo color del reflejo
		- llamando la nueva función de recursión en el mismo punto con la dirección del vector reflejado
		- si importa la especularidad
		- el **finalColor** sera igual al reflectColor
		- revisar que no haga contacto conmigo mismo


Environment Maps

- utilizamos una ecuaci'on especial para obtener las coordenadas x,y de el objeto a dibujar.

En la clase de textura

- metodo para obtener el env color
	- recibe dirección




## Refracción
Whitted's algorithms 

Un material tiene un índice de refracción **ior** que indica que tánto se dobla un rallo de lúz cuando entra a un material.

Utilizamos la ==ley de Snell== para encontrar la relación entre el ángulo de incidencia y el rayo de refracción

sin(O1)/sin(O2) = n2/n1

**Fresnel Equation**

Describen la relación entre la cantidad de luz reflejada y luz refractada.

**Implementando Refracción**

1. Crear un nuevo tipo de material que sea TRANSPARENT
2. Una nueva función que va a refractar un vector
	1. Recibe: normal, dirección, ior (índice de refracción)
3. Crear una función que implementa fresnel
	1. Recib
4. Agregar un valor **ior** al material
5. Cuando casteamos el rayo, si la superficie es transparente
	1. detectar si el rayo que incide viene de afuera haciendo un producto punto entre entre la dirección del rayo y la normal. Si este resultado es menor a 0 entonces el rayo viene de afuera
	2. Agregar un **bias** que es un margen de error. Para que el rayo no tope consigo mismo
