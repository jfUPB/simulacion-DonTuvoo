
### Codigo

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/g9JdkF1M7)

En la base de los vectores lo cambie por ```createVector(moseX, mouseY)``` haciendo que las felchas sigan la posicion del mouse, y en la escala use ```dist(mouseX, mouseY, width / 2, height / 2)``` para calcular la distancia entre el mouse y el centro del canvas, tambien use ```map()``` para convertir esta distancia en un factor de escala entre 0.5 y 2 lo que evita que los vectores sean muy grandes o muy pequeños.

``` js
let t = 0;
let direction = 1;

function setup() {
    createCanvas(400, 400);
}

function draw() {
    background(200);

    let base = createVector(mouseX, mouseY);
    let scaleFactor = map(dist(mouseX, mouseY, width / 2, height / 2), 0, width / 2, 0.5, 2);

    let v1 = createVector(100 * scaleFactor, 0);
    let v2 = createVector(0, 100 * scaleFactor);
    let v3 = p5.Vector.add(base, v1);
    let v4 = p5.Vector.add(base, v2);
    let v5 = p5.Vector.sub(v4, v3);

    let myColor = lerpColor(color('red'), color('blue'), t);

    drawArrow(base, v1, 'red');
    drawArrow(base, v2, 'blue');
    drawArrow(v3, v5, 'green');
    drawArrow(base, p5.Vector.lerp(v1, v2, t), myColor);

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
