El problema con la implementacion es que el objerto force es un p5.Vector, pasando por una referencia y no un valor. Afectando asi directamente a la variable original si se aplica cualquier modificacion.
En lugar de modificar force directamente es mejor crear una copia del vector y dividirlopor la masa antes de sumarlo a la aceleracion.


### Implementacion y solucion

``` js
class Mover {
constructor(m) {
   this. position = createVector(),
   this.velocity = createVector();
   this.mass = m;
 }
  applyForce(force){
    let f = force.copy()
    f.div(this.mass);
    this.acceleration.add(f):
 }
}
```
