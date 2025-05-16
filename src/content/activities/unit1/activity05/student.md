## Codigo

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/lbYOJdrO3)

``` js
function setup() {
  createCanvas(400, 400);
  background(200);
}

function draw() {
  noStroke();
  fill(0, 10);

  let x = randomGaussian(50, 10);
  let y = 25;
  let size = 20;
  square(x, y, size);

  x = randomGaussian(50, 10);
  y = 50;
  size = 20;
  drawTriangle(x, y, size);

  x = randomGaussian(50, 10);
  y = 75;
  let w = 30;
  let h = 15;
  rect(x, y, w, h);
  x = randomGaussian(50, 10);
  y = 100;
  w = 30;
  h = 15;
  rect(x, y, w, h);
}

function drawTriangle(x, y, size) {
  beginShape();
  vertex(x, y - size / 2);
  vertex(x - size / 2, y + size / 2);
  vertex(x + size / 2, y + size / 2);
  endShape(CLOSE);
}
```

## Que hace el codigo?
El codigo genera figuras geometricas cuadrados, triangulos y rectangulos con una distribuccion normal.

![hola](../../../../assets/Screenshot%202025-01-26%20175255.png)
