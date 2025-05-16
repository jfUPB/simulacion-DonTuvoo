### ¿Como funciona la suma de dos vectores?
Como se usa el metodo .add(), este toma los componentes individuales de ambos vectores (x, y, z) y realiza la suma de cada uno.

Matematicamente tenemos el vector position con componentes (x1, y1, z1) y el vector velocity con componentes (x2, y2, z2) entonces tendriamos =(x1 + x2, y1 + y2, z1 + z2)
y en el codigo esto literalmente se resume en position.add(velocity);




### ¿Por que la linea position = position + velocity no funcina?
La linea position = position + velocity no funciona ya que no puedes sumar dods objetos directamente como si fueran numeros. La razon es porque tanto la position como velocity son objetos del tipo p5.Vector.
En p5.js para sumar se usa el metodo .add como por ejemplo: ```position.add(velocity);```.
