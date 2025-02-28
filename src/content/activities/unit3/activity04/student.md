En la unidad anterior definiamos la aceleracion con el constructor
``` this.acceleration = createVector(0.01, 0.01); ```

En este codigo podriamos definir la aceleracion de la misma forma ``` this.acceleration = createVector(0.01, 0.01); ``` justamente en la parte donde dice ``` // Aqui calculo la aceleracion ```

Luego en update() la aceleracion se sumaria a la velocidad.
``` js
this.velocity.add(this.acceleration);
this.velocity.limit(this.topSpeed);
this.position.add(this.velocity);
```

### Que tiene que ver esto con las leyes de Newton?

En la segunda ley de Newton se dice que F=ma

Donde F es la fuerza, m la masa y a la aceleracion. Suponiendo que la masa es 1 podemos calcular directamente la aceleracion a partir de la fuerza.
