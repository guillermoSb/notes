# Creando figuras con ray tracing

## Esfera
**Propiedades básicas**
- radio
- coordenadas para el centro


## Renderer
- función castRay: crea cada rayo
	- recibe el origen del rayo y su dirección
	- 
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
	- 








