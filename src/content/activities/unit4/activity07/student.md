
[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/_YyvppljJ)

![Kylian Mbappe](../../../../assets/uni4-7.png)

### Codigo

``` js
class Oscillator {
  constructor() {
    this.angle = createVector();
    this.velocity = createVector(randomGaussian(0, 0.05), randomGaussian(0, 0.05));
    this.amplitude = createVector(random(20, width / 2), random(20, height / 2));
    this.damping = random(0.98, 0.995);
  }

  oscillate() {
    this.velocity.mult(this.damping);
    this.angle.add(this.velocity);
  }

  display() {
    let x = sin(this.angle.x) * this.amplitude.x;
    let y = sin(this.angle.y) * this.amplitude.y;

    push();
    translate(width / 2, height / 2);
    stroke(255);
    strokeWeight(2);
    fill(127, 127);
    line(0, 0, x, y);
    ellipse(x, y, 32, 32);
    pop();
  }
}

let oscillators = [];

function setup() {
  createCanvas(600, 400);
  for (let i = 0; i < 5; i++) {
    oscillators.push(new Oscillator());
  }
}

function draw() {
  background(0);
  for (let osc of oscillators) {
    osc.oscillate();
    osc.display();
  }
}
```
