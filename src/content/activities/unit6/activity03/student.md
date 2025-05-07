# Explicacion de las tres reglas de flocking

## 1. Separacion
Su objetivo es evitar que los agentes se amontonen. Si otro agente esta cerca de otro se genera una fuersa de repulsion que es proporcional a la cercania o sea entre mas cerca esta mas fuerte es. Esta fuerza empuja al agente en direccion contraria al vecino mas cercano.

## 2. Alineacion
Su objetivo es que los agentes se muevan en la misma direccion. Calculando la velocidad promedio de los vecinos cercanos y el agente intenta igualar su velocidad a la de ellos, creando una especie de movimiento sincronizado.

## 3. Cohesion
Su objetivo es mantener al grupo unido. Calculando la posicion promedio de sus vecinos y generando una fuerza que lo dirige hacia el centro acercandose a los demas.


# Parametros del flocking

```perceptionRadius``` es lo que tan lejos puede ''ver'' un agente a sus vecinos.

```separationWeight```, ```alingnmentWeight```, ```cohesionWeight``` son los pesos que determinan la influencia de cada regla.

```maxSpeed``` velocidad maxima a la que se mueve un agente.

```maxForce``` es la maxima fuerza que pued eaplicar para cambiar la direccion o su velocidad.

# Modificacion al codigo

### Objetivo
Queria ver que pasaria si reducia la percepcion de cohesion y se aumentaba el peso de separacion para que asi se disperse el grupo.

### Codigo

``` js
this.perceptionRadius = 50;

let separation = this.separate(boids);
let alignment = this.align(boids);
let cohesion = this.cohesion(boids);

separation.mult(2.5);
alignment.mult(1.0); 
cohesion.mult(0.3);
```

### Resultado
Los boids se dispersan mas rapido ya que su cohesion es debil y la separacion es fuerte, se forman pequeños subgrupos e inclusive algunos van solos y el movimiento global es menos estructurado y mas caotico con colisiones menos frecuentes pero menos organizacion.

![Mbappe](../../../../assets/uni6-3.gif)
