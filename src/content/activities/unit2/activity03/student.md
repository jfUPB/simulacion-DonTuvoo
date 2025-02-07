#### ¿Que resultado espero obtener?
Que con la funcion print() se vea el mensaje que escriba en la consola y con el toString() se vean los datos del vector en la consola.

#### ¿Que resltado obtuviste?
Tuve los resultados que esperaba obtener :), el texto que puse en el print y los datos del vector se mostraron en la consola.

#### ¿Que tipo de paso hace el codigo?

#### ¿Que aprendi?

### Codigo

``` js
let position;

function setup() {
    createCanvas(400, 400);
    posicion = createVector(6,9);
    playingVector(posicion);
    console.log(posicion.toString());
    noLoop();
}

function playingVector(v){
    v.x = 20;
    v.y = 30;
}

function draw() {
    background(220);
    console.log("Only once");
    print("hola q tal");
}
```
