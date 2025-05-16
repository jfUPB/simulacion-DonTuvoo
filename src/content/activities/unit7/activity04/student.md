## Flujo de Trabajo
Para integrar Matter,js con p5js primero importe la libreria de Matter.js en el entorno de p5. En setup() inicialice el motor de fisica (Engine.create()) cree el mundo, los cuerpos y configure el MouseConstraint para permitir interaccion. En draw(), actualizo el motor de Matter con Engine.update(engine) y luego dibujo los cuerpos manualmente con p5.js usando posiciones y angulos que proporciona Matter.js.

## Representasion visual vs simulacion fisica
Cada cuerpo de Matter.js representa una letra encerrada en una ficha cuadrada. Para mostrar esto visualemte use push(), translate() y rotate() en p5js para alinear el dibujo con la posicion y el angulo delcuerpo fisico. El pricnipal desafio fue asegurarse de que la letra se mantuviera centrada en la ficha, incluso cuando giraba o rebotaba, pero con textAling(CENTER) y ajustando el texto, se resolvio bien.

## Creacion de formas Complejas
No modele las letras como formas fisicas detalladas, sino que use cuerpos rectangulares para cada letra y dibuje el texto encima. Esta tecnica fue sencilla, pero tambien una limitacion: la colision no sigue la forma exacta de la letra, si no del cuadrado que la contiene.

## Fisica para la semantica
Usar fisica para representar el significado de una palabra me parecio muy efectivo, el rebote literal de las letras reforzo visualmente su sentido. Este enfoque funciona muy bien con palabras relacionadas con movimiento, fuerz peso o comportamientos fisicos.

## Potencial exploratorio
La combinacion de p5js y Matter.js tiene mucho potencial creativo ya que se podrian crear poesias interactivas donde cada palabra reaccion distinto, tambien se podrian simular emociones con fisica, juegos tipograficos donde el usuario reorganice o juegue con las letras, instalaciones artisticas digitales o herramientas educativas para explicar conceptos fisicos de forma visual.


