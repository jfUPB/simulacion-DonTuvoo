### Que pasa si agregamos aceleracion para que el objeto se mueva de forma mas realista, como si estuviera siendo empujado?

Si agregamos un vector de aceleracion que se suma a la velocidad en cada frame, el objeto ira aumentando su velocidad en una direccion.

### Que paso?

El objeto comienza con velocidad 0, pero a medida que pasa el tiempo la aceleracion hace que su velocidad aumente poco a poco.
Cuando el objeto cruza los bordes, su velocidad se reinicia.

### Por que paso?

Motion 101 normalmente solo usa posicion y velocidad. Le sumamos la aceleracion a la velocidad lo que hace que la velocidad aumente progresivamente.

### Codigo

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/hyaYRLRxG)

``` js
let mover;

function setup() {
  createCanvas(640, 240);
  mover = new Mover();
}

function draw() {
  background(255);
  mover.update();
  mover.checkEdges();
  mover.show();
}

class Mover {
  constructor() {
    this.position = createVector(random(width), random(height));
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0.01, 0.01);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
  }

  show() {
    stroke(0);
    strokeWeight(2);
    fill(127);
    circle(this.position.x, this.position.y, 48);
  }

  checkEdges() {
    if (this.position.x > width) {
      this.position.x = 0;
      this.velocity.mult(0);
    } else if (this.position.x < 0) {
      this.position.x = width;
      this.velocity.mult(0);
    }

    if (this.position.y > height) {
      this.position.y = 0;
      this.velocity.mult(0);
    } else if (this.position.y < 0) {
      this.position.y = height;
      this.velocity.mult(0);
    }
  }
}
```
