#### Explicacion de cambios

Se reemplazan las variables escalares ``` this.x ``` y ``` this.y ``` con un vector ``` this.position ```, creado con ``` createVector ```.

Point ahora usa ``` this.position.x ``` y ``` this.position.y ```.

Los modificadores de posicion ``` this.x++ ``` y ``` this.y++ ``` ahora se ajustaron para trabajar con x e y en los vectores.

#### Codigo

[Enlace a la simulacion](https://editor.p5js.org/DonTuvo/sketches/O0Wnuso7z)

``` js
let walker;

function setup() {
  createCanvas(400, 400);
  walker = new Walker();
  background(220);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker{
  constructor(){
 this.position = createVector(width / 2, height / 2);
  }
  
  show(){
  stroke(0);
  point(this.position.x, this.position.y);
}
  step() {
    const choice = floor(random(4));
    if (choice == 0) {
      this.position.x++;
    } else if (choice == 1) {
      this.position.x--;
    } else if (choice == 2) {
      this.position.y++;
    } else {
      this.position.y--;
    }
  }
}
```
