## Friccion 

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/YlmHnjEBP)

``` js
let mover;

function setup() {
  createCanvas(600, 400);
  mover = new Mover();
}

function draw() {
  background(220);

  let gravity = createVector(0, 0.2);
  mover.applyForce(gravity);

  if (mover.vel.mag() > 0.1) {
    let friction = mover.vel.copy();
    friction.setMag(-0.05);
    mover.applyForce(friction);
  }

  mover.update();
  mover.edges();
  mover.display();
}

class Mover {
  constructor() {
    this.pos = createVector(width / 2, height / 2);
    this.vel = createVector(2, 0);
    this.acc = createVector(0, 0);
  }

  applyForce(force) {
    this.acc.add(force);
  }

  update() {
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.acc.mult(0);
  }

  edges() {
    if (this.pos.y >= height) {
      this.pos.y = height;
      this.vel.y *= -0.8;
    }
  }

  display() {
    fill(50, 100, 250);
    ellipse(this.pos.x, this.pos.y, 30, 30);
  }
}
```

## Resistencia de aire y fluidos

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/bKXuNEY8f)

``` js
let mover;

function setup() {
  createCanvas(600, 400);
  mover = new Mover();
}

function draw() {
  background(220);

  let gravity = createVector(0, 0.2);
  mover.applyForce(gravity);

  if (mover.vel.mag() > 0.1) {
    let drag = mover.vel.copy();
    let c = 0.05; // Coeficiente de resistencia
    let speedSq = mover.vel.magSq();
    drag.setMag(-c * speedSq);
    mover.applyForce(drag);
  }

  mover.update();
  mover.edges();
  mover.display();
}

class Mover {
  constructor() {
    this.pos = createVector(width / 2, height / 2);
    this.vel = createVector(2, 0);
    this.acc = createVector(0, 0);
  }

  applyForce(force) {
    this.acc.add(force);
  }

  update() {
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.acc.mult(0);
  }

  edges() {
    if (this.pos.y >= height) {
      this.pos.y = height;
      this.vel.y *= -0.8;
    }
  }

  display() {
    fill(100, 200, 100);
    ellipse(this.pos.x, this.pos.y, 30, 30);
  }
}
```

## Atraccion gravitacional

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/RQkNF-dKF)

``` js
let attractor;
let mover;

function setup() {
  createCanvas(600, 400);
  attractor = new Attractor();
  mover = new Mover(random(width), random(height));
}

function draw() {
  background(220);

  let force = attractor.attract(mover);
  mover.applyForce(force);

  mover.update();
  mover.display();
  attractor.display();
}

class Mover {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vel = createVector(0, 0);
    this.acc = createVector(0, 0);
    this.mass = 1;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acc.add(f);
  }

  update() {
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.acc.mult(0);
  }

  display() {
    fill(50, 100, 250);
    ellipse(this.pos.x, this.pos.y, this.mass * 16, this.mass * 16);
  }
}

class Attractor {
  constructor()
```
