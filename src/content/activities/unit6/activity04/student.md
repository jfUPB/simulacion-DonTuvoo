# Explicacion de codigo 

Use flocking para simular peatones en hora pico, donde cada boid representaria a un peaton y al momento de dar un click salen aterrorizados en la direccion contraria como si spawneara un zombie en su cara o algo simila. Cada boid tiene un color y va dejando rastro, representando asi el trayecto que recorreria una persona en hora pico.

### Logica del codigo 
La alineacion simula personas tratando de caminar en la misma direccion en general.

La cohesion representa la tendencia a dirigirse hacia puntos clave.

La separacion es fuerte simulando evitar choques en un espacio tan concurrido.

Cada boid deja u nrastro tipo pincelada generando patrones en tiempo real.

### Interaccion
El mouse de por si funciona de repelente, haciendo que los boids intenten huir de el, y al hacer click genera como una fuerza de empuje, como si los boids huyeran de el.

## Codigo
[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/D-Ny093IR)

![Mbappe](../../../../assets/uni6-4.gif)

``` js
let boids = [];
let panic = false;
let panicTimer = 0;

function setup() {
  createCanvas(800, 600);
  background(20);
  for (let i = 0; i < 100; i++) {
    boids.push(new Boid());
  }
}

function draw() {
  noFill();

  if (panicTimer > 0) {
    panicTimer--;
  } else {
    panic = false;
  }

  for (let boid of boids) {
    boid.flock(boids);
    boid.update();
    boid.edges();
    boid.show();
  }
}

function mousePressed() {
  panic = true;
  panicTimer = 20;
}

class Boid {
  constructor() {
    this.position = createVector(random(width), random(height));
    this.velocity = p5.Vector.random2D();
    this.velocity.setMag(random(2, 4));
    this.acceleration = createVector();
    this.maxForce = 0.2;
    this.maxSpeed = 3;
    this.perceptionRadius = 50;
    this.color = color(random(100, 255), random(100, 255), random(100, 255), 100);
  }

  edges() {
    if (this.position.x > width) this.position.x = 0;
    else if (this.position.x < 0) this.position.x = width;
    if (this.position.y > height) this.position.y = 0;
    else if (this.position.y < 0) this.position.y = height;
  }

  align(boids) {
    let steering = createVector();
    let total = 0;
    for (let other of boids) {
      let d = dist(this.position.x, this.position.y, other.position.x, other.position.y);
      if (other != this && d < this.perceptionRadius) {
        steering.add(other.velocity);
        total++;
      }
    }
    if (total > 0) {
      steering.div(total);
      steering.setMag(this.maxSpeed);
      steering.sub(this.velocity);
      steering.limit(this.maxForce);
    }
    return steering;
  }

  cohesion(boids) {
    let steering = createVector();
    let total = 0;
    for (let other of boids) {
      let d = dist(this.position.x, this.position.y, other.position.x, other.position.y);
      if (other != this && d < this.perceptionRadius) {
        steering.add(other.position);
        total++;
      }
    }
    if (total > 0) {
      steering.div(total);
      steering.sub(this.position);
      steering.setMag(this.maxSpeed);
      steering.sub(this.velocity);
      steering.limit(this.maxForce);
    }
    return steering;
  }

  separate(boids) {
    let steering = createVector();
    let total = 0;
    for (let other of boids) {
      let d = dist(this.position.x, this.position.y, other.position.x, other.position.y);
      if (other != this && d < this.perceptionRadius / 2) {
        let diff = p5.Vector.sub(this.position, other.position);
        diff.div(d * d);
        steering.add(diff);
        total++;
      }
    }
    if (total > 0) {
      steering.div(total);
      steering.setMag(this.maxSpeed);
      steering.sub(this.velocity);
      steering.limit(this.maxForce);
    }
    return steering;
  }

  fleeMouse() {
    let flee = createVector();
    let d = dist(this.position.x, this.position.y, mouseX, mouseY);
    if (panic && d < 150) {
      flee = p5.Vector.sub(this.position, createVector(mouseX, mouseY));
      flee.setMag(this.maxSpeed);
      flee.sub(this.velocity);
      flee.limit(this.maxForce * 6);
    }
    return flee;
  }

  flock(boids) {
    let alignment = this.align(boids);
    let cohesion = this.cohesion(boids);
    let separation = this.separate(boids);
    let flee = this.fleeMouse();

    alignment.mult(0.8);
    cohesion.mult(0.3);
    separation.mult(2.5);

    this.acceleration.add(alignment);
    this.acceleration.add(cohesion);
    this.acceleration.add(separation);
    this.acceleration.add(flee);
  }

  update() {
    this.position.add(this.velocity);
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.maxSpeed);
    this.acceleration.mult(0);
  }

  show() {
    stroke(this.color);
    strokeWeight(2);
    point(this.position.x, this.position.y);

    push();
    stroke(this.color);
    strokeWeight(1);
    line(this.position.x, this.position.y,
         this.position.x - this.velocity.x * 2,
         this.position.y - this.velocity.y * 2);
    pop();
  }
}
```
