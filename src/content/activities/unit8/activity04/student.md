## Configuracion de pj5sound

Use p5.sound para conectar el audio con lo visual primero cargue la cancion con `loadSound('a.mp3')` en `preload()` y la reproduzco desde `setup()` tambien cree dos analizadores uno con `new p5.FFT()` para sacar frecuencias como graves y agudos y otro con `new p5.Amplitude()` para medir el volumen general

Estos datos controlan todo el sistema visual en especial la explosion que se activa despues del segundo 205 cuando empieza esa parte el programa analiza los graves con `fft.getEnergy("bass")` los agudos con `fft.getEnergy("treble")` y el volumen con `amp.getLevel()`

```js
let bass = fft.getEnergy("bass")
let treble = fft.getEnergy("treble")
let level = amp.getLevel()
```

Uso la diferencia entre graves y agudos multiplicada por el volumen para calcular la intensidad del efecto

```js
let diff = treble - bass
let intensity = level * 5
let rawFactor = diff * intensity
```

Eso define el tamaño y velocidad de las particulas que simulan una explosion que sale desde el mouse cuanto mas fuerte suena la cancion mas grande y rapida es la explosion

```js
let speed = constrain(baseSpeed * sizeFactor baseSpeed baseSpeed * baseSizeMax)
let radius = constrain(baseRadius * sizeFactor baseRadius baseRadius * baseSizeMax)
```

Tambien agregue una opcion para activar o desactivar el glow con click izquierdo para que el efecto se vea mas potente o mas limpio

## Codigo y Simulacion

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/rwvM04daS)

[Ver Demo](../../../../assets/uni8-4.mp4)


