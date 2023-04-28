# Modelo para predicción de prestaciones en agencia de seguros y ofuscación de datos

La compañía de seguros Sure Tomorrow quiere resolver varias tareas con la ayuda de machine learning y te pide que evalúes esa posibilidad.
- Tarea 1: encontrar clientes que sean similares a un cliente determinado. Esto ayudará a los agentes de la compañía con el marketing.
- Tarea 2: predecir la probabilidad de que un nuevo cliente reciba una prestación del seguro. ¿Puede un modelo de predictivo funcionar mejor que un modelo dummy?
- Tarea 3: predecir el número de prestaciones de seguro que un nuevo cliente pueda recibir utilizando un modelo de regresión lineal.
- Tarea 4: proteger los datos personales de los clientes sin afectar al modelo del ejercicio anterior. Es necesario desarrollar un algoritmo de transformación de datos que dificulte la recuperación de la información personal si los datos caen en manos equivocadas. Esto se denomina enmascaramiento u ofuscación de datos. Pero los datos deben protegerse de tal manera que no se vea afectada la calidad de los modelos de machine learning. No es necesario elegir el mejor modelo, basta con demostrar que el algoritmo funciona correctamente.

## Conclusiones generales:

### Tarea 1:

Se procede a escribir una función que devuelva los k vecinos más cercanos para un $n^{th}$ objeto basándose en una métrica de distancia especificada. A la hora de realizar esta tarea no debe tenerse en cuenta el número de prestaciones de seguro recibidas.

Se probará para cuatro combinaciones de dos casos- Escalado
  - los datos no están escalados
  - los datos se escalan con el escalador 
- Métricas de distancia
  - Euclidiana
  - Manhattan
 
**¿El hecho de que los datos no estén escalados afecta al algoritmo kNN? Si es así, ¿cómo se manifiesta?** 

Como se observa, el hecho de escalar los datos en este caso nos permite encontrar personas que tiene el mismo `insurance_benefits` Así como un promedio de miembro de la familia `family_members` y el género a la perfección, variando las edades y el ingreso de esas personas, siendo estos similares entre si. Haciendo alusión a que estas perosnas son bastante semejantes.

Sin embargo, al no escalar los datos, es como si colocasemos un filtro por el ingreso total, ya que al ser el valor má grande, el algoritmo lo toma con más peso, y no nos permite tener otro tipo de información sobre las personas.

**¿Qué tan similares son los resultados al utilizar la métrica de distancia Manhattan (independientemente del escalado)?** 

En este caso, son igual de precisos ambos algoritmos, ya que arrojan a las mismas personas en ambos casos

### Tarea 2:

Con el valor de `insurance_benefits` superior a cero como objetivo, evalúa si el enfoque de clasificación kNN puede funcionar mejor que el modelo dummy.
Instrucciones:
- Se procede a contruir un clasificador basado en KNN y mide su calidad con la métrica F1 para k=1...10 tanto para los datos originales como para los escalados. Sería interesante observar cómo k puede influir en la métrica de evaluación y si el escalado de los datos provoca alguna diferencia. Puedes utilizar una implementación ya existente del algoritmo de clasificación kNN de scikit-learn 
- Luego se construye un modelo dummy que, en este caso, es simplemente un modelo aleatorio. Debería devolver "1" con cierta probabilidad. Probemos el modelo con cuatro valores de probabilidad: 0, la probabilidad de pagar cualquier prestación del seguro, 0.5, 1.
La probabilidad de pagar cualquier prestación del seguro puede definirse como



Como se puede observar, la calidad el modelo es baja, con un F1 entono al 12% y 20% lo cual no nos brinda demasiada información y no es lo suficientemente preciso. Se puede decir que en este caso el modelo predictivo no funciona mejor que el Dummy, será mejor optar por la regresión lineal para aumentar el valor de F1


### Tarea 3:

### Tarea 4:
