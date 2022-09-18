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




