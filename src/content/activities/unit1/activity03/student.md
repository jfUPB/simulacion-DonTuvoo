## ¿Qué pregunta quieres responder con este experimento?
Que pasaria si modifico esta parte del codigo ```const choice = floor(random(4));``` colocandole numeros del 0 al 3
## ¿Qué resultados esperas obtener?
Que haya una alteracion al momento de generar la aleatoriedad ya que el metodo genera un numero entre 0 y 3 determinando asi el movimiento del caminante
## ¿Qué resultados obtuviste?
### Cambiandolo por los numeros 0 y 1

![Kylian Mbappe3](../../../../assets/Screenshot%202025-01-26%20161521.png)

El walker se movia solamente hacia la derecha ya sea con 0 o 1
### Cambiandolo por el numero 2

![Kylian Mbappe](../../../../assets/Screenshot%202025-01-26%20161451.png)

El walker se movia aleatoriamente de derecha a izquierda

### Cambiandolo por el numero 3

![Kylian Mpabbe2](../../../../assets/Screenshot%202025-01-26%20161505.png)

El walker se movia aleatoriamente solo hacia abajo derecha y izquierda

## ¿Qué aprendiste de este experimento?

Aprendi como generar aleatoriamente lineas usando un walker y un poquito de javascript (nunca habia programado aqui) :)

## Codigo lindo

[Enlace a la simulación](https://editor.p5js.org/DonTuvo/sketches/54IZhOgtn)

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
    this.x = width / 2;
    this.y = height / 2;
  }
  show(){
  stroke(0);
  point(this.x, this.y);
}
  step() {
    const choice = floor(random(4)); // Ya sea 1,2 o 3 en las modificaciones
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else {
      this.y--;
    }
  }
}
```
