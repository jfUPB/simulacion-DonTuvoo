### Problema en el planteamiento

El problema con el applyForce(force) es que este esta sobrescribiendo la aceleracion en vez de sumar todas las fuerzas aplicadas en un frame.
Ahora mismo, se esta definiendo asi:

``` js
applyForce(force) {
    this.acceleration = force;
    }
```

Cada que llamamos a applyForce() la aceleracion se reinicia en vez de sumar todas las fuerzas que actuan en ese momento. Ejemplo: Si aplicamos primero ```mover.applyForce(wind);``` y luego ```mover.applyForce(gravity);``` la aceleracion solo tomara el valor de gravity.

### Solucion

Para corregir esto, la aceleracion debe ser el resultado de la sumatoria de todas las fuerzas aplicadas en el frame. En vez de sobrescrbir this.acceleration, le sumamos la nuema fuerza:

``` js
applyForce(force) {
this.acceleration.add(force);
}
```
Asi sumando todas las fuerzas en un frame para la aceleracion total de un objeto.

### Implementacion en p5.js

``` js
this.velocity.add(this.acceleration);
this.position.add(this.velocity);


this.acceleration.mult(0);
}
```
