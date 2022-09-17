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

