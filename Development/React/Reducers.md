
## Razones para usar un reducer
- Realizar ciertas acciones a algún dato y enviar la acción a realizar. Como agregar, editar, etc.
- Para que la lógica quede solo en un lugar cuando es muy compleja y un **useState** requiere demasiados cambios.
## Que Recibe un reducer
- Estado actual
- accion
## Que tiene que regresar un reducer
- Un nuevo estado

## useReducer
Podemos obtener el estado y la función dispatch que sirve para llamar al reducer.
Enviamos
- funcion reducer
- Valor inicial
- funcion de init
La función de init se puede ejecutar la primera vez que el reducer se crea. Luego la función reducer permite hacer los cambios al estado.

