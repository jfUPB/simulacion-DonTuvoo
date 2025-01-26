## Diferencia entre distribucciones uniformes y no uniformes.
En las distribucciones uniformes podemos ver que todas las opciones tienen la misma posibilidad, como por ejemplo tirar un dado de 6 caras, que cada numero tiene una probabilidad de 16,67% de salir.
Mientras que en la distribuccion no uniforme es todo lo contrario, algunas de las opciones tienen mas probabilidad que salir que las demas. Como por ejemplo trucar un dado para que el numero 6 tenga el 50% de salir, y el resto de caras se repartan entre si el otro 50% 

## Codigo Modificado
Los puntos generados en la linea horizontal inferior estan mas acumulados en el lado derecho del lienzo

![Mbappe](https://github.com/jfUPB/simulacion-DonTuvoo/blob/main/src/assets/hola.png)

```
function setup() {
  createCanvas(100, 100);

  background(200);
}

function draw() {

  noStroke();
  fill(0, 10);

  let x = random(100);
  let y = 25;
  circle(x, y, 5);

  x = randomGaussian(50);
  y = 50;
  circle(x, y, 5);

  x = randomGaussian(50, 10);
  y = 75;
  circle(x, y, 5);

  x = biasedRandom();
  y = 90;
  circle(x, y, 5);
}

function biasedRandom() {
  let r = random(1);

  return sqrt(r) * 100;
}
```
