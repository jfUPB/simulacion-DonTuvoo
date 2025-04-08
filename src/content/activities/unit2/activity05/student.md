
### Codigo Lindo
[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/NIw5M8x5P)

``` js
let t = 0;
let direction = 1;

function setup() {
    createCanvas(400, 400);
}

function draw() {
    background(200);

    let v0 = createVector(100, 100);
    let v1 = createVector(200, 0);
    let v2 = createVector(0, 200);
    let v3 = p5.Vector.add(v0, v1);
    let v4 = p5.Vector.add(v0, v2);
    
    let v5 = p5.Vector.sub(v4, v3);
    
    let myColor = lerpColor(color('red'), color('blue'), t);
    
    drawArrow(v0, v1, 'red');
    drawArrow(v0, v2, 'blue');
    drawArrow(v3, v5, 'green');
    drawArrow(v0, p5.Vector.lerp(v1, v2, t), myColor);
    
    t += 0.02 * direction;
    if (t >= 1 || t <= 0) {
        direction *= -1;
    }
}

function drawArrow(base, vec, myColor) {
    push();
    stroke(myColor);
    strokeWeight(7);
    fill(myColor);
    translate(base.x, base.y);
    line(0, 0, vec.x, vec.y);
    rotate(vec.heading());
    let arrowSize = 15;
    translate(vec.mag() - arrowSize, 0);
    triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
    pop();
}
```

### ```lerp()```
* ```lerp(start, stop, amt)```
  Hace una interpolacion entre ```start``` y ```stop```, segun el valor ```amt``` (entre 0 y 1).
  Si ```amt``` es 0 devuelve ```start```; si ```amt``` es 1, devuelve ```stop```; si es 0.5 devuelve el punto medio.

#### ```lerpColor(c1, c2, amt)```
Este funciona igual que ```lerp()```, pero mezcla colores, mezcla c1 y c2 en funcion de amt.

### ```drawArrow()```
La funcion ```drawArrow(base, vec, myColor)``` dibuja una flecha desde ```base``` en la direccion de ```vec``` con el color ```myColor```
* ```push()``` y ```pop``` Mantienen la transformacion aislada.
* ```translate(base.x, base.y)``` Mueve el punto de origen.
* ```line(0, 0, vec.x, vec.y)``` Dibuja la linea de la flecha.
* ```rotate(vec.heading())``` Orienta la flecha en la direccion correcta.
* ```triangle``` Dibuja el triangulo en la punta de la flecha.


  
