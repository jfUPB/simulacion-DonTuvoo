## Aceleracion constante

Cuando se aplica una aceleracion constante al objeto, su velocidad va aumentando provocando asi que el objeto se mueva mas rapido siguiendo una trayectoria.

#### Por que sucede?

Esto sucede porque la aceleracion se suma a la velocidad, como la aceleracion es constante, el objeto gana velocidad generando un movimiento mas o menos parecido a un cuerpo en caida libre.

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/V2EUrz2pg)

### Codigo aceleracion constante


``` js
let mover;

function setup() {
  createCanvas(640, 360);
  mover = new Mover();
}

function draw() {
  background(255);
  mover.applyConstantAcceleration();
  mover.update();
  mover.checkEdges();
  mover.show();
}

class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0.05, 0.05);
  }

  applyConstantAcceleration() {
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
    if (this.position.x > width) this.position.x = 0;
    if (this.position.x < 0) this.position.x = width;
    if (this.position.y > height) this.position.y = 0;
    if (this.position.y < 0) this.position.y = height;
  }
}
```

## Aceleracion aleatoria

El objeto cambia su velocidad de forma impredecible, moviendose en distintas direcciones sin un patron en si.

Por que ocurre?
La aceleracion va tomando un valor aleatorio, lo que altera la direccion y magnitud de la velocidad. Como resultado el objeto cambia de direccion y su velocidad va cambiando.

### Codigo aceleracion aleatoria

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/AgIod7P5b)


``` js
let mover;

function setup() {
  createCanvas(640, 360);
  mover = new Mover();
}

function draw() {
  background(255);
  mover.applyRandomAcceleration();
  mover.update();
  mover.checkEdges();
  mover.show();
}

class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
  }

  applyRandomAcceleration() {
    this.acceleration = createVector(random(-0.1, 0.1), random(-0.1, 0.1));
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
    if (this.position.x > width) this.position.x = 0;
    if (this.position.x < 0) this.position.x = width;
    if (this.position.y > height) this.position.y = 0;
    if (this.position.y < 0) this.position.y = height;
  }
}
```
## Aceleracion hacia el mouse

El circulo se mueve de manera fluida hacia el cursor, ajustando su trayectoria y acelerando cuando esta lejos. Cuando esta cerca del mouse, su velocidad disminuye hasta casi detenerse.

#### Por que ocurre?

La aceleracion es un vector que apunta hacia la posicion del mouse y su magnitud depende de la distancia entre el objeto y el cursor. Como resultado de este, el objeto acelera cuando esta lejos y desacelera al acercarse.

### Codigo aceleracion hacia el mouse

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/oQqwt5Rfu)

``` js
let mover;

function setup() {
  createCanvas(640, 360);
  mover = new Mover();
}

function draw() {
  background(255);
  mover.applyMouseAcceleration();
  mover.update();
  mover.checkEdges();
  mover.show();
}

class Mover {
  constructor() {
    this.position = createVector(width / 2, height / 2);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
  }

  applyMouseAcceleration() {
    let target = createVector(mouseX, mouseY);
    this.acceleration = p5.Vector.sub(target, this.position);
    this.acceleration.setMag(0.2);
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
    if (this.position.x > width) this.position.x = 0;
    if (this.position.x < 0) this.position.x = width;
    if (this.position.y > height) this.position.y = 0;
    if (this.position.y < 0) this.position.y = height;
  }
}
```
