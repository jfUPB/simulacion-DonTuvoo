## Que es el Levy Flight?
El Levy Flight es un patron de movimiento aleatorio el cual sigue una serie de saltos de longitud variable, donde las distancias de cada salto siguen una distribucion la cual se llama distribucion de Levy.
Este movmiento se encuentra en contextos como en la naturaleza en la cual parece que ciertos insectos y aves siguen patrones de levy flight en su busqueda de alimentos, tambien se puede usar en la fisica, para describir el movimiento de particulas en medios complejos.

## Codigo

``` js
let position;
let stepSize;


function setup() {
  createCanvas(400, 400);
  background(220);
  
  position = createVector(random(width), random(height));
  stepSize = random(5,20);
}

function draw() {
  stroke(0);
  strokeWeight(2);
  point(position.x, position.y);
  
  let angle = random(TWO_PI);
  let magnitude = random(1, 1000);
  
let newPosition = createVector(
position.x + cos(angle) * stepSize,
position.y + sin(angle) * stepSize
);

newPosition.x = constrain(newPosition.x, 0, width);
newPosition.y = constrain(newPosition.y, 0, height);
  
line(position.x, position.y, newPosition.x, newPosition.y);
  
  position = newPosition;
  if(random(1)<0.1){
     stepSize = random(5,20);
     }
  
}
```
![Mbappe](../../../../assets/Captura%20de%20pantalla%202025-01-31%20104326.png)