``` js
let sound;
let fft, amp;
let boids = [];
let trails = [];
let explosions = [];
let glowActive = true;
let startTime = 0;

function preload() {
  sound = loadSound('a.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB, 360, 100, 100, 1);
  noFill();
  fft = new p5.FFT();
  amp = new p5.Amplitude();
  background(0);

  for (let i = 0; i < 80; i++) {
    boids.push(new Boid(random(width), random(-height, 0)));
  }

  sound.play();
  sound.jump(startTime);
}

function draw() {
  let t = sound.currentTime();

  fill(0, 0.05);
  rect(0, 0, width, height);

  if (t < 205) { 
    for (let b of boids) {
      b.applyForce(createVector(0, 0.02));
      b.update();
      b.edges();
      b.show();

      trails.push(new Trail(b.pos.copy(), b.brightness));
    }

    for (let i = trails.length - 1; i >= 0; i--) {
      trails[i].update();
      trails[i].show();
      if (trails[i].life <= 0) trails.splice(i, 1);
    }
  } else if (t >= 205 && t < 216) {
    let fade = map(t, 205, 216, 1, 0);
    for (let b of boids) {
      b.opacity = fade;
      b.applyForce(createVector(0, 0.02));
      b.update();
      b.edges();
      b.show();
      trails.push(new Trail(b.pos.copy(), b.brightness * fade));
    }

    for (let i = trails.length - 1; i >= 0; i--) {
      trails[i].update();
      trails[i].show();
      if (trails[i].life <= 0) trails.splice(i, 1);
    }
  } else {
    drawExplosions();
  }
}

class Boid {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.baseYSpeed = random(0.3, 1.5);
    this.vel = createVector(0, this.baseYSpeed);
    this.acc = createVector();
    this.size = random(12, 25);
    this.brightness = 0;
    this.opacity = 1;
    this.oscillationAngle = random(TWO_PI);
    this.oscillationAmplitude = random(10, 25);
  }

  applyForce(force) {
    this.acc.add(force);
  }

  update() {
    let level = amp.getLevel();
    this.brightness = map(level, 0, 0.4, 0.3, 1);

    let speedFactor = map(level, 0, 0.4, 0.5, 3);
    this.vel.y = this.baseYSpeed * speedFactor;

    this.vel.y += this.acc.y;
    this.pos.y += this.vel.y;

    this.oscillationAngle += 0.03;
    this.pos.x += sin(this.oscillationAngle) * 0.5; 
    this.acc.mult(0);
  }

  edges() {
    if (this.pos.y > height + this.size) {
      this.pos.y = random(-height, 0);
      this.pos.x = random(width);
    }
    if (this.pos.x > width + this.size) this.pos.x = -this.size;
    if (this.pos.x < -this.size) this.pos.x = width + this.size;
  }

  show() {
    push();
    translate(this.pos.x, this.pos.y);
    noStroke();
    fill(55, 100, 90 * this.brightness, this.opacity);

    if (glowActive) {
      drawingContext.shadowBlur = 15 * this.brightness * this.opacity;
      drawingContext.shadowColor = color(55, 100, 90, 0.3 * this.opacity);
    } else {
      drawingContext.shadowBlur = 0;
    }

    ellipse(0, 0, this.size * 0.8, this.size * 1.6);
    ellipse(0, 0, this.size * 1.2, this.size * 2.4);
    pop();
  }
}

class Trail {
  constructor(pos, brightness) {
    this.pos = pos;
    this.life = 60;
    this.brightness = brightness;
  }

  update() {
    this.life--;
  }

  show() {
    push();
    noFill();
    stroke(55, 100, 90 * this.brightness, (this.life / 60) * 0.3);
    strokeWeight(1.5);
    line(this.pos.x, this.pos.y, this.pos.x, this.pos.y + 10);
    pop();
  }
}

class ExplosionParticle {
  constructor(angle, speed, radius, col) {
    this.pos = createVector(mouseX, mouseY);
    this.vel = p5.Vector.fromAngle(angle).mult(speed);
    this.radius = radius;
    this.life = 255;
    this.col = col;
  }

  update() {
    this.pos.add(this.vel);
    this.life -= 8;
  }

  done() {
    return this.life <= 0;
  }

  show() {
    noStroke();
    fill(this.col[0], this.col[1], this.col[2], this.life / 255);
    ellipse(this.pos.x, this.pos.y, this.radius);
  }
}

function drawExplosions() {
  fft.analyze();
  let bass = fft.getEnergy("bass");  
  let treble = fft.getEnergy("treble"); 
  let level = amp.getLevel();

  if (level < 0.03) return;

  let diff = treble - bass;
  let intensity = level * 5; 


  let rawFactor = diff * intensity;
  rawFactor = constrain(rawFactor, -255, 255);

  let baseSizeMin = 1;
  let baseSizeMax = 5;
  let sizeFactor = map(pow(abs(rawFactor)/255, 2), 0, 1, baseSizeMin, baseSizeMax);
  if (rawFactor < 0) sizeFactor = map(sizeFactor, baseSizeMin, baseSizeMax, baseSizeMax, baseSizeMin); 
  if (frameCount % 3 === 0) {
    for (let i = 0; i < 15; i++) {
      let angle = random(TWO_PI);

      let baseSpeed = map(level, 0, 1, 2, 20);
      let baseRadius = random(5, 20);

      let speed = constrain(baseSpeed * sizeFactor, baseSpeed, baseSpeed * baseSizeMax);
      let radius = constrain(baseRadius * sizeFactor, baseRadius, baseRadius * baseSizeMax);

      let colorSet = [
        [55, 100, 90],
        [45, 100, 85],
        [50, 90, 80]
      ];
      let col = random(colorSet);

      explosions.push(new ExplosionParticle(angle, speed, radius, col));
    }
  }

  for (let i = explosions.length - 1; i >= 0; i--) {
    explosions[i].update();
    explosions[i].show();
    if (explosions[i].done()) {
      explosions.splice(i, 1);
    }
  }
}

function mouseClicked() {
  if (mouseButton === LEFT) {
    glowActive = !glowActive;
  }
}
```
